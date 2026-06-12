---
title: "what utility should I use to defrag Windows XP SP2?"
date: 2007-04-01
forum: The Cafe
---

### Post by billdotson on 2007-04-01
I know that Windows has a defragmenter but it seems that it really doesn't do that well in regards to defragging the hard drive.  It will defragment files but instead of having all of the contiguous files together in a block there are usually separated blocks of contiguous files.  Also, sometimes there is still a few little "slivers" of fragmented files.  I ask because I want to use PartImage and it says that the hard drive must be defragmented and the system files must not be compressed or else it will not be able to save the disk image.

Is there a good FOSS utility that can defragment?

---

### Post by karellen on 2007-04-01
here
[http://www.download.com/Auslogics-Disk-Defrag/3000-2086_4-10628872.html?tag=lst-0-4](http://www.download.com/Auslogics-Disk-Defrag/3000-2086_4-10628872.html?tag=lst-0-4)
it's free...even if not open-source. but does it matters?

---

### Post by Arathorn on 2007-04-01
I use Raxco Perfect Disk, but that's not free. It works very well though. I'll check out the one you posted karellen.

---

### Post by billdotson on 2007-04-01
that didn't seem to do much different than the XP defragmenter.  :???: 
Eh oh well.  I guess I will try backing up my install w/ PartImage anyway.

I looked and the partition where I put stuff on it while I am in Ubuntu.. it is one perfect blue block.  In Windows just moving files fragments the heck out of stuff.  Very annoying.  I like Linux much more.. just Windows has my games..

---

### Post by FyreBrand on 2007-04-01
NTFS file management is a lot different than FAT file management.  When FAT drives are defragmented the files are stored contiguously.  NTFS drives can store files on multiple platters in the same sector area.  Basically you don't always want NTFS files to be stored contiguously.  Windows stores the files in a fashion it thinks it can most quickly and efficiently access them with minimal disk thrashing.  I use the Windows defragmenting utility and it works just fine.  A good thing to do is to defragment 2 or 3 times if the drive was particularly fragmented or if it's running out of space.  Once you get the drive as defrag'd as possible then run your imaging software.  Once you restore an image run the defrag utility again.  If you do a bit of Googling there are some good explanations on how NTFS file storage and fragmentation works.

---

### Post by banditti on 2007-04-01
I second perfect disk.  Fabulous

---

### Post by typical on 2007-07-03
> **billdotson said:**
> .  In Windows just moving files fragments the heck out of stuff.  Very annoying. 

Absolutely. My drive gets fragmented when i simply upload  snaps or install games onto it. And once fragmented,  with subsequent activity the chaos just keeps getting bigger. My lightning fast system which i used for serious gaming got so so slow and crappy that it was impossible to do anything critical on it. The system would just hang or freeze for no reason. It was like a computer that aged before its time.

---

### Post by Detonate on 2007-07-03
Hint:  Run defrag from the command line in safe mode.  Does a better job.  Defrag can't defrag files that are in use.

---

### Post by smoker on 2007-07-03
i've used this before and found ok, the commandline version is free, though you have to register!
DIRMS (do it right microsoft!)
[http://www.dirms.com/home/homepage.asp](http://www.dirms.com/home/homepage.asp)

---

### Post by LaRoza on 2007-07-03
> **Detonate said:**
> Hint:  Run defrag from the command line in safe mode.  Does a better job.  Defrag can't defrag files that are in use.

I always defrag in th command line, which is why I didn't notice that the GUI version in Vista will defrag c: no matter what drive you specify!

---

