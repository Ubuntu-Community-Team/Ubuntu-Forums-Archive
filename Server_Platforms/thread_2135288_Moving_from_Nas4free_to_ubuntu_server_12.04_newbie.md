---
title: "Moving from Nas4free to ubuntu server 12.04 newbie questions"
date: 2013-04-13
forum: Server Platforms
---

### Post by GTvert90 on 2013-04-13
Hey guys, 

I set up a 3tb drive with nas4free and played around with that a bit. Its formatted as UFS. After more research I decided I wanted to be on ubuntu server. I got ubuntu server up and running on another hard drive.. and I was wondering how I go about importing my ufs drive. If possible. Or if I have to back up all my data and format it to a different format. Once that's done I'll need help setting up samba shares. 

As of right now I have server 12.04, transmission, samba, subsonic and webmin installed. 

Thanks
phil

---

### Post by TheFu on 2013-04-14
ufs is for Solaris, SunOS and BSD operating systems, not Linux.  Linux uses journaled file systems by default for a very good reason with ext4 being the standard.  You really want to migrate to ext4, which means a backup, re-format, restore will be needed.

Samba is a fine way to share files with Windows systems, but if you have Linux systems, NFS would be preferred. There are how-to guides for both  - google that + ubuntu for step-by-step instructions.

---

### Post by GTvert90 on 2013-04-14
I have windows computers, a WD tv liv,  and Android devices.  If nfs will work with all of that I have no issues using that instead.   I'll have to find a drive to copy stuff over to while I format

---

### Post by TheFu on 2013-04-14
> **GTvert90 said:**
> I have windows computers, a WD tv liv,  and Android devices.  If nfs will work with all of that I have no issues using that instead.   I'll have to find a drive to copy stuff over to while I format

I have those same devices, plus a few Windows machines. You need samba for the Windows and Android devices. NFS isn't really an option there.  Have you considered letting the WDTVLive be the network file server? It won't be as fast or support permissions, but leaving it on won't eat as much power.  Just a thought - an option to consider. I don't use mine that way, but did for a few weeks just because "I could."  100base-tx is kinda slow on a GigE network, so moving the storage to a faster network connected server was the difference between 11 MB/s and 75 MB/s for me.  BTW, that 75 MB/s is over samba.

Please consider getting another HDD that will backup all those files. Having a 1-3TB HDD fail and losing all that data would suck. Backup religion before the data apocalypse is important.

I need to re-read your initial post.

