---
title: "My server can't get an IP"
date: 2010-03-17
forum: Server Platforms
---

### Post by feduntu on 2010-03-17
Hi. I have a LAN at my home (router: D-LINK DI-524) and one of my computers is used as a server (web, ftp, etc). After some days without turnning on the server, I turn it on only to find out that it doesn't work; because the webserver wasn't responding and couldn't connect via SSH (I use the server this way since it's in a closet) nor FTP. Luckily, despite I use the server via SSH, I happen to have a screen and a keyboard in case something like this happened. All I can tell you for the moment is that my router sets the IPs using DHCP. And I'll show you a picture of the ifconfig output. If you need more info to help me out, (sure you will, but I don't know what) please don't hesitate in asking.
 
 
[IMG]http://img31.imageshack.us/img31/9677/ubuntuserver.jpg[/IMG]
 
PD: english is not my mother tongue, therefore, if you find any error in my post, please, make me aware of it so I can improve my english. (if you have many suggestions and don't want to go off-topic too much you can send me a PM)
 
Thanks in advance.

---

### Post by KB1JWQ on 2010-03-18
Run dhclient.  Does the system get an IP as a result?

---

### Post by jrssystemsnet on 2010-03-18
1. post output of **cat /etc/network/interfaces**

2. run **dhclient eth0** and post output here.

---

### Post by spynappels on 2010-03-18
Check the ethernet plug in the back of the machine, this happened to me where it came loose and could not connect, so could not get DHCP IP Address, (Not on a server though)

Edit /etc/network/interfaces to set a static LAN IP. This is strongly recommended for servers anyway.

---

### Post by Dayofswords on 2010-03-18
so you dont have to post a huge photo of results just type
```
blahcommand -blahswitch blahblahblah.cookie > /some/place/whatgetsprintedout.txt
```
**>** makes it print the output to a file, overwriting the file or creating

**>>** adds(not overwrite everything) the output to a file, i think it can create a file as well.

much easier for terminal output

EDIT: dude above me, html and images will not work in sigs

---

