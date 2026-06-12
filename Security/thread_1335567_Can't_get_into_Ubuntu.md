---
title: "Can't get into Ubuntu"
date: 2009-11-23
forum: Security
---

### Post by kf1167 on 2009-11-23
We are trying to log into Ubuntu but we do not have the login information.  A guy who I replaced left the company and was given way too much control of passwords and logins and now, we are left in the dust.  What, if anything, can we do to get into the system??

---

### Post by lisati on 2009-11-23
I'm assuming here you've got good reason to log in to the machines e.g. work related stuff on a work machine.

I think it will be possible to start the computer in "recovery mode" and work from there to obtain access to the necessary parts of the system. One or two ways come to mind, but not having used them myself I'm not sure of the exact procedure to enable access, so I will defer to the wisdom of others.

---

### Post by BQAggie2006 on 2009-11-23
See this article: <snip>]

---

### Post by cariboo on 2009-11-24
> **kf1167 said:**
> We are trying to log into Ubuntu but we do not have the login information.  A guy who I replaced left the company and was given way too much control of passwords and logins and now, we are left in the dust.  What, if anything, can we do to get into the system??

I have a serious problem with this thread, this is the op's first post, asking for help to reset passwords with very little other info. I'm going to snip the link in the post above mine, until we get a little more information on the situation.

---

### Post by jacobs444 on 2009-11-24
Is very easy, load the live cd of ubuntu 9.04 at least to support ext4, then open terminal, then sudo su, then mkdir /media/disk1 then mount the internal HD to /media/disk1 (mount -t ext? /dev/sd? /media/disk1

then chroot /media/disk1
then passwd username
enter password
<snip>
enter password
then reboot.

---

### Post by jacobs444 on 2009-11-24
if encrypted, then you are probably boned!

---

### Post by kf1167 on 2009-11-24
I found a few articles on how to reboot in recovery mode so I was following the steps and selecting the proper menus, but then when I got to the part of entering ls/home, the keyboard was not responding, but it responded fine when I was using my up and down arrows to get through the menu selections.  Does anyone know why that might be?

---

### Post by cariboo on 2009-11-24
Once you get to the menu you use the arrow keys to navigate through the selections. Select drop to root prompt, as you will need to change the password from the root prompt.

---

### Post by __p1n__ on 2009-11-24
Hire a temp linux consultant and have him get it done and documented.

---

