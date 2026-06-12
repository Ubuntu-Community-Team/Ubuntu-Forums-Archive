---
title: "Cloning harddrive to a smaller one"
date: 2011-09-18
forum: Virtualisation
---

### Post by Howy on 2011-09-18
I want to virtualize my old system. I did it once, but it was no good, because it was a single big file, and really not handy. It's also the case that the contents of the HDD do fit on another one I have, but if I clone to whole thing with dd it won't fit. (I have around 110Gb to work with, the partition is 180Gb.)
I've already tried tar'ing up the contents, but it compromises both the MBR and the attributes of files.
So I wonder if there is a way I can use dd and compress it directly, without having to store it somewhere? (I know that if I compress it, all the empty space will become 0's, and easy to handle.)
Thanks in advance. :)

---

### Post by haqking on 2011-09-18
> **Howy said:**
> I want to virtualize my old system. I did it once, but it was no good, because it was a single big file, and really not handy. It's also the case that the contents of the HDD do fit on another one I have, but if I clone to whole thing with dd it won't fit. (I have around 110Gb to work with, the partition is 180Gb.)
I've already tried tar'ing up the contents, but it compromises both the MBR and the attributes of files.
So I wonder if there is a way I can use dd and compress it directly, without having to store it somewhere? (I know that if I compress it, all the empty space will become 0's, and easy to handle.)
Thanks in advance. :)


You want to clone a 180gb disk to a 110gb is that what you mean ?

Even with clonezilla the destination has to be the same size or larger, the image is compressed for sure but to clone it back as a working system the destination has to be same or larger.

why dont you resize the disk partition of 180 to say 110 leaving the unused 70 as free space, then you can clone the partition that now only contains the used space ?

or am i not understanding you ?

cheers

---

### Post by Howy on 2011-09-19
I don't know if I want to take the risk of resizing an NTFS partition. These drivers aren't as reliable as ext, you know.

But previously I've seen commands that allow on-the-fly decompression and writing of disk images directly to a device when there is too little memory available. It should be possible to do compression as well, I believe, because the files are written progressively. So let's say that dd output the data, and it was piped to gzip for compression.
Wouldn't that be possible?
I just don't have any idea of how to use dd and how to pipe it properly to gzip.

---

### Post by haqking on 2011-09-19
> **Howy said:**
> I don't know if I want to take the risk of resizing an NTFS partition. These drivers aren't as reliable as ext, you know.

But previously I've seen commands that allow on-the-fly decompression and writing of disk images directly to a device when there is too little memory available. It should be possible to do compression as well, I believe, because the files are written progressively. So let's say that dd output the data, and it was piped to gzip for compression.
Wouldn't that be possible?
I just don't have any idea of how to use dd and how to pipe it properly to gzip.


OK so i dont think i am understanding you then.  The title says cloning...a clone would be an exact copy of a source.

If you cloned a source as an image file the image file would be compressed and the 180gb source would fit as a image file on the 110gb destination, but this is a file.  If you want a bit for bit clone from a destination then the result would be the same as the source and hence not compressed etc. but if you want just a compressed file of a destaination then yes you can use clonezilla for example to do it, and you can ask it to split it up into smaller multiple files aswell.


For NTFS i personally have never had any issues resizing however it is often best to use the windows tools to resize it.

---

### Post by Howy on 2011-09-22
So, I can get Clonezilla running on an Ubuntu liveCD, am I right?
And it allows you to directly compress the file?
Then it's all I need. :) I'll set it up tomorrow, and let it run throughout the day.

I read this:
[http://tuxradar.com/content/how-clone-hard-drives-clonezilla](http://tuxradar.com/content/how-clone-hard-drives-clonezilla)
And I see that it's all I'll need.
Thanks for the tip. ;)

---

### Post by haqking on 2011-09-22
> **Howy said:**
> So, I can get Clonezilla running on an Ubuntu liveCD, am I right?
And it allows you to directly compress the file?
Then it's all I need. :) I'll set it up tomorrow, and let it run throughout the day.

I read this:
[http://tuxradar.com/content/how-clone-hard-drives-clonezilla](http://tuxradar.com/content/how-clone-hard-drives-clonezilla)
And I see that it's all I'll need.
Thanks for the tip. ;)

no you download the clonezilla .iso and burn it to a CD then boot to the CD

---

### Post by Howy on 2011-09-24
Oh, okay. But I found Partimage to work better. I think it's a part of Clonezilla, but I believe Clonezilla is more of a imaging suite rather than a single-function program that can be installed.
Anyways, Partimage does exactly what I wanted, which is to compress only the used space to a compressed file, and possibly doing it without ruining the integrity of the filesystem. :)
I'll be sure to remember this for future use if I want to image HDDs.

---

### Post by sid1950 on 2011-09-26
> **Howy said:**
> Oh, okay. But I found Partimage to work better. I think it's a part of Clonezilla, but I believe Clonezilla is more of a imaging suite rather than a single-function program that can be installed.
Anyways, Partimage does exactly what I wanted, which is to compress only the used space to a compressed file, and possibly doing it without ruining the integrity of the filesystem. :)
I'll be sure to remember this for future use if I want to image HDDs.

Howy:
May be too late, but I have been using PartedMagic Live on CD & USB for some years and never had a problem with resizing NTFS partitions apart from once when the partition had not been unmounted properly. A bit of fiddling got it to work.

I have used PartedMagic and Clonezilla succesfully to clone 5 or 6 Win XP installs to new drives. In each case I moved the user data onto a new drive  first to make space, resized the C: partition to about as small as it would go, then used CloneZilla to clone the C: partition onto a new drive. After that I use PartedMagic to resize the new partition to a sensible size, add  D: partition for the user data and copy it all back. So far this has worked fine on both laptops and desktops.

---

