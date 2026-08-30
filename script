// Carrossel em Fade
const slides = document.querySelectorAll('.fade-bg');
let currentSlide = 0;

function nextSlide() {
    slides[currentSlide].classList.remove('active');
    currentSlide = (currentSlide + 1) % slides.length;
    slides[currentSlide].classList.add('active');
}
setInterval(nextSlide, 4000);

// Gerenciamento de Idioma e Links Locais DinÃ¢micos (PT | EN)
let currentLang = localStorage.getItem('pref_lang');

if (!currentLang) {
    const browserLang = navigator.language || navigator.userLanguage;
    currentLang = browserLang.toLowerCase().startsWith('pt') ? 'pt' : 'en';
}

function updateLanguage(lang) {
    currentLang = lang;
    localStorage.setItem('pref_lang', lang);
    document.documentElement.lang = lang === 'pt' ? 'pt-BR' : 'en';
    document.getElementById('lang-text').textContent = lang === 'pt' ? 'EN' : 'PT';

    // SeleÃ§Ã£o de todos os elementos de links de currÃ­culo e portfÃ³lios (Topo e Cards)
    const resumeLink = document.getElementById('resume-link');
    const copyPortfolioLink = document.getElementById('copy-portfolio-link');
    const photoPortfolioLink = document.getElementById('photo-portfolio-link');
    const cardCopyLink = document.getElementById('card-copy-link');
    const cardPhotoPortfolioLink = document.getElementById('card-photo-portfolio-link');

    if (lang === 'pt') {
        if (resumeLink) resumeLink.href = './curriculo_pt.pdf';
        if (copyPortfolioLink) copyPortfolioLink.href = './portfolio_copy_pt.pdf';
        if (photoPortfolioLink) photoPortfolioLink.href = './portfolio_fotografia_pt.pdf';
        if (cardCopyLink) cardCopyLink.href = './portfolio_copy_pt.pdf';
        if (cardPhotoPortfolioLink) cardPhotoPortfolioLink.href = './portfolio_fotografia_pt.pdf';
    } else {
        if (resumeLink) resumeLink.href = './curriculo_en.pdf';
        if (copyPortfolioLink) copyPortfolioLink.href = './portfolio_copy_en.pdf';
        if (photoPortfolioLink) photoPortfolioLink.href = './portfolio_fotografia_en.pdf';
        if (cardCopyLink) cardCopyLink.href = './portfolio_copy_en.pdf';
        if (cardPhotoPortfolioLink) cardPhotoPortfolioLink.href = './portfolio_fotografia_en.pdf';
    }

    document.querySelectorAll('[data-pt]').forEach(el => {
        const text = el.getAttribute(`data-${lang}`);
        if (text) {
            if (el.children.length > 0 && el.querySelector('strong')) {
                const strongText = el.querySelector('strong').outerHTML;
                el.innerHTML = strongText + ' ' + text.split(': ')[1];
            } else {
                el.textContent = text;
            }
        }
    });
}

function toggleLanguage() {
    const newLang = currentLang === 'pt' ? 'en' : 'pt';
    updateLanguage(newLang);
}

// FunÃ§Ãµes de Compartilhamento Inteligente
function shareLink() {
    const shareData = {
        title: 'Aryel Evelin | Copywriting, Roteiros & Storytelling | Fotografia',
        text: 'Especialista em unir visÃ£o estratÃ©gica de negÃ³cios, copywriting, crescimento de audiÃªncia e storytelling de alto impacto.',
        url: 'https://smoakdanvers.github.io/portfolio/'
    };

    if (navigator.share) {
        navigator.share(shareData).catch(() => {});
    } else {
        navigator.clipboard.writeText(shareData.url);
        const alertMsg = document.documentElement.lang === 'pt-BR' 
            ? 'Link copiado para a Ã¡rea de transferÃªncia! Pronto para enviar com prÃ©via.' 
            : 'Link copied to clipboard! Ready to share with preview.';
        alert(alertMsg);
    }
}

function shareInstagram() {
    const textToCopy = "Confira o portfÃ³lio da Aryel Evelin: https://smoakdanvers.github.io/portfolio/";
    navigator.clipboard.writeText(textToCopy);
    
    const msg = document.documentElement.lang === 'pt-BR'
        ? "Link copiado! Como o Instagram nÃ£o permite envio automÃ¡tico de DM via web, abra o Direct do Instagram e cole (Ctrl+V) o link para enviar com a prÃ©via!"
        : "Link copied! Since Instagram doesn't allow automatic web DMs, open Instagram Direct and paste the link to send it with the rich preview!";
    alert(msg);
}

// Aplica o idioma ao carregar a pÃ¡gina
document.addEventListener('DOMContentLoaded', () => updateLanguage(currentLang));
