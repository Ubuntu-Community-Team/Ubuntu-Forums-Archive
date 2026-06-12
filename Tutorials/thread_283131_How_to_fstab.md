---
title: "How to fstab"
date: 2006-10-23
forum: Tutorials
---

### Post by bodhi.zazen on 2006-10-23
[IMG]http://www.faculty.de.gcsu.edu/%7Edvess/ids/fap/Rox/14.jpg[/IMG]

[SIZE=6]**Understanding fstab**[/SIZE]

Sorry this is such a long post.

[SIZE=2]**I added much of this information to the Ubuntu wiki.**

update May 2009 : [/SIZE][tbuss]("http://ubuntuforums.org/member.php?u=256430") kindly converted this post to a pdf which is available [here]("http://www.scribd.com/doc/15124069/Understandingfstab%5BSIZE=2"). The pdf can be downloaded if you log into scribd. You may use openid to log in, so should be easy if you also have an account at launchpad.

[[SIZE=2]Ubuntu Wiki : fstab[/SIZE]]("https://help.ubuntu.com/community/Fstab")

There are essentially 5 sections:

[LIST=1]
[*]Introduction / Mount.
[*]"fstab syntax" - Syntax and fstab options.
[*]How to label, FAT and Linux file systems.
[*]Examples, FAT and Linux native file systems.
[*]References
[/LIST]

**Scroll down to the section you need.**

[SIZE=3]_**Introduction**_[/SIZE]

[SIZE=2][COLOR=blue]If you simply want a gui tool to manage your partitions (/etc/fstab) try [Pysdm]("http://pysdm.sourceforge.net/").[/COLOR][/SIZE]

[IMG]http://pysdm.sourceforge.net/screenshots/fstab_04.png[/IMG]

[indent][indent]pysdm Screen Shot[/indent][/indent]

/etc/fstab is a system configuration file and is used to tell the Linux kernel which partitions (file systems) to mount and where on the file system tree.

/etc/mtab is an index of all mounted partitions/file systems.

[COLOR=darkred]_Note_: See references section at the end of this how to for useful links.[/COLOR]

[SIZE=2]How to mount[/SIZE]

_The mount command and fstab go hand in hand_:
[LIST=1]
[*]Options for mount and fstab are similar.
[*]If a device/partition is not listed in fstab **ONLY ROOT** may mount the device/partition.
[*]Users can mount a removable device using pmount.
[*]Users may mount a device/partition if the device is in fstab with the proper options.
[/LIST]

[How to mount]("http://www.tuxfiles.org/linuxhelp/mounting.html")
[Mount Partitions Automatically]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") (At BOOT).
[[COLOR=navy]Filesystems and Mounting[/COLOR]]("http://users.bigpond.net.au/hermanzone/p10.htm") **[COLOR=red]Thanks Hermanzone[/COLOR]**

mount has a multitude of options. Manpage: [man mount]("http://www.die.net/doc/linux/man/man8/mount.8.html")

_pmount_: Pmount allows a user to mount _removable media_.
pmount uses /media/<NAME> as the mount point.

Syntax: > pmount <device> <NAME>Example:```
pmount /dev/dsa1 data
```This creates a directory "data" in /media (mount point is /media/data) and mounts your removable device there.

To unmount:```
pumount <NAME>
```_Note_: pmount does not like to mount to an existing directory in /media.
[LIST]
[*]For example, if you have a directory /media/usb ; pmount /dev/sda1 usb may fail.
[*]If you are having problems with gnome-volume-manager or pmount check the contents of /media and delete directories as needed.
[*]Obviously do not delete a directory in /media if a device is mounted to this mount point.
[/LIST]

[Configure pmount for internal drives]("http://doc.gwos.org/index.php/Understanding_fstab#Configure_pmount_for_internal_HD")

[SIZE=2]**To show your partitions/usb devices, first plug in your usb card.**[/SIZE]

_To list your mounted partitions_:```
mount
```_To list all your partitions, mounted or not_:```
sudo fdisk -l
```_To list all your partitions by **UUID**_:
First connect all your devices, then:
```
ls /dev/disk/by-uuid -alh
```============== END OF INTRODUCTION ===============


[SIZE=3]**_fstab Syntax_**[/SIZE]

> [Device] [Mount Point] [File_system] [Options] [dump] [fsck order][SIZE=2]**Device = Physical location.**[/SIZE]

/dev/hd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR] or /dev/sd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR].

[COLOR=red]x[/COLOR] will be a letter starting with a, then b,c,....
[COLOR=green]y[/COLOR] will be a number starting with 1, then 2,3,....

Thus hda1 = First partition on the master HD.[INDENT] See [Basic partitioning]("http://ubuntuforums.org/showthread.php?t=282018") for more information[/INDENT]_**Note**_**: zip discs are always numbered "4".**
Example: USB Zip = /dev/sda[COLOR=red]4[/COLOR].

_**Note**_[B]: You can also identify a device by udev, volume label (AKA LABEL), or uuid.

These fstab techniques are helpful for removable media because the device (/dev/sd[COLOR=red]x[/COLOR]y) may change. For example, sometimes the USB device will be assigned /dev/sda1, other times /dev/sdb1. This depends on what order you connect USB devices, and where (which USB slot) you use to connect. This can be a major aggravation as you must identify the device before you can mount it.  fstab does not work well if the device name keeps changing.[/B]

To list your devices, first put connect your USB device (it does not need to be mounted).
_By volume label_:```
ls /dev/disk/by-label -lah
```_By id_:```
ls /dev/disk/by-id -lah
```_By uuid_:```
ls /dev/disk/by-uuid -lah
```**IMO, LABEL is easiest to use as you can set a label and it is human readable.**

_The format to use instead of the device name in the fstab file is_:

LABEL=<label> (Where <label> is the volume label name, ex. "data").

UUID=<uuid> (Where <uuid> is some alphanumeric (hex) like fab05680-eb08-4420-959a-ff915cdfcb44).

Again, IMO, using a label has a strong advantage with **removable media** (flash drives).

[SIZE=2]**See _How to use Labels_ below.**[/SIZE]

_For udev_: udev does the same thing as LABEL, but I find it more complicated.
See [How to udev]("http://ubuntuforums.org/showthread.php?t=168221") for a very nice how to on udev.


[SIZE=2]**Mount point.**[/SIZE]
This is where the partition is mounted or accessed within the "tree" (ie /mnt/hda1). 
You can use any name you like.
In general
[LIST=1]
[*]/mnt Typically used for fixed hard drives HD/SCSI. [COLOR=darkred]If you mount your hard drive in /mnt it will NOT show in "Places" and your Desktop.[/COLOR]
[*]/media Typically used for removable media (CD/DVD/USB/Zip). [COLOR=navy]If you mount your hard drive in /media it WILL show in "Places" and your Desktop.[/COLOR]
[/LIST]

Examples:
[LIST=1]
[*]/mnt/windows
[*]/mnt/data
[*]/media/usb
[/LIST]

_To make a mount point_:```
sudo mkdir /media/usb
```[SIZE=2]**File types:**[/SIZE]

**_auto_:** The file system type (ext3, iso9660, etc) it detected automatically. Usually works. Used for removable devices (CD/DVD, Floppy drives, or USB/Flash drives) as the file system may vary on these devices.


_Linux file systems_: ext2, ext3, jfs, reiserfs, reiser4, xfs, swap.

_Windows_:
vfat = FAT 32, FAT 16
ntfs= NTFS

