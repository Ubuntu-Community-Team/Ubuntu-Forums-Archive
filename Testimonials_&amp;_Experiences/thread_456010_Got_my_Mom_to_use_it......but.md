---
title: "Got my Mom to use it......but"
date: 2007-05-27
forum: Testimonials &amp; Experiences
---

### Post by kprowell on 2007-05-27
My mom asked me to install Ubuntu (of course after a lot of bugging her to do so) so I packed my wife and son and drove to moms to install Ubuntu.  I planned on having a dual boot for her in case she wanted to go to Windows foe something.  The install went great!  Her machine now flies where before she complained it was too slow.  Also, she (for whatever reason) had trouble with her printer printing envelopes.........well with OO and Ubuntu, it worked!  She was amazed.  Even Beryl worked which she likes.

Here's where the bad part comes in.  Now Windows will not boot.  The partition is there and can be seen in Ubuntu.  Grub installed and listed it (correctly) on the menu.  But, when you select Windows from Grub it just sits there.  Just as an FYI, I did have to resize her partition to create some space for Ubuntu.  I'm wondering if for some reason Windows is struggling with the resizing of the drive?  Any thoughts???  Right now she's "stuck" in Ubuntu.  Not that running Ubuntu is a bad thing......I just wanted her to have some options.

---

### Post by Metacarpal on 2007-05-27
Did you defragment the Windows drive before you repartitioned?  Windows has a habit of flinging files all over the hard drive, even on a clean installation.  If you resized without defragging, you may have accidentally taken away space occupied by files (or parts of files) that Windows needed to run...

---

### Post by kprowell on 2007-05-27
No, I didn't do that.  I've done quite a few Ubuntu installs with Windows and never ran across this.  I did some research and I found a few items referring to the geometry of the drive changing with the resize and that Windows sometimes has issues with that.  I tried a few things in the BIOS that some suggested like changing the settings for the drive from auto to LBA, etc.  Still nothing.  Ubuntu works great though!  :p

---

### Post by blacksadness on 2007-05-27
hey, try to scan the windows disk from win xp cd in repair mode, use chkdsk c:\ maybe it just needs some checking

---

### Post by Cows on 2007-05-27
From my experiences the problem that I have about 99% of the time is that when you resized it the order of the HDD changed.. like if it was hda2 before and you resize it would be hda3 or 4. But then Ubuntu put down hda2 and it didn't recognize. Is this computer running on a sata drive and ubuntu running on a ide because if it is then you need to map the harddrive. You can also go into windows recovery mode and type:

```
bootcfg /configure // configures the boot ini for windows.
```

---

### Post by kprowell on 2007-05-27
I'm not at the computer but I will forward these suggestions for my mom to try...

---

