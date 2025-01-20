# Docker Setup

### **Step 1: Install Docker on Different Environments**

#### **For Windows:**
1. **Download Docker Desktop**  
   Go to the official Docker website: [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop) and download the installer for Windows.
   
2. **Install Docker Desktop**  
   Run the installer and follow the on-screen instructions. During installation, ensure that the required virtualization features (Hyper-V, WSL 2) are enabled.

3. **Run Docker Desktop**  
   After installation, launch Docker Desktop. Docker will run in the background, and you'll see the Docker icon in the system tray.

4. **Verify Installation**  
   Open PowerShell or Command Prompt and run:
   ```bash
   docker --version
   ```
   You should see the Docker version if it's installed correctly.

#### **For macOS:**
1. **Download Docker Desktop**  
   Visit the Docker website: [Docker Desktop for Mac](https://www.docker.com/products/docker-desktop) and download the macOS version.

2. **Install Docker Desktop**  
   Open the `.dmg` file and drag the Docker icon to your Applications folder.

3. **Run Docker Desktop**  
   Open Docker from your Applications folder. Docker will start, and you'll see the Docker icon in the menu bar.

4. **Verify Installation**  
   Open Terminal and run:
   ```bash
   docker --version
   ```
   This will confirm that Docker is installed.

#### **For Linux (Ubuntu Example):**
1. **Update APT package index**  
   Open a terminal and run:
   ```bash
   sudo apt update
   ```

2. **Install dependencies**  
   Install required packages for HTTPS and apt over HTTPS:
   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Add Docker’s official GPG key**  
   Run this to add Docker's GPG key:
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

4. **Set up the Docker repository**  
   Add Docker's official repository:
   ```bash
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

5. **Install Docker Engine**  
   Update the package index again and install Docker:
   ```bash
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io
   ```

6. **Verify Installation**  
   Check if Docker is running:
   ```bash
   sudo systemctl status docker
   ```

   Also, verify the installation by running:
   ```bash
   docker --version
   ```

---

### **Step 2: Running a Simple Docker Container**

Now that Docker is installed on your system, let’s run a simple container to ensure everything is working.

1. **Pull an Image**  
   Docker images are used to create containers. To pull a popular image, such as the official `hello-world` image, run:
   ```bash
   docker pull hello-world
   ```

2. **Run a Container**  
   Once the image is pulled, you can run a container from it:
   ```bash
   docker run hello-world
   ```
   This command will print a message confirming that Docker is working correctly.

---

### **Step 3: Basic Docker Commands**

Here are some basic Docker commands you can use to interact with containers:

- **List running containers:**
  ```bash
  docker ps
  ```

- **List all containers (including stopped):**
  ```bash
  docker ps -a
  ```

- **Stop a container:**
  ```bash
  docker stop <container_id_or_name>
  ```

- **Remove a container:**
  ```bash
  docker rm <container_id_or_name>
  ```

- **Remove an image:**
  ```bash
  docker rmi <image_name_or_id>
  ```

---

### **Step 4: Working with Docker Compose (Optional)**

If you want to work with multi-container applications, Docker Compose is a helpful tool.

#### **Install Docker Compose:**

- **On Windows/macOS:** Docker Compose is bundled with Docker Desktop, so you don’t need to install it separately.
  
- **On Linux (Ubuntu Example):**
  Download the Docker Compose binary from GitHub:
  ```bash
  sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  sudo chmod +x /usr/local/bin/docker-compose
  ```

  Then verify the installation:
  ```bash
  docker-compose --version
  ```

#### **Using Docker Compose:**
Create a `docker-compose.yml` file to define multi-container applications. For example:

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: example
```

To run the application, execute:
```bash
docker-compose up
```

This will start the web and db services defined in the `docker-compose.yml` file.

---

### **Step 5: Docker Cleanup**

After using Docker, you might want to clean up unused images, containers, and volumes to save disk space:

- **Remove stopped containers:**
  ```bash
  docker container prune
  ```

- **Remove unused images:**
  ```bash
  docker image prune
  ```

- **Remove unused volumes:**
  ```bash
  docker volume prune
  ```

- **Remove all unused objects (containers, images, volumes, networks):**
  ```bash
  docker system prune
  ```

---
