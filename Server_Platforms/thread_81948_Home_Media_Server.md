---
title: "Home Media Server"
date: 2005-10-25
forum: Server Platforms
---

### Post by Dagr on 2005-10-25
I apologize, I read the sticky that said "don't ask for How-Tos; there's a forum for it" but I didn't see a how-to forum specific to servers.

What I want to do is have my old computer athlon 1.4, 768MB, 160GB hdd, running as a couple of servers. I'm going to be hosting a small personal website, and I'm trying to get squid running properly. But my latest issue is setting this thing up as network storage.

I want to have my computers connect automatically to a common media folder (Photo/Video/Audio) and a personal documents folder, so that a minimum of data is kept on each terminal system.

I thought I could do this with samba, but I'm having problems. It doesn't reconnect at logon, and it doesn't treat the filesystem as local. I've heard of NFS before, but have zero experience with it. What do I do? My terminals run windowsXP and linux (gentoo and ubuntu). 

Help?

Thanks guys.

 ~ Dagr

---

### Post by Tomy on 2005-10-25
[quote=Dagr]...
I want to have my computers connect automatically to a common media folder (Photo/Video/Audio) and a personal documents folder, so that a minimum of data is kept on each terminal system.

I thought I could do this with samba, but I'm having problems. It doesn't reconnect at logon, and it doesn't treat the filesystem as local....
 ~ Dagr[/quote] I have done this using samba by adding an **smbfs** entry to /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system>          <mount point>   <type>  <options>          <dump>  <pass>
proc                    /proc           proc    defaults                0       0
/dev/hda2               /               reiserfs defaults               0       1
/dev/hda4               swap            swap    defaults                0       0
/dev/hdd                /media/cdrom0   iso9660 ro,user,noauto          0       0
/dev/fd0                /media/floppy0  auto    rw,user,noauto          0       0
//hostName/shareName    /mountPoint     smbfs user,rw,auto,umask=0,     0       0

``` Sometimes the remote userName and password is needed:
```
//hostName/shareName    /mountPoint     smbfs user,rw,auto,umask=0,username=remoteUser,password=remotePassword  0       0

``` I am not sure about  **umask=0 ** but I use it when I am connecting to a fat32 (windows) computer.

Maybe somebody more experienced can help with the correct answer:smile:
Tomy

---

### Post by Dagr on 2005-10-25
When I get home I'll have to give that a shot, thank you!!

 ~ Dagr

---

### Post by GrammatonCleric on 2005-10-28
If your drive mappings require a password I would add something like the code below to your /etc/fstab. If you are connecting to a 2000 or 2003 you'll need to use cifs instead of smbfs.

```


//server/videos              /media/videos    cifs  credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//server/music                  /media/music       cifs    credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0


``` 
The dmask=777,fmask=777 will allow you to read and write to the shares.

Now create a file in the /root that stores your username and password for the share(s). If the shares require different credentials then you will need to create two seperate files. From the command line type....

```


sudo nano /root/.smbcredentials


``` 
Enter in the file your user name and password as follows...

```


username=jdoe
password=f00


``` 
Save the file... You should be golden!:D

GC

---

