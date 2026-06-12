---
title: "Root warning"
date: 2013-10-22
forum: Security
---

### Post by Algoodman on 2013-10-22
[ Rootkit Hunter version 1.3.8 ]

[1;33mChecking rkhunter version...[0;39m
  This version  : 1.3.8
  Latest version: 1.4.0
  Update available
[ Rootkit Hunter version 1.3.8 ]

[1;33mChecking rkhunter data files...[0;39m
  Checking file mirrors.dat[34C[ [1;32mNo update[0;39m ]
  Checking file programs_bad.dat[29C[ [1;32mNo update[0;39m ]
  Checking file backdoorports.dat[28C[ [1;32mNo update[0;39m ]
  Checking file suspscan.dat[33C[ [1;32mNo update[0;39m ]
  Checking file i18n/cn[38C[ [1;32mNo update[0;39m ]
  Checking file i18n/de[38C[ [1;32mNo update[0;39m ]
  Checking file i18n/en[38C[ [1;32mNo update[0;39m ]
  Checking file i18n/zh[38C[ [1;32mNo update[0;39m ]
  Checking file i18n/zh.utf8[33C[ [1;32mNo update[0;39m ]
Warning: The command '/sbin/ifdown' has been replaced by a script: /sbin/ifdown: Bourne-Again shell script text executable
Warning: The command '/sbin/ifup' has been replaced by a script: /sbin/ifup: Bourne-Again shell script text executable
Warning: The command '/usr/bin/groups' has been replaced by a script: /usr/bin/groups: Bourne shell script text executable
Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne shell script text executable
Warning: The command '/usr/bin/whatis' has been replaced by a script: /usr/bin/whatis: Bourne shell script text executable
Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Hidden directory found: /dev/.udev
Warning: Hidden file found: /usr/share/man/man1/..1.gz: gzip compressed data, from Unix, max compression
Warning: Hidden file found: /usr/bin/.fipscheck.hmac: ASCII text
Warning: Hidden file found: /usr/bin/.ssh.hmac: ASCII text
Warning: Hidden file found: /usr/sbin/.sshd.hmac: ASCII text
Warning: Application 'httpd', version '2.2.3', is out of date, and possibly a security risk.
Warning: Application 'openssl', version '0.9.8e', is out of date, and possibly a security risk.
Warning: Application 'sshd', version '4.3p2', is out of date, and possibly a security risk.

Please what do i do about this?

---

### Post by sandyd on 2013-10-22
moved to security discussions

---

### Post by oldos2er on 2013-10-22
See [http://ubuntuforums.org/showthread.php?t=1555978](http://ubuntuforums.org/showthread.php?t=1555978)

---

### Post by Algoodman on 2013-10-22
Thanks oldos2er, its helpful.

---

