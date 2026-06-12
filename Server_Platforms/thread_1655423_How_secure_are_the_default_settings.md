---
title: "How secure are the default settings"
date: 2010-12-29
forum: Server Platforms
---

### Post by VoiDeR on 2010-12-29
I have been running Ubuntu Server 10.04 for a month now, and I want to make it accessible from the internet. I setup dyndns and everything works fine. My question is how secure are the default settings that are used when you install Ubuntu? Basicly the only thing I want to be accessible from the web are ssh and apache web server. Are there any other things I should do to lock this down?

---

### Post by stmiller on 2010-12-29
Yep - default settings of ssh and apache are both pretty much ok out of the box.


You can take a few quick steps to make apache not reveal so much about your server if you wish:

[http://www.debianadmin.com/securing-apache-web-server-from-information-leakage.html](http://www.debianadmin.com/securing-apache-web-server-from-information-leakage.html)

---

### Post by James78 on 2010-12-29
Well, SSH's default settings actually aren't that secure. For SSH you should disable passworded logins, root login, and enable keyed only logins. Optionally, you can also change the port number from the default. If you don't do these, then other random zombie computers/script kiddies can brute force into your computer. It's impossible to get in when they can't brute force a password, because it never asks for one.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Listen on a Non-Standard Port](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Listen on a Non-Standard Port)

---

