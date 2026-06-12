---
title: "Postfix per user smtpd restrictions"
date: 2010-02-15
forum: Server Platforms
---

### Post by damone333 on 2010-02-15
[FONT=Book Antiqua][SIZE=2][FONT=Arial Black]Been trying for some time to get Postfix to not allow some internal users to send email externally. I have found some good resources online but none of them work. The user is still able to send email internally and externally.

I used the following web pages to assist me...
[http://www.postfix.org/RESTRICTION_CLASS_README.html](http://www.postfix.org/RESTRICTION_CLASS_README.html)
[http://marc.info/?l=postfix-users&m=97308745518658&w=2](http://marc.info/?l=postfix-users&m=97308745518658&w=2)[/FONT]


[FONT=Arial Black]Below is my main.cf[/FONT]
[/SIZE][/FONT]    [FONT=Book Antiqua][SIZE=2]# See /usr/share/postfix/main.cf.dist for a commented, more complete version[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]# Debian specific:  Specifying a file name will cause the first[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# line of that file to be used as the name.  The Debian default[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# is /etc/mailname.[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#myorigin = /etc/mailname[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]smtpd_banner = $myhostname ESMTP $mail_name[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]biff = no[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]# appending .domain is the MUA's job.[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]append_dot_mydomain = no[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]# Uncomment the next line to generate "delayed mail" warnings[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#delay_warning_time = 4h[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]readme_directory = /usr/share/doc/postfix[/SIZE][/FONT]
  
  
  [FONT=Book Antiqua][SIZE=2]# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# information on enabling SSL in the smtp client.[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]myhostname = EMAIL2.EXAMPLE.com[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]alias_maps = hash:/etc/aliases[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]alias_database = hash:/etc/aliases[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]myorigin = /etc/mailname[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# Identifies what mail the host will deliver locally.[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]mydestination = EXAMPLE.com, EMAIL2.EXAMPLE.com, localhost.EXAMPLE.com[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#relayhost =[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]mynetworks = 192.168.1.0/24, 127.0.0.0/8,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]mailbox_size_limit = 0[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]recipient_delimiter = +[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]inet_interfaces = all[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]html_directory = /usr/share/doc/postfix/html[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]mydomain = EXAMPLE.com[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# Rewriting Addresses in Outgoing Mail[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]masquerade_domains = EXAMPLE.com[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# MailScanner Header Cheecker[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]header_checks = regexp:/etc/postfix/header_checks[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# Enables maildir style email retension[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]home_mailbox = Maildir/[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]### Reject bogus email[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_delay_reject = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_helo_required = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] #smtpd_helo_restrictions =[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#        permit_mynetworks,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]##      reject_invalid_hostname,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]##      reject_non_fqdn_hostname,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#        permit[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_data_restrictions =[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        reject_unauth_pipelining,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        permit[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#smtpd_sender_restrictions =[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#       permit_mynetworks,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#       reject_non_fqdn_sender,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#       reject_unknown_sender_domain,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#       permit[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_recipient_restrictions =[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        permit_sasl_authenticated,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        permit_mynetworks,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        reject_unknown_recipient_domain,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        reject_unauth_destination,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#        permit[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]###TEST AREA###[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_sender_restrictions =[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]        hash:/etc/postfix/restricted_senders,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#        permit_mynetworks,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#        reject,[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_restrictions_classes = local_only[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]local_only = check_sender_access hash:/etc/postfix/local_domains, reject[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]###END###[/SIZE][/FONT]
  
  [FONT=Book Antiqua][SIZE=2]### TLS - SASL ###[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_sasl_local_domain = EXAMPLE.com[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_sasl_auth_enable = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]broken_sasl_auth_clients = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_auth_only = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_use_tls = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtp_tls_note_starttls_offer = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_loglevel = 1[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_received_header = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_session_cache_timeout = 3600s[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]tls_random_source = dev:/dev/urandom[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_received_header = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_key_file = /etc/ssl/private/smtpd.key[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtp_tls_note_starttls_offer = yes[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]#smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]



[FONT=Arial Black]This is the local_domains file:[/FONT]
[/SIZE][/FONT]    [FONT=Book Antiqua][SIZE=2]user@EMAIL2:/etc/postfix$ cat local_domains[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# This table defines what destinations are local[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]# FORMAT = this.domain     OK[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]EXAMPLE.com     OK[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]EMAIL2.EXAMPLE      OK[/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=2]
[/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=2]
[/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=2][FONT=Arial Black]This is the restricted senders file[/FONT][/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=2]user@EMAIL2:/etc/postfix$ cat restricted_senders
# Users restricted to local only.
# FORMAT IS = foo@domain      local_only
brose@EXAMPLE local_only
[EMAIL="brose@EMAIL2.EXAMPL"]brose@EMAIL2.EXAMPL[/EMAIL]E Local_only


[FONT=Arial Black]Any help will be greatly appreciated.[/FONT]


[/SIZE][/FONT]

---

### Post by damone333 on 2010-02-16
If helped will be willing to put config and user guide here.

---

### Post by damone333 on 2010-02-16
Solved my own problem just needed this in the main.cf...

smtpd_recipient_restrictions = check_sender_access hash:/etc/postfix/restricted_senders, reject_unauth_destination
smtpd_restriction_classes = local_only
local_only = check_recipient_access hash:/etc/postfix/local_domains, reject

Then postmap your files again and restart postfix.

---

### Post by damone333 on 2010-02-16
Looks like this code doesn't work it denies everybody. looking into a fix....:confused:

---

