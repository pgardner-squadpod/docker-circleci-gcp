# docker-circleci-gcp
CI/CD setup using CircleCI and Docker, deployed to Google Cloud Platform

## How to Run

docker build -f Dockerfile.dev . -t docker-cicd
    * -f Dockerfile.dev     => reference the specific file Dockerfile.dev
    * -t docker-cicd        => use alias "docker-cicd"

docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app docker-cicd
    * -p 3000:3000          => map host local port 3000 to container local port 3000
    * -v /app/node_modules  => bookmark the app/node_modules folder, protecting it against other mappings
    * -v $(pwd):/app        => map the path of working directory to /app in container
    * <image_id>            => image id or name

docker run docker-cicd npm run test
    * docker-cicd           => container id or friendly name
    * npm run test          => command to run within the container, overriding what was in the Dockerfile