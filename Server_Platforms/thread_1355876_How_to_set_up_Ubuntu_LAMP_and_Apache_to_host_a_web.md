---
title: "How to set up Ubuntu LAMP and Apache to host a website with dynamic IP on home server"
date: 2009-12-15
forum: Server Platforms
---

### Post by SeaWolfy on 2009-12-15
[SIZE=3][FONT=Times New Roman]Hi,[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]I would like to host a website on my server at home, but I am very new to Linux and Apache so I need some help.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]I have an Ubuntu 9.04 LAMP server running on ESXi4. I have managed to update the Ubuntu server, set up the network address, install SSH and Webmin from command line. [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]The Ubuntu server has a static IP on the local network (192.168.0.14). I have a registered domain name (mydomain.com). I have dynamic IP address. I registered with OpenDNS…as far as I know I need some kind of dynamic DNS solution because of my dynamic IP. [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]I would like to set up the Apache2 web server either from Webmin or from command line. Anyone could give me a guide please, how to set up the whole thing so that I could host the website on my server? [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]There is lot of options on the webhost I registered my domain, also in Webmin and I just can’t get it work.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]I appreciate any comment on this![/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Thanks![/FONT][/SIZE]

---

### Post by HighCommander540 on 2009-12-15
> **SeaWolfy said:**
> [SIZE=3][FONT=Times New Roman]Hi,[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]I would like to host a website on my server at home, but I am very new to Linux and Apache so I need some help.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]I have an Ubuntu 9.04 LAMP server running on ESXi4. I have managed to update the Ubuntu server, set up the network address, install SSH and Webmin from command line. [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]The Ubuntu server has a static IP on the local network (192.168.0.14). I have a registered domain name (mydomain.com). I have dynamic IP address. I registered with OpenDNS…as far as I know I need some kind of dynamic DNS solution because of my dynamic IP. [/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]I would like to set up the Apache2 web server either from Webmin or from command line. Anyone could give me a guide please, how to set up the whole thing so that I could host the website on my server? [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]There is lot of options on the webhost I registered my domain, also in Webmin and I just can’t get it work.[/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]I appreciate any comment on this![/FONT][/SIZE]

[SIZE=3][FONT=Times New Roman]Thanks![/FONT][/SIZE]

All you really need to do. Is download the program that OpenDNS provides for you, that will update your IP address whenever it changes. Then all you need to do is configure your router to forward the correct ports (80, 22, 20-21) to 192.168.0.14.

The final thing is to configure your domain's settings to use the hostname that OpenDNS is giving you instead of an IP address.

---

### Post by aschlosberg on 2009-12-15
SeaWolfy there are a lot of great tutorials regarding setting up Apache2 that you can find at [http://articles.slicehost.com/apache](http://articles.slicehost.com/apache) (I don't work for them, I'm a client who is impressed with the services).

---

### Post by HighCommander540 on 2009-12-16
> **aschlosberg said:**
> SeaWolfy there are a lot of great tutorials regarding setting up Apache2 that you can find at [http://articles.slicehost.com/apache](http://articles.slicehost.com/apache) (I don't work for them, I'm a client who is impressed with the services).

None, of those tuts have anything to do with dynamic IP.

---

### Post by aschlosberg on 2009-12-16
> **HighCommander540 said:**
> None, of those tuts have anything to do with dynamic IP.

He had two questions though... one regarding a dynamic IP address and one about setting up Apache.

---

