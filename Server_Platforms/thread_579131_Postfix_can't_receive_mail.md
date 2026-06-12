---
title: "Postfix can't receive mail"
date: 2007-10-18
forum: Server Platforms
---

### Post by macka` on 2007-10-18
Hi there, 
I've been searching a bit trying to find some answers as to what is happening. 
I've got my postfix + mysql + courier-imap + spamassassin yada yada install, and it runs ok. 
I can send out of the network, but i can't receive anything. ie, i can send to an external address, but not an internal one. 
If i set up 2 users A and B i can't send user A an email from user B, and also it doesn't deliver the "bounce" messages back to user A. 

Has someone struck this before? do i need to post my postconf -n?

oh - i should mention, i have set this machine up with a FQD name, but there's no external IP address pointing at it, so i think the problem is that it can't do any reverse lookups?
eg log file results from /var/log/mail.log after sending an email from local client

Oct 18 17:22:56 reddwarf postfix/smtpd[18836]: connect from unknown[192.168.1.103]
Oct 18 17:22:56 reddwarf postfix/smtpd[18836]: 038D5168756: client=unknown[192.168.1.103]
Oct 18 17:22:56 reddwarf postfix/cleanup[18846]: 038D5168756: message-id=<007c01c8113e$8ed61b20$6701a8c0@TAGD101>              
Oct 18 17:22:56 reddwarf postfix/qmgr[18794]: 038D5168756: from=<userA@domain.com>, size=1335, nrcpt=1 (queue active)               
Oct 18 17:22:56 reddwarf postfix/smtpd[18836]: disconnect from unknown[192.168.1.103]
Oct 18 17:23:00 reddwarf postfix/smtpd[18844]: connect from localhost[127.0.0.1]
Oct 18 17:23:00 reddwarf postfix/smtpd[18844]: 6F98716876A: client=localhost[127.0.0.1]
Oct 18 17:23:00 reddwarf postfix/cleanup[18837]: 6F98716876A: message-id=<007c01c8113e$8ed61b20$6701a8c0@TAGD101>
Oct 18 17:23:00 reddwarf postfix/qmgr[18794]: 6F98716876A: from=<userA@domain.com>, size=1850, nrcpt=1 (queue active)
Oct 18 17:23:00 reddwarf postfix/smtpd[18844]: disconnect from localhost[127.0.0.1]
Oct 18 17:23:00 reddwarf amavis[18036]: (18036-02) Passed CLEAN, LOCAL [192.168.1.103] [192.168.1.103] <userA@domain.com> -> <userA$
Oct 18 17:23:00 reddwarf postfix/smtp[18841]: 038D5168756: to=<userA@domain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=4.6, dela$
Oct 18 17:23:00 reddwarf postfix/qmgr[18794]: 038D5168756: removed
Oct 18 17:23:30 reddwarf postfix/smtp[18847]: connect to mailmachine.domain.com[<our.external.IP.addy]: Connection timed out (port 25)
Oct 18 17:23:30 reddwarf postfix/smtp[18847]: 6F98716876A: to=<userA@domain.com>, relay=none, delay=30, delays=0.08/0.01/30/0, dsn=$
Oct 18 17:24:10 reddwarf postfix/smtpd[18836]: connect from unknown[192.168.1.103]

Cheers
Grant

---

### Post by GrumpySmurf on 2007-10-18
Yes, please post your postconf -n. Of particular note will be the values of mynetworks, mydestination, relayhost, and inet_interfaces.

Also post relevant lines from sending test emails from your /var/log/mail.log, /var/log/mail.err.

---

### Post by macka` on 2007-10-18
postconf -n output is ::: 

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
mailbox_command = procmail -a $EXTENSION
mailbox_size_limit = 0
mydestination = mailmachine.domain.com, reddwarf, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 192.168.0.0/24
myorigin = /etc/mailname
proxy_read_maps = $local_recipient_maps $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
receive_override_options = no_address_mappings
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains = 
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /location/of/mail/directory
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = virtual
virtual_uid_maps = static:5000

---

### Post by GrumpySmurf on 2007-10-18
I assume 'domain.com' is a fill in for your actual domain?

