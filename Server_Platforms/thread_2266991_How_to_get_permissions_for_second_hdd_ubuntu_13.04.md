---
title: "How to get permissions for second hdd ubuntu 13.04 server."
date: 2015-02-26
forum: Server Platforms
---

### Post by DD1 on 2015-02-26
Server 13.04. 

I just put in a second hdd for more storage space but I cant get permissions for it to share. I use plex to stream, all videos on first hdd are just fine until i put them on the second hdd. It totally refuses to let me see the videos. Although I can move files back and forth, delete etc.. Makes no sense to me what so ever. I am assuming this has to do with permissions for sharing the drive? Im pretty new to this server stuff so take it easy on me if I ask noob questions.

---

### Post by ajgreeny on 2015-02-26
Is this second drive an external USB attached or an internal drive?

I have never managed to get a USB drive seen by my Plex mediaserver; they are totally invisible, and I have tried all the usual filesystems usable in Linux; ext2, 3 and 4, fat32, ntfs, but all are non-starters.

---

### Post by DD1 on 2015-02-26
Just a standard 1 TB internal hdd. Im sure its something I am missing or dont have it setup right. Im guessing both.

I can see it, I can move and delete files from it I just cant get plex to see the files on it. I share file folders on it, I just cant get the drive itself to share.

---

### Post by darkod on 2015-02-26
If it's only permissions it's an easy fix. Open a ssh session and check permissions for both mount points of both disks.
You check permissions with:
ls -l /path

It will give you three groups of rwx, for owner, group and others. That's read write execute.

---

### Post by DD1 on 2015-02-26
Right. It shows: 

drwxrwxrwx 5 dj dj 4096 Feb 23 19:13 media

Which is why I can move, delete files to and from the drive. But I need to share the drive itself. Is that correct?

---

### Post by darkod on 2015-02-26
Ok, so you have rw for all. It's good from that side. How plex works I don't know. You probably need to modify the config to tell it to include the second disk (mount point) too. Try googling 'adding disk to plex'.

---

### Post by mörgæs on 2015-02-26
You should be warned that using 13.04 is a security risk. Have you considered installing a supported version?

---

### Post by DD1 on 2015-02-26
Ok, back up the train a minute. Lets pretend plex isnt on here. By the way, with simple things I cant figure out like this, I installed a gui to make it work or break it more.

If I go to my new hdd, I called it Storage, If I right click on it and try to share, it gives me an error 255.
But the files and folder on the Storage drive is shared enabled. 
The Storage drive is owned by me, I did this thinking it would make it work.
So, with all this mumbo jumbo said, I used the command you said again but backed up a folder to check the drive, again it is telling me it is shared or whatever rwx is just like before.
So, even though it is owned by me, why cant I get the drive to share itself? I think this is where the problem is coming from.

---

### Post by DD1 on 2015-02-26
> **mörgæs said:**
> You should be warned that using 13.04 is a security risk. Have you considered installing a supported version?

Yes, I do know this. Im just using it as a in house server and nothing more. Only goes on internet if something needs updating, like i dunno, ubuntu server 14.04. LOL
Thanks though.

---

### Post by darkod on 2015-02-26
> **DD1 said:**
> Ok, back up the train a minute. Lets pretend plex isnt on here. By the way, with simple things I cant figure out like this, I installed a gui to make it work or break it more.

If I go to my new hdd, I called it Storage, If I right click on it and try to share, it gives me an error 255.
But the files and folder on the Storage drive is shared enabled. 
The Storage drive is owned by me, I did this thinking it would make it work.
So, with all this mumbo jumbo said, I used the command you said again but backed up a folder to check the drive, again it is telling me it is shared or whatever rwx is just like before.
So, even though it is owned by me, why cant I get the drive to share itself? I think this is where the problem is coming from.

Well it doesn't work like that... What you need to do depends what you want to achieve. If you want to offer some content through Plex you need to work with its config files. The permissions don't have much to do with it, only up to some point.

The rwx doesn't mean shared. It means that any user can make changes to the files, including write/modify.

Do you only want to share the disk? That is usually done with samba especially if you want it accessible from windows clients too.

Other programs can be used for specific use. For example I use minidlna to stream content to my Samsung TV. I can have the permissions I need on the folder I want to stream, but until I make an entry in minidlna config to actually share/stream that folder, the TV won't see it as available.

So what actually is your idea? Plex?

---

### Post by DD1 on 2015-02-26
Yes PLEX is my intent on top of file storage. Why cant it just be simple? So my idea is kinda right, just going about it wrong. Apparently I need to find a book or something because this just got a whole lot deeper then I wanted it too. All I wanted was to add a flippin HDD for more room.

---

### Post by darkod on 2015-02-26
Please post the outputs of:
```
cat /etc/fstab
df -h
```

I googled a bit about Plex and I think I can help you...

---

### Post by DD1 on 2015-02-26
dj@ubuntuserver:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d28665dc-82e1-4828-a934-08ba90dfef7f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=afc012e6-dc02-450c-adde-b79a66392b11 none            swap    sw              0       0
dj@ubuntuserver:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       144G   24G  113G  18% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           298M  1.1M  297M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  248K  1.5G   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb1       917G   19G  852G   3% /media/dj/Storage
dj@ubuntuserver:~$

---

### Post by DD1 on 2015-02-26
Hmmm apparently ext4 has errors on line 9. Could this be something wrong with the hdd?

---

### Post by darkod on 2015-02-26
No, that's the option to remount it as RO if it finds errors... if you mean the fstab line.

I see in fstab you do not have an entry for sdb1 (the new disk). It means it will not mount automatically.

I suggest the following:
1. If you tried sharing the new hdd over the GUI somehow, undo that. Just disable the sharing you did.
2. Create new folder to act as mount point for the new disk, outside of /media. For example:
```
sudo mkdir /plex/disk2
```
3. Modify fstab to include entry for sdb1 and mount it:
```
sudo nano /etc/fstab
#Add the a new line:
/dev/sdb1   /plex/disk2   ext4   defaults   0   2
#Save and close the file with Ctrl+O, Enter, Ctrl+X
sudo mount -a   (to remount)
```

After that the new disk should be mounted at /plex/disk2, and on each boot it will do the same.
4. Give RW permissions to all:
```
sudo chmod -R a+rw /plex/disk2
sudo chmod -R +X /plex/disk2
```

After that it should be done. I'm not sure if Plex needs a reboot or it will try reading the media right away, but you can try rebooting the machine.

---

### Post by DD1 on 2015-02-26
Oh my gosh. I thank you. Ive been pulling my hair out over this for a few days. I figured it was a simple fix, just didnt know where to start.

 Thank a ton.

---

### Post by darkod on 2015-02-26
No problem. Glad you got it working.

Please mark the thread as solved. You can do that in Thread Tools above the first post.

---

