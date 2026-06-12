---
title: "Dual booting UbuntuStudio + XP on a Thinkpad"
date: 2008-05-27
forum: Ubuntu Studio
---

### Post by kawasakiguy37 on 2008-05-27
I already have Xp installed just as I would like it on my Thinkpad R61. Consequently, I do not want to lose this install when installing Ubuntu Studio. I stupidly did not create two partitions when I repartioned the laptop, so first of all, what is the best (and safest) way to repartion this machine? Ive looked at a few guides, and I am currently conflicted between using two methods:

1. Just splitting up my HD into two separate and equal partitions (one for windows, one for Xp) or

2. Creating a windows install partition, and then a Ubuntu Partition with the main portion of the drive and then using fs-driver to have windows be able to access and read the Ubuntu EXT partition.

I have a few questions about the above two variants: If I use method two and use fs-driver, how "fast" will Xp be able to read the Ubuntu shared data partition in comparison to a normal NTFS partition? The main use for my laptop will be school (Film major), and I also casually game as well (mostly stuff on steam, I have a desktop for more powerful games) so speed is a must. Also, is there a more optimal way I could breakup the partition space?

Finally, I have one last question. In looking at different installation instructions I realized it would be ideal to set a separate partition for the "swap" file of Ubuntu (Which Im assuming is analagous to the paging file of windows). If I set a 3-4 gig swap file ( I have 2 gigs of installed ram ), can I set Xp to use this same partition for its paging file? I would like to get optimal performance out of both OS's. Sorry for all the questions, any help you guys can give me would be great. Thanks!

edit: O and btw, I am using the latest version of Ubuntu Studio (Dling as we speak), alernate 64 bit edition disk.

---

### Post by logos34 on 2008-05-27
I vote for #2.  Make windows C: ~10gb+.  Create an **extended** partition out of the rest of disk space and stick ubuntu root, swap and shared partitions inside. Fs-driver with ext3.  But I'm not sure whether windows is much slower accessing ext3 than linux with ntfs.

More than 2gb swap is overkill.  (remember, the 2 x ram rule is old; it only applies up to around 1gb.  Besides, linux runs much lighter than windows)

I don't believe you can share swap/paging files space.  windows needs ntfs or fat, linux uses linux-swap format

---

### Post by kawasakiguy37 on 2008-05-27
Alright, that sounds about right. I might opt to make the XP partition larger to ensure games run smoothly (I think I could handle videos encoding a bit slower, its not like ill be sitting at the machine anyways and I do have a desktop as well). Ubuntu can access NTFS without any addons, correct?

can the partition program (manual mode) that comes with ubuntu studio do everything that I need, or do I need to get a third party program?

---

### Post by prismatic7 on 2008-05-27
> **kawasakiguy37 said:**
> I already have Xp installed just as I would like it on my Thinkpad R61. Consequently, I do not want to lose this install when installing Ubuntu Studio. I stupidly did not create two partitions when I repartioned the laptop, so first of all, what is the best (and safest) way to repartion this machine? Ive looked at a few guides, and I am currently conflicted between using two methods:

1. Just splitting up my HD into two separate and equal partitions (one for windows, one for Xp) or

2. Creating a windows install partition, and then a Ubuntu Partition with the main portion of the drive and then using fs-driver to have windows be able to access and read the Ubuntu EXT partition.

The installer should offer a resize option, which will keep your existing data. It's text-based though, so if you'd prefer to have a graphical display of the trauma you're about to inflict on your hard drive (j/k) you should probably use a LiveCD with Partition Editor on it (gparted ROCKS!)

In any case, installing Windows first and Ubuntu second is the best way to go about this process, so you've scored there :)

> **kawasakiguy37 said:**
> I have a few questions about the above two variants: If I use method two and use fs-driver, how "fast" will Xp be able to read the Ubuntu shared data partition in comparison to a normal NTFS partition? The main use for my laptop will be school (Film major), and I also casually game as well (mostly stuff on steam, I have a desktop for more powerful games) so speed is a must. Also, is there a more optimal way I could breakup the partition space?

