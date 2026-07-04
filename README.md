## React Application Deployment on AWS EC2 Using Nginx

##  Project Overview

This project demonstrates a complete **end-to-end deployment of a production-ready React application** on an **AWS EC2 Ubuntu instance**, using **Nginx as a web server**.

The objective of this project is to simulate a real-world **DevOps deployment workflow**, where a frontend application is built, hosted, and served through a cloud-based Linux server.

The React application is built locally or on the server, optimized for production, and served using Nginx to ensure high performance, scalability, and reliability.

---

##  Project Goals

The main goals of this project include:

- Deploy a React application on a cloud-based Linux server (AWS EC2)
- Configure and manage an Ubuntu server environment
- Install and manage Node.js and npm for building the application
- Configure Nginx as a reverse proxy / static web server
- Build a production-ready React application
- Host and serve the application over HTTP using EC2 public IP
- Demonstrate DevOps and deployment fundamentals

---

## Technologies Used

- **Amazon Web Services (AWS EC2)**
- **Ubuntu Linux**
- **React.js**
- **Node.js**
- **npm (Node Package Manager)**
- **Nginx Web Server**
- **Git & GitHub**
- **Bash / Linux CLI**

---

##  Architecture Overview


Developer Machine / EC2 Server
│
├── React Application (Source Code)
│
├── Node.js (Build Environment)
│
├── Production Build (React build/)
│
└── Nginx Web Server
└── Serves static files to users


Users access the application through:


http://EC2-PUBLIC-IP


---

## ⚙️ Prerequisites

Before deploying the application, ensure the following:

- AWS account is active
- EC2 Ubuntu instance is launched
- Security Group allows:
  - SSH (Port 22)
  - HTTP (Port 80)
- Git is installed on the server
- Basic Linux command knowledge

---

### 1️⃣ Connect to EC2 Instance

```bash
2️⃣ Update System Packages
sudo apt update && sudo apt upgrade -y

Keeping the system updated ensures security and stability.

3️⃣ Install Node.js and npm
sudo apt install nodejs npm -y


node -v
npm -v
4️⃣ Install Nginx Web Server
sudo apt install nginx -y


sudo systemctl start nginx

Check status:

systemctl status nginx
5️⃣ Clone the Repository
git clone https://github.com/teajo99/React-App.git
cd React-App
6️⃣ Install Dependencies
npm install

This installs all required project dependencies defined in package.json.

7️⃣ Build the React Application
npm run build

This generates an optimized production build inside the build/ folder.

8️⃣ Deploy Build to Nginx Directory
sudo rm -rf /var/www/html/*
sudo cp -r build/* /var/www/html/

This step ensures Nginx serves the latest version of the application.

9️⃣ Configure Nginx

Edit Nginx default configuration:

sudo nano /etc/nginx/sites-available/default

Add the following configuration:

server {
    listen 80;
    server_name _;

    root /var/www/html;
    index index.html;

    location / {
        try_files $uri /index.html;
    }

    error_page 404 /index.html;
}

Restart Nginx:

sudo systemctl restart nginx
## Application Access

Once deployment is complete, access the application using:

http://<EC2-PUBLIC-IP>

The React application should now be live and accessible globally.

## Security Considerations
Ensure EC2 Security Groups only expose required ports
Use SSH key-based authentication instead of passwords
Regularly update system packages
Avoid exposing sensitive environment variables
## Key Learning Outcomes

Through this project, the following skills were developed:

Linux server management on AWS EC2
Deployment of frontend applications in production environments
Working with Nginx as a static web server
Understanding of React production builds
Git and GitHub version control workflow
Real-world DevOps deployment practices
## Possible Improvements

Future enhancements for this project:

Add CI/CD pipeline using GitHub Actions
Automate deployment using scripts
Add domain name with SSL (HTTPS using Let’s Encrypt)
Containerize application using Docker
Add monitoring and logging tools
## Author

teajo99
Cloud & DevOps Engineer

 ## Project Status

✔ Successfully deployed on AWS EC2
✔ React production build served via Nginx
✔ GitHub version-controlled project


---

#  STEP 3 — Save & exit

- `CTRL + X`
- `Y`
- `ENTER`

---

#  STEP 4 — Push to GitHub

```bash
git add README.md
git commit -m "add professional README"
git push origin mainsudo systemctl enable nginx
Start and enable Nginx:
Verify installation:
ssh -i your-key.pem ubuntu@<EC2-PUBLIC-IP>

