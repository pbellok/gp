<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gp Advisory</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.1/font/bootstrap-icons.css">
    <link rel="icon" type="image/svg" href="images\gp-advisory-logo-notext.svg">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    
    <style>
    .navbar-brand img {
        height: 55px; 
        width: auto;
        object-fit: contain;
    }
    .hero-section {
        /* The linear-gradient adds a 30% dark overlay so the white text stays readable */
        background-image: linear-gradient(rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0.1)), url('images/angeline-wagner-F3XB46mgpm0-unsplash(1).jpg');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        /* Sets the hero height to at least 70% of the viewport height */
        min-height: 65vh;
        display: flex;
        align-items: center;
    }
    .custom-box {
        background-color: rgba(17, 113, 150, 0.8); 
        clip-path: polygon(40px 0, 100% 0, calc(100% - 40px) 100%, 0 100%);
        
        /* Base padding for mobile devices */
        padding: 1rem 2rem; 
    }
    /* Add extra wide horizontal padding for tablets and desktops */
    @media (min-width: 768px) {
        .custom-box {
            padding: 1.5rem 5rem; /* 3rem top/bottom, 6rem left/right */
        }
    }
    /* Specialization Blocks CSS */
    .specialization-block {
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        border-left: 5px solid #117196; /* Matches the hero custom-box color */
    }
    .specialization-block:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 20px rgba(0,0,0,0.08) !important;
    }
    
    /* Optional decorative shape for the image */
    .decorative-shape {
        position: absolute;
        bottom: -20px;
        left: -20px;
        width: 100px;
        height: 100px;
        background-color: #117196;
        clip-path: polygon(0 0, 100% 100%, 0 100%);
        z-index: -1;
    }
        /* Footer link hover effect */
    .hover-primary {
        transition: color 0.2s ease-in-out;
    }
    .hover-primary:hover {
        color: #117196 !important; /* Matches your custom-box blue */
    }
    /* Animated Hamburger CSS */
    .custom-toggler:focus {
        outline: none;
    }
    .animated-icon {
        width: 26px; height: 16px; position: relative; margin: 0; 
        transform: rotate(0deg); transition: .5s ease-in-out; cursor: pointer;
    }
    .animated-icon span {
        display: block; position: absolute; height: 2px; width: 100%; 
        background: #117196; border-radius: 2px; opacity: 1; left: 0; 
        transform: rotate(0deg); transition: .25s ease-in-out;
    }
    /* Positioning the 3 lines */
    .animated-icon span:nth-child(1) { top: 0px; }
    .animated-icon span:nth-child(2) { top: 7px; }
    .animated-icon span:nth-child(3) { top: 14px; }

    /* The animation when the menu is open (Bootstrap toggles aria-expanded automatically) */
    button[aria-expanded="true"] .animated-icon span:nth-child(1) {
        top: 7px; transform: rotate(135deg);
    }
    button[aria-expanded="true"] .animated-icon span:nth-child(2) {
        opacity: 0; left: -20px;
    }
    button[aria-expanded="true"] .animated-icon span:nth-child(3) {
        top: 7px; transform: rotate(-135deg);
    }
    /* --- Contact Us Button Base (Magenta Rectangle) --- */
    .contact-btn {
        background-color: #e00073; /* Magenta */
        color: #ffffff !important;
        border-radius: 0; /* Forces a rectangle */
        text-decoration: none;
        font-weight: 500;
        transition: background-color 0.3s ease;
    }

    .contact-btn:hover {
        background-color: #b3005c; /* Darker magenta on hover */
    }

    /* --- Desktop Styles (min-width: 992px) --- */
    @media (min-width: 992px) {
        .contact-btn {
            padding: 0.5rem 1.5rem;
            display: inline-block;
        }
    }

    /* --- Mobile (Collapsed) Styles (max-width: 991.98px) --- */
    @media (max-width: 991.98px) {
        /* Make the collapsed menu sit in front of all content */
        .navbar {
            position: relative; /* Ensures the absolute collapse positions relative to the nav */
        }
        
        .navbar-collapse {
            position: absolute;
            top: 100%; /* Pushes the menu exactly below the navbar header */
            left: 0;
            width: 100%;
            background-color: #f8f9fa; /* Matches the bg-light of your navbar */
            z-index: 1050; /* Keeps it above other page elements */
            box-shadow: 0 10px 15px rgba(0,0,0,0.1); /* Adds depth */
        }
        
        /* Style the list items as stacked blocks */
        .navbar-nav .nav-item {
            width: 100%;
            border-bottom: 1px solid #e9ecef; /* Separator lines between blocks */
        }
        
        .navbar-nav .nav-link {
            padding: 1rem 1.5rem !important;
            text-align: left !important; /* Left alignment looks better for block menus */
        }

        /* Make the Contact container and button full-width blocks */
        .mobile-contact-container {
            width: 100%;
            display: block !important;
        }

        .contact-btn {
            display: block;
            width: 100%;
            padding: 1rem 1.5rem;
            text-align: center;
        }
      }
      /* --- Dark Background Overlay for Mobile Menu --- */
    @media (max-width: 991.98px) {
        /* 1. Ensure the navbar header stays on top of the dark overlay */
        .navbar {
            position: relative;
            z-index: 1050; 
        }

        /* 2. Create the dark overlay when the button is clicked */
        body:has(.navbar-toggler[aria-expanded="true"])::after {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: rgba(0, 0, 0, 0.65); /* 65% opacity black */
            z-index: 1040; /* Places it just below the navbar (1050) */
            backdrop-filter: blur(3px); /* Optional: adds a slight blur to the background content */
        }
    }
    /* --- Testimonial Postcard Slider --- */
    .postcard-wrapper {
        background-color: #ffffff;
        border-radius: 12px;
        box-shadow: 0 15px 35px rgba(0,0,0,0.06);
        position: relative;
        border-top: 5px solid #e00073; /* Magenta accent */
        padding: 3rem 2rem;
        margin: 1rem auto;
        max-width: 800px;

        /* --- THE FIX: Use a fixed height to completely lock the size --- */
        height: 400px; 
        
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    /* --- Taller fixed height for mobile to accommodate text wrapping --- */
    @media (max-width: 767.98px) {
        .postcard-wrapper {
            height: 480px; 
            padding: 2rem 1.5rem; /* Slightly tighter padding for mobile screens */
        }
    }
    
    .quote-icon {
        font-size: 3rem;
        color: rgba(17, 113, 150, 0.2); /* Light transparent brand blue */
        position: absolute;
        top: 15px;
        left: 25px;
        line-height: 1;
    }

    /* Customize Bootstrap Carousel Indicators */
    #testimonialCarousel .carousel-indicators {
        bottom: -50px;
    }
    #testimonialCarousel .carousel-indicators [data-bs-target] {
        background-color: #cbd5e1;
        width: 12px;
        height: 12px;
        border-radius: 50%;
        margin: 0 6px;
    }
    #testimonialCarousel .carousel-indicators .active {
        background-color: #117196; /* Brand Blue */
    }

    /* Adjust Carousel Controls to sit nicely outside the card on desktop */
    #testimonialCarousel .carousel-control-prev,
    #testimonialCarousel .carousel-control-next {
        width: 10%;
        opacity: 0.7;
    }
    #testimonialCarousel .carousel-control-prev:hover,
    #testimonialCarousel .carousel-control-next:hover {
        opacity: 1;
    }
    /* --- Services Grid CSS --- */
    .service-card {
        background: #ffffff;
        border-radius: 10px;
        transition: all 0.3s ease;
        border: 1px solid #f0f0f0;
        border-top: 4px solid #117196; /* Brand blue border */
        height: 100%;
    }
    
    .service-card:hover {
        transform: translateY(-8px);
        box-shadow: 0 15px 30px rgba(0,0,0,0.08) !important;
        border-top-color: #e00073; /* Changes to magenta on hover */
    }

    .service-icon-box {
        width: 65px;
        height: 65px;
        background-color: rgba(17, 113, 150, 0.1); /* Light transparent blue */
        color: #117196;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.8rem;
        margin-bottom: 1.5rem;
        transition: all 0.3s ease;
    }

    /* Invert icon colors on hover */
    .service-card:hover .service-icon-box {
        background-color: #e00073;
        color: #ffffff;
    }
    /* You can delete this part! */
    .how-we-work-title {
        border: 2px solid #117196; 
        border-radius: 8px;
        background-color: #ffffff;
    }

    .step-box-left {
        background-color: #117196; /* Brand blue */
        color: #ffffff;
        border-radius: 8px;
        box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        min-height: 100px;
        transition: transform 0.3s ease;
    }
    
    .step-box-right {
        background-color: #ffffff;
        border: 1px solid #e9ecef;
        border-left: 5px solid #e00073; /* Magenta accent */
        border-radius: 8px;
        box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        min-height: 100px;
        transition: transform 0.3s ease;
    }

    /* Small hover effect to make the steps feel interactive */
    .step-row:hover .step-box-left,
    .step-row:hover .step-box-right {
        transform: translateY(-4px);
    }
    /* --- Office Location Blocks CSS --- */
    .office-block {
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        border-left: 5px solid #117196; /* Brand blue border */
    }
    .office-block:hover {
        transform: translateX(5px); /* Slides slightly to the right on hover */
        box-shadow: 0 10px 20px rgba(0,0,0,0.08) !important;
    }
    
    .office-icon {
        color: #e00073; /* Magenta accent for icons */
        font-size: 1.1rem;
        margin-right: 0.5rem;
    }
    </style>
