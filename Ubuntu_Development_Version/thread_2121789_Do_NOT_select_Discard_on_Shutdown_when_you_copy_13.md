---
title: "Do NOT select Discard on Shutdown when you copy 13.04 .ISO to a USB Stick!"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-03-03
Do NOT select Discard on Shutdown when you copy Ubuntu 13.04 .ISO to a USB Stick! You need to create a Persistence File in order for the Desktop Version of 13.04 .ISO to Copy to a USB Stick! This most likely applies to the 12.10 Desktop as well!

---

### Post by MacUntu on 2013-03-03
Why not just do ```
sudo dd if=/path/to/iso of=/path/to/usb/drive bs=1M
```?

---

### Post by sgage on 2013-03-03
Unetbootin works fine for me, and quickly, too.

---

### Post by screaminj3sus on 2013-03-03
I've found it most reliable to use dd, and on windows I use win32diskimager

startup disk creator has been really broken ever since 12.10, its pretty ridiculous. random crashes and such when making a usb.

---

### Post by kevpan815 on 2013-03-03
That's why I am using 12.04.2's USB Start Up Disk Creator which works just fine, Thank You Very Much. There is a reason why I have more than 1 computer just to let you know. :-)

---

### Post by kevpan815 on 2013-03-03
> **MacUntu said:**
> Why not just do ```
sudo dd if=/path/to/iso of=/path/to/usb/drive bs=1M
```?

I am still NOT very good at using the Ubuntu Command Line as all of the Computer Classes that I had taken back in 2000-2003 only covered Windows 2000 Professional & Windows 2000 Server Edition at the time. Just FYI.

---

### Post by kevpan815 on 2013-03-03
I should also note that do to the Source of my Income being from Disability Benifits I am unable to go back to College and learn about Linux, otherwise the U.S. Government would most likely declare me well enough to go back to work again, believe me I would love to go back to College if I could but the source of my Income does not allow it.

---

### Post by kevpan815 on 2013-03-03
I just found the reason why Ubuntu 13.04 USB Start Up Disk Creator was attempting to create a UEFI Firmware on my USB Stick from my 2010 Dell's which do NOT have UEFI on them: The USB Stick had a GPT File System on it, most likely from while I was still using my 2010 Mac Mini before it got Broken. I used The Advanced Disk Creator in Ubuntu to change it back to Master Boot Record, the weird thing is that even with Windows 8 on my 2010 Dell's it still recognizes my USB Drive with GPT File System on it.

---

### Post by cariboo on 2013-03-03
That's because WIndows 8 uses a GPT file system. I recently had a HP all-In-One that came with Windows 8, the customer just didn't want to make the effort to learn how to use windows 8, so he asked to install Windows 7 on it. I had to remove all the windows 8 partitions, before Windows 7 would install.

---

### Post by kevpan815 on 2013-03-03
> **cariboo907 said:**
> That's because WIndows 8 uses a GPT file system. I recently had a HP all-In-One that came with Windows 8, the customer just didn't want to make the effort to learn how to use windows 8, so he asked to install Windows 7 on it. I had to remove all the windows 8 partitions, before Windows 7 would install.

It also was Preventing the USB Stick from Booting the Ubuntu Installation Setup on my two 2010 Dell's until I changed it back to Master Boot Record, by the way!

---

