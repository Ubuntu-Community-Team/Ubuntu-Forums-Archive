---
title: "problems with very secure ftp server"
date: 2005-03-24
forum: Server Platforms
---

### Post by iomicifikko on 2005-03-24
hi guys, i installed vsftpd to access a few of my folders via internet but when i try accessing the server via localhost [ftp://127.0.0.1](ftp://127.0.0.1) to see if the server works i have a problem, i am able to see the tree and all the files and directories, i can go within dirs too, but im not able to open files ( i tryed with txt files, set to be only readable by anyone, and writeable by root, the owner:  644)

the error i receive is:  550 Failed to open file

ps: according to the little guide i followed (im a newbie in these things) i should be able to start,stop and reload the server with "#vsftpd start/stop/reload" everywhere or at least in /etc/init.d/ (here is the vsftpd executable) but i receive this error:  "500 OOPS: vsftpd: cannot open config file: stop/start/reload"

always according to the guide if i type "grep ftp /etc/passwd" i should receive the following "ftp:x:101:65534::/home/ftp:/bin/false"; i actually receive 105 instead of 101

ppss: where can i find the meanings of all these error-codes?

thanks for any help!

bye

---

### Post by artnay on 2005-03-24
You should set all the directories which you want to be accessible to read and executable (5). In Unix world this is needed, read permission isn't enough. Can't help with the warnings and errors, sorry.

---

### Post by alastair on 2005-03-24
Note - the first place to look would always be the ftp daemon log file.

For your user id question - the docs don't know what the next spare uid is on any specific system (e.g. yours). So the /etc/passwd uid would not necessarily match ...

For FTP error codes etc., you could take a look at the FTP RFC e.g. 

[http://www.faqs.org/rfcs/rfc959.html](http://www.faqs.org/rfcs/rfc959.html)

(this might be slightly out of date - but error codes are near the end).

---

