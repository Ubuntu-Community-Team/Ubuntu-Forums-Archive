---
title: "Permission Help"
date: 2009-01-04
forum: Ubuntu Dev Link Forum
---

### Post by kineem on 2009-01-04
Hello. I am software developer. I need to create a directory in Ubuntu Home directory via software interface that any files can be copied into and new subdirectories can be added into. I tried to create the directory with 0667 permission. But when I tried to add a subdirectory in it system denied. Then I tried the main directory with 0777 permission. This allowed me to place subdirectories in it. But I want to ask creating a directory with 0777 permission  may create any security or system issue?

Thanks.

---

### Post by gjoellee on 2009-01-04
> **kineem said:**
> Hello. I am software developer. I need to create a directory in Ubuntu Home directory via software interface that any files can be copied into and new subdirectories can be added into. I tried to create the directory with 0667 permission. But when I tried to add a subdirectory in it system denied. Then I tried the main directory with 0777 permission. This allowed me to place subdirectories in it. But I want to ask creating a directory with 0777 permission  may create any security or system issue?

Thanks.

with the 777 everyone can read/write/delete it might be a secutity issue.

chmod 775 will be more secure

---

### Post by ajgreeny on 2009-01-04
In view of your apparent uncertainty, I wonder if you are aware that you can make a new directory with a terminal command ```
sudo mkdir /path/to/directory/directoryname
``` for anywhere in the system and the same command without sudo in your /home.

If you want them all to have 0667 permissions just make all of them first and then set permissions after.  Or perhaps I have misunderstood the manner in which you are trying to do this and the reasons why.

---

### Post by kineem on 2009-01-04
Thanks gjoellee. It is not a terminal issue. I create the directory and also its permission via software interface. As stated in my first post, 0667 created problem but 0777 just worked ok. But I thought it might be problematic for security. 0775 works now,too. And I hope 0775 will be more secure for Ubuntu.

---

### Post by jpkotta on 2009-01-04
Directories should usually be listable (that's the meaning of the execute bit for directories).

---

### Post by kineem on 2009-01-05
> **jpkotta said:**
> Directories should usually be listable (that's the meaning of the execute bit for directories).

Hello. What does it mean in 0*** way? Does 0775 assures your suggestion?

---

