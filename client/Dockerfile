FROM node:alpine as builder

WORKDIR '/app'
COPY package.json .

RUN npm install

COPY . .

# Build command will create a /build folder
# within our working directory
RUN npm run build

FROM nginx as deploy
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html