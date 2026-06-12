---
title: "Friday 13th! Ubuntu installed :)"
date: 2009-11-13
forum: The Cafe
---

### Post by headbuster on 2009-11-13
Hello friends :)
Today my CD finally came! Until now I had been trying to install ubuntu but every time it failed. It said my CD was dirty...
But today it all worked well when I tried to install it with the original CD.

So now what do you suggest me to do? Any interesting games or apps?
I have only installed skype for now. What should I do next?
:)

---

### Post by blueshiftoverwatch on 2009-11-13
Didn't realize it was Friday the 13th until this morning. Good thing I re-partitioned my hard drive yesterday evening. Maybe I should wait until 12:01 tonight to setup my virtual machines.

---

### Post by Swagman on 2009-11-13
Yeah, It's Black Friday.

And I'm about to install 9:10

Dat... Dut....... Daaaaaaaaaaaaaaaaar !!

---

### Post by UKBB on 2009-11-13
> **Swagman said:**
>  Dat... Dut....... Daaaaaaaaaaaaaaaaar !!

Is that "Dunt dunt duuuuuunnnnnnnnn!!" while speaking like a pirate?

---

### Post by headbuster on 2009-11-13
> **UKBB said:**
> Is that "Dunt dunt duuuuuunnnnnnnnn!!" while speaking like a pirate?

Hahaha arghhh me mate :D

---

### Post by Swagman on 2009-11-14
My experience of finally clean installing Karmic Koala on **MY** machine.


Some background...

I've already successfully upgraded a laptop from 9:04 to 9:10rc and clean installed the daughters mother in laws machine to 9:10 and my daughters with no issues.

My machine however... All those gripes you read people posting about... I think I got the lot !!

The machine...  
[b][i]
MSI K8 platinum
AMD athlon64 XP3500 (single core)
2gb RAM (four sticks)
XFX AlphaDog GTX8800 (nVidia)
2x 200gb Maxtor Sata drives (Capture & Render)
1x 80 gb Windows XP (Sata)
1x 200gb Ubuntu drive (9:04) now unpowered for clean install on...
1x250gb Sata
Sony DVDRW (IDE) on the slave part of the unpowered ubuntu drive cable

[/i][/b]

boot up live cd and remove all the partitions from target drive. This was my daughters drive until I upgraded her to 1 Tb drive.

Start installer......

Can only see Capture & Render (NTFS) drives and as I had bunged all the stuff I wanted to keep on those drives using them for O/s was out of the question.

A googling we will go.....

Find there's a bug with installer dealing with multiple sata drives.

disable dmraid apparently cures it

```
 sudo apt-get remove dmraid
```

Yay... success... But have to manual partitioning... No probs, I was gonna make separate /Home Partition anyway.

Finish install and reboot

**Grub error 22**

Bah... More googling

decide to re-install (getting late and I'm fed up with googling)

doesn't see boot drive again although it's listed in Places/Computer

enter dmraid code again.. re-install.. Just don't format

At apply section click advanced tab and see Grub is set to be written to Hd0: (is this an Amiga ?)
Ubuntu drive is listed so choose that instead.


reboot

Success.

Now I'm bloody glad I wasn't round somebodies house trying to do this in front of them on their machine. Although I suppose it's good I've learned the work around.

---

