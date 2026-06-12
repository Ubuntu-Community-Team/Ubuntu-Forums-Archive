---
title: "Citadel and SSL"
date: 2008-09-08
forum: Server Platforms
---

### Post by endorphine44 on 2008-09-08
I've searched for 3 days and can't find an answer so hopefully you guys can help. My previous server install was Fedora 6 using Citadel as a mail server. Everything worked great, but I had a wild hair to upgrade to Ubuntu 8.04 last week. I did a clean install on everything, EasyInstall on Citadel and recreated all my users. Now my problem is I can't connect to IMAP or POP3 with SSL. sshd is running and port scan from Network Tools shows my SSH port listening, but no 993 or 465 listening for mail. Also when I installed Citadel it won't let me just type sudo, I get this error:

dir: cannot create directory `/usr/local/ctdltest.8973': Permission denied

Easy Install is unable to create subdirectories in /usr/local.
Did you forget to run the install command as the root user?
Please become root (with a command like "su" or "sudo su") and
try again.

I have to go su, then run the curl easyinstall command to complete the installation. 

Any ideas how I can enable SSL in this Citadel install?  ufw is disabled, IPtables is disabled.
Thanks for the help.

---

