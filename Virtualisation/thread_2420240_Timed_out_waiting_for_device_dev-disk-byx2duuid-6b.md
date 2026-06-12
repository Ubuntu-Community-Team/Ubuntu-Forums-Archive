---
title: "Timed out waiting for device dev-disk-by\x2duuid-6bc02b1e\x2dccfb\x2d4079\x2db258\x2d"
date: 2019-06-01
forum: Virtualisation
---

### Post by linuxnoob87 on 2019-06-01
All,

I've searched around but am not 100% sure what exactly my issue is or how to fix it. When rebooting my server (the past 2-4 times) I've been booting into emergency mode. I'm able to exit it and log in successfully, however, I'm not really sure what's wrong. I've run the "journalctl -xb" and amongst some of the error is 
```
Timed out waiting for device dev-disk-by\x2duuid-6bc02b1e\x2dccfb\x2d4079\x2db258\x2d21d08f302acd.device.

```

I've checked my fstab and I see an entry similar to that (minus the "x2d" part before each one). Running a "sudo blkid" I get (server name changed to protect the innocent):

```
/dev/sda1: UUID="6bc02b1e-ccfb-4079-b258-21d08f302acd" TYPE="ext2" PARTUUID="28e04850-01"
/dev/sda5: UUID="LqnSnl-IDFj-2nUu-U0GF-CJO4-mha2-031n5K" TYPE="LVM2_member" PARTUUID="28e04850-05"
/dev/mapper/Server1--vg-root: UUID="88d9a9d0-9ad7-4801-83c7-cc4dc748a8e3" TYPE="ext4"
/dev/mapper/Server1--vg-swap_1: UUID="5a178a9a-c874-4e10-af7b-90f678a208a4" TYPE="swap"

```

How do I go about fixing this? From what I've read it's sometimes an entry in the fstab file for a partition that's changed but I've not added or removed any partitions to this device in quite some time. The only thing I did do several months back was expand the partition used for storing files (as it was full).


THANK YOU in advance for any help you can provide; I feel as if i'm in waaaaaay over my head on this one.

Thanks,
LN87

---

### Post by linuxnoob87 on 2019-06-01
Ok. I totally shut down the VM and restarted it (from a "power off") and it booted up without any errors. What's weird, though, is that this will happen again at some point in the future.

---

### Post by TheFu on 2019-06-03
You are using LVM.  That is different from using straight partitions.
If you look at lsblk -f, you'll see how LVs are layered.  LVM is extremely flexible and LVs can be treated as regular partitions, with a few exceptions.  Those exceptions are in the ftsab and if they are used for boot partitions, than the initrd needs to have LVM capable code included at boot.

The pvs, vgs, and lvs commands provide short overviews of the physical volumes, volume groups, and logical volumes, which make up LVM.

Not sure if any of this helps.  Boot messages are full of lines that sound like issues, but aren't.  Usually it is due to a broken bios, but the kernel recognizes the issue and fixes it. Storage connections included.

---

### Post by linuxnoob87 on 2019-06-05
Sorry it's taken me a while to reply.

Yes, I am using LVM. I think I understood most of what you said and, if I get this correctly, there isn't much I need to do to fix anything as the filesystem should fix itself - correct?

Thanks!

---

### Post by TheFu on 2019-06-05
You say it is an issue with ftab entries, but never post the fstab?
That's like reading all but the last chapter from a book.

---

### Post by linuxnoob87 on 2019-06-07
Sorry about that! Here's my fstab file as is (with some usernames/passwords changed for security reasons - I know I need to go in and clean up the commented out sections):

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/FileServer--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6bc02b1e-ccfb-4079-b258-21d08f302acd /boot           ext2    defaults        0       2
/dev/mapper/FileServer--vg-swap_1 none            swap    sw              0       0
# - Commented out by USER -
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# - Commented out by USER -
# --
# Added by USER
## Double most recently working
# --
##//Server1/TV /mnt/TV cifs user=User1,password=Password1,iocharset=utf8,sec=ntlmsspi 0 0
#//Server1/TV /mnt/TV cifs user=User1,password=Cavaler0!,iocharset=utf8,sec=ntlmsspi 0 0
##//Server1/Movies /mnt/Movies cifs user=User1,password=Password1,iocharset=utf8,sec=ntlmsspi 0 0
#//Server1/Movies /mnt/Movies cifs user=User1,password=Cavaler0!,iocharset=utf8,sec=ntlmsspi 0 0
##//Server1/Music /mnt/Music cifs user=User1,password=Password1,iocharset=utf8,sec=ntlmsspi 0 0
##//Server1/Plex\040preroll /mnt/PlexPreroll cifs user=User1,password=Password1,iocharset=utf8,sec=ntlmsspi 0 0
# -- START Swich from Server1 to Server2 --
//Server2/Videos/TV /mnt/TV cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Movies /mnt/Movies cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Music /mnt/Music cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Plex\040preroll /mnt/PlexPreroll cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Comedy /mnt/Comedy cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Documentaries /mnt/Documentaries cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Karaoke /mnt/Karaoke cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
#//Server2/Videos/Other/Baby\040Songs /mnt/BabySongs cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Kids /mnt/Kids cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/DVR /mnt/DVR cifs uid=plex,gid=plex,user=plex,password=Password3,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Wedding /mnt/Wedding cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/4k/Movies /mnt/4k/Movies cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/4k/TV /mnt/4k/TV cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Other /mnt/Other cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0
//Server2/Videos/Movies/Riff\040Trax /mnt/RiffTrax cifs user=User1,password=Password1,iocharset=utf8,vers=2.0 0 0


