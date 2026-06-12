---
title: "Redirect subdomain to IPAddress with Port"
date: 2024-05-10
forum: Server Platforms
---

### Post by dfrusone on 2024-05-10
Dear Support,

i have a test-server where i installes 3 subdomains
wp.server.net for Worpress
moodle.serer.net for moodle
server.net for Apache2

Now i want to configure the server, to open the different applications adressing a port

For example:
10.10.8.1:8080 for Wordpress
10.10.8.1:8081 for moodle
10.10.8.1:8082 for Apache2

How can i configure the server in this way?

Can somebody help me?

Thanks a lot

---

### Post by TheFu on 2024-05-10
For **apache**, [https://httpd.apache.org/docs/2.4/vhosts/examples.html](https://httpd.apache.org/docs/2.4/vhosts/examples.html)  and [https://www.howtogeek.com/devops/how-to-set-up-a-reverse-proxy-with-apache/](https://www.howtogeek.com/devops/how-to-set-up-a-reverse-proxy-with-apache/)

But I'd use **nginx** myself as the reverse proxy and perhaps TLS termination point.  [https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)  There are lots of examples and discussions for accomplishing this with a search  "nginx reverse proxy for multiple webapps"    Stackoverflow had a few answers.

There's no formal support here. We are all your peers, volunteers.

---

### Post by dfrusone on 2024-06-04
Thank you a lot!!!

---

