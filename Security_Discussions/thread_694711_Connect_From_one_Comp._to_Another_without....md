---
title: "Connect From one Comp. to Another without..."
date: 2008-02-12
forum: Security Discussions
---

### Post by TimUkaj on 2008-02-12
Hey guys, this is my first post here, so be easy on me =)!

I have two laptops. On one of them I've installed Vista (we'll call this** comp. a**), and the other one which I'm currently on is my Ubuntu laptop (**comp. b**).

Both computers are connected to the same LAN (obviously).** Is it possible for me to connect from comp. a to comp. b without having to install anything on the host machine (comp. b)**? 

I hope I've been clear enough.

Cheers!

---

### Post by paultag on 2008-02-12
out of the box? not likely. 

You can look up current security flaws on Launchpad. If you want shell based access, you can use SSH, or if you want to experiment with cracking, install some old version of a service (apache, etc) and try to break it (read: buffer overflows, etc)

---

### Post by Dr Small on 2008-02-12
No, it isn't possible without first installing some service.

---

### Post by k_grdn on 2008-02-12
Hi,
 
Depends what packages you initially installed, and what services are listening, try netstat -pant to see what tcp services are listening.

Shell:
Install openssh-server on the host b, install putty on the windows box to connect via ssh protocol.

Gui:
Install vncserver on host b, install vncveiwer on windows box, connects port 5900.

The reason for this is ubuntu is secure out of the box, unlike windows distros, you have control of port states.

Regards,

k_grdn

---

### Post by HermanAB on 2008-02-14
No, Ubuntu does a totally boneheaded default install.  You would need to install the OpenSSH server, a FTP server, or something like Netcat.

Alternatively, you could install Filezilla server on the Vista machine.

Cheers,

Herman

---

### Post by paultag on 2008-02-14
boneheaded? Try Secure! Ubunu may not be any OpenBSD ("Only two remote holes in the default install, in more than 10 years!") but Ubuntu has a damn secure default install. Most Linux n00blets will never even notice their machine has no SSH Server.

---

