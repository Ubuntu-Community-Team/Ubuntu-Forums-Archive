---
title: "Can't get squirrelmail to work"
date: 2008-11-20
forum: Server Platforms
---

### Post by Phases on 2008-11-20
I'm hoping someone can help me. They will need super l33t skillz to weed through my own confusion and help me figure myself out.

I've been working on this for days. I have followed flurdys guide for setting up a mail server using postfix and courier (i guess it's using it) but can't get squirrelmail to work for the life of me. 

Here is what (I think) I know. 

Mail works. You know, I type "mail" it tells me my new mail, i can read, reply, etc. I can recieve and send to wherever, using a comcast server as a relay.

[email]phases@superstickphase.com[/email]

It users the regular unix mail dir, var/spool/mail for new mail, seems to store non-new mails in /home/phases/mbox

I've been tailing mail.log and mysql.log during all this. 

What I want to do is use squirrelmail for this! Can I? Or must I use the virtual directory that squirrelmail keeps looking for when I try to log in. It doesn't find it and IMAP drops my connection:

/var/spool/mail/virtual/phases

there is a vitual folder, but no phases inside. 

I've added a phases folder, played with sym links to /var/spool/mail/phases, messed with dir's it points to in phpmyadmin when it authenticates, I just can't get it to work.

Anyone have any insight? I just want to setup squirrelmail to work with the standard unix mail system. (I guess?)

---

### Post by amauk on 2008-11-20
> **Phases said:**
> It users the regular unix mail dir, var/spool/mail for new mail, seems to store non-new mails in /home/phases/mbox
I think this is your problem,
If you're using virtual email accounts, they should not end up on actual Linux account home folders

You may want to re-check your postfix config against the tutorial to make sure you haven't missed anything

All email (both unread & read) should be under /var/mail/virtual/<account>/

*edit*
try double checking the entries in the users table on MySQL
make sure "home" is specified as "/var/spool/mail/virtual"

---

### Post by Phases on 2008-11-20
Thanks for the reply. Yeah in sql it's set up right, here is the last bit of my mail.log when I try to connect, too:

Nov 20 09:57:05 phases78s1 authdaemond: Authenticated: clearpasswd=mypassword, passwd=<null>
Nov 20 09:57:05 phases78s1 imapd: chdir /var/spool/mail/virtual/phases/: No such file or directory

and I get the "ERROR: Connection dropped by IMAP server."

In my main.cf for postfix, I do see this:

# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual

but, it's not using it and there's no 'phases' folder inside virtual.

Here is my whole main.cf file. Excuse the mess, been trial and erroring:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# This is already done in /etc/mailname
myhostname = /etc/mailname

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myorigin = superstickphase.com

smtpd_banner = $myhostname ESMTP $mail_name (SSP)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

#relayhost =

relayhost = [smtp.comcast.net]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/comcast/comcast_passwd
smtp_sasl_security_options =

#relayhost = [smtp.gmail.com]:587
#smtp_sasl_auth_enable = yes
#smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
#smtp_sasl_security_options = noanonymous
#smtp_tls_CAfile = /etc/postfix/cacert.pem
#smtp_use_tls = yes

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = superstickphase.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = superstickphase.com, superstickphase.com', phases78s1, localhost.localdomain, localhost
#mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks = 192.0.0.0/8 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/16
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
#masquerade_domains = sub.domain.com !sub.dyndomain.com
#masquerade_exceptions = root

local_recipient_maps =

# how long if undelivered before sending warning update to sender
delay_warning_time = 1h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 100
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit smtpd_da$

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

```

---

### Post by amauk on 2008-11-20
can you send yourself an email, then post the error logs for postfix

```
tail -20 /var/log/mail.err
```

---

### Post by Phases on 2008-11-20
Sent one from CLI to myself and from gmail, and got no errors generated there.

---

### Post by amauk on 2008-11-20
well,
I'm fresh out of ideas unfortunately

other than go back through the tutorial and ensure everything's setup correctly

---

### Post by Phases on 2008-11-20
Yeah, I've been up and down that thing 100 times, but I musta missed something and will keep trying. 

No worries though, I do appreciate it. I've been [posting on the tutorial thread for days]("http://ubuntuforums.org/showthread.php?t=40047&page=15") and you're the only person who's offered to try to help. My posts there have just turned into a running log of my progress.

I DO like to figure things out on my own though, so no real biggie :) I'm just getting worn out lol. And the funny thing is I don't even need it. I only set this up so I could put together a mailing list for my website, which what I have now will (well, should, never done this before..) work fine for. 

It's just bugging me that I can't get it.

Thanks again!

---

