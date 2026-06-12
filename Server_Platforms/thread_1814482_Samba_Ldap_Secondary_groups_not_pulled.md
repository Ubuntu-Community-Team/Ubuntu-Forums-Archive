---
title: "Samba Ldap Secondary groups not pulled"
date: 2011-07-29
forum: Server Platforms
---

### Post by skinnyquiver on 2011-07-29
Samba version is 3.4.7
System is Ubuntu 10.04.2 LTS

What works is everything except secondary groups users cannot view or edit files owned by secondary groups. 

I am not using winbind as i need to be able to access this server from ftp with the same uid and gid on each system

I have this system authenticating to my AD 2008 server pam is working fine getent group shows all the groups and id shows all the correct groups and correct gids.

Samba shows correct uid and primary gid but it is not honoring secondary gids

if I have not provided enough information ask for more

Thanks for your help


smb.conf
[global]
       security = ADS
       realm = some.domain
       workgroup = domain
       encrypt passwords = yes
       template shell = /bin/bash
       server string = somedomainshare
       wins support = Yes
       syslog = 1
       log file = /var/log/samba/log.%m
       max log size = 1000
       guest account = nobody
       map to guest = bad user
       passdb backend = ldapsam:ldaps://dc1.some.domain:636/
       ldap ssl = off
       ldap suffix = cn=users,dc=some,dc=domain
       ldap admin dn = cn=binduser,cn=users,dc=some,dc=domain
       ldap passwd sync = No
       ldap user suffix = cn=users
#Removes Printers
        printcap name = /etc/printcap
        load printers = no

[homes]
        comment = Home Directory for %U
        root preexec = /usr/local/sbin/mkhomedir.sh %U %P
        read only = No
        browseable = Yes
        valid users = %S
        vfs object = recycle
        recycle:repository = .trash
        recycle:keeptree = yes
        recycle:exclude = *.tmp, *~, *.bak

[share]
        comment = publicly accessible share
        read only = No
        browsable = Yes
        writeable = Yes
        force group = share
        guest ok = yes
        path = /share/

[groups]
        comment = Shared Group Directories
        path = /home/groups
        browseable = Yes
        read only = No

---

### Post by skinnyquiver on 2011-09-28
I changed to using winbind and Kerberos for samba as ldap has known issues with this.

---