</head>
<body>

<nav class="navbar navbar-expand-lg navbar-light bg-light shadow-sm">
  <div class="container">
    
    <a class="navbar-brand" href="index.html">
      <img src="images\gp-advisory-logo-horizontal.svg" alt="GP Advisory">
    </a>

    <button class="navbar-toggler border-0 shadow-none custom-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarContent" aria-controls="navbarContent" aria-expanded="false" aria-label="Toggle navigation">
  <div class="animated-icon">
    <span></span><span></span><span></span>
  </div>
</button>

    <div class="collapse navbar-collapse" id="navbarContent">
      
      <ul class="navbar-nav mx-auto mb-2 mb-lg-0">
        <li class="nav-item mx-lg-4">
          <a class="nav-link" href="#who-we-are">Who We Are</a>
        </li>
        <li class="nav-item mx-lg-4">
          <a class="nav-link" href="#what-we-do">What We Do</a>
        </li>
        <li class="nav-item mx-lg-4">
          <a class="nav-link" href="#where-to-find-us">Where To Find Us</a>
        </li>
      </ul>

    <div class="d-flex mobile-contact-container">
      <a href="#contact-section" class="btn contact-btn border-0">Contact Us</a>
    </div>

    </div>
  </div>
</nav>

<div id="who-we-are" class="page-section">
  <header id="mission" class="hero-section text-white">
    <div class="container">
      <div class="row align-items-center custom-box">
        
        <div class="col-md-5 mb-4 mb-md-0">
          <h1 class="display-3 fw-bold">Our Mission</h1>
          <div class="bg-white rounded mt-3" style="width: 210px; height: 5px;"></div>
        </div>

        <div class="col-md-7">
          <p class="lead fs-3 mb-0">
            We provide strategic, data-driven advisory services that empower businesses to navigate complex challenges, optimize their operations, and achieve sustainable growth.
          </p>
        </div>

      </div>
    </div>
  </header>

  <section id="specializations" class="py-5 mt-md-4">
    <div class="container py-4">
      
      <div class="row mb-5">
        <div class="col-12 text-center text-lg-start">
          <h2 class="display-5 fw-bold" style="color: #117196;">Our Specializations</h2>
          <p class="text-muted lead">Tailored expertise to navigate your business challenges.</p>
        </div>
      </div>

      <div class="row align-items-center g-5">
        
        <div class="col-lg-6">
          <div class="d-flex flex-column gap-4">
            
            <div class="specialization-block bg-white p-4 rounded shadow-sm">
              <h4 class="fw-bold mb-2">Strategic Planning</h4>
              <p class="text-muted mb-0">We help you define clear, actionable roadmaps to achieve long-term market dominance and operational efficiency.</p>
            </div>

            <div class="specialization-block bg-white p-4 rounded shadow-sm">
              <h4 class="fw-bold mb-2">Financial Advisory</h4>
              <p class="text-muted mb-0">Optimize your capital structure, manage risks, and maximize shareholder value with our expert financial insights.</p>
            </div>

            <div class="specialization-block bg-white p-4 rounded shadow-sm">
              <h4 class="fw-bold mb-2">Digital Transformation</h4>
              <p class="text-muted mb-0">Modernize your legacy systems and integrate cutting-edge tech to streamline workflows and boost productivity.</p>
            </div>

          </div>
        </div>

        <div class="col-lg-6">
          <div class="position-relative z-1">
            <img src="https://images.unsplash.com/photo-1600880292203-757bb62b4baf?q=80&w=1000&auto=format&fit=crop" alt="Business Specializations" class="img-fluid rounded-4 shadow-lg w-100" style="object-fit: cover; min-height: 450px;">
            
            <div class="decorative-shape d-none d-lg-block"></div>
          </div>
        </div>

      </div>
    </div>
  </section>
  <section class="py-5 bg-light mt-md-4">
    <div class="container py-4">
      
      <div class="row mb-4">
        <div class="col-12 text-center">
          <h2 class="display-5 fw-bold" style="color: #117196;">Our Partners & Projects</h2>
          <p class="text-muted lead">The impact we've made alongside our partners.</p>
        </div>
      </div>

      <div class="row justify-content-center">
        <div class="col-lg-10">
          
          <div id="testimonialCarousel" class="carousel carousel-dark slide" data-bs-ride="carousel">
            
            <div class="carousel-indicators">
              <button type="button" data-bs-target="#testimonialCarousel" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
              <button type="button" data-bs-target="#testimonialCarousel" data-bs-slide-to="1" aria-label="Slide 2"></button>
              <button type="button" data-bs-target="#testimonialCarousel" data-bs-slide-to="2" aria-label="Slide 3"></button>
            </div>

            <div class="carousel-inner pb-5">
              
              <div class="carousel-item active" data-bs-interval="7000">
                <div class="postcard-wrapper text-center">
                  <span class="quote-icon">❝</span>
                  <h4 class="fw-bold mb-4" style="color: #117196;">European Market Expansion</h4>
                  <p class="fs-5 fst-italic text-muted mb-4 px-md-4">
                    "GP Advisory provided us with an incredibly precise roadmap for our European launch. Their data-driven approach allowed us to optimize our operational costs by 20% while hitting all our strategic milestones six months ahead of schedule."
                  </p>
                  <hr class="w-25 mx-auto mb-4" style="border-color: #117196;">
                  <h6 class="fw-bold mb-1">Alessandro Rossi</h6>
                  <p class="small text-muted mb-0">CEO, TechLogistics Solutions</p>
                </div>
              </div>

              <div class="carousel-item" data-bs-interval="7000">
                <div class="postcard-wrapper text-center">
                  <span class="quote-icon">❝</span>
                  <h4 class="fw-bold mb-4" style="color: #117196;">Digital Workflow Integration</h4>
                  <p class="fs-5 fst-italic text-muted mb-4 px-md-4">
                    "The digital transformation strategies implemented by the GP team completely revitalized our legacy systems. We experienced a seamless transition and a tremendous boost in cross-departmental productivity."
                  </p>
                  <hr class="w-25 mx-auto mb-4" style="border-color: #117196;">
                  <h6 class="fw-bold mb-1">Sarah Jenkins</h6>
                  <p class="small text-muted mb-0">CTO, FinServe Global</p>
                </div>
              </div>

              <div class="carousel-item" data-bs-interval="7000">
                <div class="postcard-wrapper text-center">
                  <span class="quote-icon">❝</span>
                  <h4 class="fw-bold mb-4" style="color: #117196;">Capital Restructuring</h4>
                  <p class="fs-5 fst-italic text-muted mb-4 px-md-4">
                    "Navigating a complex financial restructure is never easy, but GP Advisory brought clarity and immense expertise to the table. They protected our core assets and maximized our shareholder value beautifully."
                  </p>
                  <hr class="w-25 mx-auto mb-4" style="border-color: #117196;">
                  <h6 class="fw-bold mb-1">Michael Chang</h6>
                  <p class="small text-muted mb-0">Managing Partner, Apex Capital</p>
                </div>
              </div>

            </div>

            <button class="carousel-control-prev" type="button" data-bs-target="#testimonialCarousel" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#testimonialCarousel" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Next</span>
            </button>

          </div>
        </div>
      </div>
      
    </div>
  </section>
