---
title: "Samba 4/Ubuntu 12.04.1 Server roaming profiles permissions"
date: 2013-02-01
forum: Server Platforms
---

### Post by Roswebnet on 2013-02-01
Hi everyone,
 
I just played around with Ubuntu Server 12.04.1 and samba 4 alpha 18 (from apt-get).
Installation goes ok. However, I got some issues with BIND. When I combine those 2 tutorials:
 
[http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04)
[http://www.darklab.co.uk/tag/samba-4/](http://www.darklab.co.uk/tag/samba-4/)
 
I had no problems anymore.
 
Now I can join windows 8 to the domain. Also I can create users in dsm.msc, but when I log in as user I am getting "temporary account bla bla warning."
 
After researching, I set my roaming profile folder to chmod 0777. And it's working...
 
But 0777 does not look secure, isn't it?
Is there any solution?
 
My smb.conf:
```

# Global parameters
[global]
server role = domain controller
workgroup = ODM
realm = odm.lan
netbios name = SERVER
passdb backend = samba4
[netlogon]
path = /var/lib/samba/sysvol/odm.lan/scripts
read only = No
[sysvol]
path = /var/lib/samba/sysvol
read only = No
[profiles]
comment = Users Profile Directories
path = /data/profiles/
browseable = no
read only = no
writable = yes
directory mask = 0777
create mask = 0777
[printers]
comment = All Printers
path = /data/print/spool/ 
guest ok = yes
printable = yes
read only = no
[shares]
comment = Global share for all users
path = /data/global
read only = No
directory mask = 0777
create mask = 0777
&#12288;

```
 
This I already tried:
[http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO#Setting_Up_Roaming_Profiles](http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO#Setting_Up_Roaming_Profiles)
 
and /etc/fastab tweak:
UUID=3cf9653f-7aa0-4e55-a6df-41bd281858d4 / ext4 errors=remount-ro,acl,user_xattr 0 1
 
[http://ubuntuforums.org/showthread.php?t=1563085](http://ubuntuforums.org/showthread.php?t=1563085)

---

### Post by lingpanda on 2013-02-01
> **Roswebnet said:**
> Hi everyone,
 
I just played around with Ubuntu Server 12.04.1 and samba 4 alpha 18 (from apt-get).
Installation goes ok. However, I got some issues with BIND. When I combine those 2 tutorials:
 
[http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04)
[http://www.darklab.co.uk/tag/samba-4/](http://www.darklab.co.uk/tag/samba-4/)
 
I had no problems anymore.
 
Now I can join windows 8 to the domain. Also I can create users in dsm.msc, but when I log in as user I am getting "temporary account bla bla warning."
 
After researching, I set my roaming profile folder to chmod 0777. And it's working...
 
But 0777 does not look secure, isn't it?
Is there any solution?
 
My smb.conf:
```

# Global parameters
[global]
server role = domain controller
workgroup = ODM
realm = odm.lan
netbios name = SERVER
passdb backend = samba4
[netlogon]
path = /var/lib/samba/sysvol/odm.lan/scripts
read only = No
[sysvol]
path = /var/lib/samba/sysvol
read only = No
[profiles]
comment = Users Profile Directories
path = /data/profiles/
browseable = no
read only = no
writable = yes
directory mask = 0777
create mask = 0777
[printers]
comment = All Printers
path = /data/print/spool/ 
guest ok = yes
printable = yes
read only = no
[shares]
comment = Global share for all users
path = /data/global
read only = No
directory mask = 0777
create mask = 0777
&#12288;

```This I already tried:
[http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO#Setting_Up_Roaming_Profiles](http://wiki.samba.org/index.php/Samba_AD_DC_HOWTO#Setting_Up_Roaming_Profiles)
 
and /etc/fastab tweak:
UUID=3cf9653f-7aa0-4e55-a6df-41bd281858d4 / ext4 errors=remount-ro,acl,user_xattr 0 1
 
[http://ubuntuforums.org/showthread.php?t=1563085](http://ubuntuforums.org/showthread.php?t=1563085)

For what ever reason the samba4 Wiki link to implementing roaming profiles is blank. A cached version of the page is attached.

---

### Post by Roswebnet on 2013-02-01
> **lingpanda said:**
> For what ever reason the samba4 Wiki link to implementing roaming profiles is blank. A cached version of the page is attached.
 
Thank you I feel me much safer now. :) According posted file:
 
 
[HTML] 
Creating the Profile Share
To create a Samba share to use for your user's profiles simply add something similar to your share section of the smb.conf file:
[profiles] 
comment = Network Profiles Share 
path = /srv/samba/profiles 
read only = No 
store dos attributes = Yes 
create mask = 0600 
directory mask = 0700 
browseable = no 
guest ok = no 
printable = no 
profile acls = yes 
csc policy = disable
Then ensure that everyone has write access to the directory listed as the path:
chmod 1777 /srv/samba/profiles
 
[/HTML]
 
Further, as far as I know, in samba 4 those settings:
```
 
logon path = [\\%L\profiles\%U]("file://%25l/profiles/%25U") 
logon home = [\\%L\%U\.9xprofile]("file://%25l/%25U/.9xprofile") 
logon drive = P:

```
 
Does not work anymore. 
In addition, cached link was last modified in 2011, and there was samba 3.6.+... Correct me, if I am wrong.
 
I added in my smb.conf next things(I will update if comes any changes):
```

[profiles]
        comment = Users Profile Directories
        path = /data/profiles
        read only = no
        create mask = 0600
        directory mask = 0700
        profile acls = yes

```
 
for folder I set:
chmod 1777 /srv/samba/profiles
 
and 
 
chmod a+rwx /srv/samba/profiles
 
The future files and directories should be now accessed by root and related windows user only.

---

