---
title: "AUTRUN.INF 'Panda Vaccine'"
date: 2010-05-15
forum: The Cafe
---

### Post by Penguin Guy on 2010-05-15
What's going on? An 'AUTORUN.INF' file appeared on my flash drive. Gedit refuses to display the file, but the terminal gives me this:
```
$ cat AUTORUN.INF 
caacaacaacaacaa
```
A quick Google reveals something to do with a 'Panda' vaccine: [here](http://hype-free.blogspot.com/2009/03/how-does-panda-usb-vaccination-work.html) and [here](http://www.technibble.com/forums/showthread.php?t=6157). My USB has only been plugged into three computers since it was last reformatted so I know that nobody put it on there knowingly, and I don't like the idea of robots sticking files on my flash drive. Anyone else had this happen to them?

EDIT: I've deleted the file and don't need any help, I just wanted to see what people thought about this - it seems odd behavior for an antivirus.

---

### Post by gradinaruvasile on 2010-05-15
Well there you have it. You answered yourself in the links. Maybe on one of those computers there was a Panda Antivirus or something.
How did you format the stick? Windows or Linux?

Just format it in Linux and see if it is there afterwards:

Unmount the drive:

```
sudo umount /dev/sdX
```

Then format it:

```
sudo mkfs.vfat /dev/sdX
```

Where the X is the corresponding letter (b,c etc) to your USB drive. You can see it by issuing the "dmesg" command after inserting the USB drive (sdb, sdc, sdd or whatever).

MAKE ABSOLUTELY SURE you use the correct DEVICE NAME!
The SATA HDDs have the same naming conventions (usually the first HDD is /dev/sda) so check carefully before proceeding!

---

### Post by viralmeme on 2010-05-15
> **Penguin Guy said:**
> 
```
$ cat AUTORUN.INF 
caacaacaacaacaa
``` .. Anyone else had this happen to them?

NO, obviously someone ran a DOS executable on your USB device ..

---

### Post by Lightstar on 2010-05-15
> **Penguin Guy said:**
> What's going on? An 'AUTORUN.INF' file appeared on my flash drive. Gedit refuses to display the file, but the terminal gives me this:
```
$ cat AUTORUN.INF 
caacaacaacaacaa
```
A quick Google reveals something to do with a 'Panda' vaccine: [here](http://hype-free.blogspot.com/2009/03/how-does-panda-usb-vaccination-work.html) and [here](http://www.technibble.com/forums/showthread.php?t=6157). 

Sounds more like a crow than a panda.
Sometimes some tools format a USB as a CD, that makes it autorun (can be risky) and also prevents you from deleting anything.  (because you can't delete files on a cd (except if it's cd-rw))

format it would be the best option.
In windows, you can use HP's floppy disk formatting tools to make sure it gets rid of the 'cd' ish type.
In linux, I'd use what gradinaruvasile said, or gparted.

and then if you want, plug it in a computer, one by one, and try to find out which computer did it.  Panda usually shows in the add/remove programs from control panel in windows.   It's not a bad antivirus though I'm surprised they mess up usb disks like that (if it really was panda).

---

### Post by Penguin Guy on 2010-05-15
> **Lightstar said:**
> I'm surprised Panda messes up usb disks like that (if it really was panda).
My thoughts exactly - I had no trouble removing it, I just thought it seemed a bit odd that an antivirus would do this.

---

### Post by TheLions on 2010-05-15
> **Penguin Guy said:**
> My thoughts exactly - I had no trouble removing it, I just thought it seemed a bit odd that an antivirus would do this.

to prevent viruses creating infected autorun...

usualy viruses spread over usb using some excecutable file and autorun which runs that exectuable...

---

