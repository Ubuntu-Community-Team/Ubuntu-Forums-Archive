---
title: "MS Exchange and LDAP, LDAP Capabilities"
date: 2010-07-19
forum: Server Platforms
---

### Post by yebo29 on 2010-07-19
Hi everyone,

I'm in charge of building out the infrastructure for my office and I'm having to decide between LDAP or Active Directory.

First question is: can Exchange integrate with LDAP, or does it **have** to be Active Directory? In other words, if I choose OpenLDAP or 389 server or whatever, will I be able to implement an Exchange server?

Second: what is LDAP capable of? Can I automount home directories on windows clients? Can I push packages, or at the least scripts to install packages? I understand that GPO's are only Active Directory - is this correct? 
Do most sysadmins implement an LDAP **and** Samba server at the same to provide all the functionality? 

Thanks!
>a sysadmin looking for answers

---

### Post by HermanAB on 2011-02-25
Howdy,

Active Directory *is* LDAP.

AD is a modified version of LDAP with an old modified version of BIND 8, plus a modified version of Kerberos.

You can do Windows NT style AD with Samba.  That should be good enough.

---

### Post by koenn on 2011-02-25
> **HermanAB said:**
> 
AD is a modified version of LDAP with an old modified version of BIND 8, plus a modified version of Kerberos.

It's those modifications that make things tricky. 
If Exchange relies, in any way, on one of those modifications, trying to run Exchange against a standard LDAP server, such as OpenLDAP, is a no go. 
And who, except MS, knows *what* Exchange is going to expect, LDAP-wise?


@OP
most of the stuff you mention  --  automount home directories on windows clients, push packages or scripts to install packages, GPO's, ... -
ar MS additions that have little to nothing to do with LDAP :
home directories is network file sharing (SMB, Samba), GPO is based on registry editing, and the remote install/publishing of software is (I'm guessing here) a combination of file sharing and remote procedure calls.

---

