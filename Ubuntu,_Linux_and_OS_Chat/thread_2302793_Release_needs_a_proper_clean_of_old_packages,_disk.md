---
title: "Release needs a proper clean of old packages, disk full of updates"
date: 2015-11-13
forum: Ubuntu, Linux and OS Chat
---

### Post by eric13 on 2015-11-13
I wonder why there is no automatic clean (e.g. apt-get clean && autoremove) of old packages once they got updated for a while.

Concrete case: I installed Lubuntu 14.04 LTS in mid 2014 on a 10y old PC own by a senior (aunt of mine) to replace Windows XP. I quickly got a positive feedback that the PC got faster. I obviously set the autoupdate of the system to let get most recent security updates. Target is to have a productive and safe system with as least maintenance as possible.

15 months later, I pay a visit to this senior and have a look on the computer. The / partition (16 GB) is 100% full. No way to get the last updates, some services or application don't work properly anymore because of lack of space.

So I manually run "apt-get clean" and "apt-get autoremove". This saves me 7GB !! That means half of the root partition was full of old packages!
Could then run a "apt-get update && upgrade" to get another 600 MB of recent updates that were not possible anymore.

Why it that kind of cleanup procedure not included in the default auto update feature?
At least remove all packages that got obsolete e.g more than 3 months ago!

Side consideration: "apt-get autoremove" removes old kernels, I reckon in the upper case more than 20! Why does _every_ step of the autoremove related to the kernel run a "update-grub" and thus make it so slow? A single update-grub at the end of the autoremove script would be much more efficient! I suppose the script runs in a try/catch/finally loop, put the update-grub in the 'finally' part if at least one kernel has been removed...

---

### Post by mörgæs on 2015-11-13
If has been proposed some time ago:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1250109](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1250109)

I agree: When a bug is fairly simple to fix and benefits a large number of people it should receive more attention.

I suggest that people click 'me too'.

---

### Post by eric13 on 2015-11-13
thanks for the link considering the upate-grub consideration.

The main issue is still about the lack of cleanup of old packages.

---

### Post by Sweet_Baby_Jamie on 2015-11-13
Doesn't Bleachbit do the same thing?  Perhaps a script that runs Bleachbit at certain intervals would help keep the system clean.

---

### Post by QIII on 2015-11-13
Doing an automatic cleanup after updates would smack of "we know what's best..."  Personally, I would not want that.  However, a "Clean up, I know what I'm doing" button might be appropriate.

The problem is that such a thing might do just what Bleachbit does sometimes: go too far and bork your system.

---

### Post by eric13 on 2015-11-16
> **QIII said:**
> Doing an automatic cleanup after updates would smack of "we know what's best..."  Personally, I would not want that.  However, a "Clean up, I know what I'm doing" button might be appropriate.

The problem is that such a thing might do just what Bleachbit does sometimes: go too far and bork your system.

I was more thinking about an automatic "clean these 3-months-old-never-used-since stuffs" button.

Bleachhit seems to be a nice cleanup service, similar to ccleaner or Windows "clean-up" tools under Windows.

But even if you don't use these tools, Microsoft do a clean of some 30-days-old Windows-Updates (typically removes windows.old), it exists for a while but became for famous with the Windows 10 upgrade. If MS package management is very far from those under Linux, this 30-days stuff is not a bad idea to prevent running out of space on /
So I wish a similar "feature" under Ubuntu.

---

