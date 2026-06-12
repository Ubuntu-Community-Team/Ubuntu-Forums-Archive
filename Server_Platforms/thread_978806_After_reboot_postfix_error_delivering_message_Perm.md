---
title: "After reboot postfix error delivering message: Permission denied"
date: 2008-11-11
forum: Server Platforms
---

### Post by smullie on 2008-11-11
Hallo frends,

I use Ubuntu server 8.04.
Mail has worked fine till yesterday. I rebooted the server after adding some harddisks to it.
Put the new disks in raid5 ( i had already raid 1 settings)
I update always (automaticly), so perhaps an old update is bugging me?


On recieving mail, Error message:
maildir delivery failed: create maildir file /home/richard/Maildir/tmp/1226422563.P13974.rvs001.ri-vier.nl: Permission denied

I can send mail, no problems
I have not change the permissions of something.
I have tried to set 777 to complete home dir, but no succes.
I have tried other users, also the same type of error.

postconf -n:
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
header_checks = regexp:/etc/postfix/header_checks
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
masquerade_domains = $mydomain
message_size_limit = 52428800
mydestination = rvs001.ri-vier.nl, localhost.ri-vier.nl, , localhost, rvs001, ri-vier.nl, ri-4.nl
myhostname = rvs001.ri-vier.nl
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = Ri-Vier_MailServer ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,check_policy_service inet:127.0.0.1:60000
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

Who can help me out here, can't find the solution of the problem.

---

### Post by MJN on 2008-11-11
Are you running any element of Postfix chrooted? (if you're not sure post the contents of /etc/postfix/master.cf)

Also, what are the permissions of /home/richard/Maildir/tmp and every folder above it to the root? (ls -ld for each)

Mathew

---

### Post by smullie on 2008-11-11
Hallo Mathew,

Permissions of /home/richard and below are 700
user:group = richard:richard
All other users are similar.
I have not changed any permissions on directory's

Also the config files are not altered by me.

Master.cf:
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
#autoresponse line hier onder 1 regel
   -o content_filter=autoresponder:dummy
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
#628      inet  n       -       -       -       -       qmqpd
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
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop}$
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
#autoresponse line hier onder 2 regels
autoresponder unix - n n - - pipe
   #flags=Fq user=autoresponse argv=/usr/local/sbin/autoresponse -s ${sender} -$
   flags=Fq user=www-data argv=/usr/local/sbin/autoresponse -s ${sender} -r ${r$

Postfix is running chrootet, as far as i know.

Smullie.

---

### Post by MJN on 2008-11-11
> **smullie said:**
> Permissions of /home/richard and below are 700
user:group = richard:richard
All other users are similar.

Please don't interpret the permissions, just post the **ls -ld** output as there is a danger of misunderstanding creeping in.

As the user 'richard' can you create a file within tmp e.g. **touch ~richard/Maildir/tmp/test**   without any problem?

> Postfix is running chrootet, as far as i know.It's not, at least for local delivery which is what we're concerned with here.

Postfix stores mail with the permissions of the recipient hence we need to work out why 'richard' can create a file (the touch test above) but Postfix, acting as 'richard', cannot.

Mathew

---

### Post by smullie on 2008-11-12
Hallo Mathew,

I understand.
It is not only the user richard, it's with all users!
You ask if i was running any element of Postfix chrooted, there i though it was, and not only the local.

For you info, i have deleted and removed apparmor after setup the base server 6 months ago, so i think that is not an issue, but you never know....
I also tought that the postfix was running as root?
I have tried with permissions set to home/richard as 777, that run was also not working.
It looks like postfix puts it in another directory, but the eror message shows the correct one.

But here the answers:
I can create as user richard a file (touch test in tmp dir).

ls -ld
home: drwxr-x--- 19 root media
home/richard: drwxr-x--- 26 richard richard
home/richard/Maildir: drwxr-x--- 21 richard richard
home/richard/Maildir/tmp: drwxr-x--- 2 richard richard

Hope this helps....

---

### Post by MJN on 2008-11-12
I must admit, I'm stumped.
 
Postfix doesn't run as root - it runs at whatever level and with whatever permissions is required for each particular task. Hence, for local mail delivery (dropping mail into users' mailboxes) it impersonates the user the mail is for. Hence, in your case it runs as 'richard' thus should be able to create mail inside your mailbox.
 
