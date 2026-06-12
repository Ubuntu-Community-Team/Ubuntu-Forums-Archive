---
title: "runngin prog as own user + autostart at booting, how?"
date: 2005-03-22
forum: Server Platforms
---

### Post by sonium on 2005-03-22
Hi,
I want to build an [Asterisk]("http://www.asterisk.org") Server. So I have installed tha Asterisk package by Synapting. After looking in /etc/passwd I found it made hisself an new account
```
asterisk:x:115:115:Asterisk PBX daemon,,,:/var/lib/asterisk:/bin/false
```
fine.
1. how do I start the program using this account?
2. how do I setup the program to start at boot time using this account?

- Sonium

---

### Post by alastair on 2005-03-24
You can run a command as another user using "su". See : man su

But you might be best looking at the docs for the s/w. There might be some docs in /usr/share/doc/asterisk*, or some man pages installed that will help you.

---

