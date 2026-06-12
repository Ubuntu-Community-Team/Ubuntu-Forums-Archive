---
title: "Postfix problem can't send mails"
date: 2010-09-07
forum: Server Platforms
---

### Post by Somebi on 2010-09-07
From log, when i'm trting to send mail from php:

(updated...)

Sep  7 18:47:57 mydomain postfix/smtpd[23560]: connect from mydomain.lv[vps ip here]
Sep  7 18:47:57 mydomain postfix/smtpd[23560]: NOQUEUE: reject: RCPT from mydomain.lv[vps ip here]: 554 5.7.1 <test@gmail.com>: Relay access denied; from=<from@mydomain.lv> to=<test@gmail.com> proto=ESMTP helo=<localhost>
Sep  7 18:47:57 mydomain postfix/smtpd[23560]: lost connection after RCPT from mydomain.lv[vps ip here]
Sep  7 18:47:57 mydomain postfix/smtpd[23560]: disconnect from mydomain.lv[vps ip here]


my main.cf:

# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual


# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes


#The host name where your MX for virtual domains will point to

myhostname = mail.mydomain.lv  
#Remains blank since we are going to host virtual domains
#mail.mydomain.lv, localhost.localdomain, localhost, mydomain.lv
mydestination = 
#Remains blank unless you are going to use your ISP's SMTP server mail sending out mails. In which case it would be set to the host name of the ISP's SMTP server 
relayhost = 

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mynetworks = all
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

strict_mailbox_ownership = no

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
# modify the existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# then add these
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
home_mailbox = Maildir/
mailbox_command =

I was doing configuration from this manual:
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

It seems something went wrong.

Please help me.

---

### Post by Somebi on 2010-09-07
added to main.cf

mynetworks = 127.0.0.0/8, 192.168.0.0/24, 10.10.0.0/24 

and now mails are going out, but i can't receive mails from google now, that's what log is saying when google is trying to send a message:

Sep  7 19:37:51 mydomain postfix/smtpd[12054]: connect from mail-yw0-f41.google.com[209.85.213.41]
Sep  7 19:37:52 mydomain postfix/smtpd[12054]: warning: connect to 127.0.0.1:10023: Connection refused
Sep  7 19:37:52 mydomain postfix/smtpd[12054]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Sep  7 19:37:53 mydomain postfix/smtpd[12054]: warning: connect to 127.0.0.1:10023: Connection refused
Sep  7 19:37:53 mydomain postfix/smtpd[12054]: warning: problem talking to server 127.0.0.1:10023: Connection refused
Sep  7 19:37:53 mydomain postfix/smtpd[12054]: NOQUEUE: reject: RCPT from mail-yw0-f41.google.com[209.85.213.41]: 451 4.3.5 Server configuration problem; from=<test@gmail.com> to=<info@mydomain.lv> proto=ESMTP helo=<mail-yw0-f41.google.com>
Sep  7 19:37:53 mydomain postfix/smtpd[12054]: disconnect from mail-yw0-f41.google.com[209.85.213.41]


What kind of  "Server configuration problem"?

---

