---
title: "Interesting permissions on mother's macbook Pro"
date: 2012-03-11
forum: The Cafe
---

### Post by flyingsliverfin on 2012-03-11
My mom for some reason couldn't eject her sony walkman mp3 player normally by clicking the little eject button next to the device in Finder.
However, it was working fine when I went to the terminal and used the standard 'sudo umount /dev/disk1'...
I stuck it in a file, added permissions to execute, set standard app to execute with to terminal.

What scares me is that the script didn't prompt for a password to execute the script (or failed) but happily unmount the disk. I mean, isn't the 'sudo' there for a reason?

---

### Post by MarkC3pO on 2012-03-11
Does she have a password? When I had my Mac, you could choose not to have a password at all.

---

### Post by MisterGaribaldi on 2012-03-11
Not everything requires sudo. It could be your Mom's account has sufficient inherent privs to obviate the need to sudo an unmount request.

BTW, you might want to be sure all possible relevant applications are quit the next time. Something somewhere might still have an active claim on the mounted media.

---

### Post by aysiu on 2012-03-12
The Mac OS X permissions are a bit laxer. For example, if you're a sudoer, you can drag applications into the /Applications directory without a password prompt, even though it's a system directory. Most sudo commands will prompt you for a password, though.

---

### Post by Lucradia on 2012-03-12
The OP kind of reminds me what Fedora does to the CD-ROM Drive after you've installed the system and rebooted. It won't eject the disk at all until you manually shut down from outside the LiveCD.

Or how Ubuntu can't overwrite an NTFS Drive via installation. It must be first wiped clean. (And will then spam a message saying it has Partial DOS Tables and Partial GPTs... and asks if you want to treat it as GPT.)

Linux has some oddities too ;)

---

### Post by aysiu on 2012-03-12
Haven't tried Fedora in years, but Ubuntu can most certainly overwrite an NTFS drive during installation. I've done it many times over the years.

---

### Post by Lucradia on 2012-03-12
> **aysiu said:**
> Haven't tried Fedora in years, but Ubuntu can most certainly overwrite an NTFS drive during installation. I've done it many times over the years.

With the latest version of Ubuntu, it pretty much has a 50% chance to fail for me. On the mini.iso, it always fails, unless I use LILO. But if I use LILO, and then boot into Ubuntu via mini.iso, it'll throw a kernel panic, and freeze, forcing me to cold shut down or whatever.

As for the LiveCD when it fails, it will infinitely show the solid purple screen, if I change to the terminal, it will be frozen on something that's not a FAIL check or anything. Can't remember what it froze on last time honestly.

Fedora pretty much gets the installation right the first time, and often has network drivers that ubuntu doesn't have yet. I've pretty much made it my mission, no matter the computer I'm using, to boot to the live cd, wipe the entire system, or use DBAN to also wipe the MBR so that Linux won't throw GPT Warnings, etc. Usually the latter, which takes a while to do.

I can't install linux in its own partition as such. Windows has to be installed first, and then ubuntu has to try to resize the partition (this fails always on Fedora for some reason, and won't work in ubuntu's mini.iso, it will damage the Windows MBR.) I often have to resort to wubi or virtualbox if I want to install a side-by-side system.

---

### Post by Warpnow on 2012-03-12
I've overwritten an NTFS drive during an install 3-4 times on the most recent ubuntu. Never had a problem.

---

### Post by 3rdalbum on 2012-03-12
Mac OS X has very lax security. Incidentally, OS X is the only *nix that gets messed-up permissions in its filesystem and requires a special "fix permissions" function.

---

### Post by Lucradia on 2012-03-12
> **Warpnow said:**
> I've overwritten an NTFS drive during an install 3-4 times on the most recent ubuntu. Never had a problem.

Neither have I until Windows 7 and my new Western Digital Green harddrive. (It can dynamically change the spin speed from 5400 to 7200 based on usage.)

---

### Post by flyingsliverfin on 2012-03-13
> **3rdalbum said:**
> Mac OS X has very lax security. Incidentally, OS X is the only *nix that gets messed-up permissions in its filesystem and requires a special "fix permissions" function.

This is interesting :)
Does that mean OSX is also more likely to get a virus than Linux/ubuntu?

---

### Post by 3rdalbum on 2012-03-14
> **flyingsliverfin said:**
> This is interesting :)
Does that mean OSX is also more likely to get a virus than Linux/ubuntu?

I believe so. From my understanding, there are security holes in OS X that are a result of the design of the operating system, rather than just "patchable" flaws. They can't be fixed without breaking most existing software.

A sufficiently-determined attacker could write an actual virus for Mac OS X, and potentially devastate Macs all over the world. Only the comparatively-small market share of Macs would stop the spread of the virus, as probably many Mac users interact only with Windows users via e-mail (and Windows users wouldn't propagate the virus).

---

