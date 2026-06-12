---
title: "Samba4 ACLs"
date: 2018-11-22
forum: Server Platforms
---

### Post by needlenose2 on 2018-11-22
Hello, I am setting up an Active Directory controller  using the below version.

```
Ubuntu 16.04.4 LTS 
```

The controller is setup and everything is working fine. I am able to join, authenticate Windows clients, add/remove users, etc, using the Windows Admin tools. I am now in the process of setting up some shares which will use Windows ACLs to authenticate. I am using the below link as a guide:

[https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs](https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs)

I have checked ACLs are built into my version:

```
root@adc1:/hd2# smbd -b | grep HAVE_LIBACL
   HAVE_LIBACL
```

I set the SetDiskOperatorPrivilege for my Domain Admins group, just like the tutorial and the rights list now returns:

```
root@adc1:/hd2# net rpc rights list privileges SeDiskOperatorPrivilege -U "XXX\administrator"
Enter XXX\administrator's password:
SeDiskOperatorPrivilege:
  XXX\Domain Admins
```

However, when I attempt to set the ownership of the share directory as specified in the tutorial, I get:

```
root@adc1:/hd2# chown root:"Domain Admins" /hd2/Admin
chown: invalid group: ‘root:Domain Admins’
```

As does:

```
root@adc1:/hd2# chown root:"XXX\Domain Admins" Admin
chown: invalid group: ‘root:XXX\\Domain Admins’
```

My smb.conf:

```
# Global parameters
[global]
        workgroup = XXX
        realm = XXX.LAN
        netbios name = ADC1
        server role = active directory domain controller
        dns forwarder = 10.5.1.1
        idmap_ldb:use rfc2307 = yes

[netlogon]
        path = /var/lib/samba/sysvol/xxx.lan/scripts
        read only = No

[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

```


Below is the dump from testparm

```
root@adc1:/hd2# testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[netlogon]"
Processing section "[sysvol]"
Loaded services file OK.
Server role: ROLE_ACTIVE_DIRECTORY_DC

Press enter to see a dump of your service definitions

# Global parameters
[global]
    workgroup = XXX
    realm = XXX.LAN
    server role = active directory domain controller
    passdb backend = samba_dsdb
    dns forwarder = 10.5.1.1
    rpc_server:tcpip = no
    rpc_daemon:spoolssd = embedded
    rpc_server:spoolss = embedded
    rpc_server:winreg = embedded
    rpc_server:ntsvcs = embedded
    rpc_server:eventlog = embedded
    rpc_server:srvsvc = embedded
    rpc_server:svcctl = embedded
    rpc_server:default = external
    winbindd:use external pipes = true
    idmap_ldb:use rfc2307 = yes
    idmap config * : backend = tdb
    map archive = No
    map readonly = no
    store dos attributes = Yes
    vfs objects = dfs_samba4 acl_xattr


[netlogon]
    path = /var/lib/samba/sysvol/xxx.lan/scripts
    read only = No


[sysvol]
    path = /var/lib/samba/sysvol
    read only = No
```


What am I missing? It seems like I have Samba running, but maybe the OS isn't aware that it exists for authentication?

Thanks!

---

### Post by volkswagner on 2018-11-24
Did you see the recommendation on SAMBA Wiki, suggesting not running fileserver directly on domain controller?

Did you setup [winbindd according to SAMBA Wiki]("https://wiki.samba.org/index.php/Configuring_Winbindd_on_a_Samba_AD_DC")?

What are the output of [winbindd tests]("https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Domain_Member#Testing_the_Winbindd_Connectivity")?

---

### Post by needlenose2 on 2018-11-24
> **volkswagner said:**
> Did you see the recommendation on SAMBA Wiki, suggesting not running fileserver directly on domain controller?

Did you setup [winbindd according to SAMBA Wiki]("https://wiki.samba.org/index.php/Configuring_Winbindd_on_a_Samba_AD_DC")?

What are the output of [winbindd tests]("https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Domain_Member#Testing_the_Winbindd_Connectivity")?

No, I didn't see the recommendation. I'm a bit h/w challenged right now. I do have a ZeroShell router running on the network, perhaps I will move the share there if I can get it to authenticate to the AD controller. That's the main reason I'm doing this. Centralized management of shares.

I actually set everything up from here:

[https://www.tecmint.com/install-samba4-active-directory-ubuntu/](https://www.tecmint.com/install-samba4-active-directory-ubuntu/)

Mainly because the guide is specifically for the distro/version I'm running. I thought it kept me from having to figure out all the the little nuances that are different from distro to distro that wouldn't be included in a generic Samba guide.

The output of wbinfo is:

```
root@adc1:~# wbinfo --ping-dc
checking the NETLOGON for domain[XXX] dc connection to "adc1.XXX.lan" succeeded
```


Thanks for your response! I will see about moving the share to the gateway machine.

---

### Post by volkswagner on 2018-11-24
Don't burn the barn to roast a pig.

If you read the reasons why it's not a good idea to
run a domain controller and fileserver on same machine
and don't feel the negatives affect you, then go ahead
and proceed.

I think looking into the winbindd will be a big help.
Note, that the WiKi says to setup the Winbindd before
setting up shares, so you may want to create new shares.

---

