---
title: "POSTFIX smtpd relay problem"
date: 2011-02-02
forum: Server Platforms
---

### Post by cromestant on 2011-02-02
Hello, 
I have setup postfix with courier to use mysql for virtual domains.
I have maildirs working on a single user, adding the maildirs to /home/vmail under the format user@domain/

Now all is working except for the relaying of outbound mails.
it always fails with :

[PHP]Feb 2 10:07:40 li197-251 postfix/smtpd[6719]: connect from localhost[127.0.0.1] Feb 2 10:07:40 li197-251 postfix/smtpd[6719]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 554 5.7.1 <email@gmail.com>: Relay access denied; from=<email@mydomain.com> to=<email@gmail.com> proto=ESMTP helo=<squirrel.mydomain.com> Feb 2 10:07:40 li197-251 postfix/smtpd[6719]: lost connection after RCPT from localhost[127.0.0.1] Feb 2 10:07:40 li197-251 postfix/smtpd[6719]: disconnect from localhost[127.0.0.1] Feb 2 10:07:41 li197-251 postfix/smtpd[6707]: disconnect from mail-ww0-f46.google.com[74.125.82.46][/PHP]


Now I can send emails to domains managed by the system but not to anything outside
postconf -n :
[PHP]alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = 
myhostname = mail.domain.com
mynetworks = all
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_unauth_pipelining,				 permit_mynetworks,			 permit_sasl_authenticated,				 reject_non_fqdn_recipient,				 reject_unknown_recipient_domain,				 reject_unauth_destination,				 permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail/
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_limit = 51200000
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid = 5000
virtual_transport = virtual
virtual_uid_maps = static:5000
[/PHP]


thank you in advance, can post more configs if necessary

---

### Post by drkoaxaco on 2012-04-11
Hi,
 
Just curious if you had any success in resolving **relay access denied** problem. I am trying to configure essentially the exact same set-up and am having the exact same issue that you have described. I would appreciate any insight that anyone can provide. I've been at this (on & off) for almost 10 days and still no success. Thank you.

---

### Post by viperce on 2012-04-11
[COLOR=#000000][COLOR=#0000BB]relayhost [/COLOR][COLOR=#007700]= isp smtp details here?
[/COLOR][/COLOR]

---

### Post by cromestant on 2012-04-11
drkoaxaco, I did fix it, unfortunately I no longer work at that company and as such have lost access to the server.

IIRC, it was an issue with the authentication, I had to go through some other authentication mechanism.

I{ll check into my backups to see if I have the conf backups.

---

### Post by cromestant on 2012-04-11
related thread. 
maybe you {ve not tried some of these things.

[http://ubuntuforums.org/showthread.php?t=1678960](http://ubuntuforums.org/showthread.php?t=1678960)

---

### Post by drkoaxaco on 2012-04-11
I should have mentioned that I can send email to an external email address (I presume via the relay host) via sendmail... I just can't send or receive email via the postfix mail server that I am attempting to configure.
 
relayhost = [smtp.comcast.net]:587 and set-up is per this link found on the Comcast website: [http://forums.comcast.com/t5/E-Mail-and-Xfinity-Connect-Help/sending-email-from-linux-server/td-p/1226495](http://forums.comcast.com/t5/E-Mail-and-Xfinity-Connect-Help/sending-email-from-linux-server/td-p/1226495)
 
I'm thinking that I do have some sort of authentication problem but, at this point, the only lead that I can find in my log files is this from my mail.log:
 
*postfix/smtpd[15819]: connect from localhost[::1]*

*postfix/smtpd[15819]: NOQUEUE: reject: RCPT from localhost[::1]: 554 5.7.1 <xxxx@gmail.com>: Relay access denied; from=<myvirtualuser@myvirtualdomain.com> to=<xxxx@gmail.com> proto=ESMTP helo=*[*www.myvirtualdomain.com*]("http://www.myvirtualdomain.com")

*postfix/smtpd[15819]: lost connection after RCPT from localhost[::1]*

*postfix/smtpd[15819]: disconnect from localhost[::1]*
 
Any assistance or direction would be greatly appreciated. Thank you.

---

