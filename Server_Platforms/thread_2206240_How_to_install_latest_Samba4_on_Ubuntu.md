---
title: "How to install latest Samba4 on Ubuntu?"
date: 2014-02-18
forum: Server Platforms
---

### Post by insiki2 on 2014-02-18
Hello.
I want to make AD/DC Samba4 server.
When i install Samba4 on Ubuntu Server 13.10 i have errors. 
Look.

Preparing system.
```
apt-get install build-essential libacl1-dev libattr1-dev \
libblkid-dev libgnutls-dev libreadline-dev python-dev \
python-dnspython gdb pkg-config libpopt-dev libldap2-dev \
dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev acl
```

Enable ACL support
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sdb1 during installation
UUID=dffa8d87-bae2-4002-b118-3108f9b8e20e / ext4 errors=remount-ro,user_xattr,acl,barrier=1 0 1
# swap was on /dev/sdb5 during installation
UUID=10ff38ce-54b6-459b-82a9-93566f02d401 none swap sw 0 0
```

Rebooting server and installing samba4
```
sudo apt-get install samba4 samba4-common-bin
```

Get error
```
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
```

Try to configure
```

sudo samba-tool domain provision
Realm: tps7.local
Domain [tps7]: tps7
Server Role (dc, member, standalone) [dc]: dc
DNS backend (SAMBA_INTERNAL, BIND9_FLATFILE, BIND9_DLZ, NONE) [SAMBA_INTERNAL]: SAMBA_INTERNAL
DNS forwarder IP address (write 'none' to disable forwarding) [192.168.1.1]: 192.168.1.1
Administrator password:
Retype password:
Looking up IPv4 addresses
Looking up IPv6 addresses
No IPv6 address will be assigned
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Setting up secrets.ldb
Setting up the registry
Setting up the privileges database
Setting up idmap db
Setting up SAM db
Setting up sam.ldb partitions and settings
Setting up sam.ldb rootDSE
Pre-loading the Samba 4 and AD schema
Adding DomainDN: DC=tps7,DC=local
Adding configuration container
Setting up sam.ldb schema
Setting up sam.ldb configuration data
Setting up display specifiers
Modifying display specifiers
Adding users container
Modifying users container
Adding computers container
Modifying computers container
Setting up sam.ldb data
Setting up well known security principals
Setting up sam.ldb users and groups
Setting up self join
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_x
```
It's true, there is no folder .../samba/vfs and there is no file "acl_xattr.so"
Google asked me that it fixed in Samba 4.0.9. 

Okay. 
Im trying to build *.deb packet from sources, coz make / make install is not good way (for future - updating and etc.)
Installing auto-apt &#1080; checkinstall 
```
sudo apt-get install auto-apt
sudo apt-get install checkinstall
```
Go to the home directory
```
cd
```

Take last version 
```
wget http://www.samba.org/samba/ftp/samba-latest.tar.gz
```
Extract
```
tar xzf samba*
```
Create package
```
cd samba*
sudo auto-apt -y run ./configure
sudo make
sudo checkinstall -D --install=no
```
Install
```
sudo dpkg -i samba4_4.1.4-1_amd64.deb

```
And what i have?..

```
cd /usr/local/samba


``````
 sudo samba-tool
Traceback (most recent call last):
  File "/usr/bin/samba-tool", line 33, in <module>
    from samba.netcmd.main import cmd_sambatool
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/main.py", line 24, in <module>
    from samba.netcmd.delegation import cmd_delegation
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/delegation.py", line 23, in <module>
    from samba import provision
  File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 46, in <module>
    from samba.samba3 import smbd, passdb
ImportError: libdfs_server_ad.so: cannot open shared object file: No such file or directory

