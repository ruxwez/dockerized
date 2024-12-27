# Base image
FROM golang:1.23.4-bullseye

# Set environment variables
ENV NODE_VERSION=20

# Install Node.js and npm
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get update && \
    apt-get install -y nodejs && \
    npm install -g pnpm yarn

# Detect architecture and set Go environment variables accordingly
ARG TARGETARCH
ENV CGO_ENABLED=1 \
    GOOS=linux \
    GOARCH=${TARGETARCH}

# Verify installations
RUN go version && node -v && yarn -v

# Set working directory
WORKDIR /app