---
title: "Partitions, HDDs, Windowses (lol)... repartition and boot"
date: 2016-07-03
forum: Windows
---

### Post by Mellatau on 2016-07-03
Hello, I'm here with a wired question again :D
Here's the situation: laptop with legacy BIOS and two HDDs; the 2nd (second) HDD contains Windows 10 (owner - dad; must not touch it), the first one was used to play with Linuxes; a while ago decided to settle with Win8.1 + Mint. So I installed Windows and now want to install Mint... and here is **the problem**: when I installed Win8.1 it seems like its loader is somehow ended up in the 2nd HDD where Win10's one is. Here's why I think so: BIOS is set to boot 1st HDD first and it says that "OS is not found..." so I press esc and the 2nd HDD boots; there after some time I see a blue screen with two boot options (Win10 and Win8.1) and some "preferences"; if Win10 option is selected the said Win10 will (continue to) boot as if nothing happened, and if Win8.1 is selected the laptop reboots and still shows the "OS is not found..." message but when I press esc again it boots straight into Win8.1...
And so **here's the REAL problem :D** I want to shrink the Windows' partition a bit AND move it to the right (is my guess about the right side being the center of HDD right? ) leaving the faster part of hard drive for Linux. So *the core of the problem* (...) is about Win8.1 and its ability to boot after I rape its partition and shove Linux beside it; and if ability turns to inability, how to get rid of the "in-" prefix?
Thank You.

---

### Post by oldfred on 2016-07-03
Moved to Windows sub-forum.
Really better to ask on Windows forum.

But Windows in BIOS boot mode only boots from one primary NTFS partition with boot flag and drive set as default during install as BIOS boot drive.

So when you installed second copy of Windows your other drive was default boot and you installed your boot loader over the boot loader install in that drive.

Do not think this mentions BIOS setting on boot drive, but otherwise explains Windows BIOS booting regardless of version of Windows.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html) 

Do not move start of Windows. And any resize of Windows must be done using Windows tools & reboot immediately to run chkdsk.
Newer drives and difference in rotational speed will not be noticeable. If you want to improve speed invest in a SSD.

---

