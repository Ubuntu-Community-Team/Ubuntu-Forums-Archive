---
title: "Can't open etc shadow"
date: 2007-06-20
forum: Server Platforms
---

### Post by fuzzypig on 2007-06-20
I am suddenly getting strange errors regarding /etc/shadow on ubuntu server 6.10.

root@fuzzypig:/etc# pwconv
pwconv: can't open shadow file

root@fuzzypig:/etc# pwck
pwck: cannot open file /etc/shadow

root@fuzzypig:/etc# useradd test
useradd: cannot open shadow password file


This started when I tried to install sendmail, and dpkg didn't finish because it couldn't access the shadow file during sendmail-base configuration.

I have confirmed that the /etc/shadow file exists, and all looks fine inside. Even stranger, my Google searches could not find a single occurrence of this problem elsewhere.

Does anyone have the slightest idea what the problem is?

Edit: Sorry, looks like I posted this in the wrong place.

---

### Post by Mr. C. on 2007-06-20
Show output from:

```
ls -l /etc/shadow
lsattr /etc/shadow
```

MrC

---

### Post by fuzzypig on 2007-06-20
Sorry, too late. I already reinstalled the system. It's a newer version anyway.

Thanks anyway,
Michael "Fuzzypig" Reiley

---

### Post by zaedi_ahmed on 2008-05-25
I have also faced the same problem.

useradd: Cannot open /etc/shadow file.

and the ls -ali shows

read write permission for root but couldn't open.

Can any one help me.....

And 

ls -l /etc/shadow       

shows : -rw-r--r--   for shadow

lsattr /etc/shadow

shows : ----------   for shadow
Thanks in advance

---

