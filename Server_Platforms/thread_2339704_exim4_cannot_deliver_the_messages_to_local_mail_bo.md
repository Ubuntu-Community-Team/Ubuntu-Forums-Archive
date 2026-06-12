---
title: "exim4 cannot deliver the messages to local mail box?"
date: 2016-10-12
forum: Server Platforms
---

### Post by shamsat on 2016-10-12
Hi,
 My local mail server with exim4 and dovecot was running fine in ubuntu 10.04, i installed the ubuntu 16.10, now exim4 cannot deliver the mails to my local mail box in /var/mail/me, when send the mail to  me@localhost i get this error:
This is /var/log/exim4/mainlog :
```

2016-10-12 11:18:31 1buDL5-0002OC-O0 <= root@ETC_MAILNAME U=root P=local S=344
2016-10-12 11:18:31 1buDL5-0002OC-O0 ** me@localhost: Unrouteable address
2016-10-12 11:18:31 1buDL5-0002OG-RH Error while reading message with no usable sender address (R=1buDL5-0002OC-O0): at least one malformed recipient address: root@ETC_MAILNAME - malformed address: _MAILNAME may not follow root@ETC
2016-10-12 11:18:31 1buDL5-0002OC-O0 Process failed (1) when writing error message to root@ETC_MAILNAME (frozen)

```
This is /var/log/exim4/rejectlog:
```

2016-10-12 11:54:09 H=localhost (me.publicvm.com) [127.0.0.1] F=<me@localhost> temporarily rejected RCPT <me@localhost>: DNS lookup of "MAIN_RELAY_NETS" deferred

```
This is the local delivery error for  [email]me@me.linkpc.net[/email], the me.linkpc.net and me.publicvm.com are my local hosts:
In /var/log/exim4/mainlog:
```

2016-10-12 12:05:16 H=localhost (me.publicvm.com) [127.0.0.1] F=<me@localhost> temporarily rejected RCPT <me@me.linkpc.net>: DNS lookup of "MAIN_RELAY_NETS" deferred
2016-10-12 12:05:16 unexpected disconnection while reading SMTP command from localhost (me.publicvm.com) [127.0.0.1]

```
And this is the /var/log/eim4/rejectlog:
```

2016-10-12 12:05:16 H=localhost (me.publicvm.com) [127.0.0.1] F=<me@localhost> temporarily rejected RCPT <me@me.linkpc.net>: DNS lookup of "MAIN_RELAY_NETS" deferred

```

This is a part of /etc/exim4/exim4.conf:
```
# Create domain and host lists for relay control
# '@' refers to 'the name of the local host'

# List of domains considered local for exim. Domains not listed here
# need to be deliverable remotely.
domainlist local_domains = MAIN_LOCAL_DOMAINS

# List of recipient domains to relay _to_. Use this list if you're -
# for example - fallback MX or mail gateway for domains.
domainlist relay_to_domains = MAIN_RELAY_TO_DOMAINS

# List of sender networks (IP addresses) to _unconditionally_ relay
# _for_. If you intend to be SMTP AUTH server, you do not need to enter
# anything here.
hostlist relay_from_hosts = MAIN_RELAY_NET

# Decide which domain to use to add to all unqualified addresses.
# If MAIN_PRIMARY_HOSTNAME_AS_QUALIFY_DOMAIN is defined, the primary
# hostname is used. If not, but MAIN_QUALIFY_DOMAIN is set, the value
# of MAIN_QUALIFY_DOMAIN is used. If both macros are not defined,
# the first line of /etc/mailname is used.
.ifndef MAIN_PRIMARY_HOSTNAME_AS_QUALIFY_DOMAIN
.ifndef MAIN_QUALIFY_DOMAIN
qualify_domain = ETC_MAILNAME
.else
qualify_domain = MAIN_QUALIFY_DOMAIN
.endif
.endif
```

---

### Post by howefield on 2016-10-12
Thread moved to the "*Server Platforms*" forum where you are more likely to get the help you need.

---