```
wt..?

---

### Post by insiki2 on 2014-02-18
Before i'm trying to install Samba-4.1.4 on Ubuntu Server 12.04 from sources and got error..

[COLOR=#000000][FONT=tahoma]cat /etc/fstab[/FONT][/COLOR]
```
[COLOR=#000000][FONT=tahoma]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]#[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# Use 'blkid' to print the universally unique identifier for a[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# device; this may be used with UUID= as a more robust way to name devices[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]#[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# <file system> <mount point> <type> <options> <dump> <pass>[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# / was on /dev/sdb1 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]UUID=6a5a4984-594c-4074-9fc4-d7ddc9d907d7 / ext4 acl,user_xattr,errors=remount-ro 0 1[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# swap was on /dev/sdb5 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]UUID=10ff38ce-54b6-459b-82a9-93566f02d401 none swap sw 0 0[/FONT][/COLOR]
```

[COLOR=#000000][FONT=tahoma]sudo samba-tool domain provision[/FONT][/COLOR]
```
[COLOR=#000000][FONT=tahoma]Realm: [/FONT][/COLOR][tps7.local]("http://vk.com/away.php?to=http%3A%2F%2Ftps7.local")
[COLOR=#000000][FONT=tahoma]Domain [tps7]: tps7[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Server Role (dc, member, standalone) [dc]: dc[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]DNS backend (SAMBA_INTERNAL, BIND9_FLATFILE, BIND9_DLZ, NONE) [SAMBA_INTERNAL]: BIND9_DLZ[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Administrator password:[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Retype password:[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Looking up IPv4 addresses[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Looking up IPv6 addresses[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]No IPv6 address will be assigned[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: module schema_load initialization failed : No such object[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: module rootdse initialization failed : No such object[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: module samba_dsdb initialization failed : No such object[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: Unable to load modules for /var/lib/samba/private/sam.ldb: (null)[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]samdb_connect failed[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]VFS connect failed![/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed - ProvisioningError: Your filesystem or build does not support posix ACLs, which s3fs requires. Try the mounting the filesystem with the 'acl' option.[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]File "/usr/lib/python2.7/dist-packages/samba/netcmd/[/FONT][/COLOR][domain.py]("http://vk.com/away.php?to=http%3A%2F%2Fdomain.py")[COLOR=#000000][FONT=tahoma]", line 398, in run[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]use_rfc2307=use_rfc2307, skip_sysvolacl=False)[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 2052, in provision[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]raise ProvisioningError("Your filesystem or build does not support posix ACLs, which s3fs requires. Try the mounting the filesystem with the 'acl' option.")[/FONT][/COLOR]
```

---

### Post by lingpanda on 2014-02-18
> **insiki2 said:**
> Before i'm trying to install Samba-4.1.4 on Ubuntu Server 12.04 from sources and got error..

[COLOR=#000000][FONT=tahoma]cat /etc/fstab[/FONT][/COLOR]
```
[COLOR=#000000][FONT=tahoma]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]#[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# Use 'blkid' to print the universally unique identifier for a[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# device; this may be used with UUID= as a more robust way to name devices[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]#[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# <file system> <mount point> <type> <options> <dump> <pass>[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# / was on /dev/sdb1 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]UUID=6a5a4984-594c-4074-9fc4-d7ddc9d907d7 / ext4 acl,user_xattr,errors=remount-ro 0 1[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]# swap was on /dev/sdb5 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]UUID=10ff38ce-54b6-459b-82a9-93566f02d401 none swap sw 0 0[/FONT][/COLOR]
```

[COLOR=#000000][FONT=tahoma]sudo samba-tool domain provision[/FONT][/COLOR]
```
[COLOR=#000000][FONT=tahoma]Realm: [/FONT][/COLOR][tps7.local]("http://vk.com/away.php?to=http%3A%2F%2Ftps7.local")
[COLOR=#000000][FONT=tahoma]Domain [tps7]: tps7[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Server Role (dc, member, standalone) [dc]: dc[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]DNS backend (SAMBA_INTERNAL, BIND9_FLATFILE, BIND9_DLZ, NONE) [SAMBA_INTERNAL]: BIND9_DLZ[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Administrator password:[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Retype password:[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Looking up IPv4 addresses[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Looking up IPv6 addresses[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]No IPv6 address will be assigned[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: module schema_load initialization failed : No such object[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: module rootdse initialization failed : No such object[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: module samba_dsdb initialization failed : No such object[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ldb: Unable to load modules for /var/lib/samba/private/sam.ldb: (null)[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]samdb_connect failed[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]VFS connect failed![/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed - ProvisioningError: Your filesystem or build does not support posix ACLs, which s3fs requires. Try the mounting the filesystem with the 'acl' option.[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]File "/usr/lib/python2.7/dist-packages/samba/netcmd/[/FONT][/COLOR][domain.py]("http://vk.com/away.php?to=http%3A%2F%2Fdomain.py")[COLOR=#000000][FONT=tahoma]", line 398, in run[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]use_rfc2307=use_rfc2307, skip_sysvolacl=False)[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 2052, in provision[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]raise ProvisioningError("Your filesystem or build does not support posix ACLs, which s3fs requires. Try the mounting the filesystem with the 'acl' option.")[/FONT][/COLOR]
```

I would replace the following line

```
UUID=dffa8d87-bae2-4002-b118-3108f9b8e20e / ext4 errors=remount-ro,user_xattr,acl,barrier=1 0 1
```

With

```
UUID=dffa8d87-bae2-4002-b118-3108f9b8e20e / ext4 errors=remount-ro,user_xattr,acl,barrier=1 1     1
```

Notice I replaced the zero with a 1. After a failed domain provision you must remove all traces of your initial Samba install or you will get errors about "[COLOR=#000000][FONT=tahoma]ProvisioningError("Your  filesystem or build does not support posix ACLs, which s3fs requires.  Try the mounting the filesystem with the 'acl' option.")[/FONT][/COLOR]."

---

### Post by insiki2 on 2014-02-18
I changed 0 to 1 and got
sudo apt-get install samba4
```
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1088;&#1077;&#1076;&#1083;&#1072;&#1075;&#1072;&#1077;&#1084;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;:
  phpldapadmin samba-gtk swat2 ntp
&#1053;&#1054;&#1042;&#1067;&#1045; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099;:
  samba4
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 1 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1053;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1089;&#1082;&#1072;&#1095;&#1072;&#1090;&#1100; 0 B/1 691 kB &#1072;&#1088;&#1093;&#1080;&#1074;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1074;&#1086;&#1079;&#1088;&#1072;&#1089;&#1090;&#1105;&#1090; &#1085;&#1072; 11,1 MB.
&#1055;&#1088;&#1077;&#1076;&#1074;&#1072;&#1088;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1072;&#1103; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; ...
&#1042;&#1099;&#1073;&#1086;&#1088; &#1088;&#1072;&#1085;&#1077;&#1077; &#1085;&#1077; &#1074;&#1099;&#1073;&#1088;&#1072;&#1085;&#1085;&#1086;&#1075;&#1086; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; samba4.
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; … &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 96993 &#1092;&#1072;&#1081;&#1083;&#1072; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;.)
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; samba4 (&#1080;&#1079; &#1092;&#1072;&#1081;&#1083;&#1072; …/samba4_4.0.3+dfsg1-0.1ubuntu1_amd64.deb) …
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; ureadahead …
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; man-db …
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; samba4 (4.0.3+dfsg1-0.1ubuntu1) …
Looking up IPv4 addresses
Looking up IPv6 addresses
No IPv6 address will be assigned
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Setting up share.ldb
Setting up secrets.ldb
Setting up the registry
Setting up the privileges database
Setting up idmap db
Setting up SAM db
Setting up sam.ldb partitions and settings
Setting up sam.ldb rootDSE
Pre-loading the Samba 4 and AD schema
Adding DomainDN: DC=localdomain
Adding configuration container
Setting up sam.ldb schema
Setting up sam.ldb configuration data
Setting up display specifiers
Modifying display specifiers
Adding users container
Modifying users container
Adding computers container
Modifying computers container
Setting up sam.ldb data
Setting up well known security principals
Setting up sam.ldb users and groups
Setting up self join
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Error loading module '/usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so': /usr/lib/x86_64-linux-gnu/samba//vfs/acl_xattr.so: cannot open shared object file: No such file or directory
error probing vfs module 'acl_xattr': NT_STATUS_UNSUCCESSFUL
smbd_vfs_init: vfs_init_custom failed for acl_xattr
Adding DNS accounts
Creating CN=MicrosoftDNS,CN=System,DC=localdomain
Creating DomainDnsZones and ForestDnsZones partitions
Populating DomainDnsZones and ForestDnsZones partitions
Setting up sam.ldb rootDSE marking as synchronized
Fixing provision GUIDs
A Kerberos configuration suitable for Samba 4 has been generated at /var/lib/samba/private/krb5.conf
Once the above files are installed, your Samba4 server will be ready to use
Server Role:           active directory domain controller
Hostname:              tps7dc01
NetBIOS Domain:        WORKGROUP
DNS Domain:            localdomain
DOMAIN SID:            S-1-5-21-2840583755-2156081812-968736069
samba4 start/running, process 15312
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; ureadahead …
```

---

### Post by lingpanda on 2014-02-19
Lets start from the beginning. Remove all traces of Samba. Use the following

```
apt-get autoremove purge samba4
```

Then look for all traces of Samba

```
locate /samba
```

Remove all traces of Samba you find. Autoremove should do this for you. If you find /usr/local/samba make sure to remove this Samba directory. Also remove any krb.conf file from /etc/.

Install the following 


```
[FONT=&amp]apt-get install build-essential libacl1-dev libattr1-dev libblkid-dev libgnutls-dev libreadline-dev python-dev python-dnspython gdb pkg-config libpopt-dev libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev acl libpam0g-dev docbook-xsl xsltproc inkscape dnsutils[/FONT]
```

Download Samba as a tar.
 ```

wget http://ftp.samba.org/pub/samba/samba-4.1.5.tar.gz

  tar -zxvf samba-4.1.5.tar.gz


```   
  Change into the extracted folder

   
  ```
cd samba-4.1.5


```   
  Now we need to configure and make samba. These steps will take a while.
   
   ```
./configure
  sudo make
  sudo make install
```


  Once this completes we can start configuring our Samba 4 Active Directory domain
   
   ```

sudo /usr/local/samba/bin/samba-tool domain provision


```  


See below for info on XATTR Support.



  **[FONT=&amp]File System Support [/FONT]**

  To use the advanced features of Samba4 you need a filesystem that supports both the "user" and "system" xattr namespaces. 
  **[FONT=&amp]ext3/ext4 File System [/FONT]**

  If you are using either ext3 or ext4 for your file system you will need to include the options "user_xattr","acl" and "barrier=1" in your /etc/fstab. For example: 
  /dev/mapper/samba4pdc-root /               ext4    errors=remount-ro,user_xattr,acl,barrier=1 1       1
  Simply change ext3 to ext4 if you are using it. Normally you will want to just modify the existing line to add those options. Please use caution when modifying your fstab as it can lead to an un-bootable system if the wrong thing is modified. 
  The **barrier=1** option ensures that tdb transactions are safe against unexpected power loss. A number of sites have corrupted their AD database in sam.ldb by not having this option enabled. 
  You also need to compile your kernel with the XATTR, SECURITY, and POSIX_ACL options for your filesystem. For ext3 (change the 3 to a 4 for ext4) that means you need: 
    CONFIG_EXT3_FS_XATTR=y
    CONFIG_EXT3_FS_SECURITY=y
    CONFIG_EXT3_FS_POSIX_ACL=y
  If you are running a Linux 2.6 (or greater) kernel with CONFIG_IKCONFIG_PROC defined you can check this with the following command: 
    $ zgrep CONFIG_EXT3_FS /proc/config.gz
  **[FONT=&amp]File Systems without xattr support [/FONT]**

  If you don't have a filesystem with xattr support, then you can simulate it by adding the following line to your smb.conf: 
    posix:eadb = /usr/local/samba/eadb.tdb
  that will place all extra file attributes (NT ACLs, DOS EAs, streams etc), in that tdb. It is not efficient, and doesn't scale well, but at least it gives you a choice when you don't have a modern filesystem. 
  **[FONT=&amp]Testing your filesystem [/FONT]**

  To test your filesystem support, install the 'attr' package and run the following 4 commands as root: 
   # touch test.txt
   # setfattr -n user.test -v test test.txt
   # setfattr -n security.test -v test2 test.txt
   # getfattr -d test.txt
   # getfattr -n security.test -d test.txt
  You should see output like this: 
   # file: test.txt
   user.test="test"
   # file: test.txt
   security.test="test2"
  For ACL testing do the following as root: 
   # touch test3.txt
   # setfacl -m g:adm:rwx test3.txt
   # getfacl test3.txt
  and you should get a line like [FONT=&amp]group:adm:rwx[/FONT] in your output. 
  
If you get any "Operation not supported" errors then it means your kernel is not configured correctly, or your filesystem is not mounted with the right options. 
  If you get any "Operation not permitted" errors then it probably means you didn't try the test as root. 
  If you are using the posix:eadb option then you don't need to test your filesystem in this manner.

---

