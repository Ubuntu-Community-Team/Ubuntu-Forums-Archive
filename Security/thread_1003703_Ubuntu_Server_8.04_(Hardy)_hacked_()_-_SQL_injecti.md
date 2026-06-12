---
title: "Ubuntu Server 8.04 (Hardy) hacked (?) - SQL injection?"
date: 2008-12-06
forum: Security
---

### Post by wolfchri on 2008-12-06
Hello folks,

need the advice of one or more security guru(s):

I have 2 virtual machines running (Ubuntu Jeos 8.04) on a VirtualBox host (Ubuntu 8.04 server), behind a router.

Both have Webmin running on a non-standard port, not forwarded from the internet. 

Both VM are running a LAMP stack (Wordpress and Drupal as application), the host also an NFS server (ports not forwared, of course). Both have also Postfix as mail agent running, ports not forwared, for outbound status mails only.

One machine has SSH access on a non standard port, with fail2ban protecting it. I did not have reports about unsuccessful access tries from logcheck. All passwords are hard passwords with more than 10 charakters, John the Ripper is running daily to test them.

All updates were installed in due course. 

IDS: Samhain, Rkhunter. Logeck and Tiger are running via cron. All are reporting via e-mail.

About 4 weeks ago, I got a warning from rkhunter that inodes of some vital system files got changed (lsmod, su, etc.). I also got a checksum mismatch for lsmod. Samhain did not work at that time, I forgot why. 

I manually checked lsmod against the repositories in a clean enviroment. MD5sum calmed me down as the lsmod of the suspicious machine and lsmod from the repos had the same MD5 checksum.

I ran rkhunter --propupdate and forgot the issue. 

Until yesterday, when I got this on the other VM - with the last update installed a few days ago and daily maintainance cron jobs:

Warning: The file properties have changed:
        File: /bin/login
        Current inode: 104169    Stored inode: 104032
        Current file modification time: 1226559073
        Stored file modification time : 1207184931
Warning: The file properties have changed:
        File: /bin/lsmod
        Current inode: 104032    Stored inode: 104061
        Current size: 3952    Stored size: 4344
        Current file modification time: 1223297493
        Stored file modification time : 1203974432
Warning: The file properties have changed:
        File: /bin/su
        Current inode: 104170    Stored inode: 104033
        Current file modification time: 1226559073
        Stored file modification time : 1207184931
Warning: The file properties have changed:
        File: /usr/bin/lastlog
        Current inode: 202299    Stored inode: 201733
        Current file modification time: 1226559073
        Stored file modification time : 1207184931
Warning: The file properties have changed:
        File: /usr/bin/newgrp
        Current inode: 202300    Stored inode: 201734
        Current file modification time: 1226559073
        Stored file modification time : 1207184931
Warning: The file properties have changed:
        File: /usr/bin/passwd
        Current inode: 207535    Stored inode: 201906
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /sbin/depmod
        Current inode: 24566    Stored inode: 24055
        Current size: 31448    Stored size: 45216
        Current file modification time: 1223297493
        Stored file modification time : 1203974432
Warning: The file properties have changed:
        File: /sbin/insmod
        Current inode: 24002    Stored inode: 24052
        Current size: 4632    Stored size: 5740
        Current file modification time: 1223297493
        Stored file modification time : 1203974432
Warning: The file properties have changed:
        File: /sbin/lsmod
        Current hash: be5bd1d2d0e00b4f999cacaa0e47a75db7431976
        Stored hash : 56f23aee856a79d9bfe663303945cf700323951b
        Current inode: 24569    Stored inode: 24075
        Current file modification time: 1226697519
        Stored file modification time : 1210612644
Warning: The file properties have changed:
        File: /sbin/modinfo
        Current inode: 24567    Stored inode: 24056
        Current size: 8652    Stored size: 10872
        Current file modification time: 1223297493
        Stored file modification time : 1203974432
Warning: The file properties have changed:
        File: /sbin/modprobe
        Current inode: 24564    Stored inode: 24053
        Current size: 19876    Stored size: 26860
        Current file modification time: 1223297493
        Stored file modification time : 1203974432
