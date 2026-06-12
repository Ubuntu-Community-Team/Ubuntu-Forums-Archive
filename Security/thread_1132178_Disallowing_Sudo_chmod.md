---
title: "Disallowing Sudo chmod?"
date: 2009-04-21
forum: Security
---

### Post by JK3mp on 2009-04-21
Hey i was wondering if there was a way to disallow certain actions such as chmod for sudoers. Just curiouse cause it makes it pointless to chmod a file to 700 if someone can just sudo the permissions back to open and then open the file/folder then. Im sure theres a way.. im just not educated on it. Thanks ahead of time. :-)


ADDED NOTE: But i DO wanna try to retain a few sudo permissions such as update and install. (Though installs probably not a good one to keep security wise if a cracker gets your acct)

---

### Post by Odemia on 2009-04-21
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

I think what you are looking for is command list.  You are going to have to decide what commands the user or group are allowed to execute with sudo.

---

### Post by JK3mp on 2009-04-21
Thanks Odemia! :)

---

### Post by bodhi.zazen on 2009-04-21
Well, this is the "problem" of root access :)

There is greater and greater interest in restricting root. Options include configuring sudo, acl, selinux, and apparmor.

---

### Post by JK3mp on 2009-04-21
> **bodhi.zazen said:**
> Well, this is the "problem" of root access :)

There is greater and greater interest in restricting root. 

Exactly what i've been noticing on the forum which is why i've been setting on a bit of an adventure into security techniques. Been trying to find away to make the root directory and files/dirs within unaccessable from everyone else and the files within unaccessable EVEN from root without a password. Which best method seems to be encryption through GNU gpg command or something similiar like Trucrypt etc.

---

### Post by bodhi.zazen on 2009-04-21
You might want to look at acl and selinux.

---

### Post by JK3mp on 2009-04-21
> **bodhi.zazen said:**
> You might want to look at acl and selinux.

Yeah i will. I think i've used SE Linux before if your reffering to that annoying application that comes with Core Fedora Install. LoL. I'll look into acl though.

---

### Post by JK3mp on 2009-04-21
This is all more for research than personal use... but with the vast amount of people interested in secure and lock down there OS and files thought i might make myself useful and look into the topics myself.

---

### Post by sisco311 on 2009-04-21
You might also take a look at PolicyKit.

---

### Post by bodhi.zazen on 2009-04-21
If you have not looked at selinux recently, a lot has changed. It is much easier to manage now.

this is a nice "one-pager" [HowTos/SELinux - CentOS Wiki]("http://wiki.centos.org/HowTos/SELinux")

For personal use, acl may be the way to go.

---

### Post by JK3mp on 2009-04-22
Not so much for personal use as just personal research so that i may be a bit more helpful with the recent upcoming of interests in security and securing files by New ubuntu users.

---

