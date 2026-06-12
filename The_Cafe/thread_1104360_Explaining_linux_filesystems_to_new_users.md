---
title: "Explaining linux filesystems to new users"
date: 2009-03-23
forum: The Cafe
---

### Post by SunnyRabbiera on 2009-03-23
A lot of people when they first use linux seem to always ask about defragmentation, understandable as they are used to Windows and defragging.
A lot of people have tried to explain why Linux filesystems typically dont need defragging.
I have seen some interesting explanations, the most interesting way I have seen someone explain the difference between EXT3 and NTFS is that EXT is like pigeonholes while NTFS is like a string of beads.
A good analysis indeed, the way I see the difference is like this:

EXT and most other Linux filesystems is like a book, or if one must be literal its like a journal (as most linux filesystems are journalized)
This said journal is a composition book, for me its a 75 page composition book.
Currently I use 31 pages in this book, one entry consistent with the next.
On day 1 I ate, drank and slept, same as most other days though on some days I do more then others.
On day 6 I had to go into work at 6:00AM, on Day 12 I had to go to the supermarket.
But most of my entries are organized and the flow of my entries are similar.

NTFS and FAT is more like a series of Post it notes on my refrigerator.
Note 1 says get milk
Note 2 says get eggs
Note 3 says pick up the kids from soccer practice
Note 4 says what I will make for dinner tonight
While my journal explains what I did that day, my post it notes tell me what I have to do today...
It still gives me the same info, my journal says I went to to the store to pick up the eggs while my post it note tells me that I need eggs.
But once I got those eggs that post it note becomes unneeded, but what if I forget to take that post it note down and the following day I go out to the store to buy eggs again forgetting I picked up eggs the other day.
My journal says I already got those eggs, but my post it note says otherwise.
The confusing gets worse when I start running out of room on my refrigerator and I dont take down all those other post it notes that I made and when I make a new post it note telling me to do the laundry today and put it on the refrigerator and all my other post it notes fall down.
This is a big issue, not only do I have all these post it notes on the floor but I cannot tell what day they are from as I never put any dates on my post it notes, just things I had to do on that day...
I didnt think of the long term when I made those post it notes.

My journal keeps my records of what I did that day better then my post it notes, because I have the date and time numbered in my journal but these post it notes I have are so tiny I dont have room to put a date on them and I have big bold handwriting.
When I drop my journal on the floor its very easy to find where I left off at if I lost my place but my post it notes are in chaos.

How would you explain the two?

---

### Post by Icehuck on 2009-03-23
I would be careful in wording this statement

> EXT and most other Linux filesystems is like a book, or if one must be literal its like a journal (as most linux filesystems are journalized)

EXT2 is not journaled, but EXT3 is. I know it's not a major thing, but it could lead to confusion.

---

### Post by SunnyRabbiera on 2009-03-23
Thats why I said most are journalized, but I didnt say all.
EXT2 should not come up for the new user much anyway though, its pretty much phased out these days.

---

### Post by Therion on 2009-03-23
[The Single Best (Graphical!) Explanation for This I've Yet Found](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by SunnyRabbiera on 2009-03-23
> **Therion said:**
> [The Single Best (Graphical!) Explanation for This I've Yet Found](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Yes but even that tends to be on the technical side, I tend to use non tech terms to explain things like saying Windows is like Cocoa cola and Linux is like Joe's home made soda pop.

---

### Post by Rokurosv on 2009-03-23
I think that's pretty clear for an explanation

---

### Post by Therion on 2009-03-23
> **SunnyRabbiera said:**
> Yes but even that tends to be on the technical side, I tend to use non tech terms to explain things like saying Windows is like Cocoa cola and Linux is like Joe's home made soda pop.
As do I, but at some point when dealing with technicalities such as file structure on a hard drive you're going to have to move away from "Dick, Jane and Spot".  

Simple analogies are fine as far as they go, and your example above works just fine for the matters it addresses (Windows vs. Linux). 

Some subjects, however, are not so easily reduced; like file structure on a hard drive.

---

### Post by SunnyRabbiera on 2009-03-23
Thats why I used the composition book vs post it note comparison.

---

### Post by MikeTheC on 2009-03-24
Usually, I just neuralize them and make them think that wasn't a question they wanted to ask. It makes conversations much shorter that way. ;)

---

### Post by mocoloco on 2009-03-24
[Here ya go]("http://www.whylinuxisbetter.net/items/defragment/index.php?lang=").  Lots of other good stuff on that site for those contemplating the switch too.

---

### Post by billgoldberg on 2009-03-24
> **SunnyRabbiera said:**
> Thats why I said most are journalized, but I didnt say all.
EXT2 should not come up for the new user much anyway though, its pretty much phased out these days.

It's getting a second life on the ssd drives.

---

