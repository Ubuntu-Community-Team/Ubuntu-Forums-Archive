---
title: "adding a formal root account/undo the sudo"
date: 2008-12-27
forum: Security
---

### Post by graysky on 2008-12-27
I noticed that Ubuntu doesn't have a formal root account like Debian does... how can I make Ubuntu more like Debian in this regard?  In other words, I'd like to have a formal 'root' account that I can switch to rather than using 'sudo su -' to do this.

Thanks!

---

### Post by FreeFull on 2008-12-27
All you need to do is 'sudo passwd root'. Once you set a password for the root account, you can log into it.

---

### Post by graysky on 2008-12-27
> **FreeFull said:**
> All you need to do is 'sudo passwd root'. Once you set a password for the root account, you can log into it.

Very cool, thanks for the info.  What do I need to edit (/etc/sudoers ?) to remove the ability of regular users to simply sudo command?

---

### Post by matej on 2008-12-27
Most probably you have to remove users from "admin" group. You can do it using "Administration &#9656; Users and groups".

---

### Post by Nepherte on 2008-12-27
Enabling the root account in ubuntu is actually against the ubuntu forum policies but since you now already know how to do so, I can only try to make you aware of possible security risks. Be sure to read the sticky about it.

You have to remove the groups and users from /etc/sudoers accordingly, because everyone listed in that file gets sudo privileges. Always use the visudo command for editing this file. This assures the correct ownership and permissions of the file:
```
sudo visudo
```
or if you're not familiar with vi:
```
sudo EDITOR=gedit visudo
```

---

### Post by graysky on 2008-12-27
Didn't see the sticky, thanks for pointing me to it and apologies for violating the forum rule retrospectively.

I'm not an LINUX expert by any means. My concern with sudo open to users is that any root command is also open to users.  Isn't this tantamount to my user more or less being root since root privileges are open to my user's password?

Say someone gets into my box by having knowledge of my password.  They are not limited to my account's privileges since my account's password is all that's protecting root access via sudo.

---

### Post by sisco311 on 2008-12-27
> **graysky said:**
> Didn't see the sticky, thanks for pointing me to it and apologies for violating the forum rule retrospectively.

I'm not an LINUX expert by any means. My concern with sudo open to users is that any root command is also open to users.  Isn't this tantamount to my user more or less being root since root privileges are open to my user's password?

Say someone gets into my box by having knowledge of my password.  They are not limited to my account's privileges since my account's password is all that's protecting root access via sudo.

most hackers are looking first for the root password.
to get root privileges with sudo they need to know your username first and then your password.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

[http://ubuntuforums.org/showthread.php?p=4464175#post4464175]("http://ubuntuforums.org/showthread.php?p=4464175#post4464175")

---

### Post by lensman3 on 2008-12-27
I would suggest that if you are going to be editing the /etc/passwd and /etc/group files that you use vipw and vigr.  Both of these use VI as default, but they have the ability to set exclusive use locks on the files preventing file corruption.  That way two people or two processes can be modifying the files at the same time.

---

### Post by bodhi.zazen on 2008-12-27
> **graysky said:**
> Didn't see the sticky, thanks for pointing me to it and apologies for violating the forum rule retrospectively.

I'm not an LINUX expert by any means. My concern with sudo open to users is that any root command is also open to users.  Isn't this tantamount to my user more or less being root since root privileges are open to my user's password?

Say someone gets into my box by having knowledge of my password.  They are not limited to my account's privileges since my account's password is all that's protecting root access via sudo.

Only users in the admin group can access the root account via sudo.

Although rare, you can break Ubuntu by enabling the root account.

There is no need to enable the root account, you access root with sudo 

```
sudo -i
```

Or if you are running X applications, use gksu

```
gksu nautilus
```

Since you are new to Ubuntu, why are you making changes to it in this way ? If you prefer Debian, run Debian.

I suggest you learn how sudo works before you make these kind of changes.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

We support enabling the root account when it is necessary.

We prefer to educate users how to use Ubuntu "properly" first.

Since the OP question has been asked and answered, and since setting a root password is not necessary, and since I have provided you with enough information to get started with sudo, this thread will be closed. 

If you have a question on how to use or configure sudo, feel free to start a new thread.

---

