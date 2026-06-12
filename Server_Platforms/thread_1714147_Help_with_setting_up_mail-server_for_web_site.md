---
title: "Help with setting up mail-server for web site"
date: 2011-03-25
forum: Server Platforms
---

### Post by Farrukhjon on 2011-03-25
Hi guys, help me to setting up the mail server for my site. The situation is such that it is necessary to allow access through the site (built under LAMP) to the mail server. Ligament postfix + dovecot good option? or who have a similar configs mail server,  please give me.
Thanks in advance.

---

### Post by coolburnmx on 2011-03-25
Try postfix + courier, but with the smtps and pop3s protocols, because some ISP block by default the 25 port (smtp)

try [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

the server is a complete virtual mail server in SQL, the web interface is preforge

---

