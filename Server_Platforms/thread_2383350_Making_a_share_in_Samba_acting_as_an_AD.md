---
title: "Making a share in Samba acting as an AD"
date: 2018-01-23
forum: Server Platforms
---

### Post by adamkn on 2018-01-23
[FONT=&quot]Hi![/FONT]

[FONT=&quot]We have recently taken over a new client who has an Ubuntu 14.04 server running Samba that acts as a DC. We also have a Windows 2012 R2 server with AD connected to this server.[/FONT]

[FONT=&quot]What we want to do, is make a new share that only members of a security group in AD can access. Following the guide found here, [/FONT][https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs](https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs)[FONT=&quot] , i run the below as root,[/FONT]

[FONT=&quot]chown -R root:"Domain Admins" /mnt/data/destination[/FONT]

[FONT=&quot]Each time I do this, Ubuntu cant understand who Domain Admins is. My samba config for this is[/FONT]

[FONT=&quot][Share Name][/FONT]
[FONT=&quot]path = "/mnt/data/destination"[/FONT]
[FONT=&quot]read only = no[/FONT]
[FONT=&quot]vfs objects = streams_xattr[/FONT]

[FONT=&quot]The share works and is viewable, and making the permissions 777 in Linux does allow me to write (Will be changed, that's just for testing) but the whole idea of this share was for it to be exclusive for certain users in a security group.[/FONT]

[FONT=&quot]Any assistance or queries would be greatly appreciated![/FONT]

---

### Post by darkod on 2018-01-24
The chown command is listed there only as additional step. If your domain administrator can control the share, simply add the Domain Admins using Windows ACL through the windows GUI. Don't bother with chown.

---

### Post by LHammonds on 2018-01-24
See if this article helps: [Group share for a Active Directory domain group with Samba](https://www.surlyjake.com/blog/2009/05/06/create-a-group-share-for-a-domain-group-with-samba/)

You might need to include [valid users](https://www.samba.org/samba/docs/using_samba/ch09.html) in the share config (my syntax might not be 100% correct):
```
valid users = "@Domain Admins"
```
or
```
valid users = "@DOMAIN\Domain Admins"
```

Be sure to restart Samba if you make any changes to the config file.

LHammonds

---

### Post by volkswagner on 2018-01-24
I belive you'll need to follow AD Member server instructions for the 
file server to have access to AD users/groups.

[https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Domain_Member](https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Domain_Member)

Check out section for "Testing the Winbindd Connectivity"

---

### Post by darkod on 2018-01-25
> **volkswagner said:**
> I belive you'll need to follow AD Member server instructions for the 
file server to have access to AD users/groups.

In his post he says the Samba server is also running as a DC. That should already be able to read all users and groups, no?

---

### Post by volkswagner on 2018-01-25
> **darkod said:**
> In his post he says the Samba server is also running as a DC. That should already be able to read all users and groups, no?

Agreed, I misread the OP. 
My brain focused on mention of Server 2012 (which
I thought was acting as ADDC).

It still may be a good idea
to post the smb.conf and output of
the following commands to make sure
the server can read AD users/groups:

```
sudo wbinfo -g
sudo wbinfo -u
sudo getent group "domain users"
```

---

### Post by adamkn on 2018-01-28
Thanks all for the assistance so far! Volkswagner, please find the below my smb.conf

> # Global parameters[global]
workgroup = DOMAINNAMEHERE
realm = DOMAINNAMEHERE.LAN
netbios name = DC01
server role = active directory domain controller
dns forwarder = 192.168.10.1
idmap_ldb:use rfc2307 = yes
netbios aliases = wpkg
server signing = Auto
tls verify peer = no_check
socket options = SO_KEEPALIVE TCP_KEEPIDLE=300 TCP_KEEPINTVL=10 TCP_KEEPCNT=5
reset on zero vc = yes
log level = 3
include = /etc/samba/shares.conf
#reset on zero vc = yes


[netlogon]
path = /var/lib/samba/sysvol/domainname.lan/scripts
read only = No


[sysvol]
path = /var/lib/samba/sysvol
read only = No


[homes]
path = /mnt/data/homes/%S
readonly = No
browseable = No


[profiles]
path = /mnt/data/profiles
read only = No


[home]
path = /mnt/data/homes
read only = No




The commands sudo wbinfo -g and sudo wbinfo -u worked fine and reported the correct data, however, sudo getent group "domain users" gave me nothing....

Thanks!

---

### Post by volkswagner on 2018-01-28
I believe you still need winbind when you want to have
your AD DC also act as a file server. This is not recommended but
does work with some oddities that are not clearly documented.

Check out the section in [SAMBA4 as AD DC Wiki]("https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller") related to 
Configuring Winbindd on a Samba AD DC and
Using the Domain Controller as a File Server

---

