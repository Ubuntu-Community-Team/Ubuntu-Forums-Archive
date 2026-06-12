---
title: "Mail Server Can't Receive Email But Can Send Email - Postfix, Dovecot, Postgresql"
date: 2016-07-05
forum: Server Platforms
---

### Post by vince.the on 2016-07-05
Hallo!

I have server where I want to set up a mail server to let me receive and send email from my domain. I'm currently having a problem where while I am can not receive mails. Sending emails works perfect.

I'm going off of this script, which shows how to configure a mail server using Postfix, Dovecot, and using Postgresql as the backend ([https://gist.github.com/solusipse/7ed8e1da104baaee3f05](https://gist.github.com/solusipse/7ed8e1da104baaee3f05)).


/etc/postfix/main.cf:
```

    relay_domains =
    virtual_alias_maps = proxy:pgsql:/etc/postfix/virtual_alias_maps.cf
    virtual_mailbox_domains = proxy:pgsql:/etc/postfix/virtual_mailbox_domains.cf
    virtual_mailbox_maps = proxy:pgsql:/etc/postfix/virtual_mailbox_maps.cf
    virtual_mailbox_base = /home/vmail
    virtual_mailbox_limit = 512000000
    virtual_minimum_uid = 5000
    virtual_transport = virtual
    virtual_uid_maps = static:5000
    virtual_gid_maps = static:5000
    local_transport = virtual
    local_recipient_maps = 
    transport_maps = hash:/etc/postfix/transport


    smtpd_sasl_auth_enable = yes
    smtpd_sasl_type = dovecot
    smtpd_sasl_path = private/auth
    smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
    smtpd_sasl_security_options = noanonymous
    smtpd_sasl_tls_security_options = 
    smtpd_tls_auth_only = yes
    smtpd_tls_cert_file = /etc/ssl/private/server.crt
    smtpd_tls_key_file = /etc/ssl/private/server.key
    smtpd_sasl_local_domain = 
    broken_sasl_auth_clients = yes
    smtpd_tls_loglevel = 1
    html_directory = /usr/share/doc/postfix/html
    queue_directory = /var/spool/postfix
    mydestination = localhost

``` 

/etc/dovecot/dovecot.conf:
```

    protocols = imap
    auth_mechanisms = plain
    passdb {
        driver = sql
        args = /etc/dovecot/dovecot-sql.conf
    }
    userdb {
        driver = sql
        args = /etc/dovecot/dovecot-sql.conf
    }
    service auth {
        unix_listener /var/spool/postfix/private/auth {
        group = postfix
        mode = 0660
        user = postfix
        }
        user = root
    }
    mail_home = /home/vmail/%d/%u
    mail_location = maildir:~
    ssl_cert = </etc/ssl/private/server.crt
    ssl_key = </etc/ssl/private/server.key

``` 

/var/logs/mail.log:
```
 
    Apr 17 19:46:18 v22015072919626549 postfix/smtpd[8837]: connect from ***
    Apr 17 19:46:18 v22015072919626549 postfix/smtpd[8837]: 62D6A3E0DC9: client=***
    Apr 17 19:46:18 v22015072919626549 postfix/cleanup[8843]: 62D6A3E0DC9: message-id=***
    Apr 17 19:46:18 v22015072919626549 postfix/smtpd[8837]: disconnect from ***
    Apr 17 19:46:18 v22015072919626549 postfix/qmgr[9001]: 62D6A3E0DC9: from=<***>, size=1160, nrcpt=1 (queue active)
    Apr 17 19:46:18 v22015072919626549 postfix/virtual[8844]: 62D6A3E0DC9: to=<***>, relay=virtual, delay=0.05, delays=0.01/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
    Apr 17 19:46:18 v22015072919626549 postfix/qmgr[9001]: 62D6A3E0DC9: removed

```

---

### Post by Graham_Willis on 2016-07-06
How exactly do you test if you can send e-mails to your domain and if it can receive them?
Did you try to send e-mails to this domain both from itself and from another domain, not located on your server at all?
In both the cases you got the same results?
Did you get any bounce messages? If yes, it'd be helpful if you show us their contents.
Does MX and A combinations of DNS records of your domain point to your mail server?
If you don't know, then check

**dig domain.com MX**

It will return something like 
[B]
domain.com             86400   IN      MX      10 mx1.domain.com.[/B]

Then issue dig **mx1.domain.com.** and check if the returned A record points to IP address of your server.

What is the result of **telnet domain.com 25** ? What is the result of **telnet your_server_ip 25** ?

Also, if the logs that you presented are the logs describing an incoming e-mail, then it seems like it was delivered (**delivered to maildir**), so double check if the message is actually not there.

---

