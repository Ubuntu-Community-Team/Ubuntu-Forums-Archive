---
title: "strange log entries....."
date: 2004-11-29
forum: Server Platforms
---

### Post by gballard on 2004-11-29
**In the auth.log:**
Nov 29 10:33:29 localhost sshd[11284]: Did not receive identification string from ::ffff:21$
Nov 29 10:39:57 localhost sshd[11311]: Illegal user patrick from ::ffff:211.33.175.54
Nov 29 10:39:59 localhost sshd[11313]: Illegal user patrick from ::ffff:211.33.175.54

**In the daemon.log:**
Nov 28 18:27:53 localhost proftpd[6804]: localhost.localdomain (213.149.238.3[213.149.238.3
Nov 28 18:27:53 localhost proftpd[6804]: localhost.localdomain (213.149.238.3[213.149.238.3
Nov 29 11:17:04 localhost proftpd[11542]: localhost.localdomain (208.62.217.86[208.62.217.86
Nov 29 11:28:14 localhost proftpd[11542]: localhost.localdomain (208.62.217.86[208.62.217.86
Nov 29 11:28:14 localhost proftpd[11542]: localhost.localdomain (208.62.217.86[208.62.217.86

Someone doing a scan perhaps?

---

### Post by HungSquirrel on 2004-11-29
Is your username patrick?

---

### Post by gballard on 2004-11-30
[QUOTE=HungSquirrel]Is your username patrick?[/QUOTE]
 nope...no idea who patrick is...

---

### Post by jdong on 2004-11-30
It seems like somehow sshd is getting some FTP traffic -- perhaps a port number confusion (22 vs 21)

Perhaps a faulty FTP client. Are you running a public FTP server?

---

### Post by gballard on 2004-12-03
[QUOTE=jdong]It seems like somehow sshd is getting some FTP traffic -- perhaps a port number confusion (22 vs 21)

Perhaps a faulty FTP client. Are you running a public FTP server?[/QUOTE]
 I am running an ftp server..yes...proftpd...

---

### Post by jdong on 2004-12-04
Seems like a problem with faulty FTP clients. Don't worry about it, then!

---

