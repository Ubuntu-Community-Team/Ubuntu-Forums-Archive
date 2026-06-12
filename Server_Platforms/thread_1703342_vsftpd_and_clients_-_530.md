---
title: "vsftpd and clients - 530"
date: 2011-03-09
forum: Server Platforms
---

### Post by Turiko on 2011-03-09
Hello all,

I recently built a little fileserver for personal use. When i don't need it, i put on standby, and i use wakeonlan. The system runs ubuntu 10.04.

vsftpd seems to work fine if i connect to it from my windows pc, using the [ftp://192.168.1.10](ftp://192.168.1.10) and entering the login in the dialog box or just username:password before the ip.

However, i would prefer to mount the drive. Any program i try to log in on except windows explorer now returns error 530 access denied... I tried this using two utilities to mount as a drive, but even firefox can't connect :o.

I know for sure that the login is correct, and it seems i'm stuck with the worst way of accessing ftp right now :(.

Could anyone shed some light on why this seems to happen? I'm thinking it's some configuration in vsftpd, but i'm still very much a noob when it comes to anything linux - i can only do basic things in the console.

---

### Post by aeiah on 2011-03-09
have you tried with an actual ftp client? use filezilla and see what errors it spits out

---

### Post by Turiko on 2011-03-09
This is what i get in filezilla

Antwoord:	530 Login incorrect.
Fout:	Fatale fout
Fout:	Kan niet verbinden met server

translated:
response: 530 login incorrect.
error: fatal error
error: could not connect to server

Right after trying to connect with filezilla, i connected using windows explorer, and it works.

---

### Post by Lars Noodén on 2011-03-11
You may already have SFTP up and running.  That is a lot easier to work with than FTP.  

If you have OpenSSH server already  on that machine, then you're all set and do not need FTP. It is probably easier to add the SSH server than to debug and secure FTP over SSL.

---

