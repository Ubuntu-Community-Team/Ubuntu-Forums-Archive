---
title: "OpenLdap+Samba Domain Controller on Ubuntu 9.04"
date: 2009-08-29
forum: Server Platforms
---

### Post by fkhan on 2009-08-29
Dear Guys
 
can someone send me step by step to configure OpenLdap+Samba Domain controller on Ubuntu 9.04.
I followed the steps of Samba+OpenLdap domain Controller on Ubuntu 7.10, after reaching to certain point i'm gettng confused.
i.e /etc/ldap/slapd.conf file is missing. How to go for configuration as this file is not there.

---

### Post by HermanAB on 2009-08-29
Read the Official Howto:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

all other howtos should be taken with a pinch of salt...

---

### Post by scorp123 on 2009-08-29
> **fkhan said:**
> /etc/ldap/slapd.conf file is missing. as far as I was told it has only changed the location slightly. Did you follow the thread? Other posters have asked this too and found the file it seems.

---

### Post by scorp123 on 2009-08-29
> **HermanAB said:**
>  all other howtos should be taken with a pinch of salt... That "HowTo" he's talking about is one of the best ever written in this forum.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Also available here:
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

---

### Post by cowmix on 2009-09-07
Hmm.. I just read the guide... and I still can not find my slapd.conf file.

---

### Post by AlexanderDGreat on 2009-09-27
Hi cowmix, I've also done my homework, it seems ALL HOWTOs out there are designed for Ubuntu 8.04 LTS that's why we can't find the /etc/ldap/slapd.conf

This guy on youtube, told me that there's a BIG CHANGE in 9.04 and LDAP, which makes me think if it's even worth the trouble, I'm so confused.

[http://www.youtube.com/watch?v=kSCx3tzC0cA](http://www.youtube.com/watch?v=kSCx3tzC0cA)

Just look for his other video, they're 2 parts.

It seems every other distro-upgrade, Ubuntu breaks something for me, which can be so frustrating. Productivity in our office dimininishes.

Anyway, I've found this tutorial for setting up 9.04 w/ LDAP + SMB PDC:

[http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)

Maybe it can help you, but I won't tinker w/ my box for now, it seems complicated because it requires DELETING something, a "red flag" for me, and possibly a headache in the future.

If you ever find a REAL solution for configuring LDAP on Ubuntu 9.04, can you do us a favor and UPDATE this thread?

Appreciate it a lot if you will.

Thanks and good luck.

---

