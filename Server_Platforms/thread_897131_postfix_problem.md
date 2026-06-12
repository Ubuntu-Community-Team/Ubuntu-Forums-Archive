---
title: "postfix problem"
date: 2008-08-21
forum: Server Platforms
---

### Post by stim on 2008-08-21
Hello, I am attempting to set up a mail server on my home machine.  Currently I have Ubuntu 8.04 apache2, modjk and tomcat.  

I followed [this]("http://ubuntuforums.org/showthread.php?t=40047") guide.

I stepped through it and got it somewhat up and running except that I am unable to receive mail.  I forwarded the port on my router and allowed it from the firewall.  

stim@stim-laptop:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
status0
^at this point, it does not respond to keyboard input, it must be killed from another process.

However, I can send mail using the 'mail' command, and it works both to users on the system (i.e. root@localhost) and external accounts.  

I feel that I may have buggered up a .cf file so I will post them first, and some log info.  If any of you have any suggestions I would really appreciate it.  This is the first time I have attempted to set up a mail server.

If you need any more information I will gladly provide it. Thanks again.



**main.cf**
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
 
 
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname 
 
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
 
# appending .domain is the MUA's job.
append_dot_mydomain = no
 
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
 
readme_directory = no
 
# TLS parameters
smtp_tls_security_level = may 
smtpd_tls_security_level = may 
smtp_tls_note_starttls_offer = yes 
smtpd_tls_loglevel = 1 
smtpd_tls_received_header = yes 
 
smtpd_tls_session_cache_timeout = 3600s 
tls_random_source = dev:/dev/urandom 
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
 
myhostname = stimrob.ath.cx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = stimrob.ath.cx,stim-laptop,localhost.localdomain,localhost
relayhost = smtp.comcast.net 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
masquerade_domans = stim.ath.cx
masquerade_exceptions = root
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
 
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
 
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
virtual_mailbox_base = /var/spool/mail/virtual 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf 
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 
content_filter = amavis:[127.0.0.1]:10024
```
 
**master.cf**
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
smtp      inet  n       -       n       -       -       smtpd
submission inet n       -       n       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtp     inet  n       -       n       -       -       smtp
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
 
#smtpd_client_restrictions=reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
#-o smtpd_client_restrictions=permit_assl_authenticated,reject_unauth_destination, reject 
#-o smtpd_sasl_security_options=noanonymous,noplaintext 
#-o smtpd_sasl_tls_security_options=noanonymous
#smtp inet n - - - - smtp  
#-o smtpd_tls_wrappermode=yes 
#-o smtpd_sasl_auth_enable=yes 
#-o smtpd_tls_auth_only=yes 
#-o smtpd_client_restrictions=permit_sasl_authenticated,reject 
#-o smtpd_sasl_security_options=noanonymous,noplaintext 
#-o smtpd_sasl_tls_security_options=noanonymous 
 
 
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
#-o content_filter= 
 #    -o receive_override_options=no_header_body_checks
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
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
 
amavis unix - - n - 2 smtp 
 -o smtp_data_done_timeout=1200 
 -o smtp_send_xforward_command=yes 
 -o disable_dns_lookups=yes 
 -o max_use=20
 
127.0.0.1:10025 inet n - - - - smtpd 
 -o content_filter= 
 -o local_recipient_maps= 
 -o relay_recipient_maps= 
 -o smtpd_restriction_classes= 
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
 -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```
**mail.log when I telnet in**
```
Aug 21 20:08:18 stim-laptop postfix/master[7971]: reload configuration /etc/postfix
Aug 21 20:08:15 stim-laptop dovecot: Time just moved backwards by 4 seconds. I'll sleep now until we're back in present. [http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)
Aug 21 20:08:20 stim-laptop dovecot: pop3-login: Time just moved backwards by 3 seconds. I'll sleep now until we're back in present. [http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)
Aug 21 20:08:20 stim-laptop last message repeated 2 times
Aug 21 20:08:20 stim-laptop dovecot: auth(default): Time just moved backwards by 2 seconds. I'll sleep now until we're back in present. [http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)
Aug 21 20:38:27 stim-laptop postfix/smtp[25518]: warning: unexpected end-of-input from smtp socket while reading input attribute name
Aug 21 20:38:27 stim-laptop postfix/smtp[25518]: warning: deliver_request_get: error receiving common attributes
Aug 21 21:00:14 stim-laptop postfix/smtp[25785]: warning: unexpected end-of-input from smtp socket while reading input attribute name
Aug 21 21:00:14 stim-laptop postfix/smtp[25785]: warning: deliver_request_get: error receiving common attributes
```

**mail.warn**
```
Aug 21 20:38:27 stim-laptop postfix/smtp[25518]: warning: unexpected end-of-input from smtp socket while reading input attribute name
Aug 21 20:38:27 stim-laptop postfix/smtp[25518]: warning: deliver_request_get: error receiving common attributes
Aug 21 21:00:14 stim-laptop postfix/smtp[25785]: warning: unexpected end-of-input from smtp socket while reading input attribute name
Aug 21 21:00:14 stim-laptop postfix/smtp[25785]: warning: deliver_request_get: error receiving common attributes
```