_Note_: For NTFS rw [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009")

_CD/DVD/iso_: iso9660[INDENT]_To mount an iso image (*.iso NOT CD/DVD device)_: ```
sudo mount -t iso9660 -o ro,loop=/dev/loop0 <ISO_File> <Mount_Point>
```[/INDENT]_Network file systems_: **This section assumes the server and client are already setup.**


_nfs_ Example:> server:/shared_directory /mnt/nfs nfs <options> 0 0[INDENT]More detailed information on [nfs]("https://help.ubuntu.com/community/SettingUpNFSHowTo")[/INDENT]_smb_ (samba) : Samba mounts can be performed very easily via gui tools (See [Ubuntu Wiki Setting up Samba]("https://help.ubuntu.com/community/SettingUpSamba")). If you mount a samba share with the gui tools it will be placed in ~/.gvfs , a hidden directory in your home directory.

This section is limited to fstab and you will need a fstab entry to mount samba shares at boot.

smbfs is now depreciated for cifs : [http://linux-cifs.samba.org/](http://linux-cifs.samba.org/)

cifs still uses a credentials file to avoid the need to enter a password. If you do not use a credentials file, you will mount a samba share with sudo and enter your username and password in a terminal.

> //Server/share /mnt/samba cifs users,auto,credentials=/path/credentials_file,noexec,noperm  0 0
[LIST]
[*]Server = Name (if in /etc/hosts) or IP Address of samba server.
[*]share = Name of shared directory (folder).
[*]/mnt/samba = your desired mount point.
[*]/path/credentials_file = full path to your credentials file. A credentials file should be owned by root (permissions 400) and contain two lines :
> username = samba_user[FONT=monospace]
[/FONT]password = samba_user_password
[/LIST]
[INDENT][INDENT]samba_user = samba user (on server).[/INDENT][INDENT] samba_user_password = samba user password (on server).[/INDENT][/INDENT]
[LIST]
[*]noexec for security (it can be bypassed ...).
[*]noperm - Allows users to read/write samba shares ([COLOR=red]you still need to configure the server to allow rw on shares !!![/COLOR]). Without this option, users will not be able to have rwx access to new directories in the samba share. See [this thread]("http://ubuntuforums.org/showthread.php?t=455129") for further details.
[/LIST]
 
smbfs : depreciated, but similar.

> //win_box/shared_folder /mnt/samba smbfs rw,credentials=/home/user_name/winbox-credentials.txt 0 0[COLOR=blue]And from Buck2348:[/COLOR][INDENT]> I don't mount any vfat shares but uid and gid work with smbfs shares.  I might have to try out your syntax.

I could not automount at boot my smbfs shares until I found the [this fix]("http://www.ubuntuforums.org/showthread.php?t=103274") in the Forums.  I hope it will help someone else.  I think the problem was related to the fact that I don't use a username and password in the Windows systems.  All I had to do was add ```
username=share,password=
``` to the options list in the fstab line for these shares.[/INDENT][INDENT]More detailed information on see : [The Official Samba 3.2.x HOWTO and Reference Guide]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/")[/INDENT]_sshfs_ : Network shares over ssh

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

```
sshfs#user@server:/share  fuse  user,allow_other  0  0
```
[LIST]
[*]"Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
[*]"share" = name of the shared directory
[/LIST]


[SIZE=2]**Options:**[/SIZE]

**Ubuntu 8.04 now defaults to "relatime". For a discussion of this option see** : [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

[COLOR=red]defaults = rw, suid, dev, exec, auto, nouser, and async.[/COLOR]

[COLOR=blue]Options for a separate /home : nodev,nosuid,relatime[/COLOR]

My recommended options for [COLOR=navy]removable (USB) drives[/COLOR] are in [COLOR=green]green[/COLOR].

[COLOR=red]auto[/COLOR]= mounted at boot
[COLOR=green]noauto[/COLOR]= not mounted at boot

[COLOR=green]user[/COLOR]= when mounted the mount point is owned by the user who mounted the partition
[COLOR=red]users[/COLOR]= when mounted the mount point is owned by the user who mounted the partition and the group users

[COLOR=red]ro[/COLOR]= read only
[COLOR=green]rw[/COLOR]= read/write

**_VFAT/NTFS_**:

**In general, ownership and permissios of vfat / ntfs are set at the time of mounting**. This is often a source of confusion.
 
uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or GID #.

umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

[COLOR=blue]Best is to set directories with executable permissions and file with read write. To do this, use fmask and dmask (rather then umask):
dmask=027
fmask=137

With these options files are not executable (all colored green in a terminal w/ ls)[/COLOR]

**NTFS ONLY:**
You may now mount a ntfs partition with the "permissions" option. This options supports standard linux permissions on ntfs.
> UUID=12102C02102CEB83 /media/windows ntfs-3g auto,users,permissions 0 0

**_Linux native file systems_**: Use defaults or users. To change ownership and permissions, mount the partition, then use chown and chmod.

Note: Warning re: sync and flash devices:
    [[COLOR=red]_Warning_[/COLOR]]("http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html")

Additional Options: (From [wiki.linuxquestions.org/wiki/Fstab]("http://wiki.linuxquestions.org/wiki/Fstab")):

[LIST]
[*]sync/async - All I/O to the file system should be done (a)synchronously.
[*]auto - The filesystem can be mounted automatically (at bootup, or when mount is passed the -a option). This is really unnecessary as this is the default action of mount -a anyway.
[*]noauto - The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.
[*]dev/nodev - Interpret/Do not interpret character or block special devices on the file system.
[*]exec / noexec - Permit/Prevent the execution of binaries from the filesystem.
[*]suid/nosuid - Permit/Block the operation of suid, and sgid bits.
[*]ro - Mount read-only.
[*]rw - Mount read-write.
[*]user - Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.
[*]nouser - Only permit root to mount the filesystem. This is also a default setting.
[*]defaults - Use default settings. Equivalent to rw, suid, dev, exec, auto, nouser, async.
[*]_netdev - Used for network shares (nfs, samba, sshfs, etc), mounting the network share is delayed until after the boot process brings up the network (otherwise the mount will fail as the network is not up).
[/LIST]


[SIZE=2]**Dump**[/SIZE]
Dump: Dump field sets whether the backup utility dump will backup file system. If set to "0" file system ignored, "1" file system is backed up.



[SIZE=2]**Fsck order**[/SIZE]
Fsck: Fsck order is to tell fsck what order to check the file systems, if set to "0" file system is ignored.

See also: [Tuning the Filesystem Check at Bootup]("http://ubuntu.wordpress.com/?s=tune2fs&searchbutton=go%21")

[SIZE=2]**Fstab Examples**[/SIZE]


> /dev/sda14  /mnt/zen  ext3  relatime  0  2

# Usb device (assuming vfat)
/dev/sdb1  /media/usb  auto  users,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0

#Data partition
LABEL=data  /mnt/usr_data  ext3  auto,users,rw,relatime  0  0

# Flash drive By UUID
UUID=fab05680-eb08-4420-959a-ff915cdfcb44 /media/flash vfat user,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0


/dev/disk/by-id/usb-IOMEGA_ZIP_250_059B00301400B0F1-part4  /mnt/zip  vfat  users,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0

/dev/hda1  /mnt/windows  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0

# VFAT
# FAT ~ Linux calls FAT file systems vfat)
# /dev/hda1
UUID=12102C02102CEB83  /media/windows vfat  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137   0  0

# NTFS ~ Use ntfs-3g for write access (rw) 
# /dev/hda1
UUID=12102C02102CEB83 /media/windows ntfs-3g auto,users,permissions 0 0

[COLOR=blue]# Separate Home
# /dev/sda7
UUID=413eee0c-61ff-4cb7-a299-89d12b075093  /home  ext3  nodev,nosuid,relatime  0  2[/COLOR]

# Samba
//server/share  /media/samba  cifs  user=user,uid=1000,gid=100,noperm  0  0

# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory
# "user" = your samba user
# This set up will ask for a password when mounting the samba share. If you do not want to enter a password, use a credentials file.
# replace "user=user" with "credentials=/etc/samba/credentials" In the credentials file put two lines
[indent]# user=user[/indent]
[indent]# password=password[/indent]
# make the file owned by root and ro by root (sudo chown root.root /etc/samba/credentials && sudo chmod 400 /etc/samba/credentials)

# NFS
Server:/share  /media/nfs  nfs  rsize=8192,wsize=8192,noexec,nosuid

# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory

#SSHFS
Sshfs#user@server:/share  fuse  user,allow_other  0  0

# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory=========== End of fstab =============


[SIZE=3]**_How to Label_**[/SIZE]

_Linux_: How the label and the UUID are set depends on the file system type used. It can normally be set when creating/formatting the file system and the file system type usually has some tool to change it later on (e.g. e2tunefs,xfs_admin,reiserfstune,etc.)

[Labels]("http://www.linux.com/howtos/Partition/labels.shtml")

_Mke2fs/e2label/tune2fs_:

Note: For either ext2 or ext3 file systems.

[COLOR=red][B][SIZE=2]_WARNING_: mke2fs will reformat your partition and set a label at the same time. This will delete any data on the target partition.

To set a label without reformatting use e2label or tune2fs[/SIZE][/B][/COLOR]

[LIST=1]
[*]Make a label:```
mke2fs -L <label> <dev>
```OR```
e2label <dev> <label>
```OR```
tune2fs -L <label> <dev>
```Examples:> mke2fs -L data /dev/hda3 OR> e2label /dev/hda3 dataOR> tune2fs -L data /dev/hda3
[*]Create a mount point:```
sudo mkdir /media/data
```
[*]Add an entry to /etc/fstab:> LABEL=data /media/data ext3 defaults 0 0
[*]To mount:```
sudo mount LABEL=data
```
[/LIST]


_ReiserFS_:
 Use reiserfstune:```
reiserfstune --l <Label> <device>
```[INDENT]_Note_:That is a small "L" and not the number 1.[/INDENT]_JFS_:
 Use jfs_tune:```
jfs_tune -L <Label> <device>
```To show the label: ```
jfs_tune -l <device>
```[INDENT]_Note_:That is a small "L" and not the number 1.[/INDENT]_XFS_:
 Use xfs_admin:```
sudo xfs_admin -L <Label> <device>
``` To show the label: ```
xfs_admin -l <device>
```[INDENT]_Note_:That is a small "L" and not the number 1.[/INDENT]_FAT (Windows partitions)_:

Use mtools to label a FAT partition:

[LIST=1]
[*]Install mtools:```
sudo aptitude install mtools
```
[*]Copy the mtools configuration file to ~:```
cp /etc/mtools.conf ~/.mtoolsrc
```_Note_: ~ is shorthand for /home/user_name.
[*]Mount your flash drive.
[*]Edit ~/.mtoolsrc:```
gedit ~/.mtoolsrc
```
[*]Add these lines to the end of ~/.mtoolsrc:
> drive i: file="<device>"
mtools_skip_check=1Where <device> is the device assigned to your mounted USB device/flash drive (ie sda1, sdb1, ...).
_**Note**_**: You can do this from the command line:**```
echo 'drive i: file="<device>"' >> ~/.mtoolsrc
echo mtools_skip_check=1 >> ~/.mtoolsrc
```[INDENT]Although you will need to edit ~/.mtoolsrc for each new device if the device assignment changes.[/INDENT]_**Example**_**: = drive i: file="/dev/sda1"**
[*]Change to drive i:```
mcd i:
```
[*]Check the current label:```
mlabel -s i:
```
[*]Change the current label:```
sudo mlabel -s i:DATA
```
[*]Or ```
sudo mlabel i:DATA
```[INDENT]pieroxy reports the -s flag did not work, [COLOR=blue]thanks pieroxy[/COLOR][/INDENT][INDENT]_Note_: mlabel USES ALL CAPS.[/INDENT]
[*]Add an entry to fstab:> LABEL=DATA <mount_point> vfat defaults 0 0_Note_: You can also mount the usb device with:```
mount LABEL=<label>
```
[/LIST]

_NTFS (Windows partitions)_:[INDENT][COLOR=blue]Thanks to rudyj for pointing out the oversight.[/COLOR][/INDENT]Use ntfsprogs:

First install ntfsprogs:```
sudo aptitude install ntfsprogs
```Or use Synaptic.

Then:

[LIST=1]
[*]Show label:```
ntfslabel <device>
```
[*]Change label:```
ntfslabel <device> <label>
```[INDENT]**Where:**
[LIST]
[*]**<label> = your new label**
[*]**<device> = your partition to label (/dev/hda1 perhaps)**
[/LIST]
[/INDENT]
[*]Add an entry to fstab:> LABEL=DATA <mount_point> ntfs(or ntfs-3g) defaults 0 0_Note_: You can also mount the usb device with:```
mount LABEL=<label>
```
[/LIST]


============== END OF LABEL ===============


[SIZE=3]**_Examples of fstab options_**[/SIZE]


[COLOR=blue]**[SIZE=2]********* FAT **********[/SIZE]**[/COLOR]

FAT partitions are easy to share between Linux and Windows as both OS will read FAT "out of the box" without additional installation or configuration.

In this example I will use /mnt/data as my mount point.

```
sudo mkdir /mnt/data
```fstab:> LABEL=data /mnt/data vfat <***see options below***> 0 0Default permissions of /mnt/data:> drwxr-xr-x  2 root root
[LIST=1]
[*]_fstab options_: **defaults**
mount /mnt/data yields: mount: only root can mount /dev/sdb1 on /mnt/data

sudo mount /mnt/data mounts the device.
Permissions:> drwxr-xr-x  7 root root_Note_: ONLY ROOT has rw permissions. [-(
[*]_fstab options_: **users,noauto,rw**
mount /mnt/data mounts the partition.
Permissions:> drwxr-xr-x  7 bodhi adm_Note_: The user can mount the device and has rw permissions. :p
_Note_: The ownership and permissions of the mount point have changed !
[*]_fstab options_: **users,noauto,gid=100,umask=007**
mount /mnt/data mounts the partition.
Permissions:> drwxrwx---  7 bodhi users_Note_: The user can mount the device and now both the user and the users group have rw permissions.
_Note_: The ownership and permissions of the mount point have changed again ! :twisted:
[/LIST]


[COLOR=green]**[SIZE=2]********* Linux Native File Systems **********[/SIZE]**[/COLOR]

**In this example I will use ext3, but this holds true for ext2, reiserfs, jfs, and xfs.**

```
sudo mkdir /mnt/ext3
```fstab:> LABEL=ext3 /mnt/ext3 auto **<see options below>** 0 0
[LIST=1]
[*]_fstab options_: **defaults**
mount /mnt/data yields: mount: only root can mount LABEL=ext3 on /mnt/ext3

sudo mount /mnt/ext3 mounts the device.
Permissions:> bodhi@Arch:~$ls -l /mnt | grep ext3
drwxr-xr-x  3 bodhi users  1024 2006-11-07 17:26 ext3_Note_: Ownership has changed ! owner=bodhi, group=users, however ONLY USER (and root of course) has rw permissions.
[*]_fstab options_: **users,noauto**

mount /mnt/ext3 mounts the partition.
Permissions:> bodhi@Arch:~$mount /mnt/ext3/
bodhi@Arch:~$ls -l /mnt | grep ext3
drwxr-xr-x  3 bodhi users  1024 2006-11-07 17:26 ext3_Note_: The user can mount the device and has rw permissions. :p
_Note_: Ownership remains bodhi:users

**_Note_: ext2 and ext3 do not take uid=xxx, gid=xxx, or umask=xxx**

To set group rw permissions:
_fstab options_: **users,noauto**
[LIST=1]
[*]mount the partition: **mount /mnt/ext3**
[*]Set permisions of the mount point: **chmod 777 /mnt/ext3**
[/LIST]

**[COLOR=red]The set ownership and permissions will remain in effect with un-mount and re-boot.[/COLOR]**

Example:
> **bodhi@Arch:~$chmod 777 /mnt/ext3**
bodhi@Arch:~$ls -l /mnt | grep ext3
drwxrwxrwx  3 bodhi users  1024 2006-11-07 17:51 ext3
bodhi@Arch:~$**umount /mnt/ext3/**
bodhi@Arch:~$ls -l /mnt | grep ext3
[COLOR=red]drwxr-xr-x  2 root  root   4096 2006-11-07 17:28 ext3[/COLOR]
bodhi@Arch:~$**mount /mnt/ext3/**
bodhi@Arch:~$ls -l /mnt | grep ext3
[COLOR=blue]drwxrwxrwx  3 bodhi users  1024 2006-11-07 17:51 ext3[/COLOR]
bodhi@Arch:~$_Note_: The permissions revert when the partition is un-mounted [COLOR=red]RED[/COLOR]
_Note_: The permissions remain rw when the partition is re-mounted [COLOR=blue]BLUE[/COLOR]
Permissions:
_Note_: The user can mount the device and now both the user and the users group have rw permissions. 8)
[/LIST]


============== END OF EXAMPLES ===============


_[SIZE=3]**References**[/SIZE]_

_Partitioning_: [Basic partitioning]("http://ubuntuforums.org/showthread.php?t=282018")

_Mount_:

[How to mount filesystems in Linux]("http://www.tuxfiles.org/linuxhelp/mounting.html")
[Ubuntu Automatically Mount Partitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
[man mount]("http://www.die.net/doc/linux/man/man8/mount.8.html")
[Mount Other Filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm")

_Fstab_:
[fstab wiki]("http://en.wikipedia.org/wiki/Fstab")
[How to edit and understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")
[Tuning the Filesystem Check at Bootup]("http://ubuntu.wordpress.com/?s=tune2fs&searchbutton=go%21")

_Labels_: [How to use Labels]("http://www.linux.com/howtos/Partition/labels.shtml")

_udev_: [How to udev]("http://ubuntuforums.org/showthread.php?t=168221")

_NTFS_: [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009")

_Zip dirve how-to_: [How to Zip Drive]("http://www.faqs.org/docs/Linux-mini/ZIP-Drive.html")

_nfs_:
[How to set up NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[How to NFS v4]("https://help.ubuntu.com/community/NFSv4Howto")
[[COLOR=black]Debian/Ubuntu NFS Guide[/COLOR]]("http://www.unhandledexceptions.com/tutorials/tut_11.html") [COLOR=navy]Short but sweeeet ![/COLOR]

_Mount Windows Sares_: [Mount Windows shares permanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

_Samba_:
[Setting up Samba]("https://help.ubuntu.com/community/SettingUpSamba")
[How to mount smbfs shares permanently]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently")

[IMG]http://www.laiwa.com/cache/3/1/531045_70x70.gif[/IMG] [COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen[/COLOR]

---

### Post by 5-HT on 2006-10-24
Thanks for the detailed walkthrough!
I'm sure the UUID info will come in handy once Edgy hits.

---

### Post by givré on 2006-10-24
Great works man, this is a must ;)

---

### Post by mssever on 2006-10-24
Thanks for the comprehensive guide. I'll be pointing people here.

---

### Post by Abhi Kalyan on 2006-10-27
swell bodhi.zazen,
Thats grand detailing there, Thank You.

---

### Post by xyz on 2006-11-06
Great job! Thanks a lot,bodhi.zazen!

---

### Post by Gen2ly on 2006-12-02
I learned howto mount my hfsplus at startup.
> mkdir /mnt/Macintosh_HD
Or whatever you choose to call it, and add this line to your fstab:

> /dev/hda11 /media/Macintosh_HD hfsplus rw,exec,auto,users 0 0

Sweet guide thanks!

---

### Post by bodhi.zazen on 2006-12-02
> **Dirk.R.Gently said:**
> What about HFSPlus drives.  As of the moment I can't even get a UUID, though I have it mounted.  I mounted with:

sudo mount /dev/hda## -t hfsplus /media/hda##

I was hoping to have this partition mounted at boot.

Hmm...  Ive no experience with HFSPlus....

Try:```
ls /dev/disk/by-label -lh
```
To see if the partition/device has a label.

If so... try this fstab entry:
> LABEL=## /media hfsplus defaults 0 0


If not... try this fstab entry:
> /dev/hda## /media/hda## hfsplus defaults 0 0

Here are some links that may help you....

[Gentoo wiki How to hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

[Gentoo wiki how to IPOD](http://gentoo-wiki.com/HOWTO_Using_an_iPod_With_Gentoo_Linux)

[Ubuntu Forums hfsplus](http://ubuntuforums.org/showthread.php?&t=2221)

If you would be so kind as to post the solution I will update this "how-long" as xpod calls it :p

---

### Post by bulldog on 2006-12-02
Well bodhi,you're a busy man.

I definitely bookmark this one,it should come handy some day.

Thank you very much for this howto.

---

### Post by pawik on 2006-12-11
great guide, helped me a lot ;)

there is also options not mentioned in guide but i found them in some examples: nls, iocharset for correct encodeing file names. I don't know anything more about them.

Anyway when i tryed to use a cd where filenames had special characters (Polish), but instead of them there were non-alphabetical signs.
So i used this entry in fstab and it helped

```
/dev/hdd  /media/cdrom0  udf,iso9660  **utf8**,user,noauto  0  0
```

---

### Post by Buck2348 on 2007-01-08
Excellent how-to--it helped me a lot, and I haven't nearly finished studying it.  :-k 

One question and one observation:
> VFAT/NTFS:
umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
to set permissions of 700, umask=077
o= Sets owner. Syntax: must use owned BY USER ID # not name.
g= sets group ownership of mount point. Again syntax is by GROUP ID # not name.
I can't find any reference to this in man mount, to which man fstab refers for details on mounting options.  Instead it mentions uid=xxx and gid=xxx to set the owner and group.  I don't mount any vfat shares but uid and gid work with smbfs shares.  I might have to try out your syntax.

I could not automount at boot my smbfs shares until I found the [this fix]("http://www.ubuntuforums.org/showthread.php?t=103274") in the Forums.  I hope it will help someone else.  I think the problem was related to the fact that I don't use a username and password in the Windows systems.  All I had to do was add ```
username=share,password=
``` to the options list in the fstab line for these shares.

Thanks again for a great article.

Buck

---

### Post by ~LoKe on 2007-01-08
Nice work; very thorough!

---

### Post by pieroxy on 2007-01-17
Hi,

Changing the label for a vfat drive doesn't take the '-s' option. So the line 

> sudo mlabel -s i:****DATA

should read:

> sudo mlabel i:****DATA

Thanks for the great post.

---

### Post by aretei on 2007-01-21
deleted

---

### Post by thor918 on 2007-01-28
I had problems putting the uuid like you had in your example of fstab
however I did find a way that worked for me.

# /dev/sdb 
/dev/disk/by-uuid/c4e0ea4c-1806-468e-85fa-1730632e4ee5       /mountpoint        ext3    defaults  0       1

if I format the uuid line like this instead it works for me.

---

### Post by malarky on 2007-02-08
How can I mount a windows share that has a space? eg: //server/stupid share name

Ugly, I know, but changing the share name is not an option :(

---

### Post by bodhi.zazen on 2007-02-08
You have to "escape" the spaces with a \ 

Like this :

> //server/stupid\ share\ name

---

### Post by mrwilloby on 2007-02-13
> Make a label:```
mke2fs -L <label> <dev>
```

First of all, great post, very helpful. 

I know I should be more responsible and figure out what I'm doing first because I interpreted this section and this code in particular as only making a label on my partition, not as it erasing everything. I lost a few scores of GB, but I think it was all replaceable.

After that I found out there is no way at all to undo a mke2fs command.

Pointing people to **tune2fs -L** might be helpful. I found that afterwards.

---

### Post by bodhi.zazen on 2007-02-14
> **mrwilloby said:**
> I know I should be more responsible and figure out what I'm doing first because I interpreted this section and this code in particular as only making a label on my partition, not as it erasing everything. I lost a few scores of GB, but I think it was all replaceable.

OMG, I am so sorry. :frown:

> After that I found out there is no way at all to undo a mke2fs command.

Pointing people to **tune2fs -L** might be helpful. I found that afterwards.

I updated this posting and added a warning re: usage of mke2fs directing people to either tune2fs (as you point out) or e2label.

If you do not feel this is obvious enough, please let me know and I will make further modifications.

---

### Post by mykalreborn on 2007-02-18
hi there! i'm having some troubles with the cds not mounting. [this]("http://www.ubuntuforums.org/showthread.php?t=363025") is a previous thread i wrote but since no one answered i asked you too.
i know it's not nice to ask in two places but i really want this problem solved. thank you!

---

### Post by Peter Cordes on 2007-07-07
I just discovered that the default fstab line for /cdrom isn't good when you have a dvd with a file >4GB on it, which requires UDF.  It should be iso9660,udf,  not udf,iso9660.  mount seems to try filesystems in reverse order, so putting it last makes it get tried first.  edit: mount only tries the last one.  reversing the order makes it fail to mount normal discs without UDF filesystems.  I'll file a bug report.

 I'm posting here because it took me a while to figure this out, but I don't know if it should be considered a bug, and if so what package is responsible for the default /etc/fstab anyway.

  You make such a disk by using the latest version of growisofs/genisoimage (in Gutsy testing, but not Feisty.)  The -allow-limited-size option makes an iso9660 filesystem with the file sizes truncated to 32 (or 31) bits, and a UDF filesystem with the proper sizes.
[http://geekpit.blogspot.com/2007/02/creating-large-2gb-dvd-backups-under.html](http://geekpit.blogspot.com/2007/02/creating-large-2gb-dvd-backups-under.html)
(This option is supported by the latest k3b, but k3b doesn't work in my gutsy chroot. :(  It can't see the filesystem and complains about file:/// URLs.  I don't know where all the sockets are for the kde IPC stuff...)

 Anyway, so if you write the image to a file (genisoimage -o), and mount -o loop, Linux will use the UDF filesystem structures because /proc/filesystems lists udf before iso9660.  This means the directory listing shows a 4.3GB file, in my case.  Burning to a disk and doing  mount /cdrom  makes Linux use the iso9660 (+Rock Ridge) filesystem, which means my directory listing shows a 300MB file.  With sudo mount -t udf ... I can mount the optical disc and see the 4.3GB file.  The only problem anywhere with this is that Ubuntu defaults to trying iso9660 first.

 BTW, it's only a problem if you have a disc with a bogus iso9660 filesystem, like genisoimage creates with -allow-limited-size.  Otherwise I don't know of a reason why you'd rather have UDF instead of RR.  genisoimage can't currently create images with no iso9660 filesystem, apparently because they don't trust their UDF code enough.

 BTW, I like to use these options for growisofs to master+burn large files all in one go:
growisofs -volid 'disc name' /dev/dvd -speed=6 \
-use-the-force-luke=notray -dvd-compat \
-use-the-force-luke=bufsize:32m \
-allow-limited-size -udf -rational-rock \
-allow-leading-dots -full-iso9660-filenames -relaxed-filenames -allow-lowercase \
-no-iso-translate -allow-multidot -omit-period -iso-level 3 \
-graft-points -f \
foo.vol000....par2 foo foo.vol128...par2

 (par2 is forward error correction data to make the data recoverable in case of scratches.  Not putting all the recovery files next to each other on disc should give you a better chance of not losing them all.  growisofs orders files in the image in the order they appear on the command line.)

 Usually I use k3b to set up and burn.  I even have some perl scripts that I can run on a k3b project file to create par2 files for the set of files that will be on the CD.  (I should publish those somewhere...  email me if you want them.)

---

### Post by sneax on 2007-08-23
Hi, i found this thread through search. I have a problem with fstab. I like this guide but it's not completely clear.

I have made an entry for my removable usb hard disk, it mounts ok (but I have to do mound manually) is there a way so that it would mount the hard disk as soon as I plug it in (hotplug)? It was like that when installing ubuntu but ntfs-config broke that so I'm trying to remake my fstab.

Also, I want to use an external usb stick and put it in fstab but when I do this command to list uuid and label it doesn't show my stick! So I don't know the label/uuid to put it in fstab!

WHen I list the 'id' then it shows the usb stick.

I can also mount the usb stick fine as root but i want it to automount (hotplug) and be usable as user.

Any ideas?

---

### Post by bodhi.zazen on 2007-08-23
> **sneax said:**
> Hi, i found this thread through search. I have a problem with fstab. I like this guide but it's not completely clear.

I have made an entry for my removable usb hard disk, it mounts ok (but I have to do mound manually) is there a way so that it would mount the hard disk as soon as I plug it in (hotplug)? It was like that when installing ubuntu but ntfs-config broke that so I'm trying to remake my fstab.

Also, I want to use an external usb stick and put it in fstab but when I do this command to list uuid and label it doesn't show my stick! So I don't know the label/uuid to put it in fstab!

WHen I list the 'id' then it shows the usb stick.

I can also mount the usb stick fine as root but i want it to automount (hotplug) and be usable as user.

Any ideas?

I assume you are using gnome? 

gnome auto mounts removable devices with gnome-volume-manager (which has always been hard form me to configure).

I find that gnome-volume-manager does NOT like it if you have an entry in fstab for flash/usb drivers, so I would remove the fstab entry, unmount the device, remove the device, delete the mount point in /media, and reboot. The re-try the device.

I do not user ntfs at all, I use FAT to windows share, so I do not know if it will work or not, but set a label on your ntfs partition and see if that help.

---

### Post by mssever on 2007-08-23
> **sneax said:**
> I have made an entry for my removable usb hard disk, it mounts ok (but I have to do mound manually) is there a way so that it would mount the hard disk as soon as I plug it in (hotplug)? It was like that when installing ubuntu but ntfs-config broke that so I'm trying to remake my fstab.
That used to work for me, but after recently upgrading my server to Feisty, my fstab-listed vfat USB drive no longer automounts, either. I noticed that Feisty renamed a bunch of things. My disks changed names from hd* to sd*, and my external drive's symlink in /dev/disk/by-id was renamed. This renaming broke my fstab, of course (I refuse to use UUIDs, since IMO there is no sane reason to use such unreadable identifiers when suitable alternatives exist).

I believe that pmount is responsible for automounting.
> I can also mount the usb stick fine as root but i want it to automount (hotplug) and be usable as user.You didn't say what format your USB stick was. For vfat, I use the following in the options column of fstab: ```
uid=1000,gid=1000,umask=077
```uid is your normal user's numeric user ID as listed in /etc/passwd. gid is for the group ID as listed in /etc/group. These control which user owns the files on disk. Finally, the umask sets up the permissions. Setting it to 000 would allow all users full control.

I have no issues with my ntfs-3g partition, so if that's the one you're having issues with, I don't know how to help you.

==================

By the way, if you still can't manage to get anything that's mentioned in fatab to be automounted, you might be able to hack the pmount source code to force pmount to use the options you want (which, last I checked were hard-coded), then re-compile pmount. This process, however, isn't for the faint of heart.

---

### Post by theDaveTheRave on 2007-08-25
Hello All.

Great info in here and I have read with some interest - I think it may have solved an issue I had with a partition not being accessible by my "almost never used" Vista partition (but then who would want to use it!?).

OK so my problems / solutions.

I think I had my share partition set to the wrong type untill I read this howto I mistakenly thought vfat and fat32 were "simlar" and readable by Windoze -  I have now changed my fstab to set it as NTFS-3g.

More alarmingly I am confused about how I set a label?? probably me just being dopey / sleepy / snoozey and waiting for snow white to show up and help out.... - maybe Bodhi is SnowWhite in disguite??:confused:

Anyway onto my main problem.

I have an issue with the UUID of my linux swap partition changing on a "Semi regular basis" - this means that each time I boot up I have to check that I have my swap in place - or else my system does a serious go-slow.

A serious go slow is tantamount to the old MS blue screen of death, so I use the power switch to turn off then reboot. this seems to bugger up the uuid of my swap partition, oddly enough it has no effect on any of the others!?

Personally I am not too bothered with the loss of the swap, it s a nuisance more than anything and it keeps me on my toes :o  and mens I have to remember some admin stuff (regular training is allways a good way to stay in shape I say), what gets me is what is causing it to happen??

what solutions can I use?? if I set a "label" will this work or does it map to the uuid??

Any thoughts would be greatly appreciated and more than welcome.

hope to hear from you soon.

Dave

---

### Post by mssever on 2007-08-25
> **theDaveTheRave said:**
> I have an issue with the UUID of my linux swap partition changing on a "Semi regular basis" - this means that each time I boot up I have to check that I have my swap in place - or else my system does a serious go-slow.

A serious go slow is tantamount to the old MS blue screen of death, so I use the power switch to turn off then reboot. this seems to bugger up the uuid of my swap partition, oddly enough it has no effect on any of the others!?
I don't really care for using UUIDs. If I were you, I'd list the actual device name in fstab (e.g., /dev/hda3). That should be a stable name (except that the upgrade from Edgy to Feisty inexplicably renames hd* disks to sd*.)

I really don't know what could be causing the swap partition to change UUIDs, though.

Before I increased the amount of swap I have, I experienced numerous serious slow downs, like you do. Normally with a lot of patience I could eventually log in via SSH and kill off the memory-hogging program. Of course, sometimes there's just nothing you can do but ```
<Alt><SysRq>E 
<Alt><SysRq>I
<Alt><SysRq>S
<Alt><SysRq>U
<Alt><SysRq>B
``` (which is a little nicer than using the power button)

---

### Post by theDaveTheRave on 2007-08-26
mssever

I had forgotten about the <alt><sysrq>.... trick, In fact I though that there was an even quicker one that that??

couple of silly questions though, 

which key is the <SysRq>, is it synonomous with the <ctrl> key or is it the <windows> button that is on keyboards these days?

query on the line of code I need for my fstab,

currently the offending part reads ( I have included the notes that I have commented out in the file as well, in case is helps!
> 
#Entry for /dev/sda6 - to hold a file for memory swap.
# seems that the UUID has changed?? how and why? now funcions as
#  today 24July07<< dev/sda6: UUID="6fa837b7-46f9-448e-b4b9-b72929cc76be" TYPE="swsuspend"  >>
#UUID=6fa837b7-46f9-448e-b4b9-b72929cc76be /dev/sda6 swap default 0 0
#required to change again as of 24 Aug 08
#UUID=a5a030a0-0955-46c4-9569-815f04a56635 /dev/sda6 swap default 0 0

#has changed again 25 Aug 08!
UUID=157abc4f-3652-4cb4-80c0-7819d56575ba /dev/sda6 swap default 0 0


do I simply put in the "link" FQN of the drive (in this instance it is < /mnt/swap> )

In fact I will try this and report back in a few minutes.

Dave

OK I had a play and it doesn't seem to have worked

the line in the fstab now reads
> 
/dev/sda6 /mnt/swap  swap default 0 0


I'll keep working on it, I'll reboot then come back in a few hours - just off to break the rest of our old/new kitchen!

Dave

ps. I've rebooted and it all seems to work, oh what joy.

Thanks Bodi, Thanks mssever

now I just need to try breaking it by using the power button!!! hmmm, maybee later....

---

### Post by mssever on 2007-08-26
> **theDaveTheRave said:**
> I had forgotten about the <alt><sysrq>.... trick, In fact I though that there was an even quicker one that that??

couple of silly questions though, 

which key is the <SysRq>, is it synonomous with the <ctrl> key or is it the <windows> button that is on keyboards these days?
SysRq is the same key as Print Screen. You can learn more from Wikipedia. Here's what the <Alt><SysRq> combos I use mean (there are others, as well):[LIST=1]
[*]E: Send SIGTERM to all processes. SIGTERM is a request to the program to exit normally and clean up after themselves. Be sure to allow enough time for programs to exit.
[*]I: Send SIGKILL to all processes. This signal causes the kernel to immediately kill the process without trying to be nice.
[*]S: Sync the disks. Be sure to allow sufficient time here, too.
[*]U: Remount the disks read only
[*]B: Reboot[/LIST]When it comes to your fstab, here's mine for reference: ```
/dev/hda6 none swap sw 0 0
```As far as I know, the second field--which is traditionally "none"--can be anything you want, since the swap partition is not mounted as a part of the filesystem and consequently has no mountpoint.

---

### Post by FrankVdb on 2007-09-30
I read somewhere that from Edgy upwards, one needs to replace the device name (e.g. /dev/sda1) with its UUID in the fstab. Under Feisty, this only applies to scsi or scsi-emulated drives!

When adding two drives (an IDE and an SATA drive) to one of my PC's, I noticed that the IDE drive I added (/dev/hdb1) went unnoticed when mentioned by its UUID in fstab! It took me a long time to find that out, messing around with countless option alternatives before it dawned to me that the UUID just did not work.

I'm actually using Linux Mint, which is Feisty plus multimedia support out of the box.

---

### Post by mssever on 2007-09-30
> **FrankVdb said:**
> I read somewhere that from Edgy upwards, one needs to replace the device name (e.g. /dev/sda1) with its UUID in the fstab. Under Feisty, this only applies to scsi or scsi-emulated drives!

When adding two drives (an IDE and an SATA drive) to one of my PC's, I noticed that the IDE drive I added (/dev/hdb1) went unnoticed when mentioned by its UUID in fstab! It took me a long time to find that out, messing around with countless option alternatives before it dawned to me that the UUID just did not work.

I'm actually using Linux Mint, which is Feisty plus multimedia support out of the box.

Actually, you don't have to use UUIDs. Edgydoes it that way, but I prefer other mechanisms: /dev/{h,s}d*, /dev/disks/by-*, etc.

Also, in Feisty, all disks are now sd*. There is no such thing anymore as /dev/hda1. I think that this was actually a kernel change, but I'm not positive about that.

---

### Post by duruttye on 2007-10-11
Hy guys!

This will be easy for you!!
My newly formatted drive has 1GB of swap, but it doesn't automount.
I just need a line to put in fstab, so it would automount for now on.

[HTML]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5005    40202631    5  Extended
/dev/sda5               1        2943    23639584+  83  Linux
/dev/sda6            2944        5005    16562983+  83  Linux

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   82  Linux swap / Solaris
/dev/sdb2             132        4998    39094177+  83  Linux
[/HTML]

I'm talking about /dev/sdb1.

Thank you!

---

### Post by bodhi.zazen on 2007-10-11
> **duruttye said:**
> Hy guys!

This will be easy for you!!
My newly formatted drive has 1GB of swap, but it doesn't automount.
I just need a line to put in fstab, so it would automount for now on.

I'm talking about /dev/sdb1.

Thank you!

> /dev/sdb1  none  swap  sw  0 0

:twisted:

---

### Post by ubunew12 on 2007-11-13
I'm running Ubuntu 7.04 and am fairly new to Linux.  I have a spare ext3 partition that I would like r/w access, but have only -ro access at the moment.  Any Ideas?

Fstab:
# /dev/sda5
UUID=a01a59b8-052e-4c3b-8832-d689d99dfc68 /media/sda5     ext3    rw,user,sync    0       2

Mount Command:
/dev/sda5 on /media/sda5 type ext3 (rw,noexec,nosuid,nodev,sync)

Also, I can't edit my fstab using sudo.  I have to use a livecd to edit my fstab.

---

### Post by mssever on 2007-11-13
> **ubunew12 said:**
> I'm running Ubuntu 7.04 and am fairly new to Linux.  I have a spare ext3 partition that I would like r/w access, but have only -ro access at the moment.  Any Ideas?

Fstab:
# /dev/sda5
UUID=a01a59b8-052e-4c3b-8832-d689d99dfc68 /media/sda5     ext3    rw,user,sync    0       2

Mount Command:
/dev/sda5 on /media/sda5 type ext3 (rw,noexec,nosuid,nodev,sync)
You have rw access. The mount command proves that. Check the permissions on your partition.
> Also, I can't edit my fstab using sudo.  I have to use a livecd to edit my fstab.
fstab should be owned by root:root and have 644 permissions. For example, here's the output of running ls -l /etc/fstab on my box: ```
-rw-r--r-- 1 root root 1.7K 2007-06-16 19:32 /etc/fstab
``` If your permissions are incorrect, then fixing them should fix your sudo problem. Otherwise, your problem is with sudo, not fstab. I don't know enough about fixing sudo to be able to help with that.

---

### Post by juje on 2007-11-14
I have a problem, deleted a partition but didn't unmounted it before...now every time i boot a get this error (# /dev/hdb2
UUID=24c6deb0-d9cd-42a9-974c-a401c4db74d2 /               ext3    defaults,errors=remount-ro 0       1)...and can't get into my graphical interface..
I know i have to comment the line with "noauto" to solve this (at least that's what i guess)...my problem is that i don't know how to comment that line thru the command line (i mean without thru the [email]root@desktop:$)...can[/email] anybody help me with it?
Thanks!

(sorry for my lousy english)

---

### Post by bodhi.zazen on 2007-11-14
> **juje said:**
> I have a problem, deleted a partition but didn't unmounted it before...now every time i boot a get this error (# /dev/hdb2
UUID=24c6deb0-d9cd-42a9-974c-a401c4db74d2 /               ext3    defaults,errors=remount-ro 0       1)...and can't get into my graphical interface..
I know i have to comment the line with "noauto" to solve this (at least that's what i guess)...my problem is that i don't know how to comment that line thru the command line (i mean without thru the [email]root@desktop:$)...can[/email] anybody help me with it?
Thanks!

(sorry for my lousy english)

Boot to a live CD if needed.

Open a terminal and mount your root partition, if needed.

for the rest of this post I will assume you have mounted you ubuntu root partition in /media/ubuntu ...

Now, again in a terminal,

```
sudo nano /media/ubuntu/etc/fstab
```

Since you deleted the partition, either comment out (add a # in the front of the line) or update your partition information.

Control -X to exit nano, type Y to save the changes.

Reboot to hard drive.

---

### Post by callouscrab on 2007-11-27
bodhi-zazen, thanks a lot for your awesome post! Mounted a VFAT volume with no trouble with the name fixed!

---

### Post by boob11 on 2007-11-30
tnx man

---

### Post by Sicundercover on 2007-12-09
Thanks for the post taught me alot.

However I have a situation. Im using KTorrent and fails to see my other mounted hardrives. Ive been told its probably because my hard drives are owned by root.

I used ntfs-3g to set up these hard drives because they are an existing partition in NTFS and Im not about to move 100Gigs of data over into my Ubuntu partition.

So anyway Ive read all the links for ntfs-3g and seems all the suggestion for gonfiguration is through the auto config. Grant it they mount but when I bring up the fstab it looks like this.

```
proc /proc proc defaults 0 0
# Entry for /dev/sdc2 :
UUID=8e8cf5f3-cedb-45dc-a98e-d71bf3575e33 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=f91cdd5d-1a8b-47fe-8574-3e1d97714f46 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdd1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc1 /media/BigBob ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Now Im pretty sure the defaults in owner root. But when I change the defaults to "noauto,rw,users" I loose the mount entirely and cant remount.

I know Im doing something wrong here just cant figure it out.

EDIT: Figure that about 5 minutes after writing this I went in and unmounted from root and the remounted in root and everything worked.

---

### Post by SnakeHips on 2008-03-02
Nice one Bodhi , great article 10/10

---

### Post by XStatic64 on 2008-04-02
Hi all,

I have ubuntu installed on a 120GB IDE HDD, with 2x 200GB Sata drives spare that i wish to mount.

I've gone ahead and created/formatted the partitions as you can see below:

```
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux
```

And I've tried to mount the drive(s) via:

```
mount -t ext3 /dev/sdb1 /mnt/files
```

Which returns:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I've also tried adding the entry in fstab but of course that doesn't work if the drives wont manually mount..

Any suggestions? :(

Please forgive me if I'm a moron, new to linux :).

---

### Post by bodhi.zazen on 2008-04-02
I do not see any obvious problem.

If you do not have an entry in fstab, you need to mount with sudo.

Make a mount point first.

Are your partitions formatted ?

```
sudo mkdir /mnt/files
sudo mount /dev/sdb1 /mnt/files
```

Also, right after attempting to mount, what is the output of this command :

```
dmesg | tail
```

---

### Post by tnl2k7 on 2008-04-19
Thanks for this post, I'm gonna bookmark it. I'm pretty sure it'll come in handy :D

---

### Post by A$h X on 2008-04-25
I want to change the default label for my mounts as they are being displayed as 10.7gb media, and I would like more meaningful names. Tried using tune2fs and e2label but I get a "Couldn't find valid filesystem superblock" error. 
Seeing as they are already mounted, could I just edit fstab and add some labels?

EDIT: Okay got the ext3 partition sorted, now ntfslabel can't access my windows partition as it 's already mounted. I sudo nautilus unmounted it, but then ntfslabel is denied access to it. Anyway to change an unmounted NTFS partition's label?

EDIT 2: No matter, managed to unmount it from terminal, and then used PYSDM to create a label for it. Job done.

---

### Post by Tharmas on 2008-04-28
> **A$h X said:**
> EDIT: Okay got the ext3 partition sorted, 
Could you tell me how you did it?
Because I have similar problems:
[http://ubuntuforums.org/showthread.php?t=771496](http://ubuntuforums.org/showthread.php?t=771496)

---

### Post by A$h X on 2008-04-28
Pretty sure it was simply:
> sudo e2label /dev/sdax label 

where sdax refers to your partition. and label is what you want to call it. If you run it without sudo then you get the previously mentioned error. You'll need a reboot to see the changes take effect, and I don't think you need to edit fstab as your partitions are already mounted.

If it's still giving you problems after entering the command and rebooting, then try installing PYSDM, a nice little app which allows you to to mount and label drives/partitions. It basically edits fstab on your behalf, and it seems to work for me.

Get it from synaptic, or type:

> sudo aptitude install pysdm

---

### Post by Tharmas on 2008-04-28
Thanks A$h X, but I guess my problem is different.
I just wanted my ext3 partition mounted as a unremovable drive (without the desktop icon).

---

### Post by duckgoesoink on 2008-04-28
Hi, this post is great, thanks a lot!

I'm a bit stuck on one thing though. I have a FAT32 partition I've managed to get automounting, however it's not letting me write data to it because the owner is root. This is the fstab entry for it:

> #/dev/sda2
UUID=4812-2CE3 /media/SHARED vfat auto,users,rw 0 0

What should I change to allow read/write access to anyone logged in? I'm on Hardy if that's of any relevance...

Thanks a bunch :-)

---

### Post by bodhi.zazen on 2008-04-28
> **duckgoesoink said:**
> Hi, this post is great, thanks a lot!

I'm a bit stuck on one thing though. I have a FAT32 partition I've managed to get automounting, however it's not letting me write data to it because the owner is root. This is the fstab entry for it:



What should I change to allow read/write access to anyone logged in? I'm on Hardy if that's of any relevance...

Thanks a bunch :-)

Try this entry :

```
                              #/dev/sda2
UUID=4812-2CE3  /media/SHARED  vfat  auto,users,uid=1000,gid=100,dmask=007,fmask=137  0 0
```

---

### Post by duckgoesoink on 2008-04-28
@bodhi.zazen - thanks a lot! That seems to have fixed it (after I rebooted). :-)

---

### Post by mssever on 2008-04-28
> **Tharmas said:**
> Thanks A$h X, but I guess my problem is different.
I just wanted my ext3 partition mounted as a unremovable drive (without the desktop icon).

Here's a wild guess: If you mount it somewhere other than /media or /mnt, does that make a difference?

If not, then you'll probably have to look into configuring Nautilus (which is the program that displays desktop icons). If you don't find anything through the normal methods, don't forget about gconf-editor. I don't know whether such configuration is possible.

---

### Post by duckgoesoink on 2008-04-28
> **bodhi.zazen said:**
> 
Try this entry :
```
#/dev/sda2
UUID=4812-2CE3  /media/SHARED  vfat  auto,users,uid=1000,gid=100,dmask=007,fmask=137  0 0
```

Actually, is it possible to give full permissions to all? (Owner, group, others.) I want to use a folder on this partition as the Apache DocumentRoot, but I can't yet because permission is denied (it's just a development environment not a live one).

