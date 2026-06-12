---
title: "Postfix error"
date: 2008-08-09
forum: Server Platforms
---

### Post by RalphG1000 on 2008-08-09
Hi everyone,

I have installed postfix and Squirrelmail onto the latest Ubuntu server release.

I followed this tutorial:
[http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/)

I can receive email fine but cannot send email to ANY external domains from either Telnet (from server lan range of 10.0.0.*) or Squirrelmail!

Squirrelmail gives this response after pressing the send button...

Message not sent. Server replied: 
Requested action not taken: mailbox unavailable
550 5.1.1 <TheUser@hotmail.com>: Recipient address rejected: hotmail.com

Can anyone shed any light here please?

Here is my conf file (appologies for the long post)


# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = TheDomain.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.0.0.0/20
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
default_transport = error
relay_transport = error
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key


Thanks in advance... Ralph

---

### Post by ronnieredd on 2008-08-09
A couple things that may help.
[LIST]
[*]First and foremost - check your ip address against any and all rbls' (Realtime Blackhole Lists) to make sure your ip address isn't listed as a spam source

[*]send a message to:```
ralphg AT cruzit d0t com
``` It's an alias I just set up for testing. It will be deleted shortly. If it does get rejected from this end, there should be a be description of why it was rejected. If it goes through I'll answer back. [*]When using hotmail - hotmail is owned by m$ and run on Exchange servers which quite often report errors pointing the problem in the wrong direction.
[*]sign up to the postfix mailing list - it's monitored by the maintainer and a huge list of postfix experts.
[/LIST]
Here's my main.cf for comparison:
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
Edit the lines that are specific to your needs.
==/etc/postfix/main.cf==

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Linux)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# progressive timeouts for error prone connections
smtpd_error_sleep_time = 5s
smtpd_soft_error_limit = 9
smtpd_hard_error_limit = 21
# Change this to a higher number once moved to
# a larger production - probably 50-75 - to allow 
# an "all users" message: 
#default_destination_recipient_limit = 75
default_destination_recipient_limit = 25
maximal_queue_lifetime = 4d
mailbox_size_limit = 309600000
message_size_limit = 50000000
readme_directory = /usr/share/doc/postfix
html_directory = /usr/share/doc/postfix/html
mydestination = put_all_your_domains_here_seperated_by_spaces.com localhost.yourdomain.com, localhost
recipient_delimiter = +
myorigin = /etc/mailname
mynetworks = 127.0.0.0/8 your_ip_address_networks_seperated_by_spaces 192.168.104.0/24

recipient_delimiter = +
disable_vrfy_command = yes
smtpd_delay_reject = yes
header_checks = regexp:/etc/postfix/header_checks
# Restrictions for antispam RR010907
smtpd_helo_required = yes
smtpd_recipient_restrictions =
	reject_non_fqdn_recipient
	reject_non_fqdn_sender
	reject_unknown_sender_domain
	reject_unknown_recipient_domain
	permit_mynetworks
	permit_sasl_authenticated
	reject_unauth_destination
	check_policy_service inet:127.0.0.1:60000
	check_recipient_access hash:/etc/postfix/roleaccount_exceptions
	reject_multi_recipient_bounce
	reject_non_fqdn_hostname
	reject_invalid_hostname
	reject_unknown_hostname
	check_helo_access pcre:/etc/postfix/helo_checks
	reject_rbl_client nomail.rhsbl.sorbs.net
	reject_rbl_client dul.dnsbl.sorbs.net
	reject_rbl_client zen.spamhaus.org
	reject_rbl_client bl.spamcop.net
	reject_rbl_client bl.spamcannibal.org
	reject_rbl_client dnsbl.njabl.org
	reject_rbl_client cbl.abuseat.org
	reject_rbl_client dnsbl.sorbs.net
	permit
==

If you want to check mail directly from the command line on the server:
```
 mail -s "check mail server" yourgmailaddress@gmail.com
```
The -s is subject
Once you can send to gmail check the drop down for "show original" to look at the headers.

Lastly I highly recommend buying the book of postfix: 
[http://www.amazon.com/exec/obidos/ASIN/1593270011/postfixbook-20/ref=nosim/104-7493587-4700709]("http://www.amazon.com/exec/obidos/ASIN/1593270011/postfixbook-20/ref=nosim/104-7493587-4700709")

Hope some of this may help.

---

### Post by RalphG1000 on 2008-08-09
Thank you for that ronnieredd,

After performing those steps this is what my mail.log states:


Aug  9 17:50:43 MTA postfix/smtpd[5117]: disconnect from localhost[127.0.0.1]
Aug  9 17:50:49 MTA postfix/smtpd[5117]: connect from localhost[127.0.0.1]
Aug  9 17:50:49 MTA postfix/smtpd[5117]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 5.1.1 <ralphg@cruzit.com>: Recipient address rejected: cruzit.com; from=<user@virtual.test> to=<ralphg@cruzit.com> proto=ESMTP helo=<10.0.0.18>
Aug  9 17:50:49 MTA postfix/smtpd[5117]: lost connection after RCPT from localhost[127.0.0.1]
Aug  9 17:50:49 MTA postfix/smtpd[5117]: disconnect from localhost[127.0.0.1]


The message in Squirrelmail still reads as it did also.

I can't see anthing in the main.cf but I am faily blind to all the meanings so it't hard to diagnose.

---

