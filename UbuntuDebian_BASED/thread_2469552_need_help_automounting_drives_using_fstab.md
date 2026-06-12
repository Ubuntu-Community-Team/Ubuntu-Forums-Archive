---
title: "need help automounting drives using fstab"
date: 2021-12-02
forum: Ubuntu/Debian BASED
---

### Post by unknowable on 2021-12-02
Hi everyone.  I'm trying to mount my external drives (one 2TB and one  3TB) automatically on boot.  I started with a video that shows you how  to automount drives in a virtual machine, then googled for a few more  specifics, but only root has write access to the first drive I created.   [Here's the video]("https://www.youtube.com/watch?v=PmswUaf96ZA") I watched, and [this page]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") was the second place I looked for more info, followed by [this one]("https://help.ubuntu.com/community/Fstab").  While none were specific to my exact needs, all three were helpful in getting me started.

Now  when my computer boots up, it automounts the 3TB drive to  /home/USERNAME/3TB but the drive is read only by everyone but root.  I  want to make it writeable by me specifically, there are no other users.   I'm using the /etc/fstab to automount the drive.  Here is the line I  have in /etc/fstab:

```
UUID=1df48e6a-8f70-4325-b00a-998cade164d7       /home/unknowable/3TB    ext4    defaults,nofail 0 0
```

I  have tried changing the options (currently defaults,nofail) to  defaults,nofail,rw and rw,defaults,nofail and even rw,nofail but that's  definitely not doing it.  I'm pretty sure all I need is the correct  option there in /etc/fstab but I can't figure out what the right option  is.  The places I've looked don't show how to do that specifically, or  else they're way too technical and I can't understand them.   :D

If  there's a better way to automount a drive other than /etc/fstab please  let me know.  Again, I'm the only user on the system but I definitely  need write access all the time, especially so that an app I want to run  can access the drive at startup.  Your assistance is greatly  appreciated.  Thank you for taking time out of your day to help a noob.   :)
_____________________________________________

EDIT: According to [this page]("https://man.archlinux.org/man/mount.8#FILESYSTEM-INDEPENDENT_MOUNT_OPTIONS") it looks like I just need to set the owner option, as right now the owner is root.  My username is unknowable, but I haven't figured out how to set owner yet.  Let me know if this is the quick answer, and thanks again.
_____________________________________________

EDIT:  I tried setting the owner tag in the options field to defaults,nofail,owner=unknowable .  That did give me ownership back but it didn't mount the drive.  I then tried owner=unknowable,defaults,nofail but both of those didn't work, same result: my username as the owner, drive not mounted.
_____________________________________________

EDIT: Alright, I tried creating a new subdirectory in my home directory, ~/3_TB/ .  I checked the owership (using ls -al) and it did show that I (unknowable) was the owner.  I then changed the fstab to show the new directory and rebooted.  It did properly mount the drive, but now the owner is root and I don't have write access to it.  Should I just create a quick script file that mounts my drives and put the file into my startup applications?  That would be less dangerous than editing the /etc/fstab file and not really too difficult...  Maybe I'll try that next.

---

### Post by oldfred on 2021-12-02
With NTFS the permissions are set in mount by fstab.

But with Linux formats you specify ownership & permissions.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I do this on my data partitions that have mount point /mnt/data
sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown -R $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

Note that the -R is recursion and all lower level folders are also changed.
Never run on a system folder, only on data folders.

In addition to nofail you may want either systemd-automount or autofs.
 [https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd](https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd)
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by Dennis N on 2021-12-02
> it looks like I just need to set the owner option, as right now the owner is root. My username is unknowable, but I haven't figured out how to set owner yet. Let me know if this is the quick answer, and thanks again. 

Use a terminal command. Assuming your user name is unknowable:

```
sudo chown -R unknowable:unknowable /home/unknowable/3TB
```

The first unknowable changes the owner, the second after the : changes the group. The -R changes this for all existing folders and files on the mounted file system. Some distros don't have a group with the users name, so that could be changed to something else. What does your OS use as default for group in files you create? Use that if necessary. This is for only file systems without an OS - a disk you use for your own files.

