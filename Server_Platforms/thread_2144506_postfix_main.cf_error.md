---
title: "postfix main.cf error"
date: 2013-05-12
forum: Server Platforms
---

### Post by CatorAde on 2013-05-12
hi guys,

im following a tutorial to setup a mail server, [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts-p2](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts-p2) all has gone well up until this point.
im supposed to do some configuration to postfix, so i copied the code ([COLOR=#000000][FONT=Courier New]*postconf -e 'myhostname = server1.example.com'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'mydestination = server1.example.com, localhost, localhost.localdomain'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'mynetworks = 127.0.0.0/8'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_alias_domains ='*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_mailbox_base = /home/vmail'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_uid_maps = static:5000'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_gid_maps = static:5000'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'smtpd_sasl_auth_enable = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'broken_sasl_auth_clients = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'smtpd_sasl_authenticated_header = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'smtpd_use_tls = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'smtpd_tls_cert_file = /etc/postfix/smtpd.cert'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'smtpd_tls_key_file = /etc/postfix/smtpd.key'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_maildir_extended = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_mailbox_limit_override = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_maildir_limit_message = "The user you are trying to reach is over quota."'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*postconf -e 'virtual_overquota_bounce = yes'*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New][I]postconf -e 'proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps')

but im getting the error

postconf: fatal: open /etc/postfix/main.cf for reading: No such file or directory

can anyone help please 

many thanks
Ade[/I][/FONT][/COLOR]

---

### Post by CatorAde on 2013-05-12
n/m sorted :)
can't seem to find the resolved button tho?

---

