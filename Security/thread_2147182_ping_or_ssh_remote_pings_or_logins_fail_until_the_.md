---
title: "ping or ssh: remote pings or logins fail until the first local login"
date: 2013-05-21
forum: Security
---

### Post by cppgent0@gmail.com on 2013-05-21
I'm posting this even though it's already solved. Hopefully it will save other folks a bit of time.

**Set up:**
There is a server and a client PC on the same network.
Server is Ubuntu 10.04, fresh install (mine had a static IP address, but I believe that doesn't matter)
Client is Ubuntu 12.04 (or any)

**Steps to Reproduce:**[INDENT]1) reboot server; do not log in

2) ping the server from the client PC
[ping fails]
3) ssh to the server from the client PC
[ssh also fails][/INDENT]
[INDENT]
4) login locally to the server

5) ping the server from the client PC
[ping succeeds]
6) ssh to the server from the client PC
[ssh now succeeds][/INDENT]

It seems this is a common problem, here are some similar posts:[INDENT][http://ubuntuforums.org/showthread.php?t=1225436](http://ubuntuforums.org/showthread.php?t=1225436)
[http://ubuntuforums.org/showthread.php?t=1294024](http://ubuntuforums.org/showthread.php?t=1294024)
[http://ubuntuforums.org/showthread.php?t=1156633](http://ubuntuforums.org/showthread.php?t=1156633)
[https://answers.launchpad.net/ubuntu-vancouver-loco-tech-support/+question/153213](https://answers.launchpad.net/ubuntu-vancouver-loco-tech-support/+question/153213)
(and more)[/INDENT]

**Solution:**
The network connection needs to be shared otherwise it won't be accessible until the user who owns it logs in. Having said that now, it seems obvious, but at the time, it wasn't clear.

**Steps to Fix:**
So, using the Server's GUI:[INDENT]1) Login to server
2) clickNetwork Manager icon
3) click Edit Connections
4) click on the network connection the server uses when it starts up (usually only one in there)
5) check the "Available to all users" box
6) click Save
(you may have to enter a password somewhere in this sequence)
7) reboot  (Do not login)[/INDENT]

Test: Try the ping and ssh from your client PC. Should work now.

Notes:
- Sorry, but I don't know how to do this without a GUI.
- Network Manager has changed in 12.04 but the steps above are still roughly applicable

John

---

