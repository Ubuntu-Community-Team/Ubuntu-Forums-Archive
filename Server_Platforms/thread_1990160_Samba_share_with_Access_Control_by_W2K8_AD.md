---
title: "Samba share with Access Control by W2K8 AD"
date: 2012-05-29
forum: Server Platforms
---

### Post by falcovd on 2012-05-29
Dear readers,

I am trying to have a Samba share who has its User control on a Windows Server 2008 Active Directory.
I've spent a lot of time with Google to find the solution but i can't figure it out.

This is my smbd.conf
[global]
workgroup = *Domainname*
passdb backend = ldapsam:ldap://dc01.*Domain*.nl
domain master = no
domain logons = yes
ldap suffix = dc=*Domain*,dc=nl
ldap user suffix = ou=Users
ldap group suffix = ou=Groups
ldap machine suffix = ou=Computers
ldap idmap suffix = ou=Idmap
ldap admin dn = cn=Users,dc=*Domain*,dc=nl
ldap ssl = off 
ldap passwd sync = yes
idmap backend = ldap:ldap://dc01.*domain*.nl
idmap uid = 10000-20000
idmap gid = 10000-20000

[share]
path = /home/share
comment = 'Samba als Slave'

After restarting samba, the log files will be filled with:
lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 15 try!

after a ldapsearch command i've got the following output:
ldapsearch -h DC01.*domain*.nl -D "cn=Administrator,cn=Users,dc=*domain*,dc=nl" -w mypass
ldap_bind: Invalid credentials (49)
    additional info: 80090308: LdapErr: DSID-0C0903A9, comment: AcceptSecurityContext error, data 52e, v1db1

I am sure i've used the correct credentials. 

Does someone has a solution for me?

---

### Post by luvshines on 2012-06-10
Maybe you have already figured it out and I am too late to reply

Why are you trying ldap configuration with a Windows AD server ? I don't think that will be possible

Have you tried this:
[http://ubuntuforums.org/showthread.php?t=1580505](http://ubuntuforums.org/showthread.php?t=1580505)

---

