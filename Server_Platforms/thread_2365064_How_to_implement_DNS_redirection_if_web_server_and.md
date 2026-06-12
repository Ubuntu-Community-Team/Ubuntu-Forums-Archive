---
title: "How to implement DNS redirection if web server and dns server are down?"
date: 2017-07-01
forum: Server Platforms
---

### Post by Grigoriy on 2017-07-01
Hello!
                          I have a dedicated local server in our office.  On one physical machine we run both HTTP and DNS servers. Also we have a  cheap shared hosting alternative. Let's say that our dedicated server  is temporarily dow (say, for maintenance). During that time I want our  web site visitors to be redirected to shared hosting alternative while  our main servers are down. I was thinking to use as a secondary DNS  server, registered at domain's registrar to be that shared hosting DNS  server. Thus when our DNS server is down (and it's down together with  HTTPS server, since they both sit on one physical machine), then during  that period of time, our website visitors would be forwarded to shared  hosting. And when our DNS servers is up again (together with our HTTP  server), then our website visitors would be forwarded to our main  dedicated server.
                          
My question is... If it's a right way of doing it and if it would actually work in a reality?[COLOR=#009900][/COLOR]

---

### Post by darkod on 2017-07-02
As a secondary dns, it should work. When the primary is down all requests should go to the secondary.

As a secondary webserver, I don't think it will work. It is the A record that tells clients where to find the website and if you have two A records clients get directed to them by round-robin usually, which means one half of the clients will be directed to web1 even when it is down. The dns server doesn't check that.

Usually for web HA you would have like load balancer in front of the webservers, and in that case the device actually checks which servers are up and directs clients only to them ignoring the servers that are down.

---

### Post by Grigoriy on 2017-07-02
Thanks for your reply!

---

