---
title: "Samba is not authenticating with LDAP"
date: 2013-04-02
forum: Server Platforms
---

### Post by j4ckripp3r on 2013-04-02
Hello Everyone.

I've just setup an HP Proliant server running Ubuntu Precise 64bit. I also have another server running precise which has an OpenLDAP server running on it. I'm trying to get the Samba server to authenticate with my LDAP server so users will be able to log into Samba using their LDAP credentials.

I followed the directions on this site:
[http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap.html](http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap.html)
[http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap_28.html](http://raerek.blogspot.com/2012/05/samba-pdc-on-ubuntu-1204-using-ldap_28.html)

I'm using a Mac running mountain lion to connected to the samba share but when I do I get this message:
"Check the server name or IP address, and then try again. If you continue to have problems, contact your system administrator."

When I go into /var/log/samba/log.workstation
[2013/04/02 21:56:33.187358,  0] auth/check_samsec.c:491(check_sam_security)
  check_sam_security: make_server_info_sam() failed with 'NT_STATUS_UNSUCCESSFUL'

> $ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[OH-Fileshare]"
Global parameter encrypt passwords found in service section!
Global parameter unix password sync found in service section!
Global parameter passwd program found in service section!
Global parameter passwd chat found in service section!
Global parameter pam password change found in service section!
Global parameter map to guest found in service section!
Global parameter domain logons found in service section!
Global parameter usershare allow guests found in service section!
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
 
[global]
    workgroup = OS
    server string = %h server (Samba, Ubuntu)
    passdb backend = ldapsam:ldap://10.12.10.4
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    add user script = /usr/sbin/smbldap-useradd -m '%u'
    add machine script = /usr/sbin/smbldap-useradd -w '%u'
    dns proxy = No
    wins support = Yes
    ldap admin dn = cn=admin,dc=onerecovery,dc=net
    ldap group suffix = ou=Groups
    ldap idmap suffix = ou=Idmap
    ldap machine suffix = ou=Computers
    ldap passwd sync = yes
    ldap suffix = dc=onerecovery,dc=net
    ldap ssl = no
    ldap user suffix = ou=People
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[OH-Fileshare]
    comment = OS Fileshare
    path = /srv/fileshare
    read only = No
    create mask = 0775
    force create mode = 0775
    force security mode = 0775
    directory mask = 0775
    force directory mode = 0775
    force directory security mode = 0775


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No



I'm not too sure where I'm going wrong here so any help is appreciated.

---

### Post by j4ckripp3r on 2013-04-03
bump....

---

### Post by j4ckripp3r on 2013-04-04
bump!

---

### Post by luvshines on 2013-04-07
On the Ubuntu samba server, does user authentication succeed ?
```
smbclient -L localhost -U<ldap-user-name>%<ldap-user-passwd>
```

Also what does following say```
sudo net getlocalsid
```

We'll also need to have look at the user attributes for the user from ldap server to check if all the required attributes have been populated

---

