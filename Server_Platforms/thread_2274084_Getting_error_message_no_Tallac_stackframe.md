---
title: "Getting error message no Tallac stackframe"
date: 2015-04-17
forum: Server Platforms
---

### Post by Mike_Hughes on 2015-04-17
I am trying to set up a new Web Server. My old 32 bit one bit the dust so trying to set up a new 64 bit. I installed Ubuntu 14.04 LTS server. I then wanted to use apt-get and download the lamp server files. When I put in sudo apt-get i get a message back that says no talloc stackframe at ../source3/param/;pad[arm.c:4864, leaking memory. E: Invalid operation apache2.

Any help or ideas appreciated.

---

### Post by Doug S on 2015-04-17
> **Mike_Hughes said:**
>  i get a message back that says no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memoryThat part is an [annoying bug ]("https://bugs.launchpad.net/ubuntu/trusty/+source/samba/+bug/1257186")that has been around for over a year now. Basically it is harmless.> **Mike_Hughes said:**
> E: Invalid operation apache2.That part, I don't know.

---

### Post by bab1 on 2015-04-18
> **Doug S said:**
> That part is an [annoying bug ]("https://bugs.launchpad.net/ubuntu/trusty/+source/samba/+bug/1257186")that has been around for over a year now. Basically it is harmless.

The error is due to some assumptions made by the Ubuntu Server installer when you installed the Samba server via *tasksel*.  The assumption (and therefore the bug) is that you are going to provide domain wide user management with Samba.  

@ Mike_Hughes;  you might check to see if you have libpam-winbind installed and remove that first.  It may solve the problem.  If not then you can get rid of the error message by removing libpam-smbpass with this terminal command ```
sudo apt-get remove libpam-smbpass
``` 

My assumption is that libpam-winbind is needed for domain user management and libpam-smbpass is a dependency.  Some folks have reinstalled only libpam-smbpass to manage the Samba users password synchronization.  Not very clear I know, but Samba has more than just file sharing ability

---

### Post by steeldriver on 2015-04-18
The message

```

E: Invalid operation apache2

```

suggests your apt-get command is missing the action (install, remove, purge etc.) e.g. 

```

sudo apt-get **install** apache2

```

---

