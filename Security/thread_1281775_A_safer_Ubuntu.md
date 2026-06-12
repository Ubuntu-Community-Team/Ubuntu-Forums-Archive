---
title: "A safer Ubuntu"
date: 2009-10-03
forum: Security
---

### Post by vvfrn on 2009-10-03
My best friend notified me that he had several attempts to log unto hir system but they were denied (ubuntu).
How do I make my system safer since I am using this computer as my person banking computer. Any attempt to get on this  can ruin my  financial life forever! How do I check my attempt logs and what do I  install? :)

---

### Post by vvfrn on 2009-10-03
My friend told me that someone tried to enter his system but thankfully, Ubuntu's firewall denied access to it. Well, I want to know what are some precautions I can take to avoid this happening to me! I already know how to see my attempt log even though I do not:K know how to decipher it. I would like to know what software to install to make my computer safer!:KS
Thanks from the Ubuntu fan(been on Ubuntu for 2 months and loving it)

---

### Post by aysiu on 2009-10-03
This should help you out:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by vvfrn on 2009-10-03
Thanks for your time but I already went through  that however, I can not really keep up on what it is saying just the firestarter part since  I know loads on that!

---

### Post by aysiu on 2009-10-03
Just stick with the default settings and you'll be fine.

Don't mess with ports or firewalls. Don't enable any listening services (OpenSSH, for example).

You'll be fine.

---

### Post by Mourvedre on 2009-10-03
Start reading up on Security: 

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/) is a good place to start.

---

### Post by credobyte on 2009-10-03
If they all ( attempts ) were denied ( blocked ), why to bother ?

```

sudo ufw enable
sudo ufw default deny
```Now you are safe :p

---

