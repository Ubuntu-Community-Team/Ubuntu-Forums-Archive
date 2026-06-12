---
title: "Postfix cant connect"
date: 2010-06-12
forum: Server Platforms
---

### Post by thamathar on 2010-06-12
Hi ppl, im having some problems whit postfix. Im geting a mensage from the mail.info and mail.log like this:

mail.info
```

Jun 12 17:00:01 owdasy postfix/smtpd[15367]: connect from localhost[127.0.0.1]
Jun 12 17:00:01 owdasy postfix/smtpd[15367]: lost connection after CONNECT from localhost[127.0.0.1]
Jun 12 17:00:01 owdasy postfix/smtpd[15367]: disconnect from localhost[127.0.0.1]

```mail.log
```

Jun 12 16:57:48 owdasy postfix/smtp[14331]: connect to 127.0.0.1[127.0.0.1]:10024: Connection refused
Jun 12 16:57:48 owdasy postfix/smtp[14332]: connect to 127.0.0.1[127.0.0.1]:10024: Connection refused
Jun 12 16:57:48 owdasy postfix/smtp[14331]: B05D9102F2B: to=<ant.reis@gmail.com>, relay=none, delay=4686, delays=4686/0.01/0/0, dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
Jun 12 16:57:48 owdasy postfix/smtp[14331]: connect to 127.0.0.1[127.0.0.1]:10024: Connection refused
Jun 12 16:57:48 owdasy postfix/smtp[14332]: A688A100CAD: to=<ant.reis@gmail.com>, relay=none, delay=4427, delays=4427/0.02/0/0, dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
Jun 12 16:57:48 owdasy postfix/smtp[14331]: 83D47102F35: to=<ant.reis@gmail.com>, relay=none, delay=4210, delays=4210/0.11/0.01/0, dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)

```main.cf
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
body_checks = regexp:/etc/postfix/body_checks
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
header_checks = regexp:/etc/postfix/header_checks
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_size_limit = 0
message_size_limit = 0
mime_header_checks = regexp:/etc/postfix/mime_header_checks
mydestination = owdasy.no-ip.org, localhost, locahost.$mydomain
mydomain = owdasy.no-ip.org
mynetworks = 127.0.0.0/8# [::1]/128
myorigin = /etc/mailname
nested_header_checks = regexp:/etc/postfix/nested_header_checks
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
receive_override_options = no_address_mappings
recipient_delimiter = +
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = maildrop
virtual_uid_maps = static:5000

```

Have all ports for the email open, even i have added them on the iptables

Thanks for the help.

---

### Post by thamathar on 2010-06-12
No one ? :confused:

---

### Post by karesmakro on 2010-06-12
Hey!
Whats about your relayhost?
[quote="mail.log"]B05D9102F2B: to=<ant.reis@gmail.com>, relay=none, ... [/quote]

You forgot, to fill the relayhost in main.cf
```
relayhost = example.org
```
or is it a standalone mailserver?

**Edit:** please provide your master.cf!

---

### Post by thamathar on 2010-06-12
I did, is on the code below main.cf,

I have seen and its empty.

I have done this, by following the manual on the howtoforge, for the ubuntu server 10.04.

The main server is owdasy.no-ip.org, should i put it there ?

The acount that im trying to send or recive emails is another one, one from the Virtual user that have the host name reistic.no-ip.org.

Thanks for the help :D

---

### Post by karesmakro on 2010-06-13
If this is a internet relay server, the relayhost must be empty (is it an internet relay?), otherwise there should be your providers mail relay!


What I need to help you, is the "master.cf"!
There should be a treatment for your virtual_transport section!

---

### Post by thamathar on 2010-06-13
Here it is:

```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d vmail ${extension} ${recipient} ${user} ${nexthop} ${sender}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


amavis unix - - - - 2 smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes

127.0.0.1:10025 inet n - - - - smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_client_restrictions=
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o mynetworks=127.0.0.0/8
        -o strict_rfc821_envelopes=yes
        -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
        -o smtpd_bind_address=127.0.0.1


```

---

### Post by karesmakro on 2010-06-13
The "connection refused" comes from your content filter!
You should check your amavis settings and if service is running!
Both files main.cf and master.cf seems to be o.k. (hope you have a new line in your master.cf?)
What shows
```
lsof -Pni | grep amavis
```?

---

### Post by thamathar on 2010-06-13
```

