---
title: "Samba Problem -  &quot;Thereis not enough free space..&quot;"
date: 2015-05-28
forum: Server Platforms
---

### Post by jayjay89 on 2015-05-28
Hi,

I am running samba 4.1.17-Zentyal on Ubuntu 14.04.2 LTS. Now I am no longer able to create/copy any directories on my shares. I get the message "Thereis not enough free space..". Unfortunately there is still 2,3T left and I have no problems creating files and folders on the filesystem.


smbstatus shows following:
```
params.c:pm_process() - Processing configuration file "/etc/samba/openchange.conf"Processing section "[global]"
params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
params.c:pm_process() - Processing configuration file "/etc/samba/openchange.conf"
Processing section "[global]"
params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"


Samba version 4.1.17-Zentyal
PID     Username      Group         Machine
-------------------------------------------------------------------
13301     user01         domain users  10.10.10.3   (ipv4:10.10.10.3:57400)


Service      pid     machine       Connected at
-------------------------------------------------------
Movies       13301   10.10.10.3    Thu May 28 11:11:48 2015
user01        13301   10.10.10.3    Thu May 28 11:11:48 2015
IPC$         13301   10.10.10.3    Thu May 28 11:11:48 2015


Registered MSG_REQ_POOL_USAGE
Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
Locked files:
Pid          Uid        DenyMode   Access      R/W        Oplock           SharePath   Name   Time
--------------------------------------------------------------------------------------------------
13301        2502       DENY_NONE  0x100081    RDONLY     NONE             /home/samba/shares/movies   .   Thu May 28 11:11:47 2015
13301        2502       DENY_NONE  0x100081    RDONLY     NONE             /home/samba/shares/movies   .   Thu May 28 11:11:47 2015
13301        2502       DENY_NONE  0x100081    RDONLY     NONE             /home/user01   .   Thu May 28 11:11:48 2015
13301        2502       DENY_NONE  0x100081    RDONLY     NONE             /home/user01   .   Thu May 28 11:11:49 2015
```

smb.conf
```
[global]    workgroup = DOMAIN
    realm = DOMAIN.ONL
    netbios name = cloud
    server string = Zentyal Server
    server role = dc
    server role check:inhibit = yes
    server services = -dns
    server signing = auto
    dsdb:schema update allowed = yes
    drs:max object sync = 1200


    idmap_ldb:use rfc2307 = yes




    log level = 3
    log file = /var/log/samba/samba.log
    max log size = 100000




    include = /etc/samba/openchange.conf


    include = /etc/samba/shares.conf








[netlogon]
    path = /var/lib/samba/sysvol/DOMAIN.onl/scripts
    browseable = no
    read only = yes


[sysvol]
    path = /var/lib/samba/sysvol
    read only = no



```

shares.conf
```
[homes]    comment = Home Directories
    path = /home/%S
    read only = no
    browseable = no
    create mask = 0611
    directory mask = 0711
    vfs objects = acl_xattr full_audit
    full_audit:success = connect opendir disconnect unlink mkdir rmdir open rename
    full_audit:failure = connect opendir disconnect unlink mkdir rmdir open rename


# Shares


[Photos]
    comment = Photos
    path = /home/samba/shares/pics
    browseable = Yes
    read only = No
    force create mode = 0660
    force directory mode = 0660
    vfs objects = acl_xattr full_audit
    acl_xattr:ignore system acls = yes
    full_audit:success = connect opendir disconnect unlink mkdir rmdir open rename
    full_audit:failure = connect opendir disconnect unlink mkdir rmdir open rename


[Movies]
    comment = Movies
    path = /home/samba/shares/movies
    browseable = Yes
    read only = No
    force create mode = 0660
    force directory mode = 0660
    vfs objects = acl_xattr full_audit
    acl_xattr:ignore system acls = yes
    full_audit:success = connect opendir disconnect unlink mkdir rmdir open rename
    full_audit:failure = connect opendir disconnect unlink mkdir rmdir open rename


[Backup]
    comment = Backup
    path = /home/samba/shares/backup
    browseable = Yes
    read only = No
    force create mode = 0660
    force directory mode = 0660
    vfs objects = acl_xattr full_audit
    acl_xattr:ignore system acls = yes
    full_audit:success = connect opendir disconnect unlink mkdir rmdir open rename
    full_audit:failure = connect opendir disconnect unlink mkdir rmdir open rename


[Music]
    comment = Music
    path = /home/samba/shares/music
    browseable = Yes
    read only = No
    force create mode = 0660
    force directory mode = 0660
    vfs objects = acl_xattr full_audit
    acl_xattr:ignore system acls = yes
    full_audit:success = connect opendir disconnect unlink mkdir rmdir open rename
    full_audit:failure = connect opendir disconnect unlink mkdir rmdir open rename



```

