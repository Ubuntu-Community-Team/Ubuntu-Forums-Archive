---
title: "Daru2 Gutsy DVD Problem"
date: 2007-10-19
forum: System76 Support
---

### Post by agisfox on 2007-10-19
I've upgraded my Darter (2nd version) to Gutsy (including the 2.1.1 System76 Driver) and it mostly works, but seems to have disabled my DVD drive.  The drive spins up fine when I put in a DVD or CD, but the operating system never registers it.

There's GUI entries for "CD-ROM 1" but if I try to access them - whatever is in the drive, or if there's nothing there - it gives a "mount: special device /dev/scd0 does not exist" error, and I couldn't find anything in Hardware Information that would suggest the DVD drive.

---

### Post by palintheus on 2007-10-19
I can confirm this in my daru2

---

### Post by thomasaaron on 2007-10-19
OK, I just imaged and ran the system 76 driver on our shop DarU2, and the drive works fine..

First, did you actually*_ run_* the driver? If not, run the driver with the restore tab and button.

If that doesn't work, go to a terminal and enter these commands:
echo blacklist ata_piix | sudo tee -a /etc/modprobe.d/blacklist-ata
echo piix | sudo tee -a /etc/initramfs-tools/modules
sudo update-initramfs -u   
sudo reboot

Does this fix it?

---

### Post by agisfox on 2007-10-19
Yes, I ran the driver, though I didn't do a restore, just a straight run of the driver from the "Install Drivers" tab.

Ran a restore now, same result; then ran those commands, still same result.

---

### Post by palintheus on 2007-10-19
Ran the commands, I had previously ran the 'restore' from the driver, rebooted, same result, rant the 'install drivers' button, rebooted, same result, ran the 'restore' button again, rebooted same result.

also when mine errors it says "mount: special device /dev/hda does not exist" vs "/dev/scd0" like agisfox's

---

### Post by agisfox on 2007-10-19
Since the block device /dev/scd0 indeed didn't exist, I created it - 22 appears to be the correct major device #, so 

"sudo mknod /dev/scd0 b 22 0" got it to start working, although with the block device /dev/hda.  (/dev/scd0 existed but didn't work).  22 is the correct major device # for the IDE CD driver which generally uses block devices on /dev/hd*, which probably explains that, although not why it kept looking for /dev/scd* (which is the SCSI block device file).

Palintheus - try "sudo mknod /dev/hda b 22 0".

Edit:
Well, the fstab line
"/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto	0	0"
probably explains the phantom device.  Wonder why it got put in there.

---

### Post by palintheus on 2007-10-20
thanks that worked to get it recognized, but when I rebooted it was gone again and had to re-run the command.

---

### Post by thomasaaron on 2007-10-22
That's strange that you would have to do it every time you boot.
Can you try it again just to confirm?

AGISFOX, do you have to run it again when you reboot?

---

### Post by palintheus on 2007-10-22
> **thomasaaron said:**
> That's strange that you would have to do it every time you boot.
Can you try it again just to confirm?

AGISFOX, do you have to run it again when you reboot?

Well I am currently doing a clean install to see if that fixed some of my issues that others with daru2's said worked. But will post my results when I can.

---

### Post by palintheus on 2007-10-22
I just reinstalled from an alt cd and this issue is no longer present for me.

---

### Post by agisfox on 2007-10-22
Yes, I need to recreate the node whenever I restart.

---

### Post by zacharydanger on 2007-11-10
I just noticed I'm having the same problem with my daru2 after upgrading from 7.04 to 7.10. I ran the system restore from the System76 driver and that hasn't fixed it. Is there a solution to this problem that doesn't require wiping my machine and doing a fresh install?

---

### Post by palintheus on 2007-11-10
> **zacharydanger said:**
> I just noticed I'm having the same problem with my daru2 after upgrading from 7.04 to 7.10. I ran the system restore from the System76 driver and that hasn't fixed it. Is there a solution to this problem that doesn't require wiping my machine and doing a fresh install?

not sure its been explored much since upgrades have shown to cause several random errors with this, sound, and others found in the forum.

---

### Post by thomasaaron on 2007-11-12
> I just noticed I'm having the same problem with my daru2 after upgrading from 7.04 to 7.10. I ran the system restore from the System76 driver and that hasn't fixed it. Is there a solution to this problem that doesn't require wiping my machine and doing a fresh install?

The problem is related to Update Manager. It hosed sound and CD's for a lot of computers (not just System 76 computers). We've been able to come up with a fix for the sound now that does not require re-imaging.

Unfortunately, we've not been able to find a fix for the CD drive. I'll try to work on it some more this week.

One idea might be to automatically run a script that creates the node on start-up. But that is definitely a hack solution.

If you decide to re-install, though, send me an email at support. I have directions that should prevent ending up in the same boat again after re-installing.

---

