---
title: "Authenticating Samba Share to AD"
date: 2013-02-14
forum: Server Platforms
---

### Post by Noobtronics on 2013-02-14
Here is my setup:

I have a small network with 2 Windows Server 2k8 DC's
I have just added a new Ubuntu 12.04 server to the network.  I haven't added the server to the domain yet.  

Ultimately what I would like to do is have this server act as a Samba share server.  I want users on the domain to be able to use their AD credentials to authenticate to the folders on that share.  I have already figured out how to authenticate users based on Samba user/Linux user syncronization, but would prefer an AD or LDAP solution. 

all of the .conf files are in their default settings, however I have already added the server to the domain.  How would you suggest I proceed?  Thanks!

---

### Post by Noobtronics on 2013-02-15
===========UPDATE=============

I have since added the server to the domain.  I have created a share to test my configuration with.  As it stands right now, I have root as the owner of the folder as well as the group.

I have configured the smb.conf file as follows:

#======================= Global Settings ===================================== 
[global]
workgroup = MYDOMAIN
netbios name = my-server_name
encrypt passwords = yes
prefered master = no
domain master = no
security = user
map to guest = bad user
dns proxy = no
idmap uid = 10000 - 10999
idmap gid = 10000 - 10999

#============================ Share Definitions ============================== 
[TEST]
path = /srv/test/testB
browsable =yes
writable = yes
;guest ok = yes
read only = no

Kerberos is configured and is successfully pulling tickets for the domain.

I still haven't configured the ldap portion yet, but will look into trying to get it working today.

Is authenticating my 'testB' share with LDAP even feasible?  

Thanks

---