---

### Post by bodhi.zazen on 2008-04-28
yes

```

UUID=4812-2CE3  /media/SHARED  vfat  auto,users,uid=1000,gid=100,umask=000  0 0
```

---

### Post by Tharmas on 2008-04-29
> **mssever said:**
> Here's a wild guess: If you mount it somewhere other than /media or /mnt, does that make a difference?

No, it doesn't. I guess it's a nautilus bug in Hardy. And yes, I've already tried all those options. In gconf-editor I can only  disable all volume icons in the desktop. But my internal HDD partition keeps mounting as removable, and that's what's wrong.
Thanks, anyway.

---

### Post by caspartroy on 2008-04-29
if you use the user option in /etc/fstab and want to override noexec, nosuid or nodev, you have to place the options in the right order:

exec,user does not work, it must be user,exec

---

### Post by mssever on 2008-04-30
> **caspartroy said:**
> if you use the user option in /etc/fstab and want to override noexec, nosuid or nodev, you have to place the options in the right order:

exec,user does not work, it must be user,exec

I never knew that. Any idea why that is?

---

### Post by Geezle on 2008-04-30
Hey folks, I'm having a problem mounting a freshly partitioned ext3 partition on a fresh 8.04 install.  

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a30a6512-da7c-42e9-be90-5939d61d90f4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=4522-FC6F  /media/sdb1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdc5
UUID=BDB4-6E5F  /media/sdc5     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdc6
UUID=829ff193-0787-4b80-abed-8b479d638eee /media/sdc6     ext3    defaults	0	2
# /dev/sda5
UUID=cd49cb69-19df-4690-bd9a-5e733a71efb4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
/dev/sdc6 is the drive in question.  It mounts and shows up but only Root has ownership so I only have read only access.  I'm sure it's just something simple but I don't know entirely know how fstab works.