</div>

<div id="what-we-do" class="page-section d-none">
  <section class="py-5 mt-md-4">
    <section id="services" class="py-5 bg-white">
      <div class="container py-4">
        
        <div class="row mb-5">
          <div class="col-12 text-center">
            <h2 class="display-5 fw-bold" style="color: #117196;">Our Core Services</h2>
            <p class="text-muted lead mx-auto" style="max-width: 700px;">
              Comprehensive advisory solutions designed to guide your business through every phase of growth and complexity.
            </p>
          </div>
        </div>

        <div class="row g-4">
          
          <div class="col-12 col-md-6 col-lg-4">
            <div class="service-card p-4 shadow-sm">
              <div class="service-icon-box">
                <i class="bi bi-bullseye"></i>
              </div>
              <h4 class="fw-bold mb-3">Corporate Strategy</h4>
              <p class="text-muted mb-0">We partner with executives to design robust business strategies that identify new revenue streams and secure competitive advantages.</p>
            </div>
          </div>

          <div class="col-12 col-md-6 col-lg-4">
            <div class="service-card p-4 shadow-sm">
              <div class="service-icon-box">
                <i class="bi bi-briefcase"></i>
              </div>
              <h4 class="fw-bold mb-3">Mergers & Acquisitions</h4>
              <p class="text-muted mb-0">End-to-end M&A support, from target identification and rigorous due diligence to seamless post-merger integration.</p>
            </div>
          </div>

          <div class="col-12 col-md-6 col-lg-4">
            <div class="service-card p-4 shadow-sm">
              <div class="service-icon-box">
                <i class="bi bi-graph-up-arrow"></i>
              </div>
              <h4 class="fw-bold mb-3">Financial Advisory</h4>
              <p class="text-muted mb-0">Expert guidance on capital structuring, risk management, and financial forecasting to maximize your shareholder value.</p>
            </div>
          </div>

          <div class="col-12 col-md-6 col-lg-4">
            <div class="service-card p-4 shadow-sm">
              <div class="service-icon-box">
                <i class="bi bi-globe2"></i>
              </div>
              <h4 class="fw-bold mb-3">Market Expansion</h4>
              <p class="text-muted mb-0">Data-backed roadmaps for entering new geographic markets or launching new product lines with minimized risk.</p>
            </div>
          </div>

          <div class="col-12 col-md-6 col-lg-4">
            <div class="service-card p-4 shadow-sm">
              <div class="service-icon-box">
                <i class="bi bi-gear-wide-connected"></i>
              </div>
              <h4 class="fw-bold mb-3">Operational Excellence</h4>
              <p class="text-muted mb-0">We analyze your supply chain and internal workflows to eliminate inefficiencies and reduce operational costs.</p>
            </div>
          </div>

          <div class="col-12 col-md-6 col-lg-4">
            <div class="service-card p-4 shadow-sm">
              <div class="service-icon-box">
                <i class="bi bi-cpu"></i>
              </div>
              <h4 class="fw-bold mb-3">Digital Transformation</h4>
              <p class="text-muted mb-0">Modernize legacy systems and integrate scalable technologies to future-proof your business operations.</p>
            </div>
          </div>

        </div>
      </div>
    </section>
  </section>
    <section class="py-5 bg-light">
    <div class="container py-4">
      
      <div class="row mb-5">
        <div class="col-12 text-center">
          <h2 class="display-5 fw-bold" style="color: #117196;">How we work</h2>
        </div>
      </div>

      <div class="row mb-4 g-3 step-row">
        <div class="col-12 col-md-3">
          <div class="step-box-left p-4 d-flex align-items-center justify-content-center h-100">
            <h5 class="mb-0 fw-bold">Phase 1</h5>
          </div>
        </div>
        <div class="col-12 col-md-6">
          <div class="step-box-right p-4 d-flex align-items-center h-100">
            <p class="text-muted mb-0">Initial consultation and comprehensive business audit to identify key growth areas, market opportunities, and operational bottlenecks.</p>
          </div>
        </div>
      </div>

      <div class="row mb-4 g-3 step-row">
        <div class="col-12 col-md-3 offset-md-1">
          <div class="step-box-left p-4 d-flex align-items-center justify-content-center h-100">
            <h5 class="mb-0 fw-bold">Phase 2</h5>
          </div>
        </div>
        <div class="col-12 col-md-6">
          <div class="step-box-right p-4 d-flex align-items-center h-100">
            <p class="text-muted mb-0">Developing a tailored strategic roadmap aligned with your long-term corporate objectives and current market realities.</p>
          </div>
        </div>
      </div>

      <div class="row mb-4 g-3 step-row">
        <div class="col-12 col-md-3 offset-md-2">
          <div class="step-box-left p-4 d-flex align-items-center justify-content-center h-100">
            <h5 class="mb-0 fw-bold">Phase 3</h5>
          </div>
        </div>
        <div class="col-12 col-md-6">
          <div class="step-box-right p-4 d-flex align-items-center h-100">
            <p class="text-muted mb-0">Execution and implementation, working closely with your leadership team to integrate new processes and technologies seamlessly.</p>
          </div>
        </div>
      </div>

      <div class="row mb-4 g-3 step-row">
        <div class="col-12 col-md-3 offset-md-3">
          <div class="step-box-left p-4 d-flex align-items-center justify-content-center h-100">
            <h5 class="mb-0 fw-bold">Phase 4</h5>
          </div>
        </div>
        <div class="col-12 col-md-6">
          <div class="step-box-right p-4 d-flex align-items-center h-100">
            <p class="text-muted mb-0">Continuous monitoring, performance tracking, and agile adjustments to ensure sustainable success and maximum ROI.</p>
          </div>
        </div>
      </div>

    </div>
  </section>
