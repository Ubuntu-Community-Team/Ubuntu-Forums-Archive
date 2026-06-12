---
title: "Samba/LDAP issues"
date: 2013-03-28
forum: Server Platforms
---

### Post by sdmike6 on 2013-03-28
I'm fixing an issue with Samba not being able to authenticate with LDAP. Samba externally authenticates with an OpenLDAP server. When I create a user on LDAP and then go into the samba server and run $ getent passwd, I see the user there. Even though the user appears samba is still not letting that user authenticate. This is what I'm seeing in one of the samba log files. I've been working on this for two days and I'm not quite sure how to resolve this.

```
==> log.workstation <==
[2013/03/28 16:48:17.417727,  0] auth/auth_sam.c:493(check_sam_security)
  check_sam_security: make_server_info_sam() failed with 'NT_STATUS_NO_SUCH_USER'
[2013/03/28 16:48:17.548388,  0] smbd/map_username.c:140(map_username)
  can't open username map /etc/samba/smbusers. Error No such file or directory
[2013/03/28 16:48:17.549368,  0] passdb/pdb_get_set.c:212(pdb_get_group_sid)
  pdb_get_group_sid: Failed to find Unix account for batman
[2013/03/28 16:48:17.549524,  1] auth/auth_util.c:580(make_server_info_sam)
  User batman in passdb, but getpwnam() fails!
[2013/03/28 16:48:17.549557,  0] auth/auth_sam.c:493(check_sam_security)
  check_sam_security: make_server_info_sam() failed with 'NT_STATUS_NO_SUCH_USER'

```

---

### Post by bab1 on 2013-03-28
Are you using Samba 3 or Samba 4? 

If it is Samba 3 then I'll bet you need to add the user to the smbpasswd database like this ```
smbpasswd -a <username>
```... You can see who is in the database with this ```
sudo pdbedit -L
```

I have no Samba 4 experience, but I believe this is all handled internally in LDAP as there is no smbpasswd per se.

---

### Post by sdmike6 on 2013-04-05
I went onto the LDAP server and ran:
```
smbpasswd -a someuser
```

Then I went onto the samba fileshare server and ran:
```
sudo pdbedit -L
```

I'm seeing a bunch of this:
```
sid S-1-5-21-1713727836-2215038221-1160323130-3062 does not belong to our domain
sid S-1-5-21-3060199750-4236102679-2651694663-1002 does not belong to our domain
sid S-1-5-21-1713727836-2215038221-1160323130-3072 does not belong to our domain
sid S-1-5-21-3060199750-4236102679-2651694663-1003 does not belong to our domain

```


Now on the samba server when I run:
```
sudo getent group

```
I see all the groups come in from LDAP.

When I run:
```
sudo getent passwd

```
I see all the users coming in, even the new ones I created briefly on the LDAP server.

---

### Post by luvshines on 2013-04-07
What does following return on Samba server ?```
testparm -s
```

---

### Post by sdmike6 on 2013-04-08
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[OR-Fileshare]"
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
[global]
    workgroup = OR
    server string = %h server (Samba, Ubuntu)
    passdb backend = ldapsam:ldap://10.12.10.4
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    add user script = /usr/sbin/smbldap-useradd -m '%u'
    add machine script = /usr/sbin/smbldap-useradd -w '%u'
    dns proxy = No
    wins support = Yes
    ldap admin dn = cn=admin,dc=mainoffice,dc=net
    ldap group suffix = ou=Groups
    ldap idmap suffix = ou=Idmap
    ldap machine suffix = ou=Computers
    ldap passwd sync = yes
    ldap suffix = dc=mainoffice,dc=net
    ldap ssl = no
    ldap user suffix = ou=People
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[OH-Fileshare]
    comment = OR Fileshare
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

```

---

### Post by luvshines on 2013-04-08
I am asking a dumb question.
Did you carry out the steps for adding samba schema on LDAP server and additional steps required for configuring samba with LDAP as authentication backend(smbpasswd -W, net getlocalsid etc) ?

---

### Post by sdmike6 on 2013-04-08
Originally there was a server running samba on Ubuntu 11.04 that was authenticating externally with LDAP. The servers hardware needed to be replaced so everything has been migrated over to a new server running Ubuntu 12.04. 

So [COLOR=#000000]adding samba schema on LDAP server and additional steps required for configuring samba with LDAP for authentication backend has already been done. (smbpasswd -W, net getlocalsid etc) ?

I've already run smbpasswd -W on the new server and net getlocalsid is: [/COLOR]SID for domain VAULT is: S-1-5-21-3824860550-1351888951-1520703921

---

### Post by luvshines on 2013-04-09
Ok, if that's the case, then simply increase the samba log level ```
sudo smbcontrol smbd debug 10
```
Clean the existing log file for samba. Try user access ```
smbclient -L localhost -U<username>%<password>
``` and let if fail.
Then check samba log file for the error reported

May want to revert log level after this activity

---

