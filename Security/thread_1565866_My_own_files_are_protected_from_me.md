---
title: "My own files are protected from me"
date: 2010-09-01
forum: Security
---

### Post by dudemanguy333 on 2010-09-01
I have been a user of ubuntu for a while, but of course I have run into problems like I would never see myself when trying to coordinate my mom using it...

She has files that were saved in a previous installation on a different harddrive. That hard drive is still in the computer as a secondary one, but the permissions on the files are not aligned with the users that are on the current operating system. How do I change users to users that don't exist anymore in order to access those files? If only I could just put in a password!

---

### Post by apmcd47 on 2010-09-01
I'm assuming this is on Linux, given the forum.
```
chown -R user.group *
```
The -R is to recusively go down the directory tree. user.group are the names of the user and group your mother's account belong to.

However, if you are talking about a Windows system: As administrator, take ownership of the files then give full control to the actual user.

Andrew

---

### Post by CharlesA on 2010-09-01
The correct syntax is:

```
sudo chown -R user:group /path/to/directory
```

---

### Post by BkkBonanza on 2010-09-01
Just be sure to only target files you want to change. If you do this in the wrong place or at a higher level directory you could "mocha frappe" a lot of files on the system.

---