---

### Post by unknowable on 2021-12-02
Alright, cool, thanks oldfred!  That looks like exactly what I need to get this thing working, but it's going to take me a few minutes to read, understand, and implement what you told me - I'm new.  :D   I'll try that out and let you know what happens.

---

### Post by unknowable on 2021-12-02
Alright, thanks to both of you, I now have a totally writeable  directory with the drive mounted.  Now I just need to make that happen  on boot every time.  I guess for that I need a script file to run at  login?  Hmm....

---

### Post by unknowable on 2021-12-02
AWESOME!!  That did it!  I just created a script file in my home directory using the two lines you two gave me to chmod and chown the directory (recursively as you suggested,) and when I rebooted it mounted the drive and i (unknowable) have write/execute access to it!  WOW!  Awesome, thanks to both of you for your help!

I'm not going to mark this one resolved yet because I still have to mount my windows partition, ntfs.  That should be pretty easy to do now that I know how, so I'll set it up, test it out, then let you know and mark it resolved.

Thanks again to both of you for your help!  I'm learning and it's really exciting!  :D

---

### Post by Dennis N on 2021-12-02
> **unknowable said:**
> Alright, thanks to both of you, I now have a totally writeable  directory with the drive mounted.  Now I just need to make that happen  on boot every time.  I guess for that I need a script file to run at  login?  Hmm....

No, the fstab entry is fine. The change you made is permanent for every boot (unless you change it yourself).

Edit: Except the last 0 in the entry should be a 1 (or 2) to enable file system check. And I don't know about the nofail option you are using. I use just defaults.

---

### Post by unknowable on 2021-12-02
> **Dennis N said:**
> No, the fstab entry is fine. The change you made is permanent for every boot (unless you change it yourself).

Edit: Except the last 0 in the entry should be a 1 (or 2) to enable file system check. And I don't know about the nofail option you are using. I use just defaults.

Ok, thanks, that helps me out.  I read the nofail option allows the system to boot even if it can't mount the drive.  It's supposed to be a failsafe in case I don't have the drive plugged in I think.

I made the change you suggest, Dennis, changing the last 0 to a 1 to enable file system check.  Just about to reboot and try out the ntfs partition.

---

### Post by Dennis N on 2021-12-02
OK, nofail it is then. My data disk is internal so always connected. An NTFS partition is going to need a separate fstab entry. The one you display is only for an ext4 file system.

---

### Post by unknowable on 2021-12-02
> **Dennis N said:**
> OK, nofail it is then. My data disk is internal so always connected. An NTFS partition is going to need a separate fstab entry. The one you display is only for an ext4 file system.

Yah, I just set the type to ntfs and rebooted, it mounted the drive fully writeable and executable.  Now I only have one more drive - an external 2TB ext4 drive - to add, but that's gonna be the same as the first, so this is definitely resolved.

Thank you both for your time and guidance.  It was really helpful in resolving my issue.  :)

---

### Post by TheFu on 2021-12-02
Looks like you are getting good help already. I didn't notice all the posts until I'd written this, walked away, came back.  Anyway, I'd already written it.  Feel free to ignore it completely.

To be pedantic, "automount" is something very specific in Unix/Linux. There is a daemon that handles mounting on an "as-needed" basis, then it removes the mount when they aren't needed anymore.  "ubuntu autofs" are the search terms for this.  autofs is the same across all Linux (and probably Unix).  I use it for all USB and networked storage, since those connections are flaky.

But I don't think you are interested in autofs.  Sounds like you just want a simple /etc/fstab setup to mount storage at boot, before any users have logged in. I'm not a fan of using UUIDs for external storage mounts.  I much prefer LABELs, since humans think in those terms much easier.  **gparted** can set a LABEL on a partition.  [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) explains how to use the LABEL= for mounts.
```
[COLOR="#FF0000"]LABEL=Extern3TB[/COLOR]       /[COLOR="#FF0000"]media[/COLOR]/unknowable/3TB    [COLOR="#FF0000"]ext4[/COLOR]    [COLOR="#FF0000"]nofail,noatime,errors=remount-ro[/COLOR]  0 [COLOR="#FF0000"]2[/COLOR]
```

