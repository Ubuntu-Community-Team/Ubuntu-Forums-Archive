---
title: "samba4 and ACL"
date: 2010-08-28
forum: Server Platforms
---

### Post by anchise on 2010-08-28
I am running ubuntu server 10.04 32-bit. I compiled samba4 from git and everything works like a dream: Adding clients to the domain, managing users and groups, applying GPOS. The only problem is with changing ACLs of samba shares.

Whenever I try to add an ACE to an existing ACL or try to edit an existing ACE, after pressing OK it simply dissapears. I am doing this from a windows XP pro domain computer by opening windows explorer and selecting properties>security from the context menu.

Browsing samba forums and searching google has yielded no solution so far.

Is anybody else experiencing similar problems?
Does anybody have a clue why this could be?

Thanks in advance.

Here my smb.conf as located in /usr/local/samba/etc:

```
[globals]
    netbios name    = SAMBA
    workgroup    = ASRIRA
    realm        = ASRIRA.LOCAL
    server role     = domain controller

[recepcion]
    path = /shares/recepcion
    

[netlogon]
    path = /usr/local/samba/var/locks/sysvol/asrira.local/scripts
    read only = no

[sysvol]
    path = /usr/local/samba/var/locks/sysvol
    read only = no


```/shares/recepcion is owned by root:root with a+rwx

---

### Post by headvampyre@hotmail.co.uk on 2010-08-29
What filesystems are you using? If you using ext4/ext3 install the packages attr and acl with: sudo apt-get install attr acl then add acl,user_xattr to the partition on /etc/fstab. Heres what my root partition(ext4) looks like:

UUID=b65f3bca-29b5-4a28-99dc-595c009020bb /               ext4    errors=remount-ro,acl,user_xattr 0       1

Also, if your using seperate partitions for different shares, you could try using an xfs filesystem, i use that for my shares and it works flawlessly with windows acls.
Hope this helps.

---

### Post by anchise on 2010-08-29
Thanks a lot headvampyre,

First thing tomorrow, I will try the package you named. I fact I am using ext4.
Appearently, I got something wrong reading the documentation of samba4. I thought as samba4 doesn't use unix accounts any more (compared to its predecessors) and hence does no nt-account/unix-account mapping, i wouldn't need to use acl on my linux machine.

---

### Post by anchise on 2010-08-30
XFS did the trick.

Thanks a lot headvampyre.

---

