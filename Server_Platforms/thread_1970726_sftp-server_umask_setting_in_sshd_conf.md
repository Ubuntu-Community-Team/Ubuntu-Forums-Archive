---
title: "sftp-server umask setting in sshd_conf"
date: 2012-05-01
forum: Server Platforms
---

### Post by mogmismo on 2012-05-01
Just installed 12.04 Ubuntu Server (with OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012), and changed my /etc/ssh/sshd_conf from:

Subsystem sftp /usr/lib/openssh/sftp-server

to

Subsystem sftp /usr/lib/openssh/sftp-server -u 0002

and restarted ssh.  The sftp-server man page indicates that the -u switch should override umasks set elsewhere (.bashrc, etc...), and indeed, I've used this before on other systems w/ newish OpenSSH installs.  When connecting via sftp, I do see (from another terminal), that there is a process running that looks like this:

username   2582  2581  0 19:07 ?        00:00:00 /usr/lib/openssh/sftp-server -u 0002

so it is running correctly, it's just not applying the umask.  I've tried with sftp gui's, with sftp on the commandline, nothing seems to work.  Any ideas?

---

### Post by tylerjoh on 2012-05-08
I'm having the same problem. In addition to editing sshd_config sftp subsystem I have also tried changing system-wide umask in /etc/login.defs and tweaking /etc/pam.d/ssh by adding:

session	optional	pam_umask.so debug	umask=002

rssh/scponly?

---

