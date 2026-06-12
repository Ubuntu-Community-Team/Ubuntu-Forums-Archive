---
title: "Is it possible to log in as root?"
date: 2011-02-13
forum: Security
---

### Post by Bernie Gallagher on 2011-02-13
Bear with me, I'm still somewhat of a Linux noob.  

In Users and Groups, there's two IDs: mine and root (which I assume is the admin account).  

When I turn on my computer, I'm only given the option to log on to my regular account.  

Is it possible to log in to the root account?  

So far, I've been able to do anything I want with the normal account as long as I type my admin password whenever I do admin functions.

---

### Post by kn0w-b1nary on 2011-02-13
As a security precaution, not in GUI, at least default. You can sudo to root in terminal:

sudo su -

In Debian, there is a settings file somewhere to let you login GUI as root, but I don't know if you can do it in Ubuntu or how. To be honest, I would recommend against doing even if you knew how.

Hope this helps!

---

### Post by uRock on 2011-02-13
The root account is recommended, but it can be used via the info in this link. Please heed the warnings. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bernie Gallagher on 2011-02-13
Yeah, I've had to use the sudo command a few times in the terminal when I originally set up my Linux system.  I guess it stands for Super User something-or-other...  

But the Linux terminal commands are so different from Windows terminal commands and it would be much easier to do some admin stuff if I could copy files with File Browser instead of sudo cp...

---

### Post by uRock on 2011-02-13
You can copy files using **gksudo nautilus** in a terminal, which opens the file browser as root. Be careful because if you can mess up your OS if you move or alter files/directories.

---

### Post by Bernie Gallagher on 2011-02-13
Thanks!  That's what I need.  

But I'm curious.  If there's no actual root login and I can become super user just by using the sudo command from my regular signin, any other user can also run sudo from their regular signin...  

It seems to me that it would be more secure to have to log in as root to do admin stuff, and just make sure that the root password is really strong.

---

### Post by cariboo on 2011-02-13
The reason your user can use sudo, is because of group membership, unless you make a special effort, the first user you set up is the only one that is a member of the admin group, any subsequent users you setup aren't a member of that group.

---

### Post by Bernie Gallagher on 2011-02-13
I see.  If I create a new user account for guests, they won't have admin privileges to run sudo.  So my system will be secure.  Thanks!

---

### Post by linuxsyst on 2011-02-13
The ```
gksudo nautilus
```is to run the file browser as root
Good Luck

---

### Post by The Cog on 2011-02-14
> **Bernie Gallagher said:**
> I see.  If I create a new user account for guests, they won't have admin privileges to run sudo.  So my system will be secure.  Thanks!
Exactly. Don't disable your account or remove it from the admin group without putting someone else in the admin group first. There are ways to recover from that, but it involves command line in recovery mode.

---

### Post by Bernie Gallagher on 2011-02-14
> **The Cog said:**
> Exactly. Don't disable your account or remove it from the admin group without putting someone else in the admin group first. There are ways to recover from that, but it involves command line in recovery mode.

Right.  I just created an Admin account (not a root account, just another admin account).  Next, after I use it for a while and make sure it's working as desired, I'll make my regular account a non-admin account (but still with plenty of privileges).

I'll do the same thing with my Windows machine, but it probably won't matter much there.

---

