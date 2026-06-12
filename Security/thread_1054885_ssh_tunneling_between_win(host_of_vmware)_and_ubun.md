---
title: "ssh tunneling between win(host of vmware) and ubuntu inside vmware ?"
date: 2009-01-30
forum: Security
---

### Post by kirb on 2009-01-30
Hello ubuntu fans! My question is if i can make a ssh tunnel between the host(windows) and ubuntu (in vmware) in order to "get out" in LAN  with encrypted data? I hope my question is clear cuz i am kinda new to linux.
Thank's !

---

### Post by Branimir on 2009-01-30
I did it with cygwin on windows.
It is ssh -L option as I can remember. Host was not in vmware
and was not ubuntu rather centos, but sshd is same ?

Greetsa, Branimir.

---

### Post by kirb on 2009-01-30
I did this some time ago with bitvise and sockscap the problem is that i was connecting with bitvise at my remote server, then open app need to be tunneled through sockscap.
What i don't know is how can i asign a local ip like 192.168.0.23 to ubuntu inside vmware and then try the upper steps for get in LAN encrypted from the win OS

---

