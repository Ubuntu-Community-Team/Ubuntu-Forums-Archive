---
title: "samba4 share problem"
date: 2013-12-31
forum: Server Platforms
---

### Post by doom.pl on 2013-12-31
Hi, 

At the beginning I wanted to apologize for my English :)
I have a problem which samba4 i have partition(mounted on /dev/sda2) only for DFS and user profile. I try to share it, but as Administrator i dont have permission to change permission xD I can`t do anything with permissions on sda2. When i open on Windows Samba sysvol or netlogon and i create any folder or file then everything is ok i have permission to change RW RO privileges. I think problem is in permission on the sda2 partition. What should i do to copy permissions from sysvol to other mounted partition ?  

My fstab:
```

UUID=639b3712-b2b7-4af0-b90a-254cc793c748 /               ext4    errors=remount-ro,user_xattr,acl,barrier=1 0       1
UUID=139c3431-5a7c-442c-9b01-3c1cd59b0723 /mnt/sda2            ext4    user_xattr,acl,barrier=1        0       2
UUID=546e1b29-c5a9-4b15-aac4-cfab4b758789 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

smb.conf

```

cat /etc/samba/smb.conf
# Global parameters
[global]
        workgroup = example
        realm = EXAMPLE.LOCAL
        netbios name = RTR-GW-01
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate

[netlogon]
        path = /usr/local/samba/var/locks/sysvol/example.local/scripts
        read only = No

[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No

[share]
path = /mnt/sda2
read only = no

```

What should i do ?

---

### Post by volkswagner on 2014-01-01
The SAMBA4 Wiki may help with [setting up shares]("https://wiki.samba.org/index.php/Setup_and_configure_file_shares").
    You may want to pay particular attention to "SeDiskOperatorPrivilege"

Also the root of the share should have full permissions.

```
sudo chmod 777 /mnt/sda2
```

---

### Post by doom.pl on 2014-01-01
I do everything from [https://wiki.samba.org/index.php/Setup_and_configure_file_shares](https://wiki.samba.org/index.php/Setup_and_configure_file_shares) but i don`t have Security Tab on computer management shares :(

---

### Post by lingpanda on 2014-01-02
> **doom.pl said:**
> I do everything from [https://wiki.samba.org/index.php/Setup_and_configure_file_shares](https://wiki.samba.org/index.php/Setup_and_configure_file_shares) but i don`t have Security Tab on computer management shares :(

As Volkswagner said, make sure the user you are using to control the ACL's has the following rights.

"You may want to pay particular attention to "SeDiskOperatorPrivilege""

---

### Post by volkswagner on 2014-01-02
> **doom.pl said:**
> I do everything from [https://wiki.samba.org/index.php/Setup_and_configure_file_shares](https://wiki.samba.org/index.php/Setup_and_configure_file_shares) but i don`t have Security Tab on computer management shares :(

Do other folders/shares show the security tab?  Sounds more like a Windows issue to me.
Are you logged into the workstation using a domain admin account (not a local user)?

---

