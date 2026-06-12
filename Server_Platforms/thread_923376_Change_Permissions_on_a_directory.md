---
title: "Change Permissions on a directory"
date: 2008-09-18
forum: Server Platforms
---

### Post by vegas588 on 2008-09-18
Read only
File /etc/xinetd.d/swat not changed so no update needed
jamesc@UbuntuServer1:/etc/xinetd.d$ cd /etc/xinetd.d
jamesc@UbuntuServer1:/etc/xinetd.d$ ls -l
total 24
-rw-r--r-- 1 root root  798 2007-12-03 19:19 chargen
-rw-r--r-- 1 root root  660 2007-12-03 19:19 daytime
-rw-r--r-- 1 root root  549 2007-12-03 19:19 discard
-rw-r--r-- 1 root root  580 2007-12-03 19:19 echo
drwxr-xr-x 2 root root 4096 2008-09-18 10:21 swat
-rw-r--r-- 1 root root  727 2007-12-03 19:19 time


I need to edit the swat directory but everytime I try to go into it, I get a read-only message. How do I implement the correct permissions to edit this directory?

---

### Post by Krupski on 2008-09-18
> **vegas588 said:**
> Read only
File /etc/xinetd.d/swat not changed so no update needed
jamesc@UbuntuServer1:/etc/xinetd.d$ cd /etc/xinetd.d
jamesc@UbuntuServer1:/etc/xinetd.d$ ls -l
total 24
-rw-r--r-- 1 root root  798 2007-12-03 19:19 chargen
-rw-r--r-- 1 root root  660 2007-12-03 19:19 daytime
-rw-r--r-- 1 root root  549 2007-12-03 19:19 discard
-rw-r--r-- 1 root root  580 2007-12-03 19:19 echo
drwxr-xr-x 2 root root 4096 2008-09-18 10:21 swat
-rw-r--r-- 1 root root  727 2007-12-03 19:19 time


I need to edit the swat directory but everytime I try to go into it, I get a read-only message. How do I implement the correct permissions to edit this directory?

If you want to make the directory read/write for all users... do this:

```

sudo chmod 0777 /etc/xinetd.d/swat

```

-- Roger

---

### Post by vegas588 on 2008-09-18
and then to change it back to its original settings?

Thanks.

---

### Post by vegas588 on 2008-09-18
I just tried to go into it and it still says Read Only

---

### Post by vegas588 on 2008-09-18
Read only
File /etc/xinetd.d/swat not changed so no update needed
jamesc@UbuntuServer1:/etc/xinetd.d$ cd /etc/xinetd.d
jamesc@UbuntuServer1:/etc/xinetd.d$ ls -l
total 24
-rw-r--r-- 1 root root  798 2007-12-03 19:19 chargen
-rw-r--r-- 1 root root  660 2007-12-03 19:19 daytime
-rw-r--r-- 1 root root  549 2007-12-03 19:19 discard
-rw-r--r-- 1 root root  580 2007-12-03 19:19 echo
drwxrwxrwx 2 root root 4096 2008-09-18 10:21 swat
-rw-r--r-- 1 root root  727 2007-12-03 19:19 time
jamesc@UbuntuServer1:/etc/xinetd.d$


This is what it looks like now. When I enter the command sudo joe /etc/xinetd.d/swat and it opens, it reads at the top Error reading file. I then hit Ctrl+C and it reads Read Only at the bottom of the screen

---

### Post by Krupski on 2008-09-18
> **vegas588 said:**
> I just tried to go into it and it still says Read Only

If you are trying to "go into" that directory as a normal user (rather than root), maybe the user account doesn't have the proper group permissions (although 0777 should allow everyone in)..

:confused:

Call me confused.

---

### Post by Krupski on 2008-09-18
> **vegas588 said:**
> Read only
File /etc/xinetd.d/swat not changed so no update needed
jamesc@UbuntuServer1:/etc/xinetd.d$ cd /etc/xinetd.d
jamesc@UbuntuServer1:/etc/xinetd.d$ ls -l
total 24
-rw-r--r-- 1 root root  798 2007-12-03 19:19 chargen
-rw-r--r-- 1 root root  660 2007-12-03 19:19 daytime
-rw-r--r-- 1 root root  549 2007-12-03 19:19 discard
-rw-r--r-- 1 root root  580 2007-12-03 19:19 echo
drwxrwxrwx 2 root root 4096 2008-09-18 10:21 swat
-rw-r--r-- 1 root root  727 2007-12-03 19:19 time
jamesc@UbuntuServer1:/etc/xinetd.d$


This is what it looks like now. When I enter the command sudo joe /etc/xinetd.d/swat and it opens, it reads at the top Error reading file. I then hit Ctrl+C and it reads Read Only at the bottom of the screen

Ah... I just looked up what "swat" is.

Why are you using that? The samba config file is EASY to setup... just ask!

The more you do with the CLI, the more you will learn.

The mechanic knows more about cars than the driver... get under that hood!  :)

---

### Post by vegas588 on 2008-09-18
I just wanted some kind of gui to understand all of the various options within Samba.

I have been reading all kinds of posts on all kinds of forums about how to configure Samba, but have been lost. Granted I am new to Linux, but it seems that I am reading too much! Definitely need a helping hand so that I can get some basic connectivity between my windows xp box and this ubuntu server.

---

