---
title: "Precise server install to adaptec AIC7902 SCSI RAID1 -No os after install"
date: 2012-04-30
forum: Server Platforms
---

### Post by pwhalley on 2012-04-30
I am hoping someone here can shed a little light.

I have an IBM E server 226 with 2 - 36G ultra 320 SCSI disks connected to the second AIC7920 in the system.  I have a 1TB SATA drive for /Home. I have had 10.4 installed and working (I use the term loosely)in a RAID1 config but had some problems early on and ended up pulling one of the drives and running in degraded mode for a long time (more than 1 year?). This is a single boot server. No other OS is or will be installed.

I decided to start over and now am trying to install Precise on the system and have had minimal success.  I started with smartraid on in adaptec firmware and pairing the two drives in a  RAID1 config.  Then I installed OS. When install is complete and I reboot, I get OS not found errors. I tried using boot repair from here [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)  without success.

I even tried installing on one drive (no raid) and then going into the adaptec bios and setting up raid 1 after install.  The BIOS seems to allow me to specify one drive as the one 'reference' drive to copy from when building the other drive.  I also tried with and without specifying this RAID1 as bootable in BIOS. After trying to undo the RAID1, which the BIOS appears to allow. Select delete RAID option then it offers choice of both, 1 or the other. After this, I still can't boot but using recover option on server install I can see all files on drive I specified to be left alone.

 I also am thinking to use the RAID1config (fastest drives in system for capture buffer for OTA broadcasts) for any transient storage(faster drives for capture buffer for OTA broadcasts).  If OS, swap and temp files won't fit in 30 G then I would need to overflow to sata or re-think config. Pointers to good info on capture buffer setup would be nice but are not my focus. Though it might be less trouble to set up space for it now which is why I mention it.

So, I am looking for one of two solutions.
1.Understand how to make RAID1 work and install reliably with this hardware that won't break with updates or upgrades.
2.Do single disk non RAID install AND have some automatic easy to use way to periodically (weekly) generate an image or backup of the working drive and an equally simple way to restore that image to the replacement drive once a failure occurs - and that dosen't take 4 or 5 hours to run to completion and then tell me the restore failed.

If 2 is the route I go, i would like some opinions on what is the smallest I should make the OS partition - 12G? Naturally, smaller images are easier to store...

If I recall correctly in this context it is not necessary to use GRUB and I dont see GRUB installed.

Hopefully I can get some good direction in next 24 Hrs. and just fix boot to drive that should be gtg otherwise.

Thanks to all who read and double to those with a solution.

Peter

---

### Post by pwhalley on 2012-05-03
bump... anyone?

---