I'm not sure about fs-driver, so I hope someone else can help you there. You should be able to read the NTFS partition in Ubuntu, though, if that helps. On a laptop, where you only have one hard disk - and that is usually a slower one - there's not really an optimal partition method, apart from placing your swap at the end of the disk.


> **kawasakiguy37 said:**
> Finally, I have one last question. In looking at different installation instructions I realized it would be ideal to set a separate partition for the "swap" file of Ubuntu (Which Im assuming is analagous to the paging file of windows). If I set a 3-4 gig swap file ( I have 2 gigs of installed ram ), can I set Xp to use this same partition for its paging file? I would like to get optimal performance out of both OS's. Sorry for all the questions, any help you guys can give me would be great. Thanks!

Linux swap is not really like a paging file - it's actually a totally different filesystem type (as opposed to a special file) and for Windows to use it, it would have to be reformatted every time you booted into one OS or the other. There are other, technical differences, but I won't list them all here!

> **kawasakiguy37 said:**
> edit: O and btw, I am using the latest version of Ubuntu Studio (Dling as we speak), alernate 64 bit edition disk.

Welcome to the clan!

---

### Post by logos34 on 2008-05-27
> **kawasakiguy37 said:**
> Ubuntu can access NTFS without any addons, correct?

yes, ntfs-3g is included but you might want to add the **ntfs-config** gui frontend 
> 
can the partition program (manual mode) that comes with ubuntu studio do everything that I need,?

**Gparted** on the livecd should work fine 
(System>Admin>partition editor)

---

### Post by kawasakiguy37 on 2008-05-28
Is Ubuntu Studio a live CD? (the 64 bit ISO image, its about a 1 gig in size, says its the 'alternate' cd.)

So I just burn as an image and then boot from the Ubuntu Cd, correct?

---

### Post by prismatic7 on 2008-05-28
> **kawasakiguy37 said:**
> Is Ubuntu Studio a live CD? (the 64 bit ISO image, its about a 1 gig in size, says its the 'alternate' cd.)

So I just burn as an image and then boot from the Ubuntu Cd, correct?

It's not a LiveCD - it's an installer DVD.

---

### Post by kawasakiguy37 on 2008-05-28
Does it still then contain the necessary software to partition? Sorry for the confusion here

---

### Post by prismatic7 on 2008-05-28
> **kawasakiguy37 said:**
> Does it still then contain the necessary software to partition? Sorry for the confusion here

Sorry - my mistake... Yes, it includes a partitioner, but it's text-based rather than graphical. It can take some effort to get your head around, and if you're worried about losing data I wouldn't recommend it without making a VERY complete backup. If you'd rather not download an Ubuntu 8.04 LiveCD just for gparted, there is a smaller [gparted LiveCD](http://gparted.sourceforge.net/livecd.php) but I haven't used it since a couple of years ago, so I don't know how well it works.

---

### Post by kawasakiguy37 on 2008-05-28
Text based is fine, I usually actually prefer that sort of thing, as long as its fairly straightforward and not crazily complicated. I dont have any SUPER important data I really need, I jus tdont want to go through the process of reinstalling Xp and all of the programs and settings I like (which takes way longer than it really should).

---

### Post by logos34 on 2008-05-28
sorry for contributing to any confusion when I mentioned running gparted form 'livecd'--forgot you wanted UbuntuStudio, which of course comes with only a text-mode installer. (By the way I run x64 Ubuntustudio).

It's not too much more complicated if you know what to expect.  I'd go with 'guided' partitioning option, which will shrink your windows partition. (make sure to defrag and run error check on windows first).

Take a look here: 
[http://www.howtoforge.com/the_perfect_desktop_ubuntustudio_7.10](http://www.howtoforge.com/the_perfect_desktop_ubuntustudio_7.10)
(nothing much has changed in hardy)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
(-->partitioning section)

Good luck!

---

