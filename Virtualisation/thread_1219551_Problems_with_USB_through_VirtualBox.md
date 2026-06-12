---
title: "Problems with USB through VirtualBox"
date: 2009-07-21
forum: Virtualisation
---

### Post by nmaster on 2009-07-21
I am using the closed-source edition of VirtualBox.  Downloaded the 3.0 deb from the website.  I've installed XP, but my usb isn't working.  The host detects my bluetooth dongle but the guest doesn't.  I'm not sure why.  Look at the screenshot.  What should I do?  Thanks all.

---

### Post by synapsys on 2009-07-21
Perhaps add a new usb device? Green plus or blue circle?

---

### Post by nmaster on 2009-07-21
> **synapsys said:**
> Perhaps add a new usb device? Green plus or blue circle?

those are for adding filters.  anyone else have an idea?  the cdrom works, why doesn't this? i checked with other usb devices also, no luck.

---

### Post by WIGGMPk on 2009-07-21
By your avatar it looks like your using Jaunty.

If so, you can refer to these steps:

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

If you add a USB device filter, like synapsys is referring to, it will skip being mounted in the host and automatically be grabbed by the guest.

Otherwise, you will have to select the device. Im at work right now and I am not 100% on the names of the menus, but its the middle menu (in the upper left hand corner), there should be a spot called USB or USB Devices, and you will see the available devices to "mount" or pass through to the guest. Select the device you want and the guest should pick it up.


For situations like a device that ONLY works or you will ONLY use with Windows or a particular virtual machine and there is no sence for having it mounted in Linux/Ubuntu, just create a USB filter. Makes like easier.

---

### Post by steveneddy on 2009-07-21
Mine looks the same way - have you installed Guest Additions?

Maybe XP needs a driver?

It's a longshot.

Is USB listed in the Device Manager?

---

### Post by WIGGMPk on 2009-07-21
You dont need to install Guest Additions, you just need to follow these directions for whichever version of Ubuntu your using...


[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by nmaster on 2009-07-21
thanks for the link WIGGMPk.  that worked perfectly.  i'm not sure how i missed that when i googled, but it was just what i needed.

---

### Post by pointym5 on 2009-09-08
I've tried all of those things, and USB continues not to work for me.

Here's my uname -a output:

Linux patience 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 19:30:06 UTC 2009 i686 GNU/Linux

That's a 9.04 system if that's not clear. VirtualBox is at the latest version, and it's not the Open Source version.  I've got an XP guest that otherwise seems to work fine, and it does have the additions installed.

I've added the device as per the instructions:

```

% mount | sort
/dev/mapper/patience-root on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda5 on /boot type ext3 (rw,relatime)
/dev/sdb1 on /media/disk type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
gvfs-fuse-daemon on /home/m5/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=m5)
nfsd on /proc/fs/nfsd type nfsd (rw)
none on /proc/bus/usb type usbfs (rw,devgid=131,devmode=664)
proc on /proc type proc (rw,noexec,nosuid,nodev)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)

```

The symptom I see is as reported over and over again: all of my system USB devices show up in the list from the VirtualBox GUI, but they're all desensitized and cannot be made to work.

---

### Post by peteair1 on 2009-09-11
I feel your pain! I have been going thru this for 3 days reading prob a hundred pages of "Solutions". This is what worked for me TODAY> [http://www.linux.com/community/blogs/virtualbox-offers-a-simple-easy-to-use-virtual-machine-solution.html](http://www.linux.com/community/blogs/virtualbox-offers-a-simple-easy-to-use-virtual-machine-solution.html) About half way down the page read about "Administration menu you will see the "Users and Groups" entry" My user group for virtualbox had nothing in it, and after I added my user to it, I rebooted, loaded virtualbox/winxp, at the top devices, Check the device you want to use and bingo it works. My Creative webcam works perfect and My Flash drive.
My system is Kubuntu 9.04 and VirtualBox 3.06

---

