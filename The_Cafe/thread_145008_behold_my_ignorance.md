---
title: "behold my ignorance"
date: 2006-03-15
forum: The Cafe
---

### Post by fuscia on 2006-03-15
does having less on one's hard drive make accessing data faster?

---

### Post by mstlyevil on 2006-03-15
[QUOTE=fuscia]does having less on one's hard drive make accessing data faster?[/QUOTE]

As long as you have at least 15% of free space on your drive then no it doesn't.

---

### Post by fuscia on 2006-03-15
[QUOTE=mstlyevil]As long as you have at least 15% of free space on your drive then no it doesn't.[/QUOTE]

wow! that's lower than i thought it would be. thanks.

---

### Post by KiwiNZ on 2006-03-15
In fragmentation resistant OS's it is not a problem as long as you leave sufficient space for swap files etc.

However in Windows 9x and to a slightly lesser degree in NTFS ,as the drive gets more and more data on it the more fragmentaed it is likely to become.Fragmentation will provide a real hit on performance .

If you neglect maintainence defraging a nearly full drive takes an eternity.

---

### Post by mstlyevil on 2006-03-15
[QUOTE=KiwiNZ]In fragmentation resistant OS's it is not a problem as long as you leave sufficient space for swap files etc.

However in Windows 9x and to a slightly lesser degree in NTFS ,as the drive gets more and more data on it the more fragmentaed it is likely to become.Fragmentation will provide a real hit on performance .

If you neglect maintainence defraging a nearly full drive takes an eternity.[/QUOTE]

Good information to know.

---

### Post by Brunellus on 2006-03-15
[QUOTE=KiwiNZ]In fragmentation resistant OS's it is not a problem as long as you leave sufficient space for swap files etc.

However in Windows 9x and to a slightly lesser degree in NTFS ,as the drive gets more and more data on it the more fragmentaed it is likely to become.Fragmentation will provide a real hit on performance .

If you neglect maintainence defraging a nearly full drive takes an eternity.[/QUOTE]
so what does that mean for FAT32 filesystems in Linux?  is there a need to defragment them periodically?  are there any FAT32 defragmentation tools out there for Linux?

---

### Post by jdodson on 2006-03-15
[QUOTE=KiwiNZ]In fragmentation resistant OS's it is not a problem as long as you leave sufficient space for swap files etc.

However in Windows 9x and to a slightly lesser degree in NTFS ,as the drive gets more and more data on it the more fragmentaed it is likely to become.Fragmentation will provide a real hit on performance .

If you neglect maintainence defraging a nearly full drive takes an eternity.[/QUOTE]

Fragmentation on NTFS is not really a huge problem.  It was with FAT, but NTFS did a few things to really help the fragmentation issue that was iwth FAT32.  Not to say NTFS cannot be fragmented, but its not a huge performance killer it once was.

I am not putting in my chips for windows or anything, I personally don't use it, but whatever.

---

### Post by KiwiNZ on 2006-03-15
My experience is that NTFS is only marginally more resistent to fragmentation than Fat32.
It stll uses the firstfit as opposed to the best fit.

---

### Post by jdodson on 2006-03-15
[QUOTE=KiwiNZ]My experience is that NTFS is only marginally more resistent to fragmentation than Fat32.
It stll uses the firstfit as opposed to the best fit.[/QUOTE]

Sweet, where did you get that info on the alorighm it uses?  I have been diving more into filesystems lately, I would love to read up on that.   

But to my understanding there are like 5 versions of NTFS, not sure which one you use though, YMMV.  

Anyways, I don't use Windows so its hard to comment, I am just speaking more from a filesystem point of view.   Anyways, rock on Ext3, I would use Resier, but I guess I am just old fashioned:)

---

### Post by phen on 2006-03-15
from the hardware point of view, the data written on the beginning of the disc is accessed faster. therefore, early win installation guides recommended to make the system partition the first one. by doing this, you make sure that the system is at the beginning.

i think, the different speeds on the outer and inner side of the disc are the cause for this. i've never proven this statement, though...

cheers :-)

phen

---

### Post by Astrophobos on 2006-03-15
In FAT32 small files are store in the partition like others files, with NTFS small files are store directly in the MFT (Master File Table equivalent of File Allocation Table for the FAT32). So the fragmentation is less important.

In addition MFT is create in two locations. One at the beginning and the other in the middle. So the drive head is always at max half the way to it.

---

### Post by fuscia on 2006-03-16
[QUOTE=jdodson]Sweet, where did you get that info on the alorighm it uses? [/QUOTE]

(wtf??? time for the linux deer...)

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/IMG]

---

### Post by dtfinch on 2006-03-16
I've found NTFS fragmentation to be not only almost as bad as with FAT32, but exactly as bad as with FAT32. This comes after finding that our Windows 2003 server (yes, we have _one_), after only two months of use and still 90% free, had over 80% fragmentation with dozens of data files each broken into thousands of fragments. All NTFS did was allocate space linearly as the files grew, exactly as FAT32 does. The defrag analysis display showed just a narrow solid red strip with the rest of the drive being empty space.

> In addition MFT is create in two locations. One at the beginning and the other in the middle. So the drive head is always at max half the way to it.
I never heard about that before. But if they had any sense they'd put them at 1/4 and 3/4 of the way, so at max the head is 1/4 of the way from a copy of the MFT.

---

### Post by WildTangent on 2006-03-16
Whever I defrag my Windows computer, I mostly see red in the analysis, which I didn't used to see with FAT32 in Windows 98. Something must be up here...

-Wild

---

