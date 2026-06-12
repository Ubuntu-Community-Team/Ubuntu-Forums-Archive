---
title: "Windows 7 HD = Dumb?"
date: 2009-12-27
forum: The Cafe
---

### Post by user1397 on 2009-12-27
So if I go to 'Computer' in the start menu, and right click -> properties on my C drive, it says I am using 29.4 GB (and this is after defragmenting several times)...

...but if I go into my C drive and select everything (including hidden stuff) and right click -> properties, it says the total size is only 15.4 GB.

Where are those extra 14 GB?

---

### Post by Hwæt on 2009-12-27
> **ubuntuman001 said:**
> So if I go to 'Computer' in the start menu, and right click -> properties on my C drive, it says I am using 29.4 GB (and this is after defragmenting several times)...

...but if I go into my C drive and select everything (including hidden stuff) and right click -> properties, it says the total size is only 15.4 GB.

Where are those extra 14 GB?

The icon?

---

### Post by Exodist on 2009-12-27
> **ubuntuman001 said:**
> So if I go to 'Computer' in the start menu, and right click -> properties on my C drive, it says I am using 29.4 GB (and this is after defragmenting several times)...

...but if I go into my C drive and select everything (including hidden stuff) and right click -> properties, it says the total size is only 15.4 GB.

Where are those extra 14 GB?
Possibly cached junk and/or area reserved for virtual memory.



> **Hwæt said:**
> The icon?
LMAO..

---

### Post by CharlesA on 2009-12-27
Page file or system restore points more then likely.

Also, you do know that defragging doesn't free space, right?

EDIT: Checked mine, It's using 8Gigs for paging and 8gigs for system restore. That's about right, since the files on my C drive total around 28GB and I've got 50GB used.

---

### Post by ctrlmd on 2009-12-27
> **CharlesA said:**
> Page file or system restore points more then likely.

Also, you do know that defragging doesn't free space, right?

EDIT: _Checked mine, It's using 8Gigs for paging and 8gigs for system restore_. That's about right, since the files on my C drive total around 28GB and I've got 50GB used.
where did you see those details ? :confused:

---

### Post by TheLions on 2009-12-27
> **ctrlmd said:**
> where did you see those details ? :confused:

just type ```
fdisk -l
``` in your terminal! :lolflag:

OT:
You can see that here: 
[IMG]http://www.itechtalk.com/picture.php?albumid=422&pictureid=2463[/IMG]

---

### Post by ctrlmd on 2009-12-27
> **TheLions said:**
> just type ```
fdisk -l
``` in your terminal! :lolflag:

OT:
You can see that here: 
[IMG]http://www.itechtalk.com/picture.php?albumid=422&pictureid=2463[/IMG]

:lolflag:thx i was lost

---

### Post by CharlesA on 2009-12-27
> **TheLions said:**
> just type ```
fdisk -l
``` in your terminal! :lolflag:

But it says "Bad command or file name."

Why does it want my name?!?

:lolflag:

---

### Post by pwnst*r on 2009-12-27
> **ubuntuman001 said:**
> So if I go to 'Computer' in the start menu, and right click -> properties on my C drive, it says I am using 29.4 GB (and this is after defragmenting several times)...

...but if I go into my C drive and select everything (including hidden stuff) and right click -> properties, it says the total size is only 15.4 GB.

Where are those extra 14 GB?

/fail

---

### Post by cprofitt on 2009-12-27
Windows 7 / Vista uses Volume Shadow copies, unless you turned them off, and those will take up space as well.

---

### Post by kerry_s on 2009-12-27
:lolflag: you know what they say, it keeps a secret history of everything you do from the first day you log in, it's going to need a lot of space for me. :lolflag:

---

### Post by Dayofswords on 2009-12-27
shadow copies annoying me cuz i have 50gb used, with 25gb unaccounted for...

---

### Post by Dullstar on 2009-12-28
WELL THEN.  That had better not take up all my partition!  I only planned on using it for a few modern games, so I kinda only had a 50 gigabyte partition made with boot camp (I have Linux on my old computer and eventually Linux will be on my brother's because he insists on trading them.  I for now don't feel like putting Linux on my iMac when I can devote a whole extra computer to it as Linux deserves it and Windows doesn't)

---

### Post by Psumi on 2009-12-28
> **pwnst*r said:**
> /fail

*facepalm*

Some people actually don't know.

---

### Post by Zoot7 on 2009-12-28
> **ubuntuman001 said:**
> So if I go to 'Computer' in the start menu, and right click -> properties on my C drive, it says I am using 29.4 GB (and this is after defragmenting several times)...

...but if I go into my C drive and select everything (including hidden stuff) and right click -> properties, it says the total size is only 15.4 GB.

Where are those extra 14 GB?
You might want to try running a disk cleanup, 7 seems to have a habit of hogging hard drive space with things like system restore at times. 
I found 7 to be taking up roughly 25GB of extra space a few days ago.

> **pwnst*r said:**
> /fail
Lol, gotta love your automatically antagonistic and negative response to anything even remotely anti-windows here. :rolleyes:

---

### Post by pwnst*r on 2009-12-28
> **Psumi said:**
> *facepalm*

Some people actually don't know.

the topic title is ridiculous, not necessarily the content within.  i'll stick with my previous post, thanks.

---

### Post by Abhinavhardikar on 2009-12-28
> **cprofitt said:**
> Windows 7 / Vista uses Volume Shadow copies, unless you turned them off, and those will take up space as well.

Thats true I removed the Volume Shadow copy and showed the correct usage data

---

### Post by user1397 on 2009-12-28
Yup, deleting the restore points took out like 12 GB, and the other 2 GB are for the paging file.  I totally didn't know about that till now.  Thanks for the suggestions everyone.

And yea the title was meant to be just sorta a joke, I'm not 'bashing windows' or anything*

* meant for a particularly sensitive individual on these forums.

---

### Post by pwnst*r on 2009-12-29
haha, yes, of course sparky.  don't blame me for the irony of a particular word you used in the topic title.

---

### Post by Khakilang on 2009-12-29
Could be temporarily internet file, compressed file, cookies, rubbish bin and who know what file might be hidden. Virus? They don't want you to know they exist in your computer.

---

### Post by CharmyBee on 2009-12-29
Well in that case you would use good ol' [CrapCleaner](http://ccleaner.com).

---

