---
title: "Runt"
date: 2004-11-12
forum: The Cafe
---

### Post by HungSquirrel on 2004-11-12
There's a bootable USB thumbdrive Linux distro based on Slackware called [RUNT](http://www.ncsu.edu/project/runt/), which just released version 4.0 .  It can be used as a nice portable Linux recovery distro.  It requires a 128MB or greater USB storage device.  (I have a 128MB stick and I am nearly out of room after installing it.)  If you want to give it a shot, here's how to do so, as taken from my experience.

- If your computer supports it, set your BIOS to allow booting from USB.  Otherwise, make sure you have a blank floppy disk.
- Your USB device should have a FAT16 partition.  If you want to format it, do the following, assuming your device is /dev/sda1:
```
sudo mkdosfs -F 16 -n RUNT /dev/sda1
```

- You will need some tools for working with MSDOS partitions.
```
sudo apt-get install mtools
```
- You will need to download [this file](http://www.ncsu.edu/project/runt/runt-4.0.zip).  For these instructions, download it to your home.

(This assumes /media/usb0 exists.)
```
mount -t msdos /dev/sda1 /media/usb0
cd /media/sda1
unzip ~/runt-4.0.zip
```
The above step sets up the initial Linux file structure on the USB drive.

The below step makes the USB drive bootable.
```
sh runutil/makeboot.sh
```

If your computer doesn't support booting from USB, insert a floppy and do:
```
sh runutil/mkfloppy.sh
```

If all went well with no errors, reboot.  You should see a boot: prompt come up.  If you booted from USB, you can just hit Enter for the default.  Hit F1 for help, or to use a framebuffer console.

Once you reach the login prompt, login as root with no password.  If you want to change the blank root password, once you are logged in do *passwd*.  If you want to add another user, do *adduser*.

RUNT has a [forum](http://moses.sca.ncsu.edu/phpBB2/viewforum.php?f=2) if you need help or you want to comment on the mini distro.

---

### Post by jdodson on 2004-11-12
i think this is great.  i think it would be more helpful in the HOWTO section.  perhaps the mod can move this post.  just my 2 cents.

---

### Post by HungSquirrel on 2004-11-13
The reason I didn't put it in HOWTO is this isn't Ubuntu specific.  I thought it would be kind of weird to put a HOWTO about another distro in the Ubuntu HOWTO section.  If you guys want to move it, I don't mind of course.  :)

---

