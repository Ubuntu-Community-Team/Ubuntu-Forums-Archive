---
title: "Problem starting Postfix: mysql_alias.cf, line 1: missing '='"
date: 2009-09-14
forum: Server Platforms
---

### Post by JMadrid on 2009-09-14
Hi, I am just dealing with my first Postfix installation.
  After following a few tutorials, I’m still not able to start the Postfix server. I looked for solutions in many forums, but I cannot find this problem. Tailing the log files there is an error coming over and over:
```

    Sep 14 11:25:30 hostname postfix/cleanup[30095]: fatal: /etc/postfix/mysql_alias.cf, line 1: missing '=' after attribute name: "??h"
    Sep 14 11:25:31 hostname postfix/master[30043]: warning: process /usr/lib/postfix/cleanup pid 30095 exit status 1

Sep 14 11:25:31 hostname postfix/master[30043]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
  

```    This is my main.cf:
```
    # See /usr/share/postfix/main.cf.dist for a commented, more complete version
   
   
  # Debian specific:  Specifying a file name will cause the first
  # line of that file to be used as the name.  The Debian default
  # is /etc/mailname.
  #myorigin = /etc/mailname
  myorigin= mydomain.com
   
  smtpd_banner = $myhostname ESMTP $mail_name 
  biff = no
   
  # appending .domain is the MUA's job.
  append_dot_mydomain = no
   
  # Uncomment the next line to generate "delayed mail" warnings
  delay_warning_time = 4h
  unknown_local_recipient_reject_code = 450 
  maximal_queue_lifetime = 7d 
  minimal_backoff_time = 1000s 
  maximal_backoff_time = 8000s
  smtp_helo_timeout = 60s 
  smtpd_recipient_limit = 16
  smtpd_soft_error_limit = 3 
  smtpd_hard_error_limit = 12
   
  readme_directory = no
   
  # TLS parameters
  #smtp_use_tls = no 
  smtp_tls_security_level = may 
  #smtpd_use_tls=yes 
  smtpd_tls_security_level = may 
  #smtpd_tls_auth_only = no 
  smtp_tls_note_starttls_offer = yes 
  smtpd_tls_loglevel = 1 
  smtpd_tls_received_header = yes 
  smtpd_tls_session_cache_timeout = 3600s 
  tls_random_source = dev:/dev/urandom 
  smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem 
  smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key 
  #smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache 
  #smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
   
   
  smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit 
  smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
  smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
  smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
   
  smtpd_helo_required = yes 
  # waste spammers time before rejecting them
  smtpd_delay_reject = yes 
  disable_vrfy_command = yes
   
   
  # See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
  # information on enabling SSL in the smtp client.
   
  # content_filter = amavis:[127.0.0.1]:10024
   
  myhostname = smtp.mydomain.com
  mydomain = mydomain.com
  alias_maps = hash:/etc/postfix/aliases 
  alias_database = hash:/etc/postfix/aliases 
  myorigin = mydomain.com
  mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
  relayhost = 
  mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
  mynetworks_style = host
  mailbox_size_limit = 0
  recipient_delimiter = +
  inet_interfaces = all
  virtual_mailbox_base = /var/spool/mail/virtual 
  virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
  virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf 
  virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf 
  virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
  virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
  
```Running Ubuntu 8.04 in VPS.

Does anybody have any idea what could it be?
Thanks

---

### Post by t3r0 on 2009-09-14
Please post the contents of /etc/postfix/mysql_alias.cf

The error seems to be in that file.

- Tero

---

### Post by JMadrid on 2009-09-14
Oh yeah, sorry. Here it is:

```

hosts=127.0.0.1
user=(user)
password=(password)
dbname=maildb 
table=aliases 
select_field=destination 
where_field=mail 
additional_conditions = and enabled = 1

```I just omitted (user) and (password)

---

### Post by JMadrid on 2009-09-14
Ok, I see this is not easy...:(

Does anybody could tell me any place where I could ask or get some more information?

Thank you

---

### Post by t3r0 on 2009-09-16
hmm.. the file syntax seems to be ok.. So this is just a guess: did you copy&paste the contents to that file from your browser? if so, try to clear the file and type that same content back to that file by hand. 

Sometimes when you copy&paste content from some web pages the actual characters are not the same as they seem. Like in this case the "=" could actually be some other than ascii code 61. 

- Tero

> **JMadrid said:**
> Ok, I see this is not easy...:(

Does anybody could tell me any place where I could ask or get some more information?

Thank you

---

### Post by JMadrid on 2009-09-16
Yes, you are right!

I made a mistake saving mysql_alias.cf file in a UTF-16 encoding (just because I edited the file in Windows). I didn't know Postfix configuration files were plain ASCII text.

Thank you very much!

JC

---

### Post by noway2 on 2009-09-16
Just as a point of reference for anyone in the future, the ' attribute name: "??h" ' was a big clue.  When you see something like the "??h" it is a good indication that you have something messed up in one of the .CF files for you mapping.  I have wasted many hours trying to track those bugs down!

---

