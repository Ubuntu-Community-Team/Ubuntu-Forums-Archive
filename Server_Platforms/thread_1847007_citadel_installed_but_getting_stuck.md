---
title: "citadel installed but getting stuck"
date: 2011-09-20
forum: Server Platforms
---

### Post by mosaic2s on 2011-09-20
I have installed citadel earlier on an ubuntu m/c and ran it successfully for sometime.
now i hv setup a desktop ubuntu m/c that can run 24hrs.
on installing citadel, and running the command 127.0.0.1 - i get the following error - screenshot enclosed.

The terminal returns the following error:

> 
ibrahim@DAWOOD:~$ telnet 127.0.0.1 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refusedWhere could be the hitch?
How to release port 2000 for use of webcit?

---

### Post by HermanAB on 2011-09-20
That means that there is nothing listening on port 25, meaning that Citadel is not running - so start it!

[root@neptune ~]# ps -e | grep cit
 6933 ?        00:00:00 citserver
 6934 ?        00:08:29 citserver
 6960 ?        00:00:00 webcit
 6961 ?        00:00:06 webcit
 6963 ?        00:00:00 webcit
 6964 ?        00:00:01 webcit

---

### Post by mosaic2s on 2011-09-20
typed citadel on one terminal.
and then, started another terminal. same response.

> ibrahim@DAWOOD:~$ sudo ps -e | grep cit
[sudo] password for ibrahim: 
 1227 ?        00:00:04 metacity
 1368 ?        00:00:00 citserver
 1374 ?        00:00:01 citserver
 2133 ?        00:00:00 webcit
 2134 ?        00:00:13 webcit

---

### Post by mosaic2s on 2011-09-25
finally swapped hdd where citadel was running fine.
it worked.

then it developed same problem.

then i purged and re-installed citadel as per guidance from here - 
[http://ubuntuforums.org/showthread.php?t=1603715&highlight=citadel+postfix](http://ubuntuforums.org/showthread.php?t=1603715&highlight=citadel+postfix)

it worked again.
so i am sticking with citadel. postfix and dovecot sounds nice but could not get them to work. i would require a GUI for them.

---

