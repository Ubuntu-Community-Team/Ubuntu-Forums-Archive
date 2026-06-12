---
title: "Driver not loading for Intel integrated graphics getting gallium"
date: 2014-07-11
forum: Server Platforms
---

### Post by patrick50 on 2014-07-11
Hello smart people!

I am a rookie on this newfangled linux stuff...

I am having a problem with the right drivers not loading for my graphics system( Intel Integrated in a Xeon E-3- 1245V3 Haswell), as a result I am being forced to use some kind of automatic workaround called "Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)" needless to say it looks horrible (and yet at least it works)!

I'm running Ubuntu 14.04 LTS (pangolin?)

I have been what feels like all over with this thing and (probably stupidly) tried almost any command I could find to solve it.

Here is what I think I have tried (it gets a bit hazy so bear with me):

Loading intel drivers from intel
... I know  I have tried other stuff but it's not ringing a bell at the moment (remember I'm new to this whole thing) to be honest I was just happy to get it going and get my drives working in some fashion.

if anyone has any logs or anything they think would be helpful I'd be happy to get them.

Thanks folks!

---

### Post by oldfred on 2014-07-11
See also this:
[https://www.centos.org/forums/viewtopic.php?f=15&t=46432](https://www.centos.org/forums/viewtopic.php?f=15&t=46432)

Intel only has the one open source driver. And it should be in your install.

But Intel is always updating it as well as kernel & support software. So often just attempting to install a very new Intel driver just released that is not in Ubuntu yet can lead to even more issues.

This site tests new kernels and drivers, but it uses ppa or tests newer Ubuntu like 14.10 that may have newer drivers.
       Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)
Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

    
If you have 10 to 20GB of hard drive space you could just install 14.10. It may not work all the time as it still is early but then you would have a better idea if the new drivers help. And then you could install newer drivers with ppa into main working install (after good backups just in case). 

You can test these boot options just at grub menu and add in place of quiet splash. Change example 1280x1024 size to your correct sizes.
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

What does this show?
 For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by patrick50 on 2014-07-11
Hello oldfred,

I ran the stuff that the other forum talked about "lspci" and the results are missing a mention of the graphics card.

redbearded@redbearded-X10SLH-F-X10SLM-F:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3 Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.1 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #2 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C226 Series Chipset Family Server Advanced SKU LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Chipset Family Thermal Management Controller (rev 05)
03:00.0 PCI bridge: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 03)
04:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 30)
05:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
06:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)

as for updating the kernel to 14.10 I fear that is above my pay grade so to speak.

I ran the commands that you suggested and these were the results

redbearded@redbearded-X10SLH-F-X10SLM-F:~$ sudo apt-get install intel-linux-graphics-installer
[sudo] password for redbearded: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
intel-linux-graphics-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
redbearded@redbearded-X10SLH-F-X10SLM-F:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
redbearded@redbearded-X10SLH-F-X10SLM-F:~$ glxinfo | grep OpenGL | head -n3
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string: 2.1 Mesa 10.1.3
redbearded@redbearded-X10SLH-F-X10SLM-F:~$


I hope that this is what you were looking for, and I thank you for the assistance.

---

### Post by oldfred on 2014-07-11
That is not Intel video, but some old video card that I have never heard of.

VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family
This says it is not just video but more and not really well supported, but you may be able to download drivers from Aspeed or use some very old nVidia driver.
[http://ubuntuforums.org/archive/index.php/t-2133196.html](http://ubuntuforums.org/archive/index.php/t-2133196.html)

---

### Post by patrick50 on 2014-07-12
Hi again oldfred,

ya that was a bit confusing to me as well, the specs for the computer are as follows below. BTW this is server(Supermicro X-10slh-f) hardware new and running a 15TB ZFS array, i'm not sure if that has any thing going on, but that stuff I have managed to get going very well so far. it's goofy stuff like the networking and the display drivers that are futzing up at the moment. They are not really causing any unlivable problems but this machine is my first linux box and I want to figure stuff like this out if I can.

Again I really appreciate the help, i feel like a fish out of water on this linux stuff (you should have seen me scrambling when the GUI locked up and ctrl-alt-del did not do a thing, lol)

[TABLE]
[TR]
[TD="class: stitle, colspan: 2"]Summary
[TABLE]
[TR]
[TD="class: field"]Date[/TD]
[TD="class: value"]07/19/2013[/TD]
[/TR]
[TR]
[TD="class: field"]Vendor[/TD]
[TD="class: value"]American Megatrends Inc. ([www.ami.com](www.ami.com))[/TD]
[/TR]
[TR]
[TD="class: field"]Version[/TD]
[TD="class: value"]1.1[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Board[/TD]
[/TR]
[TR]
[TD="class: field"]Name[/TD]
[TD="class: value"]X10SLH-F/X10SLM+-F[/TD]
[/TR]
[TR]
[TD="class: field"]Vendor[/TD]
[TD="class: value"]Supermicro[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Computer[/TD]
[/TR]
[TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]8x Intel(R) Xeon(R) CPU E3-1245 v3 @ 3.40GHz[/TD]
[/TR]
[TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]16392MB (11080MB used)[/TD]
[/TR]
[TR]
[TD="class: field"]Operating System[/TD]
[TD="class: value"]Ubuntu 14.04 LTS[/TD]
[/TR]
[TR]
[TD="class: field"]User Name[/TD]
[TD="class: value"]redbearded (Patrick Callahan)[/TD]
[/TR]
[TR]
[TD="class: field"]Date/Time[/TD]
[TD="class: value"]Sat 28 Jun 2014 03:01:00 PM PDT[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Display[/TD]
[/TR]
[TR]
[TD="class: field"]Resolution[/TD]
[TD="class: value"]1920x1080 pixels[/TD]
[/TR]
[TR]
[TD="class: field"]OpenGL Renderer[/TD]
[TD="class: value"]Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)[/TD]
[/TR]
[TR]
[TD="class: field"]X11 Vendor[/TD]
[TD="class: value"]The X.Org Foundation[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Multimedia[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Input Devices[/TD]
[/TR]
[TR]
[TD="class: field"]Power Button[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Power Button[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Logitech USB Receiver[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Logitech USB Receiver[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]HID 0557:2419[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]HID 0557:2419[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Logitech Unifying Device. Wireless PID:4102[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Printers[/TD]
[/TR]
[TR]
[TD="class: field"]No printers found[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]SCSI Disks[/TD]
[/TR]
[TR]
[TD="class: field"]ATA Samsung SSD 840[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]ATA WDC WD40EFRX-68W[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]ATA WDC WD40EFRX-68W[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]ATA WDC WD40EFRX-68W[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]ATA WDC WD40EFRX-68W[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]ATA WDC WD40EFRX-68W[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Initio INIC-1610P[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: field"]Host bridge[/TD]
[TD="class: value"]Intel Corporation Xeon E3-1200 v3 Processor DRAM Controller (rev 06)[/TD]
[/TR]
[TR]
[TD="class: field"]PCI bridge[/TD]
[TD="class: value"]Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])[/TD]
[/TR]
[TR]
[TD="class: field"]PCI bridge[/TD]
[TD="class: value"]Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06) (prog-if 00 [Normal decode])[/TD]
[/TR]
[TR]
[TD="class: field"]USB controller[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])[/TD]
[/TR]
[TR]
[TD="class: field"]Communication controller[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)[/TD]
[/TR]
[TR]
[TD="class: field"]Communication controller[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #2 (rev 04)[/TD]
[/TR]
[TR]
[TD="class: field"]USB controller[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])[/TD]
[/TR]
[TR]
[TD="class: field"]PCI bridge[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])[/TD]
[/TR]
[TR]
[TD="class: field"]PCI bridge[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])[/TD]
[/TR]
[TR]
[TD="class: field"]PCI bridge[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])[/TD]
[/TR]
[TR]
[TD="class: field"]USB controller[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])[/TD]
[/TR]
[TR]
[TD="class: field"]ISA bridge[/TD]
[TD="class: value"]Intel Corporation C226 Series Chipset Family Server Advanced SKU LPC Controller (rev 05)[/TD]
[/TR]
[TR]
[TD="class: field"]SATA controller[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])[/TD]
[/TR]
[TR]
[TD="class: field"]SMBus[/TD]
[TD="class: value"]Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)[/TD]
[/TR]
[TR]
[TD="class: field"]Signal processing controller[/TD]
[TD="class: value"]Intel Corporation 8 Series Chipset Family Thermal Management Controller (rev 05)[/TD]
[/TR]
[TR]
[TD="class: field"]PCI bridge[/TD]
[TD="class: value"]ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 03) (prog-if 00 [Normal decode])[/TD]
[/TR]
[TR]
[TD="class: field"]VGA compatible controller[/TD]
[TD="class: value"]ASPEED Technology, Inc. ASPEED Graphics Family (rev 30) (prog-if 00 [VGA controller])[/TD]
[/TR]
[TR]
[TD="class: field"]Ethernet controller[/TD]
[TD="class: value"]Intel Corporation I210 Gigabit Network Connection (rev 03)[/TD]
[/TR]
[TR]
[TD="class: field"]Ethernet controller[/TD]
[TD="class: value"]Intel Corporation I210 Gigabit Network Connection (rev 03)[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-07-12
Moved to server sub-forum.

I do not know servers nor any drive format other than ext4. 

Do not use ctrl-alt-delwith Linux. You want to try to shutdown what is running or else you may corrupt drives and then have bigger issues. Remember the Elephants.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by SeijiSensei on 2014-07-13
Apparently the graphics card is supported:  [http://www.ubuntu.com/certification/catalog/component/pci/1a03%3A2000/](http://www.ubuntu.com/certification/catalog/component/pci/1a03%3A2000/)

Google still points to the company's website for drivers, but it appears that the company itself is no more.  While there is still a "whois" entry for aspeedtech.com, there are no nameservers for the domain so attempts to connect to [www.aspeedtech.com](www.aspeedtech.com) fail.

Perhaps you can find a driver at Supermicro: [http://www.supermicro.com/support/resources/](http://www.supermicro.com/support/resources/)

---

