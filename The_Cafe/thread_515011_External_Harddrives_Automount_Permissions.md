---
title: "External Harddrives Automount Permissions"
date: 2007-08-01
forum: The Cafe
---

### Post by mlanza on 2007-08-01
I am having inconsistent behavior on boot up.  I am developing a Rails application.  The application resides on an external harddrive (for backup purposes).  In my /var/www directory I have a symlink to the application's folder.  When I attempt to access my application from Firefox it *sometimes* craps out giving a generic Rails error (500.html).  I looked into the logs and it appears that the trouble is write access to the external harddrive I'm linked to.  At one time everything on my harddrive was marked as owned by me, but lately it is marked as owned by root.

I have attempted to "chown" but even with SUDO it is not permitted.  I would like the external drive to be auto-mounted upon boot.  I would like the permission for all files on it to be for my username, not root.

It appears that if I reboot enough times, I can finally run my Rails app.  This is a MAJOR pain.  Also, I have found that I can run my Rails app if I start it with a SUDO, but that defeats the purpose of it just working correctly.

Also, sometimes I see the icons for my 2 external drives on my desktop and sometimes I do not.  In any case, if I go to my "mnt" folder and click on the given drive I can see that it is indeed mounting (I think at that instant).  That is, If I start Rhythmbox all of my songs are gone until I click on that "mnt" point and it mounts.

What's the nature of the inconsistency?  That is, how can I track it down?  This is the one MAJOR pain I have experienced in the Ubuntu world.  Otherwise, everything is peachy and I actually prefer it to Windows.

Also in my mnt folder I sometimes see the two drives DOCS and MEDIA (with superimposed emblems like those appearing on my desktop) and the same two drives again in lowercase "docs" and "media".  Maybe this has something to do with it.  It there anywhere else other than fstab where information about auto mounting harddrives can be found?

Here's my fstab (last 2 entries are external drives):
I just changed to "owner" on those 2 lines from "user"...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0
# /dev/sda3
UUID=1534ea36-e748-4762-9824-7b6a4dbce5d9  /              ext3         defaults,errors=remount-ro          0  1
# /dev/sda1
#UUID=07D6-060E                            /mnt/dell      vfat         defaults,utf8,umask=007,gid=46      0  1
# /dev/sda2
UUID=E4DC69E6DC69B388                      /mnt/windows   ntfs         defaults,nls=utf8,umask=007,gid=46  0  1
# /dev/sda5
UUID=beae594f-6343-44c1-8fcb-bf6b46a03cce  none           swap         sw                                  0  0
/dev/cdrom                                 /media/cdrom0  udf,iso9660  user,noauto                         0  0
#usbfs
none                                       /proc/bus/usb  usbfs        devgid=1002,devmode=666             0  0
LABEL=DOCS                                 /mnt/docs      vfat         auto,rw,owner,exec,umask=0,iocharset=utf8,check=r,shortname=mixed   0  0
LABEL=MEDIA                                /mnt/media     vfat         auto,rw,owner,exec,umask=0,iocharset=utf8,check=r,shortname=mixed   0  0


Much thanks!!

---

### Post by mlanza on 2007-08-11
I think I identified the issue and I'm posting in the case this might save someone else the troubles I ran into...

I commented out the following lines in my fstab:

#none                                       /proc/bus/usb  usbfs        devgid=1002,devmode=666             0  0  
#LABEL=DOCS                                 /mnt/docs      vfat         auto,rw,user,exec,umask=0,iocharset=utf8,check=r,shortname=mixed   0  0  
#LABEL=MEDIA                                /mnt/media     vfat         auto,rw,user,exec,umask=0,iocharset=utf8,check=r,shortname=mixed   0  0  

The first line with "usbfs" I think tells linux to mount all the usb file systems (I have two).
The second couple lines were me explicitly telling it to mount each.  First I comment out the last 2 lines and rebooted.  Still had the issue.

The I commented out the "usbfs" line and it seemed to solve the issue however the drives were mounted under the /media folder.  (one drive has a label "MEDIA" so don't confuse it with that)

When all these lines were commented out, Ubuntu just seemed to know to go ahead and mount these external drives even with no such mention in "fstab".  Not sure why that is, but however it knows to do so, I can live with it.

---

### Post by Dimitriid on 2007-08-11
I was thinking about an external hard drive but the permission problems to correctly format them and mount them seem to be a very common issue. FAT32 drives defeats the purpose of back up.

Is there any external drives under EXT3 out of the box? Would I be better off building a small home server with my data there ( internal hard drives are cheaper anyway and I could use server functionality later on with my work group )? You know, like putting together a 150 bucks machine, adding a ton of hdd space, run Ubuntu server and call it a day.

---

