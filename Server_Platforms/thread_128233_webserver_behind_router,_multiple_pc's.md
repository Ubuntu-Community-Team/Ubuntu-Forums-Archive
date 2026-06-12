---
title: "*webserver behind router, multiple pc's*"
date: 2006-02-11
forum: Server Platforms
---

### Post by kruz on 2006-02-11
hey, say in theory
i have 30 pc's behind a router, so they all essentially have 1 computer

if i setup a bind dns server on one of the computers that had a certain port forward to them
could i make it so that when u connect to that main server, u can acess other servers?

okay
say pc 1 is the server, that is the DMZ host, and its ip is 192.168.1.100

and i have other computers, that are essentially ghost to the outside world
192.168.1.101-200
and they all have vnc servers running on them
could i setup a dmz server to where if i connect to

username.pc1'sexternalwebsite.com then it would go to that computer inside the network??

any other suggestions

thanx

---

### Post by bastya_elvtars on 2006-02-11
So you have a natbox, right? And wanna redir to a specific host. I would add the  hostname to the hosts file of the natbox and do a portforward.

---

### Post by kruz on 2006-02-12
the problem is im hosting vnc servers on all of them
so i cant forward 5900 to all of them? that wouldnt work

u can only forward to one pc for it to respond
tha tmake since?

---

### Post by henryv on 2006-02-14
[QUOTE=kruz]the problem is im hosting vnc servers on all of them
so i cant forward 5900 to all of them? that wouldnt work

u can only forward to one pc for it to respond
tha tmake since?[/QUOTE]
Hi all

Maybe you could read something on the following page 

[http://ultravnc.sourceforge.net/addons/index.html](http://ultravnc.sourceforge.net/addons/index.html)

It seems me that it could do something for you.
I have no expireinces with this NAT and repeater stuf it but a single ultraVNC does a good job  for me.

---

