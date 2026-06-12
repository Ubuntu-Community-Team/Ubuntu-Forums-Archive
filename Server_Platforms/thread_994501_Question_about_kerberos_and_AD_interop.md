---
title: "Question about kerberos and AD interop"
date: 2008-11-26
forum: Server Platforms
---

### Post by jim_harriger on 2008-11-26
Great write-up on AD and ubuntu in this thread:
**Howto: Ubuntu server as an Active Directory member server** over in the Tutorials area.

I'm trying to make this work at home, but with a few twists: i'm using Hardy, and my AD domain controllers are Windows Server 2008. my DNS and ntp situation is clean (my AD server is NTP source, not ubuntu, but that shouldn't make a difference, should it?), but when i try to get a ticket, i get this:

*kinit(v5): KDC reply did not match expectations while getting initial credentials*

in addition, even though i have these lines in my krb5.conf, i get no logs in /var/log.

[I][logging]
default = FILE:/var/log/krb5.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmin.log[/I]

any ideas what i've done wrong here? is a daemon that needs to be started? any more information that might help? thanks, all!

Jim Harriger

---

### Post by jim_harriger on 2009-01-03
i figured this out: when requesting a ticket vi kinit, the domain name part of the security pricipal must be in upper case!

i.e. this works:

sudo kinit [email]administrator@LOCALDOMAIN.NET[/email]

while this does not:

sudo kinit [email]administrator@localdomain.net[/email]

thanks, all!

---

