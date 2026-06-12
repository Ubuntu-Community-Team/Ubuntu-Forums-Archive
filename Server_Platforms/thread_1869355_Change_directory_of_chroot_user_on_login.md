---
title: "Change directory of chroot user on login"
date: 2011-10-25
forum: Server Platforms
---

### Post by Engineer007 on 2011-10-25
Hello, 

I have some chroot users on my ubuntu 10.04 64-bit box. I don't want them to see the system files when they login, but they are required for the chroot session. 

Instead I want to move them to a folder, right away called incoming. Is it possible to change their directory on login? As a side note I did not see .bashrc file in the directory because of the chroot, I'm assuming. 

I've done some searching and haven't come up with a good solution, any help would be appreciated, thanks!

---

### Post by Jonathan L on 2011-10-26
> **Engineer007 said:**
> I have some chroot users on my ubuntu 10.04 64-bit box. I don't want them to see the system files when they login, but they are required for the chroot session. 

Instead I want to move them to a folder, right away called incoming. Is it possible to change their directory on login? As a side note I did not see .bashrc file in the directory because of the chroot, I'm assuming. 


Hi Engineer

Perhaps you could put /whatever/incoming as their home directories?  Would that help?

Kind regards,
Jonathan.

---

### Post by Engineer007 on 2011-10-26
I did try that, but then when you want to connect with am SCP client it throws quite a few errors. From reading some documentation on chroot users, I think it is because the folders in the home directory of those users are necessary for the session. Which is why I am trying to CD them as soon as they login as opposed to moving their home directory.

---

