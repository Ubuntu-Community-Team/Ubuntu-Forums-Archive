---
title: "Password to short and unable to change it"
date: 2008-11-21
forum: Security
---

### Post by bismark on 2008-11-21
I noticed a serious issue on my box and I don't know where it came from.  I installed my system with a temporary user, then created a new user for myself. This was so I could create a user with a specific UID to match all my other systems and backed up files. So far so good.

I just noticed today however that I typed my password wrong on a sudo command and it accepted it.  After testing it I noticed that my password is set as only the first 8 characters of my actual password (15 characters).  This seems to be a slight issue to me. If I type my password wrong it should stop me period, even if the first part of the "password" I type is correct.  Foobar123 != Foobar12 but right now Foobar123 would allow me to login.

I don't know how this happened but I'm guessing maybe the GUI user management tool chopped it (haven't tested anything yet).

Also noow I can't seem to change it.  Running chpasswd from a terminal gives me the following:```
$ chpasswd
chpasswd: can't lock password file
``` and running System->Preferences->About Me->Change Password hangs upon clicking "Change password".


Update: I was able to change my password using System->Administration->Users and Group. Also it's passwd not chpasswd.... duh
Uddate 2: Once I changed my password sudo and login do NOT except longer passwords as valid. Going to rebuild a new machine and repeat what I've done to see if I can recreate this.

---

