---
title: "Postfix Broken...Urgent Help Needed"
date: 2008-06-03
forum: Server Platforms
---

### Post by YouBunn2 on 2008-06-03
So I was looking at my postfix configuration through Webmin and I have no idea what happened but mail stopped flowing and I cannot get it back on. 
WHen I telnet into port 25 I get a blank screen that just sits there. 
When I look at the maillog I have "postfix "warning: problem talking to server private/anvil: Connection refused"



Can someone please help me. 

thanks

---

### Post by windependence on 2008-06-04
We're gonna need a bit more info than what you gave us to fix this. I would start by posting your mail.conf file.

Are you telnetting from the local machine or a remote mahine?

-Tim

---

### Post by YouBunn2 on 2008-06-04
I am able to do the telnet test, but messages are just piling up in the queue and then bouncing, too many hops. 
I will offer someone $$$ to go into the system and fix this for me. 

Main.cf
myhostname = My.Hostname.com
mydomain = MyDomain.com
myorigin = $mydomain
mydestination = 
local_recipient_maps = 
relay_domains = name1.com, name2.com
message_size_limit = 104857600
#transport_maps = hash:/etc/postfix/transport
transport_maps = mysql:/etc/postfix/transport-mysql.cf
smtpd_helo_required = yes
disable_vrfy_command = yes
virtual_alias_maps = hash:/etc/postfix/virtual
alias_maps = hash:/etc/aliases
recipient_delimiter = +
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_banner = Hello,
content_filter = smtp-amavis:[127.0.0.1]:10024


# Anti UCE measures - first line defence mechanism before
# passing onto further more resource intensive tests.
# Some of these may be too strict for your environment...
# These have been commented out but feel free to enable
# them if you want to tighten the floodgates...

smtpd_helo_required = yes
disable_vrfy_command = yes
# strict_rfc821_envelopes = yes



smtpd_recipient_restrictions = 
        permit_mynetworks, 
        reject_unauth_destination,

#       reject_unknown_client,
#       permit_sasl_authenticated,
#       check_recipient_access pcre:/etc/postfix/recipient_checks.pcre,
#       check_helo_access hash:/etc/postfix/helo_checks,
#       check_helo_access pcre:/etc/postfix/helo_checks.pcre,


smtpd_data_restrictions =
        reject_unauth_pipelining,
        permit
mailbox_size_limit = 0


Master.cf
# Example main.cf
# Scott Hurring [scott at hurring dot com]
# [http://hurring.com/howto/postfix_spamd/](http://hurring.com/howto/postfix_spamd/)
#
# ==========================================================================
# service type	private	unpriv	chroot	wakeup	maxproc	command + args
# 		(yes)	(yes)	(yes)	(never)	(50)
# ==========================================================================
smtp	  inet	n	-	-	-	-	smtpd
	
#628	  inet	n	-	-	-	-	qmqpd
pickup	  fifo	n	-	-	60	1	pickup
         -o content_filter=
         -o receive_override_options=no_header_body_checks
cleanup	  unix	n	-	-	-	0	cleanup
qmgr	  fifo	n	-	-	300	1	qmgr
#qmgr	  fifo	n	-	-	300	1	nqmgr
rewrite	  unix	-	-	-	-	-	trivial-rewrite
bounce	  unix	-	-	-	-	0	bounce
defer	  unix	-	-	-	-	0	bounce
flush	  unix	n	-	-	1000?	0	flush
smtp	  unix	-	-	-	-	-	smtp
showq     unix	n	-	-	-	-	showq
error     unix	-	-	-	-	-	error
local	  unix	-	n	n	-	-	local
virtual	  unix	-	n	n	-	-	virtual
lmtp	  unix	-	-	n	-	-	lmtp
#
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
# The Cyrus deliver program has changed incompatibly.
#

