---
title: "how to properly use certbot for postfix on backend mail server"
date: 2022-02-09
forum: Server Platforms
---

### Post by joeydenhaag on 2022-02-09
Hi, this is my first post on the forums ):P

My aim is to set up a mail server that is on a separate machine from my web server. I have only 1 public IP address available so I think I must use a reverse proxy to make it work if I want to use Certbot on the backend mail server. So currently I have the following 3 machines running:

- ReverseProxy Server
- Mail Server
- Web Server

I have:

- Apache installed on the mail server because I think it is required to make Certbot work right? 
- Certbot installed on both the ReverseProxy and on the Mail Server.
-** copied **all the files in *etc/letsencrypt//live/<domain>/* and */etc/letsencrypt/renewal/<domain>*/ from the mailserver to the ReverseProxy.

Are both the proxy server and the mail server required to have the same certificate, private key and renewal files like this? And Is this the standard way of getting a certificate for a backend mailserver or am I overcomplicating things?

---

### Post by howefield on 2022-02-09
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by kevdog on 2022-02-10
When you say mail server, are you wanting to setup a full blown mail server or just a forwarding outgoing mailserver?

Although some reverse proxies can handle TCP reverse proxying, reverse proxying is different for web servers than mailservers.  Reverse proxies usually operate on Layer & and hence handle http traffic -- such as what is happening for web and web services.  A TCP reverse proxy would operate on Layer 4. Usually for any type of mailserver you are going to have to open various ports on your router and port forward to these ports.  Mail servers depending on how they are configured need a lot of different ports open. When setting up a mailserver (or any server for that matter) I would always first remove the reverse proxy from the situation to ensure things are setup first and functioning like you would like them prior to adding a reverse proxy.   Postfix can operate with Let's encrypt certificates itself over secure ports, so you don't exactly need the reverse proxy in the mix for a mail server unless you were running multiple servers. d

---