Thanks

---

### Post by bodhi.zazen on 2008-04-30
> **Geezle said:**
> Hey folks, I'm having a problem mounting a freshly partitioned ext3 partition on a fresh 8.04 install.  

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a30a6512-da7c-42e9-be90-5939d61d90f4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=4522-FC6F  /media/sdb1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdc5
UUID=BDB4-6E5F  /media/sdc5     vfat    utf8,umask=007,gid=46 0       1
# /dev/sdc6
UUID=829ff193-0787-4b80-abed-8b479d638eee /media/sdc6     ext3    defaults    0    2
# /dev/sda5
UUID=cd49cb69-19df-4690-bd9a-5e733a71efb4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```/dev/sdc6 is the drive in question.  It mounts and shows up but only Root has ownership so I only have read only access.  I'm sure it's just something simple but I don't know entirely know how fstab works.

Thanks

Mount the partition and change the ownership and permissions.

```
sudo chown user.users /media/sdc6
sudo chmod 770 /media/sdc6
```

Where "user" (in chown user.users) = your log-in name (leave users as users).

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by santaslittlehelper on 2008-05-02
> Mount point.
This is where the partition is mounted or accessed within the "tree" (ie /mnt/hda1).
You can use any name you like.
In general

   1. /mnt Typically used for fixed hard drives HD/SCSI.
   2. /media Typically used for removable media (CD/DVD/USB/Zip).


Examples:

   1. /mnt/windows
   2. /mnt/data
   3. /media/usb


Hi

Just curious, has anyting changed when it comes to mount points?
Because as fare as I can tell ubuntu 8.04 mounts all and anything to /media?

---

### Post by mssever on 2008-05-03
> **santaslittlehelper said:**
> Just curious, has anyting changed when it comes to mount points?
Because as fare as I can tell ubuntu 8.04 mounts all and anything to /media?

Ubuntu tends to put everything in /media (and has done so at least since Dapper--6.06--when I started using it). I don't know the official reason for putting non-removable media in /media instead of /mnt, but I'd guess that it's more consistent to keep everything in one place. Plus, /mnt is kept free for manually mounting stuff when you want to do so. Of course, there's absolutely no reason why you can't change fstab to mount stuff wherever you want. The only requirement for a mount point is that it must exist and be an empty directory. Technically, it doesn't even have to be empty, but whatever's in the directory would be inaccessible while the partition was mounted there.

---

### Post by spaceboy909 on 2008-05-10
Hi guys.  Found a typo in your options list.

The **correct** line should read:
```

[LIST]
[*]**dev/nodev** - Interpret/Do not interpret character or block special devices on the file system.
[/LIST]

```Reference:  [http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

---

### Post by MilesTEG1 on 2008-05-19
Hello,
I use ubuntu 8.04, and I have two nfts partition witch are detected and functionnal with read/write support, but they are not mounted at boot.
I suppose that they use ntfs-3g to have write support.
To acces those partitions, I have to clic on the partition's name in the menu "Shortcut" near "System" menu. Then, the partition is mounted, and can be accessed through the desktop or the file navigator.

I want to mount automaticaly at boot one of these partition.
She mounted in /media/STOCKAGE

Here the fstab :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=6523d9ef-e07a-48bf-86cb-a8328e2fcaa5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=f59fedf2-decb-4622-be68-2e73e88a0f64 /home           ext3    relatime        0       2
# /dev/sda7
UUID=dc8a3772-1364-46b6-b19b-121bab521a27 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
```

And here the mtab :
```
/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda8 /home ext3 rw,relatime 0 0
none /proc/bus/usb usbfs rw,devgid=125,devmode=664 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/pierrick/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=pierrick 0 0
/dev/sda5 /media/STOCKAGE fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda1 /media/SYSTEME-HP fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
```

I don't know how to auto mount at boot or startup the STOCKAGE partition.
Can someone help me ?

Thanks 
Miles

---

### Post by mssever on 2008-05-19
> **MilesTEG1 said:**
> Hello,
I use ubuntu 8.04, and I have two nfts partition witch are detected and functionnal with read/write support, but they are not mounted at boot.
I suppose that they use ntfs-3g to have write support.
To acces those partitions, I have to clic on the partition's name in the menu "Shortcut" near "System" menu. Then, the partition is mounted, and can be accessed through the desktop or the file navigator.

I want to mount automaticaly at boot one of these partition.
She mounted in /media/STOCKAGE
You didn't specify what type of drive you're dealing with, but assuming it's a partition on an internal hard drive that isn't going to change partition numbers, the following fstab line should get you started. These are the options I use. You may need to change them to fit your situation (I'm guessing from your signature that your locale is French, not English).
```
/dev/sda5     /media/STOCKAGE     ntfs-3g     defaults,locale=en_US.UTF-8     0     1
```

---

### Post by willoconley on 2008-05-30
Thanks OP, finding disk ID's was exactly what I needed:)

---

### Post by thotmos on 2008-05-31
Hi there!
exactly what is the effect of turning the pass column in vfat partitions from 1 to 0 ? the last time I did it boot time improved but windows keeps running the check utility as if the machine was improperly shut down

---

### Post by paulo21 on 2008-08-23
Congratulations,

It's a very thorough tutorial. Very useful.

Thanks in advance.

---

### Post by Daverobb on 2008-08-29
I've read through this post a few times aznd still can't figure out why my usb drive doesn't show in xubuntu 7.10.  It reads it:  ```
lsusb
Bus 001 Device 002: ID 067b:2506 Prolific Technology, Inc. 
Bus 001 Device 001: ID 0000:0000 
``` but it says it doesn't have a valid partition table:  ```
sudo fdisk -l
[sudo] password for flor:

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe21ae21a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2037    16362171    7  HPFS/NTFS
/dev/hda2            2038        2407     2972025   83  Linux
/dev/hda3            2408        2432      200812+   5  Extended
/dev/hda5            2408        2432      200781   82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
```

any advice?

---

### Post by mssever on 2008-08-29
> **Daverobb said:**
> I've read through this post a few times aznd still can't figure out why my usb drive doesn't show in xubuntu 7.10.
It appears that your drive is corrupt. Does it work on another system?

---

### Post by Daverobb on 2008-08-29
I'll check on another computer.

---

### Post by bodhi.zazen on 2008-08-29
you can write a partition table with fdisk

sudo fdisk /dev/sda

just go ahead an manually add in the partitions, just use your post for start and end of partitions.

Alternately try testdisk.

---

### Post by Daverobb on 2008-08-29
okay but not sure what you mean about manually creating the partitions ... any guidance on that?

---

### Post by bodhi.zazen on 2008-08-29
[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

hit n for new partition. Use the numbers from the output you posted earlier :

> /dev/hda1   *           1        2037    16362171    7  HPFS/NTFS

so, first partition use start on 1 and end of 2037

add in all your partitions ...

When you are done, use w to write your partition table and exit.

Then re-boot (you should, IMO, reboot after writing your partition table).

If you make a mistake, do not worry about it, fdisk DOES NOT change (write or erase) data to the partitions. Just re-run fdisk and fix your mistake.

:twisted:

---

### Post by Daverobb on 2008-08-29
sorry for being such a dolt but that device is my existing 20 g hard drive - should I use the same numbers for the usb drive which is labelled as /sda?

a bit confused on that point

basically I just want the usb drive to dump images, videos and files for back up

---

### Post by bodhi.zazen on 2008-08-29
Oh, I mis read sda for hda, lol

If you had one large partition, make one large partition with fdisk.

If you have more then one partition, try testdisk 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Daverobb on 2008-08-29
okay -- here's where I'm at:

I used fdisk and created on big linux partition which was super easy -- after that though it still wasn't showing as a drive.  It's actually my girlfriend's drive and I'm trying to help her out with an old laptop so I brought it back to my desktop - it seems to recognize the new partition now but doesn't show up as a drive yet-

I'm thinking that now I have to mount it and have gone through the post but still am having problems. on this computer it shows up as /dev/sdd1

---

### Post by mssever on 2008-08-29
> **Daverobb said:**
> okay -- here's where I'm at:

I used fdisk and created on big linux partition which was super easy -- after that though it still wasn't showing as a drive.  It's actually my girlfriend's drive and I'm trying to help her out with an old laptop so I brought it back to my desktop - it seems to recognize the new partition now but doesn't show up as a drive yet-

I'm thinking that now I have to mount it and have gone through the post but still am having problems. on this computer it shows up as /dev/sdd1
Have you tried ```
sudo mount -t ntfs /dev/sdd1 /mnt
```

---

### Post by Daverobb on 2008-08-30
How about if it's a FAT drive?

This is the output:

```
sudo mount -t ntfs /dev/sdd1 /mnt
[sudo] password for dave: 
NTFS signature is missing.
Failed to mount '/dev/sdd1': Invalid argument
The device '/dev/sdd1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

---

### Post by mssever on 2008-08-30
> **Daverobb said:**
> How about if it's a FAT drive?
```
sudo mount -t vfat /dev/sdd1 /mnt
```

---

### Post by Daverobb on 2008-08-30
This is what results:


```
$ sudo mount -t vfat /dev/sdd1 /mnt
[sudo] password for dave: 
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by mssever on 2008-08-30
> **Daverobb said:**
> This is what results:


```
$ sudo mount -t vfat /dev/sdd1 /mnt
[sudo] password for dave: 
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
How is your drive formatted? FAT32? In that case (or in the case of NTFS), it appears to me that the filesystem itself is corrupted.

If it's some other type, replace the argument to the -t option with the proper one for your filesystem. See [FONT=Courier New]man mount[/FONT] for a (partial) list.

---

### Post by Daverobb on 2008-08-30
I assumed it was a FAT32 drive because I have another identical drive that shows up on my ubuntu as such.  Is there a command that I can use to check the file system used?

---

### Post by bodhi.zazen on 2008-08-30
Most likely it is a fat (vfat) partition.

go into fdisk again, delete the Linux partition, make a new fat partition.

then re-try.

If that fails, go into fdisk and again delete the partition.

Then use testdisk. testdisk is easy to use as well and is in the Ubuntu repositories.

---

### Post by Daverobb on 2008-08-30
I tried both but could not do as you suggested -- maybe I wasn't doing it correctly - here are the options in fdisk - deleteing the partition iseems easy enough but how do I create a FAT partition?
```

 sudo fdisk /dev/sdc1

The number of cylinders for this disk is set to 38912.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): 


```

---

### Post by bodhi.zazen on 2008-08-30
At the fdisk prompt, use l (that is a small "L") to list the types of partitions. Partition types are identified by numbers (I do not recall the number for FAT).

then use the t to change the type of partition. 82 = linux, change it to fat.

---

### Post by vitotol on 2008-09-03
thank you guys, really helpful thread... now my ntfs data partition is mounted automatically:)

---

### Post by gjhicks on 2008-09-06
Hi,

Have been trying to get a ext3 partition to mount (using Thunar, in Xubuntu 8.04), using your guide. Keep getting "permission denied".

Here is my saga:

From your guide (page 1) on mounting native linux file systems:

[I]fstab options: users,noauto

mount /mnt/ext3 mounts the partition.
Permissions:
Quote:
bodhi@Arch:~$mount /mnt/ext3/
bodhi@Arch:~$ls -l /mnt | grep ext3
drwxr-xr-x 3 bodhi users 1024 2006-11-07 17:26 ext3
Note: The user can mount the device and has rw permissions.
Note: Ownership remains bodhi:users[/I]

My settings, in /etc/fstab:

# Entry for /dev/sda5 :
/dev/sda5 /media/ubuntu8 ext3 users,noauto 0 0

