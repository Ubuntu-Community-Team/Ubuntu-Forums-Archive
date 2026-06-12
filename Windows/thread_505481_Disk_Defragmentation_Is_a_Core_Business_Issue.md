---
title: "Disk Defragmentation Is a Core Business Issue"
date: 2007-07-20
forum: Windows
---

### Post by Soarer on 2007-07-20
From a "Windows IT Library UPDATE EXTRA" I received today:

 > Thomas's staff recognized that a key to maintaining high levels of performance and speeding file open and save times was to minimize file fragmentation on its hundreds of distributed systems. Fragmentation occurs naturally in all OSs over time. Files are stored as small chunks of data scattered throughout a hard drive instead of as a unified whole occupying a single contiguous area. Eventually, that use of fragmented disk space leads to performance degradation that gradually worsens.

For example, when deleted files open up areas of a hard drive for re-use, portions of new and modified files are saved to those first available open areas. As files grow and are edited and re-saved, they become increasingly fragmented, sometimes being broken into dozens, hundreds, and even thousands of pieces. Access times lengthen as the drive's heads shuttle back and forth across disk platters, reading file fragments in the correct order to re-assemble them in the computer's memory. The continual creation, modification, and deletion of temporary files adds to fragmentation.

Although disk defragmentation might seem to be a technical issue, it's a core business issue. Disk fragmentation is an enormous thief of productivity. Because performance erosion can be easily quantified, you can clearly demonstrate the benefits of regular disk defragmentation. A productivity loss of just 30 seconds per hour because of a slowdown in computer or server performance in a restaurant open 12 hours daily year-round is equivalent to 36.5 hours (47.5 forty-five-minute customer visits). For 900 locations with parties of three people spending an average of $15 apiece, the potential total revenue loss can be $2,137,000 a year, an enormous amount in the restaurant industry, where profit margins are razor thin.

"Fragmentation occurs naturally in all OSs over time." 

Interesting point of view. Expensive too  :)

---

### Post by tgm4883 on 2007-07-20
> **Soarer said:**
> From a "Windows IT Library UPDATE EXTRA" I received today:

 

"Fragmentation occurs naturally in all OSs over time." 

Interesting point of view. Expensive too  :)


I need to install Windows.  I'm missing out on this Fragmentation:)

---

### Post by oldos2er on 2007-07-20
"Fragmentation occurs naturally in all OSs over time." 

 Assume (s)he means all file systems. This begs the question, how does ext3 handle fragmentation? I haven't seen any defrag programs in the repos (not that I've looked!) <g>

---

### Post by az on 2007-07-20
If you substitute the words "have to go to the bathroom" for "fragmentation", the article is funny.

*Having to go to the can is an enormous thief of productivity. Because performance erosion can be easily quantified, you can clearly demonstrate the benefits of regular bathroom visits. A productivity loss of just 30 seconds per hour because of a slowdown of digestion in a restaurant open 12 hours daily year-round is equivalent to 36.5 hours (47.5 forty-five-minute customer visits). For 900 locations with parties of three people spending an average of $15 apiece, the potential total revenue loss can be $2,137,000 a year, an enormous amount in the restaurant industry, where profit margins are razor thin. *



EDIT:  *sorry...*

---

### Post by smoker on 2007-07-20
> "Fragmentation occurs naturally in all OSs over time." 

probably should be all 'window's OSs', i would think!

---

### Post by tgm4883 on 2007-07-20
> **oldos2er said:**
> "Fragmentation occurs naturally in all OSs over time." 

 Assume (s)he means all file systems. This begs the question, how does ext3 handle fragmentation? I haven't seen any defrag programs in the repos (not that I've looked!) <g>

He (Joel Shore) must have meant file systems.  It's my guesstimate that he doesn't know much about computers (or perhaps just anything not windows) which is why he confuses OS's and file systems and doesn't know about non fragmenting file systems.

---

### Post by tgm4883 on 2007-07-20
Or perhaps im wrong.  Still, doesn't mean he knows what he's talking about.

> About the Author
Joel Shore has been writing about technology for 20 years.
He is editor-in-chief of Reference Guide, a professional ser-
vices firm that provides marketing consulting, product test-
ing, and editorial services to manufacturers of technology
products. He was the editor-in-chief of ITworld.com and
co-founding editor and director of the Computer Reseller
News Test Center, has published hundreds of product re-
views and frequently moderates tradeshow and Web panels.


---

### Post by cprofitt on 2007-07-22
[http://en.wikipedia.org/wiki/Defragmentation](http://en.wikipedia.org/wiki/Defragmentation)

For those that think there is no fragmentation in Linux/Unix.

---

### Post by pjkoczan on 2007-07-23
I've seen Unix/Linux fs'es fragment, but not to the consistent and severe degree that Windows fs'es fragment.

The instances I've seen fragmentation were database servers, mail servers, and virtual machines. Basically, large files with frequent updates cause fragmentation. If you study operating systems and file systems, almost no OS/fs can fully avoid fragmentation in this case. While I'm sure that the *nix fs handled it better than Windows would have, it still fragmented.

So, it is a myth that *nix fs'es don't fragment. However, with "normal" desktop usage (i.e. not many big files that keep getting updated), *nix fs'es barely fragment (usually <1%), whereas Windows fs'es seem to fragment even using small, static files. This is where the annoyance and complaints surface.

---

### Post by cprofitt on 2007-07-23
I think one of the issues for NTFS/Windows is the non-sep. partition for the swap file; though I have not tested that theory out.

---

### Post by donkyhotay on 2007-07-25
Most OS's (like linux) use entire partitions for swap while windows uses a large file within the primary partition. Because the swap changes so much it causes fragmentation for the entire drive in general. I might be wrong but this is the reason I've always heard as to why windows gets so badly defragmented while most other OS's don't.

---

### Post by cmat on 2007-07-26
> **donkyhotay said:**
> Most OS's (like linux) use entire partitions for swap while windows uses a large file within the primary partition. Because the swap changes so much it causes fragmentation for the entire drive in general. I might be wrong but this is the reason I've always heard as to why windows gets so badly defragmented while most other OS's don't.

That's incredibly true. The page file really messes up the partition in a hurry. Not to mention I was defragging my XP drive. It had to work around the page file (which was displayed in the GUI of the defrag app I was using) and never was fully defraged because the big hulking file was sitting in a large area of free clusters. I think that was either a poor design decision or MS didn't think it would be user friendly to make people use the partitioner. The swap partition is the way to go.

---

