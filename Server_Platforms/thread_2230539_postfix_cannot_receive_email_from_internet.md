---
title: "postfix cannot receive email from internet"
date: 2014-06-19
forum: Server Platforms
---

### Post by redstone3 on 2014-06-19
Hello experts,
I am been working on my postfix issue for quite a few days but still can't make it work. please help.

I read many post and did some tests, so I think most of the configuration are good.

issue:
- send and receive email internally are all good
- can send email out to [email]xxx@gmail.com[/email] or any outside emails; ok to send
- can not receive email from any outside email.


I did the following test which are all correct:
1) nslook -type=mx mydomainabc.com, returns mail.mydomainabc.com, and point to my internet IP; 
   I use DNSexit and configured MX records there. I think this test can prove that the MX record is OK;
2) I have router forward port 25 traffic to my mail server; this can be proved by remotely running "telnet mail.mydomainabc.com 25" from outside and it works.
3) from server, run "netstat -tupln", port 25 is listening. I think the above test can also prove the server is listening on port 25.

However, when sending email from gmail, I got the following error code: 
```
[(0) [x.x.x.x]:25: Connection timed out]
```
here,  x.x.x.x is the internet IP of my home router.

please send me a private message, so I can give you my domain name. don't want to release it here because my server is not well-hardened yet.



_output of **postconf -n**:_
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
body_checks = regexp:/etc/postfix/body_checks
header_checks = regexp:/etc/postfix/header_checks
...
inet_interfaces = all
inet_protocols = ipv4
mail_owner = postfix
......
mydestination = $myhostname, $mydomain
mydomain = mydomainabc.com
myhostname = mail.mydomainabc.com
mynetworks = 192.168.1.1/24, 127.0.0.0/8
myorigin = $mydomain
...
relayhost = smtp10.bellnet.ca
...
smtpd_client_restrictions = permit_mynetworks,reject_unknown_client,permit
smtpd_recipient_restrictions = permit_mynetworks,permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
unknown_local_recipient_reject_code = 550


```

help please. 
thanks
Redstone

---

### Post by DJ_Max on 2014-06-21
Run your domain through DNSstuff.com

Did  you check to see if your server is blacklisted? Do you have a firewall in place?

---

