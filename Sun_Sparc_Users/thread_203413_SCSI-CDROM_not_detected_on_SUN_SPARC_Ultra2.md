---
title: "SCSI-CDROM not detected on SUN SPARC Ultra2"
date: 2006-06-25
forum: Sun Sparc Users
---

### Post by Haigern on 2006-06-25
Hi Ubuntu-Fans,

When trying to boot ubuntu-6.06-server-sparc.iso from a SCSI-CDROM, I get the installation started properly until hardware detection. Though SILO can access the SCSI-CDROM, hardware detection of ubuntu-6.06 doesn't detect the CDROM at all. Continuation of the installation process is not possible.

How can I get the SCSI-CDROM being detected and used ?

The same hardware is booting correctly SUSE-7.3 SPARC.

Best regards,

Ewald

---

### Post by archetypo on 2006-06-25
[QUOTE=Haigern]Hi Ubuntu-Fans,
 hardware detection of ubuntu-6.06 doesn't detect the CDROM at all. Continuation of the installation process is not possible.
[/QUOTE]

Ewald-

Installing 6.06 on the Ultra 2 is tricky, but it can be done and will work.  Strap on your seat-belt, this was really annoying to figure out and configure.

When you get to the CDROM error, hit ALT+F2 to bring up a new shell and type: modprobe esp

Hit ALT+F1 to go back and the install should continue normally.

Everything will go fine until it's time to reboot.  At that point, you will get a timeout error at boot and see /dev/sda2 not found.

Reboot again using the original cd into the rescue mode.  Mount the /dev/sda2 disk and you should see your files.  Next type: mount /dev/sda1 /boot

So, basically, you have to modify a file and create a new initrd.img in /boot

1) In /etc/mkiniramfs/modules add this line: esp
(sudo nano modules, then ctrl-x to save)
2) Backup /boot/initrd.img-2.6.15-25-sparc64-smp to initrd.img-2.6.15-25-sparc64-smp.back
3) Rebuild a new initrd.img with the command mkinitramfs -o /boot/initrd.img-2.6.15-25-sparc64-smp.  If it complains about the lib module, what you have to do is add the FULL PATH to the lib module INCLUDING THE "-smp" part!
4) When this is done, look in /boot and make sure the new initrd.img is 40K or so larger than the old one.

Reboot and voila!

---

### Post by netztier on 2006-06-26
[QUOTE=Haigern]How can I get the SCSI-CDROM being detected and used ?
[/QUOTE]

You need the **esp** (the SCSI driver) module in the initrd-kernel, as pointed out above. See also this thread: [Trouble with Sun Ultra 2]("http://ubuntuforums.org/showthread.php?t=166882&highlight=esp+mkinitramfs")

Probably also useful: this thread with a bit of info about using Creator cards: [sparc64 Sun Ultra 10 Good ISO?]("http://www.ubuntuforums.org/showthread.php?p=955542#post955542")

kind regards

Marc

---

### Post by Haigern on 2006-06-26
[QUOTE=archetypo]Ewald-

Installing 6.06 on the Ultra 2 is tricky, but it can be done and will work.  Strap on your seat-belt, this was really annoying to figure out and configure.

When you get to the CDROM error, hit ALT+F2 to bring up a new shell and type: modprobe esp

Hit ALT+F1 to go back and the install should continue normally.

Everything will go fine until it's time to reboot.  At that point, you will get a timeout error at boot and see /dev/sda2 not found.

Reboot again using the original cd into the rescue mode.  Mount the /dev/sda2 disk and you should see your files.  Next type: mount /dev/sda1 /boot

So, basically, you have to modify a file and create a new initrd.img in /boot

1) In /etc/mkiniramfs/modules add this line: esp
(sudo nano modules, then ctrl-x to save)
2) Backup /boot/initrd.img-2.6.15-25-sparc64-smp to initrd.img-2.6.15-25-sparc64-smp.back
3) Rebuild a new initrd.img with the command mkinitramfs -o /boot/initrd.img-2.6.15-25-sparc64-smp.  If it complains about the lib module, what you have to do is add the FULL PATH to the lib module INCLUDING THE "-smp" part!
4) When this is done, look in /boot and make sure the new initrd.img is 40K or so larger than the old one.

Reboot and voila![/QUOTE]

Thanks a lot. Your guideline was perfect. My SUN Sparc Ultra2 is booting Ubuntu !

Best regards,

Ewald

---

### Post by gevans on 2006-07-10
These instructions also worked (with very slight modifications) for an Ultra 1 :)

The modifications being only that there was no -smp after my initrd.img

---

