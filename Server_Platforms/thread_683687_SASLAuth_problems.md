---
title: "SASLAuth problems"
date: 2008-01-31
forum: Server Platforms
---

### Post by aeisecurity on 2008-01-31
Hello everyone - this is my first post.

i am having some troubles sending mail via outlook i can recieve mail just fine

and i can send/recieve from [https://usermin:20000](https://usermin:20000) 

heres what i get in my /var/log/auth.log;

Jan 31 13:39:30 aeisecurity postfix/smtpd[13526]: sql_select option missing
Jan 31 13:39:30 aeisecurity postfix/smtpd[13526]: auxpropfunc error no mechanism available 
Jan 31 13:39:30 aeisecurity postfix/smtpd[13526]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 
Jan 31 13:39:52 aeisecurity postfix/smtpd[13527]: sql_select option missing
Jan 31 13:39:52 aeisecurity postfix/smtpd[13527]: auxpropfunc error no mechanism available 
Jan 31 13:39:52 aeisecurity postfix/smtpd[13527]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 
Jan 31 13:39:53 aeisecurity postfix/smtpd[13528]: sql_select option missing
Jan 31 13:39:53 aeisecurity postfix/smtpd[13528]: auxpropfunc error no mechanism available 
Jan 31 13:39:53 aeisecurity postfix/smtpd[13528]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 

/var/log/mail.log;

Jan 31 14:56:21 aeisecurity postfix/smtpd[15765]: connect from unknown[xx.xx.xx.xx]
Jan 31 14:56:21 aeisecurity postfix/trivial-rewrite[15631]: warning: do not list domain aeisecurity.com in BOTH mydestination and virtual_alias_domains
Jan 31 14:56:21 aeisecurity dovecot: pop3-login: Login: user=<test.aeisecurity>, method=PLAIN, rip=xx.xx.xx.xx, lip=xx.xx.xx.xx
Jan 31 14:56:21 aeisecurity postfix/smtpd[15765]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jan 31 14:56:21 aeisecurity postfix/smtpd[15765]: warning: unknown[xx.xx.xx.xx]: SASL LOGIN authentication failed
Jan 31 14:56:21 aeisecurity postfix/smtpd[15765]: lost connection after AUTH from unknown[xx.xx.xx.xx]
Jan 31 14:56:21 aeisecurity postfix/smtpd[15765]: disconnect from unknown[xx.xx.xx.xx]
Jan 31 14:56:21 aeisecurity dovecot: pop3(test.aeisecurity): Logout. top=0/0, retr=0/ del=0/0, size=0

ive googled this and tried everything - not much applies to my configuration - if anyone can point me in the right direction i would be very greatful

Thanks in advance.

---

### Post by aeisecurity on 2008-02-01
anyone???! :confused:

---

### Post by lmahoney on 2008-02-01
Have you resolved this issue? Can you provide more background such as what steps did you take to configure postfix? Can you post your /etc/postfix/main.cf

---

### Post by aeisecurity on 2008-02-04
Hello thank you for your reply, no the problem still persists, remote access to my fasthosts server is currently down - i will reply with my postfix configurations as soon as possible - the server was configured by virtualmin pro's install.sh - but im getting no support form the virtualmin community/staff

The user accounts are not stored in a mysql database they are all stored as accounts on the system. i dont know why its looking for an sql database

---

### Post by aeisecurity on 2008-02-04
> **aeisecurity said:**
> Hello thank you for your reply, no the problem still persists, remote access to my fasthosts server is currently down - i will reply with my postfix configurations as soon as possible - the server was configured by virtualmin pro's install.sh - but im getting no support form the virtualmin community/staff

The user accounts are not stored in a mysql database they are all stored as accounts on the system. i dont know why its looking for an sql database

here is the configuration...

(i removed comments)

```
#soft_bounce = no
queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
mail_owner = postfix
#default_privs = nobody
#myhostname = host.domain.tld
#myhostname = virtual.domain.tld
#mydomain = domain.tld

#myorigin = $myhostname
#myorigin = $mydomain

#inet_interfaces = all
#inet_interfaces = $myhostname
#inet_interfaces = $myhostname, localhost
#inet_interfaces = all

#proxy_interfaces =
#proxy_interfaces = 1.2.3.4

mydestination = $myhostname, localhost.$mydomain, ubuntu
#mydestination = $myhostname, localhost.$mydomain $mydomain
#mydestination = $myhostname, localhost.$mydomain, $mydomain,
#	mail.$mydomain, www.$mydomain, ftp.$mydomain

#local_recipient_maps = unix:passwd.byname $alias_maps
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
#local_recipient_maps =

#unknown_local_recipient_reject_code = 550
unknown_local_recipient_reject_code = 450

#mynetworks_style = class
#mynetworks_style = subnet
mynetworks_style = host

#mynetworks = 168.100.189.0/28, 127.0.0.0/8
#mynetworks = $config_directory/mynetworks
#mynetworks = hash:/etc/postfix/network_table

#relay_domaixxxns = $mydestination

#relayhost = $mydomain
#relayhost = gateway.my.domain
#relayhost = uucphost
#relayhost = [an.ip.add.ress]

#relay_recipient_maps = hash:/etc/postfix/relay_recipients

#in_flow_delay = 1s

#alias_maps = dbm:/etc/aliases
alias_maps = hash:/etc/aliases
#alias_maps = hash:/etc/aliases, nis:mail.aliases
#alias_maps = netinfo:/aliases

#alias_database = dbm:/etc/aliases
#alias_database = dbm:/etc/mail/aliases
#alias_database = hash:/etc/aliases
#alias_database = hash:/etc/aliases, hash:/opt/majordomo/aliases

#recipient_delimiter = +

#home_mailbox = Mailbox
#home_mailbox = Maildir/
 
#mail_spool_directory = /var/mail
#mail_spool_directory = /var/spool/mail

#mailbox_command = /some/where/procmail
#mailbox_command = /some/where/procmail -a "$EXTENSION"

#mailbox_transport = lmtp:unix:/file/name
#mailbox_transport = cyrus

#fallback_transport = lmtp:unix:/file/name
#fallback_transport = cyrus
#fallback_transport =

#luser_relay = $user@other.host
#luser_relay = $local@other.host
#luser_relay = admin+$local
  
#header_checks = regexp:/etc/postfix/header_checks

#fast_flush_domains = $relay_domains
#fast_flush_domains =

#smtpd_banner = $myhostname ESMTP $mail_name
#smtpd_banner = $myhostname ESMTP $mail_name ($mail_version)

#local_destination_concurrency_limit = 2
#default_destination_concurrency_limit = 20

debug_peer_level = 2

#debug_peer_list = 127.0.0.1
#debug_peer_list = some.domain

debugger_command =
	 PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
	 ddd $daemon_directory/$process_name $process_id & sleep 5

sendmail_path = /usr/sbin/sendmail.postfix
newaliases_path = /usr/bin/newaliases.postfix
mailq_path = /usr/bin/mailq.postfix
setgid_group = postdrop
manpage_directory = /usr/share/man
sample_directory = /usr/share/doc/postfix-2.0.18/samples
readme_directory = /usr/share/doc/postfix-2.0.18/README_FILES
alias_database = hash:/etc/aliases

# Following entries REQUIRED by Matrix control panel
virtual_maps = hash:/etc/postfix/virtual
transport_maps = hash:/etc/postfix/transport
virtual_mailbox_domains = $transport_maps
local_destination_concurrency_limit=1
maildrop_destination_concurrency_limit=1
maildrop_destination_recipient_limit=1
relay_domains=$mydestination $transport_maps
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
home_mailbox = Maildir/
inet_interfaces = all
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_use_tls = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
```

---

### Post by lmahoney on 2008-02-04
Can you post /etc/postfix/sasl/smtpd.conf?

---

### Post by aeisecurity on 2008-02-04
/etc/postfix/sasl/smtp.conf

```
pwcheck_method: saslauthd
mech_list: plain login
```

---

### Post by lmahoney on 2008-02-04
Are you running postfix in chroot? Is saslauthd running?

---

### Post by aeisecurity on 2008-02-04
> **lmahoney said:**
> Are you running postfix in chroot? Is saslauthd running?

saslauthd is running, how do i find out if postfix is running chrooted?

---

### Post by lmahoney on 2008-02-04
Can you add "cyrus_sasl_config_path = /etc/postfix/sasl:/usr/lib/sasl2" and "broken_sasl_auth_clients = yes"  to your /etc/posfix/main.cf file and restart postfix? Also try using telnet to test sending an email. Post the telnet session and your log files.

---

### Post by lmahoney on 2008-02-04
I forgot to ask you to post /etc/default/saslauthd.

---

### Post by aeisecurity on 2008-02-05
This is /etc/default/saslauthd

```
# This needs to be uncommented before saslauthd will be run automatically
START=yes

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

MECHANISMS="pam"
PARAMS="-m /var/spool/postfix/var/run/saslauthd"
```

i cannot telnet to localhost, it just hangs for whatever reason..

but here are the logs when i try and connect from outlook...

/var/log/mail.log

```
Feb  5 10:00:35 aeisecurity postfix/smtpd[31996]: connect from unknown[xx.xx.xx.xx]
Feb  5 10:00:35 aeisecurity postfix/smtpd[31996]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Feb  5 10:00:35 aeisecurity postfix/smtpd[31996]: warning: unknown[xx.xx.xx.xx]: SASL LOGIN authentication failed
Feb  5 10:00:35 aeisecurity postfix/smtpd[31996]: lost connection after AUTH from unknown[xx.xx.xx.xx]
Feb  5 10:00:35 aeisecurity postfix/smtpd[31996]: disconnect from unknown[xx.xx.xx.xx]
```

/var/log/auth.log 

```
Feb  5 10:00:43 aeisecurity postfix/smtpd[32030]: sql_select option missing
Feb  5 10:00:43 aeisecurity postfix/smtpd[32030]: auxpropfunc error no mechanism available 
Feb  5 10:00:43 aeisecurity postfix/smtpd[32030]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 
```

---

### Post by lmahoney on 2008-02-05
Have you had a look at [http://www.postfix.org/SASL_README.html?](http://www.postfix.org/SASL_README.html?) What error is Outlook giving you?

---

### Post by aeisecurity on 2008-02-05
Outlook just hangs when i type in my username and password then it comes back and askes for authentication again - until i click cancel then it tells me the logon was rejected (0x800CCC92)

I will read the link you posted and let post the outcome - thanks.

---

### Post by aeisecurity on 2008-02-06
> **lmahoney said:**
> Have you had a look at [http://www.postfix.org/SASL_README.html?](http://www.postfix.org/SASL_README.html?) What error is Outlook giving you?

i followed that readme now, nothing works :lolflag: (cannot send mail locally or remotly)

---

### Post by aeisecurity on 2008-02-06
sorry guys, im taking the easy way out, backing up now, going to re-install

---

### Post by lmahoney on 2008-02-06
Good luck. Let me know how it goes.

---

### Post by aeisecurity on 2008-02-21
Hello all - just wanted to keep everyone and google up to date on an answer to this problem

it was not easy.. for me atleast :)

the cause was incorrect permissions on the socket file for communication between Postfix and SASLauthd. 

The commands to fix this are :

**warning this is a very specific installation - not all setups will be the same **

rm -r /var/run/saslauthd/
mkdir -p /var/spool/postfix/var/run/saslauthd
ln -s /var/spool/postfix/var/run/saslauthd /var/run
chgrp sasl /var/spool/postfix/var/run/saslauthd
adduser postfix sasl
/etc/init.d/postfix restart

then i had to restart everything and sasl wouldnt start unless i used this command...

/usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a shadow

- I hope this helps anyone

BTW - the re-install did not work at all

---

