---
title: "kerberos tickets for samba??"
date: 2006-09-09
forum: Server Platforms
---

### Post by scav on 2006-09-09
Hello! I have just set up an openldap with heimdal kerberos system its working fine, but I want my clients to automatic access the samba shares with their kerberos ticket, I have no clue how to do this, does anyone have experience with this or can maybe guide me to a side where I can find ?

---

### Post by fnjordy on 2006-09-12
A little more detail is required, do you have Active Directory?  Why are your clients using Samba?  Are you trying to replace an AD setup with a Linux equivalent?

Samba's [official howto](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#ads-member) has a section on joining a Samba v3 server to an AD domain for using Kerberos trust.

For Samba supporting AD login directly you will have to wait a (long) while for Samba v4 to release.

---

