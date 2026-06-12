---
title: "Should I ? or Not? Suggest please."
date: 2008-05-21
forum: Server Platforms
---

### Post by media_555 on 2008-05-21
What minimum hardware specifications is needed to run web server using Hardy? Just for web-server..

I know there is huge security challenge in it. But my main concern at the moment is - can I use my spare DELL machine for web server purpose (1 GB RAM, 1.87 GHz, 80 GB Disk, 111a/b/g Wireless LAN Mini PCI Expr).. Or normal desktop machine for real hosting is not possible? Are special server machines must for running simple webserver? Sorry, if I am asking stupid questions.

I am ready to upgrade my RAM, hard-drive or network card.. (please suggest minimum specifications - for better connection speed)

Actually, it all came to my mind when I read specifications of some web host provider's for dedicated server like 256 MB RAM/777 GHz/ 50 GB etc.. 

Do anyone here hosting their websites from home? please share your experience. What are the hardware sepcifications you using? 
Please share your experience. I want to learn..

---

### Post by bluefrog on 2008-05-21
what you have is more than enough for a home web server.

---

### Post by klcom on 2008-05-21
I have a Ubuntu Hardy 8.04, with compaq nx9010, is ha laptop with a pentium 1,4 512 ram... and work fine with squid for 350 users, ftp, and postfix who send 3000 information mails in 4 days.

your hardware specifications is right.

bye!

---

### Post by Mech13 on 2008-05-21
Well for me, its not so much getting enough hardware power (command line interface does not take much computing power) but once you really get into setting up your computer as a server it gets real technical real quick =) But if your up for a challenge I’m sure you’re more then capable. 

As far as specs are concerned; I’m running a 2.6Ghz Sempron, with a gig of ram and a 80 gig harddrive. My internet connection is 15Mb, which is more then enough. So far it has been able to handle the load easily. 

But I have had many frustrations along the way of setting up my website. What I found out I had to do after much studying is: 
First off I had to get the server configured to a static IP inside of my network. Then you have to configure port forwarding from your router to the now static IP server. You’ll then buy a domain name of your choice and configure it to point to your server using either BIND DNS inside of the server. Or if you have a dynamic IP address then you have to spend around $29 for the DynDns service (or find a less effective one for free). If you don’t want to be able to send emails or anything from your server that’s about all you have to do. But if you want a server with most of the features that other servers offer it can be difficult to set up the mail server and virtual servers inside of apachie2.

---

### Post by hyper_ch on 2008-05-21
to server the website from home you need:

(1) good upload speed

(2) if possible static IP

Your machine way "overpowered" to just host a webpage from home

---

