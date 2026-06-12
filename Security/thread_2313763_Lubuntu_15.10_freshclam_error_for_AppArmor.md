---
title: "Lubuntu 15.10 freshclam error for AppArmor"
date: 2016-02-15
forum: Security
---

### Post by lance bermudez on 2016-02-15
AppArmor Message
/var/log/kern.log contains 1 denied message in the last day 

AppArmor Message
profile: /usr/bin/freshclam
Operation: open
Name: /var/log/clamav/freshclam.log.1
denied: r
logfile: /var/log/kern.log

in /var/log/kern.log
Feb 15 14:29:52 Tardis kernel: [  132.575959] audit: type=1400 audit(1455571792.565:32): apparmor="DENIED" operation="open" profile="/usr/bin/freshclam" name="/var/log/clamav/freshclam.log" pid=3176 comm="freshclam" requested_mask="r" denied_mask="r" fsuid=112 ouid=112

---

### Post by SeijiSensei on 2016-02-15
Is this the version of freshclam in the repositories or one you compiled yourself?  If the latter, you'll probably have to futz with AppArmor to fix this problem.

If not, then check the permissions on the log files.  Some files like /var/log/syslog and /var/log/kern.log have user syslog and group adm as owners not root.  Also check the ownership of /var/log/clamav and its files.

---

### Post by lance bermudez on 2016-02-16
usr.bin.freshclam has in it
```

# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@ubuntu.com>
# Last Modified: Sun Aug  3 09:39:03 2008

#include <tunables/global>

/usr/bin/freshclam {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  capability setgid,
  capability setuid,

  @{PROC}/filesystems r,
  owner @{PROC}/[0-9]*/status r,

  /etc/clamav/clamd.conf r,
  /etc/clamav/freshclam.conf r,
  /etc/clamav/onerrorexecute.d/* mr,
  /etc/clamav/onupdateexecute.d/* mr,
  /etc/clamav/virusevent.d/* mr,

  owner @{HOME}/.clamtk/db/ rw,
  owner @{HOME}/.clamtk/db/** rwk,

  owner @{HOME}/.klamav/database/ rw,
  owner @{HOME}/.klamav/database/** rwk,

  /usr/bin/freshclam mr,

  /var/lib/clamav/ r,
  /var/lib/clamav/** krw,

  /var/log/clamav/* kw,
  /{,var/}run/clamav/freshclam.pid w,
  /{,var/}run/clamav/clamd.ctl rw,

  deny /{,var/}run/samba/{gencache,unexpected}.tdb mrwkl,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.freshclam>
}

```

Do I change the owner ship from adm to root?
```

$ ls -l /var/log/syslog
-rw-r----- 1 syslog adm 208297 Feb 16 11:42 /var/log/syslog

$ ls -l /var/log/kern.log
-rw-r----- 1 syslog adm 107194 Feb 16 11:10 /var/log/kern.log

ls -l /var/log/clamav
total 160
-rw-r----- 1 clamav adm  14367 Aug  4  2015 clamav.log
-rw-r----- 1 clamav adm  13862 Aug  2  2015 clamav.log.1
-rw-r----- 1 clamav adm   3748 Jul 29  2015 clamav.log.2.gz
-rw-r--r-- 1 root   root  4880 Jul 15  2015 clamfs.log
drwxrwx--x 2 clamav adm   4096 Feb  7 20:19 clamscan
-rw-r----- 1 clamav adm  11439 Feb 16 11:09 freshclam.log
-rw-r----- 1 clamav adm  22087 Feb 15 14:39 freshclam.log.1
-rw-r----- 1 clamav adm   2612 Dec  6 07:59 freshclam.log.10.gz
-rw-r----- 1 clamav adm   6951 Dec  3 08:00 freshclam.log.11.gz
-rw-r----- 1 clamav adm   5241 Nov  8 07:48 freshclam.log.12.gz
-rw-r----- 1 clamav adm   2196 Feb  7 07:47 freshclam.log.2.gz
-rw-r----- 1 clamav adm   2356 Feb  1 14:57 freshclam.log.3.gz
-rw-r----- 1 clamav adm   3161 Jan 28 07:35 freshclam.log.4.gz
-rw-r----- 1 clamav adm   6175 Jan 23 07:35 freshclam.log.5.gz
-rw-r----- 1 clamav adm   7977 Jan  3 07:36 freshclam.log.6.gz
-rw-r----- 1 clamav adm   9661 Dec 28 08:04 freshclam.log.7.gz
-rw-r----- 1 clamav adm   6398 Dec 20 08:03 freshclam.log.8.gz
-rw-r----- 1 clamav adm   3778 Dec 14 09:23 freshclam.log.9.gz

```

---