Following a post of yours elsewhere: [http://ubuntuforums.org/archive/index.php/t-482796.html](http://ubuntuforums.org/archive/index.php/t-482796.html) June 26, 2007
I entered the following command (first one is just to show the partition was not mounted):

geoff@geoff-eeepc:~$ umount /media/ubuntu8
umount: /media/ubuntu8 is not mounted (according to mtab)

geoff@geoff-eeepc:~$ ls -l /media | grep ubuntu8
drwxr----- 2 root root  4096 2008-09-05 21:32 ubuntu8

geoff@geoff-eeepc:~$ mount /media/ubuntu8

geoff@geoff-eeepc:~$ ls -l /media | grep ubuntu8
drwxr-xr-x 21 root root  4096 2008-09-06 10:00 ubuntu8

So, the mount point still has 'root' ownership, not what should have happened, according to the mentioned post.

Appreciate your comments, thanks.

---

### Post by bodhi.zazen on 2008-09-06
with the partition mounted, just do a chown :

sudo chown goeff.goeff /media/ubuntu8

---

### Post by gjhicks on 2008-09-07
Hi,

Thanks for your quick reply.

This other partition is my ubuntu 8.04 installation.

If I "chown" the whole partition, will this change the permissions for when I boot to this partition - which I am guessing would not be a good thing?

Thanks,
Geoff

---

### Post by bodhi.zazen on 2008-09-07
Ah, yes, do not chown the entire partition.

What are the permissions of the rest of the directories (such as the user directories in /home) ?

Depending on what you are wanting, for simple access to files use sudo or gksu (gksu nautilus)

If you want a shared data partition, make a shared directory in ubuntu at say /mnt/data

then set ownershiip and permission on /mnt/data

then mount the ubuntu partition and use mount --bind

mount --bind  /media/ubuntu8/mnt/data /mnt/data

---

### Post by gjhicks on 2008-09-07
Hi,

Once again, thanks for the quick reply!

Perhaps I should clarify the problem:

- am currently using ubuntu 8, the nautilus file browser will mount partitions that do not appear in /etc/fstab, in such a way that files can be edited on such partitions.

- I wanted to try using xubuntu (as I have an eeepc and disk space is an issue), the included thunar file browser would not mount the partitions, whether they were in /etc/fstab or not - even with 'users' in the fstab entry.

- so, for xubuntu, I set up the /etc/fstab as follows:

/dev/sda2 /media/sda2 ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda5 /media/ubuntu8 ext3 defaults, 0 0

now the partitions are auto-mounted at boot and thunar can access them, with editing possible on these partitions.

So, I guess the problem is the way that nautilus mounts the partitions is not available either in xubuntu and/or by thunar.

Anyway, problem solved - though not how I would have liked.

Thanks very much for your assistance,

Geoff.

---

### Post by zaine_ridling on 2008-09-12
Fantastic guide, by the way. Some of it is far above my tiny dinosaur brain, but learning and experimenting is fun. Here's my deal.

(1) New HD (2nd drive used as a backup device);
(2) Got it mounted (I think); it shows up in Nautilus; *however*,
(3a) If I do a sudo mount -a command, it returns, "mount point /media/bak/ does not exist"; also,
(3b) I do not have permission to create folders, copy files to it, etc. 

Here's my current fstab file, which is ugly, I know:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74f8afb2-b1cc-4909-b598-1014eeef8229 /	ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e23ed4d9-d618-498d-820d-a3a0e513b5ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1
UUID=ecd8a66d-6d7a-404b-b63a-9fb76325ebfe /media/bak/	ext3	defaults	0	0

How do I gain full permission to the **sdb1** drive for everything?

---

### Post by mssever on 2008-09-12
> **zaine_ridling said:**
> 
(3a) If I do a sudo mount -a command, it returns, "mount point /media/bak/ does not exist"; also,
Mount points have to exist. So create /media/bak. If Nautilus show it, you shoud type "mount" to see where it's mounted. But Nautilus sometimes uses GVFS to mount stuff, and GVFS has its own ways of handling things. Creating your mount point will probably cure everything, though.

---

### Post by zaine_ridling on 2008-09-12
Thanks mssever. Not sure how to get to 'that' 2nd drive in the terminal. Here's what I typed:

> $ sudo mount /dev/sdb1 /media/bak
$ mount: mount point /media/bak does not exist


And yes, both show up in Nautilus. Which command/s should I use to check for the "real" mount point?

---

### Post by bodhi.zazen on 2008-09-12
You need to make the mount point :

```
sudo mkdir /media/bak
sudo mount /dev/sdb1 /media/bak
```

---

### Post by zaine_ridling on 2008-09-12
Thanks for the follow-up, bodhi. That didn't work either. I still get a "permission denied" whenever I try to copy or move anything to it.

[IMG]http://www.anova.org/target/media-bak.jpg[/IMG]

Perhaps my problem is that I formatted this as a primary drive rather than extended? I intended it to be a discrete drive. And when I'm at the command line, I don't know how to navigate to this 2nd drive labeled **1000.2 GB Media**.

---

### Post by bodhi.zazen on 2008-09-12
no, you are making progress. The drive mounted and now you simply have a permissions problem.

It appears as if the file system is ext3, so ...

```
chown user.user /media/bak
```

where "user" = you log in name

---

### Post by zaine_ridling on 2008-09-12
That worked! I'm grateful, **bodhi**! :KS

---

### Post by kgas on 2008-09-13
Thanks, Mr.Bodhi. This article helped me to understand the way the linux looks at the file system.

---

### Post by saravanan.2407 on 2008-09-13
Good guide.. Thanks

---

### Post by itismike on 2008-09-14
> **bodhi.zazen said:**
> 
First install ntfsprogs:```
sudo aptitude install ntfsporgs
```Or use Synaptic.


Just a little typo: "ntfsporgs" doesn't exist. ;-)
-mike

---

### Post by akelsall on 2008-10-15
Nice write-up! Clears up a few things for me. 

Hope you don't mind me pointing out a couple of typos in the document while I'm here:

For the ntfslabel command, the syntax is actually ntfslabel <device> <label>.

In the section on ntfsprogs, the command to install it has ntfsprogs spelled ntfsporgs

---

### Post by bodhi.zazen on 2008-10-15
> **itismike said:**
> Just a little typo: "ntfsporgs" doesn't exist. ;-)
-mike

> **akelsall said:**
> Nice write-up! Clears up a few things for me. 

Hope you don't mind me pointing out a couple of typos in the document while I'm here:

For the ntfslabel command, the syntax is actually ntfslabel <device> <label>.

In the section on ntfsprogs, the command to install it has ntfsprogs spelled ntfsporgs

Thank you both, should be fixed now :twisted:

---

### Post by kevdog on 2008-10-16
I wanted to thank you on the original post however there wasnt a link to do so.  Thanks for the great tutorial.

---

### Post by keenmonkey on 2008-10-21
Thanks for the really helpful thread.  I'm trying to mount NTFS partitions with ntfs-3g in fstab using labels instead of /dev/sdx, due to device IDs changing with USB keys.

LABEL=SEA_DISC	/mnt/seagate	ntfs-3g	rw,umask=0000,defaults	0 0

This does not work, though it works fine using the standard device path.  The man pages for ntfs-3g don't mention alternative device IDs.  I've searched all over but only find examples of people using /dev/sdx.

Am I missing something here?

[root@localhost by-uuid]# mount -L SEA_DISC /mnt/seagate ntfs-3g rw,umask=0000,defaults 0 0
mount: no such partition found
[root@localhost by-uuid]# ls /dev/disk/by-label -l
total 0
lrwxrwxrwx 1 root root 10 Oct 21 12:45 SEA_DISC -> ../../sde1

---

### Post by unutbu on 2008-10-21
According to the fstab man page:
```
       Instead  of  giving  the  device  explicitly, one may indicate the **(ext2 or xfs)**
       filesystem that is to be mounted by its UUID or volume label (cf.  e2label(8) or
       xfs_admin(8)),  writing  LABEL=<label>  or  UUID=<uuid>,  e.g.,  &#8216;LABEL=Boot&#8217; or
       &#8216;UUID=3e6be9de-8139-11d1-9106-a43f08d823a6&#8217;.
```
It appears using LABELs in fstab is only supported for ext2 or xfs filesystems, not ntfs.

---

### Post by bodhi.zazen on 2008-10-21
> **keenmonkey said:**
> Thanks for the really helpful thread.  I'm trying to mount NTFS partitions with ntfs-3g in fstab using labels instead of /dev/sdx, due to device IDs changing with USB keys.

LABEL=SEA_DISC    /mnt/seagate    ntfs-3g    rw,umask=0000,defaults    0 0

This does not work, though it works fine using the standard device path.  The man pages for ntfs-3g don't mention alternative device IDs.  I've searched all over but only find examples of people using /dev/sdx.

Am I missing something here?

[root@localhost by-uuid]# mount -L SEA_DISC /mnt/seagate ntfs-3g rw,umask=0000,defaults 0 0
mount: no such partition found
[root@localhost by-uuid]# ls /dev/disk/by-label -l
total 0
lrwxrwxrwx 1 root root 10 Oct 21 12:45 SEA_DISC -> ../../sde1

I think your mount command is a wee bit off. You need the -o flag before you specify options.

```
mount -L SEA_DISC /mnt/seagate -t ntfs-3g -o umask=000
```You do not need to specify "0 0" in the mount command, and you do not need to specify multiple options (rw may conflict with umask and no need to specify "defaults").

---

### Post by keenmonkey on 2008-10-23
@unutbu: this is apparently unsupported
@bodhi: thanks for the clarification; I had hastily cut and pasted to post.  Since you bring it up: does the 'rw' replace specifying the uid and gid values?  or does omitting rw and specifying umask simply assume full rw to start?

In any case, after searching high and low and finding nothing I came upon this genious, simple solution over at 
[http://forum.ntfs-3g.org/viewtopic.php?t=26&highlight=uuid](http://forum.ntfs-3g.org/viewtopic.php?t=26&highlight=uuid)

[B]I just ntfs-3g mount by label/uuid in the following way:
ntfs-3g /dev/by-label/My_Label /mnt/ntfs_disk
replace "by-label" with "by-uuid" to use that instead. [/B]

Regards, 
Mike

---

### Post by unutbu on 2008-10-23
keenmonkey, that's really cool! Thanks for the tip.

Edit: I found [http://forum.ntfs-3g.org/viewtopic.php?t=26&highlight=uuid](http://forum.ntfs-3g.org/viewtopic.php?t=26&highlight=uuid) a little confusing, so please correct me if I have this wrong:

To mount an NTFS partition by label, you can do this:
```

sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sdb1 My_Label
sudo mkdir /media/My_Label
```

Then edit /etc/fstab by adding a line like this:
```

/dev/disk/by-label/My_Label /media/My_Label ntfs defaults,uid=1000,gid=1000,dmask=027,fmask=137 0 2

```
Now unplug the unmounted NTFS partition and re-plug it.
This time, udev (or HAL?) will detect the Label of the NTFS partition and add an entry to /dev/disk/by-label.

You can now mount the NTFS partition with 
```

sudo mount /media/My_Label
```

---

### Post by ericesque on 2008-11-14
If mtab has all currently mounted partitions, can I:
auto-mount a partition
copy the corresponding record from mtab to fstab

so that the partition will auto-mount at boot from now on?

---

### Post by mssever on 2008-11-14
> **ericesque said:**
> If mtab has all currently mounted partitions, can I:
auto-mount a partition
copy the corresponding record from mtab to fstab

so that the partition will auto-mount at boot from now on?

That'll probably work. However, if you're dealing with a removable device, you'll need to find another way to identify it. mtab lists the actual device name, and sometimes those can change. With the device mounted, look in /dev/disk/by-* for ideas.

---

### Post by ericesque on 2008-11-14
thanks for the confirmation mssever.  It's an internal drive, so I think we're in the clear.  If I get ambitious I'll figure out the UUID and change it.

---

### Post by bodhi.zazen on 2008-11-14
> **ericesque said:**
> If mtab has all currently mounted partitions, can I:
auto-mount a partition
copy the corresponding record from mtab to fstab

so that the partition will auto-mount at boot from now on?

Yes but watch 2 things.

1. The last column in mtab is always "0". You may want this to be a "2".

2. You may need to add "auto" to the options if you wish to auto mount .

---

### Post by mcarni on 2008-11-16
Thanks for the post really really great,

I have a silly question I hope you can help me with.
I have added a line on fstab so to mount on boot an ext3 partition with my personal data.
It all works fine, but I would like not to have the "15.7 GB Media" icon on the desktop, a bit like /home, I have it on a separate partition but I don't have the icon...I have seen someone else having a similar problem but I didn't understand what the solution is.
Is it something I have to change with the settings on fstab, or is there anything you can suggest I should do with gconf?

Thanks in advance

M

---

### Post by bodhi.zazen on 2008-11-16
Personally I mount my partitions in /mnt

This keeps them off the desktop, regardless of window manager.

If you want them in your home, use a link

ln -s /mnt/dharma /home/user/dharma

---

### Post by mcarni on 2008-11-17
BRILLIANT

it worked perfectly, no more icon on the desktop, tonight i will study a bit how the links work and create one.

Thanks

m

---

### Post by Toci on 2008-11-25
Hello, perhaps somebody here can help me.

 My computer has a fat32 partition, I was worried about editing the fstab file directly so I used Pysdm and that seemed to cause more problems. 

 Now I keep editing Fstab basically every day and the changes keep reverting!, this is what Fstab says:
[B]
/dev/sda5    /media/sda5    vfat    user,auto,rw      0  0 [/B]


 This is what "mount" says:

**/dev/sda5 on /media/sda5 type vfat (rw,noexec,nosuid,nodev)**



 What am I doing wrong?, I want that partition to be fully useable by anyone and I can only edit or save files as root which does work randomly after editing Fstab and rebooting several times each day.

---

### Post by bodhi.zazen on 2008-11-25
> **Toci said:**
> Hello, perhaps somebody here can help me.

 My computer has a fat32 partition, I was worried about editing the fstab file directly so I used Pysdm and that seemed to cause more problems. 

 Now I keep editing Fstab basically every day and the changes keep reverting!, this is what Fstab says:
[B]
/dev/sda5    /media/sda5    vfat    user,auto,rw      0  0 [/B]


 This is what "mount" says:

**/dev/sda5 on /media/sda5 type vfat (rw,noexec,nosuid,nodev)**



 What am I doing wrong?, I want that partition to be fully useable by anyone and I can only edit or save files as root which does work randomly after editing Fstab and rebooting several times each day.

Ownership and permissions are set at the time of mount. In your case, in fstab, you need to add uid=1000,gid=100,umask=000 to your options.

Or if you do not wish every file to be marked as executable, use dmask and fmask

---

### Post by Toci on 2008-11-25
> **bodhi.zazen said:**
> Ownership and permissions are set at the time of mount. In your case, in fstab, you need to add uid=1000,gid=100,umask=000 to your options.

Or if you do not wish every file to be marked as executable, use dmask and fmask

 Thank you very much, that did exactly what I wanted (sorry I didn't get it directly from the how-to), and eventually I'll change it to the non-executable version.

---

### Post by bodhi.zazen on 2008-11-25
> **Toci said:**
> Thank you very much, that did exactly what I wanted (sorry I didn't get it directly from the how-to), and eventually I'll change it to the non-executable version.

Glad it worked, fstab is obtuse at first, but then it kind of clicks :)

---

### Post by theDaveTheRave on 2008-12-04
bodhi

Remember me, I still have the Acer 3680, now running hardy (intrepid was too painful!)

Anwyay.

I've got a new job, and I've been asked to set up the new team server.

so on went Hardy 64 bit server edition.
Samba shares and user logons are all sorted.

Just one last little project, that should be in your sphere as it involves mounting some extra disks in a certain place.


We have a number of 1 TB disks in the server (for backups and data) ~ once upon a time it was going to be a raid device but that went out the window when we realised that for the data we were generating we needed more disk space ;) (its all genetic stuff in case you are wondering, huge text files of gene sequences and the related DBases for mining).

My Set up so far.

I have a "guest" user logon that is shared over the local network to the rest of the team for holding their data (samba shares all working fine)

So what the team (or rather my boss) would like is the following.

We have 4 internal 1TB disks (soon to become 8 or more!, and others on the network).

We want to have these 4 disks (and then the other at a later date) that are installed in the machine to appear as though they live as subsections of the "guest" area - I would like make it appear as if they were in fact sub folders. 

I want to mount them directly into the samba share

here is some information from the system
> 
davem@BlackAdder:~$ mount
/dev/mapper/BlackAdder-root on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sde1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdd1 on /media/Disk IV type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/Disk II type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc1 on /media/Disk III type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/Disk I type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
davem@BlackAdder:~$


davem@BlackAdder:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 180 2008-12-04 17:57 .
drwxr-xr-x 6 root root 120 2008-12-04 17:56 ..
lrwxrwxrwx 1 root root  28 2008-12-04 17:57 0588aecb-553d-441d-aa7a-5a7a52069604 -> ../../mapper/BlackAdder-root
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 5E32A17932A156B5 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 8472B29172B28806 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-12-04 17:57 8cf5762b-955b-450d-9138-be78f55ca490 -> ../../sde1
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 AE82CEC082CE8BF1 -> ../../sdd1
lrwxrwxrwx 1 root root  30 2008-12-04 17:57 ca718353-2185-4a77-af14-c243e3eb1346 -> ../../mapper/BlackAdder-swap_1
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 FE8EBC8F8EBC41C7 -> ../../sdc1
davem@BlackAdder:~$ 


davem@BlackAdder:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 120 2008-12-04 17:56 .
drwxr-xr-x 6 root root 120 2008-12-04 17:56 ..
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 Disk\x20I -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 Disk\x20II -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 Disk\x20III -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-12-04 17:56 Disk\x20IV -> ../../sdd1
davem@BlackAdder:~$


the last section <by-label> is the most interesting, as I want to follow your advice and set the disks into the fstab by the label id.

Currently the fstab file had no details of these disks, but they mount automatically and appear in the mtab file with the following details

> 
/dev/sde1 /media/Disk\040IV fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb1 /media/Disk\040I fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdc1 /media/Disk\040II fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdd1 /media/Disk\040III fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0


I noticed that when I <unmount> the devices this detail dissapears.

So I unmount them then add the following lines into the fstab

> 
label=Disk I	/home/guest/TB1	auto	rw,user,noauto,exec,utf8 0	0
label=Disk II	/home/guest/TB2	auto	rw,user,noauto,exec,utf8 0	0
label=Disk III	/home/guest/TB3	auto	rw,user,noauto,exec,utf8 0	0
label=Disk IV	/home/guest/TB4	auto	rw,user,noauto,exec,utf8 0	0


when I attempt to re mount them however the mtab file still shows the same details?

I've also re-booted the system but it makes no different. I assume that there is another file that the system is looking at for the mount points of the disks, but I'm not sure where it lives, or what it is.

Unless of course this is working fine but I just don't see it doing so, when I sit in front of the pc I see 4 disks on the desktop. when I check the /home/guest/TB1 (or the others) folders the size of the folder is reported as being only 60GB in size (which would fit with the size of the /home.. partition.

If this doesn't work I guess I can simply add "links" to the files and then share the disks also, but that doesn't feel like an elegant solution, or is what I am trying to do not possible??

I've just checked something, when I check the disk properties the dialog says that the disk location is "on the desktop", and confirms the mount point a /media/sda1 etc...

I've also noticed something funny about the result of the ntfslabel command says the disk are called Disk I, Disk II etc...

However in the <by-label> stuff above is says they are called Disk\x20I, Disk\x20II etc...

Hmmm...

I'm going to change my fstab to see if it makes a difference....

Edit

YIPEEEE -  it works.... but I needed to mount manually??

now to get it to happen on a boot up....

---

### Post by bodhi.zazen on 2008-12-04
I assume the "guest" is a single account ?

In that case use mount --bind

mount --bind /media/HDI /home/guest/HDI

In fstab :

```
/media/HDI /home/guest/HDI none bind
```

The symbols have to do (in a nut shell) with the spaces you used in your labels (Linux does not like spaces).

May I also suggest, if this is a linux server, you use a linux native file system (ext3) ? Linux can not really maintain (defragment) ntfs partitions and permissions (with so many users) will be easier to manage on a linux native system.

---

### Post by theDaveTheRave on 2008-12-05
Bodhi,

Thanks for the advice, I've managed to get it working, and it boots up with everything the way I wanted it, it all looks "seemless" to everyone now (I hope!).

On partition types.

My personal preference would have been for either a Reiser or EXT3 partition, but my boss wanted it in NTFS (so as the windows machines can easily read them etc) and I don't know a good way to explain about issues of "defragmentation" and with "samba" shares it doesn't really matter anyway....

Also for "safety" reasons the disks are easily removable, so we could potentially just pull out a disk and chuck it into another machine, if it is in NTFS format then this is easy.

Are you aware of any good NTFS tools for linux that will regularly "defrag" the drive?

This could become an issue as the team produce lots of "video" data in their experiments (time lapse over 2 or 3 days with pics every 30 mins).

Thanks in advance for you advice.

David.

---

### Post by bodhi.zazen on 2008-12-05
No, that is the problems with using ntfs.

Ask your boss if you can "demo" a linux native file system (as you indicated, you do not need the file system to be ntfs to share via samba).

---

### Post by theDaveTheRave on 2008-12-06
Bodhi,

<I'm not sure if this is the place for this question? maybe we should start a new thread later on, your choice>

I don't know if this makes sense or not,

I know my boss won't be keen on the idea of using another filing system on the raid devices, but I do intend to maintain the MySQL database I am developing on the main HDD (for now and while it has space - I've been here for 4 months and the database is only really in "demo" mode and I've got 18 Gb of data - and only 3 tables, and no gene sequences yet!), and this is in EXT3 (i think?)

Anyway... my question is this.

When my colleagues are creating their data sets they start with about 60GB of video data, after analysis and stuff they normaly have it trimmed to about 20 or 30 

Check out our web page to see some of the stuff we are doing

[-http://nuclear.movement.googlepages.com]("http://nuclear.movement.googlepages.com")

and here are some sample movies

[-http://nuclear.movement.googlepages.com/research2]("http://nuclear.movement.googlepages.com/research2")

What I was thinking, is when they "finalise" their movies they could potentially store them on a "separate" partition of the drive.

Do logical partitions of drive space exist in a "physical" manner (ie when I split a drive into a partition is partition1 physically all together and partition2 physcialy after it??

if so could I do the following.

Have one of my TB disks read only, so as I can do the following:

Determine the size of a set of films for one experiment, then create a partition at the "front" of that disk of exactly the desired size to hold just that set of films. copy the films into this new partition (and potentially mount it as a separate read only sub folder).

When they have the next set of films ready do the same procedure, resizing the larger portion of the disk that was remaining to hold just the films from the next experiment?

and keep doing this, meaning that each experiment will exist on a separate partition that is READ ONLY and as it of a fixed size on the disk can't become "fragmented".

Are there any dangers to doing this? such as the continuall repartitioning of the remaining space etc, will it corrupt the data in the partition at the front??

Another question, and I'm begining to think this question should be living in the hardware thread?, in fact I'm going to create this same question in a new thread in that section. I'll link to it later on

Would doing this make access the "films" faster for my colleagues??

Would I then have an easier time of creating "archives" and backup procedures for the data??

Thanks in advance for your asstance.

David

Here is the link to where I have asked this question in the hardware section of the forums.

[http://ubuntuforums.org/newthread.php?do=newthread&f=332]("http://ubuntuforums.org/newthread.php?do=newthread&f=332")

Please direct any responses there, thankyou.

---

### Post by web250 on 2008-12-09
Ok, so I messed up my fstab pretty nicely.

I need to mount a partition to /music. But its mounting as root, so I can't copy my music backups onto it.

The fstab:
```
UUID=whatever /music  ext3    relatime        0       2
```

What does it need to be changed to in order to have it mount the way I'd like it to?

---

### Post by sisco311 on 2008-12-09
> **web250 said:**
> Ok, so I messed up my fstab pretty nicely.

I need to mount a partition to /music. But its mounting as root, so I can't copy my music backups onto it.

The fstab:
```
UUID=whatever /music  ext3    relatime        0       2
```

What does it need to be changed to in order to have it mount the way I'd like it to?

The fstab entry is ok.

You need to change the owner of the partition:
```
sudo chown -R *username:username* /music
```
replace *username* with your log in name(ex. web250:web250)

You can read more about file permissions here:
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by unutbu on 2008-12-09
```
sudo chown -R $USER:$USER /music
```
Henceforth you would be the owner of the /music directory, and be able read and write to it as you wish.

---

### Post by Vanva on 2008-12-13
thanks for the tutorial
but when I mount my external usb drive i get 
> Cannot create link /etc/mtab~
Perhaps there is a stale lock file? 
any hints?

---

### Post by mssever on 2008-12-13
> **Vanva said:**
> thanks for the tutorial
but when I mount my external usb drive i get 

any hints?
Please provide the details of how you're mounting (the relevant fstab lines and/or the mount command you're using). It seems weird that /etc/mtab~ even comes into play. In fact, check if /etc/mtab~ exists. If it does, delete it.

---

### Post by acreech on 2008-12-15
I am trying automount my music folder to see if it help rhytmbox with loading my music. I am not understanding this /etc/fstab file. 

The path that I would like to automount is /media/disk-1/Music

I want it to mount with read,write, delete permissions

Here is my /etc/fstab file, can you make any suggestions on how I do this. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=05502dba-1d9d-41b7-ad03-ecf67e855e16 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ac866e41-b85e-453d-9fb8-ef84095507ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

thanks for the help.

---

### Post by bodhi.zazen on 2008-12-15
Well, you mount a device to a location

/dev/sdxy /media/disk-1/music

so ... we need to know the device you are trying to mount.

---

### Post by acreech on 2008-12-15
> **bodhi.zazen said:**
> Well, you mount a device to a location

/dev/sdxy /media/disk-1/music

so ... we need to know the device you are trying to mount.

It took me a while to figure out how to get that information but this should be what you need


/dev/sdb1 /media/disk-1/Music

---

### Post by bodhi.zazen on 2008-12-15
> **acreech said:**
> It took me a while to figure out how to get that information but this should be what you need


/dev/sdb1 /media/disk-1/Music

Sweet. See, you are learning. Once it clicks it is easy ;)

Now what file system ? FAT or NTFS ?

Also you may wish to mount by UUID (as the /dev can change)

List your uuid by :

```
sudo blkid
```

The basic format will be :

> /dev/sdb1 /media/disk-1/Music auto <options> 0 0

If it is ntfs we will change "auto" to "ntfs-3g" and it it is a fat partition we will change to "vfat"

---

### Post by acreech on 2008-12-15
acreech@acreech-laptop:~/Music$ mount | grep /dev/sd
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

acreech@acreech-laptop:~$ sudo blkid
[sudo] password for acreech: 
/dev/sda1: UUID="05502dba-1d9d-41b7-ad03-ecf67e855e16" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ac866e41-b85e-453d-9fb8-ef84095507ed" 
/dev/sdb1: UUID="dd94fee6-0dbd-4ed0-b7b5-2e90d5708c31" SEC_TYPE="ext2" TYPE="ext3"

The type is ext3. I have a feeling that this will not do what I want in the end. I was just trying a suggestion. the problem I am attempting to fix is that I have all my music saved on a 2nd internal hard drive. That 2nd internal hard drive (/media/disk-1) automounts. Rhytmbox seems to forget where my music is kept and I have to go in and remind it every time I open the program. The suggestion is that if I automount the music folder then it will be there for Rhytmbox. 

I think that this won't work because the drive is already automounted, so shouldn't all the folders be automounted too?

thanks for the help

---

### Post by bodhi.zazen on 2008-12-16
Well, that is why I was asking what you were wanting to do.

You can mount a partition somewhere, for example, you are mounting /dev/sdb1 at /media/disk-1

But you want a directory to mount. This can be done with mount -bind.

mount -bind /directory-1 /directory_new

You can also make a link.

ln -s /media/disk-1/Music /home/user/Music

---

### Post by acreech on 2008-12-16
> **bodhi.zazen said:**
> You can also make a link.

ln -s /media/disk-1/Music /home/user/Music

I like this idea. If I understand you right I could link my /home/acreech/Music directory to my /media/disk-1/Music directory. 

Then the files will still be stored on the 2nd internal hard drive and I could just point Rhythmbox to /home/acreech/Music

I don't want to store that large of a folder on my main drive withthe operating system. 

I am assuming that this would be the code I would want to use in a terminal

```

ln -s /media/disk-1/Music /home/acreech/Music

```

---

### Post by bodhi.zazen on 2008-12-16
yep, that should do the trick.

---

### Post by acreech on 2008-12-16
> **bodhi.zazen said:**
> yep, that should do the trick.

I will give it a try. 

Thanks for the help. 

acreech

---

### Post by Ant68 on 2008-12-17
Hello,
I have a desktop computer with a DVD player RW (there is a second one but it is not used). It read ok (I have set up ubuntu from it)?

I would like to copy a .iso file from the computer to a DVD disc. but when I use CD/DVD creator it asked for:
Insert a rewritable or blank disc
Please put a disc, with at least 2.3 GiB free, into the drive. The following disc types are supported:
DVD+R DL, DVD-R, DVD-RW, DVD+R, DVD+RW

I insert a 4.7GB disc in the driver but I get nothing back. 


/etc/fstab: static file system information.
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=1948d24d-a767-490d-9d69-e513ef76c0ad / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=d19b101d-8f99-4e9f-b78a-07fab9bdd5c1 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


When I try to accces (click on) the content (e.g. music) from the same DVD player: Places > Audio CD (was CE+RW / DVD+-RW Drive). It shows:
Could not open location 'cdda://scd1/'
Failed to execute child process "sound-juicer" (No such file or directory)

When I try to accces the drive with the empty DVD in: Places > CE+RW / DVD+-RW Drive. I get nothing back.

It is like it does not pick up there is a DVD ready to write on in the drive... 

What should I do?

---

### Post by unutbu on 2008-12-17
This is a guess: Ubuntu sees that you have two CD/DVD drives and labels them /dev/scd0 and /dev/scd1. Your /etc/fstab links /dev/scd1 to /media/cdrom0. My guess is that /dev/scd0 should be linked to /media/cdrom0 instead. To test this guess:
```

gksu gedit /etc/fstab
```

Change scd1 to scd0.

Save and exit.

---

### Post by daqron on 2009-01-23
Much appreciated! And in general, the information that I've found here on this forum is incredibly helpful. 

In case it helps future visitors, here's the line I added to fstab to mount a FAT32 eSATA volume into an existing directory that I created called /media/disk-1:

```
# VFAT
# /dev/sda1
UUID=0FFD-432F /media/disk-1 vfat auto,users,utf8,umask=000 37 0 0
```

---

### Post by unutbu on 2009-01-23
Hello daqron, welcome to the forums!
Just a let you know: there is a minor error in your fstab entry.

Each fstab line (besides comments and empty lines) should have exactly six space-separated fields. Yours has seven:
```

UUID=0FFD-432F /media/disk-1 vfat auto,users,utf8,umask=000 37 0 0
```

Perhaps you meant
```

UUID=0FFD-432F /media/disk-1 vfat auto,users,utf8,umask=000 0 0

```
Note that with a non-zero value (37) in the fifth field, you are telling dump to backup this partition. 
By default, however, Ubuntu does not install dump, so I think this field is meaningless unless you install dump. 

Cheers,
unutbu

---

### Post by Oldhacker on 2009-01-27
I must being doing something wrong that is simple.:(
When attempting to use e2label to assign a label to a partition on my other internal HD, I receive the following error message:

e2label: Is a directory while trying to open /media/disk/newbackup
Couldn't find valid filesystem superblock.

There a number of partitions on my other HD, which is why I want to assign a label to this one before entering it in fstab to enable it for backups.

---

### Post by unutbu on 2009-01-27
I was able to reproduce your error message. It happens when you specify the partition by mount point instead of specifying the partition by its device name.

/media/disk/newbackup is the mount point.
The device name might be something like /dev/sdb1

So the command you are looking for is 
```

sudo e2label /dev/sdb1 LABEL
```

of course, make sure you change /dev/sdb1 to the correct device name.

To find the device name type
```

df
```

Look for the line which lists /media/disk/newbackup under the column entitled "Mounted on" and find the device name under the column entitled "Filesystem".

---

### Post by daqron on 2009-01-29
> **unutbu said:**
> Hello daqron, welcome to the forums!
Thank you sir and/or madam.

> **unutbu said:**
> Perhaps you meant
```

UUID=0FFD-432F /media/disk-1 vfat auto,users,utf8,umask=000 0 0

```
That is exactly what I meant. fstab auto-corrected by removing the superfluous "0" at the end, but I went ahead and changed the 37 to 0. Thanks for the clarification.

---

### Post by andrew.46 on 2009-02-24
Hi,

A quick question that may be a little off-topic:

I am running Intrepid Ibex as guest using VirtualBox on a slackware host. I have set up a shared folder on the host and placed the matching folder on my Intrepid desktop. I have loaded this from fstab as:

```
share /home/andrew/Desktop/share vboxsf uid=andrew,gid=users 0 0 
```

Two questions about this:

[LIST=1]
[*]Why did I have to use the uid / gid pair instead of 'user'?
[*]Is there a better way to load this shared folder in fstab?
[/LIST]

I apologise ahead for this question as I suck at fstab :-(.

Andrew

---

### Post by bodhi.zazen on 2009-02-24
> **andrew.46 said:**
> Hi,

A quick question that may be a little off-topic:

I am running Intrepid Ibex as guest using VirtualBox on a slackware host. I have set up a shared folder on the host and placed the matching folder on my Intrepid desktop. I have loaded this from fstab as:

```
share /home/andrew/Desktop/share vboxsf uid=andrew,gid=users 0 0 
```Two questions about this:

[LIST=1]
[*]Why did I have to use the uid / gid pair instead of 'user'?
[*]Is there a better way to load this shared folder in fstab?
[/LIST]

I apologise ahead for this question as I suck at fstab :-(.

Andrew

On topic : As far as I know this i show you add (VirtualBox) shares to fstab (your syntax looks good to me). In terms of the options , those are determined by the VirtualBox guest Additions similar to other file systems.

By that I mean if you look at man mount

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

You will see each file system has it's own options, and this must then be the behavior of vboxsf .

======

Off topic: I find it is just as easy to use a shared USB device or better a Samba server. Just as easy, IMO, to set up. You can also use other network protocols, such as ssh (scp), sshfs, ftp, https, NFS, etc.

---

### Post by andrew.46 on 2009-02-25
Hi bohdi.zazen,

Thanks for your reply:

> **bodhi.zazen said:**
> [...] each file system has it's own options, and this must then be the behavior of vboxsf .

Indeed I see now. The options for vboxsf are a little hidden from me, the docs have little to say. I shall pursue this with the virtualbox people. Fortunately the options I scavenged from google are working as I wish :-).

> Off topic: I find it is just as easy to use a shared USB device or better a Samba server. Just as easy, IMO, to set up. You can also use other network protocols, such as ssh (scp), sshfs, ftp, https, NFS, etc.

I will investigate, although my need to share between host and guest will probably be fairly minimal.

Thanks again,

Andrew

---

### Post by munishvit on 2009-03-12
I want to make a general entry (in order to specify configuration information) to mount any ISO image file, i wish; such that when I issue mount command, image gets mounted (as staged below) and I don't have to specify configuration information.
mount <image_path> <mountpoint>
I tried
LABEL='*' /media/IMAGE udf,iso9660 user,loop=/dev/loop0 0 0
but no avail.
Do wildcards works in fstab entries?
What is difference between the options 'loop' and 'loop=/dev/loop0'?
Thanks in advance..

---

### Post by munishvit on 2009-03-13
> **munishvit said:**
> I want to make a general entry (in order to specify configuration information) to mount any ISO image file, i wish; such that when I issue mount command, image gets mounted (as stated below) and I don't have to specify configuration information.
mount <image_path> <mountpoint>


Guys, is there any way around?

---

### Post by cheruvim on 2009-03-26
Great guide.. thanks for all the deatil. 

I'm just wondering if people have noticed a difference in the behavior of fstab with the new 8.10 distro I noticed that fstab which worked with 8.04 is now not behaving as expected. Both are EXT3 mounts via USB. Their entries are:

/dev/sdc1	/media/HT750HD	ext3	rw,nouser,auto,async,relatime	0	2
/dev/sdb1	/media/MAXTORPART	ext3	rw,nouser,auto,async,relatime	0	2


Was just wondering if anyone here noticed differences with the new distro?

---

### Post by unutbu on 2009-03-26
cheruvim, in what way is Ubuntu 8.10 not behaving as expected?

If you format a partition as ext3 using Ubuntu 8.10 (Intrepid) it will use the newer 256 byte inode size for its filesystem.

Whereas, if you format a partition as ext3 using Ubuntu 8.04 (Hardy) or earlier versions, it will use a 128 byte inode size for its filesystem.

If you ask Hardy to mount an ext3 filesystem which had been formatted under Intrepid, I think it may have problems reading the filesystem. However, Intrepid should have no problem reading a Hardy-formatted ext3 filesystem.

See 
[http://ubuntuforums.org/showpost.php?p=6167548&postcount=9](http://ubuntuforums.org/showpost.php?p=6167548&postcount=9)
[http://ubuntuforums.org/showthread.php?t=837728](http://ubuntuforums.org/showthread.php?t=837728)
for a little more info on the 256 byte inode size.

---

### Post by bikerman2299 on 2009-04-09
Thank you so much! You saved me from pulling out what little hair the military allows me to have. Anyhow, I do have some questions. Is there a way to make this auto mount? I tried NTFS Config, and it won't do anything for me. The last two line are the ones that I added to my fstab, then forced mounted the drive. As you can tell from the bellow lines and such. If I leave it plugged into my laptop, and reboot, will it auto mount? Thank you very much!! 

Another Learning Newbie...

# /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1cc335cc-8cfe-4ca7-b8e0-c39d79dec4e7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a8b6c509-438d-4a61-a8c3-79b07d2558f7 /dev/sda5 /mnt/ntfs-sys ntfs 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sdb1 :
UUID=AC5C04885C044F8E /media/usb ntfs 0 0 0

Notice the last two lines. I pulled up my UUID for the sdb1 and added it. this was the command for getting by UUID: ls /dev/disk/by-uuid -lah

Then, I made a mount point: mkdir /media/usb

after that, this command did the rest.

mount -t ntfs-3g /dev/sdb1 /media/usb -o force

Again, thanks for all of everyones help.

---

### Post by theDaveTheRave on 2009-05-01
Adding drives and powerfailures etc.

So if you hunt through this forum you will see a number of posts from your truly with issues of the UUID changing between re-boots (part way down the first page).

Another set in here (related to setup of a multi part RAID TeraByte drive) had some questions relating to that also.

So now, on this box with the multiple Terabye drives I've had an interesting anomaly that I will share with everyone (hopefully this will be of interest to you all).

So I had initially 4 TB drives mounted into a samba shared partition. All was working very nicely thanks very much.

I was then tasked with adding in 4 new drives. This really buggered around with the order of the original drives, so much so that they were no longer in the correct subdirectories of the shared drive.

So with some playing around with the fstab etc I have been able to get them into the directories I wanted.

So now the strange thing is, I seem to have lost control of one of these drives? it now just appears as a standard mount point as media/disk ?

Essentially this isn't a problem but I know I'm going to have to play around with the fstab file again.

The really strange thing is this.

The I only seem to have lost control of a single disk, but, this has altered entirely the mount points for the others. I'm guessing that as this disk was part of the original 4 (mounted via the RAID controller) that this may have some bearing on the situation.

For now I need to wait untill I am able to do a "full diagnostic" and understand what has happened. This won't be untill Monday.

I will report back my findings, and my solutions then.

However I suspect I will need to implement some sort of a solution so as we know when this happens again, as we use these disks for backups, and now the backup for thursday has ended up on the wrong disk (due to the mount point changing!)

I'm guessing that by getting the corrected output for the various things (ls /media/disk/la... or whatever!) I'll be abel to run a boot time check of the files.

I'm just not sure exactly for the best way of doing this at the moment. I'm thinking of using a shell script to do a file comparison or something... I'll let you all know how I sort this out, unless of course you have a solution for this sort of thing allready!

David

OK as promised, results of further investigations.

As I had suspected it seemed that everything was "moved around" for some reason? the question is why?

I can't say any more than that because when I arrived at the office this morning, the disks were back in the "normal" configuration, but we know that it was wrong as the backups went to the wrong place?

Edit 2

So I've just had a mail telling me that the server disks are in the wrong order!

So today, I organised for each mount point (ie HDD) to contain it's own specified file (giving it's ID). so the first disk has a file called disk1.txt, and the second disk2.txt.

This means we can quickly determine if the disks are in the correct place!

Today I shutdown the machine, and when my boss turned it back on again.... the mount points had all gone south (and some east and maybe even west as well!).

The only change on this terminal is the instalation (an non functioning of) vmware server. Does anyone know if this may be causing my problem?

I would guess that there is nothing wrong with the configuration file, otherwise it would never be correct. But why does it sometimes get it right and other times not?

I need some help to try to figure out why this is happening, and what logs I need to be looking at.

My initial guess is as that the part of the boot procedure that controls the mounting of disks from the fstab isn't happening at the right time (or not at all??)

thanks in advance for the help.

David

---

### Post by theDaveTheRave on 2009-05-06
Hello again all

I'm adding an extra post as this is also a small "bump" for some advice / help.

So if you read my above post you'll understand my strange situation.

My solution.

A little shell script that I will run as part of the boot sequence that will test for the location of the various control file names. If they are in the wrong place, it will send put a put a file into a designated place called either <goodConfig.txt> or <badConfig.txt>

But I had a thought, I would like to understand why the mounting via the fstab is failing on the odd occasion. Hence I need to collect some of the files and store them somewhere, this isn't a problem.

My questions in this instance are:

Are there any extra files other than the </etc/fstab> <etc/mtab> and getting info from the output of commands like <ls </dev/disk/by-uuid -la> that I should be looking at? will the info be in the log files somewhere, if so which one?

Am I able to reset the fstab after boot? if so what is the command, as it would be nice to find that the config is all wrong and then simple "re-mount" everything where it should be, then re-check that this has worked correctly, I'm sure it is in this post somewhere, but I can't find the command, please help on this one.

some quick observations / notes

the only things to have changed recently on this server are, the addition of vmware server (which doesn't currently work :confused: ), and the initiation of a "wake on lan" so as if the system is powered down it can be restarted, could either of these be causing the issue?

Is it possible that the fstab / mount of the drives is occuring before they are have all be "found" by the system?

disk label's and the /dev/sdXY mount points seem not to be consistent, at least when we see these errors in the location. I think the label stays the same, but if the disk labeled as "diskI" moves from /dev/sda1 to dev/sdb1 will this "break" the control in the fstab?

Also we now have 8 disks in the system, and this messed things up rather a lot also, the mount points in /dev/ all changed for the original 4.

Also one of the disks is "bad" I can probe it (via an lshw) and everything seems fine, but I can't get it to mount. It has the same fstab line as for the other disks, appart from a change in the /dev/sdXY detail obviously? could this disk be causing problems in the mount procedure? - i have commented out the line in fstab, but this disk never appears on the desktop. In fact it was the appearance of a disk on the desktop that allerted me to the original error condition, which I didn't fully investigate because everything looked to be in the correct place, but in fact it was not!

As allways your help is greatly appreciated.

David

---

### Post by l-x-l on 2009-05-15
> **Ant68 said:**
> 
When I try to accces (click on) the content (e.g. music) from the same DVD player: Places > Audio CD (was CE+RW / DVD+-RW Drive). It shows:
Could not open location 'cdda://scd1/'
Failed to execute child process "sound-juicer" (No such file or directory)


I get the same message when I'm on the desktop & press "Places" -> Audio Disk. Also, my CD/DVD burner only mounts when I open up Nautilus. Any suggestions?

---

### Post by crjackson on 2009-05-18
> **theDaveTheRave said:**
> Hello again all

I'm adding an extra post as this is also a small "bump" for some advice / help.

So if you read my above post you'll understand my strange situation.

My solution.

A little shell script that I will run as part of the boot sequence that will test for the location of the various control file names. If they are in the wrong place, it will send put a put a file into a designated place called either <goodConfig.txt> or <badConfig.txt>

But I had a thought, I would like to understand why the mounting via the fstab is failing on the odd occasion. Hence I need to collect some of the files and store them somewhere, this isn't a problem.

My questions in this instance are:

Are there any extra files other than the </etc/fstab> <etc/mtab> and getting info from the output of commands like <ls </dev/disk/by-uuid -la> that I should be looking at? will the info be in the log files somewhere, if so which one?

Am I able to reset the fstab after boot? if so what is the command, as it would be nice to find that the config is all wrong and then simple "re-mount" everything where it should be, then re-check that this has worked correctly, I'm sure it is in this post somewhere, but I can't find the command, please help on this one.

some quick observations / notes

the only things to have changed recently on this server are, the addition of vmware server (which doesn't currently work :confused: ), and the initiation of a "wake on lan" so as if the system is powered down it can be restarted, could either of these be causing the issue?

Is it possible that the fstab / mount of the drives is occuring before they are have all be "found" by the system?

disk label's and the /dev/sdXY mount points seem not to be consistent, at least when we see these errors in the location. I think the label stays the same, but if the disk labeled as "diskI" moves from /dev/sda1 to dev/sdb1 will this "break" the control in the fstab?

Also we now have 8 disks in the system, and this messed things up rather a lot also, the mount points in /dev/ all changed for the original 4.

Also one of the disks is "bad" I can probe it (via an lshw) and everything seems fine, but I can't get it to mount. It has the same fstab line as for the other disks, appart from a change in the /dev/sdXY detail obviously? could this disk be causing problems in the mount procedure? - i have commented out the line in fstab, but this disk never appears on the desktop. In fact it was the appearance of a disk on the desktop that allerted me to the original error condition, which I didn't fully investigate because everything looked to be in the correct place, but in fact it was not!

As allways your help is greatly appreciated.

David

My post may be totally useless to you but I'll throw some more words into the mix.

A couple of versions back (Ubuntu versions that is), I had some problems with my drives and their switching to unexpected positions in the food chain. The cure for me was to remove all the UUID info and leave it as /dev/sda1 - /dev/sdb1 - etc...

This solved my problems but it was a non-raid setup. This probably didn't help you much but it's all I've got... :neutral:

---

### Post by theDaveTheRave on 2009-05-19
> **crjackson said:**
> My post may be totally useless to you but I'll throw some more words into the mix.

A couple of versions back (Ubuntu versions that is), I had some problems with my drives and their switching to unexpected positions in the food chain. The cure for me was to remove all the UUID info and leave it as /dev/sda1 - /dev/sdb1 - etc...

This solved my problems but it was a non-raid setup. This probably didn't help you much but it's all I've got... :neutral:

crjacson

that does sort of clear up a few potential ideas I had had on this. However due to the nature of the placement of the drives using /dev/sd1 - etc won't work anymore!

The reason for this is the following...

Initially the 1TB drives were hooked into the system via a "raid device", although the disks were not acting as a "raid" type system, (ie a 4 disk raid with redundancy) as we need all the disk space we can get for out data backups!

So when we added the next 4 disks, it seemed to play around with the locations of the original disks (ie /dev/sda1 now became /dev/sda5), the reason for this (please correct me if I am wrong) is I think something to do with the "internal" disks being loaded into the system prior to those connected via the "raid device".

all I know of this is that the order of the disks in mtab resulted in the original 4 disks being at the end of the file, which I thought of as very strange.

sorry I can't me more clear on this at this time as I am "away" from the office and I can't ssh to ascertain the actual setup due to the firewall, and I can't convince the IT team to open a port for me (or that should probably read 'each time I suggest I should talk to the IT team I don't get much of a response' - so now I've all but given up asking!).

Anyway... I digress....

The biggest curiosity for me is how sometimes the boot procedure get the setup correct and other not? I suspect that the disks are being mounted prior to the reading of the fstab or something?

In the little shell script I created I finish with remounting all the disk with a call to
```

mount -a

```
(or whatever it is to re-read the fstab file)
which seems to put things right? Which is why I think that maybe the fstab isn't being read at the right time?

Is this even possible? and what can I do to "prove" this theory?

thanks again for all the help.

David

---

### Post by theDaveTheRave on 2009-07-07
Hello again all.

so after further investigation, and not being able to solve my problem after multiple re-boots I started trawling my way though the /var/log/messages

I have been having messages relating to one of the HDD and there being a "DRDY" and I/O error at given sectors (just by the number of lines I thing this may in fact be all the sectors!)

I'm not sure but it may be related to this but on launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920").

So if you are having a similar problem check the message log and then filter by device name.

for me the device causing the grief was sdh.

then if that gives you anything check the other logs for similar info at the same time.

hope that helps anyone.

David

---

### Post by egalvan on 2009-07-11
> **bodhi.zazen said:**
> 

**Understanding fstab**

Sorry this is such a long post.

[SIZE=2]**I added much of this information toif you also have an account at launchpad the Ubuntu wiki.**

update May 2009 : [/SIZE][tbuss]("http://ubuntuforums.org/member.php?u=256430") kindly converted this post to a pdf which is available [here]("http://www.scribd.com/doc/15124069/Understandingfstab%5BSIZE=2").[B]
 The pdf can be downloaded [COLOR="Red"]if you log into scribd[/COLOR].
 You may use openid to log in, so should be easy [COLOR="Red"]if you also have an account at launchpad[/COLOR].
[/B]

[IMG]http://www.laiwa.com/cache/3/1/531045_70x70.gif[/IMG] [COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen[/COLOR]

So what can one do if one does not have, and does not want, an account at Launchpad?

---

### Post by bodhi.zazen on 2009-07-13
I posted a direct link on my server, here :

[http://bodhizazen.net/Tutorials/Understandingfstab.pdf](http://bodhizazen.net/Tutorials/Understandingfstab.pdf)

---

### Post by theDaveTheRave on 2009-07-22
Hello again everyone.

I've got another question about fstab and mounting new drives into given locations.

this time related to virtual machines, but I'm not sure where to ask the question so I'm asking it here in the first instance.

My VM is an ubuntu install on a vista terminal.

I created the disk as what I thought was "automatically expandable" but it won't expand!

Not a problem I thought, I can simply add an extra HDD and mount it to wherever I need it.... not so.

When you mount a disk in a given location (eg /home/username ) any files or directories in that partition will dissappear! not helpfull!

I am sure that they must be a way of making Ubuntu think that the new disk is actually part of the original disk? - essentially extending the disk size at a given mount point?

I wonder if this is possible by using symbolic links?

I have read about using the LVM (logical volume manager) but from what I have read it seems as though LVM will only work if you are installed from the < alternate install cd >. Other suggestions are too boot from the live CD, but this is a VM so I'm not sure that this will work!

any advice will be eagerly asborbed.

Thanks in advance.

David

---

### Post by unutbu on 2009-07-22
Hi theDaveTheRave.
You are correct: if you have files in /home/username on /dev/sdaX and then mount /dev/sdbY at /home/username, then the original files "disappear" (until you umount /dev/sdbY). The "mount" command does not merge directories together. 

Here are a few workarounds/options:
[list]
[*] You could move everything in /home/username to a partition on the extra HDD. Then mount the partition at /home/username.
[*] You could organize /home/username into a manageable number of directories: Docs, Music, Pictures, etc.  Move those directories to a partition on the extra HDD. Then make symlinks from the partition back to /home/username:

If the partition on the extra HDD is mounted at /mnt/data, then do, for example,
```

ln -s /mnt/data/Docs /home/username/Docs
```

Note that the original directory /home/username/Docs must exist when your run the "ln -s" command, because the "ln -s" command creates a symlink called /home/username/Docs which points at /mnt/data/Docs. If there is a directory called /home/username/Docs then the "ln -s" command will fail to create the symlink.

This option is particularly good if you are using more than one OS and want your data to be shared. Note that although data can be easily shared, configuration files may not be shareable. For example, if you have google earth version 4 on on OS and google earth version 5 on another, you may not be able to use the same ~/.googleearth configuration directory for both. Version 4's ~/.googleearth may cause Version 5 to crash...

[*] I think if you really really wanted to, there is a way to setup /home/username on an LVM, but unless you plan on adding additional hard drives every month and want the additional space to be added seemlessly, I think setting up LVM would be more trouble than its worth. (On the other hand, it could just be my inexperience with LVM which is biasing my opinion!)
[/list]

---

### Post by theDaveTheRave on 2009-07-22
Unutbu

I had thought it may be possible with the use of symlinks.

However (and just because I want to add in a little bit of confusion) I will explain why I need to do this.

I've been asked to create a virtual machine to hold a "dumbed down" version of a mysql database.

The tables for mysql live in /var/lib/mysql

I created the VM and it had the "normal" setup with apparently "automatically expandable HDD" which when I tried to load on the mysql tables didn't expand and promptly ran out of space!

So now I need to add in a new Virtual HDD, which seems fine but I can't add a "logical Volume" into the system, and I can't use fstab to mount it either.

this leads me nicely to my question.

If I create a symbolic link (as you are suggesting) will that enable the mysql daemon to follow it automatically when adding in new tables / adding data to existing ones?

Otherwise I had allready hit on the idea of simply copying everything over to the new disk, then de-import / re-import the relevant disks etc... which sounds far too complicated for my work colleagues!

Ah well... only another 2 days and its the weekend....

David

---

### Post by unutbu on 2009-07-22
theDaveTheRave, I don't have any experience with virtual machines. 
I hope someone with knowledge about this will chime in, especially if I'm making some mistake.

Until then I'm going to ignore that you're dealing with a VM and assume things work the same as a normal installation.
> 
If I create a symbolic link (as you are suggesting) will that enable the mysql daemon to follow it automatically when adding in new tables / adding data to existing ones?

I have some experience with this: I have /var/lib/mysql/MY_DB symlinked to /data/var/lib/mysql/MY_DB. /data is the mount point of a separate partition.

Starting with Intrepid (or maybe Hardy), Ubuntu installs mysql-server with an apparmor profile called /etc/apparmor.d/usr.sbin.mysqld. This apparmor profile restricts the directories into which mysql can read/write. In order to enable mysqld to read /data/var/lib/mysql/MY_DB you must edit /etc/apparmor.d/usr.sbin.mysqld by adding lines like this:
```

  /data/var/lib/mysql/ r,
  /data/var/lib/mysql/** rwk,
```

After you make the symlink you should be able to access the database on the separate partition... Well, my notes are a little cloudy here. You may also need to restart the mysqld server and maybe also apparmor:
```

sudo /etc/init.d/apparmor restart
sudo /etc/init.d/mysql restart

```
Hope this helps.

---

### Post by bodhi.zazen on 2009-07-22
I would look to see why your disk is full. Fix that problem (need a bigger disk ?).

Your example can not be solved with fstab or links. IMO easiest to make a new disk. Boot your Vm with a "live CD" and copy your /old_disk to the /new_disk

You might also want to look at LVM.

---

### Post by notbitmonk on 2009-07-25
I think that I read this somewhere in this post but it will be good if it is included in the HowTo.  

When making a new dir with sudo, if the directory is made in /mnt it will not show up in "Places" or in the dialogs that look for a folder.  The drive will be mounted but you will have to manually navigate to /mnt/SOMEFOLDER to access said drive.  I for one like to have the drive listed in "Places" with the drive icon.  To do that, a new dir should be mounted in /media.  I just spent a couple of hours trying to figure this out thinking that the drive was not mounting.  To follow your example:
```
sudo mkdir /media/SOMEFOLDER
```
instead of
```
sudo mkdir /mnt/SOMEFOLDER
```
The only benefit (that I can see) is that it will list the location as a drive in "Places", it will place an icon in the desktop  and it will be accessible in the dialogs that ask the user where to save or what folder/file to open instead of the user having to navigate to /mnt/SOMEFOLDER.

---

### Post by ticket on 2009-08-18
Hopefully this thread is still active and someone can help.

Here's my puzzle:

I have a second hard disc sdb1 I use to store data and programs on.
To create it, I formatted it to ext3 and did:

```
sudo chown -R myName:myName /media/Data
sudo chmod -R 755 /media/Data
```

I could happily read & write the disc, but I found I could not run any programs stored on it.  So I added 'exec' to the fstab entry like this:


```
/dev/sdb1                                  /media/Data    ext3         defaults,users,exec                 0  0  
```

But the disc still does not execute programs, even after a reboot.  What is wrong?

---

### Post by ticket on 2009-08-18
Actually, adding exec does seem to have done the trick.  I mistakenly tried running a .exe file as a test - which just threw up the archive manager, so I assumed things weren't working.  

Other binaries now do run - as do bash scripts (which gave a confusing error message before).

Now is that fstab line secure, in the sense that is 'nosuid' enabled?

I don't want a rogue binary have access to things I can't normally access.

I thought 'defaults' enabled 'suid'.

What's the recommended way here?

---

### Post by bodhi.zazen on 2009-08-18
I advise you use the options noexec and nosuid

If you want a binary, keep it in ~/bin rather then the data partition.

---

### Post by ticket on 2009-08-21
Ah, thanks Bohdi. 

I am just developing some stand-alone programs to perform various scientific calculations. I like to keep the code and binaries together on my 'data' disc, as the binaries are of no use to anyone except me. 

If I create a ~/bin folder, does Ubuntu include it in the search path? What is the order of search? I think it is something like:

/usr/local/bin first, followed by
/usr/bin, 
then ... ?

On a separate hard disc is my system disc, which holds a minimal /home directory, just to provide configuration info to the system programs like mplayer, etc.  So I think this is a fairly clean separation between the things I do and what Ubuntu does.  

I backup my system disc now and then using 'dd' to another spare disc.  I use rsync to back up my data disc, to a different spare disc. 

I suppose I could move my development environment back to /home, but I rather like the way things are set up now. Except for this 'suid' business.

---

### Post by bodhi.zazen on 2009-08-21
That all sounds reasonable to me, nothing wrong with it.

To see your path :

```
echo $PATH
```

If you have a ~/bin it should be the last item on the list.

---

### Post by rahimveron on 2009-09-04
Great Guide.

---

### Post by molavec on 2009-09-09
Good Work, very comprehensible guide.

---

### Post by bodhi.zazen on 2009-10-20
Added a link to Pysdm, a gui tool to configure fstab.

pysdm is in the Ubuntu repositories and I have been taking it for a spin on [Zenix](zenix-os.net). In general it works quite well.

---

### Post by dcstar on 2009-10-21
> **bodhi.zazen said:**
> Added a link to Pysdm, a gui tool to configure fstab.

pysdm is in the Ubuntu repositories and I have been taking it for a spin on [Zenix](zenix-os.net). In general it works quite well.

Hurrah! - I have been recommending pysdm for years to people that just want a nice, simple GUI to manage their disks.

Why packages like this - which are basically essential for any user who does not want to be forced to learn arcane things like working with the fstab file just to connect one of their disks permanently - are not installed by default is really baffling.

---

### Post by disophisis on 2009-10-21
Thank you for this!  as a beginner to linux, I look to the internet for assistance a lot for learning, and this is a very well done how-to. :)

---

### Post by paul uk on 2009-10-22
> **bodhi.zazen said:**
> 
...........

[SIZE=2]**Fstab Examples**[/SIZE]
# NFS
Server:/share  /media/nfs  nfs  rsize=8192 and wsize=8192,noexec,nosuid
# "Server" = Samba server (by IP or name if you have an entry for the server in your hosts file
# "share" = name of the shared directory



Great post, helped this noob immensely.

The above section from the original post contains a typo. The line should instead read

Server:/share  /media/nfs  nfs  rsize=8192,wsize=8192,noexec,nosuid


Thanks

---

### Post by danklaf777 on 2009-10-22
Great ! Thank you. This will surely help

---

### Post by bodhi.zazen on 2009-10-22
> **paul uk said:**
> Great post, helped this noob immensely.

The above section from the original post contains a typo. The line should instead read

Server:/share  /media/nfs  nfs  rsize=8192,wsize=8192,noexec,nosuid


Thanks

#-o

Thank you, I fixed that one.

---

### Post by northwestuntu on 2010-01-01
> **dcstar said:**
> Hurrah! - I have been recommending pysdm for years to people that just want a nice, simple GUI to manage their disks.

Why packages like this - which are basically essential for any user who does not want to be forced to learn arcane things like working with the fstab file just to connect one of their disks permanently - are not installed by default is really baffling.

wasn't there a option in 9.04 to automount? seems like they took it out? yes this is a basic function that should be added to ubuntu.

---

### Post by Keeper1 on 2010-01-01
> **dcstar said:**
> Hurrah! - I have been recommending pysdm for years to people that just want a nice, simple GUI to manage their disks.

Why packages like this - which are basically essential for any user who does not want to be forced to learn arcane things like working with the fstab file just to connect one of their disks permanently - are not installed by default is really baffling.

ubuntu 8.04 (Hardy)
Kernel Linux 2.6.24-19 generic
Gnome 2.22.3
Memory 1010.0
Processor Mobile AMD Sempron(tm) 2600+

My problem...
this is my /etc/fstab output


# /dev/sda1
UUID=3546be51-1749-4833-9cac-c709b79de06c  /            ext3  relatime,errors=remount-ro  0  1
# /dev/sda5
UUID=f4c05fe8-a243-4387-9081-3763e7f0915b  none         swap  sw                          0  0
/dev/scd0       /media/cdrom0   udf,iso9660 rw, user,noauto,exec,utf8        0  0
/dev/fd0        /media/floppy0  auto        rw, user,noauto,exec,utf8        0  0
/dev/sdb3                                  /media/sdb3  ext3  rw,user                    0  0
/dev/sdb1                                  /media/sdb1  ext3  rw,user                    0  0
/dev/sdb2                                  /media/sdb2  ext3  rw,user                    0  0
/dev/sdg1                                  /media/sdg1  ext3  rw,user                    0  0
/dev/sdh1                                  /media/sdh1  ext3  rw,user                    0  0
/dev/sdh5                                  /media/sdh5  ext3  rw,user                    0  0
/dev/sdh6                                  /media/sdh6  swap  defaults                    0  0

When I use pysdm all of the rw,user is defined as default. 
I have jacked around with pysdm and /etc/fstab till I'm about to come uncorked.
Yes, I have RTFM till I can't bear it any more, and followed the 'step-by-step' on-line how-tos, but to no avail.

Either way I can read and write to one, but not both usb drives.


Am I just really dumb, or just missing something???

Any help will be much appreciated.

---

### Post by mozartripper on 2010-06-08
here i made a easy tutorial to auto mount a hard drive with fstab [http://ubuntuforums.org/showthread.php?t=1500031](http://ubuntuforums.org/showthread.php?t=1500031)

---

### Post by SoFl W on 2010-06-26
> **bodhi.zazen said:**
> [SIZE=2]update May 2009 : [/SIZE][tbuss]("http://ubuntuforums.org/member.php?u=256430")  kindly converted this post to a pdf which is available [here]("http://www.scribd.com/doc/15124069/Understandingfstab%5BSIZE=2"). The pdf can be downloaded if you log into  scribd. You may use openid to log in, so should be easy if you also have  an account at launchpad.

*The document 'Understanding-fstab' has been deleted           *

---

### Post by bodhi.zazen on 2010-06-26
> **SoFl W said:**
> *The document 'Understanding-fstab' has been deleted           *

I put a copy here :

[http://bodhizazen.net/Tutorials/Understandingfstab.pdf](http://bodhizazen.net/Tutorials/Understandingfstab.pdf)

The above link is working, let me know if you have a problem with it.

---

### Post by cj.surrusco on 2010-07-25
Thanks, bodhi.zazen! This is a great tutorial, and I use it whenever I need some info on the fstab.

---

### Post by AlexanderDGreat on 2010-09-05
Hi bodhi.zazen! Thank you for your tutorial, you're a great asset to the community. More power to you!

**Do You Think My Problem Is My FSTAB? I've come to your thread for help!**


**********


**_Rsync DOESN'T Preserve File Owner & Permission - Using Automounted NTFS backup drive _**

Also located here: [http://ubuntuforums.org/showthread.php?t=1568402]("http://ubuntuforums.org/showthread.php?t=1568402")


Hi, this is my machine:

ext4:
1x 80gb - /boot, /swap, /(root) - sda
1x 80gb - /home - sdb

ntfs:
1x 250gb - /backups - sdc

1. First of all, I automount sdc /backups via /etc/fstab like this:

```
/dev/disk/by-label/backups /media/backups ntfs defaults,uid=1000 0 2
```

2. Second I use a rsync to backup my /boot/ /(root) and /home

For example:

```
rsync --delete -avz /boot /media/backups/boot/
```

When I check **sdc** (my ntfs backup drive), all files in there are 777, whereas it should be 755, and sometimes the owner is me, whereas it should be ROOT.

As an experiment, I backed up my files NOT in **sdc** (my ntfs backup drive), but in my /home folder instead, **_RESULT: every thing is OK, and it preserved file owner & permission!_**

Is there something I'm missing here? Is there something I don't understand?

Please help because I'm learning to BACKUP my system. Thanks for reading, bodhi. :)

---

### Post by bodhi.zazen on 2010-09-05
> **AlexanderDGreat said:**
> Hi bodhi.zazen! Thank you for your tutorial, you're a great asset to the community. More power to you!

**Do You Think My Problem Is My FSTAB? I've come to your thread for help!**


**********


**_Rsync DOESN'T Preserve File Owner & Permission - Using Automounted NTFS backup drive _**

Also located here: [http://ubuntuforums.org/showthread.php?t=1568402](http://ubuntuforums.org/showthread.php?t=1568402)


Hi, this is my machine:

ext4:
1x 80gb - /boot, /swap, /(root) - sda
1x 80gb - /home - sdb

ntfs:
1x 250gb - /backups - sdc

1. First of all, I automount sdc /backups via /etc/fstab like this:

```
/dev/disk/by-label/backups /media/backups ntfs defaults,uid=1000 0 2
```2. Second I use a rsync to backup my /boot/ /(root) and /home

For example:

```
rsync --delete -avz /boot /media/backups/boot/
```When I check **sdc** (my ntfs backup drive), all files in there are 777, whereas it should be 755, and sometimes the owner is me, whereas it should be ROOT.

As an experiment, I backed up my files NOT in **sdc** (my ntfs backup drive), but in my /home folder instead, **_RESULT: every thing is OK, and it preserved file owner & permission!_**

Is there something I'm missing here? Is there something I don't understand?

Please help because I'm learning to BACKUP my system. Thanks for reading, bodhi. :)

The problem is ntfs does not understand linux permissions, Make a linux partition to back up to.

---

### Post by AlexanderDGreat on 2010-09-05
Thank you bodhi!

Now, I understand, it's a shame I didn't read your whole tutorial, maybe you already NOTED it there?

Can you make a tutorial for lazy bums? Just kidding. :)

---

### Post by bodhi.zazen on 2010-09-05
> **AlexanderDGreat said:**
> Thank you bodhi!

Now, I understand, it's a shame I didn't read your whole tutorial, maybe you already NOTED it there?

Can you make a tutorial for lazy bums? Just kidding. :)

No worries. permissions on ntfs or fat partitions are a FAQ and often misunderstood.

---

### Post by karmila on 2010-09-19
Hi, it's a really great guide.

After read this guide i tried to automount my ntfs partition "Programs" with adding this line in /etc/fstab:

```
LABEL=Programs /media/Programs ntfs-3g defaults 0 0                      
```But then each time i deleted a file from that partition it saids "Can't move file to trash, file will be deleted immediately". Then I tried to change the options to be like this:

```
LABEL=Programs /media/Programs ntfs rw,suid,dev,exec,auto,async 0 0                      
```But resulting the same issue.

How should i write the options so deleted file won't deleted immediately but move first to the trash, makes me can restore the files when i change my mind.

Thanks

---

### Post by Morbius1 on 2010-12-22
> **karmila said:**
> Hi, it's a really great guide.

After read this guide i tried to automount my ntfs partition "Programs" with adding this line in /etc/fstab:

```
LABEL=Programs /media/Programs ntfs-3g defaults 0 0                      
```But then each time i deleted a file from that partition it saids "Can't move file to trash, file will be deleted immediately". Then I tried to change the options to be like this:

```
LABEL=Programs /media/Programs ntfs rw,suid,dev,exec,auto,async 0 0                      
```But resulting the same issue.

How should i write the options so deleted file won't deleted immediately but move first to the trash, makes me can restore the files when i change my mind.

Thanks
I got redirected here from another thread and noticed your question from 3 months ago. With the HowTo's author's indulgence I'll take a crack at it if you're still interested.
>  LABEL=Programs /media/Programs ntfs-3g defaults 0 0That will produce a mount point that's owned by root with permissions for everyone to read and write. You have permissions to delete but since it's owned by root it can't go into your trash it can only go into root's. One way around this is to take possession of the mount point by adding uid=1000 to your fstab line:
>  LABEL=Programs /media/Programs ntfs-3g defaults,uid=1000 0 0

---

### Post by graabein on 2010-12-24
It helped me, Morbius1. Merry Christmas and happy holidays!

---

### Post by Aleksandar_B on 2011-03-24
Hi, great tutorial, but I'v come across a problem.

I'v added an entry in fstab for mounting:

```
LABEL=test /media/test ext2 rw,suid,dev,exec,noauto,nouser,async    0       0
```

, and it mounts fine, but in the options I'v set it not to mount at boot-up (noauto) but it does.

I'm only trying this out to learn how it works, so any help would be appreciated :)

---

### Post by karmila on 2011-04-26
> **Morbius1 said:**
> I got redirected here from another thread and noticed your question from 3 months ago. With the HowTo's author's indulgence I'll take a crack at it if you're still interested.
That will produce a mount point that's owned by root with permissions for everyone to read and write. You have permissions to delete but since it's owned by root it can't go into your trash it can only go into root's. One way around this is to take possession of the mount point by adding uid=1000 to your fstab line:

Hi Morbius1

It's 4 months after your post but it solved my old problem, thanks :KS

---

### Post by jstoone on 2011-09-05
This saved me a lot of time, and gave me a whole lot of new and great knowledge about permissions and basic filesystems! 
I :bmark'ed and emailed to 4 of my friends, because we're all trying to learn something all the time, and it's great when people like you take your time to write this great guide in such a detail!

Tanks a lot!
- jstoone

---

### Post by abdulmudabir on 2011-12-03
the only not-so-useful thing in this post being the apology at the start :)

---

### Post by rng on 2012-01-01
Great tutorial and tips. 

I am using a windoz program thru wine and it needs to access the inserted CDROM. Wine has fixed the CDROM folder to be /cdrom, but ubuntu mounts the inserted CD in a subfolder in /media created according to the label of the CD. How can I setup that the inserted CD is always mounted on /cdrom automatically? 

Also, would I need to unmount the CD before removing it and inserting another one?  Could the other CD get automatically remounted to /cdrom folder?

---

### Post by cy3a on 2012-02-08
by mistacke i changed name of device from /dev/sdXY to /dev/something. how can i change it back so i don't have any more problems with booting?

---

### Post by Cincinnatux on 2012-04-16
[QUOTE=bodhi.zazen;1653968][IMG]http://www.faculty.de.gcsu.edu/%7Edvess/ids/fap/Rox/14.jpg[/IMG]

[SIZE=6]**Understanding fstab**[/SIZE]


[SIZE=2][COLOR=blue]If you simply want a gui tool to manage your partitions (/etc/fstab) try [Pysdm]("http://pysdm.sourceforge.net/").[/COLOR][/SIZE]

[IMG]http://pysdm.sourceforge.net/screenshots/fstab_04.png[/IMG]

[indent][indent]pysdm Screen Shot[/indent][/indent]

LOVE this post, though I'd add a caveat regarding Pysdm:  it ain't idiot-proof.  I thought I'd take the 'easy' way out in automounting partitions by using Pysdm.  Fail.  Why?  I presumed it would be intuitively obvious, so I didn't RTFM.  Borked my system, had to use my install CD to get to command line so I could manually edit fstab and fix my GUI mistakes.  I think I'll stick to command line configuration of stuff like this for a while.  :)

---

### Post by Morbius1 on 2012-04-16
pySDM has a number of issues. For example it has no idea what a UUID is and even has mounting options missing. It also lures the user to do goofy things - it's only a click away.

---

### Post by bodhi.zazen on 2012-04-16
If you change system settings without understanding what you are doing you are asking for problems, regardless of operating system or if it is from a graphical tool or the command line >:)

---

### Post by YannBuntu on 2012-05-27
Hello

For information:

[https://bugs.launchpad.net/ubuntu/+source/disk-manager/+bug/1002281](https://bugs.launchpad.net/ubuntu/+source/disk-manager/+bug/1002281)

[https://bugs.launchpad.net/ubuntu/+source/pysdm/+bug/1005279](https://bugs.launchpad.net/ubuntu/+source/pysdm/+bug/1005279)

---

### Post by Phileksa on 2012-09-10
This guide looks very comprehensive.  I think, bigawds, I can almost understand what it's all about.  But I do have one problem.

The drive I'm trying to mount is on a computer who's IP address changes from time to time.  Putting a random IP address in the fstab file doesn't seem like a permanent fix because of this.

Not too long ago, I had my partner join me in a multiplayer game.  This required the computer's IP address, too.  At that time, it was 192.168.2.4.  But today, I check the IP address on it, and it's 192.168.2.2.  As you can tell, if I set up the permanent fstab mount on the same day I was playing that game, it would be broken today, since the IP address is changed.

However, the network and computer names are both the same.

I tried using smb://networkname/computername/sharedfolder but the computer refused to mount that.  It claims it is unable to resolve this or something.  But somehow, when I click on "Network" the shared drive shows up just fine.

My purpose for mounting this drive is to make it look like a local drive for Ubuntu so I can use a scheduled rsync script to backup files off it.  This is a beautiful, elegant, and even very simple solution, and one I had on the other computer before it died.  It was simple, worked all the time, and seemed pretty fail-safe.  But it took me months of searching to find out how it was done, and I failed to record the necessary files on the backups.

The solutions that require creating a virtual linux machine on the Windows computer are untenable at best, at least in part because the Windows computer exists primarily for computer games.  Having a virtual machine, even an idle one, takes up far too many resources and creates far too many problems for gaming.

Please keep in mind I've also done what is apparently impossible on this Windows machine:  I've disabled the Explorer shell.  I understand this is impossible because whenever I report that "minimize to system tray" does not help me (because there is no system tray when there's no Explorer shell) most people tell me this is not possible.

So yes, this machine is optimized for performance, and is carefully operated to keep as many of it's now relatively meager resources free, and a virtual linux machine on it is not only undesirable, but strikes me as a bit of over-engineering and over-thinking the problem.

How do I get this machine's shared drive - a drive that contains mostly media files that I regularly add to - to mount as a local drive, in spite of it's changing IP address, so I barely have to touch the Ubuntu computer to get it to create two backups of the media drive every day using rsync?

---

### Post by bodhi.zazen on 2012-09-10
Assign the machine a static ip. This can be done in your router on in configuration of your OS.

---

