---
title: "Really weird and severe problem (I think it has to do with corrupted updates)"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jojojopo on 2012-04-16
Hello, I've been using Ubuntu for a few months now, and I've recently run into a problem that really puzzles me. I don't exactly know what went wrong or why, so I will describe the "symptoms" of the problem and how I believe this got to happen.

I have installed Ubuntu 11.10 64bit version, I use grub to multiboot.

The Symptoms: I can't take screenshots, nor can I open images (the default image viewer won't open). I can't update, the updater prompts me to do a partial upgrade, which doesn't work (more on what happens if I do a full update later). I can't open any system settings dialog, I once tried to open them and got an error message saying something about Ubuntu 12.something... which I never installed so I don't really know what that means (I can't get the same message again so I can't write exactly what it says). Besides that, system dialogs are heavily bugged, items dissapears from lists, buttons become blue with no text in it, all of this happens at random, and it may or may no fix each time I move the mouse over the items. Sometimes they freeze and I can't close them. Probably more things are not working, I only noticed these (which are enough for me :P).

How do I think this happened: Since it says something about another version of Ubuntu, I suspect it tried to upgrade and it failed. I never tried to upgrade though. Today I booted my computer and found that I had nearly 500MB of updates to install... partial upgrade didn't work, so I let it update. After I rebooted my computer so that the update would finish, the Master Boot Table was corrupted because grub told me that all my partitions had dissappeared (it wouldn't boot from any of them at all, saying that partition did not exist anymore). I booted from my Ubuntu CD and installed Boot-Repair, which fixed the boot problem. Now I have this really unstable system which I described above.

Could this had happened because I added something to the Repositories last night and it messed up the whole system with an update? Besides that, I remember that the power cable got plugged off by accident last night when I was working, but I really doubt that could mess things this bad. I can't think of anything else.

Well, sorry for making such a long post. I hope someone has an idea on this.

Thanks in advance! :D

---

### Post by stinkeye on 2012-04-16
Did you upgrade to 12.04 .
To check release in terminal...
```
lsb_release -d -r
```

Quote from a sticky in the [**_[COLOR="DarkRed"]Ubuntu +1 (Precise Pangolin) [/COLOR]_**]("http://ubuntuforums.org/forumdisplay.php?f=412") section.
> If you use Update Manager to upgrade your packages, and it offers to do a "Partial Upgrade", do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance.

You can also get problems when you add other repositories and then do a partial upgrade due to package conflicts.
Can usually be fixed by purging those repositories which will revert to the official packages.
Personally I would backup and do a fresh install otherwise you're never quite sure if everything is right.

---

### Post by Jojojopo on 2012-04-16
I never upgraded to 12.04, not willingly at least since it seems the computer tried to upgrade itself anyways :P. I checked system version as you said and it says 12.04.

Question regarding reinstalling. I have Ubuntu installed in sda1, and swap and the home folder on sda2 (sda5 and 6 respectively). Reinstalling Ubuntu on sda1, would I lose all my data stored in sda6?

---

### Post by Bucky Ball on 2012-04-16
> **Jojojopo said:**
> I never upgraded to 12.04, not willingly at least since it seems the computer tried to upgrade itself anyways :P. I checked system version as you said and it says 12.04.

Question regarding reinstalling. I have Ubuntu installed in sda1, and swap and the home folder on sda2 (sda5 and 6 respectively). Reinstalling Ubuntu on sda1, would I lose all my data stored in sda6?

12.04 LTS it is. 

When you get to the partitioning section of the install choose 'Something Else' to manually partition. Make sure your existing partition (sda6) are not ticked to format and you are installing only on sda1, the existing / partition. 

Is sda6 /home by any chance? If so, then the new install will use that as /home automatically if it is not ticked to format and all should be fine. Data on there WON'T be wiped as you are not formatting the partition.

Your situation shows the benefits of having a separate /home partition. If you need to do a full reinstall (rare, last resort, but it does happen) your data remains safe on the existing /home. 

Having said all this, it would be wise to do a backup of anything you don't want to lose before attempting. ;)

---

### Post by uRock on 2012-04-16
Moved to *Ubuntu+1*

---

