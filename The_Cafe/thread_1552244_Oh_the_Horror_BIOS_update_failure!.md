---
title: "Oh the Horror: BIOS update failure!"
date: 2010-08-13
forum: The Cafe
---

### Post by LowSky on 2010-08-13
I tried to update my BIOS last night and now my motherboard wont post a thing. I never had a BIOS update go bad on me before so I'm kinda angry. So much for trying to keep my processor upgrade options up to date. Hopefully MSI will honor the warranty.

Anyone else ever do a BIOS or Firmware update that bricked their equipment?

---

### Post by Frogs Hair on 2010-08-13
No , but the last update I did not install , because it provided support for a cpu I don't have. I check the release notes to see if the update will improve the performance of my hardware or operating system.

---

### Post by LowSky on 2010-08-13
> **Frogs Hair said:**
>  I check the release notes to see if the update will improve the performance of my hardware or operating system.

I was only updating it so I could upgrade my processor in the near future. Well I guess that isn't happening just yet, LOL

---

### Post by Frogs Hair on 2010-08-13
> **LowSky said:**
> I was only updating it so I could upgrade my processor in the near future. Well I guess that isn't happening just yet, LOL


I have to flash mine with an external floppy , and I don't like doing that . I picked  one of the Asus boards  that I can't use the GUI updating software for.

---

### Post by drawkcab on 2010-08-13
I never touch that stuff unless I absolutely have to.  I've been fairly lucky though.

---

### Post by chriswyatt on 2010-08-13
That's unlucky.  Is it that difficult to buy a new pre-flashed BIOS chip and fit it?  Or does it require some soldering skill?

---

### Post by KiwiNZ on 2010-08-13
Does your Board have Bios recovery mode ? It may require fiddling with a jumper to activate it.

Failing that you will probably need to send it away for repair which is usually outside of warranty as it is not a manufacturing fault.

---

### Post by JBAlaska on 2010-08-13
From MSI Site:

**BIOS Recovery Feature**

For AMI BIOS

   1. Rename the desired AMI BIOS file to AMIBOOT.ROM and save it on a floppy disk. e.g. Rename A569MS23.ROM to AMIBOOT.ROM
   2. Insert this floppy disk in the floppy drive. Turn On the system and press and hold Ctrl-Home to force update. It will read the AMIBOOT.ROM file and recover the BIOS from the A drive.
   3. When 4 beeps are heard you may remove the floppy disk and restart the computer.

For Award BIOS

   1. Make a bootable floopy disk
   2. Copy the Award flash utility & BIOS file to the said floppy disk
   3. Create an autoexec.bat with "Award_Flash_Utility BiosFilename" in the content (e.g. awdfl823K w6378vms.130)
      Sample on how to create an autoexec:
      a. On Windows, open the notepad
      b. On the notepad, write "awdfl823K w6378vms.130" (without the " ")
      c. Save the file as autoexec.bat
   4. Boot up system with the said floppy (it will take less than 2 minutes before screen comes out)
   5. Re-flash the BIOS & reboot.

---

### Post by LowSky on 2010-08-13
> **KiwiNZ said:**
> Does your Board have Bios recovery mode ? It may require fiddling with a jumper to activate it.

Failing that you will probably need to send it away for repair which is usually outside of warranty as it is not a manufacturing fault.

I'm going to try JBAlaska's posting. Who knows it might work, but finding a floppy drive is going to be annoying...

If that doesn't work and they don't approve my RMA, but I'm pretty sure they will, I'm going to have to replace a less than year old $150 motherboard. Well I guess its a good reason to pick up one of the new ones with USB3 and SATA3.

---

### Post by murderslastcrow on 2010-08-13
Hopefully an OpenBIOS will be more standard in the future. It'd be nice to have a BIOS that streamlines your setup rather than just staying so open to everything that it's slow and cumbersome.

---

### Post by cariboo on 2010-08-13
You can also create a boot cd using an imge from [here]("http://www.bootdisk.com/bootdisk.htm"), then add the files before burning. If you have a windows computer running Nero, there is a built in boot image that you can use.

I've done this several times with a CD/R or CD/RW. I use a cd becuase I very rarely have a system with a working floppy drive.

---

### Post by Zoot7 on 2010-08-13
Happened to me with the last laptop I had. I got the motherboard replaced under the warranty from Dell afterwards. What was amusing though, was the fact that the guy I spoke to over the phone suggested re-installing Windows as the first thing to do. :rolleyes:

I've also had a few failed flashs over the years with the motherboards in the machines I've built myself, although all of those had a recovery feature.

---

