# Dear Bakery

## 1. Project Overview and Main Features

Dear Bakery is a bakery website built using HTML, CSS, and images. It provides information about the bakery and displays bakery products.

Main features:
- Homepage displaying bakery information.
- Navigation between website pages.
- Bakery product images.
- CSS styling for the website layout.

## 2. Prerequisites and Docker Version Tested

Requirements:
- Git
- Docker Desktop
- A web browser

The project was tested using Docker Desktop on Windows with Docker Engine and an Nginx Alpine image.

To check the installed Docker version, run:

```powershell
docker --version
docker compose version
```

## 3. Clone the Repository

Clone the project repository:

```bash
git clone <repository-url>
cd <repository-folder>
```

Replace `<repository-url>` and `<repository-folder>` with the actual repository URL and folder name.

## 4. Environment Variables

This static website does not require environment variables to run.

A `.env` file is not required for the current Docker setup. No passwords, API keys, or other secrets are needed.

## 5. Build and Run with Docker

Build the Docker image:

```bash
docker build -t group6/dear-bakery:week6 .
```

Run the application:

```bash
docker run -d --name dear-bakery-app -p 8081:80 group6/dear-bakery:week6
```

Alternatively, start the services defined in the Docker Compose file:

```bash
docker compose up --build -d
```

Check the Compose services:

```bash
docker compose ps
```

## 6. Application URL and Ports

- Application URL: http://localhost:8081
- Host port: 8081
- Container port: 80
- Web server: Nginx

The Docker run command maps host port 8081 to container port 80.

## 7. Verify the Application

Check whether the container is running:

```bash
docker ps
```

Expected result: `dear-bakery-app` appears with status `Up`.

Open the application in a browser:

http://localhost:8081

Expected output:
- The Dear Bakery homepage loads successfully.
- Website navigation is accessible.
- CSS styling is applied.
- Bakery images are displayed correctly.

The container logs should show successful HTTP responses, such as status `200`, for the homepage, CSS, and image requests.

## 8. View Logs and Status

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

View application logs:

```bash
docker logs dear-bakery-app
```

Follow logs continuously:

```bash
docker logs -f dear-bakery-app
```

Inspect container configuration:

```bash
docker inspect dear-bakery-app
```

Press `Ctrl + C` to stop following logs.

## 9. Stop and Clean Up

Stop the application container:

```bash
docker stop dear-bakery-app
```

Remove the stopped container:

```bash
docker rm dear-bakery-app
```

To stop and remove services managed by Docker Compose:

```bash
docker compose down
```

These commands do not delete the Docker image. The Compose command only affects services managed by that Compose project.

## 10. Troubleshooting and Known Limitations

### Port Already in Use

If port 8081 is already in use, select another host port, such as 8082:

```bash
docker run -d --name dear-bakery-app -p 8082:80 group6/dear-bakery:week6
```

Then open http://localhost:8082.

### Container Name Conflict

If the container name already exists, check the container:

```bash
docker ps -a
```

Stop and remove the old container if appropriate before creating another container with the same name.

### Website Does Not Load

Check the container status and logs:

```bash
docker ps -a
docker logs dear-bakery-app
```

### Missing Favicon

The browser may request `/favicon.ico`. If no favicon file exists, Nginx may return HTTP 404 for that request. The main website can still work normally.

### Known Limitations

- This is a static website built with HTML and CSS.
- It does not currently use a database or backend application.
- Environment variables are not required for the current setup.

- Docker assignment updated by Radella Hafiza

- Docker assignment updated by Dian Fifi Nabilla
