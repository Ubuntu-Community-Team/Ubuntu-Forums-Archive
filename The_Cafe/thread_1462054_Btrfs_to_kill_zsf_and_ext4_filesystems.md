---
title: "Btrfs to kill zsf and ext4 filesystems"
date: 2010-04-25
forum: The Cafe
---

### Post by madjr on 2010-04-25
the zsf and ext4 killer:
[http://www.youtube.com/watch?v=Q5O98CQOS1I](http://www.youtube.com/watch?v=Q5O98CQOS1I)


zsf and time slider gnome integration overview
[http://www.youtube.com/watch?v=jfCtqX8dQtk](http://www.youtube.com/watch?v=jfCtqX8dQtk)


some butter for me please

[Btrfs article from phoronix]("http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1")

---

### Post by toupeiro on 2010-04-25
yes, use youtube as your definitive source for the lifelines of "ZFS" and ext4..

---

### Post by Gone fishing on 2010-04-25
I don't think madjr said youtube was his definitive fie system guide. But I'm interested in this topic Linus described ZFS as the best thing about Opensolaris [http://lwn.net/Articles/237905/](http://lwn.net/Articles/237905/). I use a Linux software Raid and it isn't always without problems e.g. [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375)

Zfs sounds very interesting to me as does Btrfs which is be the next replacement for Ext4? Anyone any experience of Btrfs? Haiku has a good filesystem can that be ported to Linux?

---

### Post by Paqman on 2010-04-25
Fedora has support for Btrfs as a tech preview, but the reports from people who've kicked he tyres indicate it's still got a way to go. Looks like it'll be great when it's stable though.

---

### Post by toupeiro on 2010-04-25
Oh don't get me wrong, I'm an avid fan of ZFS.  I use it at work.  It's everything a local filesystem should be and then some, and its very easy to manage!  What I've seen of, and whom I've talked to professionally, say btrfs has a lot of *promise* to be very good but its going to take a lot of work to get there..  ZFS is here, now, working amazingly, and is ridiculously scalable.  

ext4, lets face it, there's no indication that the ext filesystem lineage is going anywhere.  Its just all unprecedented claims to come on here touting btrfs is going to end the longest lineage and most widely used of all linux filesystems in ext#, and one of, if not **_the_** most robust, enterprise class filesystem that is ready for primetime and attainable at 0 cost to desktops and datacenters.  No matter how many youtube video's get made. :P  Like it all you want, hell love it, but don't get crazy. :)

---

### Post by NightwishFan on 2010-04-25
I do not really have need for many of it's features such as cloning. The online defrag is cool, but ext4 will have that as well. I switched from xfs to ext4 since 2.6.31 kernel.

---

### Post by Linuxforall on 2010-04-25
Sadly the unsung hero here is Reiser which is truly an excellent file system but due to the unfortunate circumstances, we may never ever get to enjoy its benefits and speed again, I had installed Hardy with reiser and file access was the quickest ever compared to today's ext4.

---

### Post by sdowney717 on 2010-04-25
> The principal developer of the ext3 and ext4 file systems, Theodore Ts'o, has stated that ext4 is simply a stop-gap and that Btrfs is the way forward,[9]  having "a number of the same design ideas that reiser3/4 had".[10]


[http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

simply stated BTRFS will supercede EXT4 and uses similar ideas to reiser

---

### Post by Xbehave on 2010-04-25
> **Linuxforall said:**
> Sadly the unsung hero here is Reiser which is truly an excellent file system but due to the unfortunate circumstances, we may never ever get to enjoy its benefits and speed again, I had installed Hardy with reiser and file access was the quickest ever compared to today's ext4.
while reiser4 may never make it into the mainline due to politics, btrfs is a reiser-like fs and it's main developer was a reiserfs developer, so reiserfs lives on IMHO.


I've been using btrfs for a while and without GUI tools to integrate it at all levels it's not noticeable different from ext4 (hell the GUI tools will play nicely with lvm anyway)

---

### Post by Gone fishing on 2010-04-25
> while reiser4 may never make it into the mainline due to politics

Or a murder case [http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser) - but reiser was a well respected file system presumably GPL so why was it not forked?

---

### Post by sdowney717 on 2010-04-25
tainted with the baggage associated with the murder, personal pride and interpersonal frictions killed any significant desire to prove the system amd mainstream it into the kernel. From what I read.

---

### Post by Xbehave on 2010-04-25
> **Gone fishing said:**
> Or a murder case [http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser) - but reiser was a well respected file system presumably GPL so why was it not forked?
It was/is maintained by others, the truth is it wasn't just the politics tho the fs didn't do things the kernel way and required a lot of changes, reiser himself didn't help matters by not coperating much with the people trying to review the code, plus the plugin system while amazing was also thought to be a backdoor to so reiser's company could sell proprietary plugins.

you can get reiser4 patches for 2.6.23-2.6.33 [here]("http://kernel.org/pub/linux/kernel/people/edward/reiser4/reiser4-for-2.6/")

edit: did -> didn't

---

### Post by Gone fishing on 2010-04-25
> [Reiser4]fs did do things the kernel way 

Is there a non too technical way of explaining this?

---

### Post by Xbehave on 2010-04-25
> **Gone fishing said:**
> Is there a non too technical way of explaining this?
Im not a kernel hacker, all my knowledge comes from blogs/etc, here are a few links that may explain my POV (i know this is a bit of a cop out but anything else is in effect just going to be reposting these anyway)

[Style]("http://kerneltrap.org/node/5679")
> most of my customers remark that Namesys code is head and shoulders above the rest of the kernel code. So yes, it is different." Alan Cox [interview] replied that while the kernel coding style isn't his own style, he tries to follow it when working on the kernel, "one big reason we jump up and down so much about the coding style is that its the one thing that ensures someone else can maintain and fix code that the author has abandoned, doesn't have time to fix or that needs access to specific hardware the authors may not have." 
[Pluggins]("http://kerneltrap.org/node/5330")
[Politcs]("http://lwn.net/Articles/152548/")
> "What happened later on" is that the reiser3 developers moved on to reiser4; not only did they stop maintaining the code, but they actively opposed updates made to the code by other developers. At this point, reiser3 is almost entirely maintained by non-Namesys developers. In the future, the same thing may well happen with reiser4. 
[General info]("http://kernelnewbies.org/WhyReiser4IsNotIn#head-f3604df8adecf748414145677d72149f9b7af013") ([more technical counter point by reiser]("http://lkml.org/lkml/2006/7/21/109"))

---

