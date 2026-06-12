---
title: "LTSP lts.conf not working"
date: 2008-07-06
forum: Server Platforms
---

### Post by wonk-o-matic on 2008-07-06
Running Hardy Heron 8.04 Edubuntu.  

In /opt/ltsp/i386/etc/lts.conf I have: 
```
[default]
    SCREEN_07=shell
```
but I still get a graphical login screen.  

Does this particular shell option simply not work on screen 7?  

Or, has my lts.conf lost its magical configuration powers?

---

### Post by wonk-o-matic on 2008-07-07
Holiday weekend, no responses, I understand that.  How about now?

---

### Post by BoeBoe on 2008-08-07
Hi wonk,

After changing your lts.conf in /opt/ltsp/i386/etc, you need to run ltsp-update-image to put it in effect.

In ltsp 5, you can actually make changes to lts.conf without running ltsp-update-image, but you need to move the lts.conf to /var/lib/tftpboot/ltsp/i386.

cheers

---

