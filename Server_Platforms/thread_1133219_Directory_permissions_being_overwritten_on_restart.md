---
title: "Directory permissions being overwritten on restart"
date: 2009-04-22
forum: Server Platforms
---

### Post by waylon on 2009-04-22
We are currently working on creating a mysql server on ubuntu 8.10 64bit using ESXi. The problem we are having is that the directory /var/run/mysqld keeps changing the owner and group to root (from mysql) on restart, which causes mysql to fail when it tries to start. Does anyone have any clue as to why this might be happening, or maybe someone can point me in the right direction?
 
Thanks!

---

### Post by doogy2004 on 2009-04-22
sounds like when you created the VM you made the had disk Indepenedent and non-persistant, meaning that any changes to the disk will be lost when the vm is restarted.  change the hard disk settings for the vm to be persistant.

---

### Post by waylon on 2009-04-22
Thanks for the quick reply.
I checked the disk and it is not set as independent.  We have also made other changes that have stuck (installing mysql, cron jobs).  Any other ideas?

---

### Post by waylon on 2009-04-23
So after some more research it appears as if the /var/run directory should be reset after a reboot.  The problem is that the mysql startup script was not correctly setting the user to mysql on the /var/run/mysqld dircetory.  The reason this was happening to us was because we are using PAM authentication, and we had a mysql user in our active directory, and this was messing things up.  Apparently the reason this had never been an issue for us before when setting up servers was the order in which we did things (set up mysql first, then pam).  We set up pam first and when we installed mysql it did not create the mysql user because it thought there was one.
 
Anyways, I thought I'd post that we found a solution.

---

