---
title: "Apache big problems : apt-get -f install removed it!"
date: 2015-07-12
forum: Server Platforms
---

### Post by dmitry33 on 2015-07-12
Hi everyone,

Can you please help me.

The next thins happened;
1) I wanted to install TeamViewer on Ubuntu 14.04x64
2) There was some dependencies problems, so I performed ```
apt-get -f install
```
3) After that there a long time of updating/installing, and I mentioned that apache server was restarted, all the websites get down.
4) After that I tried to do ```
service apache2 start
``` but appeared an error that there is no such service.
5) I found out that mysql and apache are NOT installed. But folders with websites and mysql databases are on the right spot.
6) I installed apache2 and mysql server... But now version of apache 2.4.10, but it was 2.2
7) when I try to open website I have "Forbidden. You don't have permission to access"
8) I have the same error even after changing "etc/apache2/sites-available/" parameters to ```
[COLOR=#333333][FONT=Menlo]Require all granted[/FONT][/COLOR]
``` and change the fite resolution to *.conf,
and one intesesting things I founded is that all files in sites-available got "100-" in the beginning of filename (example site.conf became 100-site.conf)

Can you please advise me how to overcome that issue and if it's possible to get all back (like a restore)...
Do you think that rollback to version 2.2 will solve the problem and will not give more new problems?

Thank you very much in advance.

---

