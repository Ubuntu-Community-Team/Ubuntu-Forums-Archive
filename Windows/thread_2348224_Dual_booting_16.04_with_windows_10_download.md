---
title: "Dual booting 16.04 with windows 10 download"
date: 2017-01-01
forum: Windows
---

### Post by narev2 on 2017-01-01
Hi,
I'm newish to Ubuntu, and due to a personal crisis I lost my laptop, and was given a hand me down pc that was clogged with viruses. I chose to wipe the thing and start over, loading Ubuntu first, getting rid of all old partitions. I want to download the Windows 10 upgrade, as I only have copies of Win XP and 2000 (for some reason) available to me. The problem is, I simply cannot get any windows to install itself. I have tried making an NTFS partition for it, and tried letting it have lots of open space to create its own partition. Each time I attempt to install by booting off the dvds, it gets into setup fine, loads its drivers for setup, then crashes when it says "Loading windows environment". I haven't worked on PCs seriously in some time, and am a novice with Ubuntu. Is there something I'm overlooking?

-Rob

---

### Post by Irihapeti on 2017-01-01
*Thread moved to **Windows***, as it's mostly about installing Windows.

---

### Post by oldfred on 2017-01-01
How old is computer. Or UEFI or BIOS.
If before about 2012 will be BIOS.
With BIOS the NTFS partition must be a primary partition with the boot flag.
And BIOS must have MBR(msdos) partitions with the 4 primary partition limit. Ubuntu works fine from logical partitions, but Windows must install & boot from a primary. 

 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)

---

### Post by gordintoronto on 2017-01-02
What Windows 10 upgrade are you talking about? Up until six months ago, there was a free upgrade from Windows 7 or 8, but that is long gone, and didn't apply to the versions of Windows you have.

Is there some Windows application which you require, or can Ubuntu meet your needs?

---

