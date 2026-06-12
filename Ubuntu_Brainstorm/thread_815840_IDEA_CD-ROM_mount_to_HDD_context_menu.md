---
title: "IDEA: CD-ROM mount to HDD context menu"
date: 2008-06-02
forum: Ubuntu Brainstorm
---

### Post by jcbray on 2008-06-02
I would like to have a context sensitive menu option for the CD-ROM drive/s mounted to have them made into an ISO/IMG and mounted as a virtual drive. 

I haven't seen a program that does this either, and although I'm no programmer, I imagine there would not be much difficulty. I know how to create an IMG file, and I'm sure there is another program out there to mount them as a virtual drive, as in windows - It's the extreme convenience that I see as worthwhile.

There are a number of reasons why you would want to do this, for starters, most people have only one optical drive in their computers, but play multiple games, access programs, or switch around enough that making sure the right disc is in your drive all the time can get annoying. Notably, many older games came with many discs that you have to switch between (older games that are more compatible with Wine then more modern games perhaps) and I see this as a simple option that would make these times smoother.

This is by no means an urgent issue that should be addressed, but one that I'm sure many would find convenient.

---

### Post by smartboyathome on 2008-06-02
This is actually pretty simple. Just open up Brasero (or your favorite CD burner/ripper), and make a disk copy as a .iso. Then you can mount that. The reason this doesn't happen is because it would take a while to do, decreasing the enjoyability of Ubuntu. :(

---

### Post by whitewizardcoder on 2008-06-03
As smartboyathome said, you can rip an iso of a cd using brasero, then you can mount the image like this:
```

sudo mkdir /media/virtualCD
sudo mount -t iso9660 -o user,ro,loop [iso_file] /media/virtualCD
```

replacing [iso_file] with the full path to and including your iso.  You can change the mount directory (/media/virtualCD) to anything you want.

I agree though that there should be an easier way to do this (eg. right click an iso and click "mount"), but this should be simple enough.

---

### Post by WitchCraft on 2008-06-22
> **whitewizardcoder said:**
> As smartboyathome said, you can rip an iso of a cd using brasero, then you can mount the image like this:
```

sudo mkdir /media/virtualCD
sudo mount -t iso9660 -o user,ro,loop [iso_file] /media/virtualCD
```

replacing [iso_file] with the full path to and including your iso.  You can change the mount directory (/media/virtualCD) to anything you want.

I agree though that there should be an easier way to do this (eg. right click an iso and click "mount"), but this should be simple enough.

This has already been done. ;-) See the following link:
[http://ubuntuforums.org/showthread.php?t=647833](http://ubuntuforums.org/showthread.php?t=647833)

---

