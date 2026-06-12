---
title: "Encrypted disk mounting on boot with keyfile on external USB drive?"
date: 2014-01-09
forum: Server Platforms
---

### Post by ted.drain on 2014-01-09
I'm starting a media server/NAS build ([http://pcpartpicker.com/user/TD22057/saved/3nEV](http://pcpartpicker.com/user/TD22057/saved/3nEV)) and want to use full disk encryption on my data drives (not the system).  I'd like to store the keyfiles on an external USB drive that I insert before the server boots and then remove when it's finished.  My goal is to prevent access to the data if the server is stolen.

I'm planning on using a SnapRAID setup and found this [tutorial ]("http://zackreed.me/articles/79-encrypted-snapraid")which goes through how to encrypt the drives before installing SnapRAID but it uses a local keyfile.  I also found this [tutorial ]("https://bbs.archlinux.org/viewtopic.php?pid=1035124")for ArchLinux which seems to do what I want and includes modifications to /etc/rc.d/functions/ to auto mount a USB drive, mount the encrypted drives, and unmount the USB drive.   

Has anyone tried something like this for Ubuntu?  I'm assuming the ArchLinux steps will work (server parts are arriving tomorrow) but if anyone has a different/better way to do this I'd love to hear it.

Thanks!

---

### Post by houstonbofh on 2014-01-11
Actually, here is a thought...  /boot is not needed when you are running.  (Other than updates, of course.)  If you install Ubuntu with a system drive, a boot drive on USB, and a encrypted drive, and place the key in boot, you can unmount it after booting and remove the key.  Just do not loose the key, and have copies.  USB keys are not the most robust hardware in the industry.  You may actually want to consider eSATA instead.

---

### Post by ted.drain on 2014-01-13
Thanks - that's not a bad idea.  The downside to that approach is that I can't boot the machine at all w/o the usb drive.  I'd prefer to allow it to boot all the time and just not mount the data drives.  I got my server running this weekend with encrypted drives using a local key file and optional password.  I'll try moving the keyfile to a usb drive this weekend and see if it works.

---

### Post by rubylaser on 2014-01-14
That looks like a nice server.  Moving the keyfile to a usb drive should work well, but you "may" have to mount your disks via /etc/rc.local, because the USB drive might not always be available when the machine boots (even when it's present, it might get mounted after some of the disks try to mount).  I'd write a simple shell script that tests for the presence of the USB drive, and if present, tries to mount the LUKS encrypted disks.  If it is not present, I would have it echo something back like "Decryption key not available.  Disks are not being mounted." I hope my tutorial was easy enough to follow.  Also, if you get this working properly, please post back here, I'll be happy to add your version to my tutorial.

Also, I like the idea of using [gpg to encrypt the keys]("https://bbs.archlinux.org/viewtopic.php?id=120243") on the USB drive as well.  If you are going to go crazy, you might as well go all the way :)

---

