---
title: "postfix mailserver: @www.mydomain.com works, @mydomain.com doesn't"
date: 2007-04-17
forum: Server Platforms
---

### Post by ouwenbelg on 2007-04-17
Hi all,

I've been thinkering with postfix all night now, so it's time to get some help. :) I want to have a simple mailserver on my ubuntu 6.10 amd64 machine, but I fail to get the email addresses correctly working.

The problem is everything seems to work fine if i send them to [email]auser@www.mydomain.com[/email], but I get a "PERM_FAILURE: SMTP Error (state 9): 554 5.7.1 <info@mydomain.com>: Relay access denied" is I use [email]auser@mydomain.com[/email].

I checked my postfix main.cf config file, and I never refer to [www.mydomain.com](www.mydomain.com) but always to mydomain.com. The domains / users / forwarding stuff in the mysql database courier is using is also without 'www.'.

I followed this tutorial to the letter:
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p1](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy_p1)

Is there something special I have to do to make @mydomain.com instead of @www.mydomain.com addresses work?

Using Ubuntu 6.10 edgy, amd 64 distribution, latest courier + postfix + mysql5 distributions

main.cf:
```

append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost,deugniet,localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
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
virtual_alias_domains = mydomain.com
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

(real domain substituted by mydomain.com)

```
Thanks!

---

### Post by BitHosts on 2007-04-17
Im struggling  little myself I have to admit but:

its not something as simple as MX/DNS entries not pointing at the right place or existing?

---

### Post by ouwenbelg on 2007-04-17
How can I check that? Surfing / pinging to mydomain.com works fine, it just doesn't work for mail.

There is absolutely no logging in /var/log/mail.log when sending mails to @mydomain.com, only when sending mails to @www.mydomain.com.


Is there some setting in postfix that says 'listen to [www.mydomain.com](www.mydomain.com) but ignore mydomain.com'...?

---

### Post by MJN on 2007-04-17
Your **mydestination** directive should have either **mydomain.com** or **$mydomain** (with the latter being set by **mydomain = mydomain.com**).
 
Your **myhostname** also seems wrong (although that could be due to your find-and-replace) in that it should be set to a hostname (fully qualified domain name e.g. mail.mydomain.com) and not just a domain (mydomain.com).
 
Regarding whether your DNS is correctly configured (it probably is given you're getting as far as your mail server), and indeed just in general to help with your config, it would help enormously if you said what your real domain was. Why hide it?
 
Mathew

---

### Post by ouwenbelg on 2007-04-17
Seemed like a sensible thing to do. : )

real domain: [www.hwbot.org](www.hwbot.org)

I'll try this:
```

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
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.hwbot.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = hwbot.org
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
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
virtual_alias_domains = hwbot.org
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps

```

---

### Post by ouwenbelg on 2007-04-17
I tried the settings above, it did not change anything but break the @www.hwbot.org mails. @hwbot.org still does nothing but bounce.

Apr 17 13:00:41 deugniet postfix/trivial-rewrite[25148]: warning: do not list domain hwbot.org in BOTH mydestination and virtual_alias_domains
Apr 17 13:00:41 deugniet postfix/trivial-rewrite[25148]: warning: do not list domain hwbot.org in BOTH mydestination and virtual_mailbox_domains


mysql> select * from domains;
+-----------+
| domain    |
+-----------+
| hwbot.org |
+-----------+
1 row in set (0.00 sec)

If i drop the row I get:

Apr 17 13:02:12 deugniet postfix/local[25181]: fatal: gethostbyname: Success

---

### Post by MJN on 2007-04-17
> **ouwenbelg said:**
> Seemed like a sensible thing to do. : )
 
You're not alone so don't take my dig personally...
 
> real domain: [www.hwbot.org]("http://www.hwbot.org")
 
Okay that's better! Now we can go about fixing it...
 
Your main.cf config needs a little tweaking (the mydestination directive) as whilst it's better it's not quite there - change it to **mydestination = $myhostname, hwbot.org, localhost, localhost.localdomain** just to cover all angles. (that's what I meant by it 'should have mydomain.com' - I was meaning in *addition* to what you add. My fault for not being clear)
 
_However_, that's not the only reason you've got problems - the real problems is your DNS config for hwbot.org (that's why I wanted to know your real domain!).
 
You need to change the MX records for hwbot.org as they currently point to Priorweb's mail servers (mx10.priorweb.be, mx20.priorweb.be and mx30.priorweb.be). You need a single MX record pointing to something like mail.hwbot.org and then add an A record for mail.hwbot.org pointing to your IP address (just like you have got for [www.hwbot.org]("http://www.hwbot.org")). Does that make sense?
 
The reason you're receiving mail okay for [www.hwbot.org]("http://www.hwbot.org") is because other SMTP servers are looking up the MX records for [www.hwbot.org]("http://www.hwbot.org"), not finding any (it doesn't use those for hwbot.org) and instead falling back to looking up the A record which of course you have. Hence it connects to your server and it accepts the mail.
 
Let me know if you need more detail but the bottom line is you need to change your DNS as per the above - I assume you've got some sort of 'control panel' to make these changes (just like you did for [www.hwbot.org]("http://www.hwbot.org"))?
 
Mathew

---

### Post by ouwenbelg on 2007-04-17
Okay, that's a great explenation. Thank you!! :)

I do not have full control over my MX records, the only think I can manage is mapping my domain name to nameservers.

So, I'll ask the hosting company where my colocated server is hosted whether they can add an MX entry for my server, instead of using theirs. I'll let you know whether this worked or not. Thanks!

- Edit -
This seems to be a common mistake:
[http://www.han.com/dns.html](http://www.han.com/dns.html)

---

### Post by MJN on 2007-04-17
You're welcome.
 
Note however, for clarity, you want to *change* your MX records as opposed to *adding* any (unless of course Priorweb are going to act essentially as 'backup' mail servers for your domain but there's little need for them to).
 
Let us know how you get on.
 
Mathew

---

### Post by ouwenbelg on 2007-04-17
Ok, I'll let you know.

---

### Post by ouwenbelg on 2007-04-17
It works! Well almost. :)

Sending mail using telnet works perfect.

Receiving mail using works without errors.

...

But the mechanism stores mails under /home/<user>/Maildir, yet (i think) it looks for new mails in /home/vmail/hwbot.org/<user>/.

I must have either misconfigured my pop3 or smtp server.

---