Hope that helps.  **Do not mount storage under a user's HOME directory**.  There will be problems.  Actually, we shouldn't mount it under /media/ either, but that's one of the "bless" areas for snap packages to access, so we can be practical (so it works) or we can be "right" (and snaps will never be allowed to access a more "correct" location.

I see reference to NTFS.  You should probably format the partition to use ext4 instead of whatever the USB HDD came with.  **gparted** can do that. NTFS may not be the best choice. It seldom is for a number of reasons.  NTFS brings permission issues for Linux. But if you must use it, I suppose it can work. Linux prefers native file systems. They are better supported with expected capabilities, not reverse engineered and faster.  Linux can use enterprise storage volume managers with native storage too, but that choice has to be made BEFORE the file system.  If you use NTFS, chown, chmod, chgrp, will never work with anything in that storage area.  But if you use ext4 or any other native Linux file system, all those permission/owner/group commands and ACLs plus xattrs will work as Linux programs expect.

---

### Post by oldfred on 2021-12-02
Once you reset ownership & permissions, you do not have to redo them.

I do often download something or use sudo (when I should not) and root takes ownership.
So I occasionally rerun commands, as a quick way to reset several files.

You can see settings with ll or ls -l. 
I also like to add to file browser the extra fields of ownership & permissions.

---

### Post by unknowable on 2021-12-02
> **Dennis N said:**
> OK, nofail it is then. My data disk is internal so always connected.

Hey Dennis, the thought occurs to me...  If it were me, I'd still add nofail to your fstab options, even on an internal drive.  What if the drive goes bad, or fails on you somehow?  Then your system wouldn't boot, would it?  I know that's a bit of a long shot, but that's what failsafe is for - it's a failsafe.

Obviously you know way, **WAAAY** more about this than I do on this subject, but it seems to me, as a layman, that it's always better to be safe than sorry.

Either way, I really appreciate your help.  Thanks again.   :)

______________________

SIDE NOTE: time to eat.  I'll be back to read those last replies in a few minutes.  Looks like you have something really valuable for me, TheFu, so I'll check it out when I get back.

---

### Post by unknowable on 2021-12-02
> **TheFu said:**
> To be pedantic, "automount" is something very  specific in Unix/Linux. There is a daemon that handles mounting on an  "as-needed" basis, then it removes the mount when they aren't needed  anymore.  "ubuntu autofs" are the search terms for this.  autofs is the  same across all Linux (and probably Unix).  I use it for all USB and  networked storage, since those connections are flaky.

But I don't  think you are interested in autofs.  Sounds like you just want a simple  /etc/fstab setup to mount storage at boot, before any users have logged  in. I'm not a fan of using UUIDs for external storage mounts.  I much  prefer LABELs, since humans think in those terms much easier.  **gparted** can set a LABEL on a partition.  [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) explains how to use the LABEL= for mounts.
```
[COLOR=#FF0000]LABEL=Extern3TB[/COLOR]       /[COLOR=#FF0000]media[/COLOR]/unknowable/3TB    [COLOR=#FF0000]ext4[/COLOR]    [COLOR=#FF0000]nofail,noatime,errors=remount-ro[/COLOR]  0 [COLOR=#FF0000]2[/COLOR]
```


Yah, that's exactly right.  autofs won't work for me in this case  because I have to make it run every time I want to use it.  The main  reason I'm doing all this is so that I can use an app that will run at  startup and access all my drives.  If I have to make it run by trying to  open a drive, that defeats the purpose.  It has to run on its own at  startup so that my app (which also runs at startup) can access all the drives.  As far as labels vs UUID's go, it probably would have been slightly easier to use labels instead of UUID's, but I just copy/pasted them where they needed to go.  Thanks for the info  though.

