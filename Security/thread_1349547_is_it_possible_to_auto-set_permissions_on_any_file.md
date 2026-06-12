---
title: "is it possible to auto-set permissions on any file created in a certain directory?"
date: 2009-12-08
forum: Security
---

### Post by uschxc on 2009-12-08
i am a little familiar with umasks, and how they control default permission on new files.  however I need to ensure that all files created in /var/spool/cron have permissions 600.  can this be configured?  maybe by editing the cron folder in vi?

---

### Post by Sarmacid on 2009-12-09
I don't know if there's you could auto set permissions like you want, but as a workaround, you could set up a cron job to periodically change the permissions of the files in that directory.

---

### Post by Lars Noodén on 2009-12-09
> **uschxc said:**
> i am a little familiar with umasks, and how they control default permission on new files.  however I need to ensure that all files created in /var/spool/cron have permissions 600.  can this be configured?  maybe by editing the cron folder in vi?

umasks apply to a particular program, commonly the log in shell.  What program will be creating files in /var/spool/cron?  

To get file permissions of 0600, the program creating the files will have to use the umask 0077.

---

### Post by HighCommander540 on 2009-12-09
> **Sarmacid said:**
> I don't know if there's you could auto set permissions like you want, but as a workaround, you could set up a cron job to periodically change the permissions of the files in that directory.

This is what I do, to make sure the files for Apache are set right.

On the other note, you are asking if there is a way to make sure any file created in "/var/spool/cron". No there isn't, you just have to make it so that anyone that is going to create a file there has the uMask right.

---

