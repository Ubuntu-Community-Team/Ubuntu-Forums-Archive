---
title: "can't connect to my web server"
date: 2013-05-29
forum: Server Platforms
---

### Post by fperez87 on 2013-05-29
hello, I'm new to ubuntu and web servers, so my question might be quite basic, but I've been looking for an answer and I haven't succeed. I've been following all the steps of a tutorial ( [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) ), I installed Ubuntu server 12.04, (I also installed Gnome, but I've been working in the Terminal), I set up LAMP as it says in the tutorial, but when I get to set up Transmit (on my mac), it cannot connect to the server. When I type "ifconfig | grep inet" I get 2 IP addresses: 169.254.9.153 and 192.168.1.117. Both of them passed the test of typing the IP address on firefox (it says "it works!") but none of them work at Trasmit. Any ideas??

thanks!

---

### Post by newbie-user on 2013-05-29
Make sure your server's firewall is allowing FTP (port 21) and/or SFTP/SSH (port 22). You could also try using SCP instead of SFTP.

---

### Post by chrisguk on 2013-05-29
If I get your question correct, you essentially want to view a website or websites on your MAC that are stored on your Ubuntu Server.  Is this correct?

*slight pause before I give advice*

---

### Post by fperez87 on 2013-05-29
thanks! about checking that "[COLOR=#000000]server's firewall is allowing FTP (port 21) and/or SFTP/SSH (port 22)[/COLOR]", how do I do that??

---

### Post by fperez87 on 2013-05-29
thanks chrisguk, basically, what I want to do is to host my website (very basic one). The idea is to use Transit so I can send my website's files from my mac to the server. Am I doing things right? I might be a bit lost, I'm not very familiar to this language and concepts. thanks!

---

### Post by newbie-user on 2013-05-29
> **fperez87 said:**
> thanks! about checking that "[COLOR=#000000]server's firewall is allowing FTP (port 21) and/or SFTP/SSH (port 22)[/COLOR]", how do I do that??

Well, assuming you followed the tutorial that you posted originally, you should already have ports 80 and 22 allowed through the firewall. All you would need to do is add FTP to your shorewall config:

```
FTP/ACCEPT     net     $FW
```


I don't use shorewall, so I'm not sure of the syntax, but that would basically be all you have to add.

Also, when using Transmit, have you tried using SCP or SFTP?

---

### Post by fperez87 on 2013-05-29
that worked!!! (SFTP) now, what do I have to so everyone (not only from the local network) can have access to my website?? do I need a domain (I don't have it yet)?? thanks!

---

### Post by newbie-user on 2013-05-30
> **fperez87 said:**
> that worked!!! (SFTP) now, what do I have to so everyone (not only from the local network) can have access to my website?? do I need a domain (I don't have it yet)?? thanks!

You will need to purchase a domain name. GoDaddy is cheap, though I find it not so intuitive to use. Networksolutions is not as cheap, but I find it much easier to use.

Aside from the domain name, you should get a public static IP address. If not, then you need to sign up for a dynamic DNS service, such as no-ip.com, dyndns, or freedns.afraid.org. Check with your ISP for a static IP address. Also, if you have residential connection, check if your ISP blocks any ports.

You will also need to set up port-forwarding from your gateway/router to your server, unless you plan to connect your server directly to the Internet.

tl;dr - 
1. domain name
2. routable IP
3. port forwarding

---

### Post by SeijiSensei on 2013-05-30
I have used [DirectNIC](http://www.direcnic.com) as my registrar for many years now.

Personally I avoid NetworkSolutions like the plague after numerous annoying experiences with them, and I would never give a penny to a sexist organization like GoDaddy.

---

