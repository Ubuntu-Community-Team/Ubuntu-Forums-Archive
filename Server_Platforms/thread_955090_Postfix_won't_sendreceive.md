---
title: "Postfix won't send/receive"
date: 2008-10-21
forum: Server Platforms
---

### Post by theman on 2008-10-21
Postfix won't send or receive mail. I have an Ubuntu LAMP server with webmin, procmail, dovecot, postfix, ssh, telnet, and squirrelmail. Comcast sent me an e-mail saying one of my computers was sending out spam and I'm pretty sure they blocked port 25. I need to telnet it.

Here is my mail.log full of errors.


> Oct 21 20:18:30 davidsserver postfix/smtpd[7124]: connect from localhost[127.0.0.1]
Oct 21 20:19:00 davidsserver postfix/cleanup[7128]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:19:01 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7128 exit status 1
Oct 21 20:19:01 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:20:01 davidsserver postfix/cleanup[7130]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:20:02 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7130 exit status 1
Oct 21 20:20:02 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:21:02 davidsserver postfix/cleanup[7131]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:21:03 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7131 exit status 1
Oct 21 20:21:03 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:22:03 davidsserver postfix/cleanup[7133]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:22:04 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7133 exit status 1
Oct 21 20:22:04 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:23:04 davidsserver postfix/cleanup[7134]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:23:05 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7134 exit status 1
Oct 21 20:23:05 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:23:43 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 21 20:23:43 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 21 20:24:06 davidsserver postfix/cleanup[7139]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:24:07 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7139 exit status 1
Oct 21 20:24:07 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:25:07 davidsserver postfix/cleanup[7140]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:25:08 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7140 exit status 1
Oct 21 20:25:08 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling
Oct 21 20:26:08 davidsserver postfix/cleanup[7141]: fatal: open /etc/postfix/header_checks: No such file or directory
Oct 21 20:26:09 davidsserver postfix/master[6403]: warning: process /usr/libexec/postfix/cleanup pid 7141 exit status 1
Oct 21 20:26:09 davidsserver postfix/master[6403]: warning: /usr/libexec/postfix/cleanup: bad command startup -- throttling

