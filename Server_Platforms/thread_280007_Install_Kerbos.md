---
title: "Install Kerbos?"
date: 2006-10-18
forum: Server Platforms
---

### Post by cwhitmore on 2006-10-18
I want to setup a SAMBA share that authenticates users from Active Directory so I need to install Kerbos. What packages do I need to install to get this working?

---

### Post by bswilson on 2006-10-18
I don't know how to do what you're asking about; but I think the software you need is called **kerberos** (spelling).  The packages on ubuntu that are available can be found with this command:

```
$ sudo apt-cache search kerberos
```

---

### Post by cwhitmore on 2006-10-19
Oops, 
you're right. Too many glasses of wine!

---

### Post by bswilson on 2006-10-19
Hey there.  I was reading the Ubuntu server guide and found a great many details that should help you connecting your Ubuntu system (and users) to a Microsoft AD environment.  Check this out!

[https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html)

I think this is **exactly** what you wanted...

---

### Post by cwhitmore on 2006-10-19
Thanks, I found that as well, but that document doesn't give me the names of the Kerberos package names to install.
I tried running the find command that you sent, but there are like 15 of them and I'm not sure which ones to install.
Any ideas?

---

### Post by cwhitmore on 2006-10-20
I had the wrong sourcelist options:
[http://www.ubuntuforums.org/showthread.php?t=280702&highlight=kerberos+on+dapper](http://www.ubuntuforums.org/showthread.php?t=280702&highlight=kerberos+on+dapper)

Works now.

---

### Post by Abhi Kalyan on 2006-10-25
Hi cwhitmore.
is it entirely necessary to have the users authenticated to access your share?
Cause am doing using it as a normal share, type path and the share is available.
This is a serious Doubt.
If its not big trouble could you please help?

---

### Post by cwhitmore on 2006-10-25
Abhi,
I wanted to setup a share on my laptop so users could backup their files/settings from Windows 2k before upgrading and wanted to limit access to only domain users, but you can setup a share that allows anyone access. 
I'm not familiar with the command line, but for an easier way to setup the share load the desktop on Ubuntu (sudo apt-get install ubuntu-desktop), if you don't already have it loaded and open  Places, Home directory (to get to the folder you want to share), and RIGHT mouse click the folder you want to share. One of the options is "Share Folder". 
I'm sure someone on this forum knows a cleaner way of doing this, but I'm new to Linux.
Good luck.

---

### Post by Abhi Kalyan on 2006-10-26
thank you cwhitmore,
Understood better.
Thank you once again.

---

