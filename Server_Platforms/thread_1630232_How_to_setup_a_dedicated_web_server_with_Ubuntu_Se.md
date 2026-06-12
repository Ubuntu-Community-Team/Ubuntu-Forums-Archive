---
title: "How to setup a dedicated web server with Ubuntu Server 10.10?"
date: 2010-11-24
forum: Server Platforms
---

### Post by thuongquoc on 2010-11-24
Hello everybody, After installation Ubuntu Server 10.10 I don't know what to do next to access to the Internet. I have read several tutorials but it is not possible to do. 
Thanks!

---

### Post by arrrghhh on 2010-11-24
How are you trying to access the internet?  Update?  Just trying to ping google?

Can other machines using the same router/switch/gateway connect to the internet?

---

### Post by Bucky Ball on 2010-11-24
You should be using an LTS release for a server (long term support). 10.04

---

### Post by CharlesA on 2010-11-24
> **Bucky Ball said:**
> You should be using an LTS release for a server (long term support). 10.04

+1 to that.

@OP: Try what arrrghhh suggested. We really need more info.

---

### Post by thuongquoc on 2010-11-25
> **arrrghhh said:**
> How are you trying to access the internet?  Update?  Just trying to ping google?

Can other machines using the same router/switch/gateway connect to the internet?
No. It mean how to allow everyone access my site from my Ubuntu Server. I registered a free DNS from DYNDNS, when I point address to my browser I show a dialogue requesting enter username and password to login the router. I installed LAMP and OpenSSH. I used "ifconfig | grep inet" to get my IP (I install Ubuntu Server on VirtualBox) and point the IP to the host web browser but I can't access.

---

### Post by HugoSerrano on 2010-11-25
Hi.

Probably you can connect to it inside your network connecting to the private IP assigned to the server.
e.g [http://192.168.1.25](http://192.168.1.25)

To someone connect to it from outside, you need to forward the 80 TCP port (or 443 to https) from the router to the inside IP.

---

### Post by Goldfissh on 2010-11-25
Access your router via it's IP address in your web browser, and port forward HTTP (port 80).

---

### Post by thuongquoc on 2010-11-25
Please give me a tutorial! Thanks!

---

### Post by CharlesA on 2010-11-25
> **thuongquoc said:**
> Please give me a tutorial! Thanks!

[http://portforward.com/](http://portforward.com/)

---

### Post by plusnplus on 2010-11-26
some router model is easy(with graphic interface) to do port forwarding.
some is really difficult(need do command line).

---