Are userA and userB both on the local system? For local delivery you might need to look into transports options. I would also suggest running a local DNS server for resolving your internal addresses. Proper SMTP functionality relies on stable DNS resolution.

---

### Post by macka` on 2007-10-18
Yep = domain.com is the fill in. 
and userA and userB are both on the same box.
This machine is going to be replacing the current mail server, so i'm running it in the same network. Hence why i said before there's no route from our external IP to this box. But still i would have thought if as [email]userA@domain.com[/email] i sent an email to [email]userB@domain.com[/email] that i would still transmit that message since it's on the local machine. Or even if i didn't get the email, i would atleast get the bounce back message?

Haven't got a Bind server running although thats an interesting thought... and one that would make some sense. 
Shouldn't it already semi be done already using hosts?
poking at sticks there i think. 

Grant

---

### Post by MJN on 2007-10-18
It could be your **mydestination = mailmachine.domain.com, reddwarf, localhost.localdomain, localhost** setting as Postfix has not been told it is the final destination for 'domain.com' (just *@mailmachine*.domain.com and @<localnames>).

That said, I'm surprised there aren't errors being thrown up, particularly relating to non-delivery of messages and/or unauthorised relaying (to what effectively may be considered a non-local domain given the above).

Aside from adding domain.com to the directive, an obvious test would be to send a message to [EMAIL="A@mailmachine.domain.com"]A@mailmachine.domain.com[/EMAIL] or A@localhost and seeing if it gets delivered.

Mathew

---

### Post by macka` on 2007-10-18
Hi Matthew, 

I tried doing the userA@machine.domain.com and it got removed from the mail queue. 
I do get this error tho of "warning do not list domain "domain.com" in both mydestination and virtual_mailbox_domains" is that a problem?
is that because i have it stored in the mysql database as well?

I followed this tutorial
http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy if that's any help?

I'm thinking of tackling bind now since grumpy suggested it.. do you think that's a wise choice?
the local dns is done on the router (netgear)

If i could get the bounce back messages workin' so far i'd be a happy man! lol

Cheers
Grant

---

### Post by MJN on 2007-10-18
By 'removed from the mail queue' are you saying it was successfull? In which case add domain.com to the mydestination directive, and remove it from any virtual reference.

The warning is correct - any particular domain cannot be a 'main' domain and a 'virtual' one. It's either or.

The normal configuration is that a machine receives mail for itself, and for the domain it is part of. Hence in your case your mydestination should include localhost, localhost.localdomain,mailservername.domain.com and domain.com. Any additional domains that you also accept mail for are known as virtual domains and hence should be by your virtual config (in MySQL).

See [http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html) for further details.

I don't use MySQL for my Postfix management - to be frank I don't really understand MySQL and given I only manage a handful of domains and users I really don't need it.

Mathew

---

### Post by macka` on 2007-10-18
This is the log messages now from when i send an email. 
I had an external DNS alias pointing to our IP last night, so that's why it got a connection time out, but it's still trying to resolve the smtp externally, which i'm guessing why i should probably get a DNS server going?
I only did the Mysql cos that's what the tutorial said (such sucker for following instructions sometimes). Also i have enjoyed the use of Postfixadmin which uses mysql. Plus my boss (who will eventually administrate the users) isn't overly linux savvy, so it's better for him with a web interface (simple is best:))

any other outputs i can give to anyone?

Grant