</div>

<div id="where-to-find-us" class="page-section d-none">
  
  <section id="global-network" class="py-5 mt-md-4">
    <div class="container py-4">
      
      <div class="row mb-5 text-center text-lg-start">
        <div class="col-12">
          <h2 class="display-5 fw-bold" style="color: #117196;">Our Offices</h2>
          <p class="text-muted lead">Global presence, local expertise. Find us at our key international hubs.</p>
        </div>
      </div>

      <div class="row align-items-center g-5">
        
        <div class="col-lg-5">
          <div class="d-flex flex-column gap-4">
            
            <div class="office-block p-4 bg-white rounded shadow-sm">
              <h4 class="fw-bold mb-3">Chiasso Headquarters</h4>
              <p class="text-muted mb-2 d-flex align-items-start">
                <i class="bi bi-geo-alt-fill office-icon mt-1"></i> 
                <span>Corso San Gottardo 39<br>6830 Chiasso, Switzerland</span>
              </p>
              <p class="text-muted mb-0 d-flex align-items-center">
                <i class="bi bi-telephone-fill office-icon"></i> 
                <span>+41 91 123 45 67</span>
              </p>
            </div>

            <div class="office-block p-4 bg-white rounded shadow-sm">
              <h4 class="fw-bold mb-3">Monza Office</h4>
              <p class="text-muted mb-2 d-flex align-items-start">
                <i class="bi bi-geo-alt-fill office-icon mt-1"></i> 
                <span>Via Manzoni 37<br>20900 Monza MB, Italy</span>
              </p>
              <p class="text-muted mb-0 d-flex align-items-center">
                <i class="bi bi-telephone-fill office-icon"></i> 
                <span>+39 02 1234 5678</span>
              </p>
            </div>

            <div class="office-block p-4 bg-white rounded shadow-sm">
              <h4 class="fw-bold mb-3">Dubai Office</h4>
              <p class="text-muted mb-2 d-flex align-items-start">
                <i class="bi bi-geo-alt-fill office-icon mt-1"></i> 
                <span>1 Canada Square, Canary Wharf<br>Dubai E14 5AB, UAE</span>
              </p>
              <p class="text-muted mb-0 d-flex align-items-center">
                <i class="bi bi-telephone-fill office-icon"></i> 
                <span>+971 20 7123 4567</span>
              </p>
            </div>

          </div>
        </div>

        <div class="col-lg-7">
          <div class="position-relative z-1">
            <img src="images\MapChart_Offices.svg" alt="Our Global Offices" class="img-fluid rounded-4 shadow-lg w-100" style="object-fit: contain;">
            
            <div class="decorative-shape d-none d-lg-block" style="background-color: #e00073; bottom: -20px; right: -20px; left: auto; clip-path: polygon(100% 0, 100% 100%, 0 100%);"></div>
          </div>
        </div>

      </div>
    </div>
  </section>

  <div id="contact-section" class="row mt-5 pt-5 border-top">
    <div class="col-lg-8 mx-auto text-center mb-5">
      <h3 class="display-6 fw-bold" style="color: #117196;">Get in Touch</h3>
      <p class="text-muted lead">Have a specific challenge in mind? Send us a message and our advisory team will reach out to you shortly.</p>
    </div>
  </div>
      <div class="row justify-content-center pb-5">
        <div class="col-lg-8">
          
          <div class="bg-white p-4 p-md-5 rounded shadow-sm" style="border-top: 5px solid #e00073;">
            
            <form action="https://formspree.io/f/xwvrpaze" method="POST">
              <div class="row g-4">
                
                <div class="col-md-6">
                  <label for="fullName" class="form-label fw-bold" style="color: #117196;">Full Name *</label>
                  <input type="text" class="form-control bg-light border-0 py-2" id="fullName" name="name" placeholder="John Doe" required>
                </div>
                
                <div class="col-md-6">
                  <label for="emailAddress" class="form-label fw-bold" style="color: #117196;">Email Address *</label>
                  <input type="email" class="form-control bg-light border-0 py-2" id="emailAddress" name="email" placeholder="john@company.com" required>
                </div>

                <div class="col-md-6">
                  <label for="companyName" class="form-label fw-bold" style="color: #117196;">Company Name</label>
                  <input type="text" class="form-control bg-light border-0 py-2" id="companyName" name="company" placeholder="Your Organization">
                </div>

                <div class="col-md-6">
                  <label for="phoneNumber" class="form-label fw-bold" style="color: #117196;">Phone Number</label>
                  <input type="tel" class="form-control bg-light border-0 py-2" id="phoneNumber" name="phone" placeholder="+41 91 000 00 00">
                </div>
                
                <div class="col-12">
                  <label for="serviceInterest" class="form-label fw-bold" style="color: #117196;">How can we help you?</label>
                  <select class="form-select bg-light border-0 py-2" id="serviceInterest" name="subject">
                    <option value="General Inquiry" selected>General Inquiry</option>
                    <option value="Corporate Strategy">Corporate Strategy</option>
                    <option value="Mergers & Acquisitions">Mergers & Acquisitions</option>
                    <option value="Financial Advisory">Financial Advisory</option>
                    <option value="Digital Transformation">Digital Transformation</option>
                    <option value="Other">Other</option>
                  </select>
                </div>
                
                <div class="col-12">
                  <label for="message" class="form-label fw-bold" style="color: #117196;">Your Message *</label>
                  <textarea class="form-control bg-light border-0 py-2" id="message" name="message" rows="5" placeholder="Tell us about your project or challenge..." required></textarea>
                </div>
                
                <div class="col-12 text-center mt-4">
                  <button type="submit" class="btn contact-btn px-5 py-3 w-100 fw-bold text-uppercase" style="letter-spacing: 1px;">Send Message</button>
                </div>
                
              </div>
            </form>

          </div>
        </div>
      </div>
