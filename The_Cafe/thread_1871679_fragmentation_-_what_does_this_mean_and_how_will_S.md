---
title: "fragmentation - what does this mean and how will SSDs effect linux"
date: 2011-10-29
forum: The Cafe
---

### Post by F.G. on 2011-10-29
hi folkes,

so I thought that this might be interesting for discussion and i curious about the truth of the matter, so here goes (this is my understanding):

External Fragmentation: this is what NTFS / windows suffers from and is where dynamically allocated memory chunks are freed, however are no longer usable as a result of their non-standard small size. also i think the NTFS system preferentially stores data in the 'next' space on the HDD ie consecutively, like a big stack.

Internal Fragmentation: this is what Linux suffers from inodes are use to create linked trees of data each of the nodes and leaves are a standardized size therefore when they are freed the space can easily be used by another program. this gets rid of any eternal fragmentation however as a result of the standard size of memory blocks there is typically unused memory which is allocated to each program and not usable by any other program. like each customer in a store having a basket with unused space in it, the store has only so many baskets, and the customers cannot share their unused basket space.

SSDs: apparently these do not suffer from fragmentation (i don't know how, but this is what i heard). this is presumably referring to external fragmentation. does this mean that inodes and the memory organization used by linux are now a weakness (as the fragmentation is logical and therefore still applicable). 

any help on understanding this issue are most welcome.

edit - so I just realised that the title should read 'affect', not 'effect'. sorry to all you grammarians.

---

### Post by Gremlinzzz on 2011-10-29
SSDs do not benefit from defragmentation because there is little benefit to reading data sequentially (beyond typical FS block sizes) and any defragmentation process adds additional writes on the NAND flash that already have a limited cycle life:popcorn:

---

### Post by F.G. on 2011-10-29
ok, this is pretty much what i thought, but still supports the idea that fixed size memory allocation is no longer useful with SSDs.  

also about the limited life cycle, i read in another thread that you could write continuously to a SSD for 40 years before exhausting this, and this as a practical issue is essentially mythological.

---

### Post by mips on 2011-10-29
> **F.G. said:**
> 
also about the limited life cycle, i read in another thread that you could write continuously to a SSD for 40 years before exhausting this, and this as a practical issue is essentially mythological.

The life of a ssd exceeds that of normal hard drives so I don't see the issue.

---

### Post by del_diablo on 2011-10-29
SSDs need defragmentation, but the defrag algorithms for most filesystems only works for normal spinning disks, meaning that a lot of information would be poorly and wrongly allocated things on the SSD if defragged by most applications. That means that after defragmention, the cleanup algorythm on the SSD would need to reallocated almost everything, resulting in weardown and time used for this move.
It also results in a slowdown of writing to the disk because of the way the allocation is done.

Perhaps LogFS and some other flash filesystems are good enough soon, we nobody will sit down and benchmark them to figure that out.

---

### Post by wolfen69 on 2011-10-29
> **Gremlinzzz said:**
> already have a limited cycle life :popcorn:

If you consider writing to the disk 24/7 for at least 8 years limited, then yes. At this point, I would trust an ssd before a mechanical HD.

---

### Post by F.G. on 2011-10-29
hey, so i saw this link in another thread:

[http://elitepcbuilding.com/ssd-vs-hdd](http://elitepcbuilding.com/ssd-vs-hdd)

it indicates that that SSDs can sustain continuous writes (24/7) for 40 years (rather than 8) which is easily enough for me. 
though this isn't really what this thread was asking about, what i'm wondering about is fixed vs dynamic memory allocation inodes and fragmentation in SSDs.

---

### Post by Spr0k3t on 2011-10-29
SSD drives should remain heavily fragmented due to how they store data... there is a leveling feature of the drive which helps push the lifespan out to 10+ years.  Defragmenting the drive will kill it over time.  It stores the data like a water table.

---

### Post by Copper Bezel on 2011-10-29
Isn't F.G.'s OP correct, though? SSDs don't have a problem with fragmentation, since the physical location doesn't matter, but Linux filesystems still take more space on disk to store the same amount of data, as a result of being designed to *avoid* fragmentation. It doesn't really matter, of course, but it's a fair observation.

Windows isn't using NTFS in 8, though, so ext4 vs. NTFS isn't really important.

---

### Post by Gremlinzzz on 2011-10-29
Do SSDs Slow Down Over Time?Yes. But that's just the short answer. Solid state drives, or SSDs, have often been hailed as a fast, cheap future for memory... but they have one critical flaw: a gradual slow down and corruption over time. Here's an overview of the problem, and some of the things being down to alleviate this.

[http://www.brighthub.com/computing/hardware/articles/43400.aspx](http://www.brighthub.com/computing/hardware/articles/43400.aspx)
:popcorn:


Defragmenting or "defragging" a SSD takes up many write/erase cycles... which shortens the lifetime of an SSD,

---

### Post by Paqman on 2011-10-29
> **Gremlinzzz said:**
> 
[http://www.brighthub.com/computing/hardware/articles/43400.aspx](http://www.brighthub.com/computing/hardware/articles/43400.aspx)


Er, not a great article. No mention of TRIM, which directly addresses the problem.

---

### Post by del_diablo on 2011-10-29
> **Gremlinzzz said:**
> [http://www.brighthub.com/computing/hardware/articles/43400.aspx](http://www.brighthub.com/computing/hardware/articles/43400.aspx)
:popcorn:

Thats a scaremonger article.
Or to be precice: Sunlight gives you cancer, its just that you need to be exposed to a extreme dose in order for it to gain a large enough chance of actually manifesting cancer.
For SSDs the problem can be simplied to a few core items:
[LIST=1][*]First problem is that the first 3 generations fo SSDs suffered from a extremely limited amount of writecycles, which has resulted in a urban myth about the SSD not being able to sustain and writecycles before becoming read only and slow
[*]The second problem is that there is a huge variation on how the firmware and controllers affect the lifetime and performance of the disk
[*]A third problem is that  nobody has sat down and marked where the performance decreases begin on the current generation of SSDs. Going from just reading around my peers I can currently claim that it has not been reached for the current generation, so we can assume that the next generation of SSDs might just kill the entire proble, IF that is a priority.
[*]Another problem is that SSDs are a "premium" ware for most people, mainly because computers are not shipped with a SSDs by default. Its not the typical kind of problem, but it doesn't help.[/LIST]

> Defragmenting or "defragging" a SSD takes up many write/erase cycles... which shortens the lifetime of an SSD,

A defrag takes exactly 1 write cycle away from the disk.
But due the way the data gets allocated the SSD needs either to do TRIM or garbage collection and hence doing yet another write to the disk to fix the allocation problem.
If the SSD had a filesystem that was tuned for flash disks, the problem would not have existed: You implent garbage collection and "this file should get deleted" as features, add in a few flash optimizations, and perhaps a auto defragging when it moves around the files allocation.

---

### Post by Gremlinzzz on 2011-10-29
Thats a scaremonger article.
well it is Halloween time but whats the purpose of putting out a scaremonger article about  SSDs?seems the article knows allot about em.
:popcorn:

---

### Post by del_diablo on 2011-10-29
I find to be saying "Something bad will be happening at some time, somewhere" to be to give people the idea of there exists some threat, even if it doen't exist.
If you skim read the article it says: "There is some quite large hardware issues that you will notice quite fast."
If you read the article properly you notice it never says when it will hit you, or how relevant it is. It does not mention if the performance degrading could mean that it gets slower than a normal spinning magnet disk, or if its just a 15% slowdown.
So basically the problem with the article can be simpliefied down to the fact that it lacks a conclusion.

---

### Post by 3Miro on 2011-10-29
What the OP calls "Internal Fragmentation" becomes a problem only if the file system is close to full, in which case any file system will suffer. Ext4 comes with 5% reserved space that guards against that. I doubt this is a real problem.

Assuming there really is a problem: The file allocation algorithm is part of the file system, but it can easily be replaced. If this becomes a problem, it will be fixed with a kernel patch, it doesn't require reinvention of Linux.

---

### Post by Nixarter on 2011-10-30
> **mips said:**
> The life of a ssd exceeds that of normal hard drives so I don't see the issue.

They have limits to cycles, but not moving parts.  They are more durable in some ways, and not so much in others.  Some log files get written to very often, so these regularly go over the few-hundred-thousand-write- life expectancy.  It just depends on how you use them.  Software manages this as well to help.

In general I agree, but it depends on a lot of things.

---

### Post by 3rdalbum on 2011-10-30
> **F.G. said:**
> also about the limited life cycle, i read in another thread that you could write continuously to a SSD for 40 years before exhausting this, and this as a practical issue is essentially mythological.

Recent technology in SSDs hasn't been around for 40 years, so I don't know how they can actually measure this for the real-world. Maybe they should be able to do it in theory, but who actually knows what the SSD will do in the real world?

I remember how the data on CD-Rs was meant to last for 20 years or more. I also remember backing up my hard disk onto CD-Rs that became totally unreadable within five years, even with careful storage and rarely being read.

An "in theory" figure is not good enough, and I'd be willing to bet that your "it'll last 40 years" SSD will be total junk in under 10 years of normal use.

---

### Post by Nixarter on 2011-10-30
I've noticed that some hard drive manufacturers claim to have mean time between failure rates estimated to within a single hour...  and it just so happens to be EXACTLY the same hour as, for instance, completely different models, and completely different manufacturers.

It's all complete and utter BS.  They just assume people have never taken a basic statistics course.  The sad thing is that many people haven't, so they "believe" in those numbers.  And I say believe because that is what it is, as there is no evidence, it is simply on faith.

---

### Post by Paqman on 2011-10-30
> **Nixarter said:**
> I've noticed that some hard drive manufacturers claim to have mean time between failure rates estimated to within a single hour...  and it just so happens to be EXACTLY the same hour as, for instance, completely different models, and completely different manufacturers.


MTBF is a pretty rough measure of reliability. Used on its own it's almost a useless metric for comparing between different systems. For a start it's only a mean value, it doesn't tell you what the actual rates of failure are at any particular time. Generally speaking failure rates are high at the start of life, then drop off sharply. They then climb towards the end of life, but the actual shape of the curve varies greatly, so taking the whole thing and averaging it doesn't really tell you a whole lot.

---

