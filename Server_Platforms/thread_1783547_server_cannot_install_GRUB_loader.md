---
title: "server cannot install GRUB loader"
date: 2011-06-15
forum: Server Platforms
---

### Post by Mookinator on 2011-06-15
Trying to install 11.04 64bit Server onto my machine. 
First try from USB stick failed because the installer couldn't continue without a CDROM present. fine, whatever, dust off the old CD drive and install from it.

Second and subsequent tries have failed because the installer gets to the point of installing the GRUB bootloader to the hard drive and fails. I cannot install it to any of the drives in the system, nor will it boot when using the 'boot from first harddrive' option while booting from the CD drive. This is just a regular SATA drive on the board. (no RAID or anything) Thanks.

[img]http://www.halfahemi.com/pics/GRUBfail.jpg [/img]

~Mike

---

### Post by TechSupportx86 on 2011-06-15
Does the drive have any other OS/Bootloader on it? (ubuntu, Windows, ect). Sometimes i need to burn 1-2 discs because something gets ****ed up while burning (At the fault of the CD Burner) or the download (again) gets ****ed up. 

Try re-downloading the ISO, then burn at about 4x speed. should take about 2 minutes to burn at a slower speed, but then it *should* work. If using windows built-in ISO burner, click "Verify after burning" (Vista/7).

---

### Post by garvinrick4 on 2011-06-15
Do you have a basic drive with an mbr or is it formatted something microsoft specific.

---

### Post by YesWeCan on 2011-06-22
Have you solved this yet?
If not, a look at your disks may give some clues. Using your live CD would you download [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post the RESULTS.txt here.

I didn't know the live USB would not boot without a CD drive installed. That's not very helpful.

---

### Post by brobeans on 2013-01-11
Hello there,

I've actually had the same error installing 12.04 LTS just yesterday. 

I was wondering if you had any luck resolving the issue?

The OS installed correctly for me, but the issue is with the grub bootloader still.

I was wondering, because I had 2 physical drives in RAID1 and I'm trying to install the bootloader there, would this cause an issue installing to /dev/sda? 

Many thanks!

---

### Post by dlaihk on 2013-03-12
I experienced the same.  11.04 64bit Desktop was installed with no problem with one hard disc.  But after setting to two identitcal hard disc and RAID 1 configuration, installation failed with the same situation reported by Mookinator.

---

### Post by LHammonds on 2013-03-12
When y'all said RAID, are you talking about a RAID configuration @ the BIOS from the motherboard (fakeraid) or using a RAID card or using software for RAID?  Be sure to clarify what you are using since it makes a big difference in troubleshooting.

I never use Fakeraid or software raid and have installed 10 and 12 LTS server with no issues with GRUB in single or multi-drive systems.  (just giving an FYI on my experience)

LHammonds

---

