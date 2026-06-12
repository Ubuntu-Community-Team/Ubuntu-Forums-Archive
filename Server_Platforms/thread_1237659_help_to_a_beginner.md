---
title: "help to a beginner"
date: 2009-08-11
forum: Server Platforms
---

### Post by mfighter on 2009-08-11
Hello Linux people :P
 
Iam very new to Linux and have some questions to you before installing any OS.
 
I want to build my own server, which should could have a counter-strike source server, teamspeak/ventrilo server, webserver and also a proxy server running in same time, all the time. 
 
I have nothing and no server jet, but I will soon buy all the parts for a computer and then collect it into one. therefore question 1:
 
are these parts good/recommendously for a server?
[FONT=Calibri]CPU: 2,66 quad core[/FONT][FONT=Calibri]Harddisk: 1TB 32 mb[/FONT][FONT=Calibri]RAM: 4 gb[/FONT][FONT=Calibri]motherboard: intel socket 775 which [/FONT][FONT=Calibri]power collection: 850w corsair[/FONT] 
 
 
 
 
[SIZE=1]q2: Is ubunto server edition the right OS for me?[/SIZE]

[SIZE=1]q3: is it possible to make a FTP server with linux?[/SIZE]

[SIZE=1]q4: can I control the server from my own windows computer if it is at my friends place? maybe VNC or something?[/SIZE]

[SIZE=1]q5: any tips or something, then I would be very happy :P[/SIZE]

[SIZE=1]thx for replying! :D[/SIZE]

---

### Post by sixstorm on 2009-08-11
> **mfighter said:**
> Hello Linux people :P
 
Iam very new to Linux and have some questions to you before installing any OS.
 
I want to build my own server, which should could have a counter-strike source server, teamspeak/ventrilo server, webserver and also a proxy server running in same time, all the time. 
 
I have nothing and no server jet, but I will soon buy all the parts for a computer and then collect it into one. therefore question 1:
 
are these parts good/recommendously for a server?
[FONT=Calibri]CPU: 2,66 quad core[/FONT][FONT=Calibri]Harddisk: 1TB 32 mb[/FONT][FONT=Calibri]RAM: 4 gb[/FONT][FONT=Calibri]motherboard: intel socket 775 which [/FONT][FONT=Calibri]power collection: 850w corsair[/FONT] 
 
 
 
 
[SIZE=1]q2: Is ubunto server edition the right OS for me?[/SIZE]

[SIZE=1]q3: is it possible to make a FTP server with linux?[/SIZE]

[SIZE=1]q4: can I control the server from my own windows computer if it is at my friends place? maybe VNC or something?[/SIZE]

[SIZE=1]q5: any tips or something, then I would be very happy :P[/SIZE]

[SIZE=1]thx for replying! :D[/SIZE]

Ubuntu Server is great IMO.  I just have a few short answers for you.

Q3:  Yes, you can use multiple solutions for FTP.  Filezilla is a popular GUI-based solution.

Q4:  VNC works, but you can also do SSH if you are brave enough to use commandline.

I will be building a server in another month or so.  I'll be sure to keep an eye out for this thread, as I would like to make it a CSS and/or TF2 server.

---

### Post by mfighter on 2009-08-11
thx for reply! :D
 
gr8 then maybe we can help each other out ;P
 
but know everything about connecting through filezilla but is it difficult to set up a ftp ip, user, pass to the server so I can connect from home? 
 
thx again :P

---

### Post by hessiess on 2009-08-11
> 
q3: is it possible to make a FTP server with linux?

Yes but you don't want to, FTP is an outdated and highly insecure protocol, you can use SFTP however.

> 
q4: can I control the server from my own windows computer if it is at my friends place? maybe VNC or something?

Yes, use VNC over an SSH tunnel, or ditch the useless GUI and use plain SSH.

---

### Post by mfighter on 2009-08-11
> **hessiess said:**
> Yes but you don't want to, FTP is an outdated and highly insecure protocol, you can use SFTP however.
 
 
Yes, use VNC over an SSH tunnel, or ditch the useless GUI and use plain SSH.
 
Can u tell me a bit more off SFTP, how to use, where to download etc?
 
thx :D
 
and what about making a SSH tunnel, where do I do that?
 
again thx for answer :D

---

### Post by hessiess on 2009-08-11
> **mfighter said:**
> Can u tell me a bit more off SFTP, how to use, where to download etc?

[http://ubuntuforums.org/showthread.php?t=347478](http://ubuntuforums.org/showthread.php?t=347478)

Just add a user and set the home dir to the file root, then when you sftp into the server it will upload files to the users home dir.

> 
and what about making a SSH tunnel, where do I do that?
 
again thx for answer :D
[http://www.astahost.com/info.php/Linux-Secure-Vnc-Ssh-Tunnel-Port-Forwarding_t16655.html](http://www.astahost.com/info.php/Linux-Secure-Vnc-Ssh-Tunnel-Port-Forwarding_t16655.html)
[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)

---

### Post by mfighter on 2009-08-11
thx for linking :D

---

### Post by oj0kksn5 on 2009-08-11
Q1: Of course :P

lol

just use ssh for both you can install openssh on installation of ubuntu server just tick it when it pops up 

from there u can use windows apps 

FTP: winscp [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
VNC (command Line): puTTy [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

proxy server: [https://help.ubuntu.com/7.04/server/C/squid.html](https://help.ubuntu.com/7.04/server/C/squid.html)

its really easy to install and configure

also shorewall altho a firewall can filter ports and it logs all activity

below is a nice tut for beginer
[http://net.tutsplus.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/)

also installs apache php mysql and shorewall if wanted but it runs you through the installation of server

---

### Post by mfighter on 2009-08-11
> **sephedo said:**
> Q1: Of course :P
 
lol
 
just use ssh for both you can install openssh on installation of ubuntu server just tick it when it pops up 
 
from there u can use windows apps 
 
FTP: winscp [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
VNC (command Line): puTTy [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
 
proxy server: [https://help.ubuntu.com/7.04/server/C/squid.html](https://help.ubuntu.com/7.04/server/C/squid.html)
 
its really easy to install and configure
 
also shorewall altho a firewall can filter ports and it logs all activity
 
below is a nice tut for beginer
[http://net.tutsplus.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/articles/news/how-to-setup-a-dedicated-web-server-for-free/)
 
also installs apache php mysql and shorewall if wanted but it runs you through the installation of server
 
thx so much again! omg u guys are awsome :D let it coming haha :P

---

