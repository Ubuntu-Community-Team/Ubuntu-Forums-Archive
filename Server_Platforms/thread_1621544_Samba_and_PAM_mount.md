---
title: "Samba and PAM mount"
date: 2010-11-14
forum: Server Platforms
---

### Post by LMW on 2010-11-14
Greetings!

I have the following problem:
What I have: 
1. Domain controller of Windows Server 2008 R2 with domain "domain.com";
2. CentOS 5.5 server, as Samba-server for users /home partitions;
3. Ubuntu Server 10.10. Users will login here with there /home directories mounted from CentOS.

All that should work with a pam_mount, so users mount process should be invisible for them.

What works for now:
1. CentOS and Ubuntu have joined the domain and all domain users / groups are visible via wbinfo and getent;
2. Users can login on Ubuntu with their AD credentials;
3. CentOS shares are visible from Ubuntu (via smbclient);
4. Manual mount works well (for both cifs and smbfs).

However, I don't quiet understand, how exactly in my case should [homes] part of smb.conf look like. Is there any manual or HOWTO about /home mounts? I would appreciate any help. 

What doesn't work:
I can't get users home partitions mounted. User logins, but there's no home dir for him. 

Here's the listing of Samba server's config:
> [global]
 log level = 1
 socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
 encrypt passwords = yes
 idmap gid = 10000-40000
 idmap uid = 10000-40000
 auth methods = winbind
 server string = %v samba
 password server = 192.168.1.5
 realm = DOMAIN.COM
# client use spnego = yes
 client signing = yes
 local master = no
 domain master = no
 preferred master = no
 workgroup = DOMAIN
 debug level = 2
 security = ads
 unix charset = UTF-8
 dos charset = 866
 max log size = 50
 os level = 0
 template homedir = /home/%U
 template shell = /bin/bash
# guest access = ok
 follow symlinks = yes
 winbind separator = \
 winbind uid = 10000-40000
 winbind gid = 10000-40000
 winbind enum groups = yes
 winbind enum users = yes
 winbind use default domain = yes

[homes]
comment = Home Directory for '%u'
path = /home/
public = yes
browseable = yes
writable = yes
valid users = @"DOMAIN\Domain Users"

Ubuntu smb.conf:
> [global]
 log level = 1
 socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
 encrypt passwords = yes
 idmap gid = 10000-40000
 idmap uid = 10000-40000
 auth methods = winbind
 server string = %v samba
 password server = 192.168.1.5
 realm = DOMAIN.COM
 client use spnego = yes
 client signing = yes
 local master = no
 domain master = no
 preferred master = no
 workgroup = DOMAIN
 debug level = 2
 security = ads
 unix charset = UTF-8
 dos charset = 866
 max log size = 50
 os level = 0
 template homedir = /home/%U
 template shell = /bin/bash
# guest access = ok
 follow symlinks = yes
 winbind separator = +
 winbind uid = 10000-40000
 winbind gid = 10000-40000
 winbind enum groups = yes
 winbind enum users = yes
 winbind use default domain = yes

[homes]
    comment = Home of user "%S"
    valid users = %S
    read only = No
    create mask = 0775
    directory mask = 0775
    browseable = No
    browsable = No

Here's pam_mount.conf.xml from Ubuntu:
> <volume user="smbmount" fstype="cifs" server="smb.domain.com" path="%(DOMAIN_USER)" mountpoint="/home/DOMAIN/" options="iocharset=utf8" />

Thank you for your time.

---

### Post by s1nch4n on 2010-11-14
> **LMW said:**
> Greetings!

I have the following problem:
What I have: 
1. Domain controller of Windows Server 2008 R2 with domain "domain.com";
2. CentOS 5.5 server, as Samba-server for users /home partitions;
3. Ubuntu Server 10.10. Users will login here with there /home directories mounted from CentOS.

All that should work with a pam_mount, so users mount process should be invisible for them.

What works for now:
1. CentOS and Ubuntu have joined the domain and all domain users / groups are visible via wbinfo and getent;
2. Users can login on Ubuntu with their AD credentials;
3. CentOS shares are visible from Ubuntu (via smbclient);
4. Manual mount works well (for both cifs and smbfs).

However, I don't quiet understand, how exactly in my case should [homes] part of smb.conf look like. Is there any manual or HOWTO about /home mounts? I would appreciate any help. 

What doesn't work:
I can't get users home partitions mounted. User logins, but there's no home dir for him. 

Here's the listing of Samba server's config:


Ubuntu smb.conf:


Here's pam_mount.conf.xml from Ubuntu:


Thank you for your time.at home share definition try to use 
```
valid users = %S
```
for further information [http://wiki.samba.org/index.php/Samba_&_Active_Directory](http://wiki.samba.org/index.php/Samba_&_Active_Directory)

---

### Post by LMW on 2010-11-14
> **s1nch4n said:**
> at home share definition try to use 
```
valid users = %S
```
for further information [http://wiki.samba.org/index.php/Samba_&_Active_Directory](http://wiki.samba.org/index.php/Samba_&_Active_Directory)

Thank you for your reply. However, I've managed to solve that issue. All I needed to do is edit [/etc/security/pam_mount.conf.xml
] in a way like that:
> <volume sgrp="Linux" fstype="cifs" server="smb" path="%(DOMAIN_USER)" mountpoint="/home/%(DOMAIN_USER)" options="uid=%(USERUID),gid=%(USERGID),file_mode=0600,dir_mode=0700" />
, where "Linux" is a user's AD group for Linux users.

Now, user's homedir's are mounted perfectly. That's exactly what I needed. I'm going to write a little FAQ about pam_mount+Samba /home dir server+AD 2008R2 environment, because I didn't find any good one in Internet. What do you think?

---

### Post by s1nch4n on 2010-11-15
> **LMW said:**
> Thank you for your reply. However, I've managed to solve that issue. All I needed to do is edit [/etc/security/pam_mount.conf.xml
] in a way like that:


Now, user's homedir's are mounted perfectly. That's exactly what I needed. I'm going to write a little FAQ about pam_mount+Samba /home dir server+AD 2008R2 environment, because I didn't find any good one in Internet. What do you think?
i think it's a good idea, since i never tried use PAM for samba+AD integration... :grin:

and i'm really appreciate if you write that FAQ...

---

### Post by LMW on 2010-11-15
> **s1nch4n said:**
> i think it's a good idea, since i never tried use PAM for samba+AD integration... :grin:

and i'm really appreciate if you write that FAQ...

Ok, I'll try to do it during the week. I've also corrected my previous message. Now it works as it should.

---

