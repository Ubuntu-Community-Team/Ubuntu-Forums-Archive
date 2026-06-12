---
title: "Which Windows enterprise for dual-boot testing?"
date: 2015-02-20
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-02-20
At first blush the mods might think this is an improper question for this section of the forums, but those who know my history in regards to ubiquity testing will know that I'm for real .................... I'm not at all interested in Windows itself but I'd like to do some ongoing dual-boot/re-installation testing but I certainly have no desire to spend even one thin dime on a Windows OS.

For the tests performed [here]("http://ubuntuforums.org/showthread.php?t=2264348") and [here]("http://ubuntuforums.org/showthread.php?t=2266195") I used the 64 bit iso from here:

[http://getintopc.com/softwares/operating-systems/windows-8-1-enterprise-free-download-iso-32-bit-64-bit/](http://getintopc.com/softwares/operating-systems/windows-8-1-enterprise-free-download-iso-32-bit-64-bit/)

But it's really [bloated]("http://ubuntuforums.org/attachment.php?attachmentid=259776&d=1423274857") and I suspect that it's a goofy install because it said to expect the install to restart several times before it was complete. Maybe it's just bloat - who knows :confused:

It even [seems to be growing]("http://ubuntuforums.org/attachment.php?attachmentid=260111&d=1424468544") so I almost feel like I have The Incredible Blob installed next to my Ubuntu :lolflag:

So I've been doing some reading and it seems that if I download [the real deal]("http://www.microsoft.com/en-us/evalcenter/evaluate-windows-8-1-enterprise") once the 90 days is up it should still boot but would just shut down every hour or so. Is that true? If so that would be fine, I'll never stay in the Windows OS longer than a few minutes.

How about re-installations? I can guarantee you that I'll erase it in the process of testing - probably numerous times. And I also need to test dual-boots and re-installations/upgrades via live image on both MSDOS/non-UEFI and GPT/UEFI systems so what do you all think?

Do any of you other testers have any experience with Windows enterprise editions?

---

### Post by grahammechanical on 2015-02-20
I installed Windows 8 preview. The 90 days limit are not 90 calendar days but 90 boots. As far as I can make out. I should think that it is possible to install afresh and get another 90 day period.

Regards.

---

### Post by ventrical on 2015-02-21
> **grahammechanical said:**
> I installed Windows 8 preview. The 90 days limit are not 90 calendar days but 90 boots. As far as I can make out. I should think that it is possible to install afresh and get another 90 day period.

Regards.

Yes even with the same username(s). Plus after 90 days it still runs with some bugs and less features but it's workable.  I do not use it much because after updates it does what old xp used to do .. just take  eons to get a program started and the endless 'updates are being configured' screens.

---

### Post by sudodus on 2015-02-21
You can try both Windows 8 preview and Windows Technical Preview alias Windows 10.

---

### Post by kansasnoob on 2015-02-21
This sounds good. I'll never use Windows anyway - I'll just be making sure I don't wipe it or make it totally un-bootable. I think I'll pick up another refurb hard drive so I can have one set up as MSDOS and another as GPT so all I have to do is crack the case, switch two cables, hit F2 at startup, and change the UEFI setting in the BIOS.

---

### Post by jerrylamos on 2015-02-22
Last 4 pc's we got had Win7 on them.  They still do.

On 3 I test with ubuntu on usb hard drive or ssd usually booting from /dev/sdb.  I've had ubuntu screw things up royally !!!  multi booting from /dev/sda.
On one I squashed win7 down a bit and have ubuntu long terms on it.  For later ubuntu's use a usb ssd.

There's one action my wife uses for web site which works with firefox and certain versions of microsoft office under win7.  Libre office doesn't cut it.

When I pass the pc's on they'll still have the win7's on them.

With several partitions they are all multiboot.

---

