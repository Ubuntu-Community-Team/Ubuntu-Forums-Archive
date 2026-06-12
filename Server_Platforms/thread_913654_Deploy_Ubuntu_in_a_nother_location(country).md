---
title: "Deploy Ubuntu in a nother location(country)"
date: 2008-09-08
forum: Server Platforms
---

### Post by rubysoft on 2008-09-08
Hi,
Senario
=======
1) I would like to deploy Ubuntu 8.04 LTS with Apache/PHP support.
2) The server will only be used locally (LAN enviroment)
3) I wont have any access to the server, (eg. putty) since it wont have any access to the internet.
5) The server wont have any access to the internet
6) The server is located in another country where I am currently at.


What is the best way to do it?


Theory Possilbe Solutions
===================
1) I install on a server at my side, clone it (with either ghost or acronis true image), will it work this way if both has diffrent hardware.
2) Or are there any ubuntu with pre-LAMP configured?

---

### Post by azadpanchi on 2008-09-26
You can make custom installation images, refer to:
[http://www.linux.com/feature/114335](http://www.linux.com/feature/114335)

You could go wtih ghost of acronis true image and that should work if hardware is relatively close, but, I would not recommend it.

---

### Post by pdwerryhouse on 2008-09-26
Might be worth looking at [Ubuntu preseeding]("https://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html"). This would let you build a CD/DVD that can install the whole system for you automatically.

It might be slightly more portable than ghosting an image, but unless you carefully prepare it, it could also still break.

---

