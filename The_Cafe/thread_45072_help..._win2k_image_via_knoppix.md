---
title: "help... win2k image via knoppix"
date: 2005-06-28
forum: The Cafe
---

### Post by foobar on 2005-06-28
i am getting ready to start a fresh install of win2k on my home comp. what i would like to do is set up a second partition so that i can save an image of the main partition via knoppix. i have done some research but still could use some help (a link to a tut would be great).

---

### Post by Bil-E-daKid on 2005-06-28
Great idea foobar,

I've done the same thing before using Knoppix and a tool called 'partimage' which comes with it.

When you say you still need help, are you referring to creating the second partition to store the image on or creating the image with Knoppix?

Regards

---

### Post by foobar on 2005-06-28
well i guess both,
i can make the partitions but may need help formating the second partition... i think you can do it through 'my computer'

i definitely could use help with knoppix and the 'dd' command

*also, can knoppix write to ntfs, or should i format the 2nd partition in fat32?

---

### Post by Bil-E-daKid on 2005-06-28
Not sure about formatting the drive from within linux as I've not done that before (except at installation time).

I'm sure it's possible and it's likely to a command like 'mkXXXfs' where XXX is the name of the file system you want to make (eg mkisofs for CD's, mkrieserfs for RieserFS etc).

I'd suggest using a Fat32 partition for the one to dump an image too as you'll have far less problems that way. As far as I understand NTFS writing is still largely experimental where reading is no problem at all.

The DD command would work for dumping the partition to a file but, from the research I did at the time, restoring the partition wasn't a straight forward process - especially when it came to boot sectors and the like. Which is why I settled on using 'partimage' ([http://www.partimage.org/](http://www.partimage.org/)) as it looks after all that for you and comes with Knoppix.

Partimage also has the added benefit of being able to compress the image as it's doing it (using bz2 for example) where dd will give you raw data of a much larger size.

regards

---

### Post by wherethebibawi on 2005-06-29
[QUOTE=Bil-E-daKid]Not sure about formatting the drive from within linux as I've not done that before (except at installation time).

I'm sure it's possible and it's likely to a command like 'mkXXXfs' where XXX is the name of the file system you want to make (eg mkisofs for CD's, mkrieserfs for RieserFS etc).

I'd suggest using a Fat32 partition for the one to dump an image too as you'll have far less problems that way. As far as I understand NTFS writing is still largely experimental where reading is no problem at all.

The DD command would work for dumping the partition to a file but, from the research I did at the time, restoring the partition wasn't a straight forward process - especially when it came to boot sectors and the like. Which is why I settled on using 'partimage' ([http://www.partimage.org/](http://www.partimage.org/)) as it looks after all that for you and comes with Knoppix.

Partimage also has the added benefit of being able to compress the image as it's doing it (using bz2 for example) where dd will give you raw data of a much larger size.

regards[/QUOTE]
 Dude Linux supports more file systems than any other OS and you can format the drive in any way you like exept NTFS because MS have a worldwide patent on the file system structure, but sure use linux to Fdisk and format the drive. Fat32 is great working with Linux, however, remember that Fat 32 will not format passed 80Gigs that is the theoretical maxixmum with 64K clusters. i hope you are  familiar with disk parrameters, otherwise don't even think about it, you will just getlost in numbers.

---

