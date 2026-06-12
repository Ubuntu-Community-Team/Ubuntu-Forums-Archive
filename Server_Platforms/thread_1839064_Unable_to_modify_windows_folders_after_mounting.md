---
title: "Unable to modify windows folders after mounting"
date: 2011-09-04
forum: Server Platforms
---

### Post by digital_alchemy on 2011-09-04
Systems:     
Ubuntu 11.04
                  Windows 7 Ultimate

I'm able to get my windows share folder mounted in Ubuntu, but I can't seem to modify files/folders.  I've tried creating new folders/files, but I always get the following errors: 
[SIZE=2][COLOR=DarkRed]
[/COLOR][/SIZE][INDENT][COLOR=Blue][SIZE=2][COLOR=Red]digital_alchemy@Bacon:/media/htpc$ touch test
touch: cannot touch `test': Permission denied
digital_alchemy@Bacon:/media/htpc$

digital_alchemy@Bacon:/media/htpc$ sudo mkdir test
mkdir: cannot create directory `test': Permission denied
digital_alchemy@Bacon:/media/htpc$[/COLOR][/SIZE]
[/COLOR][/INDENT]I've tried the following entries in the /etc/fstab file:

```
//htpc/media_library  /media/htpc  cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//htpc/media_library  /media/htpc  cifs credential=/home/digital_alchemy/.smbcredentials,iochart=utf8,file_mode=0777,dir_mode=0777  0  0
//htpc/media_library  /media/htpc  cifs credential=/home/digital_alchemy/.smbcredentials,dmask=777,fmask=777 0 0
//htpc/media_library  /media/htpc  cifs uid=digital_alchemy,credential=/home/digital_alchemy/.smbcredentials,dmask=777,fmask=777 0 0

```They all work fine for mounting the filesystem.... only problem is that I still can't modify or create files in the share.

I've checked folder permissions on the windows share and have both local users and authenticated users set to full control on the windows share.

Any advice is greatly appreciated.

---

### Post by volkswagner on 2011-09-05
I believe this is an issue with Windows permissions (NTFS special permissions).

This issue I have encountered on Server2008.  For example the /Users/Public folder has a "Sticky bit" set for READ ONLY.  

Log on locally or via RDP to your windows box.  Right Click the folder you are sharing and choose properties... is the checkbox selected for "Read Only"?  

I have been unsuccessful in changing this attribute.  I found [this article]("http://support.microsoft.com/kb/326549") which does not apply to Server2008, but may work For Win7. 

If the above is true, It may be easiest to just manually create a folder on the Windows box and share it.  Then move all your data to that folder once you confirm that it is not forced as read only.

---

