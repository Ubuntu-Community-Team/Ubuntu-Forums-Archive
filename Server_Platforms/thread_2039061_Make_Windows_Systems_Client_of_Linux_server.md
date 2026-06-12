---
title: "Make Windows Systems Client of Linux server"
date: 2012-08-08
forum: Server Platforms
---

### Post by Inderpreet Singh on 2012-08-08
Hi,

I want to know is there any utility or server in linux similar to Active Directory in windows. Actually I want to configure a Linux server in which I can create users and I can make windows systems clients of it.

So please give me suggestions.

---

### Post by 2F4U on 2012-08-08
The application you want to look into is called Samba. Samba allows Windows clients access to a Linux server and also can be configured to share resources such as printers.

---

### Post by bakegoodz on 2012-08-12
The Linux equivalent of Active Directory would be to use LDAP to manage a Samba PDC. LDAP gives a central directory service that can centralize Windows and Linux logins. LDAP adds complexity and may be overkill for your needs. Just setting up a Samba PDC may suit you.

Samba PDC notes:
```

apt-get install samba
```
> 
# /etc/samba/smb.conf

workgroup = DANSVILLE # set domain on this directive too
netbios name = CANDACE

security = user # require unix password

encrypt passwords = true

passdb backend = tdbsam # Different with LDAP

admin users =  agentp #domain administrators

map to guest = bad user

guest account = nobody  # Windows guest accounts map to samba's “nobody” has world unix permissions.

# don't allow root to log in to windows
invalid users = root

#enable domain logins – enables samba domain controller
domain logons = yes

# sets profile directory

logon path = \\%N\%U\.windows_profile

logon drive = u:

# set Primary domain controller
domain master = yes

# also PDC for LAN too
local master = yes
# known to make the samba PDC work well
preferred master = yes
os level = 80

# Home – automatically give home share to users

[homes]
	comment	= Home Directories
	browseable = no
        read only = no
	create mask = 0600
	directory mask = 0700

# Wild card to give share permissions according to the logged in user
	valid users = %S


```

/etc/init.d/smbd restart
/etc/init.d/nmbd restart
```

Domain admin is agentp
Normal user is doof

```

adduser agentp --disabled-password
adduser doof --disabled-password
```
create window profile directory. Can make folder /etc/skel/.windows_profile and it would create it for every new user.
```

mkdir /home/doof/.windows_profile

smbpasswd -a agentp
smbpasswd -a doof

```

Create machine trust account: ferb
  - This is also the domain clients computer name
  - Add unix account - first add user account with a dollar sign, this requires a special syntax.
  - useradd is the lower level command than adduser, it doesn't create password or home
  - smbpasswd -m means samba machine account, the dollar sign not included
```

useradd 'ferb$' 
smbpasswd -a -m ferb

```
When you join the domain, put in the domain administrator's credentials. agentp
Ignore the Domain DNS error

Windows 7 needs some registry settings
[http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)

---

