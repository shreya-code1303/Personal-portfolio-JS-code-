# Personal-portfolio-JS-code-


document.querySelectorAll('nav ul li a').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
        e.preventDefault();
        const targetId = this.getAttribute('href').substring(1);
        const targetElement = document.getElementById(targetId);

        window.scrollTo({
            top: targetElement.offsetTop - 50, 
            behavior: 'smooth'
        });
    });
});

const form = document.querySelector('form');

form.addEventListener('submit', function(e) {
    e.preventDefault(); // Prevent the default form submission

    alert('Thank you for reaching out! Your message has been sent.');

    // Reset the form
    form.reset();
});

// 3D Rotation Animation Control
const profileImg = document.querySelector('.profile-img');

profileImg.addEventListener('mouseover', () => {
    profileImg.style.animationPlayState = 'paused';
});

profileImg.addEventListener('mouseout', () => {
    profileImg.style.animationPlayState = 'running';
});

// Toggle Dark/Light Mode 
const toggleThemeButton = document.createElement('button');
toggleThemeButton.textContent = 'Toggle Dark/Light Mode';
toggleThemeButton.style.position = 'fixed';
toggleThemeButton.style.bottom = '20px';
toggleThemeButton.style.right = '20px';
toggleThemeButton.style.padding = '10px 20px';
toggleThemeButton.style.background = '#ffcc00';
toggleThemeButton.style.border = 'none';
toggleThemeButton.style.borderRadius = '5px';
toggleThemeButton.style.cursor = 'pointer';
toggleThemeButton.style.zIndex = '1000';
document.body.appendChild(toggleThemeButton);

toggleThemeButton.addEventListener('click', () => {
    document.body.classList.toggle('light-mode');
});

document.querySelector('form').addEventListener('submit', function(event) {
    event.preventDefault(); // Prevent the default form submission

    // Collect form data
    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const message = document.getElementById('message').value;

    // Send the email using EmailJS
    emailjs.send("pupe1TP4zHsGUHelb", "template_s0zysir", {
        from_name: name,
        from_email: email,
        message: message
    })
    .then(function(response) {
        console.log('SUCCESS!', response.status, response.text);
        alert('Message sent successfully!');
    }, function(error) {
        console.log('FAILED...', error);
        alert('Failed to send the message. Please try again later.');
    });

    // Optionally reset the form after submission
    event.target.reset();
});
