---
title: "Using USB drives on a File Server"
date: 2009-06-22
forum: Server Platforms
---

### Post by shobley on 2009-06-22
I recently replaced my Windows Small Business Server with Ubuntu Server. 
I have 3 USB hard drives connected and shared through Samba.

Originally I followed this tutorial to get everything working:

[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

My problem is that this is for fixed disks. I have noticed that the device names used for the USB drives sometimes change around when I boot Ubuntu.

I need them to either come up with the same /dev/<id> each time, or configure Samba to locate them dynamically.

I found something called 'usbmount' but I'm not sure how this can help me.

Any help greatly appreciated.

Steve

---

### Post by HermanAB on 2009-06-22
Howdy,

The solution is very simple actually.  If you set the filesystem Label to a unique value on each disk drive (data, stuff, garbage), then the drives will always mount under /media with those names: /media/data, /data/stuff and /media/garbage.

So depending on the file system use the appropriate tool to set the label.  You can set the ext3 label with tune2fs.

---

### Post by shobley on 2009-06-22
OK that makes sense - they are all NTFS - I've been googling for a while now but I can't find how to set an NTFS volume name in Ubuntu.

Is there a util for this?

Steve

---

### Post by shobley on 2009-06-22
OK so I installed the NTFS utilities and tried to set names on my volumes. 

When I set them it did not complain but after rebooting nothing seems to have changed. They have no fixed device names and so can't be scripted.

I installed usbmount, but so far this does not seem to have mounted anything. The usb<x> mount points do not contain any data.

Maybe it's the NTFS file system?

Is it not recommended to use USB devices as shares?

---

### Post by shobley on 2009-06-22
I did a bit more testing and it looks like the names have stabilized, but I think the problem is that the USB disks don't become available until after the fstab script has been run. So the mounting does not occur during boot up.

Logging in over SSH and executing 'mount -a' fixes things.

Can this be run after a certain time period, or is there a way to detect that the disks are now available, and do the mount?

Steve

---

### Post by HermanAB on 2009-06-22
Well, you have to ensure that the label is set properly, else it won't work.

For example:
$ sudo ntfslabel /dev/sdbX data

Get sdbX with dmesg and ls:
Plug the drive in
$ dmesg
$ ls /dev/sd*

Ensure that the label is correct:
$ ntfslabel /dev/sdbX

Then, simply unplug the disk and plug it back in again to have it remount.

The disk mounting is done by udev and HAL.  You don't need any special software.  HAL will automount any drive that is NOT listed in /etc/fstab.

---

### Post by shobley on 2009-06-22
It looks like the labels are set correctly on all 3 volumes.

Is there some additional software to install to get the automount to work? I installed autofs but I got a bit lost with writing the config files.

---
Update

Ok so I need to remove the lines in fstab, and then would a reboot do the same thing, or do I need to unplug/plug the drives manually?

---

### Post by HermanAB on 2009-06-23
Well, it should work plain vanilla right off the bat without any extra software or configuration.  Goodness knows what the schtuff you installed broke...

---

### Post by shobley on 2009-06-23
Are you sure that this works on server with NTFS disks? 

I found some articles that describe exactly what you are saying, but only for the client version of Ubuntu and for ext formatted volumes. They went on to say that FAT/NTFS do not work quite the same.

It's not a huge problem having to run mount -a manually, but it would be nice to tidy this up.

---

### Post by HermanAB on 2009-06-23
Yes it works with NTFS too on my systems.  I have used FAT, NTFS and Ext3 this way.  All you need to do is define the file system label and then it will automount in /media.  HAL and messagebus must be running though.

---

### Post by shobley on 2009-06-23
Thanks...   How do I check for HAL / Messagebus...?

---

### Post by aago1254 on 2009-06-29
hope all this works for me i am going to try to do the same thing on my system it could see it in webmin but not able to be in use. or mounted correctly i am using nfts and all but problems.   ill ssh in and see if these steps will work. :guitar:  maybe i can get my first server working without a hitch.

---

### Post by frafu on 2010-07-13
Hi,

Could anybody please tell me what packages I have to install in order to have an usb harddisk automatically mount (when it gets connected) on the directory /media/label, with the folder label being created automatically during mount?

In fact, it is how it works on the desktop edition and I would like it to work similarly on the server.

Thanks in advance.

---

