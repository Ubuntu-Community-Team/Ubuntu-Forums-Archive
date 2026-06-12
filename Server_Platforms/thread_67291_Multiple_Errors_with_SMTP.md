---
title: "Multiple Errors with SMTP"
date: 2005-09-19
forum: Server Platforms
---

### Post by dcostelloe on 2005-09-19
Well I setup the postfix and courier as per instructions with shorewall and squirrel mail etc. I am totally lost.

I tried everything multiple times. I have 25 messages in the mail queue that reports unable to deliver due to 127.0.0.1 timed out.

Error in logs:
Sep 19 20:53:00 localhost amavis[9577]: Net::Server: 2005/09/19-20:53:00 Server closing!
Sep 19 20:53:00 localhost amavis[9578]: Net::Server: 2005/09/19-20:53:00 Couldn't open lock file "/var/run/amavis/amavisd.lock" [Permission denied]\n  at line 239 in file /usr/share/perl5/Net/Server/PreForkSimple.pm
Sep 19 20:53:00 localhost amavis[9578]: Net::Server: 2005/09/19-20:53:00 Server closing!

Sep 19 20:51:13 localhost postfix/qmgr[8329]: D29E51EC8DA: to=<amavis-stats@bandit.welford-costelloe.com>, orig_to=<amavis-stats>, relay=none, delay=289, status=deferred (delivery temporarily suspended: connect to 127.0.0.1 [127.0.0.1]: read timeout)

Using Webmin and followed email prior of links to sites.

Anyone got a working process for smtp and IMAP?

Every thing is failing including squirrelmail reports IMAP disconnected.

 ](*,) 

This is a lot easier in windows... or I'm missing something.

Thanks

---

### Post by Glut on 2005-09-20
Though not an expert with some of these programs, I have noticed that your virus scanner - amavis is not getting control of it's lock file. 
check the permissions on this file. Check the permissions on the /var/run/amavis/amavisd.lock file. You will probably need write permissions for the mail user (assuming the mail user is the one running amavis)

---

### Post by dcostelloe on 2005-09-20
Yes you are correct. The problem now is everytime I log off and then on as a admin the lock returns?

Is there a way to ensure the lock is for ever?

Thanks :grin:

---

### Post by Glut on 2005-09-21
I may be misreading you, this are my possible interpretations:
a. You are logging off as user and logging on as root and the lock is deleted
b. you are logging off as root, then log back on as root and the lock is deleted

Either way, if the process is running as a daemon this shouldn't be caused by logging on/off.

Or is the lock changing ownership or permissions, rather than being deleted?

---

### Post by deuce868 on 2005-09-21
Did you try to just delete the lock file and restart avavisd?

On my system the /var/run/amavis is owned by amavis/amavis and the lock file inside there is owned the same way with permissions 640

Double check the permissions on the /var/run/amavis folder

---

### Post by dcostelloe on 2005-09-21
This happens verytime it restarts:

Starting amavisd: mode of `/var/run/amavis' changed to 0755 (rwxr-xr-x)

Just waiting to see if the file locks again...

---

### Post by dcostelloe on 2005-09-24
The user I setup as per documents was to use the user virtual and group virtual. I change this to the user on the permissions and things start to work again.

Once I re-boot I get the same errors again in the logs:


Sep 24 12:28:43 BANDIT amavis[8526]: Net::Server: 2005/09/24-12:28:43 Couldn't open lock file "/var/run/amavis/amavisd.lock" [Permission denied]\n  at line 239 in file /usr/share/perl5/Net/Server/PreForkSimple.pm

Sep 24 12:28:56 BANDIT postfix/qmgr[6919]: 94B41134581: to=<david@welford-costelloe.com>, relay=none, delay=0, status=deferred (delivery temporarily suspended: connect to 127.0.0.1 [127.0.0.1]: read timeout)

Keeps timing out and the queue is at 52 and rising. Squirrelmail still reports Imapi error.

 ](*,) 

I did a complete re-install 3 times of ubuntu

---

### Post by dcostelloe on 2005-09-30
Fix the problem with the amavis.

Edited the /etc/init.d/amavis script removed the $1:$2 and put in virtual:virtual

Having strange things happen with ubuntu updates..

Now that the problem is fixed on amavis I'm having issues with my mail queue not delivery the mail. Reports:
	connect to 127.0.0.1 [127.0.0.1]: read timeout
and 
host 127.0.0.1[127.0.0.1] said: 450 4.4.1 Can't connect to 127.0.0.1 port 10035, Operation now in progress at /usr/sbin/amavisd-new line 2912, <GEN11> line 237., id=12043-01 (in reply to end of DATA command)


arhhhhhh this is getting to be a real pain. Too bad there isn't a good smtp like Mercury32.

:confused:

---

### Post by deuce868 on 2005-09-30
[QUOTE=dcostelloe]Fix the problem with the amavis.
Edited the /etc/init.d/amavis script removed the $1:$2 and put in virtual:virtual
Having strange things happen with ubuntu updates..
Now that the problem is fixed on amavis I'm having issues with my mail queue not delivery the mail. Reports:
connect to 127.0.0.1 [127.0.0.1]: read timeout
and 
host 127.0.0.1[127.0.0.1] said: 450 4.4.1 Can't connect to 127.0.0.1 port 10035, Operation now in progress at /usr/sbin/amavisd-new line 2912, <GEN11> line 237., id=12043-01 (in reply to end of DATA command)
arhhhhhh this is getting to be a real pain. Too bad there isn't a good smtp like Mercury32.
:confused:[/QUOTE]

Post your /etc/postfix/master.cf file contents. (please remove comments)

there should be a line like:
> 
smtp      inet  n       n       n       -       -       smtpd -v
          -o content_filter=amavis:[127.0.0.1]:10025

amavis unix - - n - 2 smtp
	-o smtp_data_done_timeout=1200
	-o disable_dns_lookups=no
    
127.0.0.1:10025 inet n  -       n       -       -       smtpd
     -o content_filter=
     -o myhostname=mitechie.com
     -o local_recipient_maps=
     -o relay_recipient_maps=
     -o smtpd_restriction_classes=
     -o smtpd_client_restrictions=
     -o smtpd_helo_restrictions=
     -o smtpd_sender_restrictions=
     -o smtpd_recipient_restrictions=permit_mynetworks,reject
     -o mynetworks=127.0.0.0/8
     -o strict_rfc821_envelopes=yes
     -o smtpd_error_sleep_time=0
     -o smtpd_soft_error_limit=1001
     -o smtpd_hard_error_limit=1000


Only your port is 10035 where mine is 10025

You have to understand what postfix is doing. First a message comes in via smtp, postifx sends it to 127.0.0.1:10025 which the amavis process is listening on. Amavis picks up the message, processes it and then resends it back to postfix which then delivers it.

---

### Post by dcostelloe on 2005-09-30
Hi Thanks for the reply.
Yes I am using port 35 as 25 is block by my provider. Amavis (port 10024) is listen on port  35 ok.

When I switch back to 25 I get an error unable to connect to port 10025.

Emails are comming in ok to the server and ending up in the queue. From the queue the emails are not getting delivered.
Clamav and Spamassassin are also reporting theyare loaded and working as expected.


Thanks

---

### Post by deuce868 on 2005-10-01
> Post your /etc/postfix/master.cf file contents. (please remove comments)

hmmm... ;)

---

### Post by dcostelloe on 2005-10-01
Master.cf

#smtp      inet  n       -       -       -       -       smtpd
smtp       inet  n       -       -       -       -       smtpd 
	-o cleanup_service_name=pre-cleanup
#submission inet n      -       -       -       -       smtpd
#	-o smtpd_etrn_restrictions=reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
#cleanup   unix  n       -       -       -       0       cleanup
cleanup    unix  n       -       -       -       0       cleanup 
	-o mime_header_checks= 
	-o nested_header_checks= 
	-o body_checks= 
	-o header_checks=
amavis     unix - - - - 2 smtp 
	-o smtp_data_done_timeout=1200 
	-o smtp_send_xforward_command=yes
# 127.0.0.1:10025 inet n - - - - smtpd  - If I use this error reported
127.0.0.1:10035 inet n - - - - smtpd 
	-o content_filter= 
	-o local_recipient_maps= 
	-o relay_recipient_maps= 
	-o smtpd_restriction_classes= 
	-o smtpd_client_restrictions= 
	-o smtpd_helo_restrictions= 
	-o smtpd_sender_restrictions= 
	-o smtpd_recipient_restrictions=permit_mynetworks,reject 
	-o strict_rfc821_envelopes=yes 
	-o mynetworks=127.0.0.0/8 
	-o smtpd_error_sleep_time=0 
	-o smtpd_soft_error_limit=1001 
	-o smtpd_hard_error_limit=1001
pre-cleanup unix n - - - 0 cleanup 
	-o virtual_alias_maps= 
	-o canonical_maps= 
	-o sender_canonical_maps= 
	-o recipient_canonical_maps= 
	-o masquerade_domains=
qmgr      fifo  n       -       -       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -d -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}

# only used by postfix-tls
#tlsmgr	  fifo	-	-	n	300	1	tlsmgr
#smtps	  inet	n	-	n	-	-	smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
#587	  inet	n	-	n	-	-	smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes

---

### Post by dcostelloe on 2005-10-01
Main.cf

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
content_filter = amavis:[127.0.0.1]:10024
# My Domain as with easydns - changed for posting
myhostname = mail.mydomain.com
# Relay via Sympatico
relayhost = [smtph.sympatico.ca]
mynetworks_style = host
masquerade_exceptions = root
local_recipient_maps =
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 16d
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_sender_restrictions = reject_non_fqdn_sender permit_sasl_authenticated reject_unknown_sender_domain reject_unauth_pipelining permit eject_non_fqdn_sender permit_sasl_authenticated reject_unknown_sender_domain reject_unauth_pipelining permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, reject_rbl_client cbl.abuseat.org
smtpd_recipient_restrictions = permit_mynetworks, reject_non_fqdn_recipient, reject_unauth_destination, check_relay_domains,permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient,
smtpd_helo_required = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# Had to create these mailboxes manually due to issue with squirrelmail
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# transport_maps = mysql:/etc/postfix/mysql_transport.cf
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2 
smtpd_sasl_local_domain = $myhostname
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining
smtp_sasl_password_maps = hash:/etc/postfix/sasl/passwd
smtp_sasl_security_options =

myorigin = /etc/mailname
mailbox_size_limit = 0
recipient_delimiter = +

Thanks
David..........

---

### Post by dcostelloe on 2005-10-01
Overview of my setup:

Running DLink Router (Handles all the DNS for the network)
Dlink is setu to SMTP as follows:
local port 25
public port 35


Easydns for dynamic updates for domain on sympatico
Easydns set up to [email]mail@myserver.com[/email]


Ubuntu OS dual boot with windows 2000 server.

DDCLient 
Amavis-New
Postfix
Clamav
Spamassassin

Shorewall (disabled until I can figure out how to allow my network to access the internet and master web site)


Hoping to switch from win2000 to ubuntu

:p

---

### Post by dcostelloe on 2005-10-02
Yes!

I have kicked myself several times. But I have everything working as expected and yes even the mail relay is doing its job!

Thanks to all for your help:p

---

### Post by deuce868 on 2005-10-02
[QUOTE=dcostelloe]Yes!
I have kicked myself several times. But I have everything working as expected and yes even the mail relay is doing its job!
Thanks to all for your help:p[/QUOTE]
Hey, sorry I just got back from the Ohio Linuxfest. I'm glad you got it working.

---

### Post by dcostelloe on 2005-10-02
:-)

---

### Post by deuce868 on 2005-10-02
no, you just had a message from the www-data (apache user) sent to [email]info@welford-costelloe.com[/email]

---

### Post by dcostelloe on 2005-10-02
wew!
Thought something was off there:

Thanks
:razz:

---

