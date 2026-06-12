---
title: "PostFix send e-mails to .Com's but not .Edu, .Net"
date: 2009-02-12
forum: Server Platforms
---

### Post by k2chris1983 on 2009-02-12
Hello All,

I'm having an issue with Postfix which it will send e-mail out to gmail.com and anything that has a .com, but it will not send e-mails to .net, .edu and so on. I'm using a client (Thunderbird) to send the e-mail, but when I login to Webmail and try - it works.

My postconf -n

```


alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
mailbox_size_limit = 0
mydestination = $myhostname, localhost.$mydomain, $mydomain
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
sender_bcc_maps = hash:/etc/postfix/bcc
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = hash:/etc/postfix/virtual


```

and here is the error from maillog.

> 

Feb 11 18:09:50 MyServerName postfix/smtpd[20261]: NOQUEUE: reject: RCPT from domain.com[*.*.*.*]: 554 5.7.1 <lthomas@latech.edu>: Relay access denied; from=<my@email.com> to=<thetest@latech.edu> proto=ESMTP helo=<[192.168.1.101]>




Note: I have change the IP to *.*.*.* and where it's coming from. Also the postfix -n looks small from other configs I seen. I'm thinking it could be the config but if you need the postconf -d, I can do that.

Thanks,

Chris

---

### Post by k2chris1983 on 2009-02-12
Any clue?

---

### Post by k2chris1983 on 2009-02-12
I got it working... 

It was a problem with saslauthd not talking to postfix. 

Here is the link I followed from if anyone has problems like this!

[http://jonsview.com/2008/07/14/setting-up-email-services-on-ubuntu-hardy-using-postfix-and-courier](http://jonsview.com/2008/07/14/setting-up-email-services-on-ubuntu-hardy-using-postfix-and-courier)

---

