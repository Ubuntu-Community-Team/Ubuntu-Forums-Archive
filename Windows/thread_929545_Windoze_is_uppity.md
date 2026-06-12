---
title: "Windoze is uppity"
date: 2008-09-25
forum: Windows
---

### Post by GhentK on 2008-09-25
Hi all,

I recently upgraded to Intrepid to get away from my screwed-up Hardy installation. In the process I deleted an NTFS partition, moved my Windoze XP partition 5GB to the left, and grew it into the freed-up space on the right (without doing anything else to it).

Intrepid works far better than I'd expected from an alpha. Sure, the trash applet crashes and such, but that hardly makes it unusable.

Windoze, on the other hand, is completely useless. After having helped it find itself in boot.ini (**sighs** -- why do I even try getting it to work?!), it boots all the way up to the face browser screen -- except with no face browser, no clock, no shutdown icon. There's just the silly little Windows logo sitting there, reproaching me for having messed with the partitions without asking it first. Hard drive activity is completely absent after this point. Does anyone have a suggestion as to what I could do to make it work?

Thanks in advance.

---

### Post by karellen on 2008-09-25
you mean Windows?

---

### Post by K.Mandla on 2008-09-25
Moved to Windows Discussions.

---

### Post by smoker on 2008-09-25
if you have the install disk, you could try the 'fixboot' and fixmbr' commands from the 'recovery console. if that doesn't work you could try a repair install, this won't (or shouldn't) affect installed apps and data, though you will have to reinstall all windows updates. you will also have to reinstall grub afterwards to dual boot. as always, back up essential data first!

best of luck

---

### Post by GhentK on 2008-09-25
Sorry about posting in the wrong forum. :)

> **smoker said:**
> if you have the install disk, you could try the 'fixboot' and fixmbr' commands from the 'recovery console. if that doesn't work you could try a repair install, this won't (or shouldn't) affect installed apps and data, though you will have to reinstall all windows updates. you will also have to reinstall grub afterwards to dual boot. as always, back up essential data first!

best of luck

Thanks for your reply. I was fearing that I had to use fixmbr, but I'll see about trying it; I hope that it'll work. Otherwise, it wouldn't be a tragedy to have to reinstall it, but I'd rather be without, of course. :)

---

### Post by Battie on 2008-09-25
Are those commands going to work if he can already boot into Windows?  And won't that overwrite GRUB?

If Windows is that screwed up, I'm sure there will be juicy stuff in the system and application error logs.  Maybe post some stuff from there?

---

### Post by smoker on 2008-09-25
the OP mentions he can't fully boot into windows, it depends on where windows is stopping, by partitioning outside of windows, windows may be misreading the mbr, and therefore can't find the files it is looking for (this is only surmising on my part, hard to be absolute when the pc is not in front of you!). the fixboot and fixmbr commands will overwrite grub, as i mentioned.

---

### Post by Battie on 2008-09-25
> **smoker said:**
> the OP mentions he can't fully boot into windows, it depends on where windows is stopping, by partitioning outside of windows, windows may be misreading the mbr, and therefore can't find the files it is looking for (this is only surmising on my part, hard to be absolute when the pc is not in front of you!). the fixboot and fixmbr commands will overwrite grub, as i mentioned.

Oh, sorry!  I missed that you said that.  I must have read that post before having my coffee.

---

### Post by GhentK on 2008-09-28
> **Battie said:**
> I must have read that post before having my coffee.I won't ever learn fully not to digest anything without having had my coffee either. ;)

It seems that my HDD is giving up at the moment, so now my priorities have shifted to getting everything off the damned thing. :(

---

### Post by smoker on 2008-09-28
> **GhentK said:**
> It seems that my HDD is giving up at the moment, so now my priorities have shifted to getting everything off the damned thing. :(

drive fitness test is a great app for testing the integrity of your hard drive, you can download a bootable floppy or cd image from here if you want to try:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

either that or go to your hard drive manufacturers support site where you can usually download a similar app for the specific model.

best of luck

---

### Post by GhentK on 2008-09-28
> **smoker said:**
> either that or go to your hard drive manufacturers support site where you can usually download a similar app for the specific model. I do indeed have a Hitachi. :D Thanks a lot for the help. I'll try out the app when I'm done backing up my ~. :)

---

