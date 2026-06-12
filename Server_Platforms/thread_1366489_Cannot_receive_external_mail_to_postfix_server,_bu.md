---
title: "Cannot receive external mail to postfix server, but everything else seems to work!!"
date: 2009-12-28
forum: Server Platforms
---

### Post by headhoncho on 2009-12-28
**[FONT=Times]Re: Ubuntu Karmic Postfix Server does not receive mail[/FONT]**
Posted this on a Solved Thread but no responses - so with apologies as I am a noob, have re-posted as a new as I presume solved means no -one adds further there. Any way apols and here goes.

      [FONT=Times]Have wrestled with this for some weeks after upgrade to Karmic which happened at same time as ISP problems. Having had a functioning mailer with postfix/dovecot/mysql/spamassassin/clmav for over a year I mistakenly thought there had been a glitch, and foolishly started to change things without backing up old settings. Now have got back to functioning postfix/dovecot/mysql without the spam/clam filters, except it will not now receive external mail but will send to internal, self and external.Logs do not show any evidence of external connection from say gmail. Can access port 25 using telnet and servername, but not using the no-ip allocated ip address. Any ideas - I have played aroud with eth MX records as well. woudl it be because there is no reverse DNS ? Many thanks.[/FONT]
  ps Here is my main.cf

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = 'servername'.oldfieldhillfarm.co.uk, localhost, localhost.localdomain, localdomain
mydomain = oldfieldhillfarm.co.uk
myhostname = 'servername'.oldfieldhillfarm.co.uk
mynetworks = 127.0.0.0/8, 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = smtp.orangehome.co.uk
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_domains = 
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf, mysql:/etc/postfix/mysql-email2email.cf
virtual_gid_maps = static:5005
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = dovecot
virtual_uid_maps = static:5005

---

### Post by headhoncho on 2010-01-12
It seems that the ISP had had problems with Spammers. I emailed them about opening port 25 incoming and, to be fair, shortly afterwards email has started to flow:D

---

