---
title: "[SOLVED] VMWare won't boot virtual machine"
date: 2007-11-09
forum: Virtualisation
---

### Post by Excalibre on 2007-11-09
So I installed VMWare last night from the binary installer on their website, and that went without a hitch. (I'm running Gutsy 64-bit.) And then I created a virtual machine. But when I tried to power it on, the window just went black for about two seconds and then it powered off. It's like my virtual motherboard is fried.

I thought it was maybe failing to connect to my cd drive so I tried every possibility (different settings for the cd, in case the autodetect didn't work, booting from a cd image, booting from a floppy image) but nuthin'.  Later I looked at someone else's setup and realized that it hadn't even gotten as far as trying to boot from a cd - the whole normal boot sequence, starting from the VMWare logo - failed to happen, so it's clearly not about not attaching to the drive.

Anyone else have this problem? Any ideas? I'd really like to use VMWare but it's not cooperating at all.

---

### Post by Excalibre on 2007-11-09
Figured it out. In case anyone else needs this information, it happened because I installed the VM on my large NTFS partition instead of on an EXT3 partition.

ETA: Also, I'll mark this thread solved when I get a moment. It turns out this website doesn't work that well with IE 5, which is the only web browser included with Win2k, which is what my VM is running . . .

---

### Post by Obscurious on 2008-08-21
This information is buttery gold. Thanks 50bagilllion Excalibre.

--Obscurious

---

