---
title: "Ubuntu fails to resolve Samba share owners"
date: 2012-01-16
forum: Server Platforms
---

### Post by vikfreeze on 2012-01-16
Hi,

i have a Samba server(on 10.04 Server with LDAP authentication) set up and working as i expect it to, at least with Windows clients.
In Ubuntu 11.10 theres something strange happening, the owner of the files and permissions in nautilus show "unknown", in the command line it shows me(local client user) as the owner, witch  know is not true.
The error only seems to be aesthetic since i cant actually do anything that is against the rules permitted to the user witch i am logged in the Samba with, but its confusing to have those weired permissions show up.

Does anyone know why the owners aren't resolved properly as they are in windows?:confused:

[global]
    workgroup = namehere
    netbios name = namehere
    server string = namehere
    client schannel = No
    server schannel = No
    obey pam restrictions = Yes
    passdb backend = ip here
    pam password change = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    load printers = No
    add user script = /usr/sbin/smbldap-useradd -m '%u'
    rename user script = /usr/sbin/smbldap-usermod -r '%u'
    delete user script = /usr/sbin/smbldap-userdel %u
    add group script = /usr/sbin/smbldap-groupadd -p '%g'
    delete group script = /usr/sbin/smbldap-groupdel '%g'
    add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
    delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
    set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
    add machine script = /usr/sbin/smbldap-useradd -w '%u'
    logon script = allusers.bat
    logon path = 
    logon home = 
    domain logons = Yes
    os level = 35
    domain master = Yes
    dns proxy = No
    wins support = Yes
    ldap admin dn = cn=adm...
    ldap group suffix = ou=Groups
    ldap passwd sync = yes
    ldap suffix = dc=l...
    ldap ssl = no
    ldap user suffix = ou=Users
    panic action = /usr/share/samba/panic-action %d

[homes]
    comment = Home Directories
    valid users = %S
    admin users = victor
    read only = No
    acl group control = Yes
    create mask = 0750
    directory mask = 0750
    inherit owner = Yes
    browseable = No
    browsable = No

[public]
    comment = Public for LTI
    path = /mnt/public
    admin users = victor
    force group = lti
    read only = No
    acl group control = Yes
    create mask = 01770
    force create mode = 01770
    directory mask = 01770
    force directory mode = 01770

---