Oct 19 10:03:55 reddwarf postfix/smtpd[7683]: connect from unknown[192.168.1.103]
Oct 19 10:03:55 reddwarf postfix/trivial-rewrite[7687]: warning: do not list domain domain.com  in BOTH mydestination and virtual_mailbox_domains
Oct 19 10:03:55 reddwarf postfix/smtpd[7683]: 83892168772: client=unknown[192.168.1.103]
Oct 19 10:03:55 reddwarf postfix/cleanup[7688]: 83892168772: message-id=<000d01c811ca$654c3be0$6701a8c0@TAGD101>
Oct 19 10:03:55 reddwarf postfix/qmgr[7671]: 83892168772: from=<grant@domain.com>, size=1350, nrcpt=1 (queue active)
Oct 19 10:03:55 reddwarf postfix/smtpd[7683]: disconnect from unknown[192.168.1.103]
Oct 19 10:04:00 reddwarf postfix/smtpd[7695]: connect from localhost[127.0.0.1]
Oct 19 10:04:00 reddwarf postfix/trivial-rewrite[7687]: warning: do not list domain domain.com in BOTH mydestination and virtual_mailbox_domains
Oct 19 10:04:00 reddwarf postfix/smtpd[7695]: 10F46168773: client=localhost[127.0.0.1]
Oct 19 10:04:00 reddwarf postfix/cleanup[7688]: 10F46168773: message-id=<000d01c811ca$654c3be0$6701a8c0@TAGD101>
Oct 19 10:04:00 reddwarf postfix/qmgr[7671]: 10F46168773: from=<grant@domain.com>, size=1844, nrcpt=1 (queue active)
Oct 19 10:04:00 reddwarf postfix/trivial-rewrite[7687]: warning: do not list domain domain.com in BOTH mydestination and virtual_mailbox_domains
Oct 19 10:04:00 reddwarf postfix/smtpd[7695]: disconnect from localhost[127.0.0.1]
Oct 19 10:04:00 reddwarf amavis[4860]: (04860-09) Passed CLEAN, LOCAL [192.168.1.103] [192.168.1.103] <grant@4d-electronics.co.nz> -> <craig@domain.com>, Message-ID: <000d01c811ca$654c3be0$6701a8c0@TAGD101>, mail_id: Qg-og0aNCOa1, Hits: 2.081, queued_as: 10F46168773, 4543 ms
Oct 19 10:04:00 reddwarf postfix/smtp[7689]: 83892168772: to=<craig@domain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=4.7, delays=0.1/0/0.01/4.5, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=04860-09, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 10F46168773)
Oct 19 10:04:00 reddwarf postfix/qmgr[7671]: 83892168772: removed
Oct 19 10:04:00 reddwarf postfix/smtp[7696]: 10F46168773: to=<craig@domain.com>, relay=none, delay=0.15, delays=0.09/0/0.06/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=reddwarf.domain.com type=A: Host not found)
Oct 19 10:04:00 reddwarf postfix/cleanup[7688]: 3FDFA168775: message-id=<20071018210400.3FDFA168775@reddwarf.domain.com>
Oct 19 10:04:00 reddwarf postfix/qmgr[7671]: 3FDFA168775: from=<>, size=3924, nrcpt=1 (queue active)
Oct 19 10:04:00 reddwarf postfix/bounce[7697]: 10F46168773: sender non-delivery notification: 3FDFA168775
Oct 19 10:04:00 reddwarf postfix/trivial-rewrite[7687]: warning: do not list domain domain.com in BOTH mydestination and virtual_mailbox_domains
Oct 19 10:04:00 reddwarf postfix/qmgr[7671]: 10F46168773: removed
Oct 19 10:04:00 reddwarf postfix/smtp[7696]: 3FDFA168775: to=<grant@domain.com>, relay=none, delay=0.11, delays=0.05/0/0.06/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=reddwarf.domain.com type=A: Host not found)
Oct 19 10:04:00 reddwarf postfix/qmgr[7671]: 3FDFA168775: removed

---

### Post by MJN on 2007-10-18
Have you changed your config?

Your server should be the final destination for domain.com hence no DNS lookups are needed.

You really must heed the warnings it's giving you regarding having the domain specified as a 'real' and 'virtual' domain. I am not familiar with the potential failure characteristics but you'd be mad to try and proceed looking for another fault before you eliminate that one.

Perhaps my conventional use of your domain in mydestination is at odds with how the HowTo is constructed hence it may be advisable to stick with the HowTo way of doing things. Have you tried restarting it from scratch?

Mathew

P.S. In case you're on the verge of pulling your hair out in frustration - don't - you'll get there if you persevere!!

---

### Post by macka` on 2007-10-22
Hi guys, 

after much pulling out (of grey hairs only), i finally realised this was a transport issue. 
The transport data was being held in Mysql, and was not being resolved. 

My best guess is that because i had smtp:mail.mydomain.com as the only transport it therefor wouldn't know about anything locally. 

anyhow - all sorted now, will more on to more exciting things now:D

Thanks for the hand!

Grant

---

