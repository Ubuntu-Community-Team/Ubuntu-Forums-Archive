---
title: "Root password is my login password after root login enabled"
date: 2008-04-29
forum: Security
---

### Post by itix on 2008-04-29
I seriously wonder if this is right. I just enabled root login on my Eee running xubuntu 7.10, as well as on my twice as big acer laptop running ubuntu 7.10 and the administrative password has been changed to my login password on both machines.

I mean, isn't it supposed to stay the root password?? I have separate passwords for my "itix" login account and my root account which should mean that the administrative password should stay the root password. At least according to my security logic.

This means that if someone can log on to the machine, they can automatically change everything and even wipe the system if they like since it's only the login password that is required for root activities.

---

### Post by cdenley on 2008-04-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ubuntu systems aren't supposed to have a root password set. During the install, the user you create is added to the admin group. Users in the admin group can gain root access using sudo, which prompts them for their own password. If a user shouldn't have administrative privileges, don't put them in the admin group.

---

### Post by itix on 2008-04-29
Ah, ok. I like the way fedora is constructed with root and user separated, but I don't really like fedoras other parts. The network manager for instance =(
Keblaaaah!

---

