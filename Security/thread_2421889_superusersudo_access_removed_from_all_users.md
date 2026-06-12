---
title: "superuser/sudo access removed from all users"
date: 2019-06-28
forum: Security
---

### Post by arealperson on 2019-06-28
lubuntu 19

The only sudo user got removed from sudo access.

Thus, the system has no superuser access that I can find. I can't sudo, can't login as root, no su - etc.

How do I fix it, I tried booting from a live CD but I can't seem to get the GRUB bootscreen
to load as to go into recovery mode.

The live CD allows me to access and edit files on the other mount point of the broken OS.
But how do I restore/fix or add sudo access to the user I removed it from the other mount point.

It looks like commands from the Live CD boot are only for that boot and don't modify the other OS mount point.

Thanks,

---

### Post by #&amp;thj^% on 2019-06-28
Give this a whirl: [https://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user](https://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user)

---

### Post by arealperson on 2019-06-28
The last option with the 5 steps worked.

Thanks for the help.

---

### Post by #&amp;thj^% on 2019-06-28
Awesome! :)
Also thanks for pointing out which steps you took, as the page-link is not a one-size fits all.

---

