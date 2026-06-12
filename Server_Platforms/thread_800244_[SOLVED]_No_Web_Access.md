---
title: "[SOLVED] No Web Access"
date: 2008-05-19
forum: Server Platforms
---

### Post by NateMan on 2008-05-19
I just recently install ubuntu on a new server at a different location using 192.168.2.0 for a network. I then brought it to my home, where I use 192.168.1.0 for my network. I changed /etc/network/interfaces and /etc/hosts to the proper address with 192.168.1. addresses. I then tried to install some software, and I realized I was unable to connect to the internet. I verified this by attempting to ping google, which I am able to do from my desktop. I am able to ping and ssh into the server over the local network. I shouldn't have to forward any ports for outward traffic/downloads. I can see my server in the arp table of my router also. I would really love to get this connected so I can setup some software on it.
Thanks in advance.

---

### Post by NateMan on 2008-05-19
Ok solved the issue. I forgot to change my /etc/resolv.conf to my routers name server. Changed and issue is fixed now. Hope this helps someone else out!

---

