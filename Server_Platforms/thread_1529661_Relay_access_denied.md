---
title: "Relay access denied"
date: 2010-07-12
forum: Server Platforms
---

### Post by VRage on 2010-07-12
Hi!

Posted this before under general help, I'm sorry for the repetition... only noticed I had it placed in the wrong category.

I've just finished setting up postfix with courier and mysql(for users and domains) on my server and all seemed to be fine and dandy until I tried to send an email from another machine using my email client. The email seems to be sent but never really arrives, also if I send emails locally on the server using roundcube all goes well and the email arrives.

In postfix mail.log I have the following:

postfix/smtpd[13491]: NOQUEUE: reject: RCPT from a81-84-xx-**.***.*******.**[81.84.****.**]: 554 5.7.1 <*********@*****.com>: Relay access denied; from=<******@*********.com> to=<*********@****.com> proto=ESMTP helo=<********>

What do I need to change to make this sort of relay ( sending emails from other machines ) available?

Thanks in advance

--------------
postfix main.cf contents:

> 
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

myhostname = ve.wncmvr67.vesrv.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mynetworks = 127.0.0.0/8
# relay_domains = $mydestination
relayhost =
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
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, permit_mynetworks
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_$
content_filter = smtp-amavis:[127.0.0.1]:10024


---

### Post by cdenley on 2010-07-12
[http://www.postfix.org/postconf.5.html#mynetworks](http://www.postfix.org/postconf.5.html#mynetworks)

---

### Post by VRage on 2010-07-12
thanks for the quick reply!
I had been to that page a couple of days back and changed the mynetworks line to:

mynetworks = 127.0.0.0/8, 192.168.0.0/28

Still gave the same relay access denied error though =(

---

### Post by cdenley on 2010-07-12
> **VRage said:**
> thanks for the quick reply!
I had been to that page a couple of days back and changed the mynetworks line to:

mynetworks = 127.0.0.0/8, 192.168.0.0/28

Still gave the same relay access denied error though =(

Well the error you posted indicates you are attempting to relay from 81.84.****.**, not from any IP on 192.168.0.0/28.

---

### Post by MidSpeck on 2010-07-12
Just as a word of caution, be careful you don't accidentally set yourself up as an open relay -- or people will find it and send spam through your server.

---

### Post by VRage on 2010-07-12
That is correct, I only copied the example, didn't even try it with the  81.84.***.*** ip as it's not fixed and I would very much like to be able to send emails from other machines.

I thought from reading a post in another forum that having it set just to accept 127.0.0.0/8 and authentication on would suffice, is this correct?

And thank you MidSpeck, I actually am trying not to have that problem, was made aware of it a few months back when a server of someone I know pretty much was spamming himself.

---