smtp-amavis	unix	-	-	y	-	2	smtp
	-o smtp_data_done_timeout=1200
	-o smtp_send_xforward_command=yes
	-o disable_dns_lookups=yes
	-o max_use=20

127.0.0.1:10025	inet	n	-	y	-	-	smtpd
	-o local_recipient_maps=
	-o relay_recipient_maps=
	-o smtpd_restrictions_classes=
	-o smtpd_delay_reject=no
	-o smtpd_client_restrictions=permit_mynetworks,reject
	-o smtpd_helo_restrictions=
	-o smtpd_sender_restrictions=
	-o smtpd_recipient_restrictions=permit_mynetworks,reject
	-o smtpd_data_restrictions=reject_unauth_pipelining
	-o smtpd_end_of_data_restrictions=
	-o mynetworks=127.0.0.0/8
	-o smtpd_error_sleep_time=0
	-o smtpd_soft_error_limit=1001
	-o smtpd_hard_error_limit=1000
	-o smtpd_client_connection_count_limit=0
	-o smtpd_client_connection_rate_limit=0
	

spamassassin unix -     n       n       -       -       pipe
        user=nobody argv=/usr/bin/spamc -f -e
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}

cyrus	  unix	-	n	n	-	-	pipe
  flags=R user=cyrus argv=/usr/sbin/cyrdeliver -e -m ${extension} ${user}
uucp	  unix	-	n	n	-	-	pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -d -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}

# only used by postfix-tls
#smtps	  inet	n	-	n	-	-	smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
#587	  inet	n	-	n	-	-	smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes



mail is just piling up in the queue and not relaying to the smtp server.
Is this good to go on?

---

### Post by dmond on 2008-06-04
is the queue full?
why is it taking a long time in the queue?

