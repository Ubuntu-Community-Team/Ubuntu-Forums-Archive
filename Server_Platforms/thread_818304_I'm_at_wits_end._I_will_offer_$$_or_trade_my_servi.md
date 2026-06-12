---
title: "I'm at wits end. I will offer $$ or trade my services if someone can..."
date: 2008-06-04
forum: Server Platforms
---

### Post by YouBunn2 on 2008-06-04
work with me in resolving my mail problem.

I am not a technical person, I know enough to be dangerous as proved last night. 
I have started a thread on my postfix being broken. I have tried alot and read alot to no avail. 
Can someone work with me in getting mail restore:confused:
thanks,

---

### Post by collinp on 2008-06-04
Well, first of all, what did you do to it and what did it do?

---

### Post by YouBunn2 on 2008-06-04
> **Hellow said:**
> Well, first of all, what did you do to it and what did it do?

I use webmin to modify the max attachment size and it seemed to hose the main and master config files. 

When I did that the smtp wouldnt start due to a smtpd_recipient_restrictions = not right. I added a few checks. 
But I think the mapping to the mysql broke. 
Mail is coming in and staying in the queue. 

beyond that I am pretty much googling and trying things. 

any help is appreciated.

---

### Post by collinp on 2008-06-04
Well, it appears that you set the attachment size too high for the server, try resetting the attachment size.

---

### Post by YouBunn2 on 2008-06-04
> **Hellow said:**
> Well, it appears that you set the attachment size too high for the server, try resetting the attachment size.

I set it to 100M, was that too much? yikes. 
But in the process I modified the master.cf and main.cf. How do these look?
I have a MySQL db for the transport mapping to relay to servers. 

Master.cf

ld@name:/etc/postfix$ cat master.cf
# Example main.cf
# Scott Hurring [scott at hurring dot com]
# [http://hurring.com/howto/postfix_spamd/](http://hurring.com/howto/postfix_spamd/)
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (50)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd

#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
         -o content_filter=
         -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       -       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       nqmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
flush     unix  n       -       -       1000?   0       flush
smtp      unix  -       -       -       -       -       smtp
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
#
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
# The Cyrus deliver program has changed incompatibly.
#

smtp-amavis     unix    -       -       y       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20

127.0.0.1:10025 inet    n       -       y       -       -       smtpd
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


# anvil unix ---- 1 anvil


spamassassin unix -     n       n       -       -       pipe
        user=nobody argv=/usr/bin/spamc -f -e
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}

cyrus     unix  -       n       n       -       -       pipe
  flags=R user=cyrus argv=/usr/sbin/cyrdeliver -e -m ${extension} ${user}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -d -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}

# only used by postfix-tls
#smtps    inet  n       -       n       -       -       smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
#587      inet  n       -       n       -       -       smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes


main.cf

myhostname = server.MyDomain.com
mydomain = Domain.com
myorigin = $mydomain
mydestination =
local_recipient_maps =
relay_domains = domain1.com, domain2.com
message_size_limit = 10485760
#transport_maps = hash:/etc/postfix/transport
transport_maps = mysql:/etc/postfix/transport-mysql.cf
smtpd_helo_required = yes
disable_vrfy_command = yes
virtual_alias_maps = hash:/etc/postfix/virtual
# virtual_alias_maps = mysql:/etc/postfix/transport-mysql.cf
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


# smtpd_recipient_restrictions = permit_mynetworks, check_relay_domains
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

---

### Post by koenn on 2008-06-04
> **YouBunn2 said:**
> I set it to 100M, was that too much? yikes. 

SMTP (internet e-mail protocol) was designed for msg's of 5 MB max. That includes attachments. If you need to distribute 100 MB files, you need other solutions (a server where people can upload to and download from ?)

I know this doesn't help much for your actual problem, but it might explain why Postfix doesn't like the attachement size you set. 

I don't know anything about Postfix, so ...

---

### Post by YouBunn2 on 2008-06-04
What do I need to do to send all the mail to one specific server? 90% of all mail gets relayed to this?

I can telnet into the server just fine and send myself a message.
Postfix on the other hand gets mail refused. I think it may be trying to relay to localhost.

---

