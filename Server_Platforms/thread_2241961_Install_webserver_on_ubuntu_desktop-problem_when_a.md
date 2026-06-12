---
title: "Install webserver on ubuntu desktop-problem when access external address"
date: 2014-08-29
forum: Server Platforms
---

### Post by Angelos_Konstantin on 2014-08-29
[COLOR=#333333][FONT=UbuntuRegular]I have Ubuntu 14.04.1 LTS (desktop) and I would like to install a web server and have my own wordpress website. So, I installed LAMP, then I checked whether Apache2 works (I typed on the browser http:// 192.168.1.5) and it works. However, as I understand this is the internal address of my pc (I connect to the internet through wireless home router). When I try my external address (currently is 213.16.159.224) a pop-up window emerges:
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Authentication Required A username and password are being requested by http:// 213.16.159.224. The server says: "ZXHN H108L"[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]User Name:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Password:
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What am I doing wrong?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks in advance[/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-08-29
Welcome.

Everything as it should be.  What needs to happen for you to activate port forwarding in your router (it's a ZXHN H108L ?) and maybe also turn off external access to the administrative functions of your router.  The details of port forwarding vary from router to router but there should be a menu to that effect.  You'll want to forward port 80 (http) and port 443 (https) to your internal web server (192.168.1.5) if you want external access. Also, you'll need to open up ports 80 and 443 on 192.168.1.5 in UFW if you haven't already.

---

