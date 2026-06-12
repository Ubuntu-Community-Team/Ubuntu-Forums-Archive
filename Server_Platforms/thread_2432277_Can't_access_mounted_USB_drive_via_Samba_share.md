---
title: "Can't access mounted USB drive via Samba share"
date: 2019-11-29
forum: Server Platforms
---

### Post by altereg02 on 2019-11-29
This is going to sound silly

0. Running Ubuntu 19
1. I have a Samba share configured for '/usr/share/ which I can access remotely just fine, as well as any directories and subdirectories created therein.
2. If I mount my USB drive manually through the command line to '/usr/share/media', I can access it via the Samba share.
    a. E.G. smb://myservername/share/media
3. Not wanting to manually mount the drive after every reboot I added the USB drive to my fstab
    a. /dev/sda2 /usr/share/media  exfat defaults  0  0
    b. After rebooting, the volume is mounted and accessible via the CLI, even by non-root users. E.G. no sudo required
4. When I connect to my share I can still see the original directories I could in step #1, as well as my mounted USB drive 'Media'
    a. What I can't do is access the 'Media' directory via Samba. I receive 'Access Denied' 

[ATTACH=CONFIG]284511[/ATTACH]

5. Thinking it was a permissions issue, I did a chmod 777 against the 'media' mount point and restarted Samba, but that didn't help

[ATTACH=CONFIG]284512[/ATTACH]

Maybe I'm barking up the wrong tree, but what is the difference between mounting the volume from the command line vs. through fstab that would make the directory inaccessible via Samba? Is there anything else it might be? Why can't I access the 'Media' directory via Samba?

---

### Post by TheFu on 2019-11-30
exFAT doesn't support chmod.  Permissions are only controlled using mount options with non-Linux file systems.  Those would include NTFS, FAT32, exFAT, FAT16.  I know a few people have setup samba to work with those file systems, but doing it will be a hassle, since you want non-root users to mount, which will create unknown permissions based on the user.  There are some ways around this, but I've not attempted those.

It is dangerous to assume /dev/sda is the flash disk.  Really should mount using one of these : LABEL=  UUID= or using one of the path symbolic links that won't change if you always plug into the same USB port.  The order of devices can and does change, so sda might be sdb or sdc or sdd in future boots.  Just depends on the order that the OS discovers each storage device.

I've been using f2fs for flash media storage. It supports Unix permissions.  If you have an SSD or spinning disk, then using ext4 is probably the best compromise.

If you are running a "server", then really it is best to stick with LTS releases. The last one is 18.04.

While you can mount storage anywhere you like, /usr/share/ really is meant to be read-only storage.  There is a Linux file system hierarchy standard document for what should be placed where.  The wikipedia article about it should be sufficient, unless you are making a distro to be released on the world.  

As for troubleshooting samba, it is always good to check the log files. These are in /var/log/smb/....

---

### Post by Morbius1 on 2019-12-01
What a curious bug - at least I think it's a bug.

I have an Ubuntu 18.04 server set up that also mounts an external exfat usb "drive" which is then shared through Samba. Although my mount expression is different from yours I have no problem accessing that share and that device through Finder on the Mac.

I set up an Ubuntu 19.10 system and did the same thing with the same exfat usb drive and when I go to Finder and follow the path to the device I get the dreaded "no enter" emblem on the folder. Honestly, I have no idea what the problem is here - newer version of exfat? Samba? MacOS? All of the above?

I did notice another oddity - and don't ask me to explain this one. If I modify the mount expression on the server to include umask=000 so that in your case it would be something like this:
```
UUID=xxxx-xxxx /usr/share/media  exfat defaults,umask=000  0  0
```
If I follow the path through Finder it still shows up with the "no enter" emblem but I can use Connect to Server to access the share and its subfolder directly without issue.

[COLOR=#0000cd]***Note**: You will notice that I replaced /dev/sda2 with the partitions UUID number. The old /dev/sdxy is too unpredictable a method to denote a partition. To find the UUID number for your partition run:*[/COLOR]
```
sudo blkid -c /dev/null
```

---

