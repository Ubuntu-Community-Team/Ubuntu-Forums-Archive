---
title: "Darter Ultra Problem with booting into 2.6.22 kernel"
date: 2008-03-30
forum: System76 Support
---

### Post by ahood on 2008-03-30
I have a System76 Darter Ultra (1.3" white) that came with Feisty Fawn. I did a system upgrade last night to Gutsy Gibbon (7..10). It all seemed to well. When I rebooted the machine for the first time into Gutsy, the boot process hung at the point where the Ubuntu splash screen appears and the orange bar never moves from left to right. 

I can boot up the system if I press the 'Esc' key to bring up the Grub menu and select the 2.6.20 kernel.

I have the System76 2,1,7 driver installed, which was probably installed during the upgrade.

Any help in getting the system to boot with the 2.6.22 kernel will be much appreciated.

Al

---

### Post by ahood on 2008-03-30
This looks like a pretty serious situation and I really could use a bit of direction on how to proceed.

If I wait long enough, eventually a Busy Box message shows up. There are a few posts on the Ubuntu forums on possible solutions (see link below); however, the modprobe ide-core and editing /etc/initramfs-tools/modules hasn't worked for me.

[Re: PowerBook does not boot after upgrade to Gutsy / 7.10]("http://ubuntuforums.org/showthread.php?t=581280&highlight=gutsy+initramfs+busy+box&page=6")

When the Busy Box message appears, typing 'modprobe ide-core' and then 'exit' does not result in the system trying to boot. It just gives a return. Thus, I cannot edit any files when the busy box message appears.

I have edited the /etc/initramfs-tools/modules files with the ide-core after booting into the 2.6.20 kernel. I ran the 'sudo update-initramfs -u' command and there was a message saying that the 2.6.22 kernel was being updated.

However, on reboot, it just hangs still.........

I have also tried editing grub and replacing the root=UUID=... with the system drive (/dev/hda1), but this hasn't worked either.

The conclusion I am reaching is that this Darter Ultra is not compatible with the 2.6.22 kernel for some unknown reason.

Any help will be greatly appreciated.

Al

---

### Post by thomasaaron on 2008-03-31
Ah, a late bloomer!

Please follow these instructions:

Press Escape when you see Grub loading
Choose an earlier kernel (2.6.20-something if I remember correctly)
Your system will boot - open up a terminal and run the following commands

sudo rm /etc/modprobe.d/blacklist-ata
sudo gedit /etc/initramfs-tools/modules

remove "piix" from the bottom of the file > save and close
sudo update-initramfs -u
sudo reboot

Your Darter should now boot into Gutsy. 

If you've never done the firmware upgrade on your CD drive, you might experience the old freezing bug. In that case, please contact me via email (support<at>system76<dot>com) for firmware flashing instructions.

---

### Post by ahood on 2008-04-01
THANK YOU thomasaaron

I am a late bloomer!! hehe

What you suggested did work and I can now boot into the 6.2.22 kernel. 

I did have to undo the changes I made to the /etc/initramfs-tools/modules, which was deleting the ide-core entry that I added as per another post. I also restored the /boot/grub/menu.lst to the original, which had root=UUID=.... I had modified it by replacing the root=UUID=.... with /dev/hda1.

I have not updated the firmware on the DVD drive and will email you for the instructions.

Thanks again.

Al

---

