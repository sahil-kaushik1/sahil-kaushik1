<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sahil Kaushik - Full Stack & Blockchain Developer</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0f1419 0%, #1a1e2e 50%, #16213e 100%);
            color: #e6edf3;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 50px;
            opacity: 0;
            animation: fadeInUp 1s ease forwards;
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: linear-gradient(45deg, #00d4ff, #090979);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            font-size: 60px;
            font-weight: bold;
            color: white;
            box-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
            animation: pulse 2s infinite;
        }

        .name {
            font-size: 3rem;
            font-weight: 700;
            background: linear-gradient(45deg, #00d4ff, #ff0080);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
        }

        .title {
            font-size: 1.3rem;
            color: #8b949e;
            margin-bottom: 20px;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .contact-link {
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 25px;
            text-decoration: none;
            color: #e6edf3;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .contact-link:hover {
            background: rgba(0, 212, 255, 0.2);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 212, 255, 0.3);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }

        .stats-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            opacity: 0;
            animation: fadeInUp 1s ease forwards;
        }

        .stats-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.2);
        }

        .card-title {
            font-size: 1.4rem;
            font-weight: 600;
            margin-bottom: 20px;
            color: #00d4ff;
        }

        .skill-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .skill-name {
            font-weight: 500;
        }

        .skill-bar {
            width: 60%;
            height: 8px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, #00d4ff, #ff0080);
            border-radius: 4px;
            width: 0%;
            animation: fillBar 2s ease forwards;
        }

        .chart-container {
            position: relative;
            height: 300px;
            margin-top: 20px;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 50px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            opacity: 0;
            animation: fadeInUp 1s ease forwards;
        }

        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(255, 0, 128, 0.2);
        }

        .project-title {
            font-size: 1.3rem;
            font-weight: 600;
            color: #ff0080;
            margin-bottom: 10px;
        }

        .project-description {
            color: #8b949e;
            line-height: 1.6;
            margin-bottom: 15px;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tech-tag {
            background: rgba(0, 212, 255, 0.2);
            color: #00d4ff;
            padding: 4px 12px;
            border-radius: 15px;
            font-size: 0.85rem;
            border: 1px solid rgba(0, 212, 255, 0.3);
        }

        .achievements {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 30px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 30px;
            opacity: 0;
            animation: fadeInUp 1s ease forwards;
        }

        .achievement-item {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            transition: all 0.3s ease;
        }

        .achievement-item:hover {
            background: rgba(255, 215, 0, 0.1);
            transform: translateX(10px);
        }

        .achievement-icon {
            font-size: 1.5rem;
            margin-right: 15px;
            color: #ffd700;
        }

        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(0, 212, 255, 0.5);
            border-radius: 50%;
            animation: float 6s infinite linear;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 30px rgba(0, 212, 255, 0.3); }
            50% { box-shadow: 0 0 50px rgba(0, 212, 255, 0.6); }
            100% { box-shadow: 0 0 30px rgba(0, 212, 255, 0.3); }
        }

        @keyframes fillBar {
            from { width: 0%; }
            to { width: var(--width); }
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        .typing {
            border-right: 2px solid #00d4ff;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { border-color: transparent; }
            51%, 100% { border-color: #00d4ff; }
        }

        @media (max-width: 768px) {
            .name { font-size: 2rem; }
            .title { font-size: 1.1rem; }
            .contact-links { flex-direction: column; align-items: center; }
            .stats-grid { grid-template-columns: 1fr; }
            .projects-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div class="floating-particles" id="particles"></div>
    
    <div class="container">
        <div class="header">
            <div class="profile-img">SK</div>
            <h1 class="name">Sahil Kaushik</h1>
            <p class="title typing" id="typing-text">Full Stack Developer & Blockchain Engineer</p>
            <div class="contact-links">
                <a href="mailto:sahilkaushik2444@gmail.com" class="contact-link">📧 Email</a>
                <a href="#" class="contact-link">🔗 LinkedIn</a>
                <a href="#" class="contact-link">🐙 GitHub</a>
                <a href="#" class="contact-link">🐦 Twitter</a>
            </div>
        </div>

        <div class="stats-grid">
            <div class="stats-card" style="animation-delay: 0.2s">
                <h3 class="card-title">🚀 Tech Stack Proficiency</h3>
                <div class="skill-item">
                    <span class="skill-name">JavaScript/TypeScript</span>
                    <div class="skill-bar">
                        <div class="skill-progress" style="--width: 95%; animation-delay: 0.5s"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <span class="skill-name">React/Next.js</span>
                    <div class="skill-bar">
                        <div class="skill-progress" style="--width: 92%; animation-delay: 0.7s"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <span class="skill-name">Solidity/Smart Contracts</span>
                    <div class="skill-bar">
                        <div class="skill-progress" style="--width: 88%; animation-delay: 0.9s"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <span class="skill-name">Node.js/Backend</span>
                    <div class="skill-bar">
                        <div class="skill-progress" style="--width: 85%; animation-delay: 1.1s"></div>
                    </div>
                </div>
                <div class="skill-item">
                    <span class="skill-name">Rust/Move</span>
                    <div class="skill-bar">
                        <div class="skill-progress" style="--width: 78%; animation-delay: 1.3s"></div>
                    </div>
                </div>
            </div>

            <div class="stats-card" style="animation-delay: 0.4s">
                <h3 class="card-title">📊 Development Focus</h3>
                <div class="chart-container">
                    <canvas id="focusChart"></canvas>
                </div>
            </div>

            <div class="stats-card" style="animation-delay: 0.6s">
                <h3 class="card-title">⛓️ Blockchain Expertise</h3>
                <div class="chart-container">
                    <canvas id="blockchainChart"></canvas>
                </div>
            </div>

            <div class="stats-card" style="animation-delay: 0.8s">
                <h3 class="card-title">📈 Activity Overview</h3>
                <div style="text-align: center; margin: 20px 0;">
                    <div style="display: inline-block; margin: 10px 20px;">
                        <div style="font-size: 2rem; font-weight: bold; color: #00d4ff;">12+</div>
                        <div style="color: #8b949e;">Projects</div>
                    </div>
                    <div style="display: inline-block; margin: 10px 20px;">
                        <div style="font-size: 2rem; font-weight: bold; color: #ff0080;">95%</div>
                        <div style="color: #8b949e;">Test Coverage</div>
                    </div>
                    <div style="display: inline-block; margin: 10px 20px;">
                        <div style="font-size: 2rem; font-weight: bold; color: #ffd700;">8.90</div>
                        <div style="color: #8b949e;">GPA</div>
                    </div>
                </div>
            </div>
        </div>

        <div class="achievements">
            <h3 class="card-title">🏆 Achievements & Recognition</h3>
            <div class="achievement-item">
                <span class="achievement-icon">🥇</span>
                <div>
                    <strong>Winner AI/ML Track</strong> - Hack-a-Harbour Technovate 6.0 (2025)
                </div>
            </div>
            <div class="achievement-item">
                <span class="achievement-icon">🥈</span>
                <div>
                    <strong>Runner-up Web3 Track</strong> - E-summit (2025)
                </div>
            </div>
            <div class="achievement-item">
                <span class="achievement-icon">🎓</span>
                <div>
                    <strong>Aspire Scholar</strong> - Merit-based Scholarship (2023)
                </div>
            </div>
            <div class="achievement-item">
                <span class="achievement-icon">💼</span>
                <div>
                    <strong>Multiple Internships</strong> - BlockseBlock, ThinkMile & Freelance Projects
                </div>
            </div>
        </div>

        <div class="projects-grid">
            <div class="project-card" style="animation-delay: 1s">
                <h3 class="project-title">Will-chain - Decentralized Land Registry</h3>
                <p class="project-description">
                    Blockchain platform for land ownership using ERC-721 NFTs and Ethereum smart contracts with comprehensive testing coverage.
                </p>
                <div class="project-tech">
                    <span class="tech-tag">Solidity</span>
                    <span class="tech-tag">Next.js</span>
                    <span class="tech-tag">Ethereum</span>
                    <span class="tech-tag">Foundry</span>
                </div>
            </div>

            <div class="project-card" style="animation-delay: 1.2s">
                <h3 class="project-title">Perpchain - Cross-Chain Trading</h3>
                <p class="project-description">
                    DeFi platform with isolated margin and automated liquidation mechanisms integrated with Chainlink oracles.
                </p>
                <div class="project-tech">
                    <span class="tech-tag">DeFi</span>
                    <span class="tech-tag">Chainlink</span>
                    <span class="tech-tag">React</span>
                    <span class="tech-tag">Web3</span>
                </div>
            </div>

            <div class="project-card" style="animation-delay: 1.4s">
                <h3 class="project-title">Stablecoin Protocol</h3>
                <p class="project-description">
                    Algorithmic stablecoin with WBTC/WETH collateral and automated liquidation ensuring market stability.
                </p>
                <div class="project-tech">
                    <span class="tech-tag">Stablecoin</span>
                    <span class="tech-tag">DeFi</span>
                    <span class="tech-tag">Economics</span>
                    <span class="tech-tag">Solidity</span>
                </div>
            </div>

            <div class="project-card" style="animation-delay: 1.6s">
                <h3 class="project-title">RAG - AI Document Retrieval</h3>
                <p class="project-description">
                    Document retrieval system combining vector embeddings with LLMs and semantic search using FAISS indexing.
                </p>
                <div class="project-tech">
                    <span class="tech-tag">AI/ML</span>
                    <span class="tech-tag">LangChain</span>
                    <span class="tech-tag">Python</span>
                    <span class="tech-tag">FAISS</span>
                </div>
            </div>

            <div class="project-card" style="animation-delay: 1.8s">
                <h3 class="project-title">Suicon - Sui Blockchain Wallet</h3>
                <p class="project-description">
                    Multi-signature wallet on Sui blockchain for group payment management with real-time transaction tracking.
                </p>
                <div class="project-tech">
                    <span class="tech-tag">Sui</span>
                    <span class="tech-tag">Move</span>
                    <span class="tech-tag">Multi-sig</span>
                    <span class="tech-tag">React</span>
                </div>
            </div>

            <div class="project-card" style="animation-delay: 2s">
                <h3 class="project-title">Lottery Foundry</h3>
                <p class="project-description">
                    Provably fair lottery using Chainlink VRF for verifiable random generation with automated prize distribution.
                </p>
                <div class="project-tech">
                    <span class="tech-tag">VRF</span>
                    <span class="tech-tag">Chainlink</span>
                    <span class="tech-tag">Foundry</span>
                    <span class="tech-tag">Testing</span>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Floating particles animation
        function createParticle() {
            const particle = document.createElement('div');
            particle.className = 'particle';
            particle.style.left = Math.random() * 100 + 'vw';
            particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
            particle.style.backgroundColor = `rgba(${Math.random() * 100 + 155}, ${Math.random() * 100 + 155}, 255, 0.8)`;
            document.getElementById('particles').appendChild(particle);

            setTimeout(() => {
                particle.remove();
            }, 6000);
        }

        setInterval(createParticle, 300);

        // Typing effect
        const texts = [
            'Full Stack Developer & Blockchain Engineer',
            'Smart Contract Developer',
            'DeFi Protocol Builder',
            'Web3 Innovation Enthusiast'
        ];
        let textIndex = 0;
        let charIndex = 0;
        let isDeleting = false;

        function typeEffect() {
            const currentText = texts[textIndex];
            const typingElement = document.getElementById('typing-text');
            
            if (isDeleting) {
                typingElement.textContent = currentText.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentText.substring(0, charIndex + 1);
                charIndex++;
            }

            if (!isDeleting && charIndex === currentText.length) {
                setTimeout(() => { isDeleting = true; }, 2000);
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                textIndex = (textIndex + 1) % texts.length;
            }

            setTimeout(typeEffect, isDeleting ? 50 : 100);
        }
        typeEffect();

        // Charts
        setTimeout(() => {
            // Focus Chart
            const focusCtx = document.getElementById('focusChart').getContext('2d');
            new Chart(focusCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Blockchain', 'Frontend', 'Backend', 'AI/ML'],
                    datasets: [{
                        data: [40, 30, 20, 10],
                        backgroundColor: [
                            'rgba(0, 212, 255, 0.8)',
                            'rgba(255, 0, 128, 0.8)',
                            'rgba(255, 215, 0, 0.8)',
                            'rgba(50, 255, 50, 0.8)'
                        ],
                        borderWidth: 2,
                        borderColor: 'rgba(255, 255, 255, 0.1)'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: { color: '#e6edf3' }
                        }
                    }
                }
            });

            // Blockchain Chart
            const blockchainCtx = document.getElementById('blockchainChart').getContext('2d');
            new Chart(blockchainCtx, {
                type: 'radar',
                data: {
                    labels: ['Ethereum', 'Solana', 'Sui', 'ICP', 'DeFi', 'Smart Contracts'],
                    datasets: [{
                        label: 'Expertise Level',
                        data: [95, 80, 75, 70, 90, 92],
                        backgroundColor: 'rgba(0, 212, 255, 0.2)',
                        borderColor: 'rgba(0, 212, 255, 1)',
                        pointBackgroundColor: 'rgba(255, 0, 128, 1)',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: 'rgba(255, 0, 128, 1)'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            beginAtZero: true,
                            max: 100,
                            ticks: { color: '#8b949e' },
                            grid: { color: 'rgba(255, 255, 255, 0.1)' },
                            pointLabels: { color: '#e6edf3' }
                        }
                    },
                    plugins: {
                        legend: { labels: { color: '#e6edf3' } }
                    }
                }
            });
        }, 1000);

        // Smooth scrolling and intersection observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.stats-card, .project-card, .achievements').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>
</html>