Warning: The file properties have changed:
        File: /sbin/rmmod
        Current inode: 24565    Stored inode: 24054
        Current size: 6672    Stored size: 7800
        Current file modification time: 1223297493
        Stored file modification time : 1203974432
Warning: The file properties have changed:
        File: /usr/sbin/groupadd
        Current inode: 207539    Stored inode: 201910
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/groupdel
        Current inode: 207540    Stored inode: 201911
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/groupmod
        Current inode: 207541    Stored inode: 201912
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/grpck
        Current inode: 207542    Stored inode: 201913
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/nologin
        Current inode: 202297    Stored inode: 201731
        Current file modification time: 1226559073
        Stored file modification time : 1207184931
Warning: The file properties have changed:
        File: /usr/sbin/pwck
        Current inode: 207546    Stored inode: 201917
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/useradd
        Current inode: 207549    Stored inode: 201920
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/userdel
        Current inode: 207550    Stored inode: 201921
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/usermod
        Current inode: 207551    Stored inode: 201922
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: The file properties have changed:
        File: /usr/sbin/vipw
        Current inode: 207552    Stored inode: 201923
        Current file modification time: 1226559071
        Stored file modification time : 1207184929
Warning: Account 'sashroot' is root equivalent (UID = 0)
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
============================
The sashroot and hidden directory stuff is Debian specific, AFAIK nothing to worry, I had this all the time. But the inode changes of this crucial system files really trouble me. I also noticed that Samhain was shut down without a warning (as far as I remember, I get about 100 system mails / day...)

I also got for the other VM on the same day this again:

Warning: The file properties have changed:
        File: /sbin/lsmod
        Current file modification time: 1227370880
        Stored file modification time : 1226698446

I have an honeypot running in my network which did report no access tries until now. I also do not see suspicous outbound traffic from my network. Nevertheless, I have shut down the ports to the second VM as I am really feel not good about this. 

Is this maybe (I hope it!!!) caused by a known anomalie in rkhunter? If not, what could I do to further check my systems?  As I do not use standard ports on the second VM, an scripted attack seems to be rather unlikely - if it is an intrusion, looks more like an SQL injection - but since also Apache on this machine is not running on port 80 but somewhere else, and it is only a test machine unknown to Google, somebody had to waste quite some time manually? For a test machine?  

Any help is appreciated! ):P

---

### Post by Kinstonian on 2008-12-06
Is this your work's server, and if so is there an incident response plan you should be following?

I take it the property changes can't be attributed to a system update?  I'd check the modification time stamps on the system binaries, then use *find* to search for files that were modified at around the same time.  Also, check the logs for entries around that time.  Try chkrootkit and see if that detects anything.  Basically you should follow the steps listed on [CERT's Intrusion Detection Checklist](http://www.cert.org/tech_tips/intruder_detection_checklist.html).

---

### Post by wolfchri on 2008-12-06
Thank you Kinstonian.

Fortunately only a private network with few external users, testing on my machine - so there is no escalation plan as I am the only admin ;-)

chkrootkit was the first I tried, I re-installed from the repos just to be safe. Did not find anything. 

Updates: I checked very carefully against the apt-logs but the last update was November 27 (kernel, Mysql etc.) I run integrity tests every day so even if there were updates this should have poped up much earlier.

I will try to check all changes in the respective time frame with find, as suggested. If I can not find the reason this way, I will log all traffic to/from the machine for a while and check it and then install my backup. Fortunately restoring a VM is not that much work.

Still, that would leave a bitter taste not to know what happened.

---

### Post by Kinstonian on 2008-12-06
Yeah, file properties changing is something that is simply suspcious-- it could just as easily be malicious as it could be benign.  It's not one of those things such as finding attack tools in /tmp where you can definitively say you've been hacked.  All you can do is investigate it like you are now.

An incident is a **series** of adverse and anomalous events, which means they can often be detected in multiple ways.  If at the end of the day you don't find any further evidence of an intrusion, it's probably safe to conclude it's a false positive.

---

