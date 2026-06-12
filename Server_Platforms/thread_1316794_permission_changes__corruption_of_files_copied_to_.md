---
title: "permission changes / corruption of files copied to samba share"
date: 2009-11-06
forum: Server Platforms
---

### Post by waspinator on 2009-11-06
Hi,

I'm using ubuntu as both the server and the client. (ubuntu server, and ubuntu desktop)

I have ebox installed, and I created some file shares using it and the samba module. 

Whenever I copy a file to a shared folder, (from ubuntu desktop) it changes the permissions and ownership of the files.
Example:

I have this file on my desktop, and it has the following permissions as seen by ls -l
```
-rw-r--r-- 1 waspinator waspinator    26424 2009-11-04 20:50 ubuntu-9.10-server-amd64.iso.torrent
```

I can open this file up in transmission or rtorrent, and it will begin to download ubuntu.

Now when I copy this file to the samba shared folder the permissions and ownership of the files change to:
```
-rwxr--r-- 1 root          __USERS__     26424 Nov  4 20:50 ubuntu-9.10-server-amd64.iso.torrent
```

I can no longer open this file in transmission or rtorrent. Now it says that the file is corrupt.

Even if I copy the file back, and I change the permissions, it still cannot be opened by transmission/rtorrent.

I am worried that samba is messing with my files. I removed "force create mode" in
/usr/share/ebox/stubs/samba/smb.conf.mas but that did not help. I also removed "enable privileges = yes", but nothing changed either.

here is my smb.conf file that ebox generates:
```
[global]
 workgroup = WASPNET
 netbios name = server
 server string = Ubuntu Samba Server
 interfaces = lo,eth1
 bind interfaces only = Yes
 passdb backend = ldapsam:ldapi://%2fvar%2frun%2fslapd%2fldapi
 ldap ssl = Off
 log level = 1
 syslog = 0
 log file = /var/log/samba/%m
 max log size = 50
 vfs objects = full_audit
 full_audit:success = connect opendir open disconnect unlink mkdir rmdir rename
 full_audit:failure = none
 smb ports = 137 138 139 445
 name resolve order = wins bcast hosts
 time server = Yes
 printcap name = CUPS
 wins support = Yes
 dns proxy = Yes
 ldap suffix = dc=example,dc=org
 ldap machine suffix = ou=Computers
 ldap user suffix =  ou=Users
 ldap group suffix =  ou=Groups
 ldap idmap suffix = ou=Idmap
 ldap admin dn = cn=ebox,dc=example,dc=org
 map acl inherit = Yes
 printing = cups

 encrypt passwords = Yes
 obey pam restrictions = No
 ldap passwd sync = Yes
 mangling method = hash2

 logon script = logon.bat
 logon drive = H:
 logon home =
 logon path =

 domain logons = Yes
 os level = 65
 preferred master = Yes
 domain master = Yes
 add user script = /usr/sbin/smbldap-useradd -m "%u"
 ldap delete dn = Yes
 add machine script = /usr/sbin/smbldap-useradd -w "%u"
 add group script = /usr/sbin/smbldap-groupadd -p "%g"
add group script = /usr/sbin/smbldap-groupadd -p "%g"
 add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
 delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
 set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"

 [netlogon]
        path = /home/samba/netlogon/
        browseable = No
        read only = yes

 [profiles]
        path = /home/samba/profiles
        read only = no
        create mask = 0600
        directory mask = 0700
        browseable = No
        guest ok = Yes
        profile acls = yes
        csc policy = disable
        valid users = %U
        admin users = @"Domain Admins"

 [netlogon]
        path = /home/samba/netlogon/
        browseable = No
        read only = yes

 [profiles]
        path = /home/samba/profiles
        read only = no
        create mask = 0600
        directory mask = 0700
        browseable = No
        guest ok = Yes
        profile acls = yes
        csc policy = disable
        valid users = %U
        admin users = @"Domain Admins"


[homes]
 comment = Home Directories
 valid users = %S
 read only = No
 browseable = No



[torrents]
 comment = Torrent Downloads
 path = /downloads/torrents
 valid users = "waspinator"
 read list = 
 write list =
 admin users = "waspinator"
 read only = No
 browseable = Yes




```

I just want a simple file server, that stores my files without doing anything to them. Just like any other storage area on my desktop. 

What do I need to change to my smb.conf to fix this?

Thanks,

Waspinator

---

### Post by waspinator on 2009-11-07
bump

---

### Post by redmk2 on 2009-11-08
> **waspinator said:**
> bump

One can only guess at whether you problems are Samba related or due to eBox.  For sure it is some sort of misconfiguration.  This is not a known problem with Samba (or Ubuntu).

I am a long time user of Samba, but have never used eBox to configure it.  It appears that eBox significantly alters the standard configuration.  A lot of the configuration in your smb.conf file appear to be peculiar to eBox.  Even the smb.conf file has been moved from its traditional location.

This is the reason webmin was dropped.  Too many deviations from the standard Ubuntu/Samba implementation.

Sorry to say, I think you will have more luck at the eBox forum.

---

