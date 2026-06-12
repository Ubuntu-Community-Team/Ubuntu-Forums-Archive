---
title: "Major failure at reboot, possible Raid5 problem"
date: 2006-05-07
forum: Server Platforms
---

### Post by spetko on 2006-05-07
Hi guys!

I have a serious problem. I have a server with 4 disks, 1st is the bootable one (raiserfs), and the other 3 are in RAID5 array. Everyting worked fine until now. Today I patched the system through the ubuntu upgrade service (I believe there were some kernel patches involved) and then rebooted the system. The first reboot worked fine. Than I changed my resolution of the screen (nothing  fancy, just 800x600) and after reboot, the problem started. 

During the boot the system hangs at:
 *Starting Enterprise Volume Management System...
*** glibc detected *** corrupted double-linged list: 0x0806f0b0 ***

After pressing CTRL-ALT-F1 the screen shows:

Uncompressing Linux ... Ok, booting the kernel.
Loading, please wait...
mdadm: /dev/md0 has been started with 2 drives (out of 3)


Needless to say this caused some mayor acceleration of my heart rate. I have no clue where to go from here. Any ideas? Any help would be appreciated.

Thanks, Spetko

---

### Post by spetko on 2006-05-08
Hi again!

I've managed to resolve the issue, so I'm posting it for all others that might have the similar problem. It was an allnighter so if I can spare you of this nightmare, read this.

As it looks the Enterprise Volume Management Systems sometimes damages the Raid array, so the system halts after reboot. Here is what you should do if you get similar messages after reboot as I did. 

1. Reboot again 
2. When Enterprise Volume Management is being started hit (Ctrl-C) to skip it, if you miss it, go back to 1. and hit the CTRL-C a bit earlier
3. After that boot should go through without a problem. You should be able to login into the system normally. Backup everthing that you can!!!
4. Run mdadm --D /dev/md0     (or md1, md2 ... .whatever you have)
   You should get the result where it is clear that one of the disks in the array failed, or it is listed as spare
5. Figure out what is the raid device that is spare. At the bottom of the screen of the mdadm --D command there is a list of active raid devices, the spare one is missing, that is the one that you are looking for. In my case I know that /dev/sda1 was my first disk, and the table listed /dev/sdc1 and /dev/sdd1 as active, therefore /dev/sdb1 was the one I was looking for
6. Run mdadm -a /dev/md0 /dev/sdb1    (adjust the mdX and sdY1 to your settings), it runs as a deamon so don't be alarmed since it looks like it finishes immediately.
7. Hit mdadm --D /dev/md0 occasionaly, there should be a line with notification that a recovery is in process, there is also a percentage completed there. When the recovery is over, you should be up and running. Also the table od active raid devices should now list all devices as active 
8.You can reboot now and/or remove the damn Enterprise Volume Manager. You do this by apt-get remove evms
9. go for a beer and send me a thank you note.:D 

best, spetko

p.s. Before doing any of the steps, read this:
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-8.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-8.html)
[http://ubuntuforums.org/showthread.php?t=37521](http://ubuntuforums.org/showthread.php?t=37521)
[http://ubuntuforums.org/showthread.php?t=86874](http://ubuntuforums.org/showthread.php?t=86874)

---

### Post by EmmEff on 2006-05-29
I had this **exact** problem over the weekend...  I did solve it by essentially booting from a Gentoo live CD (can't use Ubuntu Live CD since it starts evms automatically), disable evms starting at boot, and then rebooting from the hard drive.

My RAID5 array has been working flawlessly for over a year and this happens on the weekend...  what's up with that?

---

