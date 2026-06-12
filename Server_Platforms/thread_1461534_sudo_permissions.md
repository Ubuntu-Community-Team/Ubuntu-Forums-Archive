---
title: "sudo permissions"
date: 2010-04-24
forum: Server Platforms
---

### Post by SPConsole on 2010-04-24
I have a VPS, one of the ones that defaults to only root access (eww!). I got my admin group + permissions setup, and deleted the root password, and full sudo access is fine for MY account, but I'd like to make an admin group that isn't allowed to change the root password, if that's even possible.

I tried reading the sudoers man pages, but it made me dizzy :confused:

---

### Post by conradin on 2010-04-24
[http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html](http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html)

try this. 

the /etc/group file has all the groups 
also check out groupadd

---

### Post by SPConsole on 2010-04-24
As I said, I have a user, and it's in the admin group.

I want to know if it's possible to make a usergroup with admin privileges, but no access to "sudo psswd", everything else, just not "sudo passwd"

---

### Post by cdenley on 2010-04-24
> **SPConsole said:**
> As I said, I have a user, and it's in the admin group.

I want to know if it's possible to make a usergroup with admin privileges, but no access to "sudo psswd", everything else, just not "sudo passwd"

I don't think you can do this. Unless you restrict them to only a few commands, they can always run a shell as root to set the password, modify /etc/shadow directly, or find/create/install a new command to set the password. I don't think apparmor would help, either, since they have root access.

---

### Post by conradin on 2010-04-25
What you do is create is user of slightly less privi than root, and give them an alternate password.

---

