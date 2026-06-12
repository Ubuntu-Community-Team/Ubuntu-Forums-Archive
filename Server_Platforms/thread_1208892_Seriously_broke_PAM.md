---
title: "Seriously broke PAM"
date: 2009-07-09
forum: Server Platforms
---

### Post by dave562 on 2009-07-09
Help!

I messed up big time.  I removed the following files from the /etc/pam.d directory

common-auth
common-session
sudo

I CANNOT sudo anymore.  I need to recreate those files.  This is a production server and I cannot not have access to it.  I am currently SSH'd into it.  If the connection goes down, I am locked out of the box because PAM cannot authenicate any sort of logon activity.

I have physical access to the server.  What do I need to do to recreate those files?  I have backup copies of them, but when I try to create the files with a cp of the backup file, I get a permission denied, file cannot be created.  Obviously sudo doesn't work so I can't sudo cp.

---

### Post by HermanAB on 2009-07-09
Install the same version on another machine, then copy the missing files over.  However, the server would need to be in single user mode, so you would likely need on-site support to fix this and it means rebooting of course.

---

### Post by dave562 on 2009-07-09
I have backups of the missing files located in the same directory (/etc/pam.d).  How do I boot the system into single user mode and copy them?  I have the original setup CD (Ubuntu 8.04 server).

Would I be better off using a LiveCD and mounting the file system through that?  If so, how do I do that?

---

### Post by dave562 on 2009-07-09
I solved my own problem.  Luckily I had previously created backup copies of the files that I deleted.  I was able to boot into the recovery mode using the Ubuntu installer CD.  From there I launched a shell and was able to cp the backup files back to their original file names.

---

