---
title: "GRUB error on dual boot with Elementary OS and Windows 10"
date: 2018-09-07
forum: Ubuntu/Debian BASED
---

### Post by ccm1776 on 2018-09-07
I am having pretty much the same problem. I have windows 10 on a 2.5" SSD and I installed a new NVME drive in my m.2 slot and tried out elementary OS. When switching to a different distro I formatted my NVME and for some reason I still have a boot option in my BIOS that shows ubuntu. When I try to boot from there, just to see what happens, the minimal bash like line editing screen comes up. The part that trips me out is that the boot option says its in my 2.5" SSD, and elementary OS was never installed on that drive. I had a separate drive for elementary. I wanted to get rid of it so I found this article ([https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)) made a live usb of elementary os and I ran boot repair and it auto cancelled. Now im stuck just like you. I can boot windows no problem. Its not a big deal to have that boot option but it is annoying as hell, especially since it says its on the same drive as windows, which is what I was trying to avoid since the beginning and thats why I installed a separate NVME m.2. Any help would be appreciated.

[ATTACH=CONFIG]281010[/ATTACH]

---

### Post by DuckHook on 2018-09-07
Welcome to the forums, ccm1776

Your post has been moved to its own thread in the "Ubuntu/Debian BASED" subforum with a new title that is more relevant to your issue. Also, just a friendly reminder not to hijack threads. Although symptoms may appear similar, causes are usually different and conflating two problems just creates confusion for helpers and those seeking help. Both the OP and you deserve answers that are focused to your own specific needs.

Also, Elementary OS is not Ubuntu. Despite the fact that it is derived from Ubuntu, its developers will choose to implement many things differently. Solutions for one may not work on the other. You may wish to also ask for help on Elementary OS's forum.

---