# -- END Switch from Server1 to Server2 --
#
# -- Original Line to mount photos folder ---
#//Server3/USERPics /mnt/Photos cifs user=User1,password=Password1,iocharset=utf8,sec=ntlmsspi 0 0
# -------------------------------------------
#SMB 1.0 - Working 1.6.18
#//Server3/USERPics /mnt/Photos cifs user=User1,password=Password1,iocharset=utf8,sec=ntlm,vers=1.0  0  0
#SMB 2.0 - Testing 1.6.18
#USE THESE - COMMENTED OUT DURING Server3 MIGRATION
//Server3/USERPics /mnt/USERPhotos cifs user=USER2,password=Password2,iocharset=utf8,vers=2.0  0  0
#//Server3/USER2Photos /mnt/USER2Photos cifs user=USER2,password=Password2,iocharset=utf8,vers=2.0  0  0
//Server3/Rendered /mnt/USERHomeVideos cifs user=USER2,password=Password2,iocharset=utf8,vers=2.0  0  0
//Server3/USER2HomeMovies /mnt/USER2HomeVideos cifs user=USER2,password=Password2,iocharset=utf8,vers=2.0  0  0
//Server3/Dashcam_Video /mnt/Dashcam cifs user=USER2,password=Password2,iocharset=utf8,vers=2.0  0  0
//Server3/Youtube /mnt/Youtube cifs user=USER2,password=Password2,iocharset=utf8,vers=2.0 0 0


```

---

### Post by TheFu on 2019-06-07
The fstab has to be read early in the boot cycle, before networking is up and working.  But almost all of the mount commands in there completely depend on networking being up.  The option to tell the mount command to ignore those until networking is up is :
```
_netdev
```
But I would just remove those lines - not just comment them - from the file while troubleshooting this.  Save them into a file elsewhere.   I think that will solve it.  Let us know.

From the mount manpage:```

       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).
```

Simplify and test. Simplify and test.

Please don't put credentials in the fstab. There is an option, 
```
credentials=/etc/samba/win7lap-D.credentials
```
to avoid that.  The credential files(s) can be anywhere on the system.  /root/ would be a good place for them too. All mounts run as root, so the credential file(s) only need root:root  600 access.
BTW, Win7 and later support **vers=2.1**, which should be faster.

Another option is to use **autofs** for non-local storage.  This delays mounting until there is a request made.  The storage is mounted only as long as it is actively used, then it is automatically umount'ed when not needed anymore.  I use autofs for all non-local and USB mounts.  It is just a fast as the fstab mounts, accepts all the same options (unlike the GVFS/GIO GUI pseudo-mounts), and reduces resourced allocated when not in use.  This isn't really all that important.

BTW, you missed a password above - probably want to edit that out ... er ... and pick a better password. ;)

---

### Post by linuxnoob87 on 2019-06-09
Ok, here is what I've got as of now:
```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/FileServer--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6bc02b1e-ccfb-4079-b258-21d08f302acd /boot           ext2    defaults        0       2
/dev/mapper/FileServer--vg-swap_1 none            swap    sw              0       0
# Added by USER
_netdev
//Server1/Videos/TV /mnt/TV cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Movies /mnt/Movies cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Music /mnt/Music cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Plex\040preroll /mnt/PlexPreroll cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Comedy /mnt/Comedy cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Documentaries /mnt/Documentaries cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Karaoke /mnt/Karaoke cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
#//Server1/Videos/Other/Baby\040Songs /mnt/BabySongs cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Kids /mnt/Kids cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/DVR /mnt/DVR cifs uid=plex,gid=plex,user=user3,password=Password3!,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Wedding /mnt/Wedding cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/4k/Movies /mnt/4k/Movies cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/4k/TV /mnt/4k/TV cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Other /mnt/Other cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos/Movies/Riff\040Trax /mnt/RiffTrax cifs user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server2/USERPics /mnt/USERPhotos cifs user=User2,password=Password2,iocharset=utf8,vers=2.1  0  0
#//Server2/USER2Photos /mnt/USER2Photos cifs user=User2,password=Password2,iocharset=utf8,vers=2.1  0  0
//Server2/Rendered /mnt/USERHomeVideos cifs user=User2,password=Password2,iocharset=utf8,vers=2.1  0  0
//Server2/USER2HomeMovies /mnt/USER2HomeVideos cifs user=User2,password=Password2,iocharset=utf8,vers=2.1  0  0
//Server2/Dashcam_Video /mnt/Dashcam cifs user=User2,password=Password2,iocharset=utf8,vers=2.1  0  0
//Server2/Youtube /mnt/Youtube cifs user=User2,password=Password2,iocharset=utf8,vers=2.1 0 0


