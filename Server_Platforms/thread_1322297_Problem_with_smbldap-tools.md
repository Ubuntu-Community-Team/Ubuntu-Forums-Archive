---
title: "Problem with smbldap-tools"
date: 2009-11-10
forum: Server Platforms
---

### Post by tristanhall on 2009-11-10
I'm having issues when I try to add users using smbldap-tools. I'll use
```
**smbldap-useradd -a -P username**
**smbldap-useradd -a -P username**

```
 
and then I get an error that says
```
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/smbldap_tools.pm line 135, <CONFIGFILE> line 79.
Error looking for next uid in sambaDomainName=WORKGROUP,dc=home,dc=come:invalid DN at /usr/share/perl5/smbldap_tools.pm line 1071, <DATA> line 466.
```
 
I am totally clueless as this is the new version of OPENldap with their new cn=config idea. It's been LOADS of fun so far (3 days searching for the right guide to even set it up!!!) I'll put a new reply with the contents of smbldap_tools.pm.
 
I'm getting all of this trouble in an ongoing search on how to add users to OPENldap with Samba abilities. I'm trying to create a free version of Novell Netware server using Linux however. The only thing I'm stuck on is the Single-Sign on thing. I'm not sure if I should use Kerberos either. If anybody could point me in the right direction or give a clear guide it would be GREATLY appreciated.
 
Current Setup:
Ubuntu Server 9.10
Openldap 2.4
 
I also am wondering how to have the ldap server or client setup so that when a user logs on it automatically maps certain folder as set drive letters. My network is all Windows computers.
Thank you very much in advance! I know this is a tall order.

---

### Post by tristanhall on 2009-11-12
I've figured this out now.

---

