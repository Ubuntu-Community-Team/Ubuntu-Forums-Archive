---
title: "Wine and Silverfast scanner software"
date: 2009-12-14
forum: Wine
---

### Post by Bryan.Smith on 2009-12-14
I am attempting to wine version 1.1.31 using Ubuntu 9.10 (64 bit) to run Silverfast SE scanner software to access an Epson V700 scanner.  When I attempt to run I get an error "There was no scanner found.  Check that Your scanner is properly connected to your computer and is switched on . . . ".  I can use the linux application xsane to successfully access the scanner so the scanner is alive and well.

When running from the command line I get the following output.

[FONT=Courier New]wine "C:\Program Files\LaserSoft\SilverFast Epson\SF Launcher.exe" 
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:sti:stillimagew_GetDeviceList (0x19d438, 0, 0x0, 0x982674, 0x982670): stub
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
fixme:aspi:SendASPI32Command Unknown command 7[/FONT]

My video card is the Radeon HD 5750 using drives downloaded from the ATI site.  (The video drivers available through Ubuntu are problematic.).

I can find nothing in the wine application database regarding silverfast.

---