> **TheFu said:**
> Hope that helps.  **Do not mount storage under a user's HOME directory**.   There will be problems.  Actually, we shouldn't mount it under /media/  either, but that's one of the "bless" areas for snap packages to  access, so we can be practical (so it works) or we can be "right" (and  snaps will never be allowed to access a more "correct" location.

Don't  mount my storage under the home directory?  This is my personal machine  and nobody else will ever log into it, so my home directory will always  be accessible.  I can see how that would be an issue if I had another  user logging in, but it's just me.  Will that still cause problems in  the future?

> **TheFu said:**
>  I see reference to NTFS.  You should probably format the partition to use ext4 instead of whatever the USB HDD came with.  **gparted** can do that. NTFS may not be the best choice. ...

Heh. Yes, I am at least slightly aware of the shortcomings in using  NTFS in Linux, but that's my Windows drive.  It won't use ext4 at all  and as far as I know and NTFS was my only real choice in setting up the  Windows partition.  I mean I could have used FAT, but really?   :D   Oh, and that one is internal instead of USB based, so I would think it should be ok.

---

### Post by unknowable on 2021-12-02
> **oldfred said:**
> You can see settings with ll or ls -l. 

Yah, every time I want to see stuff I just use *ls-al |more*.

> **oldfred said:**
>  I also like to add to file browser the extra fields of ownership & permissions.

That's a great idea.  I'm definitely going to do that right now.  Thanks!

---

### Post by TheFu on 2021-12-02
> **unknowable said:**
> Yah, that's exactly right.  autofs won't work for me in this case  because I have to make it run every time I want to use it.  The main  reason I'm doing all this is so that I can use an app that will run at  startup and access all my drives.  If I have to make it run by trying to  open a drive, that defeats the purpose.  It has to run on its own at  startup so that my app (which also runs at startup) can access all the drives.  As far as labels vs UUID's go, it probably would have been slightly easier to use labels instead of UUID's, but I just copy/pasted them where they needed to go.  Thanks for the info  though.
autofs mounts whenever **any** process requests access. No user has to do anything. If samba tries to access the storage, for any reason and it isn't mounted, then it will be, automatically.  If samba isn't serving files off storage under autofs, then when the last process closes the last file, it will wait a few minutes, then umount it.  If the entire point of this is to have samba make this storage available, there is little difference between using fstab and autofs ... except the fstab is easier to setup.

> **unknowable said:**
> 
Don't  mount my storage under the home directory?  This is my personal machine  and nobody else will ever log into it, so my home directory will always  be accessible.  I can see how that would be an issue if I had another  user logging in, but it's just me.  Will that still cause problems in  the future?
Yes. You will have issues in the future.  There's a thread here from a guy who was sharing some storage in his home and got into some issues.  Then there is the entire backup problem.  Especially on a single-user box, the most important data backed up for any desktop will be in the users' HOME.  By mounting added, huge, storage there, your backup scripts need to specifically exclude those mounts.   The solution for is well traveled.  Put the mount in /media/somewhere, then create a symbolic link from /media/somewhere to your $HOME.  That makes access to the other mount easy and backup programs will just see the link as ... a link.

Whether a Windows OS partition should be mounted is a different question - my answer for this is NO WAY.  Windows data partitions can be mounted with little risk, but not the OS partition.  It is so easy to trash Windows due to an accidental mouse action.  I've seen that a few times in businesses.