Here is my Postfix.conf (I don't understand what some of the settings mean but they look good.) :): 


> #
### Postfix main.cf
#
### Verify these directory settings - they are critical to Postfix operation.
biff = no
recipient_delimiter = .
command_directory = /usr/sbin
daemon_directory = /usr/libexec/postfix
program_directory = /usr/libexec/postfix

### Interface to listen on

### smtp banner
mail_name = davidsserver Daemon
smtpd_banner = $mail_name. All Spam Is Reported. ESMTP

### Who delivers the mail (never root for security).
setgid_group = postdrop

### Default user to deliver mail to (NEVER ENABLE)
luser_relay =

### The myorigin parameter specifies the domain that appears in mail that is posted on/through this machine.
append_dot_mydomain = no
append_at_myorigin = yes

### alias's
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

### the internet hostname of this mail system
myhostname = davidsserver
mydomain=com

### The mydestination parameter specifies what domains this machine will deliver locally, instead
### of forwarding to another machine. The default is to receive mail for the machine itself.
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

### Relay Host this mail server should send its mail to. (NONE)
relayhost = [smtp.comcast.net]

### Relay Client SASL Authentication
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

### External Networks to accept RELAYED mail from.
mynetworks = 127.0.0.0/8

### Where to send mail that is delivered locally.
mailbox_command = procmail -a "$EXTENSION"

### How much of the message in bytes will be bounced back to the sender.
bounce_size_limit = 5000

### No limit on mailbox size.
mailbox_size_limit = 0

### Message Restrictions
header_checks = regexp:/etc/postfix/header_checks

### Limit sent/recieved emails to 1 Meg "(header+body+attachment)x(mime-encoding) <= 1 meg"
message_size_limit = 102400

### How long do messages stay in the queue before being sent back to the sender. (in days)
### By default, postfix attempts to resend the message every (1000 secs)x(# attempts)x(days).
bounce_queue_lifetime = 4h
maximal_queue_lifetime = 4h
delay_warning_time = 1h

### Parrallel delivery force (local=2 and dest=20 are aggressive)
local_destination_concurrency_limit = 2
default_destination_concurrency_limit = 20

### Max flow rate (1 sec delay per 50 emails/sec over the number of emails delivered/sec)
in_flow_delay = 1s

### no one needs to ask our server who is on it
disable_vrfy_command = yes

#### user%domain != user@domain
allow_percent_hack = no

#### user!domain != user@domain
swap_bangpath = no

smtpd_sasl_auth_enable = yes

#####################  END  #####################################################


Here is the original config file I copied from:


> #
### Postfix main.cf
#
### Verify these directory settings - they are critical to Postfix operation.
biff = no
recipient_delimiter = .
command_directory = /usr/sbin
daemon_directory = /usr/libexec/postfix
program_directory = /usr/libexec/postfix

### Interface to listen on

### smtp banner
mail_name = davidsserver Daemon
smtpd_banner = $mail_name. All Spam Is Reported. ESMTP

### Who delivers the mail (never root for security).
setgid_group = postdrop

### Default user to deliver mail to (NEVER ENABLE)
luser_relay =

### The myorigin parameter specifies the domain that appears in mail that is posted on/through this machine.
append_dot_mydomain = no
append_at_myorigin = yes

### alias's
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

### the internet hostname of this mail system
myhostname = davidsserver
mydomain=com

### The mydestination parameter specifies what domains this machine will deliver locally, instead
### of forwarding to another machine. The default is to receive mail for the machine itself.
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

### Relay Host this mail server should send its mail to. (NONE)
relayhost = [smtp.comcast.net]:587

### Relay Client SASL Authentication
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

### External Networks to accept RELAYED mail from.
mynetworks = 127.0.0.0/8

### Where to send mail that is delivered locally.
mailbox_command = procmail -a "$EXTENSION"

### How much of the message in bytes will be bounced back to the sender.
bounce_size_limit = 5000

### No limit on mailbox size.
mailbox_size_limit = 0

### Message Restrictions
header_checks = regexp:/etc/postfix/header_checks

### Limit sent/recieved emails to 1 Meg "(header+body+attachment)x(mime-encoding) <= 1 meg"
message_size_limit = 102400

### How long do messages stay in the queue before being sent back to the sender. (in days)
### By default, postfix attempts to resend the message every (1000 secs)x(# attempts)x(days).
bounce_queue_lifetime = 4h
maximal_queue_lifetime = 4h
delay_warning_time = 1h

### Parrallel delivery force (local=2 and dest=20 are aggressive)
local_destination_concurrency_limit = 2
default_destination_concurrency_limit = 20

### Max flow rate (1 sec delay per 50 emails/sec over the number of emails delivered/sec)
in_flow_delay = 1s

### clients must send a HELO (or EHLO) command at the beginning of an SMTP session.
smtpd_helo_required = yes

### no one needs to ask our server who is on it
disable_vrfy_command = yes

#### user%domain != user@domain
allow_percent_hack = no

#### user!domain != user@domain
swap_bangpath = no

### delay until RCPT TO: to reject the email for nagios compatability

### Tarpit those bots/clients/spammers who send errors or scan for accounts !!!!
smtpd_error_sleep_time = 20
smtpd_soft_error_limit = 4
smtpd_hard_error_limit = 6
smtpd_junk_command_limit = 4

### Reject codes (change these as you see fit)
access_map_reject_code = 450
invalid_hostname_reject_code = 450
maps_rbl_reject_code = 450
multi_recipient_bounce_reject_code = 450
non_fqdn_reject_code = 450
plaintext_reject_code = 450
reject_code = 450
relay_domains_reject_code = 450
unknown_address_reject_code = 450
unknown_client_reject_code = 450
unknown_hostname_reject_code = 450
unknown_local_recipient_reject_code = 450
unknown_relay_recipient_reject_code = 450
unknown_virtual_alias_reject_code = 450
unknown_virtual_mailbox_reject_code = 450
unverified_recipient_reject_code = 450
unverified_sender_reject_code = 450

### SMTP Restrictions
smtpd_client_restrictions = permit_mynetworks,
                                reject_invalid_hostname,
                                check_client_access regexp:/etc/postfix/client_restrictions
                                reject_rbl_client zen.spamhaus.org,
                                reject_unknown_client,
                                permit

smtpd_helo_restrictions = permit_mynetworks,
                                check_helo_access hash:/etc/postfix/helo_access,
                                reject_unauth_pipelining,
                                reject_non_fqdn_hostname,
                                reject_invalid_hostname,
                                permit

smtpd_recipient_restrictions = permit_mynetworks reject_non_fqdn_sender reject_non_fqdn_recipient reject_non_fqdn_hostname reject_invalid_hostname reject_unauth_pipelining reject_rbl_client zen.spamhaus.org reject_unknown_sender_domain reject_unknown_recipient_domain reject_unauth_destination reject_unknown_client permit

smtpd_sender_restrictions =  permit_mynetworks,
                                reject_non_fqdn_sender,
                                reject_unknown_sender_domain,
                                reject_unknown_address,
                                permit

smtpd_etrn_restrictions = permit_mynetworks,
                                reject

smtpd_data_restrictions = reject_unauth_pipelining,
                                reject_multi_recipient_bounce,
                                permit

#####################  END  #####################################################

---

### Post by MJN on 2008-10-22
Any Postfix error prefixed with 'fatal' is generally serious enough to bring the whole thing down...
 
```
Oct 21 20:19:00 davidsserver postfix/cleanup[7128]: fatal: open /etc/postfix/header_checks: No such file or directory
```
 
Does /etc/postfix/header_checks exist? If not, why is it referenced in main.cf? Either create that file with your desired contents or scrap the header checking line.
 
Mathew

---

### Post by theman on 2008-10-22
Thanks that helped a lot but it gives me these messages back and it won't send mail. I called Comcast and they said I have no ports blocked.

Here is my mail.log:

> ct 22 16:17:43 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:17:43 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:17:44 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:17:44 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:17:44 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:17:44 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:20:27 davidsserver postfix/qmgr[4445]: DBFDE822B5: from=<david@davidsserver.com>, size=747, nrcpt=1 (queue active)
Oct 22 16:20:39 davidsserver postfix/smtp[5453]: DBFDE822B5: to=<*@hotmail.com>, relay=smtp.comcast.net[76.96.30.117]:587, delay=2979, delays=2968/0.07/0.72/10, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.30.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 16:23:08 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:23:08 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:23:10 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:23:10 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:23:13 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:23:13 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:24:02 davidsserver postfix/smtpd[5467]: connect from localhost[127.0.0.1]
Oct 22 16:24:02 davidsserver postfix/smtpd[5467]: EBB66822C8: client=localhost[127.0.0.1]
Oct 22 16:24:03 davidsserver postfix/cleanup[5470]: EBB66822C8: message-id=<2133.192.168.1.100.1224707042.squirrel@davidsserver>
Oct 22 16:24:03 davidsserver postfix/qmgr[4445]: EBB66822C8: from=<david@davidsserver.com>, size=713, nrcpt=1 (queue active)
Oct 22 16:24:03 davidsserver postfix/smtpd[5467]: disconnect from localhost[127.0.0.1]
Oct 22 16:24:03 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:24:03 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:24:03 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:24:03 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:24:14 davidsserver postfix/smtp[5471]: EBB66822C8: to=<*@comcast.net>, relay=smtp.comcast.net[76.96.30.117]:587, delay=11, delays=0.14/0.07/0.82/10, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.30.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 16:24:18 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:24:18 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:24:18 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:24:18 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:24:20 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:24:20 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:24:21 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:24:21 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:25:27 davidsserver postfix/qmgr[4445]: AA056822CC: from=<david@davidsserver.com>, size=715, nrcpt=1 (queue active)
Oct 22 16:25:35 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:25:35 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:25:47 davidsserver postfix/smtp[5494]: AA056822CC: to=<*@yahoo.com>, relay=smtp.comcast.net[76.96.62.117]:587, delay=2197, delays=2177/0.04/0.23/20, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.62.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 16:26:40 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:26:40 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:26:53 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:26:53 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:26:57 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:26:57 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:28:41 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:28:41 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 16:30:27 davidsserver postfix/qmgr[4445]: EBB66822C8: from=<david@davidsserver.com>, size=713, nrcpt=1 (queue active)
Oct 22 16:30:27 davidsserver postfix/qmgr[4445]: 3BC28822D3: from=<david@davidsserver.com>, size=713, nrcpt=1 (queue active)
Oct 22 16:30:27 davidsserver postfix/qmgr[4445]: 967F8822C4: from=<david@davidsserver.com>, size=733, nrcpt=1 (queue active)
Oct 22 16:30:49 davidsserver postfix/smtp[5542]: EBB66822C8: to=<*@comcast.net>, relay=smtp.comcast.net[76.96.62.117]:587, delay=406, delays=384/0.33/0.22/22, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.62.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 16:30:49 davidsserver postfix/smtp[5544]: 967F8822C4: to=<*@yahoo.com>, relay=smtp.comcast.net[76.96.62.117]:587, delay=3319, delays=3297/0.22/0.23/22, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.62.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 16:31:28 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 16:31:28 davidsserver dovecot: IMAP(david): Disconnected: Logged out


---

### Post by MJN on 2008-10-22
Is davidsserver.com your real domain name? If so, it doesn't have any MX records (or fallback A record) and so you certainly won't receive any mail for that domain.

For outgoing, the 452 code seems like a problem at Comcast's end. Try disabling smtp_sasl_auth_enable to satisfy yourself that authentication is occuring properly. Alternatively, try adding -vv to the end of the smtp line in master.cf, restart, then watch the logs when a message is sent - you'll get a whole load of dialogue captured and most importantly will be able to see each command (and response).

You could also try disabling your relayhost directive too in order to send direct. Sure, if you're on a dynamic IP then you'll suffer from spamtraps but at least you'll be able to rule out Comcast by seeing if you can deliver mail to other servers.

Mathew

---

### Post by theman on 2008-10-22
I disabled sasl in both the main and master and I get the same response. I'm not clear on where exactly to put -vv.

---

### Post by MJN on 2008-10-22
Just modify the smtp line in /etc/postfix/master.cf to read:

```
smtp      inet  n       -       -       -       -       smtpd -vv
```..then restart Postfix.

Mathew

---

### Post by theman on 2008-10-22
same thing really

> Oct 22 17:45:06 davidsserver postfix/smtpd[5414]: connect from localhost[127.0.0.1]
Oct 22 17:45:06 davidsserver postfix/smtpd[5414]: 092FC822E7: client=localhost[127.0.0.1]
Oct 22 17:45:06 davidsserver postfix/cleanup[5417]: 092FC822E7: message-id=<3151.192.168.1.100.1224711906.squirrel@davidsserver>
Oct 22 17:45:06 davidsserver postfix/qmgr[5325]: 092FC822E7: from=<david@davidsserver.com>, size=714, nrcpt=1 (queue active)
Oct 22 17:45:06 davidsserver postfix/smtpd[5414]: disconnect from localhost[127.0.0.1]
Oct 22 17:45:06 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 17:45:06 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 17:45:06 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 17:45:06 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 17:45:17 davidsserver postfix/postfix-script[5427]: refreshing the Postfix mail system
Oct 22 17:45:17 davidsserver postfix/master[4440]: reload configuration /etc/postfix
Oct 22 17:45:17 davidsserver postfix/qmgr[5432]: 092FC822E7: skipped, still being delivered
Oct 22 17:45:17 davidsserver postfix/qmgr[5432]: 20AA2822D5: from=<david@davidsserver.com>, size=724, nrcpt=1 (queue active)
Oct 22 17:45:28 davidsserver postfix/smtp[5434]: 20AA2822D5: to=<*@yahoo.com>, relay=smtp.comcast.net[76.96.30.117]:587, delay=1391, delays=1380/0.04/0.67/10, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.30.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 17:45:30 davidsserver postfix/smtp[5418]: 092FC822E7: to=<*@yahoo.com>, relay=smtp.comcast.net[76.96.62.117]:587, delay=25, delays=0.07/0.07/0.48/24, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.62.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: syslog_facility = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: mail
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  mail
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: syslog_facility = mail
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: inet_protocols = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: ipv4
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  ipv4
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: inet_protocols = ipv4
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: name_mask: ipv4
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myhostname = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydomain = com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_name = davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: syslog_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: syslog_name = postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_owner = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: mail_owner = postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: setgid_group = postdrop
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: postdrop
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  postdrop
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $myhostname, localhost.$mydomain, localhost, $mydomain
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myhostname = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydomain = com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydomain = com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $myhostname, localhost.$mydomain, localhost, $mydomain -> davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myorigin = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $myhostname
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myhostname = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $myhostname -> davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: myorigin = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: relayhost = [smtp.comcast.net]:587
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: [smtp.comcast.net]:587
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  [smtp.comcast.net]:587
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: daemon_directory = /usr/libexec/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: /usr/libexec/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  /usr/libexec/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: data_directory = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: /var/lib/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  /var/lib/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: data_directory = /var/lib/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: command_directory = /usr/sbin
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: /usr/sbin
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  /usr/sbin
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: queue_directory = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: /var/spool/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  /var/spool/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: queue_directory = /var/spool/postfix
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: process_id_directory = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: pid
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  pid
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: process_id_directory = pid
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: inet_interfaces = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: all
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  all
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: inet_interfaces = all
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: proxy_interfaces = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: proxy_interfaces = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: double_bounce_sender = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: double_bounce_sender = double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: default_privs = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: nobody
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  nobody
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: default_privs = nobody
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: alias_database = hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_release_date = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 20080216
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  20080216
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: mail_release_date = 20080216
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_version = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: mail_version = 2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: default_database_type = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: hash
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  hash
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: default_database_type = hash
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: hash_queue_names = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: deferred, defer
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  deferred, defer
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: hash_queue_names = deferred, defer
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: recipient_delimiter = .
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: .
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  .
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: relay_domains = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $mydestination
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $myhostname, localhost.$mydomain, localhost, $mydomain
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myhostname = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydomain = com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mydomain = com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $mydestination -> davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: relay_domains = davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: fast_flush_domains = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $relay_domains
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: relay_domains = davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $relay_domains -> davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: fast_flush_domains = davidsserver.com, localhost.com, localhost, com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: export_environment = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: TZ MAIL_CONFIG LANG
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  TZ MAIL_CONFIG LANG
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: export_environment = TZ MAIL_CONFIG LANG
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: import_environment = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: import_environment = MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mynetworks_style = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: subnet
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  subnet
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: mynetworks_style = subnet
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: debug_peer_list = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: debug_peer_list = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: default_verp_delimiters = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: +=
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  +=
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: default_verp_delimiters = +=
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: verp_delimiter_filter = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: -=+
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  -=+
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: verp_delimiter_filter = -=+
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: parent_domain_matches_subdomains = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: parent_domain_matches_subdomains = debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: alternate_config_directories = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: alternate_config_directories = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: bounce_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: bounce_service_name = bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: cleanup_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: cleanup
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  cleanup
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: cleanup_service_name = cleanup
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: defer_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: defer
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  defer
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: defer_service_name = defer
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: pickup_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: pickup
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  pickup
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: pickup_service_name = pickup
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: queue_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: qmgr
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  qmgr
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: queue_service_name = qmgr
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: rewrite_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: rewrite
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  rewrite
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: rewrite_service_name = rewrite
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: showq_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: showq
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  showq
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: showq_service_name = showq
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: error_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: error
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  error
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: error_service_name = error
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: flush_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: flush
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  flush
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: flush_service_name = flush
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: address_verify_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: verify
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  verify
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: address_verify_service_name = verify
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: trace_service_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: trace
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  trace
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: trace_service_name = trace
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: internal_mail_filter_classes = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: internal_mail_filter_classes = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: max_use = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: max_use = 100
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: dont_remove = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: dont_remove = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: line_length_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: line_length_limit = 2048
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: message_size_limit = 102400
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 102400
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  102400
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: hash_queue_depth = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: hash_queue_depth = 1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: fork_attempts = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: fork_attempts = 5
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: deliver_lock_attempts = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: deliver_lock_attempts = 20
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: debug_peer_level = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: debug_peer_level = 2
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: fault_injection_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: fault_injection_code = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: berkeley_db_create_buffer_size = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: berkeley_db_create_buffer_size = 16777216
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: berkeley_db_read_buffer_size = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: berkeley_db_read_buffer_size = 131072
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: header_size_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: header_size_limit = 102400
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: header_address_token_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: header_address_token_limit = 10240
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mime_nesting_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: mime_nesting_limit = 100
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mime_boundary_length_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: mime_boundary_length_limit = 2048
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: delay_logging_resolution_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: delay_logging_resolution_limit = 2
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: disable_dns_lookups = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: disable_dns_lookups = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: soft_bounce = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: soft_bounce = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: owner_request_special = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: owner_request_special = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: strict_8bitmime = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: strict_8bitmime = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: strict_7bit_headers = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: strict_7bit_headers = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: strict_8bitmime_body = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: strict_8bitmime_body = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: strict_mime_encoding_domain = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: strict_mime_encoding_domain = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: disable_mime_input_processing = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: disable_mime_input_processing = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: disable_mime_output_conversion = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: disable_mime_output_conversion = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: address_verify_negative_cache = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: address_verify_negative_cache = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: backwards_bounce_logfile_compatibility = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: backwards_bounce_logfile_compatibility = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: helpful_warnings = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: helpful_warnings = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: send_cyrus_sasl_authzid = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: send_cyrus_sasl_authzid = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: application_event_drain_time = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: application_event_drain_time = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: application_event_drain_time = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: max_idle = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: max_idle = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: max_idle = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: ipc_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: ipc_timeout = 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: ipc_timeout = 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 5s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  5s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: ipc_idle = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: ipc_idle = 5s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: ipc_idle = 5s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 5s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  5s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: ipc_ttl = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: ipc_ttl = 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: ipc_ttl = 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 10s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  10s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: trigger_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: trigger_timeout = 10s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: trigger_timeout = 10s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 10s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  10s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: fork_delay = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: fork_delay = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: fork_delay = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: deliver_lock_delay = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: deliver_lock_delay = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: deliver_lock_delay = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 500s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  500s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: stale_lock_time = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: stale_lock_time = 500s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: stale_lock_time = 500s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 500s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  500s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 18000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  18000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: daemon_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: daemon_timeout = 18000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: daemon_timeout = 18000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 18000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  18000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: in_flow_delay = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: in_flow_delay = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mynetworks = 127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: inet_addr_list_append: 127.0.0.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: inet_addr_list_append: 255.0.0.0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: inet_addr_list_append: 192.168.1.151
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: inet_addr_list_append: 255.255.255.0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: inet_addr_local: configured 2 IPv4 addresses
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: process_id = 5441
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_recipient_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_recipient_limit = 1000
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_soft_error_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_soft_error_limit = 10
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_hard_error_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_hard_error_limit = 20
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: queue_minfree = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: queue_minfree = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_client_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_client_reject_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: invalid_hostname_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: invalid_hostname_reject_code = 501
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_hostname_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_hostname_reject_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_address_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_address_reject_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: relay_domains_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: relay_domains_reject_code = 554
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: maps_rbl_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: maps_rbl_reject_code = 554
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: access_map_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: access_map_reject_code = 554
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: reject_code = 554
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: defer_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: defer_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: non_fqdn_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: non_fqdn_reject_code = 504
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_junk_command_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_junk_command_limit = 100
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_recipient_overshoot_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_recipient_overshoot_limit = 1000
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_history_flush_threshold = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_history_flush_threshold = 100
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unverified_sender_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unverified_sender_reject_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unverified_recipient_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unverified_recipient_reject_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: multi_recipient_bounce_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: multi_recipient_bounce_reject_code = 550
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_local_recipient_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_local_recipient_reject_code = 550
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_virtual_alias_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_virtual_alias_reject_code = 550
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_virtual_mailbox_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_virtual_mailbox_reject_code = 550
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: unknown_relay_recipient_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: unknown_relay_recipient_reject_code = 550
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: plaintext_reject_code = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: plaintext_reject_code = 450
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: address_verify_poll_count = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: address_verify_poll_count = 3
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_connection_rate_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_connection_rate_limit = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_connection_count_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_connection_count_limit = 50
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_message_rate_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_message_rate_limit = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_recipient_rate_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_recipient_rate_limit = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_new_tls_session_rate_limit = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_new_tls_session_rate_limit = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_ccert_verifydepth = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_ccert_verifydepth = 9
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_loglevel = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_loglevel = 0
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_banner = $mail_name. All Spam Is Reported. ESMTP
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $mail_name. All Spam Is Reported. ESMTP
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_name = davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $mail_name. All Spam Is Reported. ESMTP -> davidsserver Daemon. All Spam Is Reported. ESMTP
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: notify_classes = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: resource, software
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  resource, software
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: notify_classes = resource, software
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_restrictions = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_helo_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_helo_restrictions = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sender_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sender_restrictions = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_recipient_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: permit_mynetworks, reject_unauth_destination
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  permit_mynetworks, reject_unauth_destination
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_etrn_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_etrn_restrictions = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_data_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_data_restrictions = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_end_of_data_restrictions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_end_of_data_restrictions = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: maps_rbl_domains = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: maps_rbl_domains = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: rbl_reply_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: rbl_reply_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: error_notice_recipient = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: postmaster
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  postmaster
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: error_notice_recipient = postmaster
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_restriction_classes = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_restriction_classes = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: canonical_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: canonical_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: recipient_canonical_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: recipient_canonical_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: virtual_alias_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $virtual_maps
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: virtual_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $virtual_maps -> 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: virtual_alias_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: virtual_mailbox_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: virtual_mailbox_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: alias_maps = hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: local_recipient_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: proxy:unix:passwd.byname $alias_maps
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: alias_maps = hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand proxy:unix:passwd.byname $alias_maps -> proxy:unix:passwd.byname hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: local_recipient_maps = proxy:unix:passwd.byname hash:/etc/aliases
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_security_options = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_security_options = noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_path = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: smtpd
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  smtpd
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_path = smtpd
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: cyrus_sasl_config_path = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: cyrus_sasl_config_path = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_local_domain = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_local_domain = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_exceptions_networks = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_exceptions_networks = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: content_filter = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: content_filter = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: permit_mx_backup_networks = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: permit_mx_backup_networks = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sender_login_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sender_login_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_noop_commands = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_noop_commands = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_forbidden_commands = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: CONNECT GET POST
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  CONNECT GET POST
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_forbidden_commands = CONNECT GET POST
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_null_access_lookup_key = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: <>
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  <>
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_null_access_lookup_key = <>
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: relay_recipient_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: relay_recipient_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: address_verify_sender = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $double_bounce_sender
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: double_bounce_sender = double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $double_bounce_sender -> double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: address_verify_sender = double-bounce
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_authorized_verp_clients = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $authorized_verp_clients
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: authorized_verp_clients = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $authorized_verp_clients -> 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_authorized_verp_clients = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_proxy_filter = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_proxy_filter = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_proxy_ehlo = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $myhostname
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myhostname = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $myhostname -> davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_proxy_ehlo = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: receive_override_options = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: receive_override_options = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_authorized_xclient_hosts = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_authorized_xclient_hosts = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_authorized_xforward_hosts = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_authorized_xforward_hosts = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_event_limit_exceptions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: ${smtpd_client_connection_limit_exceptions:$mynetworks}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_connection_limit_exceptions = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $mynetworks
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mynetworks = 127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand ${smtpd_client_connection_limit_exceptions:$mynetworks} -> 127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_event_limit_exceptions = 127.0.0.0/8
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: local_header_rewrite_clients = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: permit_inet_interfaces
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  permit_inet_interfaces
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: local_header_rewrite_clients = permit_inet_interfaces
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_discard_ehlo_keywords = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_discard_ehlo_keywords = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_discard_ehlo_keyword_address_maps = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_discard_ehlo_keyword_address_maps = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: relay_clientcerts = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: relay_clientcerts = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_tls_security_options = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $smtpd_sasl_security_options
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_security_options = noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $smtpd_sasl_security_options -> noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_tls_security_options = noanonymous
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_cert_file = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_cert_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_key_file = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $smtpd_tls_cert_file
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_cert_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $smtpd_tls_cert_file -> 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_key_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_dcert_file = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_dcert_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_dkey_file = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $smtpd_tls_dcert_file
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_dcert_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $smtpd_tls_dcert_file -> 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_dkey_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_CAfile = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_CAfile = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_CApath = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_CApath = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_mandatory_ciphers = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: medium
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  medium
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_mandatory_ciphers = medium
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_exclude_ciphers = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_exclude_ciphers = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_mandatory_exclude_ciphers = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_mandatory_exclude_ciphers = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_mandatory_protocols = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: SSLv3, TLSv1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  SSLv3, TLSv1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_mandatory_protocols = SSLv3, TLSv1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_dh512_param_file = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_dh512_param_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_dh1024_param_file = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_dh1024_param_file = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_fingerprint_digest = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: md5
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  md5
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_fingerprint_digest = md5
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_security_level = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_security_level = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_type = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: cyrus
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  cyrus
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_type = cyrus
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_milters = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_milters = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_connect_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: j {daemon_name} v
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  j {daemon_name} v
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_connect_macros = j {daemon_name} v
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_helo_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_helo_macros = {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_mail_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: i {auth_type} {auth_authen} {auth_author} {mail_addr}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  i {auth_type} {auth_authen} {auth_author} {mail_addr}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_mail_macros = i {auth_type} {auth_authen} {auth_author} {mail_addr}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_rcpt_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: i {rcpt_addr}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  i {rcpt_addr}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_rcpt_macros = i {rcpt_addr}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_data_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_data_macros = i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_end_of_header_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_end_of_header_macros = i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_end_of_data_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_end_of_data_macros = i
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_unknown_command_macros = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_unknown_command_macros = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_protocol = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 2
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  2
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_protocol = 2
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_default_action = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: tempfail
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  tempfail
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_default_action = tempfail
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_macro_daemon_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $myhostname
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: myhostname = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $myhostname -> davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_macro_daemon_name = davidsserver.com
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_macro_v = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: $mail_name $mail_version
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_name = davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: davidsserver Daemon
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: mail_version = 2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: expand $mail_name $mail_version -> davidsserver Daemon 2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_macro_v = davidsserver Daemon 2.5.1
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: stress = 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_expansion_filter = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_expansion_filter = \t\40!"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: default_rbl_reply = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: default_rbl_reply = $rbl_code Service unavailable; $rbl_class [$rbl_what] blocked using $rbl_domain${rbl_reason?; $rbl_reason}
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_helo_required = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_helo_required = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_delay_reject = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_delay_reject = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: strict_rfc821_envelopes = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: strict_rfc821_envelopes = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: disable_vrfy_command = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: allow_untrusted_routing = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: allow_untrusted_routing = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_auth_enable = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_sasl_authenticated_header = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_sasl_authenticated_header = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: broken_sasl_auth_clients = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: broken_sasl_auth_clients = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: show_user_unknown_table_name = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: show_user_unknown_table_name = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_reject_unlisted_sender = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_reject_unlisted_sender = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_reject_unlisted_recipient = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_reject_unlisted_recipient = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_use_tls = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_use_tls = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_enforce_tls = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_enforce_tls = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_wrappermode = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_wrappermode = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_auth_only = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_auth_only = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_ask_ccert = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_ask_ccert = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_req_ccert = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_req_ccert = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_received_header = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_received_header = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_always_issue_session_ids = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_always_issue_session_ids = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_peername_lookup = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_peername_lookup = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_delay_open_until_valid_rcpt = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_delay_open_until_valid_rcpt = yes
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_client_port_logging = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_client_port_logging = no
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_timeout = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_timeout = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_error_sleep_time = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_error_sleep_time = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_error_sleep_time = 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_proxy_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_proxy_timeout = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_proxy_timeout = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 3s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  3s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: address_verify_poll_delay = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: address_verify_poll_delay = 3s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: address_verify_poll_delay = 3s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 3s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  3s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_policy_service_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_policy_service_timeout = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_policy_service_timeout = 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  100s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_policy_service_max_idle = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_policy_service_max_idle = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_policy_service_max_idle = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_policy_service_max_ttl = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_policy_service_max_ttl = 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_policy_service_max_ttl = 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  1000s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_starttls_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_starttls_timeout = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_starttls_timeout = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_session_cache_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: smtpd_tls_session_cache_timeout = 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: smtpd_tls_session_cache_timeout = 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  3600s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_connect_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_connect_timeout = 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_connect_timeout = 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_command_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_command_timeout = 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_command_timeout = 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  30s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_content_timeout = (notfound)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_update: milter_content_timeout = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_lookup: milter_content_timeout = 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: mac_parse: 300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: dict_eval: const  300s
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: process generation: 220 (220)
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: match_string: mynetworks ~? debug_peer_list
Oct 22 17:45:45 davidsserver postfix/smtpd[5441]: match_string: mynetworks ~? fast_flush_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: mynetworks ~? mynetworks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: relay_domains ~? debug_peer_list
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: relay_domains ~? fast_flush_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: relay_domains ~? mynetworks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: relay_domains ~? permit_mx_backup_networks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: relay_domains ~? qmqpd_authorized_clients
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: relay_domains ~? relay_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: permit_mx_backup_networks ~? debug_peer_list
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: permit_mx_backup_networks ~? mynetworks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_open: calling proxy open routine
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: connect to subsystem private/proxymap
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr request = open
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr table = unix:passwd.byname
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr flags = 16448
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/proxymap socket: wanted attribute: status
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: status
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/proxymap socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 16464
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/proxymap socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_proxy_open: connect to map=unix:passwd.byname status=0 server_flags=fixed|lock|fold_fix
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_open: proxy:unix:passwd.byname
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_register: proxy:unix:passwd.byname(0,lock|fold_fix) 1
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_open: calling hash open routine
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: Compiled against Berkeley DB: 4.6.21?
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: Run-time linked against Berkeley DB: 4.6.21?
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_open: hash:/etc/aliases
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: dict_register: hash:/etc/aliases(0,lock|fold_fix) 1
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? debug_peer_list
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? fast_flush_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? mynetworks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? relay_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: smtpd_access_maps ~? smtpd_access_maps
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: xsasl_cyrus_server_init: SASL config file is smtpd.conf
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: fast_flush_domains ~? debug_peer_list
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: fast_flush_domains ~? fast_flush_domains
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: chroot /var/spool/postfix user postfix
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: auto_clnt_create: transport=local endpoint=private/anvil
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_create: 0x807f750 18000
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_stop: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_start: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: connection established
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: master_notify: status 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: name_mask: resource
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: name_mask: software
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: xsasl_cyrus_server_create: SASL service=smtp, realm=(null)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: name_mask: noanonymous
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: connect from localhost[127.0.0.1]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: localhost: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: 127.0.0.1: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: localhost: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: 127.0.0.1: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_hostname: localhost ~? 127.0.0.0/8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_hostaddr: 127.0.0.1 ~? 127.0.0.0/8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 220 davidsserver Daemon. All Spam Is Reported. ESMTP
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_pat: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: < localhost[127.0.0.1]: EHLO davidsserver
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-davidsserver.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-PIPELINING
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-SIZE 102400
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-ETRN
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: localhost: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: 127.0.0.1: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-AUTH LOGIN NTLM CRAM-MD5 PLAIN DIGEST-MD5
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-ENHANCEDSTATUSCODES
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250-8BITMIME
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250 DSN
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_pat: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: < localhost[127.0.0.1]: MAIL FROM:<david@davidsserver.com>
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: extract_addr: input: <david@davidsserver.com>
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: smtpd_check_addr: addr=david@davidsserver.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: connect to subsystem private/rewrite
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr request = rewrite
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr rule = local
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr address = [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: address
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: address
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: rewrite_clnt: local: [email]david@davidsserver.com[/email] -> [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr request = resolve
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr sender = 
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr address = [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: transport
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: transport
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: local
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: nexthop
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: nexthop
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: davidsserver.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: recipient
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: recipient
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 256
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: resolve_clnt: `' -> `david@davidsserver.com' -> transp=`local' host=`davidsserver.com' rcpt=`david@davidsserver.com' flags= class=local
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: ctable_locate: install entry key [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: extract_addr: in: <david@davidsserver.com>, result: [email]david@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: fsspace: .: block size 4096, blocks free 2793480
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: smtpd_check_queue: blocks 4096 avail 2793480 min_free 0 msg_size_limit 102400
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250 2.1.0 Ok
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_pat: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: < localhost[127.0.0.1]: RCPT TO:<*@yahoo.com>
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: extract_addr: input: <*@yahoo.com>
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: smtpd_check_addr: addr=*@yahoo.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr request = rewrite
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr rule = local
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr address = [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: address
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: address
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: rewrite_clnt: local: [email]*@yahoo.com[/email] -> [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr request = resolve
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr sender = 
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr address = [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: transport
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: transport
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: relay
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: nexthop
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: nexthop
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: [smtp.comcast.net]:587
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: recipient
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: recipient
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 2048
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: resolve_clnt: `' -> `*@yahoo.com' -> transp=`relay' host=`[smtp.comcast.net]:587' rcpt=`*@yahoo.com' flags= class=relay
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: ctable_locate: install entry key [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: extract_addr: in: <*@yahoo.com>, result: [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr request = rewrite
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr rule = local
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr address = double-bounce
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: flags
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: address
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: address
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: [email]double-bounce@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: private/rewrite socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: rewrite_clnt: local: double-bounce -> [email]double-bounce@davidsserver.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: >>> START Recipient address RESTRICTIONS <<<
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: generic_checks: name=permit_mynetworks
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: permit_mynetworks: localhost 127.0.0.1
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_hostname: localhost ~? 127.0.0.0/8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_hostaddr: 127.0.0.1 ~? 127.0.0.0/8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: generic_checks: name=permit_mynetworks status=1
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: >>> CHECKING RECIPIENT MAPS <<<
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: ctable_locate: leave existing entry key [email]*@yahoo.com[/email]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: maps_find: recipient_canonical_maps: [email]*@yahoo.com[/email]: not found
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? davidsserver.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? localhost.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? localhost
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: yahoo.com: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: maps_find: recipient_canonical_maps: @yahoo.com: not found
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: mail_addr_find: [email]*@yahoo.com[/email] -> (not found)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: maps_find: canonical_maps: [email]*@yahoo.com[/email]: not found
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? davidsserver.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? localhost.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? localhost
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: yahoo.com: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: maps_find: canonical_maps: @yahoo.com: not found
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: mail_addr_find: [email]*@yahoo.com[/email] -> (not found)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: maps_find: virtual_alias_maps: [email]*@yahoo.com[/email]: not found
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? davidsserver.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? localhost.com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? localhost
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_string: yahoo.com ~? com
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_list_match: yahoo.com: no match
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: maps_find: virtual_alias_maps: @yahoo.com: not found
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: mail_addr_find: [email]*@yahoo.com[/email] -> (not found)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: smtpd_check_rewrite: trying: permit_inet_interfaces
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: permit_inet_interfaces: localhost 127.0.0.1
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: before input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping enable_milters
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: after input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: connect to subsystem public/cleanup
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: public/cleanup socket: wanted attribute: queue_id
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: queue_id
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 13A3A822E8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: public/cleanup socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: send attr flags = 178
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: 13A3A822E8: client=localhost[127.0.0.1]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250 2.1.5 Ok
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_pat: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: < localhost[127.0.0.1]: DATA
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 354 End data with <CR><LF>.<CR><LF>
Oct 22 17:45:46 davidsserver postfix/cleanup[5444]: 13A3A822E8: message-id=<3153.192.168.1.100.1224711946.squirrel@davidsserver>
Oct 22 17:45:46 davidsserver postfix/qmgr[5432]: 13A3A822E8: from=<david@davidsserver.com>, size=714, nrcpt=1 (queue active)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: public/cleanup socket: wanted attribute: status
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: status
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: 0
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: public/cleanup socket: wanted attribute: reason
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: reason
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute value: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: public/cleanup socket: wanted attribute: (list terminator)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: input attribute name: (end)
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 250 2.0.0 Ok: queued as 13A3A822E8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_pat: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: < localhost[127.0.0.1]: QUIT
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: > localhost[127.0.0.1]: 221 2.0.0 Bye
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_hostname: localhost ~? 127.0.0.0/8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: match_hostaddr: 127.0.0.1 ~? 127.0.0.0/8
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: disconnect from localhost[127.0.0.1]
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: master_notify: status 1
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: connection closed
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_stop: 0x807f750
Oct 22 17:45:46 davidsserver postfix/smtpd[5441]: watchdog_start: 0x807f750
Oct 22 17:45:46 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 17:45:46 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 17:45:46 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 22 17:45:46 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 22 17:45:51 davidsserver postfix/smtpd[5441]: proxymap stream disconnect
Oct 22 17:45:51 davidsserver postfix/smtpd[5441]: rewrite stream disconnect
Oct 22 17:45:51 davidsserver postfix/smtpd[5441]: watchdog_stop: 0x807f750
Oct 22 17:45:51 davidsserver postfix/smtpd[5441]: watchdog_start: 0x807f750
Oct 22 17:45:58 davidsserver postfix/smtp[5434]: 13A3A822E8: to=<*@yahoo.com>, relay=smtp.comcast.net[76.96.30.117]:587, delay=12, delays=0.09/0/0.69/12, dsn=4.1.0, status=deferred (host smtp.comcast.net[76.96.30.117] said: 452 4.1.0 ... temporary failure (in reply to MAIL FROM command))


---

### Post by MJN on 2008-10-22
Something doesn't add up...

You say your config is the top one, yet only the bottom one contains the :587 port which your server is connecting to...

There is no SMTP dialogue shown in your log between you and Comcast's server yet supposedly it is getting as far as the MAIL FROM command and then being rejected.

It's as if you've got some other instance of SMTP running on your machine...

You did **restart** (not reload) Postfix didn't you?

Mathew

Edit: Oops - could be my error. Try adding the -vv to the smtp line that ends in smtp (not smtpd) instead in master.cf (and restart, not reload in case that's what you were doing)

---

### Post by theman on 2008-10-22
I did /etc/init.d/postfix restart but it fails saying postfix is already running. It tells me postfix restart isn't a valid command so I just did a complete reboot :). I edited the master.cf again and fixed -vv but it displays the same info/error. My sasl_passwd is [smtp.comcast.net]:587 comcastwebmailun:comcastwebmailpw, correct?

---

### Post by theman on 2008-10-22
Come on guys, I can't figure out what the problem is :(.

---

### Post by MJN on 2008-10-23
Post another log of the mail being sent. This time it should show in detail the message actually being sent (as opposed to it being received by Postfix from Squirrelmail) since the verbosity is on the smtp client (and not smtpd like I originally said).

I am intrigued as to why sudo /etc/init.d/postfix restart doesn't work.

Mathew

---

### Post by theman on 2008-10-23
I changed to [smtp.gmail.com]:587. I had to create a TLS certificate. Now it complains about a STARTTLS command.

Here is mail.log:

> Oct 23 20:21:08 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 23 20:24:06 davidsserver postfix/smtpd[5210]: connect from localhost[127.0.0.1]
Oct 23 20:24:06 davidsserver postfix/smtpd[5210]: 7D23A822BA: client=localhost[127.0.0.1]
Oct 23 20:24:06 davidsserver postfix/cleanup[5213]: 7D23A822BA: message-id=<2429.192.168.1.100.1224807846.squirrel@davidsserver>
Oct 23 20:24:06 davidsserver postfix/qmgr[4960]: 7D23A822BA: from=<david@davidsserver.com>, size=724, nrcpt=1 (queue active)
Oct 23 20:24:06 davidsserver postfix/smtpd[5210]: disconnect from localhost[127.0.0.1]
Oct 23 20:24:06 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 23 20:24:06 davidsserver postfix/smtp[5214]: Host offered STARTTLS: [smtp.gmail.com]
Oct 23 20:24:07 davidsserver postfix/smtp[5214]: 7D23A822BA: to=<*@yahoo.com>, relay=smtp.gmail.com[64.233.179.109]:587, delay=0.3, delays=0.08/0.11/0.09/0.02, dsn=5.7.0, status=bounced (host smtp.gmail.com[64.233.179.109] said: 530 5.7.0 Must issue a STARTTLS command first. 52sm10861533hsf.1 (in reply to MAIL FROM command))
Oct 23 20:24:07 davidsserver dovecot: IMAP(david): Disconnected: Logged out
Oct 23 20:24:07 davidsserver postfix/cleanup[5213]: 2E1E7822BC: message-id=<20081024002407.2E1E7822BC@davidsserver.com>
Oct 23 20:24:07 davidsserver postfix/qmgr[4960]: 2E1E7822BC: from=<>, size=2775, nrcpt=1 (queue active)
Oct 23 20:24:07 davidsserver postfix/bounce[5217]: 7D23A822BA: sender non-delivery notification: 2E1E7822BC
Oct 23 20:24:07 davidsserver postfix/qmgr[4960]: 7D23A822BA: removed
Oct 23 20:24:07 davidsserver postfix/local[5219]: 2E1E7822BC: to=<david@davidsserver.com>, relay=local, delay=0.28, delays=0.02/0.21/0/0.04, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Oct 23 20:24:07 davidsserver postfix/qmgr[4960]: 2E1E7822BC: removed
Oct 23 20:24:07 davidsserver dovecot: imap-login: Login: user=<david>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Oct 23 20:24:07 davidsserver dovecot: IMAP(david): Disconnected: Logged out

Here is postfix.conf:

> #
### Postfix main.cf
#
### Verify these directory settings - they are critical to Postfix operation.
biff = no
recipient_delimiter = .
command_directory = /usr/sbin
daemon_directory = /usr/libexec/postfix
program_directory = /usr/libexec/postfix

### Interface to listen on

### smtp banner
mail_name = davidsserver Daemon
smtpd_banner = $mail_name. All Spam Is Reported. ESMTP

### Who delivers the mail (never root for security).
setgid_group = postdrop

### Default user to deliver mail to (NEVER ENABLE)
luser_relay =

### The myorigin parameter specifies the domain that appears in mail that is posted on/through this machine.
append_dot_mydomain = no
append_at_myorigin = yes

### alias's
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

### the internet hostname of this mail system
myhostname = davidsserver.com
mydomain=com

### The mydestination parameter specifies what domains this machine will deliver locally, instead
### of forwarding to another machine. The default is to receive mail for the machine itself.
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

### Relay Host this mail server should send its mail to. (NONE)
relayhost = [smtp.gmail.com]:587

### Relay Client SASL Authentication
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

### External Networks to accept RELAYED mail from.
mynetworks = 127.0.0.0/8

### Where to send mail that is delivered locally.
mailbox_command = procmail -a "$EXTENSION"

### How much of the message in bytes will be bounced back to the sender.
bounce_size_limit = 5000

### No limit on mailbox size.
mailbox_size_limit = 0

### Limit sent/recieved emails to 1 Meg "(header+body+attachment)x(mime-encoding) <= 1 meg"
message_size_limit = 102400

### How long do messages stay in the queue before being sent back to the sender. (in days)
### By default, postfix attempts to resend the message every (1000 secs)x(# attempts)x(days).
bounce_queue_lifetime = 4h
maximal_queue_lifetime = 4h
delay_warning_time = 1h

### Parrallel delivery force (local=2 and dest=20 are aggressive)
local_destination_concurrency_limit = 2
default_destination_concurrency_limit = 20

### Max flow rate (1 sec deslay per 50 emails/sec over the number of emails delivered/sec)
in_flow_delay = 1s

### no one needs to ask our server who is on it
disable_vrfy_command = yes

#### user%domain != user@domain
allow_percent_hack = no

#### user!domain != user@domain
swap_bangpath = no

#### tls certification
smtpd_tls_auth_only = no
#smtp_use_tls = yes
#smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_interfaces = all
smtp_tls_CAfile=/etc/ssl/certs/ca-certificates.crt 
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client

#####################  END  #####################################################



---

### Post by theman on 2008-10-23
When I telnet localhost 25, ehlo localhost, there is no 250 AUTH. when I type auth login I get 503 5.5.1 Error: authentication not enabled.

---

### Post by theman on 2008-10-23
Okay telnet now shows auth plain, auth=plain. typing auth login in telnet gives me "535 5.7.8 Error: authentication failed: Invalid authentication mechanism".

---

### Post by MJN on 2008-10-24
You have overlooked a number of my suggestions so I'm going to hand you over to someone else now.
 
I suggest you go back to basic and cover one thing at a time. You are diving in at the deep end so it is no wonder you are drowning.
 
Mathew

---

### Post by theman on 2008-10-24
Thank God I got it working after installing ca-certificates and uncommenting #smtp_use_tls = yes, #smtpd_use_tls = yes. The only problem is that after my email is relayed on gmail, it shows up as my [email]un@gmail.com[/email] not [email]un@davidsserver.com[/email]. How do I fix that.

---

### Post by theman on 2008-10-24
So I am back to square 1. I need to use smtp.comcast.net:587 but I get temporary failure, too many sessions.

---

### Post by theman on 2008-10-24
Help would be appreciated.

---

### Post by theman on 2008-10-25
Help would really be appreciated.

---

### Post by theman on 2008-10-26
Still waiting...

---

### Post by theman on 2008-10-27
Wow, and they say Ubuntu's community plays a big role in choosing it as a distribution.

---

