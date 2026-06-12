---
title: "SASL / Outgoing Mail Authentication Not Working"
date: 2007-04-15
forum: Server Platforms
---

### Post by BitHosts on 2007-04-15
Hey all - Ive had a few issues setting up a mail server.

I can now successfully send and receive email, only problem is outbound email authentication doesnt work.

I have followed: [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

and as i saw it i thought this would mean that SASL etc would be configured.

If i turn authentication off in my email client for SMTP it works perfectly, and receiving emails isnt an issue.  However if i turn it on all I get is that my usernam/password has been rejected.  Naturally I think this isnt secure, and so want it sorted as a result at the moment SMTP is blocked at the firewall level.

If you can help me that would be awesome, thankyou very much!  If your willing to help me but need more information please ask!

Thanks!!!

Felix

---

### Post by bmathis on 2007-04-15
do you have the proper settings in your main.cf file and is sasl started? try doing a sudo /etc/init.d/saslauthd start and test it out again.

---

### Post by BitHosts on 2007-04-16
Heya, thanks for the reply.

I checked the daemon and it claims to already br running.

Here is my Main.cf:

```

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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.bithosts.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.bithosts.co.uk, localhost, localhost.bithosts.co.uk
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mys$
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reje$
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_lim$
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over their$
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps$virt$
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
smtpd_sasl_security_options = noanonymous
smtpd_tls_auth_only = no
smtp_use_tls = yes
```

---

### Post by bmathis on 2007-04-16
Here's all the sasl commands i have in my main.cf, keep in mind that im not using a database for my users since there is less then 200 of them and what I have, has been working fine now for quite some time.

> smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


I also noticed that you dont have a certificate or maybe its just a different process with the database?!?

---

### Post by MJN on 2007-04-16
> **BitHosts said:**
>  I have followed: [http://www.howtoforge.com/virtual_po...er_ubuntu_edgy]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy")

Well that's your first problem - these HowTo's are all fine and dandy when they work (although you usually learn little), but when you hit a problem a different story entirely...! ;-)

> Naturally I think this isnt secure, and so want it sorted as a result at the moment SMTP is blocked at the firewall level.As long as you've got **reject_unauth_destination** in your **smtpd_recipient_restrictions** you're fine as far as not being an open relay is concerned. Your config is truncated hence I can't check. Besides, if you as an authorised user can't authenticate to send mail then sure as hell noone else can!

Your client isn't Outlook is it? That requires a [B]broken_sasl_auth_clients = yes

[/B]Did you also mean to use **smtp_use_tls = yes** and not **smtpd_use_tls = yes** ? The latter is essential for TLS with clients, the former is probably not what you intended to do (valid but probably not intentional).

Telnet to **localhost 25**, issue an **ehlo test** command and post the output - that might help us see what's wrong. Your mail.log file would be useful too as the error your client gives may not be indicative of the cause of the problem.

Incidentally, when you're good and ready you should change **smtpd_tls_auth_only** to **yes** otherwise clients won't be required to start a TLS tunnel before sending the cleartext password across.

One other tip - sort your config file into logical sections, at least all the smptd directives together and preferably seperate general, SASL, etc sections as it makes problem spotting much easier! :-)

Mathew

---

### Post by BitHosts on 2007-04-16
Sorry, heres an untruncated version of my main.cf:

```

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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.bithosts.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.bithosts.co.uk, localhost, localhost.bithosts.co.uk
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over their quote."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps$virtual_alias)domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
smtpd_sasl_security_options = noanonymous
smtpd_tls_auth_only = no
smtp_use_tls = yes

```

> As long as you've got reject_unauth_destination in your smtpd_recipient_restrictions you're fine as far as not being an open relay is concerned. Your config is truncated hence I can't check. Besides, if you as an authorised user can't authenticate to send mail then sure as hell noone else can!

Sorry thats not what I meant,  If authentication is turned off in my client I can send emails without an issue - which leads me to believe that there is something wrong.  With SMTP authentication turned on my login gets denied.  I believe I have reject_unauth_destination set in my config too.

I also have broken_sasl_auth_clients set to yes aswell.  I cant honestly remember whether I had smtp_use_tls = yes and not smtpd_use_tls = yes (ive continued trying to get it to work since I posted) , but now it seems to be correct as with what your saying - however it still doesnt work im afraid.


ehlo test produces:

```
250-mail.bithosts.co.uk
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME
```

These are the last few lines of the mail.log, ive changed a few entries here and there - to protect peoples identities mainly, afraid it doesnt really help me much - and it also hints at another issue im yet to come across:

