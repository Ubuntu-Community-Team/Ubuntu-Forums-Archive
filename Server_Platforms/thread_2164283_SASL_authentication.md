---
title: "SASL authentication"
date: 2013-07-31
forum: Server Platforms
---

### Post by m_gustafsson on 2013-07-31
I am trying to set up a mail server on my Ubuntu 12.04 server and I have been following this nice guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/).
As a webmail client I am using RoundCube, but I cannot get it to send email.

I use a relay server to send my emails and it requires SMTP authentication and I have thus added the following into my /etc/postfix/master.cf file:
```
smtps     inet  n       -       n       -       -       smtpd  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous

```

If I try to send an email from RoundCube to "mail@gmail.com" RoundCube tells me that:
```
[COLOR=#000000][FONT=Lucida Grande]SMTP-error (554): Cannot add recipient address "mail@gmail.com"[/FONT][/COLOR]
```

The mail log shows:
```
postfix/smtpd[29571]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0.0.1]: 554 5.7.1 <localhost.localdomain[127.0.0.1]>: Client host rejected: Access denied; from=<m@mailserver.homeip.net> to=<mail@gmail.som> proto=ESMTP helo=<mailserver.homeip.net>
```

If I remove the line "-o smtpd_client_restrictions=permit_sasl_authenticated,reject" from my master.cf file I can send the email without problem from RoundCube, and I thus believe that I cannot get RoundCube to pass the sasl authentication.

I have tried to test sasl with testsalsauthd and that works:
```
$ testsaslauthd -um@mailserver.homeip.net -p password -f/var/spool/postfix/var/run/saslauthd/mux -s smtp
0: OK "Success."
```

With telnet it fails though.

My postfix configuration looks likefollows:

```
$ postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
inet_protocols = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
mynetworks = 192.168.0.0/24 127.0.0.0/8
mynetworks_style = host
myorigin = $mydomain
readme_directory = no
recipient_delimiter = +
relayhost = mailout.telia.com
smtp_helo_timeout = 60s
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/relay_passwd
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000

```

I have been trying for quite some days now to find a solution to this, but...
So, help would be much appreciated.

/M

---

### Post by m_gustafsson on 2013-07-31
I believe that I found the solution now.
I had to modify[I] /etc/roundcube/main.inc.php and make it contain:
[/I]```
[I]$rcmail_config['smtp_server']= 'ssl://localhost';
[/I]*$rcmail_config['smtp_port']= 465;*
*$rcmail_config['smtp_user']= '%u';*
*$rcmail_config['smtp_pass']= '%p';”*
```

Then I also had to make sure that I ran chrooted, i.e. in /etc/postfix/master.cf my smtps line now looks like this:
```
smtps    inet  n       -       -       -       -       smtpd
```

And after that:
```
# service postfix reload
```

/M

---

