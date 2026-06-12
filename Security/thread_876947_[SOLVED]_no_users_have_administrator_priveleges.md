---
title: "[SOLVED] no users have administrator priveleges"
date: 2008-08-01
forum: Security
---

### Post by johnr9 on 2008-08-01
I am sorry if this is the wrong place to post, but I had administrator rights for my machine running ubuntu 7.10, I am the only user with administrator  rights and i clicked on users and groups and my user name and properties etc. and unclicked the checkbox  administer the system; there was no error message and now no users have administrator rights, and apparently I cannot undo the action.
What do I do?

---

### Post by Dr Small on 2008-08-01
Reboot, and at the GRUB menu, boot into Recovery Mode.
From there, you will be taken to the root prompt. If I am not mistaken, I believe you need to run:
```
adduser *username* wheel
```

To add the user back to the wheel group.

---

### Post by Oldsoldier2003 on 2008-08-01
Ubuntu doesn't use the wheel group subsitute admin for wheel in the above command.  ```
adduser username admin
```

---

### Post by Dr Small on 2008-08-01
Ah, ok. I couldn't remember if it was wheel or admin. It's been awhile since I've been on Ubuntu.

---

### Post by johnr9 on 2008-08-06
thanks alot - it worked

---

### Post by trksh22 on 2008-12-19
Thanks so much! This happened to me and your instructions worked perfectly! :)

---

