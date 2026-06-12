---
title: "SAMBA4 AD DC and ADS fileserver idmap acls not honored"
date: 2017-01-19
forum: Server Platforms
---

### Post by rvwbug on 2017-01-19
Greetings,

I have Ubuntu 16.04 AD DC installed using apt.

```
[FONT=arial]apt-get install samba [/FONT][COLOR=#000000][FONT=arial]krb5-config winbind [/FONT][/COLOR][COLOR=#000000][FONT=arial]smbclient [/FONT][/COLOR][COLOR=#000000][FONT=arial]krb5-user [/FONT][/COLOR][COLOR=#000000][FONT=arial]libnss-winbind[/FONT][/COLOR]
```

smb.conf
```
[global]
    workgroup = EVENTS
    realm = EVENTS.DOMAIN.COM
    netbios name = DC1
    server role = active directory domain controller
    dns forwarder = 10.10.10.1
    idmap_ldb:use rfc2307 = yes


[netlogon]
    path = /var/lib/samba/sysvol/events.domain.com/scripts
    read only = No


[sysvol]
    path = /var/lib/samba/sysvol
[FONT=Menlo]    [/FONT][FONT=Menlo]read only = No[/FONT]
```

/etc/nsswitch.conf
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat
gshadow:        files


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


[FONT=Menlo]netgroup:       nis[/FONT]
```

On domain controller 

```
root@dc1:/etc/samba# wbinfo -i 'EVENTS\marty'
EVENTS\marty:*:3000021:100:Marty Bathrick:/home/EVENTS/marty:/bin/false
```

I also have an member server to act as file server Ubuntu 16.04 installed:
```
apt-get install samba krb5-config winbind smbclient krb5-user libnss-winbind
```

smb.conf
```
[global]    server string = %h server (Samba, Ubuntu)
    security = ADS
    workgroup = EVENTS
    realm = EVENTS.DOMAIN.COM
       log file = /var/log/samba/%m.log
       log level = 1
    username map = /etc/samba/user.map
       # Default ID mapping configuration for local BUILTIN accounts
       # and groups on a domain member. The default (*) domain:
       # - must not overlap with any domain ID mapping configuration!
       # - must use an read-write-enabled back end, such as tdb.
       idmap config * : backend = tdb
       idmap config * : range = 3000-7999
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        client ntlmv2 auth = yes
        encrypt passwords = yes
        winbind use default domain = yes
        restrict anonymous = 2
    vfs objects = acl_xattr
    map acl inherit = yes
    store dos attributes = yes
    inherit permissions = Yes
    directory mask = 0775
    create mask = 0775
    veto files = /.*/ 




[PTShared]
        comment = Party Track Shared Files
        path = /srv/PartyTrackShared
    browseable = Yes
    read only = No
    vfs objects = acl_xattr full_audit
    acl_xattr:ignore system acls = yes
    full_audit:success = connect opendir disconnect unlink mkdir rmdir open rename
    full_audit:failure = connect opendir disconnect unlink mkdir rmdir open rename
    hide dot files = yes
    hide unreadable = yes


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
root@FS1:/etc/samba# 



```

/etc/nsswitch.conf
```
passwd:         compat winbindgroup:          compat winbind
shadow:         compat
gshadow:        files


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis
```

On member server:
```
root@FS1:/etc/samba# wbinfo -i 'EVENTS\marty'
marty:*:3001:3000:Marty Bathrick:/home/EVENTS/marty:/bin/bash
```


Should the id be the same as result from AD DC?

Issue I'm having is related to file permissions.

Setting acls on directories seem to be ignored (I have to have owner or group permissions for file access as the extended permissions seem to be ignored).

With windows 10 client, If I try to change file permissions, I see a warning/error:
```
unable to contact active directory to verify claim types
```

I can change permissions with Explorer ie set 'domain users' full permissions, but they are ignored
and not reflected when checking with "getfacl" on linux side.

I don't have the same symptom if I change file permissions on shared directory on the AD DC server. I can add a user or group
to file permissions in Explorer and the change is reflected when checking "getfacl".

Following SAMBA4 wiki I see references to "winbind" is setup differently for AD DC vs member server, but I don't
find specifics.  I'm unable to find a current instruction set for comprehensive setup AD DC + Member server.
SAMBA4 Wiki recommends separate fileserver not on AD DC, but again not comprehensive instructions for setting
up the infrastructure.

I'm not sure if I have idmap issue or simply filesystem problem. The windows error "unable to contact active directory to verify claim types" leads
me to believe it's not filesystem or acl issue directly.

Thanks in advance!

---

### Post by volkswagner on 2017-01-19
The OP is actually me (volkswagner).
I cleared cache in my browser and didn't realize I logged into the wrong account (one left over from the major forum change a few years back).

Anyway, I'd like to add another symptom (not sure if it's related).

Windows 10 clients don't get added to DNS (samba_internal), but Linux fileserver/domain member did.

Since realizing there wasn't an A record for the client, I added one via RSAT DNS. nslookup now works
when using FQDN but not short name. Even with DNS entry I still get error message when modifying permssions
via Explorer on share sub folders "unable to contact active directory to verify claim types"

---

### Post by volkswagner on 2017-01-19
Well, it seem I'm implementing things I know nothing about.

Disabling:
```
acl_xattr:ignore system acls = yes
```

Corrected the problem with Windows clients not reading extended acls.

It seems I need some learning on the following:
acl_xattr:ignore system acls = yes
vfs objects = acl_xattr
map acl inherit = yes
idmap

and a whole lot more I'm sure!

PS: it seems "acl_xattr:ignore system acls = yes" has different behavior when run on an AD DC vs member.

---

### Post by volkswagner on 2017-01-19
Now that I know "what" to search, I see
"acl_xattr:ignore system acls = yes" behavior possibly changed?
[https://www.spinics.net/lists/samba/msg136465.html](https://www.spinics.net/lists/samba/msg136465.html)

---