openchange.conf
```
[global]    dcerpc endpoint servers = +epmapper, +mapiproxy
    dcerpc_mapiproxy:server = true
    dcerpc_mapiproxy:interfaces = exchange_emsmdb, exchange_nsp, exchange_ds_rfr


    mapistore:namedproperties = mysql
    namedproperties:mysql_user = openchangeuser
    namedproperties:mysql_pass = openchangepw
    namedproperties:mysql_host = localhost
    namedproperties:mysql_db = openchange


    mapistore:indexing_backend = mysql://openchangeuser:openchangepw@localhost/openchange
    mapiproxy:openchangedb = mysql://openchangeuser:openchangepw@localhost/openchange[/QUOTE]

Samba error samba.log shows follwoing:

[QUOTE][2015/05/28 11:42:12.739959,  3] ../source3/smbd/msdfs.c:974(get_referred_path)  get_referred_path: |Movies| in dfs path \10.10.10.2\Movies is not a dfs root.
[2015/05/28 11:42:12.784184,  3] ../source3/smbd/vfs.c:1137(check_reduced_name)
  check_reduced_name [.] [/home/samba/shares/movies]
[2015/05/28 11:42:12.784267,  3] ../source3/smbd/vfs.c:1267(check_reduced_name)
  check_reduced_name: . reduced to /home/samba/shares/movies
[2015/05/28 11:42:12.784341,  3] ../source3/smbd/dosmode.c:163(unix_mode)
  unix_mode(.) returning 0664
[2015/05/28 11:42:12.815098,  3] ../source3/smbd/vfs.c:1137(check_reduced_name)
  check_reduced_name [.svn] [/home/samba/shares/movies]
[2015/05/28 11:42:12.815246,  3] ../source3/smbd/vfs.c:1267(check_reduced_name)
  check_reduced_name: .svn reduced to /home/samba/shares/movies/.svn
[2015/05/28 11:42:12.815392,  3] ../source3/smbd/dosmode.c:163(unix_mode)
  unix_mode(.svn) returning 0664
[2015/05/28 11:42:13.593361,  3] ../source3/smbd/trans2.c:3092(smbd_do_qfsinfo)
  smbd_do_qfsinfo: level = 1001
[2015/05/28 11:42:13.593584,  3] ../source3/smbd/trans2.c:3092(smbd_do_qfsinfo)
  smbd_do_qfsinfo: level = 1005
[2015/05/28 11:42:14.273699,  3] ../source3/smbd/vfs.c:1137(check_reduced_name)
  check_reduced_name [New folder] [/home/samba/shares/movies]
[2015/05/28 11:42:14.273850,  3] ../source3/smbd/vfs.c:1267(check_reduced_name)
  check_reduced_name: New folder reduced to /home/samba/shares/movies/New folder
[2015/05/28 11:42:14.274001,  3] ../source3/smbd/dosmode.c:163(unix_mode)
  unix_mode(New folder) returning 0664
[2015/05/28 11:42:14.293660,  3] ../source3/smbd/vfs.c:1137(check_reduced_name)
  check_reduced_name [New folder] [/home/samba/shares/movies]
[2015/05/28 11:42:14.293811,  3] ../source3/smbd/vfs.c:1267(check_reduced_name)
  check_reduced_name: New folder reduced to /home/samba/shares/movies/New folder
[2015/05/28 11:42:14.293877,  3] ../source3/smbd/dosmode.c:163(unix_mode)
  unix_mode(New folder) returning 0775
[2015/05/28 11:42:14.294247,  2] ../source3/smbd/open.c:3107(open_directory)
  open_directory: unable to create New folder. Error was NT_STATUS_DISK_FULL
[2015/05/28 11:42:14.319880,  3] ../source3/smbd/trans2.c:3092(smbd_do_qfsinfo)
  smbd_do_qfsinfo: level = 1003
[2015/05/28 11:42:14.332220,  3] ../source3/smbd/trans2.c:3092(smbd_do_qfsinfo)
  smbd_do_qfsinfo: level = 1003
```

