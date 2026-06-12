---
title: "This morning Postfix just stop working"
date: 2013-04-09
forum: Server Platforms
---

### Post by fher98 on 2013-04-09
Hello everyone

Last year I installed a postfix email servir with users on a mysql DB (following this howto [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)). Everyting worked fine till today out of nowhere I cant recieve my own domains emails.

This morning it started with:

status=bounced (mail for DOMAIN.com loops back to myself)

So I added to main.cf

virtual_alias_domains = DOMAIN.com

Now im getting:

Apr  9 21:22:42 mail postfix/error[4678]: E402A21C81: to=<ME@DOMAIN.com>, relay=none, delay=0.01, delays=0.01/0/0/0, dsn=5.0.0, status=bounced (User unknown in virtual alias table)

So I did a:

root@mail:/etc/postfix# for cf in $(ls *.cf); do echo ${cf}; postmap -q [email]ME@DOMAIN.com[/email] mysql:./${cf}; done
dynamicmaps.cf
postmap: fatal: ./dynamicmaps.cf, line 8: missing '=' after attribute name: "tcp?/usr/lib/postfix/dict_tcp.so??dict_tcp_open?"
main.cf
postmap: fatal: ./main.cf: bad string length 0 < 1: dbname = 
master.cf
postmap: fatal: ./master.cf, line 10: missing '=' after attribute name: "smtp      inet  n       -       -       -       -       smtpd"
mysql_alias.cf
[email]ME@DOMAIN.com[/email]
mysql_domains.cf
mysql_mailbox.cf
ME/

So it seems that it does query the DB. Also people can login with outlook or whatever, and send emails to gmail and the like, please help im kindda lost here.
Im running postfix  version 2.8.5 on 10.04 LTS

Thanks!

---

