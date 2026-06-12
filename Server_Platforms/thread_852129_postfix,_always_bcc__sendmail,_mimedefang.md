---
title: "postfix, always_bcc | sendmail, mimedefang"
date: 2008-07-07
forum: Server Platforms
---

### Post by suresh.amrita on 2008-07-07
Hi,

My very first post to ubuntu forums. If this is not the appropriate place, please let me know.

I was a debian user for around 11 years and switched to ubuntu (8.04 - desktop)  yesterday. :)

I faced a very peculiar problem.

I was using sendmail + mimedefang to automatically archive my outgoing emails to an external account. The same setup did not work in ubuntu. (I just added this much in the mimedefang-filter - exactly same set up which worked in debian etc)

sub filter_begin {
    #bcc to gmail
    add_recipient( 'mygmailaddress' );
:
:

Finding it not working, i changed my MTA to postfix and used the always_bcc option. 

This is the postconf -n output

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
always_bcc = mygmailaddress
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = amritapuri.amrita.edu, 07cpu0013,
localhost.localdomain, localhost
myhostname = 07cpu0013
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = webmail.amrita.ac.in
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/
smtpd_scache
smtpd_use_tls = yes

Could you please suggest how can i go about? I am not particular about sendmail or postfix. My only requirement is that I must be able to archive outbound emails.

Thanks for the great ubuntu team.
with warm regards
suresh

---

### Post by zhangfengsh on 2008-07-08
[https://help.ubuntu.com/community/PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")

---

