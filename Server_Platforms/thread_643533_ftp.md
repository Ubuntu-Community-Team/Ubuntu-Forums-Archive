---
title: "ftp"
date: 2007-12-17
forum: Server Platforms
---

### Post by hobojjr on 2007-12-17
I installed apache2 server. Now I would like to allow some people to manipulate my site via ftp.

I tried vsftpd but I can't figure out how to manipulate user's privilege they way I want to. For example I one some users to be able to just download and browse my whole site, some user to be able to create new folders and upload new stuff, and others to be confined to their own folders.

Then I tried gproftpd and it does what I want to. The only problem is that I can't figure out how to do it via command line or config files.

Anyone knows how to do this?

---

### Post by HermanAB on 2007-12-17
Proftpd can be configured to make certain directories 'invisible' to certain users.  It is the best FTP server for web site management.  Read the man page a few times.

---

### Post by hobojjr on 2007-12-18
> **HermanAB said:**
> Proftpd can be configured to make certain directories 'invisible' to certain users.  It is the best FTP server for web site management.  Read the man page a few times.

I find their docs to be very bad. I've been trying to set up logging for proftpd but I can't figure out how and I can't find anything usefull in the docs. The default logs are empty /var/logs/proftpd/ and when I try to remove # from gp_html_path in config file for proftpd I get a parse error  on restart.

Perhaps we are reading different mans???

---

