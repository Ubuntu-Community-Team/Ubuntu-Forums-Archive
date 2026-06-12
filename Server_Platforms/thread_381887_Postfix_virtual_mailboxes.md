---
title: "Postfix virtual mailboxes"
date: 2007-03-11
forum: Server Platforms
---

### Post by Steve Smith on 2007-03-11
I'm following this howto:

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

I can now log in to my mailbox by IMAP, using my full email address as the user, and the password I've set using postfixadmin web interface.  But my mail's not being delivered to that mailbox!  It's still being delivered to the mailbox that is kept in my home directory.

Here's my main.cf:

```

#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = nonexistence.co.uk, jamiebunce.co.uk
relayhost =
mynetworks = 127.0.0.0/8, 10.1.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
virtual_alias_domains = jamiebunce.co.uk
virtual_alias_maps = hash:/etc/postfix/virtual

# SASL SUPPORT FOR CLIENTS
#
# The following options set parameters needed by Postfix to enable
# Cyrus-SASL support for authentication of mail clients.
smtpd_sasl_auto_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = nonexistence.co.uk
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions =
   permit_sasl_authenticated,
   permit_mynetworks,
   check_relay_domains

# Virtual Mailbox Domain Settings
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /srv/vmail
virtual_transport = virtual

# Additional for quota support
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps                                             .cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your disks                                             pace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes

```

I thought setting:

myhostname = localhost

would be enough, but obviously not.  Any help would be great, thanks!

---

### Post by Steve Smith on 2007-03-24
I still haven't got anywhere with this, anyone got any ideas? :)

---

### Post by Nikron on 2007-03-24
home_mailbox may be conflicting with virtual_mailbox_base, so I'd set home_mailbox  to nothing

---

### Post by Steve Smith on 2007-03-24
Commenting out home_mailbox has stopped mail being delivered to linux user mailboxes, but it doesn't go anywhere else either!  You can't sign in to the virtual mailbox accounts with an email client.  In fact, the mailbox directories don't get created (in my case /srv/vmail - the home directory of uesr 'vmail'.

---

### Post by Nikron on 2007-03-24
Hmmm, It also looks like virtual_mailbox_limit_maps is deformed, lots of spaces before the .cf

---

### Post by Mr. C. on 2007-03-24
You have your domain defined in both mydestination and virtual_alias_domains:

```
mydestination = nonexistence.co.uk, jamiebunce.co.uk
virtual_alias_domains = jamiebunce.co.uk
```

NEVER define a domain to be in more than one class (local, virtual alias, or virtual domain).

Remove jamiebunce.co.uk from mydestination

