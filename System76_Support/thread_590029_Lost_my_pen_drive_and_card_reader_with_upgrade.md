---
title: "Lost my pen drive and card reader with upgrade"
date: 2007-10-24
forum: System76 Support
---

### Post by TomLawell on 2007-10-24
I have upgraded my daru1 (white) to 7.10 using update manager. All seems to have gone well except my pen drive and the builtin card reader do not mount.I can mount a 250G HD. Message is: Details: wrong fs type, bad option, bad superblock on /dev/sda1. missing codepage or helper program, or other error. 
Also the default kernel 2.6.22-14 hungs and the Darter will boot with 2.6.20-16
I have not updated the firmware and now I can't use the pen drive.

tal

---

### Post by thomasaaron on 2007-10-24
Not sure yet about the pen drive. What filesystem type is on it.

If the Darter will not boot into Gutsy, follow these directions:

Press Escape when you see Grub loading
Choose an earlier kernel (2.6.20-something if I remember correctly)
Your system will boot - open up a terminal and run the following commands

sudo rm /etc/modprobe.d/blacklist-ata
sudo gedit /etc/initramfs-tools/modules

remove "piix" from the bottom of the file > save and close
sudo update-initramfs -u

sudo reboot

Your computer should now boot into 7.10.

---

### Post by TomLawell on 2007-11-15
Thomas,

Sorry about the late reply. Had a death in the family to attend to.

I did as you said and I am now booting through to the latest kernel. It also now mounts my memory sticks. Will check the card reader next.

Thank You.

Tom Lawell

---

