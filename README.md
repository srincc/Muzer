<h1 align='center'>Muzer - 100xDevs</h1>

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Installation](#installation)
  - [With Docker](#with-docker)
  - [Without Docker](#without-docker)
- [Usage](#usage)

## Installation

### With Docker

1. Clone the repository:
   ```bash
   git clone https://github.com/code100x/muzer.git
   ```

2. Navigate to the project directory:
   ```bash
   cd muzer
   ```

3. Create a `.env` file based on the `.env.example` file and configure everything in both the `next-app` and `ws` folders.

4. Run the following command to start the application:
   ```bash
   docker compose --env-file ./next-app/.env --env-file ./ws/.env up -d   
   ```

### Without Docker

1. Clone the repository:
   ```bash
   git clone https://github.com/code100x/muzer.git
   ```

2. Navigate to the project directory:
   ```bash
   cd muzer
   ```

3. Now Install the dependencies:
   ```bash
   cd next-app
   pnpm install
   cd ..
   cd ws 
   pnpm install
   ```
4. Create a `.env` file based on the `.env.example` file and configure everything in both the `next-app` and `ws` folders.

5. For postgres, you need to run the following command:
   ```bash
   docker run -d \
   --name muzer-db \
   -e POSTGRES_USER=myuser \
   -e POSTGRES_PASSWORD=mypassword \
   -e POSTGRES_DB=mydatabase \
   -p 5432:5432 \
   postgres
   ```

6. For redis, you need to run the following command:
   ```bash
   docker run -d \
   --name muzer-redis \
   -e REDIS_USERNAME=admin \
   -e REDIS_PASSWORD=root \
   -e REDIS_PORT=6379 \
   -e REDIS_HOST="127.0.0.1" \
   -e REDIS_BROWSER_STACK_PORT=8001 \
   redis/redis-stack:latest 
   ```

7. Now do the following:
   ```bash
   cd next-app
   pnpm postinstall
   cd ..
   cd ws 
   pnpm postinstall
   ```

8. Run the following command to start the application:
   ```bash
    cd next-app
    pnpm dev
    cd ..
    cd ws
    pnpm dev
   ```

9. To access the prisma studio, run the following command:
   ```bash
   cd next-app
   pnpm run prisma:studio
   ```

## Usage 

1. Access the application in your browser at http://localhost:3000
2. Access the redis stack at http://localhost:8001/redis-stack/browser
3. Access the prisma studio at http://localhost:5555


