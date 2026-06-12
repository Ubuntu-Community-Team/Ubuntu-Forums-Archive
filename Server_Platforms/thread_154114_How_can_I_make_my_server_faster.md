---
title: "How can I make my server faster?"
date: 2006-04-02
forum: Server Platforms
---

### Post by Hydraulix on 2006-04-02
Hey everyone,

I just installed Ubuntu on an old 500mhz box and I'm using it as my FTP server. I'm not new to Linux and I've been using Linux for about 6 years now but this is the second time I've used Ubuntu and I'm pretty impressed with it. (I use Gentoo as my main distro) Anyway, I installed proftpd and I have it serving some files off my second hard drive but the upload speed sucks. The download speed is pretty good (60-80kb) but I'm only getting 40kb when I upload. Also it takes about 5-10 seconds for the "waiting for welcome message" to come up every time I log in or when I try to upload/download. My comcast connection is at it's highest so I know it's not that. Is there something I'm missing? What do you recommend?

---

### Post by Horndog on 2006-04-02
40kbs up is about all your going to get with Comcast premium residential service. If you live in a big city then you will have a congested WAN. I had the same specs when I lived near Chicago.

---

### Post by Hydraulix on 2006-04-02
Ah that sucks. Well is there anyway I can speed up that welcome message lag?

---

### Post by Horndog on 2006-04-02
Your lag could be network related. Could you give a description of your LAN?

---

### Post by Hydraulix on 2006-04-02
Sure thing. It's a simple 10/100 home network. The server is wired into my linksys wireless router full duplex with a CAT 5 cable. I have two other machines connected with wifi. One thinkpad and one iBook. The Thinkpad is my work system and the iBook I gave to my girlfriend. So they don't use a lot of broadband. I installed two nic cards in the server but for some reason when they are both enabled it seems slower. I  really don't need to bridge them but I was going to have eth0 public and then eth1 private. So if someone is downloading on eth0 I can use eth1 to do whatever to the server. That worked great in Fedora but for some reason Ubuntu doesn't like that. Let me know if you need anymore info.

---

### Post by CyberCam on 2006-04-03
Have you disabled ipv6 on your server?

---

### Post by Hydraulix on 2006-04-03
[QUOTE=CyberCam]Have you disabled ipv6 on your server?[/QUOTE]



No I haven't. Where is the config file located so I can disable it?

---

