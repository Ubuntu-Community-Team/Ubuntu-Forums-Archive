---
title: "File Server Suggestions"
date: 2007-05-12
forum: Server Platforms
---

### Post by acegolfer on 2007-05-12
I want to set up a directory so that I can access/read/write from

1. within Ubuntu locally
2. from internet using XP (not home networked and can't use VPN but I do have a domain name for Ubuntu)

What are my options?

---

### Post by StarMonkee on 2007-05-12
Samba would be ok for local access, but xp connecting to network shares over the internet isn't that stable.

Personally I'd go for an ftp server like vsftp or proftp

---

### Post by elst on 2007-05-12
The SFTP facility of SSH is probably the best option - you can get Free clients for Windows, including versions that run directly from pen drives. FTP transmits usernames and passwords without encryption, so isn't really safe. FTP is actually largely obsolete at this point.

---

### Post by heimo on 2007-05-12
WinSCP is nice sftp client for Windows:
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

---

