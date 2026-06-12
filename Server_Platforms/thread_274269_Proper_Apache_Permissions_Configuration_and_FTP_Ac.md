---
title: "Proper Apache Permissions Configuration and FTP Access to Web Site"
date: 2006-10-09
forum: Server Platforms
---

### Post by Avian00 on 2006-10-09
Hello,

Can somebody please advise me on the ideal permissions configuration for a web server running php, mysql and some cgi scripts?  I understand that all child apache processes are executed as www-data.www-data.  Should I be chowing the entire website to www-data.www-data?  This seems to create a problem, since I want to make the site accessible via FTP to other users who will actually create and maintain the site.

As a side note, I feel I should point out that Ubuntu's implementation of Apache seems to differ from Apache's documented implementation.  All the manuals I read seem to strongly indicate that websites should reside in /home/user directories.  However, ubuntu places them in /var/www.  Can somebody also please speak to this?  Thanks!

Matt

---

