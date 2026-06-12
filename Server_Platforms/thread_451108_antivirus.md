---
title: "antivirus"
date: 2007-05-22
forum: Server Platforms
---

### Post by krisfrajer on 2007-05-22
Hi
Is there any antivirus available in ubuntu? From the repositories? Name them plz for me, and also should I run it as root user? I will thank you in advanced if you could tell me what commands to run from the command line or how to shitch into superuser in the graphical interface. 
Peace,

---

### Post by turinglabs on 2007-05-23
Clamav is available in the universe repository. For email scanning, you generally need clamav-daemon and clamav-freshclam, but this varies based on which mail server (MTA) you're using. They don't run as root, once installed, they run as user 'clamav', this is a security precaution.

If you just want to scan files, you can use clamscan from the clamav package to scan files or directories (but run freshclam first to update the virus database). You don't necessarily need to do this as root, just a user that has read privileges on the files you want to scan.

Switching to superuser is generally done on a per-command basis, using sudo. By default, the root account is disabled in Ubuntu. So 'sudo clamscan file.txt' will scan file.txt with root privs.

Doug

---

