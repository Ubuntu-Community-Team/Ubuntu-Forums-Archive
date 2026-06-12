---
title: "403 Forbidden"
date: 2009-06-01
forum: Server Platforms
---

### Post by sup3rs3nior on 2009-06-01
On Ubuntu Server 9.04, I have vsftp installed and running. When I create files in /var/www via command line (nano), I can access them via http. However, when I use an FTP client to create a file (/var/www/jr in this case), two strange things happen.

1. When I check the file permissions by running "ls -l /var/www/jr" it lists the permissions as "????????? ? ? ?" which makes no sense at all.

2. When I try to access the files via http, I get a 403 forbidden error, even though I set the permission to be readable by all ("sudo chmod a+r /var/www/jr" with no errors).

I can still access files in the main directory (/var/www) via http. But I created all the files in the main directory with nano running on the server.

I am officially stumped.

---

### Post by sup3rs3nior on 2009-06-01
Well I actually figured this one out. Here is where the problem was.

When I created the directory and files with the ftp client, it left poor apache out of the owner list. I had to do a little chown command.

"chown -R www-data:www-data /var/www"

"www-data" apparently represents apache.

=) Lesson learned.

---

