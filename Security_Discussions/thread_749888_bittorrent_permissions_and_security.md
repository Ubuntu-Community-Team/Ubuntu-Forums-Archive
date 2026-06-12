---
title: "bittorrent permissions and security"
date: 2008-04-08
forum: Security Discussions
---

### Post by cozmicharlie on 2008-04-08
I installed Azureus as per this how to [http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus).  I have used Azureus for years without any security issues but the author makes a point to keep the permissions in the opt/azurues folder as root rather than user.  He states that changing to user is a greater security risk.  I have been using Ubuntu for a few years so I am not new but I don't understand how setting the permissions to root is safer than user.  That seems backwards to me.  Is this correct?  If I set it to user what real risk do I run?

Thanks

---

### Post by Biochem on 2008-04-09
The way I understand it ( and I'm no expert) is that it only affect the file, not how the program is run. So in this case Azureus would still be run by user, but user won't be able to modify the files in /opt/azureus. This way IF there is a weakness in azureus that would allow unwanted modification of those files it would be block at the system level.

---

### Post by cozmicharlie on 2008-04-09
> **Biochem said:**
> The way I understand it ( and I'm no expert) is that it only affect the file, not how the program is run. So in this case Azureus would still be run by user, but user won't be able to modify the files in /opt/azureus. This way IF there is a weakness in azureus that would allow unwanted modification of those files it would be block at the system level.

That doesn't sound that dangerous to me.  I am not that concerned about someone modifying the AZ files.  I was more concerned that somehow it leaves my computer open to access other files.  Thanks for the info.

---

