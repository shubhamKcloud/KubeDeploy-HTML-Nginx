FROM -platform-amd64 debian: buster-slim
RUN apt-get update && apt-get install -y nginx openssl && rm -rf /var/lib/apt/lists/*

RUN mkdir /etc/nginx/ssl

RUN openssl req -x509 -newkey rsa:4096 -keyout /etc/nginx/ssl/nginx.key -out /etc/nginx.cert --days 365 -nodes -subj "/c=US/ST=CA/L=San Francisco/O=Example/CN=test.abc.com"

RUN rm /etc/nginx/sites-enabled/default

COPY nginx.conf /etc/nginx/sites-enabled/

COPY index.html /usr/share/nginx/html/

EXPOSE 80

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]