root@owdasy:/etc/postfix# lsof -Pni | grep amavis
amavisd-n  1428   amavis    5u  IPv4   6542      0t0  TCP 127.0.0.1:10024 (LISTEN)
amavisd-n  1579   amavis    5u  IPv4   6542      0t0  TCP 127.0.0.1:10024 (LISTEN)
amavisd-n  1579   amavis   13u  IPv4 113411      0t0  TCP 127.0.0.1:60435->127.0.0.1:3306 (ESTABLISHED)
amavisd-n  1580   amavis    5u  IPv4   6542      0t0  TCP 127.0.0.1:10024 (LISTEN)
amavisd-n  1580   amavis   13u  IPv4 113553      0t0  TCP 127.0.0.1:60437->127.0.0.1:3306 (ESTABLISHED)

```

---

### Post by karesmakro on 2010-06-13
Where are your amavis logs? Can you please debug amavis?
Try to set this in amavisd.conf:
```
$log_level = 2;              
$log_recip_templ = undef;    
$DO_SYSLOG = 1;         
$syslog_facility = 'mail';   
$syslog_priority = 'debug';
```
restart amavis,try to send a mail again and post the log entries

---

### Post by thamathar on 2010-06-13
Cant find that file at /etc/amavis/

---

### Post by karesmakro on 2010-06-13
if you can not find amavisd.conf in /etc you can use the config
20-debian_defaults (or 20-ubuntu_defaults, not sure what's in ubuntu) in /etc/amavis/conf.d

---

### Post by thamathar on 2010-06-13
Humm i have made some changes on the main.cf while i was waiting and now im sending emails and reciving them, but when i try to send and recive from hotmail.com i get this error:

```

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<[camadas@hotmail.com]("http://owdasy.no-ip.org/webmail/src/compose.php?send_to=camadas%40hotmail.com")>: host mx1.hotmail.com[65.55.37.120] said: 550 DY-001 Mail
    rejected by Windows Live Hotmail for policy reasons. We generally do not
    accept email from dynamic IP's as they are not typically used to deliver
    unauthenticated SMTP e-mail to an Internet mail server.
    [http://www.spamhaus.org]("http://www.spamhaus.org/") maintains lists of dynamic and residential IP
    addresses. If you are not an email/network admin please contact your
    E-mail/Internet Service Provider for help. Email/network admins, please
    visit [http://postmaster.live.com]("http://postmaster.live.com/") for email delivery information and support
    (in reply to MAIL FROM command)


```I was having the same problem whit gmail, but i have change the:

mynetworks = 192.168.1.66/8 [::1]/128 to mynetworks = 192.0.0.0/8 [::1]/128

And i start sending emails to and from gmail to me.

This should be the public ip or the lan one ? Since my public IP isnt static.

EDIT.

Since that change im geting this errors on the mail.warm

```

Jun 13 11:22:46 owdasy postfix/smtpd[8959]: warning: ::1: address not listed for hostname localhost
Jun 13 11:22:46 owdasy postfix/smtpd[8959]: warning: table "mysql:/etc/postfix/mysql-virtual_client.cf": empty query string -- ignored
Jun 13 11:22:46 owdasy postfix/smtpd[8959]: warning: table "mysql:/etc/postfix/mysql-virtual_client.cf": empty query string -- ignored
Jun 13 11:25:01 owdasy postfix/smtpd[10832]: warning: ::1: address not listed for hostname localhost
Jun 13 11:26:58 owdasy postfix/smtpd[10832]: warning: ::1: address not listed for hostname localhost
Jun 13 11:26:58 owdasy postfix/smtpd[10832]: warning: table "mysql:/etc/postfix/mysql-virtual_client.cf": empty query string -- ignored
Jun 13 11:30:01 owdasy postfix/smtpd[13131]: warning: ::1: address not listed for hostname localhost
```

---

### Post by karesmakro on 2010-06-13
did you commented out the content_filter for testing?
This is a big problem with hotmail, gmail and some other providers, as you need a rDNS entry for ipaddress! Perhaps your dynamic dns provider has an option for this?
This means, your ipaddress should always point to your DNS entry and this is not possible with a non static ipaddress!
```
We generally do not accept email from dynamic IP's
```

---

### Post by thamathar on 2010-06-13
Nop i didn't comment it :/

---

### Post by thamathar on 2010-06-13
It is posseble to make a script when the ip change, it would update the main.cf whit the new IP ?

This way would be like having a static ip

---

### Post by karesmakro on 2010-06-13
> This should be the public ip or the lan one ?
normally should be both [noparse](and 127.0.0.1/8)[/noparse], but never tried something with dynamic ipaddresses

in addition: I would make a research on internet for getting a mailserver running with dynamic ipaddress, because I'm not sure, how to handle - sorry!

---

### Post by lisati on 2010-06-13
Apologies for jumping in late in this discussion. 

I had a similar error message on my email server after tinkering with the amavis settings a week or two back. I had made a typo in one of the cofiguration files, and only discovered what the problem was by carefully inspecting the mail.log file, during which I discovered a warning. After this the problem was easily fixed.

---

### Post by thamathar on 2010-06-13
> **karesmakro said:**
> normally should be both [noparse](and 127.0.0.1/8)[/noparse], but never tried something with dynamic ipaddresses

in addition: I would make a research on internet for getting a mailserver running with dynamic ipaddress, because I'm not sure, how to handle - sorry!

Could u show me a main.cf like u have told ? that it should contain both ?

THanks

---

### Post by karesmakro on 2010-06-13
The ipaddresses must be space seperated, e.g. like:
```
mynetworks = 127.0.0.1/8 192.168.2.0/24 <puplic_ip/32>
```

I'm out of office for a short time!

---

### Post by thamathar on 2010-06-13
Thanks i will try it :D

---

### Post by thamathar on 2010-06-13
I did have to restart the PC, and now i get this error:

```

Jun 13 12:31:10 owdasy postfix/smtpd[26912]: warning: ::1: address not listed for hostname localhost
Jun 13 12:31:10 owdasy postfix/smtpd[26912]: connect from unknown[::1]
Jun 13 12:31:10 owdasy postfix/smtpd[26912]: warning: table "mysql:/etc/postfix/mysql-virtual_client.cf": empty query string -- ignored
Jun 13 12:31:10 owdasy postfix/smtpd[26912]: NOQUEUE: reject: RCPT from unknown[::1]: 554 5.7.1 <ant.reis@gmail.com>: Relay access denied; from=<antonioreis@reistic.no-ip.org> to=<ant.reis@gmail.com> proto=ESMTP helo=<owdasy.no-ip.org>
Jun 13 12:31:10 owdasy postfix/smtpd[26912]: lost connection after RCPT from unknown[::1]
Jun 13 12:31:10 owdasy postfix/smtpd[26912]: disconnect from unknown[::1]

```main.cf ( is what i have been changing all the time )
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = owdasy
mydomain = owdasy.no-ip.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = owdasy.no-ip.org, localhost, locahost.$mydomain
relayhost = 
mynetworks = 127.0.0.1/8 192.168.1.66/24 188.81.44.228/32
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0

```

Now i cant send and recive emails, even i have change to the way that it ways and cant :/

---

### Post by karesmakro on 2010-06-13
If you are using ipv6, you should also include the [::1]/128 to mynetworks, like:
```
mynetworks = [::1]/128 127.0.0.1/8 ....
```

and there must be a hosts entry like
```
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
is your mysql-virtual_client.cf empty?

please also set debug_peer_level to 2 or similiar! This would give you a better overview, what went wrong in your configuration
```
debug_peer_level = 2
```

in addition, I recommend you, to read this
[http://www.postfix.org/IPV6_README.html](http://www.postfix.org/IPV6_README.html)

---

### Post by thamathar on 2010-06-13
my /etc/hosts

```

root@owdasy:/home/camadas# cat /etc/hosts
127.0.0.1    localhost.localdomain    localhost
192.168.1.66    owdasy.no-ip.org    owdasy
192.0.0.0     owdasy.no-ip.org    owdasy
#127.0.0.7    owdasy.no-ip.org

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```mysql-virtual_client.cf
```

root@owdasy:/etc/postfix# cat mysql-virtual_client.cf 
user = ispconfig
password = XXXXXXXXXXXXXXXXXXXX
dbname = dbispconfig
table        = mail_access
select_field = access
where_field  = source
additional_conditions = and type = 'client' and active = 'y'
hosts = 127.0.0.1

```were i set that debug lvl ?


EDIT:

Now i can recive email's but i cant send them

i get this error when im trying to send them:

```

Jun 13 14:25:11 owdasy postfix/smtpd[18394]: connect from localhost.localdomain[127.0.0.1]
Jun 13 14:25:11 owdasy postfix/smtpd[18394]: 380A2102F30: client=localhost.localdomain[127.0.0.1]
Jun 13 14:25:11 owdasy postfix/cleanup[18382]: 380A2102F30: message-id=<c1420dca26b903450493b7e746b5d51d.squirrel@owdasy.no-ip.org>
Jun 13 14:25:11 owdasy postfix/qmgr[18254]: 380A2102F30: from=<antonioreis@reistic.no-ip.org>, size=1177, nrcpt=1 (queue active)
Jun 13 14:25:11 owdasy postfix/smtpd[18394]: disconnect from localhost.localdomain[127.0.0.1]
Jun 13 14:25:11 owdasy amavis[1662]: (01662-16) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <antonioreis@reistic.no-ip.org> -> <ant.reis@gmail.com>, Message-ID: <c1420dca26b903450493b7e746b5d51d.squirrel@owdasy.no-ip.org>, mail_id: cS4dxEyo3VI0, Hits: -1, size: 738, queued_as: 380A2102F30, 936 ms
Jun 13 14:25:11 owdasy postfix/smtp[18383]: 4CD9E1024CC: to=<ant.reis@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1, delays=0.09/0/0/0.94, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01662-16, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 380A2102F30)
Jun 13 14:25:11 owdasy postfix/qmgr[18254]: 4CD9E1024CC: removed
Jun 13 14:25:11 owdasy postfix/smtp[18544]: warning: relayhost configuration problem
Jun 13 14:25:11 owdasy postfix/smtp[18544]: 380A2102F30: to=<ant.reis@gmail.com>, relay=none, delay=0.57, delays=0.09/0.03/0.44/0, dsn=4.3.5, status=deferred (mail for owdasy.no-ip.org loops back to myself)
Jun 13 14:25:28 owdasy postfix/smtpd[18371]: disconnect from mail-bw0-f53.google.com[209.85.214.53]

```

---

### Post by karesmakro on 2010-06-13
in main.cf

---

### Post by thamathar on 2010-06-13
> **karesmakro said:**
> in main.cf

Done

```

Jun 13 14:32:46 owdasy postfix/cleanup[22124]: 716C5102FB4: message-id=<dba8e750d4148b02c009a251f431589d.squirrel@owdasy.no-ip.org>
Jun 13 14:32:46 owdasy postfix/qmgr[21958]: 716C5102FB4: from=<antonioreis@reistic.no-ip.org>, size=1177, nrcpt=1 (queue active)
Jun 13 14:32:46 owdasy postfix/smtpd[22136]: disconnect from localhost.localdomain[127.0.0.1]
Jun 13 14:32:46 owdasy amavis[20679]: (20679-02) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <antonioreis@reistic.no-ip.org> -> <ant.reis@gmail.com>, Message-ID: <dba8e750d4148b02c009a251f431589d.squirrel@owdasy.no-ip.org>, mail_id: Hrv3qkG-vOHS, Hits: -1, size: 738, queued_as: 716C5102FB4, 691 ms
Jun 13 14:32:46 owdasy postfix/smtp[22126]: BD061102FA5: to=<ant.reis@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.85, delays=0.14/0.02/0/0.69, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=20679-02, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 716C5102FB4)
Jun 13 14:32:46 owdasy postfix/qmgr[21958]: BD061102FA5: removed
Jun 13 14:32:46 owdasy postfix/smtp[21961]: warning: relayhost configuration problem
Jun 13 14:32:46 owdasy postfix/smtp[21961]: 716C5102FB4: to=<ant.reis@gmail.com>, relay=none, delay=0.31, delays=0.13/0/0.18/0, dsn=4.3.5, status=deferred (mail for owdasy.no-ip.org loops back to myself

```

---

### Post by karesmakro on 2010-06-13
Normally the error "mail of ... loops back to myself" comes from wrong entries in the virtual alias maps (and if you try to send an email to a local user)
[http://www.seaglass.com/postfix/faq.html#erlpbk](http://www.seaglass.com/postfix/faq.html#erlpbk)
your domain shouldn't be in the virtual alias maps

and please delete all unnecessary whitespaces like
```
user=ispconfig
```
and not 
```
user = ispconfig
``` as a whitespace in parameters is interpreted as a end of line!

Edit: forget the whitespaces, this is correct!

---

### Post by thamathar on 2010-06-13
Now i have fix the problem of sending emails from my server to gmail, is working now, but now i can't send from gmail to my server -.- this was working and now it isn't

---

### Post by karesmakro on 2010-06-13
What did you changed?
Any log entries?
I suspect, your "mydestination" is wrong!

correct the loca**l**host in this line!

---

### Post by thamathar on 2010-06-13
> **karesmakro said:**
> What did you changed?
Any log entries?
I suspect, your "mydestination" is wrong!

correct the loca**l**host in this line!


Like this:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = $mydomain

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

myhostname = owdasy
mydomain = owdasy.no-ip.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = owdasy.no-ip.org, localhost, locahost.$mydomain
relayhost = 
mynetworks =  127.0.0.0/8 192.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0
debug_peer_level = 2

```

?

---

### Post by karesmakro on 2010-06-13
sorry, I ment this line:
```
mydestination = owdasy.no-ip.org, localhost, locahost.$mydomain
```
were you has written locahost.$mydomain, instead of loca [SIZE="3"]**l**[/SIZE] host.$mydomain

---

### Post by thamathar on 2010-06-13
> **karesmakro said:**
> sorry, I ment this line:
```
mydestination = owdasy.no-ip.org, localhost, locahost.$mydomain
```were you has written locahost.$mydomain, instead of loca [SIZE=3]**l**[/SIZE] host.$mydomain

Hehe no.

Its done, but i still just cant send emails now, i cant recive them any more, don't know why. I dont get any error on the log's.

I'm testing true my gmail acount, i can recive them from my server to the gmail, but if i send from the gmail to my server, or hotmail i dont recive them.

I dont get any error :/

---

### Post by karesmakro on 2010-06-13
Is there no log entry about connections from hotmail or gmail?

Is your DNS pointing to your public ipaddress? (nslookup or use dig)
and than, you have to check the settings by your dns provider no-ip.org

---

### Post by thamathar on 2010-06-13
> **karesmakro said:**
> Is there no log entry about connections from hotmail or gmail?

Is your DNS pointing to your public ipaddress? (nslookup or use dig)
and than, you have to check the settings by your dns provider no-ip.org

On the No-ip.org is all at 100%, i have the script from them to update every 2 min my IP. And im using the webmail from my server, so yep on no-ip.org is ok.

How do i use nslookup or dig ? I never use does command's

---

### Post by karesmakro on 2010-06-13
This is a howto, to use [dig]("http://www.madboa.com/geek/dig/")
but a ```
nslookup owdasy.no-ip.org
```
does it for you!

please also try 
```
telnet owdasy.no-ip.org 25
``` and once for your local ipaddress

Nice help to check for example a rDNS entry would be
```
dig example.org MX +noall +answer
```

---

### Post by thamathar on 2010-06-13
nslookup owdasy.no-ip.org
```

root@owdasy:/etc/courier# nslookup owdasy.no-ip.org
Server:        192.168.1.254
Address:    192.168.1.254#53

Non-authoritative answer:
Name:    owdasy.no-ip.org
Address: 188.81.44.228

```

---

### Post by thamathar on 2010-06-17
Hi there, just come to say that now is everything working, and want to thank u guys for your time that u took to help me out :D

Thanks :D

:guitar:

---

### Post by karesmakro on 2010-06-17
Thanks for feedback, but I think, it would be nice for other people who has the same problem, to post your solution :)

---

### Post by thamathar on 2010-06-17
> **karesmakro said:**
> Thanks for feedback, but I think, it would be nice for other people who has the same problem, to post your solution :)

What i did mainly was working on the main.cf, i did so many thing's that i dont know what i did, i think this is right :P.

What i think it the mainly thing to put it at work was the IP address that i have put on the main.cf file.

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = owdasy.no-ip.org
mydomain = no-ip.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = owdasy.no-ip.org, localhost.$mydomain
relayhost = 
mynetworks = 127.0.0.0/8 192.168.1.0/24 192.168.1.102/32 PUBLICIP/32
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0
```

I have put the server in the hometown, were is DHCP IP, but if i dont get DC, the ip will allways be mine, i have the same for about 2 years now, so i think is the best for it.

The main change that i did was on mynetworks =

I put the localhost ip, the "netmask" of the intranet were the server is, the Intranet IP of the server, then the public address.

Remenber if an part of the IP is 0, like 127.0.0.0 is must be /8, each of the 4 takes 8 bit's.

P.S. I hope that this will help future ppl whit the same problem. 
P.S2. Change the PUBLICIP do your internet ip address.

---

