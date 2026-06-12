---
title: "sftp (ssh) chroot problem on ubuntu server 13.04"
date: 2013-09-04
forum: Server Platforms
---

### Post by Pha4drus on 2013-09-04
I have an ubuntu 13.04 server running at home as a fileserver. Access to the files is via samba and ssh sftp. The files to share are in /srv/data. /srv is root:root owned with drwxr-xr-x. /srv/data is owned by the only user and group that need access to the files: serveruser:servergroup with drwxrwxr-x.

I have made the default folder for sftp for serveruser /srv/data by changing the home directory for serveruser to that folder. Now I would like to chroot jail serveruser in /srv/data for sftp. 

I have tried several configuration options to achieve this in /etc/ssh/sshd_conf:

--Option 1--

Subsystem sftp /usr/lib/openssh/sftp-server
Match User serveruser[INDENT]ChrootDirectory /srv/data
AllowTCPforwarding no
x11Forwarding no
ForeCommand /usr/lib/openssh/sftp-server[/INDENT]

*Result*
Filezilla refuses connection with the message "Connection Refused".
--------------------

--Option 2--

Subsystem sftp internal-sftp
Match User serveruser[INDENT]ChrootDirectory /srv/data
AllowTCPforwarding no
x11Forwarding no
ForceCommand internal-sftp[/INDENT]

*Result*
Filezilla refuses connection with the message "Connection Refused".

I have tried by way of experiment to disable chroot options and switch between subsystem internal-sftp en /usr/lib..... Both connect just fine when no chroot is set.

I have googled for a while and searched the forum, but am lost right now. Any help or pointers would be greatly appreciated.

---

### Post by TheFu on 2013-09-04
[http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-chrooted-ssh-sftp-debian-squeeze](http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-chrooted-ssh-sftp-debian-squeeze) explains how to setup a chroot.  Having samba access to that same storage could be problematic, but I honestly don't know.  To understand chroot better, review the wikipedia article. [https://en.wikipedia.org/wiki/Chroot](https://en.wikipedia.org/wiki/Chroot)  be certain to carefully review the "limitations" section.

---

### Post by SeijiSensei on 2013-09-04
A chrooted service requires that separate copies of all the binaries, libraries, and configuration files the program uses be maintained in the chroot tree.  For instance, the RedHat implementation of BIND runs chrooted.  It requires a lib, var, and etc directory below the top of the chroot.  This can be a pain in the butt to implement manually.  You cannot symlink these files to their corresponding copies in the real directory tree either, since anything above the top of the chroot is invisible to the application.

Short answer, just telling sshd to chroot /srv/data is probably not sufficient.

---

### Post by Pha4drus on 2013-09-05
Thank you TheFu and SeijiSensei. 

By reviewing the howtoforge guide I realized I am chrooting to /srv/data which is not root:root owned. I think I should chroot to /srv, which is root owned. Will try this later today.

SeijiSensei, I understand what you are saying, though all guides I've read say this problem is solved by using the internal sftp subsystem and ForceCommand. If chrooting to /srv also does not work, I'll try copying /usr/lib/ssh/sftp-server to the jail.

---