Google found this how-to for UFS under Ubuntu: [http://askubuntu.com/questions/85154/mount-ufs-filesystem](http://askubuntu.com/questions/85154/mount-ufs-filesystem)  Seems that mounting the file system should be fairly easy.  However, I stand behind the idea that UFS is an inferior file system and that EXT4 would be vastly preferred thanks to journaling.  Having to wait 4+ hrs for an fsck to finish on a non-journaled file system sucks. I remember it clearly.  Still, this mount might be a good short-term option until another drive can be acquired and formatted with a journaled file system.

---

### Post by GTvert90 on 2013-04-14
Right now I have under a TB  on my 3Tb drive.  I'm gonna pick up a 1TB USB drive to backit iup and reformat the main drive.  Plus I like the idea If my box dies I can take it out and use a USB adapter and windows will see it.  Then I can use the USB drive to duplicate backup the important files pics and videos.  The nas is primarily for movies and TV shows

---

### Post by darkod on 2013-04-14
Take it out of the box and windows will see it? Are you talking about the hdd? If you use ext4 which is the usual filesystem (for both the system and data disks), windows will not be able to read it if attached to a windows machine. Not by default anyway.

Some people do use programs to access ext2/3/4 partitions from windows but I wouldn't trust that for my data.

However, if the disk is good you can read it attached to any linux machine, including attached to a windows machine if you boot it with the ubuntu cd in live mode.

---

### Post by GTvert90 on 2013-04-15
> **darkod said:**
> Take it out of the box and windows will see it? Are you talking about the hdd? If you use ext4 which is the usual filesystem (for both the system and data disks), windows will not be able to read it if attached to a windows machine. Not by default anyway.

Some people do use programs to access ext2/3/4 partitions from windows but I wouldn't trust that for my data.

However, if the disk is good you can read it attached to any linux machine, including attached to a windows machine if you boot it with the ubuntu cd in live mode.


Good to know about the format. EXT4 still seems to be more accessible then the UFS it is now. 

My drive will hopefully be here later this week so I can do the setup properly and format and start fresh.

---

### Post by thnewguy on 2013-04-15
> **TheFu said:**
> ufs is for Solaris, SunOS and BSD operating systems, not Linux.  Linux uses journaled file systems by default for a very good reason with ext4 being the standard.  

I'd like to point out that UFS is a journaled file system these days.

Regarding the 3TB drive, instead of using ext4 as the file system it might make more sense to use ZFS. Both BSD-based NAS solutions and Linux can use ZFs, which would make it easier to switch back and forth.

---

### Post by GTvert90 on 2013-04-15
I don't see me switching back to nas4free after the move here. But I'll keep that in mind. With the ZFS as I add drives to the box it just pools data right? say I add another 3tb drive it'll look as if I have 1 6tb drive? I need to look into the advantages a bit more 

I really appreciate the help guys.

---

### Post by TheFu on 2013-04-15
Choosing ZFS is not as easy as implied.  The easy ZFS to use on Linux is FUSE - and very slow.  For your main storage to be that slow would be bad, IMHO. I'd never recommend anyone deploy ZFS over FUSE.

Using a kernel-based ZFS comes with different issues. Base on your current questions, I don't think you are ready to address each of those difficulties.  Heck, I'm not ready for those and have built many kernels and ran special file systems for years before Linux support was built-in.  ZFS isn't ready on Linux for average users. The level of hardware and administrative effort to run ZFS on Linux is too high for my consideration still.  You might have a different threshold.  The data on any computer is more important than the computer itself to me. I'm cautious about file system deployment choices.  A year ago, I wasn't use EXT4 in production systems yet. It was too new to me even with 5 yrs of general use.  I still run JFS on a few machines - it is proven and I've never lost a single bit from that file system. JFS isn't the fastest and wasn't bootable under Linux for many years when I first started using it.  It was a pain to use sometimes.  These days I only want to use file systems that are first-class citizens of Linux and easily booted by the kernel. That dumps a number of file systems from consideration - I think ZFS is one that fails those requirements too, but I could be wrong. 

Any storage that spans disks and presents a single mount point usually comes with additional risks. If 1 disk in the storage pool files, you might lose all the data spread across all the other disks too.  I've had that happen to me. It was bad.  RAID0 is normally what this is called and really should be used only by professionals who completely understand these risks or when the space is only used for temporary files and performance is more important than data safety ... like when video editing.  RAID0 is dangerous. If you can't clear all the files off that partition daily, I wouldn't use it.  I learned this the hard way.  Please learn from my mistake.

I was unaware that UFS was journaled now.  Used it on Solaris back when it definitely was not journaled.

ZFS does have some interesting capabilities, but there is a price for those. Complexity, learning, lots of RAM needed to make use of many of the more interesting aspects and a 64-bit OS.  4G is the minimal amount of RAM recommended for ZFS deployment unless an extremely basic setup is used. Sure people use it with 1G of RAM, but they don't use deduplication and almost always have performance issues.
If you do decide to check out ZFS, look into RAIDz and RAIDz2 so your data is better protected.

---

### Post by GTvert90 on 2013-04-22
so this Ubuntu is kicking my butt. LOL 

Having issues setting up the 3tb drive. Making a mount point. and getting it to mount on boot.. its formatted as ext4 now... Then samba is a whole other issue. I've googled my butt off but can't find many tutuorials that are any help to me. Or that I understand enough. Would any of this be easier/ possible if I installed a full desktop ontop of the server? I'm not too opposed to that at this point.

---

### Post by TheFu on 2013-04-22
> **GTvert90 said:**
> so this Ubuntu is kicking my butt. LOL 

Having issues setting up the 3tb drive. Making a mount point. and getting it to mount on boot.. its formatted as ext4 now... Then samba is a whole other issue. I've googled my butt off but can't find many tutuorials that are any help to me. Or that I understand enough. Would any of this be easier/ possible if I installed a full desktop ontop of the server? I'm not too opposed to that at this point.

* Partitions over 2TB in size need to be on GPT formatted disks - not MBR formats
* Always use **parted** or **gparted** to create partitions going forward. fdisk and other legacy apps don't do things you want done, automatically. This can get new users into trouble and could cause really poor performance.  It is just easier to use gparted and parted, IMHO.
* Samba is pretty easy to get working.  A desktop GUI will enable remote access to shared remote folders easy, but not provide server-class file shares - which is what you need. You need to use the CLI, period.

Getting Samba working breaks down into these tasks:
* Get name resolution working - 10 different ways to accomplish this. If the clients cannot "locate" the server, you will get really frustrated with Samba when that isn't the issue at all. Test with ping using the server-name from each client.  Static IPs, editing either /etc/hosts on every client or setting up central DNS using the router capabilities with dhcp reservations are the most common methods.
* Install samba - easy
* Configure /etc/samba/smb.conf for a few global settings, then the specific shared folder(s) you want. About 10 lines needed total.
* Set samba passwords to match Linux passwords. Initialize them. 
* Restart the samba service
OR
* setup access using the samba guest account where anyone on the network can read-write-delete everything. (bad idea, IMHO)

Sound simple?

---

### Post by darkod on 2013-04-22
Lets take it in smaller steps.

First, as noted in the previous post, you need to use gpt table on 3TB disk. If you used msdos, forget about it. Since I guess there is no data on the disk yet, just write new gpt table using parted. lets not assume and make errors. So we can see the disk device, post the output of:
```
sudo parted /dev/sda unit MiB print all
```

If there are more 3TB disks let us know which one you want to use with a new ext4 partition, and we can give exact commands. For both making the ext4 partition and mounting it on boot with /etc/fstab.

---

### Post by GTvert90 on 2013-04-22
Model: ATA ST940210AS (scsi)
Disk /dev/sda: 38154MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start    End       Size      Type      File system  Flags
 1      1.00MiB  244MiB    243MiB    primary   ext2         boot
 2      245MiB   38154MiB  37909MiB  extended
 5      245MiB   38154MiB  37909MiB  logical                lvm




Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdb: 2861588MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start    End         Size        File system  Name  Flags
 1      1.00MiB  2861588MiB  2861587MiB  ext4         red




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-swap_1: 4028MiB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start    End      Size     File system     Flags
 1      0.00MiB  4028MiB  4028MiB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 25532MiB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start    End       Size      File system  Flags
 1      0.00MiB  25532MiB  25532MiB  ext4

---

### Post by GTvert90 on 2013-04-22
i went back and am running a clean install with no added packages at the moment. the system is on a 40gb hdd and I have the 3tb drive there as well... I apreciate the help. I'll be working on this a little longer but then gotta get going to work I'll be back at it tonight/tomorrow

---

### Post by darkod on 2013-04-22
OK, so you actually have a gpt table and one partition spanning the whole disk, /dev/sdb1.

In /etc/fstab you can mount it on each boot by adding this line:
```
/dev/sdb1   /mountpoint   ext4   defaults   0   2
```

Of course, replace the /mountpoint with the mount point (folder) you created for the partition. That will mount it on each boot and it will be available at /mountpoint. Save and close the file. Reboot to check if it mounts OK on boot.

These days partitions are often mounted by UUID, not by /dev/sdb1. That can help you in future if you move the disk and it's no longer /dev/sdb. The UUID string will be the same so fstab will mount it OK. You can get the UUID strings for all partitions with:
```
sudo blkid
```

So, the alternative line for fstab is:
```
UUID=<string>   /mountpoint   ext4   defaults   0   2
```

That will work even if the partition is no longer sdb1. Until you format it, because when you format a partition it gets a new UUID.

---

### Post by GTvert90 on 2013-04-23
can we start over at the formatting step? I used ajenti and don't recall what I used as /mountpoint. so I'm having trouble using your uuid command to set the mountpoint at boot.. Noobie problems.

---

### Post by GTvert90 on 2013-04-23
[http://ubuntuforums.org/showthread.php?t=267869](http://ubuntuforums.org/showthread.php?t=267869) would that be a good guide to follow? I'm headed to bed tonight some more wrenching on the mustang tomorrow and then some computer time.

---

### Post by darkod on 2013-04-24
But you select the mount point. And it has nothing to do with formatting. It only has to be an existing folder in the filesystem and empty. For example, lets say you want to use /data. First check if it already exists (if it does it needs to be empty):
```
ls /data
```

If that says there is no /data, create it:
```
sudo mkdir /data
```

Then check the sdb1 UUID with:
```
sudo blkid
```

Once you have the UUID string, modify /etc/fstab with:
```
sudo nano /etc/fstab
```

Add the line:
```
UUID=<string>   /data   ext4   defaults   0   2
```

Save the file with Ctrl+O, Enter. Close it with Ctrl+X.

To mount it right away use:
```
sudo mount -a
```

After that you should have it mounted at /data. You can check with:
```
df -h
```

And it will keep mounting it at each boot.

---

### Post by rubylaser on 2013-04-24
+1 to Darko's directions.  If you want to make this even a bit more automatic, then just copy and paste these into your terminal.

```

# Make yourself root, enter password when asked
sudo -i
# Remove any lines containing /dev/sdb from /etc/fstab
sed '/sdb/d' /etc/fstab
# Make a mountpoint for your disk
mkdir -p /data
# Get the UUID of /dev/sdb1 and add it to /etc/fstab
echo `blkid | grep sdb1 | cut -d " " -f2 | tr -d '"'` /data   ext4   defaults   0   2 >> /etc/fstab
# Mount the disk
mount -a

```

Once you've verified that the disk is mounted, then it's on to sharing it with Samba.

---

### Post by GTvert90 on 2013-04-24
After I go to do mount -a I get root@ubuntu:~# mount -amount: special device UUID=<242a7740-c73b-40dc-8c5a-3193a6a253a8> does not exist

---

### Post by darkod on 2013-04-24
Don't put the <>, they were just to specify the <string> value. Put only the value after the = without the <>.

---

### Post by GTvert90 on 2013-04-24
Got it! thanks Now to setting up samba. 

Ideally I'd like 1 folder that is mine to be password protected to keep computer backups and important files. Then at least 1 other folder to be public that I can keep media in.

---

### Post by GTvert90 on 2013-04-24
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) this accurate?

---

### Post by TheFu on 2013-04-24
> **GTvert90 said:**
> Got it! thanks Now to setting up samba. 

Ideally I'd like 1 folder that is mine to be password protected to keep computer backups and important files. Then at least 1 other folder to be public that I can keep media in.

The best way to handle this is 2 different mount points - that means 2 different stanzas inside the smb.conf file.

* Check out the [Home] method - limited to just your ID ; each user would get this if they have an account on the Linux machine.
* somewhere else that can be shared with anyone (no account needed) or just with authenticated users on the Linux machine.

I've seen lots of how-to guides for both and I use both here - with authentication and without it. I do only allow very specific IPs to access the read-only mount that doesn't require authentication. A DHCP user will not see the open samba-share at all.

---

### Post by TheFu on 2013-04-24
> **GTvert90 said:**
> [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) this accurate?

There are many different setups. It appears that those instructions are trying to address everyone and some more complex options that home users don't need. A simple samba config is what you seek. Forget about Domains or Active Directory, AD. You don't care. Stay "workgroup" only to make it simple.

I have **never** needed to use WINS on a small network. NEVER. On work networks, sure WINS is needed, but not at home.  

Besides that, those instructions seem very thorough - perhaps with more than a few extra steps.  I didn't try to follow all the steps - that is your job.  Try it. If it works, great, but perhaps the instructions are making it overly complex?

This [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/) seems easier to me and I think it will work for small setups.  Again, I didn't try these instructions either. That is your job with your system. 

When you try things and it doesn't work, we will ask you to look in the log files for clues.  Have you seen those yet?  /var/log/samba/ is usually where samba logs sit.  Lots of help in solving issues, they are.

---

### Post by GTvert90 on 2013-04-24
How do I set up more users on main server? Then I could just do a /media folder for all the movies and what not and have that as browsable by anyone on network?

---

### Post by darkod on 2013-04-24
For a simple user creation, where the home folder will be default /home/username you simply use:
```
sudo adduser new_username
```

It will prompt you for the password you want to set (twice), the full name, and other stuff to which you can simply press Enter leaving them blank.

---

### Post by GTvert90 on 2013-04-24
I believe I've followed the steps in the how to guide you linked to but I'm having issues. What do I use to view the log?

---

### Post by ally_uk on 2013-04-25
[http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend)

Very easy to follow Samba tutorial includes tdbsam for user authentication

Hope it helps :)

