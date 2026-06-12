---
title: "run commands without requiring sudo command"
date: 2009-12-14
forum: Server Platforms
---

### Post by osx on 2009-12-14
Is there any way to let certain users run commands without having to type "sudo" before the command?

Thanks.

---

### Post by benj1 on 2009-12-14
theres only certain commands where you need to use sudo anyway, what are you wanting to do?

---

### Post by osx on 2009-12-14
> **benj1 said:**
> theres only certain commands where you need to use sudo anyway, what are you wanting to do?

I want to be able to use any and all commands without having to constantly type "sudo" before the ones that do. I was hoping that editing the sudoers file, by uncommenting the "%sudo ALL=NOPASSWD: ALL" would do the trick, but it hasn't.

I am a member of the sudo and admin groups if that matters.

---

### Post by benj1 on 2009-12-14
it is possible using the sudoers file, don't know how tho, ive never done it, you could also just log in as root, but i would highly recommend against these, the protections are there for a reason.

---

### Post by osx on 2009-12-14
> **benj1 said:**
> it is possible using the sudoers file, don't know how tho, ive never done it, you could also just log in as root, but i would highly recommend against these, the protections are there for a reason.

Yep, I know the security is there for a reason, but it would be nice to be able to turn it off when not needed.

I know it can be done, however, as I have seen others doing it in the past, but they aren't around any longer where I can ask them how they did it.

---

### Post by buntunoob on 2009-12-14
If you need a shell with root privileges, run sudo -s.        this pulled from [http://ubuntulinux.tribe.net/thread/5de8f757-cc0b-4f1e-a6c0-91813346d721](http://ubuntulinux.tribe.net/thread/5de8f757-cc0b-4f1e-a6c0-91813346d721)

---

### Post by Thocrun on 2009-12-14
you could also log in as root (then it won't ask you again and again-does have a little bit more security issues with this tho(not many)):

sudo su

---

### Post by sisco311 on 2009-12-14
Setting up and configuring a server can be a real PITA and it requires a lot of work which must be done as root. But once your server is configured properly you shouldn't have to do much work as root.

```
sudo -i
```
simulates a root initial login.

Contrary to *sudo -s* and *sudo su* it also initializes the environment, leaving DISPLAY and TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, as well as the contents of /etc/environment.  All other environment variables are removed.

Once you are done with the root tasks, you can log out with the *exit* command or by pressing Ctrl+d.

In the sudoers file later entries override the former ones. If your user is in the admin and sudo groups, the "%sudo ALL=NOPASSWD: ALL" entry should be placed after the "%admin ALL=(ALL): ALL". Note that you will still have to use sudo in front of the commands, but you will not be prompted for a password. Which is a security risk, IMHO *sudo -i* is much safer.

---

### Post by osx on 2009-12-15
Thanks everybody. These are all great suggestions, and do work to some extent, but I was hoping for a solution that would still log my commands to my own bash history file instead of root's (which can get messy if more than one person administrates the system). Using sudo before each command does this, but is a little bit of a pain.

Just as sisco311 said, this is really something I am trying to do simply because initial server setup can be a PITA.

Also, I did experiment with the order issue of the sudoers file, but that didn't work either. I tested it with an account that belongs to sudo, but not admin, and the account still needs to precede certain commands with sudo for it to work.

---

### Post by osx on 2009-12-15
sisco311,

I should add that I am looking at the bash history of one of the former sys admins to confirm that what I saw him doing is what I thought. Sure enough, never in his bash history does he procede any command with sudo. Also, the sudoers file only has the %sudo ALL=NOPASSWD: ALL line uncommented. Nothing else in it is different.

---

### Post by sisco311 on 2009-12-15
never mind

---

### Post by osx on 2009-12-15
sisco311,

sudo -s does work for maintaining my bash history, and for now that is what I will use, but the former sys admin's bash history doesn't contain any record of him using sudo -s. Any idea how he could have done this?

Thanks.

---

