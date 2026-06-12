---
title: "postfix imap issues"
date: 2008-11-22
forum: Server Platforms
---

### Post by genesimmons4201 on 2008-11-22
I started over and followed the perfect virtual mail server howto and have the following issue

Nov 22 20:08:54 www postfix/master[11145]: daemon started -- version 2.5.1, configuration /etc/postfix
Nov 22 20:09:00 www imapd: Connection, ip=[::ffff:76.70.7.182]
Nov 22 20:09:00 www imapd: chdir xxxxxxxxxxx.com/sales/: No such file or directory
Nov 22 20:09:51 www imapd: Connection, ip=[::ffff:76.70.7.182]
Nov 22 20:09:51 www imapd: chdir xxxxxxxxxxxx.com/sales/: No such file or directory


main.cf

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


# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = [www.xxxxxxxxxxxx.com](www.xxxxxxxxxxxx.com)
alias_maps = hash:/etc/postfix/aliases
mydestination = [www.xxxxxxxxxxxxx.com](www.xxxxxxxxxxxxx.com), localhost, localhost.localdomain
#relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 51200000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
alias_database = hash:/etc/postfix/aliases
virtual_transport = virtual

Chris

---

### Post by MJN on 2008-11-24
Hi Chris,
 
Postfix has nothing to do with IMAP hence you are probably looking in the wrong place. You need to be looking at the config of your IMAP server.
 
(Incidentally, drop the '[www.']("http://www.'") prefix from your domain in mydestination - it is wrong unless you want receive mail for <user>@www.domain.com)
 
Mathew

---

### Post by HermanAB on 2008-11-24
Install Dovecot.

Postfix is only one Lego block of a complete mail system.  To have the whole kit and kaboodle, you also need Dovecot, Apache, Squirrel, Spam Assassin, ClamAV, Amavisd-new, Razor, Pyzor and some black lists.  Getting that lot to work will take one to four weeks depending on your level of expertise.

Alternatively, you can just take the easy way out and install Citadel.  You can have Citadel up and running in about 20 minutes and it does everything.  You can even download a pre-installed Citadel VM from VMware, but that will take longer to download than to run the Citadel Easy Install script.

Cheers,

Herman

---

### Post by Dr Small on 2008-11-24
> **HermanAB said:**
> Install Dovecot.

Postfix is only one Lego block of a complete mail system.  To have the whole kit and kaboodle, you also need Dovecot, Apache, Squirrel, Spam Assassin, ClamAV, Amavisd-new, Razor, Pyzor and some black lists.  Getting that lot to work will take one to four weeks depending on your level of expertise.

Alternatively, you can just take the easy way out and install Citadel.  You can have Citadel up and running in about 20 minutes and it does everything.  You can even download a pre-installed Citadel VM from VMware, but that will take longer to download than to run the Citadel Easy Install script.

Cheers,

Herman
If I thought that you were a Citadel advertiser, I'd call that post FUD advertising :p

---

### Post by CrucifiedEgo on 2008-11-24
Uh, guys?  look at the log.  He clearly has courier installed based on the 'imapd:' syslog prefix. 

Moving on, it looks like the directory hasn't been created yet.  Postfix will do this for you if you send a quick message to it to create the maildir.  It's easy enough to do via telnet.  Here's an example (i've prefaced the server responses with ">>" to clarify what's happening):
```
james@poseidon [/home/vmail] $ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
>>220 poseidon.mykauaitech.com ESMTP Postfix (Ubuntu)
HELO poseidon.mykauaitech.com
>>250 poseidon.mykauaitech.com
MAIL FROM: james@jamesandportia.com
>>250 2.1.0 Ok
RCPT TO: web@jamesandportia.com
>>250 2.1.5 Ok
DATA
>>354 End data with <CR><LF>.<CR><LF>
test
.
>>250 2.0.0 Ok: queued as CA2E4C0747
quit
>>221 2.0.0 Bye
Connection closed by foreign host.

```just replace the hostname in the HELO command and the to: and FROM: addresses with what's appropriate for your situation.  Then try to login via IMAP.  if the directory still doesn't exist, then courier and postfix are pointing to different directories -- fix one, and go from there.

---

