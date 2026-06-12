---
title: "Samba / AD 2008 R2"
date: 2012-05-22
forum: Server Platforms
---

### Post by talishka on 2012-05-22
Hi! I'm trying to join a just updated ubuntu server to my domain. I already joined a few servers, but this one (Ubuntu 12.04 LTS) it keeps giving me troubles.

I installed krb5-user winbind and samba.
Configured as usual krb5.conf with my domain controllers (same configuration in every server)
Edited smb.conf (same configuration in every server, different shares)
Created the smb user for mapping
Edited /etc/nsswitch.conf 
Modified /etc/pam/common-account, /etc/pam/common-auth, /etc/pam/common-password, and /etc/pam/common-session

Then i run kinit admin@DOMAIN, and i get the ticket without problems.

Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]admin@DOMAIN.COM[/email]

Valid starting    Expires           Service principal
22/05/2012 16:43  22/05/2012 23:23  krbtgt/DOMAIN.COM@DOMAIN.COM

But when i try to join i get the following error:

root@server:/etc/pam.d# net ads join -U [email]admin@DOMAIN.COM[/email]
Enter [email]admin@DOMAIN.COM[/email]'s password:
dos charset 'CP850' unavailable - using ASCII
convert_string_talloc: Conversion not supported.
Failed to join domain: failed to lookup DC info for domain 'DOMAIN.COM' over rpc: Memory allocation error

or

root@server:/etc/pam.d# net rpc join -U [email]admin@DOMAIN.COM[/email]
dos charset 'CP850' unavailable - using ASCII
convert_string_talloc: Conversion not supported.
Connection failed: NT_STATUS_NO_MEMORY
Enter [email]admin@DOMAIN.COM[/email]'s password:
convert_string_talloc: Conversion not supported.
Could not connect to server DC1
Connection failed: NT_STATUS_NO_MEMORY

Everything looks normal and well configured, but i cannot locate the problem.. i can ping both DC without problems, dns resolution is working good..

Any ideas? Thanks!

---

