---
title: "How to: install Ubuntu 10.04 LTS on Bladecenter"
date: 2010-05-21
forum: Server Platforms
---

### Post by pytheas22 on 2010-05-21
As reported on Launchpad as [bug 574468]("https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/574468"), installation of 64-bit Ubuntu 10.04 fails on IBM Bladecenters because the installer fails to detect the CD, due to a bug that has yet to be tracked down.

I've developed a workaround that will allow Ubuntu 10.04 Server to be installed on a Bladecenter blade by mounting an Ubuntu Server ISO image as a loopback device (and then further working around issues that arise from manually mounting the ISO image), and want to document it here.

**Materials**

You will need:

1. an Ubuntu Server 10.04 CD.

2. a USB stick formatted as ext2 with the Ubuntu Server ISO image stored on it.  Other file systems may work as well, however fat32 does not seem to work, as I was unable to mount a fat32 USB stick in the installer shell.

3. a Bladecenter with a CD drive and a USB port.  Both devices should be "attached" to whichever blade you're trying to install Ubuntu on.

**Installation Steps**

1. boot your blade to the Ubuntu Server CD. Make sure the USB stick is plugged in as well.

2. proceed with the installer as normal, setting the keyboard layout, etc.

3. when the installer gets to the point where it fails to detect the CD, go back to the main menu and select "Execute Shell."

4. in the shell, mount the USB stick with commands like these:
```

mkdir /mnt/sdb1
mount /dev/sdb1 /mnt/sdb1
```

5. copy the Ubuntu Server ISO image to the /root directory of the live file system with a command like:

```
cp /mnt/sdb1/ubuntu-10.04-server-amd64.iso /root/ubuntu-10.04-server-amd64.iso
```

6. mount the Ubuntu Server ISO image as a loopback device with mountpoint /cdrom:

```
mount -o loop -t iso9660 /root/ubuntu-10.04-server-amd64.iso /cdrom
```

7. unmount the USB stick (but leave it plugged in):
```

umount /dev/sdb1
```

Unmounting the USB stick seemed to be necessary in order to work around the "Failed to determine codename" issue detailed below in steps 9 and 10.

8. type "exit" to exit the shell and go back to the main menu. From there, select the option to detect the CD ROM.

9. continue with the installation.  It will go through networking and partitioning.  After partitioning, however, it will fail again, complaining that it "Failed to determine codename for release."  

10. at this point, go back to the main menu and choose the option to "Load installer components from CD."  Then check the option that reads "Load Installer Components from an ISO Image" and press Continue.

After the packages for detecting and loading ISOs are installed, the installer should automatically search all available disk drives (mounted and unmounted) for ISO images.  It should find the ISO image stored on your USB key and mount it.  Thereafter, the installation will continue as normal and you will not get the error message about failing to determine the codename for the release.  If this process fails, go back to the command shell and unmount your USB key--for some reason I found that if the key was mounted, the installer wasn't able to auto-detect the ISO image stored on it.

The codename issue seems to be related to the installer not liking that the ISO image was mounted manually.  Letting the installer find and mount the ISO image itself apparently allows it to perform whatever magic is required to allow the installation to proceed.  I figured this out mostly thanks to the tip in post #3 of [bug 122402]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/122402").

Here's hoping the real bug gets fixed soon so that all this hassle is not necessary in order to install an LTS release on popular server hardware.

---

### Post by tipsqueal on 2010-06-01
This workaround is almost entirely useless. If I have a CDROM drive I'll just use that to install. I am currently in a situation where I do not have a CDROM, just a USB flash drive.

---

### Post by pytheas22 on 2010-06-02
> This workaround is almost entirely useless. If I have a CDROM drive I'll just use that to install. I am currently in a situation where I do not have a CDROM, just a USB flash drive.

You didn't read the introduction, or I didn't make myself clear.  There's a bug that prevents the installer from working correctly when you try to install from CD on a BladeCenter.  The steps I list provide a workaround for the bug.

Of course installing from USB would be great, and preferable to using the CD, but my BladeCenter won't boot to USB.

---

### Post by marquivon on 2010-06-02
Maybe you can check out

[http://www.revouser.com/forum/viewtopic.php?f=7&t=794](http://www.revouser.com/forum/viewtopic.php?f=7&t=794)

It uses unetbootin. I've not tried it yet - I just used an external CD drive to install stuff on my server.

---

### Post by TheDigitalNinja on 2010-06-17
Whats crazy is I have even made a bootable usb drive by using the pendrivelinux tool as per ubuntu's suggestion. Even that gives me the "Failed to copy files from cd rom" error.

---

### Post by TheDigitalNinja on 2010-06-17
Alright I found a quick and simple workaround for this issue. If you have a usb cd rom you can use that to install. This is much simpler and quicker than manually mounting the iso, but it does require that you have a spare usb cd drive.

---

### Post by cignu on 2010-06-28
thanks!! this workaraond worked for me too

i'm trying to install Ubuntu Server 10.04 32bit on an intel D945GC board that wouldn't boot from an OCZ 4gb pen drive and had the "Failed to copy files from cd rom" error

---

### Post by rothux.j on 2011-06-11
(Yes, this still hasn't been fixed to work by Canonical - obviously not a priority. For anyone who is in the same boat as I was)

This workaround does actually work without a CD.
What you will need is **two** USB pendrives.

We shall call one of them /dev/sdb1, and the other /dev/sdc1. Ensure that both are formatted as FAT.

On /dev/sdb1, using unetbootin or something similar, install the iso to the pendrive. On /dev/sdc1, copy the actual server iso to the root of the disk (normal drag n' drop).

Follow the steps outlined by the OP up to number 4. Make two directories: /mnt/sdb1 and /mnt/sdc1. Use the following command:
```
mount /dev/sdb1 /mnt/sdb1
```
and then:
```
mount /dev/sdc1 /mnt/sdc1
```

At this point, you may find that you are unable to mount the drives, with an error like "invalid" or something. Type in the following:
```
nano /etc/fstab
```
You will have a nano prompt here, for editing fstab. I believe fstab monitors the mounting of devices.

Add the following to the end, following the same tab-structure:
```

none        /dev/sdb1          vfat        defaults        0          0
none        /dev/sdc1          vfat        defaults        0          0
```

Press Ctrl-O and press return, and then Ctrl-x. Again, attempt the mounts and it should work.

If it doesn't, type:
```
mount -a
```
to reload the fstab file, and it should now work.

Now type this:
```
cp /mnt/sdc1/ubuntu-server-image-##.iso /root/ubuntu-server-image-##.iso

```
Now resume the OP's tutorial, but when you do your unmount in step 7, do:
```
umount /dev/sdb1
umount /dev/sdc1
```

Easy :)

---

