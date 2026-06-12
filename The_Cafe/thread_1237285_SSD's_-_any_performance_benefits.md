---
title: "SSD's - any performance benefits?"
date: 2009-08-11
forum: The Cafe
---

### Post by starbase1 on 2009-08-11
I've always been interested in computer performance, it's a big part of my day job. And on the hobby front I like 3d graphics, and you can never get too much horsepower there! 

And I have noticed that the price of solid state drives has come down to the point where they are getting very affordable indeed at small sizes.

The relatively small sizes make them unsuitable for piles of data, but seem more than enough for an OS and lots of applications. But are there any real world performance benefits?

To be even more specific, are there any performance benefits if you already have plenty of memory? I can see how a faster swap file would be generally handy, but in these days where memory is cheap anyone who cares about performance probably have maxed out the motherboard anyway...

And I would expect any well written OS, (or even some of the rougher ones) to get frequently accessed files cached and keep them in memory...

Nick

---

### Post by mcduck on 2009-08-11
3D graphics are mainly about raw CPU power (or GPU power, if you use software that allows using GPU for rendering), and having enough memory to fit all your data in it.

On the other hand, SSD drives give better random access times for small files than hard disks do. This gives faster startup times for programs, but apart from that no real performance benefits when it comes to actual, number crunching.

So no, getting a SSD drive would not give you any better performance for 3D rendering. Of course if you have plenty of money around getting one would make your normal desktop use nicer, decreasing both OS and program startup times.

---

### Post by ssam on 2009-08-11
some ssd are better than others. read some comparisons, eg
[http://www.phoronix.com/scan.php?page=article&item=ocz_agility_120gb&num=1](http://www.phoronix.com/scan.php?page=article&item=ocz_agility_120gb&num=1)
[http://torvalds-family.blogspot.com/search?q=ssd](http://torvalds-family.blogspot.com/search?q=ssd)

---

### Post by JohnFH on 2009-08-11
The benefits of SSDs are more seen in laptops or netbooks where power consumption and noise are both big factors.  The main advantages of SSDs are not to do with performance but they use less power and are silent.

---

### Post by dragos240 on 2009-08-11
Well there is a great advantage if it's in a laptop/netbook, if you drop it, no need to worry about damaged heads.

---

### Post by starbase1 on 2009-08-11
Well, my approach to boot time issues is to never turn the computer off!
:P

---

### Post by Grenage on 2009-08-11
SSD's trounce physical disks on performance, and they are the future.  If you're in need of fast disk access, go down that route; if you're not, don't bother until they are cheaper.

---

### Post by starbase1 on 2009-08-11
But what applications will actually push disks that hard these days, apart from big database queries?

---

### Post by Grenage on 2009-08-11
> But what applications will actually push disks that hard these days, apart from big database queries?

That's a valid question, and for your average user, it won't make too much difference.  Then again, seek times are a lot faster too; there's a good reason a lot of us run RAID configurations, it really really makes the computer much quicker to use.

For pure data transfers, game loading is a big one.

---

### Post by mcduck on 2009-08-11
> **starbase1 said:**
> But what applications will actually push disks that hard these days, apart from big database queries?

Hardly anything, apart from starting the programs (or operating systems).

Perhaps some multi-channel audio recording, but that's more about writing performance which isn't as great as the reading speed on SSD's (and most people who do that run some RAID setup anyway and need more disk space than what they could afford to buy as SSD drives). All video-related stuff seems to be more limited by processing power than I/O speeds.

---

### Post by JohnFH on 2009-08-11
> **Grenage said:**
> SSD's trounce physical disks on performance, and they are the future.  If you're in need of fast disk access, go down that route; if you're not, don't bother until they are cheaper.

No they don't trounce rotating disks.  They are better in read performance, but random write access is worse in many cases.  (BTW, solid state disks are physical too, but I knew what you meant).

There seems to be a lot of confusion over SSD vs rotating disks.  Many claim they are faster and in many respects they are, but not always.  Here's an excellent article that runs into many pages exploring various claims about SSDs:  [http://www.anandtech.com/storage/showdoc.aspx?i=3531]("http://www.anandtech.com/storage/showdoc.aspx?i=3531").  Did you know that SSDs slow down dramatically as they are used?  Have a read - very interesting.

---

### Post by Grenage on 2009-08-11
Touché on the physical. :)

You are correct that rotating discs are sometimes slower, but overall the performance on a decent SSD is quite a lot higher (relative to hard drive benchmarks).  That's providing you get a modern SSD with all the TRIMmings (*boom*tish*); those won't slow down over time.

---

### Post by Stan_1936 on 2009-08-11
> **JohnFH said:**
> ....SSDs slow down dramatically as they are used....

There are ways to counter that...

If you decide to buy an SSD, you NEED to read up on how to maintain* your drive BEFORE purchasing it!  This isn't one of those plug-n-play deals......your SSD will suffer if you do that, and your $200 will be .....well not worth it.

* - drive maintenance in Linux is not even half as mature as it is in Windows......Windows 7, for example, offers TRIM suipport out of the box.  This can ONLY be put to use IF your SSD has a version of firmware that provides HARDWARE TRIM support.  Even if it does provide hardware TRIM support, if you are using Linux, you'll be out of luck as TRIM for Linux = nothing of the sort currently exists in a stable form!

The average user would most certainly not know any of this and end up complaining that the SSD speed has reduced.

---

