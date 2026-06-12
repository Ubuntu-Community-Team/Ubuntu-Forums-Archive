---
title: "Clonezilla backup on external usb HDD"
date: 2011-09-08
forum: The Cafe
---

### Post by CoreyB. on 2011-09-08
I know in clonezilla you can backup a computer's hard drive to an external usb hard drive. My question is, if I were to use that option, will I be able to save the backup as a file on my ntfs formatted external hard drive?

---

### Post by Eldera on 2011-09-08
Clonezilla gives you several different options: If you do a disk to disk clone, it will just erase (reformat) your hard drive. If you used Gparted from a live Cd or USB to shrink your ntsf partition first and create a partition for your backup, you could do a partition to partition clone with out touching your ntsf partition. 

There may be some other options using Clonezilla images, but I have not worked with them.

Perhaps someone who has worked with Clonezilla images can also add advice.

---

### Post by haqking on 2011-09-08
> **CoreyB. said:**
> I know in clonezilla you can backup a computer's hard drive to an external usb hard drive. My question is, if I were to use that option, will I be able to save the backup as a file on my ntfs formatted external hard drive?

once you have made the image you can put it where you like.

unsure if you can then read the imagefile from the NTFS when cloning back though, i think so as it supports NTFS so i cant see why not

but once you have the file you cna store it where you like

---

### Post by CoreyB. on 2011-09-08
Right, a guess to be a little more clear, my question is, if I clone my laptop HDD and use my NTFS formatted usb hard drive as the destination, will it copy it on to my NTFS partition as a single file or will it try to repartition in like my laptop and erase everything else on my external HDD?

---

### Post by haqking on 2011-09-08
> **CoreyB. said:**
> Right, a guess to be a little more clear, my question is, if I clone my laptop HDD and use my NTFS formatted usb hard drive as the destination, will it copy it on to my NTFS partition as a single file or will it try to repartition in like my laptop and erase everything else on my external HDD?


Depends if you choose to do a direct clone or clone to an image.

You want to clone to an image which create a file.
read here at the FAQ on step by steps etc [http://www.clonezilla.org/clonezilla-live-doc.php](http://www.clonezilla.org/clonezilla-live-doc.php)

---

### Post by Eldera on 2011-09-08
There are several different ways of using clonzilla: making clones or making images. Different techniques have different results. You need to figure out whether you are going to make an image file like haqking was talking about. If you "clone" it will erase your drive, unless you do some partitioning ahead of time. 

If you create an image, you can store the image somewhere, but I am the wrong one to tell you how to make and store an image, because all I have done is "Clones"

Read up on what are "clones" and what are "images" and a lot of your questions will be answered. Clonezilla can be used to do both.

Edit: Looks like hagking types faster than I do. Ha

---

### Post by CoreyB. on 2011-09-08
OK, thanks haqking and Eldera.

---

### Post by cariboo on 2011-09-08
I use clonezilla all the time to store images on my server, when you restore them to a hard drive, the image creates a clone of the original. All the functions are available via menus on the clonezilla boot disk.If you are creating an image of a hard drive, clonezilla doesn't care about the format, the drives on my server are xfs

---