> **unknowable said:**
> 
Heh. Yes, I am at least slightly aware of the shortcomings in using  NTFS in Linux, but that's my Windows drive.  It won't use ext4 at all  and as far as I know and NTFS was my only real choice in setting up the  Windows partition.  I mean I could have used FAT, but really?   :D   Oh, and that one is internal instead of USB based, so I would think it should be ok.
To my knowledge, there aren't any safe ext4 drivers for Windows.  FAT is ambiguous.  FAT16, FAT12, FAT32, exFAT?  At this stage, exFAT should be used only for flash storage that has to be shared between different OSes.  Some devices only support FAT32 and the EFI partition **must** be FAT32, regardless of OS.  However, Linux has f2fs for flash storage. It is native Linux, friendly towards flash (keeps write counts low) and supports all the expected Linux/POSIX file system stuff.  Some Android devices support f2fs, though some vendors go out of their way to disable it (f2fs is part of the default Android builds for the last few years).  They did this purely to ensure we didn't make that microSD slot into a place with 256G of storage, all native to Android so programs could be loaded there.  They want to charge $50 more between the 32G and 64G internal storage models. f2fs breaks that price model.

I've heard that MSFT is working to support native Linux file systems under Windows.  That would have been nice a few decades ago. At this point, we barely use Windows - only for financial programs and video editing. The video editing stuff is nearly gone as of this week, but most people aren't a tenacious about NOT using Windows.

---

### Post by Dennis N on 2021-12-02
> **unknowable said:**
> Hey Dennis, the thought occurs to me...  If it were me, I'd still add nofail to your fstab options, even on an internal drive.  What if the drive goes bad, or fails on you somehow?  Then your system wouldn't boot, would it?  

It won't boot completely, but far enough to allow you to fix it. It your data partition isn't mountable for some reason, then you probably end up in "Emergency Mode". If you then choose "Maintainance", you can immediately edit the fstab with a terminal based editor like nano to fix an incorrect entry, or comment it out to bypass the mounting. Then issue a reboot command and you will boot to your desktop as usual.

On where to mount, I have always used a subdirectory of /mnt

```
# data LV
LABEL=Common-Files /mnt/Common-Files ext4 defaults 0 2
# Virtual Machine Location
LABEL=VM-Disks2 /mnt/VM-Disks2 ext4 defaults 0 2

```

---

### Post by unknowable on 2021-12-02
> **TheFu said:**
> autofs mounts whenever **any** process requests access. No user has to do anything. If samba tries to access the storage, for any reason and it isn't mounted, then it will be, automatically.  If samba isn't serving files off storage under autofs, then when the last process closes the last file, it will wait a few minutes, then umount it.

Oh, cool.  So my app would still work fine if I used autofs.  That's good to know for the future.  Thanks!

> **TheFu said:**
>   If the entire point of this is to have samba make this storage available, there is little difference between using fstab and autofs ... except the fstab is easier to setup.

Well that's good to know.  My understanding is that if you screw up fstab at all the system won't boot, but this was pretty straightforward and I didn't have any issues.  Yes, it was pretty easy to setup after I learned the necessary stuff.

> **TheFu said:**
> Yes. You will have issues in the future.  There's a thread here from a guy who was sharing some storage in his home and got into some issues.  Then there is the entire backup problem.  Especially on a single-user box, the most important data backed up for any desktop will be in the users' HOME.  By mounting added, huge, storage there, your backup scripts need to specifically exclude those mounts.   The solution for is well traveled.  Put the mount in /media/somewhere, then create a symbolic link from /media/somewhere to your $HOME.  That makes access to the other mount easy and backup programs will just see the link as ... a link.

Huh that's important, I hadn't even thought of that.  Don't want to backup every drive I'm connected to.  Thanks!

> **TheFu said:**
>  Whether a Windows OS partition should be mounted is a different question - my answer for this is NO WAY.  Windows data partitions can be mounted with little risk, but not the OS partition.  It is so easy to trash Windows due to an accidental mouse action.  I've seen that a few times in businesses.

Hm.  Unfortunately all my Windows stuff is in one partition.  That being said, I've cloned all the partitions that Windows uses, so I'm not too worried about it.  If I do screw it up, it's small enough that I can restore the image in less than an hour.  No big.

> **TheFu said:**
> I've heard that MSFT is working to support native Linux file systems under Windows.  That would have been nice a few decades ago. At this point, we barely use Windows - only for financial programs and video editing. The video editing stuff is nearly gone as of this week, but most people aren't a tenacious about NOT using Windows.

