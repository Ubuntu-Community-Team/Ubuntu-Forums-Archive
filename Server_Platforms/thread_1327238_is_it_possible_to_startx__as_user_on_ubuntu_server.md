---
title: "is it possible to startx  as user on ubuntu server"
date: 2009-11-15
forum: Server Platforms
---

### Post by shred_eng on 2009-11-15
hi, i installed xorg on ubuntu server 9.04 , i know its not a very good idea but its what i want  ;) 

only problem is, i can only startx using sudo, i tried adding single to grub but that never worked, ive googled for an answer but found nothing helpful, 

so..is it even possible?

 any suggestions will be welcomed

thx,

---

### Post by hictio on 2009-11-15
Have you tried starting the X server as a regular user as well? I mean, to see if that works at all?
Login to your box, as a regular user, and type at the console:

```

X ENTER

```

To kill gracefully type Ctrl + Alt + Backspace.

---

### Post by shred_eng on 2009-11-15
yeah, ive tried logging in as normal user but get lots of errors when i type startx , mostly permission stuff, 

i changed the permissions on a few folders and files including /var/log/  and  Xwrapper.config (i think its called) but i wish i didnt have to do that.
 although x still refuses to start it only seems to only have one error now which is : cannot open (or  similar) /var/log/log.0.log, even if i change permissions on that file it tries to create another one and complains it cant write to that either. so it goes on....

thx,

---

### Post by shred_eng on 2009-11-17
after googling around using different keywords i finally found a solution that worked for me, simply remove xorg then reinstall it - i have no idea why it worked but it did, now i can startx as user  :D

however just a small thing...when i created a new user the x shell doesnt have the users name@server but instead has  sh-3.2,

all other (2) users have their name - why is this? and can i change it so it reads: user@server

thx,

---

### Post by sisco311 on 2009-11-17
> **shred_eng said:**
> 
however just a small thing...when i created a new user the x shell doesnt have the users name@server but instead has  sh-3.2,

all other (2) users have their name - why is this? and can i change it so it reads: user@server

thx,

set bash as the user's new login shell:

```
sudo usermod --shell /bin/bash *username*
```

---

### Post by shred_eng on 2009-11-17
thanks sisco311  :D  that was the last piece in my puzzle,

everything is working the way i want it to now...\\:D/

---