usually, if the queue is 95% full, it will cost problems relaying it. try moving some of the mail in the queue to a different location. (or maybe try clearing up the queue but you'll lose important mail.) then restart postfix and test it.

---

### Post by YouBunn2 on 2008-06-04
> **dmond said:**
> is the queue full?
why is it taking a long time in the queue?

usually, if the queue is 95% full, it will cost problems relaying it. try moving some of the mail in the queue to a different location. (or maybe try clearing up the queue but you'll lose important mail.) then restart postfix and test it.

i have done that already and still no luck with it.
:(

---

### Post by MJN on 2008-06-04
Post your logs - that's what they're for!
 
In the meantime it looks like Webmin has screwed with your master file - try adding the following to it:
 
**anvil unix ---- 1 anvil**
 
When this is all over consider moving away from Webmin... it's fraught with problems like this.
 
Mathew

---

### Post by YouBunn2 on 2008-06-04
I have added anvil unix ---- 1 anvil to master.cf

now my maillog is showing:
Jun  4 07:02:59 name postfix/smtpd[15681]: warning: connect #3 to subsystem private/rewrite: Connection refused
Jun  4 07:03:01 name postfix/smtpd[15550]: warning: connect #7 to subsystem private/rewrite: Connection refused
Jun  4 07:03:01 name postfix/smtpd[15542]: warning: connect #6 to subsystem private/rewrite: Connection refused

---

### Post by YouBunn2 on 2008-06-04
I think the configs arent pointing to the MySQL db. 
I am having mail flow to what I have in the static mappings but now what is on the MySQL. 

is my config file pointing to the db?

---

### Post by MJN on 2008-06-04
Post your log from the point of a Postfix restart. Snippets really are of little use as what to you might be insignificant and hence worthy of leaving out may well be critical.

Mathew

---

### Post by YouBunn2 on 2008-06-04
> **MJN said:**
> Post your log from the point of a Postfix restart. Snippets really are of little use as what to you might be insignificant and hence worthy of leaving out may well be critical.

Mathew

What log are you looking for?

Thanks

---

### Post by MJN on 2008-06-04
Your mail log (/var/log/mail.log).

Mathew

---

### Post by YouBunn2 on 2008-06-04
Here is part of my log: I cant figure out how to do a text window.


ze: 4659, 5334 ms
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<glover@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<grant@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<grantd@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<graves@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<gray@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<grayd@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/smtp[3199]: ED6481B24C0: to=<graydd@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=14896, delays=10375/4515/0.01/5.3, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-18, DISCARD(bounce.suppressed))
Jun  4 18:37:16 MyServer postfix/qmgr[698]: ED6481B24C0: removed
Jun  4 18:37:16 MyServer postfix/smtpd[1628]: warning: 190.56.126.166: hostname 166.126.56.190.BLA.net.gt verification failed: Name or service not known
Jun  4 18:37:17 MyServer postfix/smtpd[1628]: connect from unknown[190.56.126.166]
Jun  4 18:37:17 MyServer postfix/smtpd[2583]: warning: 201.240.132.168: hostname client-201.240.132.168.speedy.net.pe verification failed: Name or service not known
Jun  4 18:37:17 MyServer postfix/smtpd[2583]: connect from unknown[201.240.132.168]
Jun  4 18:37:17 MyServer postfix/smtpd[2749]: connect from unknown[190.42.71.20]
Jun  4 18:37:18 MyServer amavis[3186]: (03186-16) Blocked SPAM, [86.14.208.65] [86.14.208.65] <plkerBLA@osce.org> -> <mccoy@MyDomain1.com>, Message-ID: <000401c8c650$05f2b255$322027ae@ffrlehe>, mail_id: 5gbKLQ9YCSG2, Hits: 14.749, size: 752, 3737 ms
Jun  4 18:37:18 MyServer postfix/smtp[3166]: EF424C322: to=<mccoy@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=32491, delays=27968/4520/0.01/3.7, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03186-16, DISCARD(bounce.suppressed))
Jun  4 18:37:18 MyServer amavis[3164]: (03164-19) Blocked SPAM, [82.154.8.193] [82.154.8.193] <sina@paratype.com> -> <morrison@MyDomain1.com>, Message-ID: <02541956.20080604161317@MyDomain1.com>, mail_id: xMM2AIbgtMe3, Hits: 18.477, size: 10672, 2032 ms
Jun  4 18:37:18 MyServer postfix/smtp[3199]: E536DCFBF: to=<morrison@MyDomain1.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=26945, delays=22422/4521/0.01/2, dsn=2.5.0, status=sent (250 2.5.0 Ok, id=03164-19, DISCARD(bounce.suppressed))
Jun  4 18:37:18 MyServer postfix/smtpd[1628]: 777E91B2AF3: client=unknown[190.56.126.166]
Jun  4 18:37:18 MyServer postfix/smtpd[1628]: lost connection after RCPT from unknown[190.56.126.166]
Jun  4 18:37:18 MyServer postfix/smtpd[1628]: disconnect from unknown[190.56.126.166]
Jun  4 18:37:18 MyServer postfix/smtpd[2583]: 9C2A91B3331: client=unknown[201.240.132.168]
Jun  4 18:37:18 MyServer postfix/qmgr[698]: EF424C322: removed
Jun  4 18:37:19 MyServer postfix/qmgr[698]: E536DCFBF: removed
Jun  4 18:37:19 MyServer postfix/cleanup[2750]: 9C2A91B3331: message-id=<000801c8c4f9$07825742$2006c0a4@mivig>
Jun  4 18:37:19 MyServer postfix/qmgr[698]: 9C2A91B3331: from=<Opbehm@BLAA.org>, size=2439, nrcpt=1 (queue active)
Jun  4 18:37:20 MyServer postfix/smtpd[2583]: disconnect from unknown[201.240.132.168]

From looking at it, it appears the relay mapping is hosed.

---

### Post by MJN on 2008-06-05
That log looks fine (spam being identified and dropped), however you need to post the log _from the point of restarting Postfix_ like I keep asking! :-) That is, restart Postfix with **sudo /etc/init.d/postfix restart** and then post the log from that point - any services that don't start, or start and then stop, will be captured in the log at the early stages of Postfix (and its supporting services) starting up.

