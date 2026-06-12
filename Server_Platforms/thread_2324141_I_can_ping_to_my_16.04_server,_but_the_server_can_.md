---
title: "I can ping to my 16.04 server, but the server can not ping to the client."
date: 2016-05-11
forum: Server Platforms
---

### Post by brayn2 on 2016-05-11
Hi,

I'm implementing an [ELK Stack]("https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04") and am trying to connect to Kibana through a client PC's browser. I did it before in a test lab and it worked all fine, but for some reason it doesn't want to right now.

I configured my ELK Stack to listen to localhost, but have set up Nginx for a reverse proxy so I'll still be able to access it. I tried to troubleshoot a little myself and noticed that I can ping to the server, but I can not ping to the client from the server.

IP configurations should be fine according to the network administrator, am I missing something?

---

### Post by brayn2 on 2016-05-11
Update:

I can access Kibana perfectly fine once I remove the "localhost" statements on the configuration file, but I prefer it being handled by the proxy so not everyone can access it.

More of a ELK Stack topic now, sorry

---