</div>




<footer class="bg-light pt-5 pb-4 border-top mt-5">
  <div class="container">
    <div class="row">
      
      <div class="col-12 col-lg-5 mb-4 mb-lg-0">
        <a class="navbar-brand" href="#who-we-are">
          <img src="images\gp-advisory-logo.svg" alt="GP Advisory" class="mb-3" style="max-height: 55px; width: auto; object-fit: contain;">
        </a>
        <p class="text-muted small mb-0">
          &copy; 2026 GP Advisory & Investments SAGL
        </p>
      </div>

      <div class="col-12 col-md-4 col-lg-2 offset-lg-1 mb-4 mb-lg-0">
        <ul class="list-unstyled small"> 
          <li class="mb-3"><a href="#mission" class="text-decoration-none text-dark hover-primary footer-link">Our mission</a></li>
          <li class="mb-3"><a href="#specializations" class="text-decoration-none text-dark hover-primary footer-link">Our specialization</a></li>
          <li class="mb-3"><a href="#clients-projects" class="text-decoration-none text-dark hover-primary footer-link">Our clients</a></li>
        </ul>
      </div>

      <div class="col-12 col-md-4 col-lg-2 mb-4 mb-lg-0">
        <ul class="list-unstyled small">
          <li class="mb-3"><a href="#services" class="text-decoration-none text-dark hover-primary footer-link">Our Services</a></li>
          <li class="mb-3"><a href="#how-we-work" class="text-decoration-none text-dark hover-primary footer-link">How we work</a></li>
        </ul>
      </div>

      <div class="col-12 col-md-4 col-lg-2 mb-4 mb-lg-0">
        <ul class="list-unstyled small">
          <li class="mb-3"><a href="#global-network" class="text-decoration-none text-dark hover-primary footer-link">Our Global Network</a></li>
          <li class="mb-3"><a href="#contact-section" class="text-decoration-none text-dark hover-primary footer-link">Contact Us</a></li>
        </ul>
      </div>

    </div>
  </div>
