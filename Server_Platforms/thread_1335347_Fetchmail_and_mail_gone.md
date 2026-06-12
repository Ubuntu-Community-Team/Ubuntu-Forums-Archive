---
title: "Fetchmail and mail gone"
date: 2009-11-23
forum: Server Platforms
---

### Post by EdUbun on 2009-11-23
Hello

I've installed postfix and dovecot with mysql to keep the aliases and so on and have postfixadmin working too. I can add accounts, and send mail. 

How ever I've two questions:
1. where is my mail going? for external domains they are going out and arriving, But the mail log says for internal mail that the status is sent and deliverd via dovecot service. That goes for alias and actual users.

2. I want to install fetchmail to collect the mail. Though occording to the next url you need a to user. Can a catchall account be put to a to user which is the vmail user so the aliases in my db pick it up?

[http://ubuntuforums.org/showthread.php?t=1015150](http://ubuntuforums.org/showthread.php?t=1015150)

Thanks

[edit] I just found the waiting mail, it's not in my /var/mail/user folder but in /var/mail/domain/user. This probably means my dovecot needs to be adjusted to contain a domain name. Only how? I followed this manual to install it:

[http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/](http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/)

---

### Post by EdUbun on 2009-11-23
The mails are coming in from internal adresses too. I misconfigured the mail user. It was configured as USER instead of USER@DAMIN and it accepted the login. Maybe i'll filter that out one day, first to fetchmail.

---

### Post by EdUbun on 2009-11-23
Ah getting there:

For fetchmail catch all to work they say this is the fetchmailrc.
```
defaults
no dns
envelope Delivered-To:
set postmaster "MAIL"
poll SERVER
localdomains DOMAINS
proto pop3
user "ACCOUNT"
pass "PASSWORD"
to *
# fetchall
keep

```

But ...
Does this go to the normal users or the alias/users in my sql database

---

