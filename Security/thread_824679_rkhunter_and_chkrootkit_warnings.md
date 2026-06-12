---
title: "rkhunter and chkrootkit warnings"
date: 2008-06-10
forum: Security
---

### Post by cssutto on 2008-06-10
Ran rkhunter today and got a warning on:
 /usr/bin/dpkg

Ran chkrootkit and got:
user claude69694 deleted or never logged from lastlog


I have googled both and looked here and found nothing that helps me understand.

I have never had the log reference before.

ubuntu 8.04  updated daily.

I have checked my user list and it is as it should be.
cd /; uname -a; id;

CSSJR

---

### Post by acrostic on 2008-06-10
Who is the owner of /usr/bin/dpkg ?

---

### Post by brian_p on 2008-06-10
> **cssutto said:**
> I have googled both and looked here and found nothing that helps me understand.

Using "never logged from lastlog" (with the quotes) in Google persuaded me it nothing to lose any sleep over.

---

### Post by The Tronyx on 2008-06-10
> **brian_p said:**
> Using "never logged from lastlog" (with the quotes) in Google persuaded me it nothing to lose any sleep over.

Rkhunter is a handy tool, but it provides false positives pretty often.

Sometimes distros upgrade frequently used binaries like `ls` and `ps`. When you run rkhunter, it might not be aware of these newly changed and updated files and as a result may return some false positives or warnings.

Here is a helpful hint from one of the many rkhunter threads floating around the forums:
> 
Here's a tip when using rkhunter... use the pkgmgr flag. This will use the distribution's package manager for verification.

ubuntu example:

sudo rkhunter --check --pkgmgr dpkg

redhat example:

rkhunter --check --pkgmgr rpm

just run rkhunter with no flags to see all the options available.


You may also want to take a look in /etc/passwd and see if there are any entries out of the ordinary.

Hope these help as well:
[http://www.uluga.ubuntuforums.org/showthread.php?t=679193](http://www.uluga.ubuntuforums.org/showthread.php?t=679193)
[http://www.linuxquestions.org/questions/linux-security-4/chkrootkit-lastlog-372419/](http://www.linuxquestions.org/questions/linux-security-4/chkrootkit-lastlog-372419/)
[http://ubuntuforums.org/archive/index.php/t-627822.html](http://ubuntuforums.org/archive/index.php/t-627822.html)
[http://www.fedoraforum.org/forum/archive/index.php/t-90512.html](http://www.fedoraforum.org/forum/archive/index.php/t-90512.html)

---

### Post by cssutto on 2008-06-10
/etc/dpkg is owned by root.

The passwd log file has no weird entires.

sudo rkhunter --check --pkgmgr dpkg returns the same info as rkhunter -c.

I am still digging.

---

### Post by cssutto on 2008-06-12
I am also getting this message from the cron:

Warning: The file properties have changed:
         File: /usr/bin/dpkg
         Current hash: 3ec47072343c8886120c1437e878cefbb914b262
         Stored hash : 8db6586337bd9aa7eb1ddfac84f6c09f316df4be
         Current inode: 188763    Stored inode: 188627
         Current size: 397840    Stored size: 405208
         Current file modification time: 1212183645
         Stored file modification time : 1202867483
Warning

---

### Post by pedja_portugalac on 2008-07-31
After todays recommended updates I get following warnings:

> /bin/kill
/bin/ps
/usr/bin/top
/usr/bin/vmstat
/usr/bin/w
/usr/bin/watch
/usr/bin/w.procps
/sbin/sysctl

I will investigate this right now but I would like to hear if you guys get similar or same changes after todays recommended updates.

---

### Post by pedja_portugalac on 2008-07-31
Changes came from recommended update of this package: 

procps (1:3.2.7-5ubuntu2) to 1:3.2.7-5ubuntu3

All the files are inside this package only not the "/usr/bin/w" which is a shortcut of "/etc/alternatives/w" who points to "/usr/bin/w.procps" which is inside procps (1:3.2.7-5ubuntu2) to 1:3.2.7-5ubuntu3

It looks like regular recommended update. I'll check hashes when I find time, now I have to go. Cheers.

---

### Post by pedja_portugalac on 2008-07-31
OK. Hashes for procps_3.2.7-5ubuntu3_i386.deb are:

729b92bebc0e9d43eb3352f96b03197d  procps_3.2.7-5ubuntu3_i386.deb
729b92bebc0e9d43eb3352f96b03197d  procps_3.2.7-5ubuntu3_i386.deb

You can make command:

$sudo rkhunter --propupdate

---

