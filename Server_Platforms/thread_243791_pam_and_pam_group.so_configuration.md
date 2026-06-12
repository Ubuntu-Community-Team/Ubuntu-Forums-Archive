---
title: "pam and pam_group.so configuration"
date: 2006-08-25
forum: Server Platforms
---

### Post by helmet on 2006-08-25
i'm having problems configuring pam_group.so

i am under the impression that this is how i would add users to groups upon login. i need to add anybody logging in through gdm to groups plugdev,audio,video,cdrom

this is what i put in my /etc/security/group.conf

```
gdm;*;*;Al;plugdev,audio,video,cdrom
login;*;*;Al;plugdev,audio,video,cdrom
```

add added this to /etc/pamd.c/common-auth

```
auth     optional        pam_group.so
```

but no dice. i've tried adding other things to group.conf but can't get it to add anybody to anything. what am i doing wrong?

---

### Post by tousoxeu on 2006-12-11
I found that :
[http://www.debian-administration.org/articles/308](http://www.debian-administration.org/articles/308)

it worked once on my computer, i'm trying to reproduce it right now
but i can't tell you which /etc/pam.d/ files to insert the line
```
auth	optional	pam_group.so
```
i tried many, it worked
(currently common-account, common-auth, gdm, gdm-autologin, login)

but the /etc/security/group.conf is like that :
```
gdm; *; *; Al0000-2400; audio, video, cdrom, floppy, plugdev
```

Edit : works fine after restarting gnome

---

