---
title: "can't connect to sendmail port 25"
date: 2008-05-05
forum: Server Platforms
---

### Post by skunkwerk on 2008-05-05
I setup postfix/sendmail on my ubuntu 7.10 box.  I can send mail when i'm logged in locally, but can't connect to the server via smtp remotely and send mail through TLS.

I've opened port 25 on the router, but when I telnet to mydomain.com 25 it times out

on the server:
ps -ef|grep sendmail
root 3675 3225 0 08:35 pts/1 00:00:00 grep sendmail

netstat -an|grep 25 has some ip addresses with ESTABLISHED but none of them are on port 25

i tried uncommenting some lines in master.cf but i got some errors:
/var/log/mail.log has a bunch of ipv6 warnings and this line:
fatal: /etc/postfix/master.cf: line 12: bad transport type: =

i added: 
25 inet n - - - - smtpd
mynetworks = 127.0.0.0/8, 192.168.0.0/24

any suggestions?
thanks

---

### Post by Big Ed on 2008-05-09
A lot of ISP's block access to port 25 these days.  All part of the fight against spam.  Try using a higher port number either on your server or use a redirect in the router.

HTH,
Ed

---

