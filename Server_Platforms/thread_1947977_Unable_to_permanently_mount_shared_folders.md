---
title: "Unable to permanently mount shared folders"
date: 2012-03-27
forum: Server Platforms
---

### Post by OasisTech on 2012-03-27
[SIZE=4]Within our network, we're running a Windows 2008 server, Ubuntu server v11.10, and several Windows 7/XP workstations.  

We are having trouble sharing folders/files that are hosted on the Ubuntu server.  I'm able to create a shared folder manually by selecting the folder and configuring the shared options. After creating the shares, other computers can access the data.

The issue starts whenever the server reboots.  

After the server restarts, we have to reconfigure the shared folders again.   [/SIZE]

[SIZE=4]I'd like to find a way to mount the shared folders during the boot process.  To date, I added the follow command to rc.local file:[/SIZE]

[SIZE=3]sudo mount -t cifs -o username=root,password=XXXXXX //192.168.1.11/ms_SHAREname /media/FC503CC8503C8C00/FOLDERName[/SIZE]
[SIZE=4]
The problem is the shared folders do not mount correctly and/or the other computers can not access these shares. Please let me know that we're missing...

Thanks.:confused:


[/SIZE]

---

### Post by collisionystm on 2012-03-27
make credentials file

put it in /root

name it .sharecred

Contents as follows...

username=DOMAIN\User
password=PASSWORD

Edit /etc/fstab

//192.168.1.11/SHARE /media/FC503CC8503C8C00/FOLDERName smbfs credentials=/root/**.sharecred**,gid=1901,iocharset=utf8,file_mode=0777,dir_mode=0777 0


type mount -a to mount it.

It will now mount after every reboot automatically.

---

### Post by Morbius1 on 2012-03-27
Maybe it's me but I'm reading 2 different questions in your post.

**Problem 1:**
> We are having trouble sharing folders/files that are hosted on the Ubuntu server. I'm able to create a shared folder manually by selecting the folder and configuring the shared options. After creating the shares, other computers can access the data.

The issue starts whenever the server reboots.

After the server restarts, we have to reconfigure the shared folders again.Your description sounds like you are using Nautilus to create the share. Nothing wrong with that but are the shares actually gone or is it that the folder icon indicates that it is not shared? Nautilus doesn't keep the share emblem on the icon very well so it may still be shared. One way to make sure though is after the next reboot run the following command to get a listing of the shares:
```
net usershare info --long
```**Problem 2:**
> I'd like to find a way to mount the shared folders during the boot process. To date, I added the follow command to rc.local file:

sudo mount -t cifs -o username=root,password=XXXXXX //192.168.1.11/ms_SHAREname /media/FC503CC8503C8C00/FOLDERName
**1st**, if it's in rc.local then it will be run by root so get rid of the sudo.

Another way is to put it in fstab like collisionystm showed you ( although I'm not sure what group 1901 is ).

**2nd**, from your description all of you clients to this server are Windows. What is it you are trying to mount? A share on one of the Windows clients?

I get confused a lot so maybe I'm not reading your post correctly.

[COLOR=Blue]**EDIT**[/COLOR]: You know, maybe this is the clue from your cifs mount statement:
> /media/FC503CC8503C8C00That's an ntfs partition that you are mounting and based on that mountpoint it looks like you are mounting this manually at every reboot. Is the problem that you want to have that partition automount? That might be the cause of Problem 1. That's easy to do since we already know it's UUID:

[1] Unmount the partition:
```
sudo umount /media/FC503CC8503C8C00
```[2] Create a mount point:
```
sudo mkdir /media/Something
```[3] Add the following line to fstab:
```
UUID=FC503CC8503C8C00 /media/Something ntfs defaults,nls=utf8,umask=000 0 0
```[4] Then run the following command to test for errors and mount the partition:
```
sudo mount -a
```

---

### Post by drdos2006 on 2012-03-27
The other question I would ask is, why does the Ubuntu server reboot so often ? I would imagine the server should be running for quite a while.

My other two cents worth is you may still have to have a batch file on your workstations to remap the server drive on a regular basis.

regards

---

### Post by OasisTech on 2012-03-27
Collisionystn,

Thanks for your replay.  After adding the mount statement to /etc/fstab:

//192.168.1.11/ms_music /media/FC503CC8503C8C00/music smbfs credentials=/root/**.sharecred**,gid=1901,iocharset=utf8,file_mode=0777,dir_mode=0  777 0

I receive the following:

root@server:~# mount -a
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


Suggestions?  

Thanks again

---

### Post by darkod on 2012-03-27
I might be reading this wrong, but in the first post you say you are having trouble mounting shares hosted on the Ubuntu Server.
Then why are you trying to mount cifs msShareName???

And as already mentioned, don't try to mount things at /media/UUID. That's where they get mounted by default, for example when plugging in a usb hdd. Create a folder /media/foldername and use that as destination mount point.

EDIT: One more idea: open terminal and try the mount command there first. It will show you errors if something is missing. Once you get the mount command working, it's easy to figure out what to put in /etc/fstab. But again, if the shares are on the ubuntu server, I have no idea why are you trying with mount cifs. It would be something like:
mount /dev/sda5 /mountpoint

---

