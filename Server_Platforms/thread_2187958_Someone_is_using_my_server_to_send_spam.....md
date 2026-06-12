---
title: "Someone is using my server to send spam...."
date: 2013-11-14
forum: Server Platforms
---

### Post by cje1232 on 2013-11-14
I appreciate any help on this issue.   Some one are using my postfix to send spam.  I suspect here is a cronjob I'm missing to locate.       My ISP provider has blocked outgoing mail.   The below sessions are running every minute.        from my auth.log

```

Nov 15 00:50:01 www CRON[2888]: pam_unix(cron:session): session opened for user cje by (uid=0)
Nov 15 00:50:01 www CRON[2889]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 15 00:50:01 www CRON[2888]: pam_unix(cron:session): session closed for user cje
Nov 15 00:50:02 www CRON[2889]: pam_unix(cron:session): session closed for user root
```

From my syslog  ```

Nov 15 00:50:01 www CRON[2891]: (root) CMD (cd /var/www2/oldsite/site/periodic; /usr/bin/php -q cron.php)
Nov 15 00:50:01 www CRON[2892]: (cje) CMD (/home/cje/ /.m/update >/dev/null 2>&1)
Nov 15 00:50:02 www sSMTP[2893]: RCPT TO: (504 5.5.2 : Sender address rejected: need fully-qualified address)
Nov 15 00:50:02 www CRON[2889]: (root) MAIL (mailed 1010 bytes of output but got status 0x0001#012)
```

I've deleted the www2/oldsite/site which was a testing site   [email]info@olddomain.com[/email] is an email which has been found in a plugin under oldsite      This is my main.cf 
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname  smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu) biff = no  # appending .domain is the MUA's job. append_dot_mydomain = no  # Uncomment the next line to generate "delayed mail" warnings #delay_warning_time = 4h  # TLS parameters smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key smtpd_use_tls = yes smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache  # See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for # information on enabling SSL in the smtp client.  myhostname = server-my alias_maps = hash:/etc/aliases alias_database = hash:/etc/aliases myorigin = /etc/mailname mydestination = my.com, server-my, localhost.localdomain, localhost relayhost =  mynetworks = 127.0.0.0/8 mailbox_size_limit = 0 recipient_delimiter = + inet_interfaces = all mailbox_command = procmail -a "$EXTENSION" inet_protocols = all smtpd_sasl_local_domain =  smtpd_sasl_auth_enable = yes smtpd_sasl_security_options = noanonymous broken_sasl_auth_clients = yes # smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,reject_invalid_hostname,reject_non_fqdn_sender, # reject_non_fqdn_recipient,reject_unknown_sender_domain,reject_unknown_recipient_domain,reject_unauth_pipelining,reject_rbl_client, # reject_bl.spamcop.net,permit smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,reject_invalid_hostname,reject_non_fqdn_sender, reject_non_fqdn_recipient,reject_unknown_sender_domain,reject_unknown_recipient_domain,reject_unauth_pipelining,reject_rbl_client, reject_bl.spamcop.net,reject smtpd_tls_auth_only = no smtp_use_tls = yes smtp_tls_note_starttls_offer = yes smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem smtpd_tls_loglevel = 1 smtpd_tls_received_header = yes smtpd_tls_session_cache_timeout = 3600s tls_random_source = dev:/dev/urandom 
```   Any suggestions how I can stop the repeating script/cronjob?  Thanks for any help.

---

### Post by SeijiSensei on 2013-11-14
Read this to start:  [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

It's unlikely that it has anything to do with cron.  You need to lock down Postfix so it only accepts mail for particular domains and rejects everything else.

You can check the integrity of the server here: [http://mxtoolbox.com/diagnostic.aspx](http://mxtoolbox.com/diagnostic.aspx)

---

### Post by cje1232 on 2013-11-14
Thanks for your suggestions >  You can check the integrity of the server here: [http://mxtoolbox.com/diagnostic.aspx](http://mxtoolbox.com/diagnostic.aspx)  returned this; >  Connecting to 12.345.678.90 11/14/2013 6:43:23 PM Connection attempt #1 - Unable to connect after 15 seconds. [15.02 sec]  MXTB-PWS3v2 15019ms   >  Read this to start: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)  I'll check this out and see what I find.

---

### Post by CharlesA on 2013-11-14
While you are troubleshooting this problem, take the server offline, if you haven't already.

Try reposting your main.cf file... all the line breaks are gone, which makes it hard to read.

Also, check mail.err and mail.log to see what email address it was trying to send that had no fqdn.

---

