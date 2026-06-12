---
title: "Dedicated Server GUI Problem"
date: 2010-04-19
forum: Server Platforms
---

### Post by davidhopkins on 2010-04-19
Hello Guys,  I have myself a new dedicated server running Ubuntu.   I have been reading these forums a fair bit trying to get a GUi installed on it.  I have got so far but it seems to have a error to which i am unsure how to fix.

Basically i have installed the desktop and gdm, when i use the startx command i get an error:

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
If this server is not longer running, remove /tmp/.X0-lock and start agaiin.

Please consut the THE X.Org foundation for support.
ddsxSigGiveUp :Closing Log
Invalid MIT-MAGIC COOKIE-1 keygiving up.
xinit: interrupted system call (errno 4): unable to connect to X server
xinit: no such process (errno 3); server error



ANy ideas on how to fix it?

Thanks in advance

---

### Post by HermanAB on 2010-04-19
Howdy,

Delete the lock file, kill all running instances of X and try again.

So how do you know what is running?
$ sudo ps -e
1234 X

and how do you kill it?
$ sudo kill -9 1234

---

### Post by davidhopkins on 2010-04-20
Thanks for the reply, im sorry but how do i delete the lock file? I am a complete new users =[

---

### Post by HermanAB on 2010-04-20
$ sudo rm /tmp/.X0-lock

---

