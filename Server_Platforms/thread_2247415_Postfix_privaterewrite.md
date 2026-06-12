---
title: "Postfix private/rewrite"
date: 2014-10-07
forum: Server Platforms
---

### Post by sym3 on 2014-10-07
I've got a postfix/dovecot/mysql server running and everything works but I get this error when I try to start it up. 

```
connect #11 to subsystem private/rewrite: Connection refused
```

Here's my master and main.cf

```
    # See /usr/share/postfix/main.cf.dist for a commented, more complete version
    
    
    # Debian specific:  Specifying a file name will cause the first
    # line of that file to be used as the name.  The Debian default
    # is /etc/mailname.
    #myorigin = /etc/mailname
    
    smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
    biff = no
    
    # appending .domain is the MUA's job.
    append_dot_mydomain = no
    
    # Uncomment the next line to generate "delayed mail" warnings
    #delay_warning_time = 4h
    
    readme_directory = no
    
    # TLS parameters
    #smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
    #smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
    #smtpd_use_tls=yes
    #smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
    #smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
    
    smtpd_tls_cert_file=/etc/ssl/certs/dovecot.pem
    smtpd_tls_key_file=/etc/ssl/private/dovecot.pem
    smtpd_use_tls=yes
    smtpd_tls_auth_only = yes
    
    smtpd_sasl_type = dovecot
    smtpd_sasl_path = private/auth
    smtpd_sasl_auth_enable = yes
    smtpd_recipient_restrictions =
            permit_sasl_authenticated,
            permit_mynetworks,
            reject_unauth_destination
    
    # See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
    # information on enabling SSL in the smtp client.
    
    myhostname = hostname.example.com
    alias_maps = hash:/etc/aliases
    alias_database = hash:/etc/aliases
    myorigin = /etc/mailname
    #mydestination = example.com, hostname.example.com, localhost.example.com
    mydestination = localhost
    relayhost =
    mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
    mailbox_size_limit = 0
    recipient_delimiter = +
    inet_interfaces = all
    
    ## Tells Postfix to use Dovecot's LMTP instead of its own LDA to save emails to the local mailboxes.
    virtual_transport = lmtp:unix:private/dovecot-lmtp
    
    ## Tells Postfix you're using MySQL to store virtual domains, and gives the paths to the database connections.
    virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
    virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
    virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
```

and...

```
    #
    # Postfix master process configuration file.  For details on the format
    # of the file, see the master(5) manual page (command: "man 5 master").
    #
    # Do not forget to execute "postfix reload" after editing this file.
    #
    # ==========================================================================
    # service type  private unpriv  chroot  wakeup  maxproc command + args
    #               (yes)   (yes)   (yes)   (never) (100)
    # ==========================================================================
    smtp      inet  n       -       -       -       -       smtpd
    #smtp      inet  n       -       -       -       1       postscreen
    smtpd     pass  -       -       -       -       -       smtpd
    #dnsblog   unix  -       -       -       -       0       dnsblog
    #tlsproxy  unix  -       -       -       -       0       tlsproxy
    submission inet n       -       -       -       -       smtpd
    #  -o syslog_name=postfix/submission
    #  -o smtpd_tls_security_level=encrypt
    #  -o smtpd_sasl_auth_enable=yes
    #  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
    #  -o milter_macro_daemon_name=ORIGINATING
    smtps     inet  n       -       -       -       -       smtpd
    #  -o syslog_name=postfix/smtps
    #  -o smtpd_tls_wrappermode=yes
    #  -o smtpd_sasl_auth_enable=yes
    #  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
    #  -o milter_macro_daemon_name=ORIGINATINGrelay      unix    -    -    n    -    -    smtp
    flush     unix  n       -       n       1000?   0       flush
    trace      unix    -    -    n    -    0    bounce
    verify      unix    -    -    n    -    1    verify
    proxymap  unix    -    -    n    -    -    proxymap
    anvil      unix    -    -    n    -    1    anvil
    scache      unix    -    -    n    -    1    scache
    discard      unix    -    -    n    -    -    discard
    tlsmgr    unix  -       -       n       1000?   1       tlsmgr
    retry     unix  -       -       n       -       -       error
    proxywrite unix -       -       n       -       1       proxymap
```

I'm not able to send or get mail.

---

