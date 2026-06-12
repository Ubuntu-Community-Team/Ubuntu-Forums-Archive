---
title: "Raid 5 or Raid 10"
date: 2008-04-17
forum: Server Platforms
---

### Post by rgotten on 2008-04-17
I have being tryaing to build a server and have play installing the Software Raid 5, and reading today found some people advising to yse Raid 10, siunce is faster and more secure:

Is Raid 10 the same as Raid 1+0
Can we do Raid 10 on Ubuntu server
Is there going to be a diferrence with the new version 8.04..Should i wait for it.

I have 3 500 gib har drive..I am newby and I am learning and help will be appreciated. Also can somebody expalin to me if i should do LVM and what is the meaning of it??

Thanks

rgotten

---

### Post by doogy2004 on 2008-04-17
> **rgotten said:**
> I have 3 500 gib har drive..

I searched Google for raid calculator [http://www.google.com/search?q=raid+calculator](http://www.google.com/search?q=raid+calculator)

The third result [http://www.z-a-recovery.com/art-raid-estimator.htm](http://www.z-a-recovery.com/art-raid-estimator.htm) allows you to calculate Raid 10, to do Raid 10 you need exactly 4 HDDs, unfortunately you are 1 short.

---

### Post by Deathrend on 2008-04-18
First just think about what RAID 5, and RAID 10 are for one.

Assume we're using 4x500Gb drives

Raid 5, takes atleast three drives, the information is constantly being wrote accross the drives spreading out the what would be bottle neck of a single drive read/write time.  this allows for one drive fault talerance, meaning you can lose one drive, and not lose any information. With four drives, you will have 1.5TB of Space

Raid 10, also known as 1+0, combines two Raid arrays into one (Like RAID 50).  You first have two striped RAIDS, this takes two drives, and writes information to the appearing as one drive double the size of the smallest drive in the array (For just two drives).  If you hadd a second stroped array, of drives them same size, you can then mirror the first array to the second (Meaning it's an exact coppy of the first array).  This can handle two drives failing SO LONG AS they're on the same side of the array.  This offers 1TB of space.  It also offers the ability to roll back changes on servers which is really handy for development.  You can pull one of the striped arrays, make your changes, if they don't work, pull the other, swap back the second, the information remains unchanged.

I know I made a huge huge run on, but I'm out of time.

---

### Post by rgotten on 2008-04-18
I understand that, but in regards to software RAID and use it on a server and reliable to recover and mantain good speed, what is recomended. Also what is the role of LVM; I have read that peole create for exmaple, RAID 5 and then do LVM on top of that..Thanks

---

### Post by doogy2004 on 2008-04-20
> **rgotten said:**
> I understand that, but in regards to software RAID and use it on a server and reliable to recover and mantain good speed, what is recomended. Also what is the role of LVM; I have read that peole create for exmaple, RAID 5 and then do LVM on top of that..Thanks

here is a link to a good resource to do exactly what you are talking about [http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

---

