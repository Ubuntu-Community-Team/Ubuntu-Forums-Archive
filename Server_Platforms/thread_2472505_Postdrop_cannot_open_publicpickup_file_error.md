---
title: "Postdrop cannot open public/pickup file error"
date: 2022-03-01
forum: Server Platforms
---

### Post by yakup83 on 2022-03-01
Hello,

I have an issue to send an email with postfix sendmail on Ubuntu 21.04. ( error mesage specified below)
Has anyone encountered a similar issue? 
I would be happy for any advice or pointers.
Thanks!

OS: Ubuntu 21.04
postfix package: postfix/hirsute-updates 3.5.6-1ubuntu0.2 amd64 [upgradable from: 3.5.6-1]

When I try to send mail with postfix provided sendmail I get the following error:

```
sendmail -vvv myemail@example.org </tmp/test_mail.txt #domain is the same as postfix $domain 
                          ... # verbose output omitted
postdrop: fifo_trigger: open public/pickup: cannot open file: No such device or address
postdrop: send attr status = 0
postdrop: send attr reason = 
postdrop: vstream_fflush_some: fd 1 flush 18
sendmail: vstream_buf_get_ready: fd 5 got 18
sendmail: /usr/sbin/postdrop -r -v -v -v: wanted attribute: status
sendmail: input attribute name: status
sendmail: input attribute value: 0
sendmail: /usr/sbin/postdrop -r -v -v -v: wanted attribute: (list terminator)
sendmail: input attribute name: reason
sendmail: input attribute value: (end)
sendmail: /usr/sbin/postdrop -r -v -v -v: wanted attribute: (list terminator)
sendmail: input attribute name: (end)
```

Pickup fifo in fact exists:
```
root@bastion:~# ls -l /var/spool/postfix/public/pickup
prw-rw-rw- 1 postfix postfix 0 Feb 24 12:29 /var/spool/postfix/public/pickup
```

I tried also a variant with unix socket instead of fifo, but got the same error (only unix_trigger instead of fifo_trigger).

Following is my configuration (domain and IPs anonymized):

```
root@bastion:~# postconf -n
alias_maps = hash:/etc/aliases
command_directory = /usr/sbin
content_filter =
daemon_directory = /usr/lib/postfix
debug_peer_level = 2
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin xxgdb $daemon_directory/$process_name $process_id & sleep 5
defer_transports =
disable_dns_lookups = yes
disable_vrfy_command = yes
header_checks = pcre:/etc/postfix/header_checks
html_directory = /usr/share/doc/packages/postfix/html
inet_interfaces = 127.0.0.1
mail_owner = postfix
mail_spool_directory = /var/spool/mail
mailbox_command =
mailbox_size_limit = 0
mailbox_transport =
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
masquerade_classes = envelope_sender, header_sender, header_recipient
masquerade_domains = example.org
masquerade_exceptions = root
message_size_limit = 28000000
mime_header_checks = pcre:/etc/postfix/header_checks
mydestination = $myhostname, localhost.$mydomain
mydomain = example.org
myhostname = bastion.example.org
mynetworks = 127.0.0.0/8, X.X.X.X/16, X.X.X.X/26 canonical_maps = hash:/etc/postfix/canonical virtual_maps = hash:/etc/postfix/virtual relocated_maps = hash:/etc/postfix/relocated transport_maps = hash:/etc/postfix/transport sender_canonical_maps = hash:/etc/postfix/sender_canonical
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/packages/postfix/README_FILES
relayhost = [mail.eclipse.org]
sample_directory = /usr/share/doc/packages/postfix/samples
sendmail_path = /usr/sbin/sendmail
setgid_group = maildrop
smtp_sasl_auth_enable = no
smtp_use_tls = no
smtpd_client_restrictions =
smtpd_helo_required = yes
smtpd_helo_restrictions =
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination, reject_invalid_hostname, reject_unauth_pipelining, reject_non_fqdn_sender, reject_unknown_recipient_domain, permit
smtpd_sasl_auth_enable = no
smtpd_sender_restrictions = reject_non_fqdn_sender,reject_unknown_sender_domain,reject_invalid_hostname
smtpd_use_tls = no
strict_rfc821_envelopes = no
unknown_local_recipient_reject_code = 550
```

content of master.cf 

```
root@bastion:~# grep -v -E "^#|^$" /etc/postfix/master.cf 
smtp      inet  n       -       n       -       -       smtpd
submission    inet  n       -       n       -       -       smtpd 
 -o smtpd_sasl_auth_enable=yes
 -o smtpd_tls_security_level=may
 -o smtpd_tls_wrappermode=yes
 -o content_filter=smtp-amavis:[127.0.0.1]:10026
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       n       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       n       -       -       trivial-rewrite
bounce    unix  -       -       n       -       0       bounce
defer     unix  -       -       n       -       0       bounce
trace     unix  -       -       n       -       0       bounce
verify    unix  -       -       n       -       1       verify
flush     unix  n       -       n       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       n       -       -       smtp
relay     unix  -       -       n       -       -       smtp
showq     unix  n       -       n       -       -       showq
error     unix  -       -       n       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
scache    unix  -       -       n       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
uucp      unix    -    n    n    -    -    pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=foo argv=/usr/local/sbin/bsmtp -f $sender $nexthop $recipient
vscan     unix  -       n       n       -       10       pipe
  user=vscan argv=/usr/sbin/amavis ${sender} ${recipient}
procmail  unix  -       n       n       -       -       pipe
  flags=R user=nobody argv=/usr/bin/procmail -t -m /etc/procmailrc ${sender} ${recipient}
discard      unix    -    -    n    -    -    discard
smtp-amavis unix -     -      n      -      4  smtp
     -o smtp_send_xforward_command=yes
     -o smtp_data_done_timeout=1200
     -o disable_dns_lookups=yes
127.0.0.1:10025 inet n  -      n      -     -  smtpd
     -o content_filter=
     -o smtpd_delay_reject=no
     -o smtpd_client_restrictions=permit_mynetworks,reject
     -o smtpd_helo_restrictions=
     -o smtpd_sender_restrictions=
     -o smtpd_recipient_restrictions=permit_mynetworks,reject
     -o smtpd_data_restrictions=reject_unauth_pipelining
     -o smtpd_end_of_data_restrictions=
     -o smtpd_restriction_classes=
     -o mynetworks=127.0.0.0/8
     -o smtpd_error_sleep_time=0
     -o smtpd_soft_error_limit=1001
     -o smtpd_hard_error_limit=1000
     -o smtpd_client_connection_count_limit=0
     -o smtpd_client_connection_rate_limit=0
     -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
     -o local_header_rewrite_clients=
retry     unix  -       -       n       -       -       error
proxywrite unix -       -       n       -       1       proxymap
```

All the solutions I found online have pointed to configuration change I already have in place i.e.

```
pickup    fifo  n       -       -       60      1       pickup
```

or 

```
pickup    unix  n       -       -       60      1       pickup
```

Any idea?

---

### Post by MAFoElffen on 2022-03-07
I don't claim to know much about postfix. I just saw this unanswered. so looked up the error, and looked at causes and solutions to...

When I looked up that error, what I found from users (in common) who got that error was that a lot of them had previous versions of postfix installed, and when they reinstalled or upgraded versions then it somehow messed up the named pipes.

On the common fix that they used, try:
```

sudo service sendmail stop
sudo service sendmail disable
## create/redo the missing postfix directory named pipe
sudo mkfifo /var/spool/postfix/public/pickup
## check to see if the previous was successful
ps aux | grep mail
kill
sudo service postfix restart

```
Then send a test email to see if it works.

---

