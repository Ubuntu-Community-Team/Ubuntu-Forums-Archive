---
title: "scponly &amp; winbind based ssh auth"
date: 2008-07-31
forum: Security
---

### Post by ulukay on 2008-07-31
hi

i'm trying to setup a chrooted sftp server (therefor i'm using scponlyc) with domain authentication. logging into a plain shell over ssh works fine with the domain users, but using scponlyc gives me an error (respectively no error, it just closes the connection) 
domain auth works with winbind/pam.

# getent passwd | grep mer
DOMAIN?mer:*:10011:10000:Hugo Tester:/raid5/home/DOMAIN/mer:/usr/sbin/scponlyc

and here's the debug log:
Jul 31 14:03:38 u096 sshd[4626]: pam_winbind(sshd:account): user 'DOMAIN?mer' OK
Jul 31 14:03:38 u096 sshd[4626]: pam_winbind(sshd:account): user 'DOMAIN?mer' granted access
Jul 31 14:03:38 u096 sshd[4626]: Accepted publickey for DOMAIN?mer from 10.10.10.71 port 41960 ssh2
Jul 31 14:03:38 u096 sshd[4628]: pam_unix(sshd:session): session opened for user DOMAIN?mer by (uid=0)
Jul 31 14:03:38 u096 sshd[4628]: subsystem request for sftp
Jul 31 14:03:38 u096 scponly[4629]: chrooted binary in place, will chroot()
Jul 31 14:03:38 u096 scponly[4629]: 3 arguments in total.
Jul 31 14:03:38 u096 scponly[4629]: ^Iarg 0 is scponlyc
Jul 31 14:03:38 u096 scponly[4629]: ^Iarg 1 is -c
Jul 31 14:03:38 u096 scponly[4629]: ^Iarg 2 is /usr/lib/openssh/sftp-server
Jul 31 14:03:38 u096 scponly[4629]: opened log at LOG_AUTHPRIV, opts 0x00000009
Jul 31 14:03:38 u096 scponly[4629]: retrieved home directory of "/raid5/home/DOMAIN/mer" for user "DOMAIN?mer"
Jul 31 14:03:38 u096 scponly[4629]: chrooting to dir: "/raid5/home/DOMAIN/mer"
Jul 31 14:03:38 u096 scponly[4629]: chdiring to dir: "/"
Jul 31 14:03:38 u096 scponly[4629]: chdiring to dir: "/"
Jul 31 14:03:38 u096 scponly[4629]: setting uid to 10011
Jul 31 14:03:39 u096 scponly[4629]: processing request: "/usr/lib/openssh/sftp-server"
Jul 31 14:03:39 u096 scponly[4629]: running: /usr/lib/sftp-server (username: DOMAIN?mer(10011), IP/port: 10.10.10.71 41960 22)
Jul 31 14:03:39 u096 sshd[4628]: pam_unix(sshd:session): session closed for user DOMAIN?mer

since there are no real error messages i haven't got a clue what goes wrong.

---

### Post by ulukay on 2008-08-04
bump

---

