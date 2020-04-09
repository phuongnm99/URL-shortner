FROM node:12 as builder

WORKDIR /app

COPY . /app

RUN echo REACT_APP_API_URL=http://u.demo01.aimesoft.com/api/ >> .env.local

RUN echo REACT_APP_BASE_URL=http://u.demo01.aimesoft.com >> .env.local

RUN npm install

RUN npm run build

FROM nginx:alpine

WORKDIR /app

COPY --from=builder /app/build /app

COPY ./nginx /etc/nginx/conf.d

RUN rm /etc/nginx/conf.d/default.conf

EXPOSE 4000

CMD ["nginx", "-g", "daemon off;"]