```
Apr 15 19:03:10 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=0
Apr 15 19:06:19 sol courierpop3login: Connection, ip=[::ffff:140.98.266.216]
Apr 15 19:06:19 sol courierpop3login: LOGIN, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216]
Apr 15 19:06:19 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=0
Apr 15 19:09:30 sol courierpop3login: Connection, ip=[::ffff:140.98.266.216]
Apr 15 19:09:30 sol courierpop3login: LOGIN, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216]
Apr 15 19:09:30 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=0
Apr 15 19:12:48 sol courierpop3login: Connection, ip=[::ffff:140.98.266.216]
Apr 15 19:12:48 sol courierpop3login: LOGIN, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216]
Apr 15 19:12:48 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=0
Apr 15 19:15:50 sol postfix/smtpd[27062]: connect from localhost[127.0.0.1]
Apr 15 19:15:59 sol courierpop3login: Connection, ip=[::ffff:140.98.266.216]
Apr 15 19:15:59 sol courierpop3login: LOGIN, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216]
Apr 15 19:15:59 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=0
Apr 15 19:16:56 sol postfix/smtpd[27062]: disconnect from localhost[127.0.0.1]
Apr 15 19:19:12 sol courierpop3login: Connection, ip=[::ffff:140.98.266.216]
Apr 15 19:19:12 sol courierpop3login: LOGIN, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216]
Apr 15 19:19:13 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=1
Apr 15 19:20:00 sol courierpop3login: Connection, ip=[::ffff:140.98.266.216]
Apr 15 19:20:00 sol courierpop3login: LOGIN, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216]
Apr 15 19:20:00 sol postfix/smtpd[28265]: connect from mp206a.halls.manchester.ac.uk[140.98.266.216]
Apr 15 19:20:00 sol courierpop3login: LOGOUT, user=john.smith@bithosts.co.uk, ip=[::ffff:140.98.266.216], top=0, retr=0, time=0
Apr 15 19:20:00 sol postfix/smtpd[28265]: warning: mp206a.halls.manchester.ac.uk[140.98.266.216]: SASL LOGIN authentication failed
Apr 15 19:20:00 sol postfix/smtpd[28265]: lost connection after AUTH from mp206a.halls.manchester.ac.uk[140.98.266.216]
Apr 15 19:20:00 sol postfix/smtpd[28265]: disconnect from mp206a.halls.manchester.ac.uk[140.98.266.216]
Apr 15 19:20:00 sol postfix/smtpd[28270]: connect from ug-out-1314.google.com[66.249.92.175]
Apr 15 19:20:01 sol postfix/smtpd[28270]: NOQUEUE: reject: RCPT from ug-out-1314.google.com[66.249.92.175]: 550 <john@bithosts.co.uk>: Recipient address rejected: User unknown in virtual mailbox table; from=<jack.sparrow@gmail.com> to=<john@bithosts.co.uk> proto=ESMTP helo=<ug-out-1314.google.com>
Apr 15 19:20:01 sol postfix/smtpd[28270]: disconnect from ug-out-1314.google.com[66.249.92.175]

```

Dont think its a certificate issue as there is a key/cert mentioned in the config file already.

Thank you both again for all the help.  Im really struggling to see what I have missed...

---

### Post by MJN on 2007-04-16
> **BitHosts said:**
> Sorry thats not what I meant,  If authentication is turned off in my client I can send emails without an issue - which leads me to believe that there is something wrong.  With SMTP authentication turned on my login gets denied.  I believe I have reject_unauth_destination set in my config too.

I meant noone can relay from outside your network can hence no need to firewall off port 25. Presumably your test client is within your LAN/machine? Hence why it can relay without authenticating. Of course, this has nothing to do with why authentication is failing...

Speaking of which I'm afraid I'm unsure. I'm guessing it's something to do with the SASL configuration/setup as opposed to the Postfix config - try testing SASL with **testsaslauthd -u username -p password -f /var/spool/postfix/var/run/saslauthd/mux** (although if you're using MySQL for the passwords this might not be helpful). Again, that's the problem with the HowTo's that don't teach and test at every step 'cos noone else can really be expected to subsequently trawl through the document to try and see where errors might occur!

Perhaps someone else that has followed that guide can help, at least by comparing their setup (I see the guide quoted a lot so obviously very popular).

Mathew

---

### Post by BitHosts on 2007-04-16
> I meant noone can relay from outside your network can hence no need to firewall off port 25. Presumably your test client is within your LAN/machine? Hence why it can relay without authenticating. Of course, this has nothing to do with why authentication is failing...

Cheers again for the info guys, its great.  Please can you explain what you mean by relaying - im not sure I follow entirely.  Surely if I dont use a password to authenticate outbound emails (and they work) this means that anyone could send emails using my domain name just by logging into the server.  Im not on the same LAN as the server.

Unfortuantely the testsasl command retuned:

"0: NO "authentication failed"

Overall I agree with you on the whole guides that teach aspect, unfortunately though sometimes you just need to get things done, and most of the time when following such a guide things dont go wrong - not straight away anyway, so its a balance between short and long term productivity.  One of the things I would like to produce is a site that hosts guides that teach - once i get this server sorted its one of the things that ill be working on.

---

### Post by etola on 2007-04-27
> **BitHosts said:**
> Cheers again for the info guys, its great.  Please can you explain what you mean by relaying - im not sure I follow entirely.  

relaying means to send your outgoing mail through another server. for example you send your email to gmail and then gmail *relays* your mail to the destination.

this is a very useful property because some mail servers reject the emails if they cannot 
verify that the mail comes from a registered host. so if you want to send emails regardless of your isp you can always relay your emails.

there is actually a very good howto to relay mail over gmail at [http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

---

