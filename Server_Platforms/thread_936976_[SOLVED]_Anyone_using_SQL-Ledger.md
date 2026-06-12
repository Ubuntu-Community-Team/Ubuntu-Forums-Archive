---
title: "[SOLVED] Anyone using SQL-Ledger?"
date: 2008-10-03
forum: Server Platforms
---

### Post by volkswagner on 2008-10-03
I have intalled Sql-ledger, and postresql-8.1 on 6.06 LAMP server.  I am using named based virtual hosts.

I am not sure what to edit in sql-ledger.conf so it is stock.

I can't run the .pl files.  They show up as a download file in firefox.

When I try to run the admin.pl in a terminal I get the following error.

```
~$ /usr/lib/sql-ledger/admin.pl
Can't locate bin/xterm/admin.pl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/sql-ledger/admin.pl line 118.
```

Attached is the perl script.  I don't see the relevance at line 118 and the error.  I renamed admin.pl to admin.txt to allow download.

---

### Post by lykwydchykyn on 2008-10-03
SQL ledger is written in perl, so you need to install the appropriate libraries and configure apache to interpret perl scripts rather than present them for download. 

Do you have libapache2-mod-perl2 installed?

---

### Post by volkswagner on 2008-10-03
thanks, that was easy.  Just putty'd into my server and installed the package.  Al from my Nokia N95.

---

