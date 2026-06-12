---
title: "hib-core driver"
date: 2008-01-01
forum: System76 Support
---

### Post by m005e on 2008-01-01
I have a Gazelle laptop from system76. I attempted to upgrade the os to 7.10  but after the upgrade the system does not boot. I entered the grub menu and selected the recovery mode and it appears that the booting process hangs at the hib-core driver.  

I am able to select from the grub menu the previous kernel and can use the machine, but would like to compete the upgrade.

Also, it's a bit confusing as to whom I am writing - System76 or Ubuntu.

Thanks

---

### Post by thomasaaron on 2008-01-02
This is the System 76 forum, in which System 76 Technical Support folks and customers provide support for... each other.

What Gazelle do you have? (You can find out the exact model number by going to System > Administration > System76 Driver.

My guess is that you have a GazV4. If this is the case, your problem is solved by following the instructions below. If you do not have a GazV4, let us know what you do have and we'll take it from there.

-------------------------------------------------------

Press Escape when you see Grub loading
Choose an earlier kernel (2.6.20-something if I remember correctly)
Your system will boot - open up a terminal and run the following commands

sudo rm /etc/modprobe.d/blacklist-ata
sudo gedit /etc/initramfs-tools/modules

remove "piix" from the bottom of the file > save and close
sudo update-initramfs -u

sudo reboot

---

### Post by m005e on 2008-01-04
Thanks,
That worked. Would you be willing to explain a bit about what actually happened when I followed your instructions.
Frank

---

