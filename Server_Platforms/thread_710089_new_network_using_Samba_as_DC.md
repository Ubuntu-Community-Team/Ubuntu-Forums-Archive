---
title: "new network using Samba as DC"
date: 2008-02-28
forum: Server Platforms
---

### Post by aknight_sa on 2008-02-28
good day all,

i have configured a PC at our small office to work as a domain controller for our network. i was able to make PC's join the domain but i am getting messages stating that windows wasnt able to locate the roaming profile, then followed by another one saying that it was going to use a temporary profile. i tried a lot of solutions off the net but didnt work.. 
what i also need to do is make a common shared folder where only domain users can have access.

please help guys.

here is my smb.conf

******************************************

[global]
# passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
# delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
# passwd program = /usr/bin/passwd %u
dns proxy = no
ldap passwd sync = Yes
workgroup = SUMITOMO-KAUST
ldap admin dn = cn=admin,dc=sumitomo-kaust,dc=local
add machine script = /usr/sbin/smbldap-useradd -w "%u"
delete user script = /usr/sbin/smbldap-userdel "%u"
max log size = 1000
log file = /var/log/samba/log.%m
ldap user suffix = ou=Users
add group script = /usr/sbin/smbldap-groupadd -p "%g"
delete group script = /usr/sbin/smbldap-groupdel "%g"
add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
logon drive = Z:
winbind trusted domains only = yes
encrypt passwords = true
passdb backend = ldapsam:ldap://localhost/
ldap delete dn = Yes
ldap machine suffix = ou=Computers
ldap group suffix = ou=Groups
server string = %h server (Samba, Ubuntu)
path = /data/
ldap suffix = dc=sumitomo-kaust, dc=local
logon path = \\%l\profiles\%u
logon home = \\CO2\%u
comment = for Sumitomo employee's only
add user script = /usr/sbin/smbldap-useradd -m "%u"
set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
syslog = 0
ldap idmap suffix = ou=Users
panic action = /usr/share/samba/panic-action %d
domain logons = yes
guest ok = yes
read only = no
case sensitive = no
strict locking = no
msdfs proxy = no


[netlogon]
;   comment = Network Logon Service
path = /home/netlogon
browseable = no
calid users = root @sumitomo-kaust

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
[profiles]
;   comment = Users profiles
path = /home/profiles
read only = no
create mask = 0700
directory mask = 0700
browseable = no
valid users = root @sumitomo-kaust

[homes]
path = /home
read only = no
browsable = no

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
********************************************

---

### Post by justleen on 2008-02-28
normally, windows will give these errors when it cant find (or cant write) to the profile folder. Make sure the profiles are there, and that write access on the folders is set.

---

### Post by rickyjones on 2008-02-28
If you want to enable roaming profiles then make sure the following line is a valid network path and that the clients have read/write access to the associated folder:

```

logon path = \\%l\profiles\%u

```

If you wish to disable roaming profiles and instead just use local profiles (I recommend this configuration) then change the logon path line as follows:

```

logon path =

```

-Richard

---

### Post by aknight_sa on 2008-03-01
> **rickyjones said:**
> If you want to enable roaming profiles then make sure the following line is a valid network path and that the clients have read/write access to the associated folder:

```

logon path = \\%l\profiles\%u

```

If you wish to disable roaming profiles and instead just use local profiles (I recommend this configuration) then change the logon path line as follows:

```

logon path =

```

-Richard


i tried this but with no luck :(

please help guys

---