---

### Post by GTvert90 on 2013-04-25
> **ally_uk said:**
> [http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend)

Very easy to follow Samba tutorial includes tdbsam for user authentication

Hope it helps :)
followed that too. I'm on 12.04 not 12.10 and I used nano to edit. but still isn't working can't log on to it with windows nor in my browser I'm sure its something really easy that I'm missing

---

### Post by darkod on 2013-04-26
I would suggest setting up open shares first. When that works, later you can start working on protecting your share with the password, and leaving the other share as open because that's what you want.

---

### Post by GTvert90 on 2013-04-26
How would I go about that?

---

### Post by darkod on 2013-04-26
I haven't tried it myself, but try something like this. The simple open sharing is easy to do with security=share in the [global] section in smb.conf. But that will not allow you later to have a share limited to your user, since all shares will be open (unless i understand that option wrong).

So, you can try with security=user and in the open share options to specify that it accepts guest. I remember something like reading that all not existing usernames/passwords are considered the guest or bad user. Lets try allowing that user to access the share.

Try making the smb.conf something like:
```
[global]
   workgroup = WORKGROUP
   netbios name = machine_name
   security = user

[opensharename]
   path = /path/of/folder
   guest ok = yes
   read only = no
```

Restart samba after making changes to the file. See if you can access that share without any password. If it works, you can do the protected share later.

