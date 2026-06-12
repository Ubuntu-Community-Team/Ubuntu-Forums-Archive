---
title: "samba: privileged user and guests access differently to the same share"
date: 2015-04-20
forum: Server Platforms
---

### Post by ubh on 2015-04-20
[SIZE=3][FONT=book antiqua]Hi all there!
I need help to a simple Samba server setup.
So... I have an USB extHDD connected to the server PC: the whole HDD has only one partition in NTFS.

I'd like to set-up environment like that:
me and _only me_ can full-access [FONT=courier new]rwx[/FONT] to whole [FONT=courier new]/dev/sdb1[/FONT]/[FONT=courier new]MyName[/FONT] mounted via Samba (path for that in Samba is [FONT=courier new]/mnt/world/MyName[/FONT]);
then
everyonone else is: VLC, bro, dad, mom, friends, PCs, tablets, smartphones and HTPC (Kodi).

The Samba server behaviour would be that _everyone else can only navigate/read **some** shares_ that are within [FONT=book antiqua][FONT=courier new]/mnt/world/MyName: [/FONT][/FONT][FONT=courier new]/mnt/world/MyName/video, /mnt/world/MyName/music, /mnt/world/MyName/ISOs, [FONT=book antiqua][FONT=courier new]/mnt/world/MyName/images[/FONT][/FONT][/FONT].

The filesystem schema on USB extHDD (NTFS):
[/FONT][/SIZE]
[LIST=1]
[*][SIZE=3][FONT=courier new]/dev/sdb1
[/FONT][/SIZE] 
[*][SIZE=3][FONT=courier new]/dev/sdb1/MyName
[/FONT][/SIZE] 
[*][SIZE=3][FONT=book antiqua][FONT=courier new]/dev/sdb1/MyName/{video,docs,ISOs,audio,music,projects,images}[/FONT]
[/FONT][/SIZE] 
[/LIST]
[SIZE=3][FONT=book antiqua]
My hope of structure with Samba:[/FONT][/SIZE]
[LIST]
[*][SIZE=3][FONT=book antiqua][FONT=courier new]/dev/sdb1/MyName = /mnt/world/MyName[/FONT] <--- Only I have full [FONT=courier new]rwx[/FONT] to this and recursively to all its subdirectories
[/FONT][/SIZE] 
[/LIST]
[SIZE=3][FONT=book antiqua]
within, then:[/FONT][/SIZE]
[LIST]
[*][SIZE=3][FONT=book antiqua]Everyone else (guest access, _no password/login_) will read and navigate these folders: [FONT=courier new]/dev/sdb1/MyName/{video,music[FONT=book antiqua][FONT=courier new],ISOs[/FONT][/FONT],images} = /mnt/world/MyName/{[FONT=book antiqua][FONT=courier new]video,music[FONT=book antiqua][FONT=courier new],ISOs[/FONT][/FONT],images[/FONT][/FONT]}[/FONT][/FONT].[/SIZE] 
[/LIST]
[SIZE=3]
[FONT=book antiqua]The important option for me is to have no password/login to access easily with - for example -  VLC without giving login credentials into its settings.

Thanks you all guys!!![/FONT][/SIZE]

---

### Post by electronico_nc on 2015-04-21
Hi,
What is the Samba version ?
```
samba -V
```
I tjhink you have to mount the NTFS drive with "permissions" option in /etc/fstab ( [http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition](http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition) )
>  For NTFS partitions, use the permissions option in fstab.
  First unmount the ntfs partition.
  Then edit /etc/fstab

sudo -e /etc/fstab 

  Identify your partition UUID with blkid
sudo blkid 

  And add or edit a line for the ntfs partition
      # change the "UUID" to your partition UUID
    UUID=12102C02102CEB83 /media/windows ntfs-3g auto,users,permissions 0 0

  Make a mount point (if needed)
  sudo mkdir /media/windows

  Now mount the partition
  mount /media/windows

  The options I gave you, auto, will automatically mount the partition when you boot and users allows users to mount and umount .
  You can then use chown and chmod on the ntfs partition.
Once permissions are OK on filesystem, you add users/groups to Samba using something like:```
sudo smbpasswd -a username
```Then setup your smb.conf file. 
This might help (depends on your Samba version) : [https://wiki.archlinux.org/index.php/Samba/Tips_and_tricks#Share_files_without_a_username_and_password](https://wiki.archlinux.org/index.php/Samba/Tips_and_tricks#Share_files_without_a_username_and_password)

Nicolas

---

