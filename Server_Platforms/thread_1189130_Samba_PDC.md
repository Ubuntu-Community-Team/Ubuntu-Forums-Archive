---
title: "Samba PDC"
date: 2009-06-16
forum: Server Platforms
---

### Post by Darrarski on 2009-06-16
There is a lot of tutorials how to setup samba as primary domain controller. I've read almost all of them, and still can't setup PDC correctly.
My configuration is mainly based on informations from this faq: [https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html) and samba documentation. The problem is that I can not add a machine to my domain. I'm trying on Windows XP Pro, entering domain name, then LOG-IN window appears (so, the system actually sees my server as domain controller), but next I'm getting error message: user could not be found on server (I'm using special user, that was created for adding machines to my domain, according to the faq). In the samba logs I've something like this:
> [2009/06/16 20:38:20, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 544 (NT_STATUS_UNSUCCESSFUL)
[2009/06/16 20:38:20, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2009/06/16 20:38:20, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 545 (NT_STATUS_UNSUCCESSFUL)
[2009/06/16 20:38:20, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2009/06/16 20:38:20, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 544 (NT_STATUS_UNSUCCESSFUL)
[2009/06/16 20:38:20, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2009/06/16 20:38:20, 0] groupdb/mapping.c:pdb_create_builtin_alias(739)
  pdb_create_builtin_alias: Could not add group mapping entry for alias 545 (NT_STATUS_UNSUCCESSFUL)
[2009/06/16 20:38:20, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[sudo] password for dcadmin: 
[2009/06/16 20:38:22, 0] passdb/pdb_interface.c:pdb_default_create_user(329)
  _samr_create_user: Running the command `sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false komp1$' gave 1
I'm attaching my smb.conf file. Please, help my with configuring Ubuntu as a domain controller, as I don't know where to find help anymore. 
I'm using Ubuntu Server 8.04 x64, for easy administration I've installed Webmin. I need server with simple management abilities, so machine account should be created when I'm trying to join the domain from Windows client, domain users should have automatically created unix accounts (and vice versa), I need roaming profiles too. I don't know if I need LDAP, at the moment I want to have domain controller just working for testing purposes.
I will be thankful for any advice.

---

### Post by rshprd on 2009-06-16
Been down this road myself.  

You will require LDAP, and if you want some security probably Kerberos as well, which if you think samba is bad, is a bigger PIA.  Even then, if you read a lot of the examples the good ones caution that you cannot completely emulate a Windows PDC, but you can get close.

Bottom line, Samba alone will not replace and/or act as a PDC.

---

### Post by ghen on 2009-06-17
rshprd is right on. I'm in this boat myself. The tutorial you linked named Samba a domain controller, but the unfortunate truth is much smaller. Samba is a translator and ambassador from linux to windows. Its not a domain controller at all which I describe as "centralized administration"

To get the equivalent of a active directory domain controller you'll need 3 basic functions that I can think of. User authentication, DNS, and group policy. The first two are relatively easy in the fact that they -exist-... But the last one is impossible AFAIK without having a pure linux environment and no windows clients.

The best I've found for group policy replacement is FreeIPA and as far as I can tell it is linux only. And it hasn't been touched since December 3, D'oh.



So if you don't need group policies and can live with just using logon scripts you can create a semi-decent linux domain controller. You'll need OpenLDAP, Kerberos support of some kind, a DNS service like Bind9, and of course Samba to make them play nice and share files. The connection between Samba and OpenLDAP is exceedingly complex, but definitely within reach. I also recommend making it an NTP server since windows time management leaves a bit to be desired.

---

