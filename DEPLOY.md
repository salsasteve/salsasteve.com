# Website Deployment with Cloudflare and Docker

This guide walks you through the process of deploying a website using Docker, Cloudflare, and a custom domain.

## Prerequisites

- Git
- Docker
- Cloudflare Account
- Domain Name (purchased from Namecheap or another domain registrar)

## Step 1: Clone the Repository 

THIS STEP IS ONLY IF YOUR ARE DEPLOYING THIS WEBISTE
OTHERWISE USE YOU OWN CONTAINER!!!!!

Clone the repository to your local machine:

```bash
git clone https://github.com/m4tt72/terminal.git
cd terminal
```

## Step 2: Install Docker

Follow the official Docker installation guide for your operating system:

- [Get Docker](https://docs.docker.com/get-docker/)

## Step 3: Create a Cloudflare Account

If you don't already have a Cloudflare account, create one:

- [Sign up for Cloudflare](https://www.cloudflare.com/)

## Step 4: Purchase and Set Up Your Domain

1. Purchase a domain from Namecheap or another domain registrar of your choice.
2. Add your domain to Cloudflare:
   - Log in to your Cloudflare account.
   - Click on 'Add a Site' and follow the instructions to add your domain.
   - Update your domain's nameservers to the ones provided by Cloudflare.

## Step 5: Create a Cloudflare Tunnel

1. Navigate to the Zero Trust dashboard in your Cloudflare account.
2. Set up a new tunnel following the instructions provided.

## Step 6: Create a Docker Network

Create a Docker network named `tunnel`:

```bash
docker network create tunnel
```

## Step 7: Run Cloudflare Tunnel with Docker

Run the Cloudflare Tunnel Docker container with the network set to `tunnel`:

```bash
docker run --network=tunnel <cloudflare-tunnel-docker-image>
```

Replace `<cloudflare-tunnel-docker-image>` with the appropriate Docker image for Cloudflare Tunnel.

## Step 8: Deploy Your Website with Docker

Deploy your website using Docker, ensuring that it is connected to the `tunnel` network:

```bash
docker run --network=tunnel <your-website-docker-image>
```

Replace `<your-website-docker-image>` with the Docker image of your website.

## Step 9: Connect Your Domain to the Tunnel on Cloudflare

1. Go back to your Cloudflare dashboard.
2. Navigate to the ZERO Trust settings for your domain.
3. Add a public hostname 
4. Check out these [docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/)

## Conclusion

Your website should now be deployed and accessible through your custom domain, secured and accelerated by Cloudflare. Ensure that all DNS and network configurations are correctly set up and that your Docker containers are running as expected.

---

Feel free to modify this template as needed to better suit your project's requirements or to add additional information and instructions.