Given the above, setting the permissions to 777 will not help - indeed it's a bad idea all round anyway (Postfix used to complain if it even saw you had this).
 
> It looks like postfix puts it in another directory, but the eror message shows the correct one.What do you mean by this?
 
You could try adding -v to the end of the 'local' line in master.cf - I'm not sure if this is an allowable option but hopefully it will increase the verbosity of its logging and potentially shed some light on what it's having trouble writing to the mailbox.
 
Mathew

---

### Post by smullie on 2008-11-12
I mee that if i put 777 it is world useable, and sould not be a problem, so perhaps, postfix tells us it write there, but it write somewere else where the user has no rights. It is just a thought.

I have put the -v as you have asked.
Grab the local stuff from te syslogfile:


Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  mail
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  all
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: all
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  rvs001.ri-vier.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  ri-vier.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  Postfix
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  postfix
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  postfix
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  postdrop
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  rvs001.ri-vier.nl, localhost.ri-vier.nl, localhost, rvs001, ri-vier.nl, ri-4.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  /etc/mailname
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  /usr/lib/postfix
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  /var/lib/postfix
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  /usr/sbin
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  /var/spool/postfix
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  pid
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  all
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  double-bounce
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  nobody
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  hash:/etc/aliases
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  20080216
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  2.5.1
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  hash
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  deferred, defer
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  +
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: expand $mydestination -> rvs001.ri-vier.nl, localhost.ri-vier.nl, localhost, rvs001, 

ri-vier.nl, ri-4.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: expand $relay_domains -> rvs001.ri-vier.nl, localhost.ri-vier.nl, localhost, rvs001, 

ri-vier.nl, ri-4.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  TZ MAIL_CONFIG LANG
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  subnet
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  +=
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  -=+
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  

debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  bounce
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  cleanup
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  defer
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  pickup
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  qmgr
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  rewrite
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  showq
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  error
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  flush
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  verify
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  trace
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  52428800
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  100s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  3600s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  3600s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  5s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  5s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1000s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1000s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  10s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  10s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  500s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  500s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  18000s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  18000s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
Nov 12 13:30:26 rvs001 postfix/local[6908]: inet_addr_local: configured 3 IPv4 addresses
Nov 12 13:30:26 rvs001 postfix/local[6908]: inet_addr_local: configured 2 IPv6 addresses
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  0
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  hash:/etc/aliases
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  Maildir/
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  alias, forward
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  alias, forward
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  /var/mail
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  canonical, virtual
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  command, file, forward
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  fcntl, dotlock
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  no
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1000s
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_eval: const  1000s
Nov 12 13:30:26 rvs001 postfix/local[6908]: process generation: 14 (14)
Nov 12 13:30:26 rvs001 postfix/local[6908]: Compiled against Berkeley DB: 4.6.21?
Nov 12 13:30:26 rvs001 postfix/local[6908]: Run-time linked against Berkeley DB: 4.6.21?
Nov 12 13:30:26 rvs001 postfix/local[6908]: dict_open: hash:/etc/aliases
Nov 12 13:30:26 rvs001 postfix/local[6908]: match_string: fast_flush_domains ~? debug_peer_list
Nov 12 13:30:26 rvs001 postfix/local[6908]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 12 13:30:26 rvs001 postfix/local[6908]: set_eugid: euid 108 egid 116
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: alias
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: forward
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: alias
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: forward
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: canonical
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: virtual
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: command
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: file
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: forward
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: fcntl
Nov 12 13:30:26 rvs001 postfix/local[6908]: name_mask: dotlock
Nov 12 13:30:26 rvs001 postfix/local[6908]: connection established
Nov 12 13:30:26 rvs001 postfix/local[6908]: master_notify: status 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_request_initial: send initial status
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr status = 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: flags
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: flags
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 3
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: queue_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: queue_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: active
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: queue_id
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: queue_id
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 5208720090BC
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: offset
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: offset
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 238
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: size
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: size
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 4391
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: nexthop
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: nexthop
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: rvs001.ri-vier.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: encoding
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: encoding
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: sender
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: sender
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: [email]richard.mulder@mapperlithography.com[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: envelope_id
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: envelope_id
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: ret_flags
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: ret_flags
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: time
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: time
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 

WMwaSQAAAACs8AwAAAAAAGLMGkkAAAAALf0GAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: log_client_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: log_client_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: log_client_address
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: log_client_address
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: log_client_port
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: log_client_port
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: log_protocol_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: log_protocol_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: log_helo_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: log_helo_name
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: sasl_method
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: sasl_method
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: sasl_username
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: sasl_username
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: sasl_sender
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: sasl_sender
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: rewrite_context
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: rewrite_context
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: remote
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: recipient_count
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: recipient_count
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 1
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: (list terminator)
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: original_recipient
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: original_recipient
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: [email]richard@ri-vier.nl[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: recipient
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: recipient
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: [email]richard@ri-vier.nl[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: offset
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: offset
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 216
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: dsn_orig_rcpt
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: dsn_orig_rcpt
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: notify_flags
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: notify_flags
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: local socket: wanted attribute: (list terminator)
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_request_get: file active/5208720090BC
Nov 12 13:30:26 rvs001 postfix/local[6908]: local_deliver: 5208720090BC from [email]richard.mulder@mapperlithography.com[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: local_deliver[0]: reset owner attr
Nov 12 13:30:26 rvs001 postfix/local[6908]: local_deliver[0]: reset user_attr
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_recipient[1]: local  recip [email]richard@ri-vier.nl[/email] exten  deliver  exp_from 
Nov 12 13:30:26 rvs001 postfix/local[6908]: been_here: recipient 1 [email]richard@ri-vier.nl[/email]: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: level: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: path: active/5208720090BC
Nov 12 13:30:26 rvs001 postfix/local[6908]: fp: 0x6205c0
Nov 12 13:30:26 rvs001 postfix/local[6908]: queue_name: active
Nov 12 13:30:26 rvs001 postfix/local[6908]: queue_id: 5208720090BC
Nov 12 13:30:26 rvs001 postfix/local[6908]: offset: 216
Nov 12 13:30:26 rvs001 postfix/local[6908]: sender: [email]richard.mulder@mapperlithography.com[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: recipient: [email]richard@ri-vier.nl[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: domain: ri-vier.nl
Nov 12 13:30:26 rvs001 postfix/local[6908]: local: richard
Nov 12 13:30:26 rvs001 postfix/local[6908]: user: richard
Nov 12 13:30:26 rvs001 postfix/local[6908]: extension: null
Nov 12 13:30:26 rvs001 postfix/local[6908]: unmatched: null
Nov 12 13:30:26 rvs001 postfix/local[6908]: owner: null
Nov 12 13:30:26 rvs001 postfix/local[6908]: delivered: [email]richard@ri-vier.nl[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: relay: local
Nov 12 13:30:26 rvs001 postfix/local[6908]: exp_type: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: exp_from: null
Nov 12 13:30:26 rvs001 postfix/local[6908]: why: buffer
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_switch[2]: local richard recip [email]richard@ri-vier.nl[/email] exten  deliver [email]richard@ri-vier.nl[/email] exp_from 
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_alias[3]: local richard recip [email]richard@ri-vier.nl[/email] exten  deliver [email]richard@ri-vier.nl[/email] exp_from 
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_alias: hash:/etc/aliases(0,lock|no_regsub|no_proxy|no_unauth|fold_fix): richard not found
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_dotforward[3]: local richard recip [email]richard@ri-vier.nl[/email] exten  deliver [email]richard@ri-vier.nl[/email] 

exp_from 
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_dotforward[3]: set user_attr: richard
Nov 12 13:30:26 rvs001 postfix/local[6908]: set_eugid: euid 1001 egid 1001
Nov 12 13:30:26 rvs001 postfix/local[6908]: set_eugid: euid 108 egid 116
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_dotforward: path /home/richard/.forward expand_status 0 look_status -1
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_mailbox[3]: local richard recip [email]richard@ri-vier.nl[/email] exten  deliver [email]richard@ri-vier.nl[/email] exp_from 
Nov 12 13:30:26 rvs001 postfix/local[6908]: been_here: mailbox richard: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_mailbox[3]: set user_attr: richard
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_maildir[4]: local richard recip [email]richard@ri-vier.nl[/email] exten  deliver [email]richard@ri-vier.nl[/email] exp_from 
Nov 12 13:30:26 rvs001 postfix/local[6908]: set_eugid: euid 1001 egid 1001
Nov 12 13:30:26 rvs001 postfix/local[6908]: set_eugid: euid 108 egid 116
Nov 12 13:30:26 rvs001 postfix/local[6908]: warning: maildir access problem for UID/GID=1001/1001: create maildir file 

/home/richard/Maildir/tmp/1226493026.P6908.rvs001.ri-vier.nl: Permission denied
Nov 12 13:30:26 rvs001 postfix/local[6908]: warning: perhaps you need to create the maildirs in advance
Nov 12 13:30:26 rvs001 postfix/local[6908]: connect to subsystem private/bounce
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr nrequest = 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr flags = 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr queue_id = 5208720090BC
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr original_recipient = [email]richard@ri-vier.nl[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr recipient = [email]richard@ri-vier.nl[/email]
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr offset = 216
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr dsn_orig_rcpt = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr notify_flags = 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr status = 5.2.0
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr diag_type = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr diag_text = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr mta_type = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr mta_mname = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr action = failed
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr reason = maildir delivery failed: create maildir file 

/home/richard/Maildir/tmp/1226493026.P6908.rvs001.ri-vier.nl: Permission denied
Nov 12 13:30:26 rvs001 postfix/local[6908]: private/bounce socket: wanted attribute: status
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: status
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute value: 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: private/bounce socket: wanted attribute: (list terminator)
Nov 12 13:30:26 rvs001 postfix/local[6908]: input attribute name: (end)
Nov 12 13:30:26 rvs001 postfix/local[6908]: 5208720090BC: to=<richard@ri-vier.nl>, relay=local, delay=9.7, delays=9.6/0.02/0/0.02, dsn=5.2.0, 

status=bounced (maildir delivery failed: create maildir file /home/richard/Maildir/tmp/1226493026.P6908.rvs001.ri-vier.nl: Permission denied)
Nov 12 13:30:26 rvs001 postfix/local[6908]: deliver_request_final: send: "" 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr status = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr diag_type = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr diag_text = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr mta_type = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr mta_mname = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr action = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr reason = 
Nov 12 13:30:26 rvs001 postfix/local[6908]: send attr status = 0
Nov 12 13:30:26 rvs001 postfix/local[6908]: master_notify: status 1
Nov 12 13:30:26 rvs001 postfix/local[6908]: connection closed
Nov 12 13:32:06 rvs001 postfix/local[6908]: idle timeout -- exiting

---

### Post by MJN on 2008-11-12
Hmm... Richard is UID/GID 1001, yes? (check the ownership of ~richard with **ls -n**)
 
It might be worth adding a new user, and seeing if mail can be delivered to them (the Maildir structure should be created by Postfix for you, or it might require an access from the IMAP server to do so). Actually, are you using IMAP? If so can your client move messages between folders okay, and in particular can it move a message into the Inbox?
 
Mathew

---

### Post by smullie on 2008-11-12
The ownership is correct.
I have made a new user, send a mail, but same error, and NO directory's made.

I use IMAP and squirrelmail, but i do not know what you meen and how to move messages between folders.
Before monday all was working fine for 6 months now.
There is someting changed, after the reboot.

---

### Post by MJN on 2008-11-12
> **smullie said:**
> I use IMAP and squirrelmail, but i do not know what you meen and how to move messages between folders.Whilst logged in as richard in Squirrelmail try selecting a message in the Sent folder (for example) and moving it to the Inbox.
 
This will test that the IMAP server is able to at least write to the Inbox, thus pin-pointing the problem to Postfix (and not an obscure filesystem issue relating to your recent disk changes).
 
Mathew

---

### Post by smullie on 2008-11-13
That worked fine, no problems moving mail from one folder to an other.

---

### Post by MJN on 2008-11-13
I'm afraid I'm running out of ideas... (you probably guessed that a couple of posts back!)
 
It could well be something obvious - perhaps so obvious we're overlooking it. But what?
 
You mentioned you used to use AppArmor.. I've not used it myself but I wonder? That said, you said it's now gone...
 
Mathew

---

### Post by smullie on 2008-11-14
In the meentime i have setup a second mailserver and that is working fine.

I will reinstall this server this weekend, and moove stuff of the secondary server to the main server.

I get the feeling that it is not solvable in a short time.

Thanks for your help so far.

please close this tread.

---

