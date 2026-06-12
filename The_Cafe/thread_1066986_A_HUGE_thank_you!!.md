---
title: "A HUGE thank you!!"
date: 2009-02-11
forum: The Cafe
---

### Post by sydbat on 2009-02-11
As the title states, I want to give a HUGE thank you to this forum! There is such a wealth of information here, that I was able to do something with my Ubuntu box that I never thought could be done.

My story...thus far...

I had a dual boot (XP, Ubuntu) and found I never used XP...so I decided to get rid of it. I had about 5 NTFS partitions in XP, because it helped keep things separate enough if anything went wrong with the OS itself. Using Linux, this scheme got annoying (as all you really need is / and /home).

So I searched to see if there was anything I could use and came across two very informative threads...
caljohnsmith [in this thread]("http://ubuntuforums.org/showthread.php?t=1050356&highlight=remove+fstab") about removing Windows (posts 4 and 6)
cariboo907 [in this thread]("http://ubuntuforums.org/showthread.php?t=1060121&highlight=grub+error+15+reinstall") about reinstalling grub (post 3)

I formatted the XP partition (sda1 - primary) to ext3, copied / (sda5 - extended) into it, deleted it and all the extraneous NTFS partitions (don't worry, everything was backed up on a separate drive) and the original / partition, then grew /home into the newly free space (212GB). It took awhile (like 3 hours altogether), but now I am Windows free.

Then came the fun part. Tried reinstalling grub via the Live CD, but it didn't work...kept getting Error 15 (for some reason, grub was found in the wrong place...hd1,0). Another quick forum search and voila...the answer presented itself again! 

Although I cannot find the thread/post (funny that it was on the first page when I needed it!--thanks to the person whose helpful post fixed everything), it basically said to boot normally, then when you get error 15 go back to the grub menu, type "c" and find grub (really in hd0,0), then esc, then "e" and change grub there. After booting into Ubuntu, make this change permanent with sudo gedit (and don't forget to make sure #groot is changed too).

I chose to post this in the Cafe because Testimonials is often overlooked, and I wanted many people to know that this is a wonderful, helpful community.

---

