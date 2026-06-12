---
title: "Possible Request: Beagle."
date: 2005-05-11
forum: Ubuntu Backports
---

### Post by TravisNewman on 2005-05-11
I've heard talk that Beagle is now in the Breezy repos. How much hell would you have to go through to get it backported?

---

### Post by thechitowncubs on 2005-05-11
since he got mono updated i don't think it would be that hard but who knows maybe i'm stupid

 :-?  :---)  :---) ??

---

### Post by Amaranth on 2005-05-11
[QUOTE=panickedthumb]I've heard talk that Beagle is now in the Breezy repos. How much hell would you have to go through to get it backported?[/QUOTE]
 Well, beagle sucks hard if you don't have a kernel with inotify. The one in Ubuntu's 2.6.10 is too old and hoary's 2.6.11 is actually an unstable pull from BitKeeper before the 2.6.11 release (it's buggy).

---

### Post by TravisNewman on 2005-05-11
Heh. Well. No point then, yet ;)

---

### Post by Knome_fan on 2005-05-12
[QUOTE=Amaranth]Well, beagle sucks hard if you don't have a kernel with inotify. The one in Ubuntu's 2.6.10 is too old and hoary's 2.6.11 is actually an unstable pull from BitKeeper before the 2.6.11 release (it's buggy).[/QUOTE]

Hm, beagle runs just fine without inotify now, at least it does for me, so I don't really see a problem here.

---

### Post by RastaMahata on 2005-05-12
[QUOTE=Amaranth]Well, beagle sucks hard if you don't have a kernel with inotify. The one in Ubuntu's 2.6.10 is too old and hoary's 2.6.11 is actually an unstable pull from BitKeeper before the 2.6.11 release (it's buggy).[/QUOTE]
 what's inotify, and why is it needed? :(

---

### Post by Amaranth on 2005-05-12
[QUOTE=RastaMahata]what's inotify, and why is it needed? :([/QUOTE]
 I don't know if you've heard how Spotlight in OS X Tiger works so I'll explain in their terms. When a file or dir is modified the kernel notifies Spotlight (or anything else listening) about the change. This is what inotify does with linux. Without it beagle has to manually index your HD (slow and resource killing) and won't update right away when you change files (because without inotify it doesn't know about the changes).

---

### Post by Knome_fan on 2005-05-12
"Without it beagle has to manually index your HD (slow and resource killing) and won't update right away when you change files (because without inotify it doesn't know about the changes)."

Sorry to be so anal about it, but that's not true either. I don't know how they do it technically, but beagle indexes my stuff right away even without inotify. And the beagle devs claim that inotify is the more elegent solution, not that it's the only solution.

---

### Post by tcamargo on 2005-05-12
From [Beagle documentation](http://www.beaglewiki.org/index.php/inotify-Enabled%20Linux%20Kernel):

"Beagle now requires the inotify option in the Linux kernel to be enabled. As of yet, this feature hasn't been included with stable kernel releases, but there are options depending on your distribution. (...)"

I did not use Beagle, so...

---

### Post by Knome_fan on 2005-05-12
[quote="beaglewiki"]
4. Inotify - CAUTION (NOT RECOMMENDED)

If you are using Beagle 0.0.8 or you have build your own kernel with inotify 0.21, you can enable inotify kernel support. You must have Hoary Final Release with the latest kernel installed as this is when inotify 0.18 support was added.PLEASE NOTE: When I enabled inotify, it broke my USB plug and play support so I wouldn't enabled it. It just means that you will loose some performance! This is a GNOME bug which should be fixed soon. I would recommend you DO NOT enable inotify until the bug is sorted. 
[/quote]
[http://www.beaglewiki.org/index.php/UbuntuInstall](http://www.beaglewiki.org/index.php/UbuntuInstall)

And believe me, it works like a charm without inotify here.

---

