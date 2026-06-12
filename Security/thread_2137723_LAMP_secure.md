---
title: "LAMP secure?"
date: 2013-04-21
forum: Security
---

### Post by zorba9 on 2013-04-21
Hi guys!

I downloaded a LAMP and then couldn't save a file in it's server documents folder; I got a permission denied error. 

I then did a scan with my security program and it found a virus! I thought I got rid of it, but still couln't save to the server's documents folder. However, I also went to a 'suspicous' site but am not sure if that did it.

Thanks for any help here!

---

### Post by cariboo on 2013-04-21
Which directory are you trying to save a file to? The server install doesn't have a /home/$USER/Documents directory.

---

### Post by zorba9 on 2013-04-21
Sorry for saying documents...the directory was home/var/www.

---

### Post by CharlesA on 2013-04-21
Huh? By default you shouldn't have write access to anything outside of your home directory.

If you have the document root for Apache set for /home/var/www, when you'd either have you add yourself to the www-data group, or mess with permissions.

---

### Post by matt_symes on 2013-04-21
Hi

Usually, you cannot write to any directory outside of you home directory. 

This is by design and is part of Ubuntu's security model. 

This is why you cannot write to /var/www

You can only create, move, rename, delete and edit files outside of your home directory by gaining elevated privileges. This requires the use of sudo and gksudo.

Read these documents.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Now you've read those documents :) to move files into /var/www, open a terminal and type 

```
gksudo nautilus
```

Enter your password. You can now copy files into /var/www, When you have finished close nautilus.

You can also press ALT + F2 and type

```
gksudo nautilus
```

to do the same thing.

This assumes you are using Ubuntu and not xubuntu or lubuntu.

_Read up on file permissions and privileges. They are central to how Ubuntu's filing system works._

Kind Reagrds

---

