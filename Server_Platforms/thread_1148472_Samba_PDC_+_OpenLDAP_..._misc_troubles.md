---
title: "Samba PDC + OpenLDAP ... misc troubles"
date: 2009-05-04
forum: Server Platforms
---

### Post by daniele_dll on 2009-05-04
Hi to all,

i've setted up a samba pdc but this time i used ldap as backend (this is the first time i use ldap :))

for first, my configuration ... i've setted up a dell t300 with an ubuntu server as host for three vm using vmware server 2.0.1. These virtual machine runs one windows xp and two ubuntu server, the first for a web application and the second for the pdc!

All datas are on the host trought nfs (i've disabled kernel oplocks for performance reasons)

Software versions are:
- ubuntu server 8.10
- samba 3.2.3
- slapd 2.4.11

On the end of the post there is samba configuration.

### FIRST QUESTION:
after some troubles to setting up openldap as provider for users and groups and setting up samba correctly with openldap i've noticed a strange behaviour.

When i join a windows machine to the samba server in user creating phase it will give an error about untrusted relation between server and workstation ... but after a minute or two it goes ahead correctly!

This is a known problem? A normal behavior?


### SECOND QUESTION
can i change the root user, used by samba as administrator, to something like Administrator or, however, to another user? Actually PAM uses files first but i didn't like to have two user with the same name (getent passwd return two root users!)

Can i use ldaprenameuser?

Here there is the root dn:
```

dn: uid=root,ou=Users,dc=cassaedile
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: sambaSamAccount
objectClass: posixAccount
objectClass: shadowAccount
gidNumber: 0
uid: root
uidNumber: 0
sambaLogonTime: 0
sambaLogoffTime: 2147483647
sambaKickoffTime: 2147483647
sambaProfilePath: \\%L\Profiles\root
sambaPrimaryGroupSID: S-1-5-21-3889976431-1177284050-1071102827-512
sambaSID: S-1-5-21-3889976431-1177284050-1071102827-500
loginShell: /bin/false
gecos: Netbios Domain Administrator
structuralObjectClass: inetOrgPerson
entryUUID: 9aa5fb34-c9b6-102d-9faa-c7f1ab29e7a1
creatorsName: cn=admin,dc=cassaedile
createTimestamp: 20090430093954Z
sn: Administrator
sambaPwdCanChange: 2147483647
cn: Administrator Administrator
givenName: Administrator
displayName: Administrator Administrator
homeDirectory: /storage/samba/homes/root
sambaNTPassword: xxxxxxx
sambaPwdMustChange: 9881001666
shadowLastChange: 14364
shadowMax: 99999
sambaPasswordHistory: xxxxxx
sambaPwdLastSet: 1241088351
sambaAcctFlags: [U          ]
userPassword:: xxxxxx
entryCSN: 20090430104551.398166Z#000000#000#000000
modifiersName: cn=admin,dc=cassaedile
modifyTimestamp: 20090430104551Z

```

### THIRD AND LAST QUESTION (less important!)
Actually ldapscripts use really high ids because the nobody user have the last usable id ... there is a param to force to start from a lower id?

--------------

Here there is my samba configuration (with testparm)
```

root@pdc:/var/log/samba# testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[netlogon]"
Processing section "[Profiles]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
        workgroup = CASSAEDILE
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        passdb backend = ldapsam:ldap://localhost
        log level = 2
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 100000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        show add printer wizard = No
        add machine script = sudo /usr/sbin/smbldap-useradd -w -t 5 "%u"
        logon script = logon.cmd
        logon path = \\%L\Profiles\%U
        logon home = ""
        domain logons = Yes
        os level = 64
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        kernel oplocks = No
        ldap admin dn = cn=admin,dc=cassaedile
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        ldap machine suffix = ou=Computers
        ldap passwd sync = Yes
        ldap suffix = dc=cassaedile
        ldap user suffix = ou=Users
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = Yes
        winbind enum groups = Yes
        admin users = root

[netlogon]
        comment = Network Logon Service
        path = /storage/samba/netlogon
        guest ok = Yes
        share modes = No

[Profiles]
        comment = Users profiles
        path = /storage/samba/profiles
        valid users = %U, @"Domain Admins"
        force user = %U
        read only = No
        create mask = 0600
        directory mask = 0700
        profile acls = Yes
        browseable = No

```

---

### Post by PoolSnoopy on 2009-05-07
have you managed to join windows machines to the samba domain? And if so which release of Ubuntu are you using?
I get these lines in the samba log file and don't know how to handle them:
```

[2009/05/07 12:00:04,  3] passdb/pdb_interface.c:pdb_default_create_user(342)
  _samr_create_user: Running the command `sudo /usr/sbin/smbldap-useradd -w -t 5 "latvmie6$"' gave 0
[2009/05/07 12:00:04,  3] passdb/pdb_interface.c:pdb_default_create_user(359)
  pdb_default_create_user: failed to create a new user structure: NT_STATUS_NO_SUCH_USER

```

the wierd thing is that the machine account is properly added in the ldap directory, but the windows client fails adding itself to the domain with a 'user not found' error.
When I try to add the machine I'm asked for user and password. I provide the credentials of the domain admin and according to the samba log files authentication runs fine.

---

### Post by daniele_dll on 2009-05-07
In the end i succeded in doing all the stuff :)

Here there is the lastest configuration file i setted up

```

[global]
        workgroup = CASSAEDILE
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        passdb backend = ldapsam:ldap://localhost
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 100000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        show add printer wizard = No
        add machine script = sudo /usr/sbin/smbldap-useradd -w -t 5 "%u"
        logon script = logon.cmd
        logon path = \\%L\profiles\%U
        logon drive = Z:
        logon home = \\%L\%U
        domain logons = Yes
        os level = 64
        preferred master = Yes
        domain master = Yes
        dns proxy = No
        wins support = Yes
        ldap admin dn = cn=admin,dc=cassaedile
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        ldap machine suffix = ou=Computers
        ldap passwd sync = Yes
        ldap suffix = dc=cassaedile
        ldap user suffix = ou=Users
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = Yes
        winbind enum groups = Yes
        admin users = root
        write cache size = 65536

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0600
        directory mask = 0700
        browseable = No

[netlogon]
        comment = Network Logon Service
        path = /storage/samba/netlogon
        guest ok = Yes
        share modes = No

[profiles]
        comment = Users profiles
        path = /storage/samba/profiles
        valid users = %U, "@Domain Admins"
        force user = %U
        read only = No
        create mask = 0600
        directory mask = 0700
        profile acls = Yes
        browseable = No


```

You could check if the machine is in ldap trought slapcat (as root user) or using smbldap-tools

you need to install libnss-ldap and libpam-ldap or auth will fail

---

### Post by PoolSnoopy on 2009-05-07
first of all thanks for your reply.

could you show me what a machine account is looking like on your side after you added it to the domain?
what I don't understand is that the "add machine script" is working fine. As I mentioned the machine account is in the LDAP directory afterwards. But still the windows client shows me a 'user not found' error and fails to add to the domain.
When I try to add the machine to the domain the authentication as domain admin also works fine according to the samba log files.
Are you using Ubuntu 8.10 or later? It seems that a lot changed in openldap compared to the many howtos in the net describing how to set this up on 7.10. :-)

---

### Post by daniele_dll on 2009-05-07
simply you should found something like

uid=machine-name$,..........

have you enabled ldap pam/nss support?

look at LDAP Authentication section of [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html) page.

On help.ubuntu.com you will found samba ldap related info too

---

### Post by halensmith01 on 2009-05-12
When I try to add the machine to the domain the authentication as domain admin also works fine according to the samba log files.

---

### Post by PoolSnoopy on 2009-05-12
well I finally gave up and will now use samba without LDAP. I'm quite disappointed, that it is not quite straight forward. it took me 10 minutes to get rid of LDAP and adding a windows client works like a charm now.

---

### Post by daniele_dll on 2009-05-12
> **halensmith01 said:**
> When I try to add the machine to the domain the authentication as domain admin also works fine according to the samba log files.

check if them are really added looking the output of
```

sudo slapcat

```

and, if yes, check if you have installed nss/pam ldap support and you have switched to ldap authentication on your system.

---

