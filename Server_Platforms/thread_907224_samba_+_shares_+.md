---
title: "samba + shares +"
date: 2008-09-01
forum: Server Platforms
---

### Post by byte_slave on 2008-09-01
Hi,

I configured Samba 3 + Windows AD access in ubuntu 8.0.4 and i got it working, at least i do a "wbinfo -u" or "-g" and i can see AD Groups and Users correctly.

The problem is that i guess these existing groups and users didn't figure yet inside /etc/passwd and /etc/group because when using the "getent" command only the native linux users and groups are displayed.

Due this i cannot setup samba shares with Domain permissions correctly.

Anyone know if i miss some step or what you i do to "pump" AD users and groups to be available in my machine and then use it to set the apropriate permissions in my files and folders?

Thank you very much.
Best regards,
Teixeira

---

### Post by puppywhacker on 2008-09-01
I don't use or understand Active Directory, other than it's an LDAP server.

The users and groups are by default stored in the passwd, shadow and groups files you mentioned, but for the AD you need to also specify that the users can also exist in ldap. so you have users in both files and ldap.

/etc/nsswitch.conf
passwd:         files ldap
group:          files ldap
shadow:         files ldap

I think you want to take a look at either links, 

[OpenLDAP-SambaPDC-OrgInfo]("https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix#Option:%20LDAP%20Authentication%20on%20Clients")

[LDAP-tastic]("http://times.usefulinc.com/2005/09/25-ldap")

---

### Post by RandomJon on 2008-09-02
If you are using winbind your nsswitch.conf entries for group and passwd (and shadow?) should be "compat winbind" if your using likewise to join the domain they should be "compat lwidentity".

In either case you need winbind enum users =yes and winbind enum groups = yes in the relevant config file (smb.conf for winbind and lwiauthd.conf for likewise)

---