The home_mailbox setting is only for local users, so in this case only mail to nonexistence.co.uk domains would be delivered to home dirs (once you've made the change above).

MrC

---

### Post by Steve Smith on 2007-03-24
Thanks, but I tried that before.  Only changed it back to use "real" mailboxes for now.  Thanks for reminding me to take it out when I try other things, though!

---

### Post by Mr. C. on 2007-03-25
It works.  You need to be sure to restart postfix.

Since we can't see the contents of your mysql database for the virtual (alias,domains) classes, and there is no log data, we can only guess what's happening.

When jamiebunce.co.uk is a virtual_alias_domains, what do your logs show for delivery ?

[quote=Nikron]Hmmm, It also looks like virtual_mailbox_limit_maps is deformed, lots of spaces before the .cf[/quote]
This makes no difference.

MrC

---

### Post by Steve Smith on 2007-03-25
> **Nikron said:**
> Hmmm, It also looks like virtual_mailbox_limit_maps is deformed, lots of spaces before the .cf

I just checked, something to do with pasting it into the forum, the spaces aren't there - thanks though!

---

### Post by Steve Smith on 2007-03-25
> **Mr. C. said:**
> When jamiebunce.co.uk is a virtual_alias_domains, what do your logs show for delivery ?

Oo, syslog tells you everything, not something I've more than glanced at before!

I've looked at it, changed what it said, and again, and now got as far as:

```

Mar 25 18:48:02 moolooite postfix/virtual[4611]: 75167722F4: to=<***@jamiebunce.co.uk>, relay=virtual, delay=5, status=deferred (recipient ***@jamiebunce.co.uk: bad uid 113 in virtual_uid_maps)

```

I've not got phpmyadmin working, which makes it easier for me to see what's going on, and for the mailbox table it says:

```

PRIMARY and INDEX keys should not both be set for column `username`

```

Which should it be?  I'm fairly new to mysql, can you have a table with no index if it's got a primary column?

---

### Post by Steve Smith on 2007-03-25
I've realised I'm on the wrong track with that.  The uid 113 is the uid of my vmail linux user.

From main.cf:

```

virtual_minimum_uid = 5000
virtual_uid_maps = static:113
virtual_gid_maps = static:113
virtual_mailbox_base = /srv/vmail
virtual_transport = virtual

```

I've changed virtual_miniumum_uid to 113 and it delivers!  What exactly is virtual_minium_uid?  I've read about it in [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html), but don't quite understand what it means.  Will there be any other uids created aside from my vmail user?  I wouldn't have thought so.  Is this a security thing?

What I still can't do is log on to the mailboxes via imap/pop!  I'm using courier-imap/pop.

---

### Post by Mr. C. on 2007-03-25
Your virtual uid range is set to start at uid 5000 in the mail.cf below.

This does not match:

Mar 25 18:48:02 moolooite postfix/virtual[4611]: 75167722F4: to=<***@jamiebunce.co.uk>, relay=virtual, delay=5, status=deferred (recipient ***@jamiebunce.co.uk: bad uid 113 in virtual_uid_maps)

which indicates a uid of 113.  This is below your uid 5000.   Show postconf -n to see what postfix thinks is in affect currently.

/var/log/maillog is your friend... review it frequently, and use some utility such as logwatch to help filter and organize the data.  Start with the lastest postfix logwatch filter:

  [http://www.mikecappella.com/logwatch/postfix.tgz](http://www.mikecappella.com/logwatch/postfix.tgz)

About your SQL question: [http://tinyurl.com/2ctsq3](http://tinyurl.com/2ctsq3)

MrC

---

### Post by Mr. C. on 2007-03-25
> **Steve Smith said:**
> I've realised I'm on the wrong track with that.  The uid 113 is the uid of my vmail linux user.

From main.cf:

```

virtual_minimum_uid = 5000
virtual_uid_maps = static:113
virtual_gid_maps = static:113
virtual_mailbox_base = /srv/vmail
virtual_transport = virtual

```

I've changed virtual_miniumum_uid to 113 and it delivers!  What exactly is virtual_minium_uid?  I've read about it in [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html), but don't quite understand what it means.  Will there be any other uids created aside from my vmail user?  I wouldn't have thought so.  Is this a security thing?

What I still can't do is log on to the mailboxes via imap/pop!  I'm using courier-imap/pop.

Our postings crossed.

Virtual mailbox users have no real system login account, but the mail has to be owned by some UID.  The uid/gid settings above force the virtual mailbox data to be owned/group'ed by those UID/GIDs.  Because you can have maps of UID/GIDs based upon key lookups (for example, domain1 = uid 1000, domain2 = uid 1001), there needs to be a minimum so that a misconfigured lookup doesn't result in mail being owned by the wrong UID/GID.  Since you are using "static", only UID 5000 will be used - and no lookups occur (static means static lookup, always returning the specified value).

What username does UID 113 belong to ?  I'm not sure you want to change your minimum to match 113 - rather, you want to know / understand why your mail is being delivered to/by UID 113.

We'll get to the courier/pop problem after this is completed.

MrC

---

### Post by Steve Smith on 2007-03-25
I'll read the sql link later, thanks!

I think I edited my post after you hit reply, or you didn't notice my comments on the bottom about uid 113.  What is the purpose of the minium uid setting?

In /etc/courier/authdaemontc I have:

```

authmodulelist="authmysql"

```

and /etc/courier/authmysqlrc contains:

```

MYSQL_SERVER localhost
MYSQL_USERNAME ***
MYSQL_PASSWORD ***
MYSQL_PORT 0
MYSQL_DATABASE postfix
MYSQL_USER_TABLE mailbox
#MYSQL_CRYPT_PWFIELD password
MYSQL_CLEAR_PWFIELD password
MYSQL_UID_FIELD 113
MYSQL_GID_FIELD 113
MYSQL_LOGIN_FIELD username
MYSQL_HOME_FIELD "/srv/vmail"
MYSQL_MAILDIR_FIELD maildir
#MYSQL_NAME_FIELD
MYSQL_QUOTA_FIELD quota

```

Do I need to change any of that?

---

### Post by Steve Smith on 2007-03-25
> **Mr. C. said:**
> What username does UID 113 belong to ?  I'm not sure you want to change your minimum to match 113 - rather, you want to know / understand why your mail is being delivered to/by UID 113.

Ahh, I see - I didn't realise you could have different uids for each domain.  Don't worry, my uid 113 is vmail - a user I've set up to own the mailboxes.

syslog says:
```

Mar 26 00:25:25 moolooite imaplogin: Connection, ip=[::ffff:127.0.0.1]
Mar 26 00:25:30 moolooite imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Mar 26 00:25:30 moolooite imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]

```

mail.log, mail.warn, etc, don't give any more info than that.

---

