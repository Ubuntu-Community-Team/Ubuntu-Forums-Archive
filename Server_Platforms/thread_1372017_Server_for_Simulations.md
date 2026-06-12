---
title: "Server for Simulations"
date: 2010-01-04
forum: Server Platforms
---

### Post by umeboshi80 on 2010-01-04
Hi

I am a total newbie and have some server confusions. I would like to run long simulations on my desktop computer and would like to be able to be able to access the computer remotely so that I won't have to be there physically. I decided to install the desktop version and are planning to install server applications. Now there comes my confusion: LAMP, OpenSSH, Samba, etc. ? Which one is the best to install for my puporse? I would like 

Thanks for any comments!

---

### Post by BkkBonanza on 2010-01-04
Well they each do completely different things. Install the ones you need...

LAMP - Apache, Mysql, PHP - to run a web site
OpenSSH - to eneble ssh access to server (probably something you want)
Samba - share files with Windows machines on network

---

### Post by umeboshi80 on 2010-01-04
Thanks! I will probably want people to able to access it from their windows computer as well so Samba is great. What does VNC do? Also, is there a possibility for a windows user not on the network to monitor their simulations on the server?

Thanks again for any comments!

---

### Post by BkkBonanza on 2010-01-04
VNC allows remote access to desktop. 
If a user is not on the network how could they possibly monitor their simulations? I mean short of walking over to the computer and looking at it. Are you thinking dial-in modem or something?

---

### Post by umeboshi80 on 2010-01-04
Thanks. As I said, I am quite clueless. I have only experience with SSH on Windows. And I probably, without knowing, was always using it being on the university network. If someone wants to access the computer from outside of the university network, how is that possible?
So both VNC and OpenSSH allow remote access over the network? Wonder, which one is better for me purposes...

Thank you :D!

---

### Post by BkkBonanza on 2010-01-04
Both SSH and VNC can be used from anywhere in the world via internet. But to get to the internet the user has to be networked somehow/somewhere. So both of these methods are good for you. 

SSH is command line based but very capable and secure.

VNC is desktop oriented so gives you graphics - though it can be painfully slow depending on the connection. VNC should be run on top of SSH to provide security otherwise the protocol is open to monitoring by other parties.

Another method is to use X forwarding over SSH. This works well when you have X running on the remote end (always in Linux desktop or special install if windows).

---

### Post by umeboshi80 on 2010-01-04
Cool, that answered all my questions! Thanks a lot!

---

