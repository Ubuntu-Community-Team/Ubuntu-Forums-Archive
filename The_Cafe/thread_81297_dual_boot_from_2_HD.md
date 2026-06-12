---
title: "dual boot from 2 HD"
date: 2005-10-24
forum: The Cafe
---

### Post by comradevik on 2005-10-24
i have windows xp on my hda - primary hard drive and 
ubuntu on my hdb slave drive

now i rly need to get windows onto another computer.. if i put my windows hard drive on the other computer and do a system restore , would i get windows taht way?

---

### Post by taavi on 2005-10-24
This really isn't Windows support forum, but I can suggest something from my own experience. Windows is not very tolerating if the base hardware like motherboard (especially chipset) changes. Usually it can't handle that and you have to reinstall whole Windows (maybe repair install helps, I don't know).

Are there any Linux/Ubuntu specific problems here?

---

### Post by SilentCacophony on 2005-10-24
As taavi mentioned, just popping a drive with Windows installed into another computer with different hardware will probably cause it to fail on bootup. A fresh install would probably be in order.

Another thing to consider is if you had installed grub to the mbr of the first drive when you installed ubuntu. If so, then you'd have to restore grub to the mbr of the second drive (see [this]("http://ubuntuforums.org/showthread.php?t=76652") thread.)

---

### Post by WildTangent on 2005-10-24
In order to do that, you must repair the windows installation after putting it into another computer. This reinstalls the base OS, without overwriting your files, or the registry, so your programs will still work. In the future, you should avoid asking questions like these, its a) not an Ubuntu problem, and b) in the wrong forum. What *will* be an Ubuntu problem will be what happens when you take the hda drive out, as this is the default location for the Grub bootloader. If you take it out, you won't be able to boot Ubuntu.

-Wild

---

### Post by Mr_J_ on 2005-10-24
I didn't read everything.

Dude! Windows will not work if you change the motherboard.
If the pc is exactly the same in terms of motherboard it might work barely.
The problem will be fixing all the errors that will probably show up.
The mobo is the most important part of the switch.

If the computer is totaly diferent, then you may get it to boot, but an onslaught of errors will fill your day. Format will be required after, at least to make the system function properly.

All this is stuff I heard. I have never ever done what you speak of.
I do not recomend what you speak of. Windows is still very very crude in that sort of thing. It is not made for such switches lightly, and from what I heard it should not work.

---

