---
title: "helo pulls from what sending from postfix? FQDN issue"
date: 2008-10-23
forum: Server Platforms
---

### Post by FawnOfFeist on 2008-10-23
I am getting an error in mail.log

Wondering where the helo=<andsuch> comes from, and what to change to make that say our fqdn

Oct 22 23:25:32 Mailserver2 postfix/smtpd[5112]: NOQUEUE: reject_warning: RCPT from cpe-74-70-80-244.nycap.res.rr.com[74.76.30.251]: 504 5.5.2 <andsuch>: Helo command rejected: need fully-qualified hostname; from=<bryant@stopthat.org> to=<pokefunatme@gmail.com> proto=ESMTP helo=<andsuch>

---

### Post by FawnOfFeist on 2008-10-23
I am of course assuming that is why I am getting the fqdn errors.  IMAP mail being sent through squirrelmail is not having this issue.

---

### Post by MJN on 2008-10-23
As the error suggets, the mail is being rejected because the machine name identified by the HELO command is no fully-qualified. That is, it has only a hostname ('andsuch') and no domain component. Poorly written spambots often fail to do this hence why it is a common anti-spam technique.
 
To fix it, ensure your myhostname in /etc/postfix/main.cf has a domain portion, e.g. andsuch.whateveryourdomainis.com
 
Given you have provided only a fraction of your logs, and no detail on who you are or what you were doing, there is every chance the hostname needs fixing elsewhere.
 
Incidentally, mail sent from Squirrelmail is SMTP just like any other client. IMAP only plays a part in reading mail off a server (i.e. not the delivery of it). Given you say Squirrelmail is able to send mail okay then I am guessing that it is a different client that you are having trouble in which case you need to ensure that client (rather the machine it's on) has a domain component on its hostname.
 
If you want more specific guidance, be more specific with your question. :-)
 
Mathew

---

### Post by FawnOfFeist on 2008-10-23
Here is some more info.  Let me know if you need anything else.

myhostname is commented out (it says because I am using /etc/mailname instead)

/etc/mailname has the FQDN Albpostfix.domain.com

I followed the guide for MTA setup here - [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Here is my postfix -n
root@albpostfix02:/home/dat# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = albpostfix02.domain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = domain.com
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, permit
smtpd_sender_restrictions = permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf


master.cf is as follows

smtp      inet  n       -       -       -       -       smtpd
587       inet  n       -       n       -       -       smtpd
        -o smtpd_enforce_tls=yes
        -o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
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
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

---

### Post by FawnOfFeist on 2008-10-23
Also, I am testing this connecting from Outlook.  I have tried to use the Outgoing server requires authentication, but when I do the message never sends.

I would also like to make it so that the client does need to authenticate, although making it send mail at all is more important at this point.

---

### Post by FawnOfFeist on 2008-10-23
From another machine using Outlook I am no longer getting FQDN errors, but still am not able to relay.  

Error is:
 NOQUEUE: reject: RCPT from static-72-10-198-244.albyny.csvoip.net[72.10.198.244]: 554 5.7.1 <goodkarma@gmail.com>: Relay access denied; from=<Bobby@sampletest.org> to=<goodkarma@gmail.com> proto=ESMTP helo=<meulth>

---

### Post by FawnOfFeist on 2008-10-23
Task 'EMAIL ADDRESS - Sending' reported error (0x800CCC80) : 'None of the authentication methods supported by this client are supported by your server.'

Also getting this from Outlook when trying to authenticate.  I am thinking the relay error is because it is requiring authentication, but now need a solution for why I can't authenticate.

---

### Post by MJN on 2008-10-23
You can't authenticate because you haven't configured any authentication method. You need to go back to your guide...

I was going suggest adding your LAN address range (e.g. 192.168/16 or whatever) to $mynetworks then internal clients would not require any authentication however I note that you are actually connecting to this externally (perhaps via the NAT loopback function of your router) and hence this will not help.

For your FQDN issue either get rid of reject_invalid_hostname restriction or configure the offending client with a proper hostname.

Mathew

---

### Post by FawnOfFeist on 2008-10-24
Here is my smtpd.conf

Where else do I need to specify an authentication method?

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: thisisapassword
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

---

