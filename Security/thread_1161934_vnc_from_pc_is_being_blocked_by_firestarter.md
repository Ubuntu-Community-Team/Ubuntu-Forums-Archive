---
title: "vnc from pc is being blocked by firestarter"
date: 2009-05-17
forum: Security
---

### Post by jp64 on 2009-05-17
I use Ubuntu 9.04
I use firestarter allowing some traffic. I've opened VNC (5500-5600 + 5900) and allowed all my pc's to connect by allowing 192.168.1.100/29 ánd 192.168.1.101 (the laptop I use for remote management - XP based). Outgoing traffic is not blocked.
When I stop FS, I can connect via VNC and the connection is up even if I turn FS ON again. After a while FS blocks the laptop/VNC and i cannot reconnect via VNC.
I use wlan.
 
What am I doing wrong?

---

### Post by lovinglinux on 2009-05-17
Check the blocked connections log to see which connections are blocked immediately after turning on Firestarter and VNC.

---

### Post by jp64 on 2009-05-17
There are no messages. Even after a reload I see no new messages. It looks as if everything works properly; but still no connection.

---

### Post by lovinglinux on 2009-05-17
Just to let you know, Firestarter is not recommended anymore. You should remove it and try gufw. Go to the "Add/Remove" manager, search for "gufw" and install the "Firewall Configuration" application.

Both Firestarter and GUFW are just firewall managers. They alllow you to create rules for the real firewall, which is the iptables, without knowing the commands.

Additionally, running Firestarter all the time, might be a security risk, since it requires root access. Once you configure Firestarter you can close it, because the iptables will do the work on the background.

---

### Post by jp64 on 2009-05-17
Hi,
 
thanks. You're right with the iptables. I'll stop FS. I will take a look at gufw.

---

### Post by HermanAB on 2009-05-17
Howdy,

Well, actually VNC is a really bad security hole, so it is a good thing that Firestarter blocked it.  Every time someone on these forums has a long and sad tale of woe about his machine getting hacked, it is due to running VNC server and forgetting about it.

If you want to connect to your machine remotely, use SSH Server.  It can do everything that VNC does plus much, much more and it is secure by default.

---

### Post by lovinglinux on 2009-05-17
> **HermanAB said:**
> Howdy,

Well, actually VNC is a really bad security hole, so it is a good thing that Firestarter blocked it.  Every time someone on these forums has a long and sad tale of woe about his machine getting hacked, it is due to running VNC server and forgetting about it.

If you want to connect to your machine remotely, use SSH Server.  It can do everything that VNC does plus much, much more and it is secure by default.

+1 for ssh

If you really need vnc, then you can tunnel it through ssh.

---

