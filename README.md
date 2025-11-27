# Refactory Website - Quick Reference Guide

## Project Structure
```
Refactory-Copy/
├── index.html          (Main HTML file)
├── style.css           (All styling)
├── README.md           (This file)
└── images/             (Background images folder)
    ├── hero1.jpg
    ├── hero2.jpg
    ├── hero3.jpg
    └── hero4.jpg
```

---

## Key Features & How They Work

### 1. **Hero Section with Auto-Cycling Background on Hover**

**HTML Structure:**
```html
<section class="hero">
    <div class="hero-layers" aria-hidden="true">
        <div class="hero-layer" style="background-image: url('images/hero1.jpg');"></div>
        <div class="hero-layer" style="background-image: url('images/hero2.jpg');"></div>
        <div class="hero-layer" style="background-image: url('images/hero3.jpg');"></div>
        <div class="hero-layer" style="background-image: url('images/hero4.jpg');"></div>
    </div>
    <div class="hero-content">
        <!-- Your content here -->
    </div>
</section>
```

**CSS (How it cycles):**
- 4 keyframe animations: `cycle-1`, `cycle-2`, `cycle-3`, `cycle-4`
- Each layer visible for ~1 second, hidden for 3 seconds
- Total cycle = 4 seconds (repeats)
- **Triggered on hover:** `.hero:hover .hero-layer { animation: cycle-X 4s infinite; }`

**To adjust timing:**
- Change `4s` to `2s` for faster, `8s` for slower cycling

---

### 2. **Dynamic Navbar (Color Change on Scroll)**

**HTML:**
```html
<nav class="navbar">
    <div class="navbar-container">
        <div class="navbar-logo">
            <img src="Refactory-Logo.png" alt="Logo">
            <span>refactory</span>
        </div>
        <ul class="nav-menu">
            <li><a href="#about" class="nav-link">About Us</a></li>
            <!-- More links -->
        </ul>
        <button class="search-btn"><!-- Search icon --></button>
    </div>
</nav>
```

**CSS Base:**
```css
.navbar {
    background: linear-gradient(135deg, #3d2a5c 0%, #2d1b4e 50%, #1a0f2e 100%);
    position: sticky;
    top: 0;
    z-index: 100;
}

/* When scrolled */
.navbar.scrolled {
    background: white;
}
.navbar.scrolled .nav-link {
    color: #333;
}
```

**JavaScript (at bottom of index.html):**
```javascript
const navbar = document.querySelector('.navbar');
window.addEventListener('scroll', () => {
    if (window.scrollY > 50) {
        navbar.classList.add('scrolled');
    } else {
        navbar.classList.remove('scrolled');
    }
});
```

**Quick tweaks:**
- Change `50` to trigger scroll effect earlier/later
- Swap colors in `.navbar` background and `.navbar.scrolled`

---

### 3. **Course Cards (3-Column Grid)**

**HTML:**
```html
<section class="courses-section">
    <div class="courses-grid">
        <div class="course-card">
            <div class="course-image foundational"></div>
            <h3>Foundational Courses</h3>
            <p>Description...</p>
            <button class="btn-learn">Learn more</button>
        </div>
        <!-- Repeat for each card -->
    </div>
</section>
```

**CSS:**
```css
.courses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}
```

---

### 4. **Sections Overview**

| Section | Purpose | Key Classes |
|---------|---------|------------|
| **Hero** | Main landing area with cycling backgrounds | `.hero`, `.hero-layers`, `.hero-layer` |
| **Courses** | 3 course cards in grid layout | `.courses-grid`, `.course-card` |
| **Success** | Stats display (814+, 91%, etc.) | `.success-section`, `.stats-grid` |
| **10X Program** | Program info + partner logos | `.program-section` |
| **Summit** | UG Dev Summit section | `.summit-section` |
| **Footer** | Contact & resource links | `.footer`, `.footer-column` |

---

## Quick Build Checklist

✅ **1. HTML Setup**
- Copy the basic structure from `index.html`
- Update `<title>` and logo path
- Add your content to each section

✅ **2. CSS Setup**
- Copy all rules from `style.css`
- Key animations: `cycle-1`, `cycle-2`, `cycle-3`, `cycle-4`
- Navbar gradient & scroll behavior

✅ **3. JavaScript Setup**
- Add scroll listener at bottom of HTML
- Detects scroll and adds `.scrolled` class to navbar

✅ **4. Images**
- Create `images/` folder
- Add: `hero1.jpg`, `hero2.jpg`, `hero3.jpg`, `hero4.jpg`
- Update image paths in `<style>` attributes if different

✅ **5. Customize**
- Colors: Change gradient values in `.hero` and `.navbar`
- Typography: Update font-size, font-weight in headings
- Spacing: Adjust `padding`, `gap`, `margin` values

---

## Common Tweaks

| What | Where | How |
|------|-------|-----|
| Change cycle speed | CSS `cycle-1` etc. | Edit `4s` to `2s` or `8s` |
| Change navbar colors | CSS `.navbar` | Update gradient value |
| Add more course cards | HTML | Copy `.course-card` block & add new content |
| Adjust section padding | CSS | Edit `.courses-section { padding: 5rem 2rem; }` |
| Change hero background | HTML `.hero-layer` | Update `url('images/...')` |

---

## File Sizes (Minimal)
- `index.html` → ~8 KB
- `style.css` → ~20 KB
- Total (no images) → ~28 KB

---

## Notes
- **No JavaScript frameworks** — pure HTML/CSS/vanilla JS
- **Responsive** — works on mobile, tablet, desktop
- **Sticky navbar** — always visible while scrolling
- **CSS animations** — smooth, hardware-accelerated
- **Accessible** — semantic HTML, ARIA labels included

---

**Last Updated:** November 27, 2025
