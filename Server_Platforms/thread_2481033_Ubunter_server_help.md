---
title: "Ubunter server help"
date: 2022-11-17
forum: Server Platforms
---

### Post by mayfield016 on 2022-11-17
OK so I've stuffed up my ubuntu server and in doing so have lost access to 3 ntfs hdds and can now only access them as root whereas before I could access them as the user mick and could acsess them through my linux mint laptop. I'm still a beginner with linux

So I had a windows 8 machine that had been driving me mad, so pulled 3 hdd out and put them into ubuntu server, mounted them and could access them from linux mint laptop everything working good, however the 3 ntfs hdd by default were read only so I went looking to change this to RW and found a site recommending installing fuse and now I cant access them.

I've tried logging in as root using sudo -i and using chown and chmod but it's not working, when I run either of these I can see the files/folder rolling along but when it's fininhed I still can't access the hdd when logged in as mick.

---

### Post by mayfield016 on 2022-11-17
Update -

I have wiped the drive I installed Ubuntu server on and have started again with a clean install. So access to the ntfs hdd is ok, however after mounting the hdd I got this message (see below) which brings me back to my original problem of read only access to the ntfs hdds. What can I do to get read/write access to these hdds?

[IMG]https://i.postimg.cc/WbzHk6nb/ntfs-hdd-fault.png[/IMG]

---

### Post by TheFu on 2022-11-17
> **mayfield016 said:**
>  
I've tried logging in as root using sudo -i and using chown and chmod but it's not working, when I run either of these I can see the files/folder rolling along but when it's fininhed I still can't access the hdd when logged in as mick.

a) use native Linux file systems whenever possible.
b) NTFS doesn't support chmod/chown ... ever. sudo doesn't matter.
c) Ownership, permissions for foreign file systems can only be controlled at the mount time, though specific mount options.
d) without specific mount options, root:root will be the owner and group.  Probably not desired.

For most people, 2 commands are needed to mount NTFS storage.  The 1st is need once.
```
sudo mkdir /media/ntfs01
sudo mount  -t auto     -o uid=$USER,windows_names,fmask=0002,dmask=0002       /dev/sdZ1      /media/ntfs01 

```
No spaces are allowed in the "options". That always applies.

The device really should be the UUID or a LABEL (you would create the label), because the device file can change at each reboot. The more storage devices there are, the more likely file systems will change.  There are other options possible, but I didn't want to scare you.

There are multiple ways to see the UUID.  I like to use 1 command to show all the important things about file systems:
```
lsblk -e 7 -o name,size,type,fstype,uuid,label,mountpoint
```
I prefer to use LABELs. 'gparted' can create/modify a label for a file system. There are other ways.  The mount command would be something like this:
```
sudo mount  -t auto     -o uid=$USER,windows_names,fmask=0002,dmask=0002       LABEL=storage01   /media/ntfs01 
```
No spaces are allowed in LABELs.

The last 2 items are the file system device and the mount point.
A mount point is just a directory that must pre-exist for the file system to be placed over/into.  Any existing files or subdirectories in that location will be inaccessible and not seen. Generally, this is not what you want.

Below, more advanced options are provided for different file systems. Any user or group entries will need to be changed for your specific situation.

**Some advanced options**

exfat
  -o dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002

ntfs - big_writes helps performance upto 30%
  -o nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002

ext4 - nofail for data-only mounts
  -o nodev,nosuid,noatime,errors=remount-ro,nofail

'id' can be used to get the uid/gid of the users and groups to provide access.

The big problem with using foreign file system is that a single permissions setting has to be used for al files/directories in that mounted file system.  Always choose a native Linux file system whenever the storage will not be directly connected to Windows or some other specific hardware that only supports foreign file systems.  That's the price.   If the storage will be accessed over a network connection, say via sshfs, nfs, or the dreaded CIFS, use a Linux file system.  CIFS is the least capable network sharing protocol available, but sadly, the most supported. The underlying file system on disk really isn't important to CIFS, though native Linux/Unix file systems are best for many reasons.  For Unix-to-Unix (that includes MacOS and Linux), use NFS.

---

### Post by slickymaster on 2022-11-17
*Thread moved to **Server Platforms**.*

---

### Post by mIk3_08 on 2022-11-19
> **mayfield016 said:**
> Update -

I have wiped the drive I installed Ubuntu server on and have started again with a clean install. So access to the ntfs hdd is ok, however after mounting the hdd I got this message (see below) which brings me back to my original problem of read only access to the ntfs hdds. What can I do to get read/write access to these hdds?


In my case, I build a web local site using some php script and their I can communicate all the hard drive on my Linux Ubuntu Server. There are lots of php script that can manipulate all your attach hdd/sdd storage in your server via gui web browser. I been doing this for a long time now. So far so fast and good. If your not much fast and familiar in executing commands to manipulate your server I prefer you try those things. Regards and cheers.

---

### Post by mayfield016 on 2022-11-19
Hello All

Big thanks for the help, very much appreciated. To get around the read only on the ntfs mounted hdd I booted up with a Windows PE boot disc and ran chkdsk on the hdds and that fixed the problem, so now when I'm using Ubuntu server I can access those drives from my Mint laptop and can read and write.

---

