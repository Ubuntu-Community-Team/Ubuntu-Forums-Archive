---
title: "Urgent Issue - Disk Space R/W unable to backup"
date: 2018-08-01
forum: Server Platforms
---

### Post by thompsonavc on 2018-08-01
Hey, hopefully one of you Ubuntu wizards can help!

I have a Dell Power Edge R410 running Ubuntu Desktop 18.04
Server ran out of disk space - 100% which stopped my applications running and made everything read only.
Can SSH int the server but the drive s read only and need to remove hidden .cache directory in /home/administrator for a backup program in order to free up enough space.

Server is running Moodle and MYSQL server won't launch

Any advise would be very appreciated as my moodle system has been down for nearly a week now.

Thank you in advance.

---

### Post by howefield on 2018-08-01
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2018-08-01
Is the entire system on a single partition?  Was it setup with LVM?

---

### Post by thompsonavc on 2018-08-01
Yes i believe so

---

### Post by LHammonds on 2018-08-01
Can you boot a desktop live DVD?  If so, you should be able to mount the HD and do your clean ups via the GUI.

If you ever re-create the server, I strongly recommend reading my tutorial on setting up Ubuntu Server...particularly the part about managing partitions and drive space to prevent such a thing from happening again in the future.

LHammonds

---

### Post by thompsonavc on 2018-08-02
I'll give that a go and let you know. Appreciate it

---

### Post by thompsonavc on 2018-08-03
Booted into live cd, cleared space. this part of the issue is now resolved.

---

