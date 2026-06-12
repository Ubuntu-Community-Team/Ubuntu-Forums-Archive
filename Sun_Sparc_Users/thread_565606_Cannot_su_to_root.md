---
title: "Cannot su to root"
date: 2007-10-02
forum: Sun Sparc Users
---

### Post by RobSand on 2007-10-02
Greetings,

I am using Solaris 10 (sparc)

When I try to su to root (giving the correct password), I get the message:    **su: sorry**

What is preventing me from doing an su to root? I checked the /etc/group file and I am a member of the sysadmin group (gid=14). All replies are solicited and appreciated! Thanks

RobSand

---

### Post by pondochris on 2007-10-02
What are you using to su? Are you typing "su root" or just "su"? Also it is much safer not to su to root but to type sudo before a command to run as root.

---

### Post by HermanAB on 2007-10-02
Try these:
su root
su -

---

### Post by netztier on 2007-10-12
> **RobSand said:**
> Greetings,

I am using Solaris 10 (sparc)

When I try to su to root (giving the correct password), I get the message:    **su: sorry**

What is preventing me from doing an su to root? I checked the /etc/group file and I am a member of the sysadmin group (gid=14). All replies are solicited and appreciated! Thanks

RobSand

You might want to read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In a (very small) nutshell: use **sudo** instead of **su**. If you need a root shell, do **sudo bash**.

best regards

Marc.

---

### Post by chefbodini on 2007-10-13
Perhaps you should ask in a Solaris forum if you are running Solaris 10...

---

