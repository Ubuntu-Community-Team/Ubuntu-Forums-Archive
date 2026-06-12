---
title: "Help Setting Up Remote Access/Desktop"
date: 2009-07-16
forum: Server Platforms
---

### Post by TheKLB on 2009-07-16
Just starting out in the linux game, so my knowledge is limited.

I have a remote server running Ubuntu. Im trying to get Gnome up and running and be able to use remote access from a Windows machine. The only access I have now is through SSH (via putty). Is there a guide somewhere I can follow to help me set this up? 

Just really confused right now with all the methods and such that I have found while trying to get this going. Im having alot of issues with:
```
xauth:  error in locking authority file /home/admin/.Xauthority
```
And errors like it



Thanks in advance :popcorn:


EDIT: was finally able to get GDM to start. When I try 'startx' i get:
> admin@xxxxx:~$ startx
xauth:  /home/admin/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/admin/.Xauthority
xauth:  error in locking authority file /home/admin/.Xauthority
xauth:  error in locking authority file /home/admin/.Xauthority
X: user not authorized to run the X server, aborting.
xinit:  Server error.
xauth:  error in locking authority file /home/admin/.Xauthority
Couldnt get a file descriptor referring to the console


---

### Post by juancarlospaco on 2009-07-16
**ssh -X user@servers-ip appYouWantToRun**

in example:

**ssh -X user@server-ip nautilus**

you can try it into yourself if you have openssh-server:

ssh -X $USER@127.0.0.1 xload

Its Secure, because its encrypted, if you want to use it over Internet,
maybe is usefull to add Compression to the data flow by adding the **-C** parameter on ssh.

---

### Post by TheKLB on 2009-07-16
Sorry, forgot to include that I am connecting from a Windows based system 

X-D

---

### Post by juancarlospaco on 2009-07-16
*so ...?*

OpenSSH for Windows and Xming for Windows

---

### Post by HermanAB on 2009-07-16
Here is the trick:
You need to run Xming first, before you start PuTTY.

---