You might want to temporarily disable your spam filter (comment out the content_filter directive in /etc/postfix/main.cf) as double-loops through content checkers can make fault diagnosis confusing.

I'm more than happy to help you solve this, but you've got to help me to help you!

Mathew

---

### Post by YouBunn2 on 2008-06-05
I hope this is what you need. Like I said before I'm not knowledgeable on this. but know enough to be dangerous. 



Jun  5 06:09:11 Server postfix/postfix-script[25779]: starting the Postfix mail system
Jun  5 06:09:11 Server postfix/master[25780]: daemon started -- version 2.5.1, configuration /etc/postfix
Jun  5 06:09:12 Server postfix/smtpd[25783]: connect from unknown[123.234.191.122]
Jun  5 06:09:12 Server postfix/smtpd[25785]: connect from unknown[88.236.103.134]
Jun  5 06:09:13 Server postfix/smtpd[25788]: warning: 92.8.51.242: hostname host-92-8-51-242.as43234.net verification failed: Name or service not known
Jun  5 06:09:13 Server postfix/smtpd[25788]: connect from unknown[92.8.51.242]
Jun  5 06:09:13 Server postfix/smtpd[25786]: warning: 218.18.173.239: hostname 239.173.18.218.broad.sz.gd.dynamic.163data.com.cn verification failed: Name or service not known
Jun  5 06:09:13 Server postfix/smtpd[25786]: connect from unknown[218.18.173.239]
Jun  5 06:09:14 Server postfix/smtpd[25783]: 47CB21899F: client=unknown[123.234.191.122]
Jun  5 06:09:14 Server postfix/smtpd[25785]: C7E29189D6: client=unknown[88.236.103.134]
Jun  5 06:09:15 Server postfix/smtpd[25788]: 08AD3189D9: client=unknown[92.8.51.242]
Jun  5 06:09:15 Server postfix/cleanup[25789]: 47CB21899F: message-id=<YAFXVURXSJQPWJLWCYLNXUDF@yahoo.com>
Jun  5 06:09:15 Server postfix/cleanup[25791]: 08AD3189D9: message-id=2507401c8c6fd$1f8f9c30$0200a8c0@your8e56f55ee8
Jun  5 06:09:15 Server postfix/smtpd[25788]: disconnect from unknown[92.8.51.242]
Jun  5 06:09:15 Server postfix/smtpd[25783]: disconnect from unknown[123.234.191.122]
Jun  5 06:09:16 Server postfix/cleanup[25790]: C7E29189D6: message-id=c434001c8c6fd$1de98d50$0202a8c0@termal
Jun  5 06:09:16 Server postfix/smtpd[25786]: 85886189DA: client=unknown[218.18.173.239]
Jun  5 06:09:16 Server postfix/smtpd[25785]: disconnect from unknown[88.236.103.134]
Jun  5 06:09:17 Server postfix/smtpd[25783]: connect from ova-9-149.adsl.sky.cz[193.165.9.149]
Jun  5 06:09:17 Server postfix/cleanup[25792]: 85886189DA: message-id=<122155897.33691312606399@bookliquidators.com>
Jun  5 06:09:18 Server postfix/smtpd[25786]: disconnect from unknown[218.18.173.239]

---

### Post by MJN on 2008-06-05
So when are you getting the private/rewrite errors as mentioned before?

I appreciate you're new to this and there's nothing wrong with that, but please stop snipping the logs. Post the whole 15 pages if you'd prefer - we need to see exactly what's happening, not just what's happening in the snippet of time that you think is relevant!

Telnet to port 25 and see what happens in the logs (or rather post them), also send in a message from outside your server.

Have you disabled the spam check?

Mathew

---

