---
title: "Cationary tale about a dual boot uninstall"
date: 2008-05-30
forum: Testimonials &amp; Experiences
---

### Post by jaspen.p on 2008-05-30
I have been running Ubuntu for about a year on a old business class PC that I bought for $25. I really like some of the applications so I decided to dual boot it on my Toshiba A75-s206 laptop with XP. All was well... until, I decided it would be cool to run ubuntu inside a virtual machine in XP. 

When I got that working I decided I didn't need the original ubuntu install so I reformatted both the Ubuntu and Grub partitions back to NTFS(DON'T DO THIS). Upon restarting my laptop I nearly crapped my pants because had forgot about the Grub Boot loader. Now that the partition was gone that contained the Grub loader my MBR wasn't correct so XP didn't boot up. I had the restore disk for my laptop but I have several software packages that would be difficult to reinstall...so that was a last resort.

Because my restore disk was not the standard XP installation disk the "FIXMBR" command did not work...I was almost frantic at this point... I did some more searching and found that my restore disk booted to Win98 so I needed to use "fdisk /mbr" to restore the MBR. Crisis avoided...

Hopefully posting this will encourage others to ask for help if they are unsure about what they are trying to do, I know I wish I had. 

Also, I would like to thank everyone who offers help in these forums because they are a great tool when you do something stupid like this.

---

### Post by anewguy on 2008-05-30
There are several how-to's on removing Ubuntu, which is what you did.  All of these tutorials explain how you need to recover the master boot record for Windows.  Unfortunately you learned this the way many of us have.  For those reading this post and contemplating doing a similar thing to remove Ubuntu, please see one of the how-to's, such as:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

---

### Post by jaspen.p on 2008-05-30
Here are some pics of ubuntu in the virtual window now that XP is back up and running.

---

### Post by bumanie on 2008-05-30
It is easier to use windows recovery console to restore the mbr, however there are a number of other utilities around that can write boot sectors for windows if a windows disc has been lost/damaged or whatever.

---

### Post by abhiroopb on 2008-05-30
If you can't boot into XP, but need to recover you're files, just slide in a LiveCD and you can browse your XP partition and copy all the data to another external hard drive. Had to do this for LOADS of my friends.

---

### Post by Sef on 2008-05-30
Moved to Testimonials and Experiences.

> It is easier to use windows recovery console to restore the mbr, however there are a number of other utilities around that can write boot sectors for windows if a windows disc has been lost/damaged or whatever.

Check out [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by wolfen69 on 2008-05-31
i like partedmagic. you are automatically root and can do anything you want, easily. it makes partitioning/resizing/formatting easy. then again, cfdisk is cool too.

@jaspen.p-    with more experience, you will avoid some of the "problems" you had. after a while it becomes second nature to use linux. like anything else in life, it takes time to become knowledgable.

---

