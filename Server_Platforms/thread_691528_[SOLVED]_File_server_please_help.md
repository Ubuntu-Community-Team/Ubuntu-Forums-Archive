---
title: "[SOLVED] File server please help"
date: 2008-02-08
forum: Server Platforms
---

### Post by mr tim esquire on 2008-02-08
Hi there, 

Ive installed ubuntu server on an old machine I want to use it as a file server to access my old files from my dual boot Ubuntu/XP PC.

I can SSH in fine and Putty in OK from Windows and i have installed Samba.
I tried following [Stormbringer's guide]("http://ubuntuforums.org/showthread.php?t=202605") But when i tried to map the network drive in windows i got a "extended error" message.

on Ubuntu i try to navigate to the share but i get error messages.

I have give the server a static IP

How can i map the server drives to my windows or Ubuntu system? ssh is a pain!

thanks!

---

### Post by faulkes on 2008-02-08
Please post the error messages you received so we can better understand the problem you are encountering.

Faulkes

---

### Post by mr tim esquire on 2008-02-08
in ubuntu nautalus

```
The folder contents could not be displayed.

Sorry, couldn't display all the contents of "farmyard".
```

---

### Post by faulkes on 2008-02-08
Sounds like a permissions issue on the windows side of things.  The user you are logged in with on the ubuntu machine should match the user on the windows machine.  If that is correct, check the permissions of the drive/folder you are sharing on windows (although that id dependent upon how the drive on windows is shared)

Also note, that in some cases if nautilus asks for a username/password, the first time you enter it, it will fail, the second attempt will succeed.

Faulkes

---

### Post by mr tim esquire on 2008-02-09
i have samba woking from ubuntu naw after following this guide:
[http://www.melbpc.org.au/pcupdate/2403/2403article7.htm](http://www.melbpc.org.au/pcupdate/2403/2403article7.htm)

---