Yes, in Windows 10 (at least, maybe sooner) if you install Windows *after* installing Linux, Windows will write almost 7,000 files to the grub and efi directories.  I know this from experience.  :P   It's not accessible to the user in Windows *yet*, but they already know how to write to (and mess up) your Linux boot partition.  As far as NOT using Windows, I can't find a complete image organization tool that does everything the way I want it to like I had in Windows, so I'm still using that app for my images.  Not very convenient, but like I said, I can't find a Linux app that does *everything* my old Windows app did, so I'm still using Windows.  Not fun to reboot every time I want to mess with my pics, but workable.  Everything else is moved over and working great in what I'm using, so I'm happy.

---

### Post by unknowable on 2021-12-02
> **Dennis N said:**
> It won't boot completely, but far enough to allow you to fix it. It your data partition isn't mountable for some reason, then you probably end up in "Emergency Mode". If you then choose "Maintainance", you can immediately edit the fstab with a terminal based editor like nano to fix an incorrect entry, or comment it out to bypass the mounting. Then issue a reboot command and you will boot to your desktop as usual.

Oh ok, good.  I knew you knew more than me.  :D

> **Dennis N said:**
>  On where to mount, I have always used a subdirectory of /mnt

```
# data LV
LABEL=Common-Files /mnt/Common-Files ext4 defaults 0 2
# Virtual Machine Location
LABEL=VM-Disks2 /mnt/VM-Disks2 ext4 defaults 0 2

```

Yah that makes sense.  TheFu told me about issues with backing up, and you both make sense.   It will only take a few minutes to change them over, so I think I'll do that.  Thanks for the tip.

---

### Post by TheFu on 2021-12-02
> **unknowable said:**
>  
<snip>
Yes, in Windows 10 (at least, maybe sooner) if you install Windows *after* installing Linux, Windows will write almost 7,000 files to the grub and efi directories.  I know this from experience.  :P   It's not accessible to the user in Windows *yet*, but they already know how to write to (and mess up) your Linux boot partition.  As far as NOT using Windows, I can't find a complete image organization tool that does everything the way I want it to like I had in Windows, so I'm still using that app for my images.  Not very convenient, but like I said, I can't find a Linux app that does *everything* my old Windows app did, so I'm still using Windows.  Not fun to reboot every time I want to mess with my pics, but workable.  Everything else is moved over and working great in what I'm using, so I'm happy.

Whenever I'm forced back to Windows, there are hundreds of Linux tools that I miss. Goes to show that it is purely a matter of perspective.  

Image organization is a complex issue. I use EXIF search tools and keep all the tags inside the base image file.  Been burned a few times when photo organization tools destroyed the DB.

---

### Post by unknowable on 2021-12-02
> **TheFu said:**
> Image organization is a complex issue. I use EXIF  search tools and keep all the tags inside the base image file.  Been  burned a few times when photo organization tools destroyed the  DB.

Yah, but it's not just the tags.  I use Google Picasa because it keeps  all of your images in the folders that you store them in on your  computer (rather than just grouping all of your photos together,) and  while it will sort by name or age by default, you can move around the  pictures in the thumbnail list in the order that you like, literally  based on your own personal likes and dislikes.  Oh, and if I change my mind about something, all I have to do to correct it is drag and drop the image(s) wherever my new choices want me to.  On top of that, the full  screen viewer really is *full screen*.  Full screen doesn't mean a  slightly larger image still showing the titlebar and all the tools and  buttons on one side, it means full screen.

I haven't found an image app for Linux that does those things, so I use  Picasa for Windows.  Although there are possibilities for running Picasa  in Linux (like WINE or PlayOnLinux) I haven't gotten them to work.   It's easier **for me personally** to use Windows than it is to configure WINE and make it  function, even for one program.  If I found an image organization tool  that runs natively in Linux and performs in the same way Picasa does,  then I would switch.  Hasn't happened yet, so I still run Windows.

---

