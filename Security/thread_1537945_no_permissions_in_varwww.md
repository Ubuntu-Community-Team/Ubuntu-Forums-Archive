---
title: "no permissions in /var/www"
date: 2010-07-24
forum: Security
---

### Post by dcurtis11 on 2010-07-24
I just installed Ubuntu workstation into VMware and then installed Apache, Mysql, PHP, and phpmyadmin.
I am able to access Apache from any computer in my home so there is not issue there.

The issue I am facing is when I try to copy anything into /var/www/ I get a permission denied messsage.
I added myself to the administrators group and then rebooted but still get the same message.

I was able to access it by using the following command...
gksu nautilus

I don't want to have to do that every time. I would like to be able to access it by just opening "Documents" and the selecting "file system" inside of Nautilus.

Any help would be greatly appreciatied.

---

### Post by Bachstelze on 2010-07-24
You can give yourself ownership (and therefore, write permission) to /var/www with

```
sudo chown `whoami` /var/www
```

Or in the Properties panel in root Nautilus.

---

### Post by ks07 on 2010-07-24
You need to give yourself privileges and/or ownership of the folder to be able to write to /var/www. However, be warned that changing permissions on the /www folder can cause security problems if set up in certain ways - e.g. allowing everyone read/write access would allow someone on the outside to change your files.

That aside, one possibility would be to make the www folder owned by you, by using ```
chown yourusername /var/www/
``` Obviously replace yourusername with whatever your user is called.

Be warned though that I haven't tested this myself, so you may want to wait for someone else to reply with a better solution. If you're desperate however, this *should* work. ;)

EDIT: Looks like I was beaten to it while I was writing! :p

---

### Post by dcurtis11 on 2010-07-24
Thanks Guys, your awesome!!
That worked!

---

### Post by bodhi.zazen on 2010-07-24
Personally I keep files in /var/www owned by either root or www-data.

IMO better to add your user to the www-data group then change the permissions of /var/www

---

