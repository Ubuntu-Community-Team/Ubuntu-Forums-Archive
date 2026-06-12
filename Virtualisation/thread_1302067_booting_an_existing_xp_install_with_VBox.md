---
title: "booting an existing xp install with VBox"
date: 2009-10-26
forum: Virtualisation
---

### Post by Rhetoric Camel on 2009-10-26
I used this tutorial/guide: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:
Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:
*** STOP: 0x0000007B (0xBACBF524, 0xC0000034, 0x00000000, 0x00000000)"

I'm running Sun VirtualBox Version 3.0.8 r53138

Under settings>hard disks the IDE Controller type is PIIX4. There are two other options which I have tried.
I tried enabling additional controllers, SATA (AHCI), SCAI (Lsilogic), and SCSI (BusLogic)
I enabled ACPI and IO APIC

When it loads it goes to the windows loading screen with the scrolling blue bar, and then the BSOD appears with the info above. Also when I picked a profile to load it, I picked the one labeled "Virtual" which was the copy of the main profile for windows to start up with. I wanted to use the copy as to not mess up my current version of windows.

I'm also on Ubuntu 9.04



oh and I noticed in the tutorial it says that this will ruin any chance to boot into windows natively. Is this still true to this date or is possible to run it in virtualbox and boot natively? I don't want to get this up and running to find out I can't restart my computer and boot right into windows.

---

### Post by Rhetoric Camel on 2009-10-27
well I did chkdsk /f in windows and a virus scan on every drive I have and everything has come back great. I even did a defrag just to cover all of my basis and none of it worked. I also disabled USB in virtualbox hoping that would do it and still a no go.

---

### Post by seraphimshift on 2009-11-07
I also had this error, booting natively would work just fine but instant BSOD after the XP splash screen when running in VBOX...

To solve this, I ended up going into the BIOS on my laptop (hp 6735b) and I changed "SATA Device Mode" from AHCI to IDE.  

It took a few passes at this before I had success, my initial attempt was to boot an XP slipstream install that had the AHCI support rolled in, the native install was just fine but I was getting the same stop error in Vbox. I ended up re-installing after the BIOS change, and then Vbox was able to boot my existing install.

hope that helps.

---

