---
title: "inotify_handler(240) No data on inotify fd?!"
date: 2009-03-18
forum: Server Platforms
---

### Post by optimaco on 2009-03-18
Hello,
One of the server I maintain has Ubuntu 8.04 LTS server with samba 3.0.28a. Kernel version is 2.6.24-16-server. The samba setup for this server is a workgroup environment, with user level security.
At least once a week, sometimes more often, the server becomes unavailable because the system disk is full. It appears that the samba logs are the problem. Although the samba configuration file indicates that logs should be limited to 1000K, one of the machine specific logs (/var/log/samba/log.machine_xyz.old) grows to the point of entirely filling the disk (140 GB of log). The log file contains endless repetitions of the same message:
smbd/notify_inotify.c:inotify_handler(240) No data on inotify fd?! 
At the same time, the smbd process for the user related to the faulty machine log uses 100% CPU, and must be stopped with kill -9. Note that it not always the same machine that creates the problem.
Because some users are never affecting the system, we tried to identify if the origin of the problem was linked to a specific data manipulation by some of the 'bad' users, but we are still clueless.
I found some info in the samba mailing list with similarities to my problem where the suggestion is to include "notify:inotify = false" in [global] to see if it helps ([http://www.mail-archive.com/samba%40lists.samba.org/msg98074.html](http://www.mail-archive.com/samba%40lists.samba.org/msg98074.html)).
I've just done this, so I will have to wait and see.
The samba mailing list indicates that if the above does help, then it points to a kernel problem (bug with inotify), not a samba problem.
Does anyone have any idea or suggestion ?
Any help would be greatly appreciated.

---

### Post by optimaco on 2009-03-26
After more than a week of functioning with "notify:inotify = false" in smb.conf [global], the problem has not re-appeared.
It seems to confirm that this is indeed a kernel issue.
Anyone having recommendations on what to do ?
Is upgrading the kernel worth the trouble (this 8.04 LTS, 2.6.24-16-server kernel) ?

---

### Post by Scott Jordahl on 2009-05-22
Is there any update on this problem. I too am having my log file (syslog for me) fill up the disk with "inotify_handler(240)" errors. I'm running Ubuntu 8.04 LTS x64 with the latest 2.6.24-24 kernel.

If I do a "service samba stop", there is still a rogue "/usr/sbin/smbd -D" running that I must kill with a -9 in order to stop the inotify messages. If you use the "notify:inotify = false" config, I would assume that rogue processes would continue to collect in the background. So I would like to understand what is causing the issue.

---

### Post by optimaco on 2009-06-01
Have a look at this thread: [http://www.mail-archive.com/samba@lists.samba.org/msg99522.html](http://www.mail-archive.com/samba@lists.samba.org/msg99522.html)
As far as I am concerned, I have not upgraded the kernel and with "notify:inotify = false", I have not seen the problem again. Please check the latest response in the thread above, clearly indicating what "notify:inotify = false" is doing.
I guess this really is a kernel issue in the end, but apparently 2.6.24-24 does not fix it.

---

### Post by vlmagee on 2010-10-07
We recently experienced this problem and have fixed it. For the benefit of others who might encounter the problem for the same reason, I have summerized our experience here:

In our case the inotify loop/100% CPU utilization was caused by having Outlook PSTs and OST on a network share. This is not a supported configuration, although that fact is hidden somewhere deep in the documentation. The symptoms also included Delayed Write errors in Outlook, and corrupted PSTs and OST. We had the problem on two PCs, one of which never got the inotify error but did get the others. The problem could be created almost at will by running something that was disk I/O intensive outside of the VM that was running Outlook (such as a file backup or file copy).

We moved our PSTs and OSTs to a separate virtual disk, rather than a network share, and the problem went away, but not after it had caused us more than 6 months of grief! Although Microsoft considers this an unsupported configuration, it seems to me that there is perhaps some I/O pattern that causes Samba to fall apart, meaning that the problem may occur with other software configurations as well.

---

