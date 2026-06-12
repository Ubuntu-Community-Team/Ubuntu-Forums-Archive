---
title: "[SOLVED] make web Server Accesible to the Internet   &amp;quot;static ip ??&amp;quot;"
date: 2008-12-29
forum: Server Platforms
---

### Post by 1467 on 2008-12-29
i am trying to make a web server gust for the leaning but I am following this tutorial [COLOR="Blue"][http://nettuts.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/]("http://nettuts.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/")[/COLOR] but now i am stuck at **"make web server Accessible to the Internet"** i think i have to log in to my router and set a static LAN address. fist off what is a static LAN and how do i log in to my router is that the ip address looking thing on the side of my **2wire 3800HGV-B** that says advanced settings i looked there and did not c static lan or any thing like that ?

one more question when i look up my ip address it says 192.168.1.102 but is that gust my local ip or is it for the www? 
 
thank you for the help

---

### Post by koenn on 2008-12-29
its not a static LAN its a static address you need it because you have to do portforwarding to make your router accessible from the internet and in order to do that you need to know the address of the server and you dont want it to change (with dhcp) so you need a static address you can set a static address the way that howto explains by making a dhcp reservation on your router which also serves as a dhcp server an other way to do it is by editing /etc/network/interfaces here is an example [http://ubuntuforums.org/showpost.php?p=6448639&postcount=20](http://ubuntuforums.org/showpost.php?p=6448639&postcount=20).

192.168.1.102 is a local network address its not visible from the www thats why you have to do the portforwarding

have fun

---

### Post by 1467 on 2008-12-29
now i can connect to my server with this 76.192.151.45 right but this is not working

---

### Post by 1467 on 2008-12-29
and is it normal for it 2 be like 2 1/2 miles off?













thany for your help

---

### Post by koenn on 2008-12-29
your router does NAT and it wont let u connect to the wan interface only to the lan interface it will work from your lan with the lan address and from the internet with the public address

and what is 2 1/2 miles off what ?

---

