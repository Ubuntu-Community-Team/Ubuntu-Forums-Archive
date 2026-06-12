---
title: "Ubuntu 12.04 Server Crash w/Mdadm Raid 5 &amp; 2GB USB Boot Drive"
date: 2015-05-14
forum: Server Platforms
---

### Post by mcapaldo on 2015-05-14
Last time I did a normal shutdown via command line no problems, that was a few weeks ago.  Today went to boot it (nothing changed) and got this info in the picture.  

System 

AMD 6000+ CPU 
2GB DDr2 Ram
USB 2GB Flash Drive boot Ubuntu 12.04
OLD Ass ATI PCI Video Card

Mdadm RAID5 = 6 x Sata II 2TB Drives on motherboard.  I had smartmon and sssmtp installed and did not get any warning of errors.  

Anytime I had server up (once a a week for rsync backups) I would login and check raid stats via cat or mdadm -details and all was good.  

Now not so much.

Can't even get to boot or in recovery mode to check array.



[ATTACH=CONFIG]261976[/ATTACH]

What do I do ???

---

### Post by tgalati4 on 2015-05-14
As I understand the linux boot process, there is a kernel (initrd.img--initial RAMdisk image) that is uncompressed and loaded and that bootstraps the reading of the "real" kernel which loads the appropriate hardware modules.  Perhaps you have a USB stick problem.  Although loading the operating system to RAM from a USB stick seems like a good idea, in practice it has issues.

Try booting into a previous kernel.  If that doesn't work, then try booting with your backup USB stick.

---

### Post by mcapaldo on 2015-05-15
Well I never bade a backup of the usb thumb drive.  I did put that thumb drive on another machine and copied all my important files off it (fstab, mdadm.conf, interfaces.conf, smb.conf, etc.)    So I used sudo dd if=/dev/sdb of=usb-image.iso to make an image of suspect thumb drive.    Then made a copy from said image sudo dd if=usb-image.iso of=/dev/sdb, after making sure 1st that /dev/sdb was the right path.  says it went without a hitch.     Put new cloned same size thumb drive in server and post, and same crashpic as before.         What do I do now?  Boot off a live cd,   run sudo apt-get install mdadm   then run...    mdadm --assemble --scan ?  See what drives are recognized/responding in the raid5.  I have a brand new spare disk in the box.

---

### Post by tgalati4 on 2015-05-15
First things first.  You call this a "crash" but I consider a "crash" a system that was working and then stopped working.  No rebooting involved.  What I see here is a bootup problem, not a RAID problem.  Once you get your system booted, then you should be able to assemble the RAID.

When you boot off of the USB, do you have a GRUB menu?  Does that menu have a "Recovery Mode" or a backup kernel to boot into?  If you don't see GRUB, try hitting ESC when booting.

Making a backup image of a bad USB stick will give you a clone of a bad USB stick.  So that is normal behavior.  It would have been helpful to have a backup of a working USB stick that you could use to boot your system.

Is it possible to repair the broken USB stick?  Yes, you would need a larger USB stick, image it with the broken USB image; use *gparted* to expand the primary partition (from 2 GB to 4 GB for instance), then rename the old initrd.img* to initrd.img--BAD.  Copy a new initrd.img to the USB stick.  However, to get the new initrd.img requires a kernel installation which takes as much time as starting from scratch.

You could create a new LiveUSB stick and boot from that, then assemble the RAID, but you will lose your specific configurations.

I would put in a small SSD and load an operating system on that.  USB sticks are not reliable enough for weekly bootups.  I have a freenas system that is booted off of USB, but I only reboot it once every 6 months, and I have a working backup of the USB image.

---

### Post by mcapaldo on 2015-05-18
Well I found out the usb flash drive was indeed semi hosed.  It was the culprit.  I have ordered a USB3.0 32 GB SSD Drive, but for now I used a spare pc and installed the latest 14.04.2 LTS 64 Bit Ubuntu Server onto a NEW 8GB Flash Drive.  Got the network working, and installed smartmontools, ssmtp, samba, & mdadm.  I copy and pasted the appropriate info from the bad stick via sudo gedit.  

Got the file server to boot now..  At 1st it dit not see the raid5, ran mdadm --assemble /dev/md0 and then it showed right up, ran update-initramfs now it auto mounts fine.  Working on samba.  got it partially working.  have added users, samba users, groups,  still got some work to do for samba.  But at least it is working now.  

Lesson learned make a backup copy of your usb thumb drive regularly.

---

### Post by tgalati4 on 2015-05-19
Glad you got it solved.  You can use the thread tools to mark the title of this thread as [SOLVED].

---

### Post by mcapaldo on 2015-05-19
Got all smb users added and updated directory permissions.  Its all working now.  And faster go figure.  Went from 12.04 LTS to 14.042 LTS.  

Had to sudo chown -R user:group /path/to-each-user-share, for each user to have separate shares.  The -R means change ownership of all files and all subdirectories.  

Soo.....

USER1 sudo chown -R user1:user1 /RAID5/user1

USER2 sudo chown -R user2:user2 /RAID5/user2

sudo nano /etc/samba/smb.conf

Scroll down to....

[USER1]

     comment = USER1 Share
     writeable = Yes
     path = /RAID5/user1
     browseable = yes
     guest ok = no

[USER2]

     comment = USER2 Share
     writeable = Yes
     path = /RAID5/user2
     browseable = yes
     guest ok = no
 

Now all is well.  Made a ISO of this 14.042 usb stick so I can restore on new 32GB SSD when it gets here.  

Lesson, make backups regularly including a USB Boot Stick.

---

