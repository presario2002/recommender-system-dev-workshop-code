# build environment
FROM node:14.5.0-alpine as build
WORKDIR /app
ENV PATH /app/node_modules/.bin:$PATH
# COPY package.json ./
# COPY package-lock.json ./
COPY . ./
RUN npm install
RUN npm rebuild node-sass
RUN npm run build

# production environment
FROM nginx:stable-alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]