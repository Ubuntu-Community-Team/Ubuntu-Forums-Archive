---
title: "public dir for samba"
date: 2010-03-28
forum: Server Platforms
---

### Post by Error403 on 2010-03-28
Hello,

I know the last samba update did something to my configurations, but I cannot find how to fix it. Here's the setup: I made a softlink to /var/www in my home directory for ease of use. That went pretty smoothly, until recently. I also made a softlink to a second harddrive, wich contains public stuff for my home users (pictures, games, music, etc). that is also not working anymore.

So, before I worsen my setup, does anyone have an idea to make those two softlinks work again?  Thanks

I'm running Ubuntu Linux 9.10 and Samba 3.4.

---

### Post by Ryan Dwyer on 2010-03-28
I don't get it. What do softlinks have to do with Samba? Are your softlinks inside your Public folder?

---

### Post by Error403 on 2010-03-29
I just dont get it either. The two links are in my home folder

```
lrwxrwxrwx  1 phil phil        8 2010-02-20 20:30 www -> /var/www

lrwxrwxrwx  1 phil phil       18 2010-01-05 23:19 pub -> /mnt/wdc_data/pub/

```

And I could swear that it stopped working after an update, because other computers have the same problem. I don't have trouble accessing by ssh, but they wont even appear in ftp.

---

### Post by Ryan Dwyer on 2010-03-29
So if you type cd www, it doesn't work? What about cd /var/www?

EDIT: Nevermind, just noticed you said it works in SSH. If it doesn't work in FTP I'd be looking through the FTP config to see if there are any options for handling symlinks.

---

### Post by Error403 on 2010-03-31
There, I fixed it with this, if anyone gets the same problem:

```
[global]
wide links = yes
unix extensions = no

```
I got the hint through the logs:
```
 Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.

```


It's supposed to be a "feature" but is in fact a security issue

[http://bbs.archlinux.org/viewtopic.php?id=92183](http://bbs.archlinux.org/viewtopic.php?id=92183)

---

### Post by marslin on 2010-04-01
Thanks. I met same problem and fixed by adding the settings in smb.conf
 
[http://ubuntuforums.org/showthread.php?p=9058590&posted=1#post9058590](http://ubuntuforums.org/showthread.php?p=9058590&posted=1#post9058590)

---