PS. I forgot to add, make sure the folder has RW permissions for all. The linux filesystem permissions might be blocking users even if samba doesn't. Run:
```
sudo chmod a+rw /path/to/folder
```

---

### Post by GTvert90 on 2013-04-26
> **darkod said:**
> I haven't tried it myself, but try something like this. The simple open sharing is easy to do with security=share in the [global] section in smb.conf. But that will not allow you later to have a share limited to your user, since all shares will be open (unless i understand that option wrong).

So, you can try with security=user and in the open share options to specify that it accepts guest. I remember something like reading that all not existing usernames/passwords are considered the guest or bad user. Lets try allowing that user to access the share.

Try making the smb.conf something like:
```
[global]
   workgroup = WORKGROUP
   netbios name = machine_name
   security = user

[opensharename]
   path = /path/of/folder
   guest ok = yes
   read only = no
```

Restart samba after making changes to the file. See if you can access that share without any password. If it works, you can do the protected share later.

PS. I forgot to add, make sure the folder has RW permissions for all. The linux filesystem permissions might be blocking users even if samba doesn't. Run:
```
sudo chmod a+rw /path/to/folder
```

i deleted everything in the smb.conf and copied in what you wrote. It worked. But it streams like ****. Not sure what's going on with that I'll have to play with it a little more.

---

### Post by GTvert90 on 2013-04-26
same computer /ram/hdd/proccessor everything nas4free vs ubuntu I can't get ubuntu to stream one show to one device without stopping and buffering and all that.. nas4free was streaming to 6 devices at once and didn't skip a beat. Not sure if its something I screwed up when I was setting up ubuntu/samba (probably)

---

