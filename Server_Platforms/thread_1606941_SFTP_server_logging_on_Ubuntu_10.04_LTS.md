---
title: "SFTP server logging on Ubuntu 10.04 LTS"
date: 2010-10-27
forum: Server Platforms
---

### Post by hawk2010 on 2010-10-27
Hi all,

I have recently configured sshd_config to have chrooted SFTP service. I'm using SFTP internal-sftp config. However now I have to figure out how to log file transfers happening using the SFTP service. I tried looking up on the net but couldn't find any good solution. I'm using the Ubuntu Server 10.04 (64bit) Would be glad if someone could help me on this.

Thanks!

---

### Post by albandy on 2010-10-27
[http://ubuntuforums.org/showthread.php?t=241188](http://ubuntuforums.org/showthread.php?t=241188)

---

### Post by hawk2010 on 2010-10-27
Tried it but getting the following errors
root@fs1:/usr/lib# patch -p0 < openssh-5.3p1.sftpfilecontrol-v1.3.patch 
patching file openssh-5.3p1-sftp_mods/version.h
Hunk #1 FAILED at 5.
1 out of 1 hunk FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/version.h.rej
patching file openssh-5.3p1-sftp_mods/servconf.c
Hunk #1 succeeded at 118 with fuzz 2 (offset -1 lines).
Hunk #2 FAILED at 114.
Hunk #3 FAILED at 231.
Hunk #4 succeeded at 268 with fuzz 2 (offset -2 lines).
Hunk #5 succeeded at 436 with fuzz 2 (offset -3 lines).
Hunk #6 FAILED at 651.
Hunk #7 FAILED at 1160.
Hunk #8 FAILED at 1301.
5 out of 8 hunks FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/servconf.c.rej
patching file openssh-5.3p1-sftp_mods/servconf.h
Hunk #1 FAILED at 35.
Hunk #2 succeeded at 144 with fuzz 1 (offset -1 lines).
1 out of 2 hunks FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/servconf.h.rej
patching file openssh-5.3p1-sftp_mods/session.c
Hunk #1 FAILED at 111.
Hunk #2 FAILED at 957.
Hunk #3 FAILED at 1083.
3 out of 3 hunks FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/session.c.rej
patching file openssh-5.3p1-sftp_mods/sftp-server.8
Hunk #1 succeeded at 50 with fuzz 2 (offset -1 lines).
Hunk #2 FAILED at 84.
1 out of 2 hunks FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/sftp-server.8.rej
patching file openssh-5.3p1-sftp_mods/sshd.c
Hunk #1 FAILED at 379.
1 out of 1 hunk FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/sshd.c.rej
patching file openssh-5.3p1-sftp_mods/sftp-server.c
Hunk #1 succeeded at 50 with fuzz 2 (offset -1 lines).
Hunk #2 FAILED at 506.
Hunk #3 FAILED at 518.
Hunk #4 FAILED at 709.
Hunk #5 FAILED at 714.
Hunk #6 FAILED at 733.
Hunk #7 FAILED at 758.
Hunk #8 FAILED at 763.
Hunk #9 FAILED at 783.
Hunk #10 FAILED at 922.
Hunk #11 succeeded at 1214 with fuzz 2 (offset -2 lines).
Hunk #12 succeeded at 1276 with fuzz 2 (offset -3 lines).
9 out of 12 hunks FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/sftp-server.c.rej
patching file openssh-5.3p1-sftp_mods/sshd_config
Hunk #1 FAILED at 91.
1 out of 1 hunk FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/sshd_config.rej
patching file openssh-5.3p1-sftp_mods/sshd_config.5
Hunk #1 FAILED at 558.
1 out of 1 hunk FAILED -- saving rejects to file openssh-5.3p1-sftp_mods/sshd_config.5.rej

---

### Post by albandy on 2010-10-27
Of course, it will not work because of the sshd versions.

You have to modify the patch in order to work with your sshd version. So read the patch, see what code the patch modifies and compare it to the sshd source code and then modify the patch according to sshd source code.

---

