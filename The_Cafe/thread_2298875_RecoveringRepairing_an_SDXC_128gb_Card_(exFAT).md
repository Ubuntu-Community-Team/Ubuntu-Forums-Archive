---
title: "Recovering/Repairing an SDXC 128gb Card (exFAT)"
date: 2015-10-14
forum: The Cafe
---

### Post by Ken UK on 2015-10-14
While I had my card plugged into a cheap card reader while using Windows 7 (on this rare occasion) the card suddenly stopped working and I was disconnected from the card and the photos I was viewing. The card will no longer mount or it says it's inaccessible and do I want to format it? So I've started doing some research to find out what I could do, the following is what I've found so far:

[LIST]
[*]The card in my internal card reader for my Ubuntu computer at home isn't picked up in the normal folder view but is picked up in disk utility with the correct size i.e. 128gb. but it says the partition is unknown.
[*]I've repeatedly come across TestDisk on the net so I tried to run it following the instructions. It detected my file system as Intel but after that lists the partition as NTFS. I ran quick scan and it came up with nothing so I run deep scan and it also found nothing. I went back into select my file system as 'none' and it found the partition and correctly identified it as exFAT although it says I can't do anything with it because I chose 'none'.
[*]I ran Photorec (the card is full of JPEGS and RAW images (Sony SR2) as well as some videos) and it managed to recover almost all of them although not completely in their original state. This is better than nothing of course but I don't trust it because for example most of the JPEGs are 1600x1000 instead of the original 6000x4000, also most of the JPEGS have los their EXIF data. A few other files with different random extensions have appeared which I assume is misinterpreted data (e.g. .apple, .zip etc.)
[/LIST]
I’m new to this but my gut feeling is that the data is there but the file system data structure has been corrupted so I’m wondering if there is a way of recovering the exFAT file system so I can access my files normally.

Any input would be greatly appreciated.

---

### Post by ajgreeny on 2015-10-14
You might have more luck attaching the card to a Windows machine.

If it was in Windows that the card stopped working the NTFS partition is probably being flagged as still in use and not shut-down properly when you attach it to Ubuntu; Windows should be able to sort that out simply by attaching it to a Windows computer.  Just make sure you eject the card properly when it is found; do not simply unplug it or you will have exactly the same problem again.

---

### Post by sudodus on 2015-10-14
Is it necessary to recover the files, or have you backed them up in some other place?

If the files are backed up, I suggest that you make a new partition table and one or more partitions. If it is a card, that belongs to a camera, I suggest that you format it in the camera. Otherwise you can use ***gparted***.

If it is necessary to recover the files, I think ajgreeny's advice is good. I would like to add one step if you want to play really safe.

- Make a cloned copy of the card to another card, pendrive or hard disk drive with ***ddrescue***, a linux tool.

```
sudo apt-get install gddrescue
```

The info page contains a good tutorial with examples

```
info ddrescue
```

Then you are safe even if the attempts to repair the file system would damage the pictures.

-o-

Try in a computer with a good card reader and Windows, and ***find a good tool*** for repairing file systems. ***exFAT*** is a proprietary Microsoft file system, and you should search for tools that can repair that file system. Maybe but only maybe ```
chkdsk /f
``` can do it.

If you cannot repair the file system, I think the best solution is to recover what you can recover with ***PhotoRec***.

---

### Post by Ken UK on 2015-10-14
Thanks alot of the advice guys! In the end it appears the problem was solved simply by running chkdsk F: /F in Windows/Command Prompt to fix the corruption. I knew the experts of the Ubuntu forum would come to the rescue! :-)

I didn't make a back up of all the photos because they are huge (24mp JPEG + RAW) but I've bought a huge external hard drive to aid this problem.

---

### Post by sudodus on 2015-10-14
I'm glad you solved the problem :KS

Good luck with the backup system using the new huge external hard disk drive.

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

