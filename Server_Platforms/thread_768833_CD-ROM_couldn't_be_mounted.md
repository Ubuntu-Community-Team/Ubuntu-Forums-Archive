---
title: "CD-ROM couldn't be mounted"
date: 2008-04-26
forum: Server Platforms
---

### Post by bmwarner88 on 2008-04-26
I use UbuntuStudio as my desktop and decided it was time to setup my own web server. I downloaded ubuntu-8.04-server-amd64 and tried to install on my new Dell server, but got this error after selecting keyboard options in the setup.

"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again."

I found a similar post here: [http://ubuntuforums.org/showthread.php?t=2988](http://ubuntuforums.org/showthread.php?t=2988)
and here:
[http://ubuntuforums.org/archive/index.php/t-2988.html](http://ubuntuforums.org/archive/index.php/t-2988.html)

But I don't have an extra CD-ROM drive to switch with it. I tried the F6 option and adding "ide=nodma" to the end of the install string, but it didn't work (not sure if I was doing this right though).  If anybody has any suggestions, please let me know!

Dell PowerEdge T105
Dual Core 1212 Processor 2.0GHz Opteron
(2) 250GB 7.2K RPM SATA
16X SATA DVD Drive

---

### Post by nanog on 2008-04-27
I had this same problem. My solution was to move the hard drive to another computer and install. Worked like a charm on two T105s. Other solutions I've seen are to make a bootable iso on a USB drive. Search around.

---

### Post by bmwarner88 on 2008-04-27
Unfortunately my server is AMD64 and my desktop isn't, so it won't let me install the ubuntu-8.04-server-amd64 when I put one of the server hard drives in one of my desktops. i'll try the bootable usb drive.

---

### Post by mrtchandler on 2008-05-28
How much memory do you have installed?

The reason I ask, is Dell has a app note for the SUSE install.  Text at the bottom of this reply, basically it appears to be a memory addressing issue if the 1st module is a 2 GB module.

Information Update
Memory Module Installation Guidelines
The following information updates the memory module installation
guidelines in your Hardware Owners Manual.

 If only DIMM_1 is installed in your system, its capacity must be 512 MB
or 1 GB. A single 2-GB DIMM installation is not supported.

SATA Optical Drive Support in SUSE Linux
The SATA optical drive does not work with SUSE® Linux Enterprise Server
10-Service Pack 1(SLES10-SP1) on the Dell® PowerEdge® T105 system with
more than 4 GB of system memory.
The SATA optical drive connected to the SATA controller is not recognized
during and after installation because of an issue with the sata_nv driver. A fix
for this issue will be available in a future service pack.
To work around this issue, you must load the sata_nv driver with the adma
mode disabled during boot-up.
Add the following text to the kernel line in the /boot/grup/menu.1st file
sata_nv.adma=0
The following is an example of the menu.1st file:
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda2 vga=0x317
resuem=/dev/sda1 splash=silent showopts
sata_nv.adma=0
initrd /boot/initrd

---

### Post by mrtchandler on 2008-05-28
A temporary solution to perform the install, is to limit the memory to 4G, do the install, on reboot after install the DVD drive will not be available due to the bug in the Kernel, with greater than 4G of RAM.  Hopefully the bug will get fixed it is known about, and an Ubuntu update will include a patched kernel with a fix for the SATA ATAPI issue on sata_nv module 32 bit DMA.

By the way to limit the memory, boot the 64 bit DVD install, and press F6 at install time, and append mem=4G to the install line.

---