---

### Post by PerJensen on 2008-08-22
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

specifies you only accept mail from localhost (what does the IPv6 state ?)

Add the networks you want to relay mail for to the "mynetworks"

For example mynetworks = 127.0.0.1, 192.168.1.0/24

/Per

---

### Post by windependence on 2008-08-22
Well, if you don't want to spend a week or two configuring your MTA and your POP3 or IMAP server, and just want something easy to load and go, then you should try a full package like Zimbra or Citadel. Installs in minutes and just works.

Of course, if you just want to learn, then by all means knock yourself out, but I can tell you from experience it generally isn't fun unless you like that kind of stuff. I'm a pretty big nerd myself but I avoid building mail servers from scratch like the plague.

-Tim

---

### Post by stim on 2008-08-22
So I scrapped my original plan and went with citadel. 
I used the web 'easy' install. Unfortunately the documentation seems to really leave a lot to be desired.  I am running apache2 and tomcat with modjk.  
[http://www.citadel.org/doku.php/faq:installation:apacheproxy](http://www.citadel.org/doku.php/faq:installation:apacheproxy)
Can someone explain this a little better? Especially the second part about the proxy......where do I enter those caommands.  

I can telnet into the imap, smtp ports, the processes are running etc.....now how can I create a user and test sending email?  I assume thats what 'webcit' is, but there seems to be almost ZERO documentation on how to get that working.  
Any help?  This is turning into a pain....
P.S. Where are the relevant log files?


Edit:I can log on to the service at port 2000, but I get this message.

This program was unable to connect or stay connected to the Citadel server. Please report this problem to your system administrator.Read More...

I restarted the server and got this message when I tried to log in on port 2000 above:


```

root@stim-laptop:/# webcit start
WebCit 7.37
Copyright (C) 1996-2008 by the Citadel development team.
This software is distributed under the terms of the GNU General Public License.

Configured available locale: C
Configured available locale: en_US.UTF8
Error configuring locale for de_DE.UTF8: No such file or directory
Error configuring locale for it_IT.UTF8: No such file or directory
Error configuring locale for es_ES.UTF8: No such file or directory
Configured available locale: en_GB.UTF8
Error configuring locale for da_DK.UTF8: No such file or directory
Error configuring locale for fr_FR.UTF8: No such file or directory
Error configuring locale for nl_NL.UTF8: No such file or directory
Error configuring locale for pt_BR.UTF8: No such file or directory
Message catalog directory: /usr/share//locale
Text domain: webcit
Text domain Charset: UTF8
Changing directory to /var/run/citadel/
Attempting to bind to port 2000...
Listening on socket 4
Creating a new thread
Creating a new thread
Creating a new thread
Creating a new thread
Creating a new thread
HTTP: GET / HTTP/1.1
Creating a new session
language found: en_US
Can't get start host entry: Connection timed out
Server connection broken: Bad file descriptor
Server connection broken: Bad file descriptor
Server connection broken: Bad file descriptor
Server connection broken: Bad file descriptor
Server connection broken: Bad file descriptor
Destroying session 1219416207
```

---

### Post by windependence on 2008-08-22
If you think Citadel is tough, it would have been much worse getting your MTA and POP3 server working right, trust me.

Here is some info on installing Citadel I dug up. 

[http://www.nettiki.com/?q=node/271](http://www.nettiki.com/?q=node/271) (mostly installing a VMware appliance)

Personally, I prefer Zimbra. You should give it a shot if you don't mind testing. Great docs from them as well as from the web. Here are a few good ones:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu](http://www.howtoforge.com/zimbra-integration-with-samba-on-ubuntu)

If you need help with Zimbra, I would be glad to assist. For help with Citadel, look for HermannAB here on the forums.

-Tim

---

### Post by stim on 2008-08-22
Installing zimbra. Will let you know how it goes.
Thanks again for your help, I really appreciate it.

---

### Post by HermanAB on 2008-08-22
Don't run Citadel together with Apache.  Citadel has its own web server (based on Apache I believe) called Webcit.

Here is a Citadel guide:
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

Cheers,

Herman

---

### Post by stim on 2008-08-24
Is there a main server that is LAMP + tomcat friendly?
Most of the zimbra stuff I have read said not to install them together.  Thanks for your help.

---

### Post by windependence on 2008-08-25
That's because Zimbra installs it's own Tomcat server. Zimbra is best if it's the only thing on the machine, that's why I usually deploy it in a VM.

-Tim

---

### Post by stim on 2008-08-25
So from what I gather, there's no easy way to run a LAMP server and e-mail system at the same time.  That's weak. 

This is going to sound real dumb:
How can I tell if I'm running the Server Edition of Hardy instead of the regular desktop edition.  I was pretty sure I had the server edition but it didn't ask me to install any software packages like apache or mail when I installed it.
Any help?

---

### Post by windependence on 2008-08-25
Well for one you won't have a GUI installed by default with the server edition. If you have a GUI, it's desktop.

-Tim

---