Any ideas?

BR
Tom

---

### Post by volkswagner on 2015-05-29
Please provide the following info:

```
mount
```
```
cat /etc/fstab
```
```
df -h
```
```
sudo du -h / --max-depth=1
```
```
sudo du -h /home --max-depth=1
```

---

### Post by jayjay89 on 2015-06-01
mount
> 
/dev/md128 on / type ext4 (rw,errors=remount-ro,acl,user_xattr,usrquota,grpquota,acl)proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=52428800)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
/dev/sda2 on /div type ext4 (rw,acl,user_xattr)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)


cat /etc/fstab
> 
#       /etc/fstab:     static  file    system  information.
#
#       Use     'blkid' to      print   the     universally     unique  identifier      for     a
#       device; this    may     be      used    with    UUID=   as      a       more    robust  way     to      name    devices
#       that    works   even    if      disks   are     added   and     removed.        See     fstab(5).
#
#       <file   system> <mount  point>  <type>  <options>       <dump>  <pass>
#       /       was     on      /dev/md127      during  installation
UUID=6950b57f-c070-4358-9362-41e6e3120bee       /       ext4    errors=remount-ro,acl,user_xattr,usrquota,grpquota,acl  0       1
#       /boot/efi       was     on      /dev/sda1       during  installation
UUID=08E8-003C  /boot/efi       vfat    defaults        0       1
#       /div    was     on      /dev/sda2       during  installation
UUID=8b98c464-fc9a-4c51-a141-30139a6aa893       /div    ext4    defaults,acl,user_xattr 0       2
#       swap    was     on      /dev/md126      during  installation
UUID=92affe7b-632c-437c-aa82-53cc68e8fc82       none    swap    sw      0       0
none    /run/lock       tmpfs   rw,noexec,nosuid,nodev,size=52428800    0       0


/home /share    none    bind  0  0





df -h
> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/md128      7.3T  4.7T  2.3T  68% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           380M  1.1M  379M   1% /run
none             50M     0   50M   0% /run/lock
none            1.9G  132M  1.8G   7% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1        93M  3.4M   90M   4% /boot/efi
/dev/sda2       294G   63M  279G   1% /div




sudo du -h / --max-depth=1 ... unfortunately I lost the connection to the server so I've posted only the output I could receive
> 
4.0K    /dev
5.3M    /root
7.8M    /etc
12K     /media
4.6T    /home
4.0K    /share_
16K     /lost+found
69M     /boot
1.2G    /usr
7.2M    /bin
1.1M    /srv





sudo du -h /home --max-depth=1
> 
4.6T    /home/samba
2.1G    /home/user1
20K     /home/user2
16K     /home/Test
24K     /home/user3
16K     /home/user4
4.0K    /home/www-data
4.0K    /home/.locks
8.0K    /home/user5
36K     /home/administrator
4.0K    /home/user6
16K     /home/scanner
28K     /home/user7
16K     /home/user8
2.5M    /home/user9
4.6T    /home


---

