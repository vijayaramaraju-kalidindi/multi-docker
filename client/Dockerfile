# Use an existing base image
FROM node:alpine as builder
# Download and install dependencies
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build
# nginx config
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

