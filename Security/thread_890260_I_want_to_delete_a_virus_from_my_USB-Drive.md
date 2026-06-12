---
title: "I want to delete a virus from my USB-Drive"
date: 2008-08-14
forum: Security
---

### Post by arashiko28 on 2008-08-14
I used my USB on a Windows XP computer, later I found out it had a virus. I know it wasn't mine, that USB was virgin for windows and was completely clean before that. Now it has all the files I copied corrupted and locked, can't remove them nor the clamav or AVG recognizes the virus, so they do nothing.
Please help! I want my USB back! I don't care about the info inside, all I want is my pen drive clean again.

---

### Post by mrtomservo on 2008-08-14
If all else fails you might have to reformat it.  I'm really surprised that AVG and CLAM didn't identify it.  If don't want to reformat, you should start by trying to figure out exactly what virus was on that XP machine.  From there you could probably get an idea what's required to solve the problem.

---

### Post by pytheas22 on 2008-08-14
You could just reformat...that would wipe it pretty clean.  You can install gparted:
```

sudo apt-get install gparted
```

if you want a nice GUI for reformatting the USB stick.

You could also use 'shred' to really wipe the disk clean, but really that shouldn't be necessary.

---

### Post by arashiko28 on 2008-08-14
I have gparted and qtparted installed. It has never been able of formatting my USB, it's a 32GB USB drive. I wish I could simply do that. On the other hand, when I try to update clamav it says that the update command takes no arguments :s

EDIT:

I have added a screenshot, this is my 4GB usb drive, it only recognizes about 972MB and it says unallocated. Does not allow me to do anything else. I have removed all files from it with rm -rf * ubt didn't recover the space, instead of 3.8GB it shows 3.6GB and it's apparently clean and doesn't show anything hidden.

The gparted shows this error message on terminal with both USB's.
> Unable to open /dev/sdb - unrecognised disk label.

---

### Post by pytheas22 on 2008-08-14
I wonder if the disk is damaged?  Otherwise I don't know why gparted only thinks there is less than 1GB there.

You could try using testdisk:
```

sudo apt-get install testdisk
```

which can rewrite the partition table (actually probably not a bad idea, if you're worried about a weird virus hiding on the driver).

You could also try reformatting in a Windows machine, although you'll obviously risk things that way.

---

### Post by mrtomservo on 2008-08-14
I saw this post, maybe this would be of some assistance.

[http://ubuntuforums.org/showthread.php?t=295596]("http://ubuntuforums.org/showthread.php?t=295596")

---

### Post by arashiko28 on 2008-08-14
> **pytheas22 said:**
> I wonder if the disk is damaged?  Otherwise I don't know why gparted only thinks there is less than 1GB there.

You could try using testdisk:
```

sudo apt-get install testdisk
```

which can rewrite the partition table (actually probably not a bad idea, if you're worried about a weird virus hiding on the driver).

You could also try reformatting in a Windows machine, although you'll obviously risk things that way.

The disk is not damaged, that thing has never worked for me even though I keep thinking that maybe I don't know how to use it. About the windows option, I'm thinking about it... now... where to find a windows computer with an extremely good antivirus in the middle of the night?? (no offense, personal joke).
I don't want to risk anyone computer, this is an extremely dangerous virus, practically destroyed my mum's office computer (original source), now I have to format that one tomorrow :(

---

### Post by arashiko28 on 2008-08-15
The 4GB drive is safe, I risked myself and used the commands of the malicious commands post and deleted all the files, then ran avast and it came clean. So I used a windows computer and formatted the disk and tada! 3.8GB available. Right now I'm formatting the 32GB drive, so let's pray.[-o<[-o<[-o<

---

### Post by Proton Soup on 2008-08-15
deleting files and not recovering space sounds familiar.  i encountered that problem while trying to move files from a windows machine with my USB drive.  when i deleted them in Ubuntu, the files weren't really deleted, just marked as such.  and i couldn't figure out how to purge the Trash for some reason (don't remember if i'd already moved the drive to the Win machine again).  but what i ended up doing was deleting the "deleted" files in Windows, which either wasn't really trashing them, or keeping a trash copy local.

in any case, you probably haven't truly deleted anything on that drive, but i'm too inexperienced to know the exact resolution.  maybe Ubuntu left you a Trash can to empty.

---

### Post by arashiko28 on 2008-08-15
They were gone for real. Linux does not really delete them at the first time, it sends them to ./thrash1000 and by hitting ctrl+h yo can see this, also when you safely unmount your drive it warns you about it and that if you don't delete it, won't recover disk space. But this was completely different. 
Anyway, my problem is solved. I had to run about... (clamAV, Avast, AVG) 3 antiviruses to get rid of this thing from my USB's, I'll try to find out what kind of a devil-sended virus is to warn out, because it's pretty hostile. Perhaps by the description someone could know: it links itself to the windows-explorer, so that everytime you turn on, it's there, it eats all of the available RAM so if you want to run something as simple as the properties of My PC it send an error message about not having resources to run the requested task.

What I did was deleting all the files with rm -rf * **(Caution to n00bs, very dangerous!!! I risked my self at doing this)** and then re-running the antivirus, when it came clean, passed it to a windows computer, and formatted the drives.

Thank you all for your help!:lolflag:

---

