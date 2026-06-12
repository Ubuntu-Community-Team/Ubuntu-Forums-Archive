---
title: "Problem with forwarding on Postfix"
date: 2010-11-03
forum: Server Platforms
---

### Post by mickey78 on 2010-11-03
Hello.

I followed this tut (Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 10.04) on Howtoforge) and my server is working well for the most part. I have similar setup on other servers and they work well.

In the specific case I'm having a forwarding problem, the email doesnt go to the forward destination address, it is being refused by the server.

Here is pertinent infos.

cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mailserver.rtccable.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = **destinations **
relayhost = **ip of relay**
mynetworks = **ip's of networks**
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
#content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 20480000


In the log, I get an error saying:
Nov 2 10:22:20 mailserver postfix/virtual[15505]: 48FFBB03AA7: to=<test@rtccable.com>, relay=virtual, delay=0.03, delays=0.01/0/0/0.02, dsn=5.1.1, status=bounced (unknown user: "test@rtccable.com")

I have an entry in my mysql database for test@rtccable and it should be redirected to another address.. I also have an entry in the domains table for rtccable.com

Anyone have any idea why?

---

### Post by trundlenut on 2010-11-03
You seem to be having a similar problem to me - see [here]("http://ubuntuforums.org/showthread.php?t=1611265").

Can't help you though.

---