</footer>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
<script>
  document.addEventListener("DOMContentLoaded", function () {
    // Select all the links inside the menu, including the contact button
    const navLinks = document.querySelectorAll('.nav-link, .contact-btn');
    const navbarToggler = document.querySelector('.navbar-toggler');
    const navbarCollapse = document.getElementById('navbarContent');

    // Loop through each link
    navLinks.forEach(function (link) {
      link.addEventListener('click', function () {
        // If the mobile menu is currently open, click the hamburger button to close it
        if (navbarCollapse.classList.contains('show')) {
          navbarToggler.click();
        }
      });
    });
  });
</script>
<script>
  document.addEventListener("DOMContentLoaded", function () {
    const navLinks = document.querySelectorAll('.nav-link, .navbar-brand, .contact-btn, .footer-link');
    const sections = document.querySelectorAll('.page-section');
    const navbarToggler = document.querySelector('.navbar-toggler');
    const navbarCollapse = document.getElementById('navbarContent');

    navLinks.forEach(function (link) {
      link.addEventListener('click', function (e) {
        const targetId = this.getAttribute('href');

        if (targetId && targetId.startsWith('#')) {
          e.preventDefault();

          const targetElement = document.querySelector(targetId);

          if (targetElement) {
            // Find which main page this element lives inside (or if it IS the main page)
            const parentPage = targetElement.closest('.page-section');

            if (parentPage) {
              // Hide all pages, then unhide the correct one
              sections.forEach(function (sec) {
                sec.classList.add('d-none');
              });
              parentPage.classList.remove('d-none');
            }

            // Close the mobile menu if it is currently open
            if (navbarCollapse.classList.contains('show')) {
              navbarToggler.click();
            }

            // Smart Scrolling: 
            // If they clicked a main menu link, scroll to top. 
            // If they clicked Contact Us, scroll down to the form.
            if (targetElement.classList.contains('page-section')) {
              window.scrollTo({ top: 0, behavior: 'smooth' });
            } else {
              // Uses a tiny timeout to ensure the page has finished unhiding before scrolling
              setTimeout(() => {
                targetElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
              }, 50);
            }
          }
        }
      });
    });
  });
</script>
</body>
</html>
