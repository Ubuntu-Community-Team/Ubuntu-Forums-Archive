---
title: "wine multiple disc installation easy fix"
date: 2010-06-17
forum: Wine
---

### Post by Azazel on 2010-06-17
I have had problems installing software that requires more than one disc and i know others have had the same issue.

For example, the game civilization IV has two discs. about halfway through installation it will ask for the second disc. The problem is, after you put in the second disc wine wont detect that there is a disc. Then ubuntu all together stops recognizing discs, only to be fixed by a restart.

The only solution I was able to find to this problem was to make a virtual image of the disc, but this is a pain and isn't necessary

Here is was what I tried for my Civ IV disc and it worked, it's very simple.

After removing the first disc, open a terminal and type:
```
sudo mount /dev/cdrom
```
then insert the next disc and it should work! if not try entering previous code again with the disc inserted.

the details may change from system to system, but basically you need to manually unmount and remount the cdrom.

let me know if anyone else gets this to work!

---

### Post by cogadh on 2010-06-17
In your attempts to find a solution, did you try using the "wine eject" command to swap out the first disk? Most of the time, that's all you need to get around multiple disk install issues with Wine.

---

### Post by Azazel on 2010-06-19
No, I haven't heard of wine eject until now, thanks for mentioning it.
is the code simply:
```
wine eject
```
if that works it would be a much better solution!

---

### Post by cogadh on 2010-06-19
You have to specify a drive, "wine eject D:" or just tell it to eject all ejectable drives "wine eject -a".

---

### Post by chromatica86 on 2010-06-19
After the wine eject command, just how do you get the next disc read by the installer??

---

### Post by cogadh on 2010-06-19
By using the "wine eject" command, it should allow the system to auto-mount it normally and the installer should just pick up where it left off.

---

### Post by ahso4271 on 2010-07-11
no FS9 installation does not detect further CDs

---

### Post by cogadh on 2010-07-11
That's probably because of the way Ubuntu now handles mounting CD/DVD disks. In the past, the CD/DVD drive had a fstab entry that basically meant the drive had a fixed mount location that Wine could recognize (as drive "D:", for example). Now it creates a unique mount location for any disk you insert, based on the disk's label. Since the label changes from disk to disk, Wine might not correctly recognize the new disk as the next disk in a series. You can fix that by simply creating your own fstab entry for the drive and multi-disk installs using "wine eject" will work normally.

---

### Post by ahso4271 on 2010-07-13
For multiple CDs install ignore automount in /media and do:

sudo mount /dev/sr0 /cdrom
sudo umount /dev/sr0 /cdrom


start not from inside the cdrom dir:

wine /cdrom/FS*/Setup.exe
-------

I had to do it the above way which is very annoying. Automount is a real joke...broken in 10.04? it never mounts any discs i simply insert.

---

### Post by cogadh on 2010-07-13
Again, creating an appropriate fstab entry for CD/DVD drive will eliminate the need for that annoying command combo.

---

### Post by mc4man on 2010-07-13
The other positive for creating a typical fstab entry(s) for your drive(s) is it will 'override' the security bit policy as far as .exe's on cd's, dvd's.

I've as yet to see any downside to having fstab entries for cd/dvd drives in 10.04 or 10.10 though the permissions on dvd media are a bit 'odd' for owner - screen

---

### Post by ahso4271 on 2010-07-14
Hi
how would the above look for an fstab cdrom entry in 10.04?
Any ideas on how to get my inserted discs automounted?
Thanks

---

### Post by Azazel on 2010-09-24
in 10.10, cannot run an .exe from the cdrom
i got around this by using
```
wine start /Unix /media/DiscLabel/file.exe
```

however i wasn't able to switch discs while installing (the installer wouldn't detect the second disc)
i tried everything i could think of, including wine eject

so i added an fstab entry, but the cdrom wouldn't mount at the mount point in the fstab and the cdrom would not automount in /media/DiscLabel

this is endlessly frustrating!! any suggestions?

---

