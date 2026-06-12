---
title: "LFTP command"
date: 2010-01-23
forum: Server Platforms
---

### Post by xernet on 2010-01-23
Hello.

I want use my ubuntu 8.04LTS to backup and mirror some files to a mine hosting web.
So, i want use lftp command.

Tipical command is:
lftp -u user,password -p [port] [server]

But i have a problem, login of mine hosting account has "@" so lftp return an error...

Infact, to connect on mine hosting web through FTP i use following parameters:

login: [email]121131@isp-domain.com[/email]
host: [www.myrealdomain.net](www.myrealdomain.net)

When i use "-u user,password" lftp get the "@" of user parameter as separator for domain, infact LFTP try to connect to isp-domain.com and not on my host....

How can i solve this matter?
Thanx in advance!

---

### Post by HermanAB on 2010-01-23
Howdy, first try to esacape the @ with a slash.  Otherwise, try using wget instead of lftp.

---

### Post by xernet on 2010-01-23
> **HermanAB said:**
> Howdy, first try to esacape the @ with a slash.  Otherwise, try using wget instead of lftp.
i cannot use wget, i must send my files and directory (mirror) from ubuntu server to webhosting...

Does not work with slash :-(

---