```

Look better?

I should probably put the passwords in a file but does it matter if this is in a homelab environment? I guess it does as I should learn the "best practices", however, I don't really utilize linux that often in my professional world. Thoughts?

Thanks again!

PS - Good catch on the password; edited the post.

---

### Post by linuxnoob87 on 2019-06-13
Bump

---

### Post by TheFu on 2019-06-14
> **linuxnoob87 said:**
> Bump

A)  didn't add the most important option.
B)  didn't simplify the file.
C)  ignored other advice.
D) didn't say whether it was fixed or not.

There's a bunch of unnecessary mounts in there.  If the directory structure and credentials are the same between the server and the client, why bother having separate mounts?

Simplify!!!!!

---

### Post by linuxnoob87 on 2019-06-19
A) Which option was that - I'll gladly add it I just don't know what you're referring to.
B) I did; I removed the commented out mount points from an old server - there's two in there I may use at a future date. I also removed the line breaks
C) What other advice did I ignore?
D) Yes, it's still working but I was waiting until I heard back to see if I could optimize the process any further

I am absolutely interesting in knowing what I did wrong and how to fix it; please don't misunderstand my posts. I'm much stronger on the windows side of things but WANT to learn linux - I'm just not that great at it yet.

Thanks again for any help you can provide. It's much appreciated.

---

### Post by TheFu on 2019-06-22
_netdev needs to be added to EVERY LINE that uses CIFS with all the other options.  

The fstab is 1 line for 1 mount. There are no other sorts of lines in that file.  The fstab has a manpage that explains the file format.  *man fstab* to see it.  The different options supported by each type of file system mount are explained in the manpage for those.  *man mount.cifs* .  The options listed in there work for fstab options and autofs options, although those config files place them in slightly different config files.  Option order does not matter, but all options in all those config files must be together, comma separated, no spaces allowed between them. 

Also, leave a blank line at the end of every config file on EVERY Unix system.  This is because the programmer who wrote the parsing code may have only looked for EOL, not EOF.  1 extra line solves days of troubleshooting over stupid config files. Yes, it shouldn't matter, but ... why tempt fate? Complaining about it never changed any code and the time is still lost.  1 extra blank line.

Simplify - that means delete all the cifs lines except 1.  Get that 1 working.  Copy the file to somewhere else while you work on this - ```
cp /etc/fstab ~/ 
```is what I'd do to have a copy in my HOME.

I can't read your mind and you can't read mine.  If you don't show the changes, How do I know what you've done?

But seriously, looks to me like you have 5x too many mounts for what you really need.

```
# Server1 mounts, simplified
//Server1/Music /mnt/Music cifs _netdev,user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0
//Server1/Videos /mnt/V1 cifs _netdev,user=User1,password=Pasword1,iocharset=utf8,vers=2.1 0 0

# Need to move teh pVideos somewhere outside Videos.
//Server1/pVideos/DVR /mnt/DVR cifs _netdev,uid=plex,gid=plex,user=user3,password=Password3!,iocharset=utf8,vers=2.1 0 0


# Move all these from Server2/{whatever} ... into Server2/V2/{whatever}
#   a single mount handles all of them now.
//Server2/V2 /mnt/V2 cifs _netdev,user=User2,password=Password2,iocharset=utf8,vers=2.1  0  0

```

Best to stop putting credentials into the fstab where **anyone** can read them. Use a credentials file for each server. It is an option, just like _netdev.  Add it to each line with amount.  You'll need at least 2 different files holding the credentials, perhaps 3.  The manpage explains that format, but
```
$ sudo more win7lap-D.credentials 
username=user1
password=whatever-the-password-might-be
```
The file location and permisssions should be such that only root can read it.  So:
```
-rw------- 1 root root 31 Jan 17  2015 win7lap-D.credentials
```

For many reasons, userids should be all lowercase, not mixed or upper. Probably can't fix that on Windows. I have no idea if it matters here or not.

Hopefully, those lines won't wrap in the post here.

---

