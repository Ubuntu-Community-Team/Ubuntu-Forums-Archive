---
title: "No More GParted Live CD"
date: 2008-01-24
forum: The Cafe
---

### Post by Sef on 2008-01-24
From the [GParted-LiveCD Website]("http://gparted-livecd.tuxfamily.org/news.php"):

> 21 january 2008 : End of Gparted-livecd !

On last July 30th, I wrote I was looking for a new livecd maintainer.
So far nodoby contacted me for this purpose.
During this time I continued maintaining the livecd,
releasing about once a month.
I am alone to maintain this livecd project since about 10 months,
and some other projects exist with about the same goals.
I think the best one is sysresccd, from François Dupoux.

If someone is interested by hacking gparted (not the livecd, but the soft),
which supposes a good knownledge on C++, let me know ! I can enable svn repository
and push files into it, and give access to them with read/write rights.


Good by !

Larry 

I wonder if Ubuntu will pick GParted up, or what it will use as its partitioner, or will GParted work continue, but just not as a Live CD.

---

### Post by Rhubarb on 2008-01-24
Oh that's a pity, I quite liked to have the gparted live cd on hand when fixing up client's PCs.

It seems I'll have to look for an alternative, perhaps sysresccd.

---

### Post by Bungo Pony on 2008-01-24
Oh man, that sucks! I use Gparted all the time!

I couldn't get the partitioner on sysrescd to work for me (wasn't that also Gparted?). I'll be making backups of my Gparted live CD. I hope someone else picks up the project.

---

### Post by quinnten83 on 2008-01-24
mayve if this gets digged a few times, we can get a new mantainer.

---

### Post by Nano Geek on 2008-01-24
That's really a shame. 
The GParted CD was a handy tool to have around.

Does this mean the GParted is also dead, or just the CD?

---

### Post by bobbocanfly on 2008-01-24
Gparted CD was really useful. Especially since the version bundled with the Gutsy CD was affected by a bug that made it fail everytime devices were reloaded. I really hope Gparted keeps being developed despite this.

---

### Post by y-lee on 2008-01-24
You can always use  [QtParted]("http://qtparted.sourceforge.net/"). It doesn't have a live CD but is included in Knoppix and some other live cd tools :)

---

### Post by Lostincyberspace on 2008-01-24
Partedmagic not partionmagic is a good one for a live distro and it is still being developed.

---

### Post by UltraMathMan on 2008-01-24
Sysresccd includes gparted. 

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by Paul820 on 2008-01-24
> I wonder if Ubuntu will pick GParted up, or what it will use as its partitioner, or will GParted work continue, but just not as a Live CD.

I hope they do as that is one handy piece of software.

---

### Post by FuturePilot on 2008-01-24
Oh man, that's terrible. The GParted live CD is an indispensable tool to me. It's come in handy a lot of times. I hope someone else might pick it up. It's too good of a tool to let die. 
I do hope at least GParted keeps being developed. There's no other partition editor that comes close to GParted.

---

### Post by zvacet on 2008-03-06
> I hope someone else might pick it up

[Here](http://gparted.sourceforge.net/news.php)

---

### Post by LaRoza on 2008-03-06
Good. I was worried...

---

### Post by Oldster on 2008-03-06
As posted earlier, PartedMagic is a good alternative.

[Link to PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php")

---

### Post by FuturePilot on 2008-03-06
> **zvacet said:**
> [Here](http://gparted.sourceforge.net/news.php)

Phew, that's great news! :)

---

### Post by uberlube on 2008-03-06
ya who needs gparted when we have partedmagic

---

### Post by LaRoza on 2008-03-06
> **uberlube said:**
> ya who needs gparted when we have partedmagic

Who needs <software> when we have <othersoftware>

I have used GParted for many tasks and it is (was?) a great tool. There are others, but why should I use them when I have GParted?

---

### Post by ~LoKe on 2008-03-06
Please forgive me, but why does it need to be maintained?  Doesn't your copy of GParted work most excellently already?  Perhaps I'm not as well versed in the subject as I thought, but wouldn't the only issue be new file systems?

---

### Post by init1 on 2008-03-06
I'm glad to hear this is a false alarm :D
Visopsys has a nice partition manager. It doesn't have as many features as Gparted, but it's graphical and fits on a floppy or CD. XFDISK is also useful at times. 
[http://visopsys.org/index.html](http://visopsys.org/index.html)

---

### Post by init1 on 2008-03-06
> **~LoKe said:**
> Please forgive me, but why does it need to be maintained?  Doesn't your copy of GParted work most excellently already?  Perhaps I'm not as well versed in the subject as I thought, but wouldn't the only issue be new file systems?
I was thinking the same thing, actually. I made the same argument for XMMS today, that even though it's old, it's still a great program. There's little need for a change since it's already nearly flawless.

---

### Post by LaRoza on 2008-03-06
> **~LoKe said:**
> Please forgive me, but why does it need to be maintained?  Doesn't your copy of GParted work most excellently already?  Perhaps I'm not as well versed in the subject as I thought, but wouldn't the only issue be new file systems?

There are bugs (read the link, one was fixed :))

The issues are also network support, stability, hardware support, and maintaining all the tools on it. (Testdisk and such).

Support for new files systems (Vista's NTFS) is important as well, but not the only thing.

---

### Post by regomodo on 2008-03-06
to be fair, the gparted cd is fairly bombproof. I've used it in many computer at work and home and so far the only issue is xserver ones.

It's not perfect but bloody close

---

### Post by uberlube on 2008-03-07
> **LaRoza said:**
> Who needs <software> when we have <othersoftware>

I have used GParted for many tasks and it is (was?) a great tool. There are others, but why should I use them when I have GParted?

I was only speaking out of personal preference of course

---

### Post by forrestcupp on 2008-03-07
> **LaRoza said:**
> There are bugs (read the link, one was fixed :))

The issues are also network support, stability, hardware support, and maintaining all the tools on it. (Testdisk and such).

Support for new files systems (Vista's NTFS) is important as well, but not the only thing.

Yeah, I agree.  The new file systems is the main reason in my opinion.  We can't be short sighted.  Sometime in the future, we will have newer and better file systems, not just in Windows, but in Linux, too.  At one time, people couldn't see past ext2, and now nobody really uses it.  If GParted Live CD isn't maintained, then a great utility will become obsolete and unusable.

---

### Post by bruce89 on 2008-03-07
Gparted is just a frontend to GNU parted, so new filesytems would be supported anyway, but not in the GUI.

---

### Post by LaRoza on 2008-03-07
> **bruce89 said:**
> Gparted is just a frontend to GNU parted, so new filesytems would be supported anyway, but not in the GUI.

It is a live disk as well, so you can't run updates on it.

The Live CD must be kept up to date and tested, which is probably time consuming.

---

### Post by forrestcupp on 2008-03-07
> **bruce89 said:**
> Gparted is just a frontend to GNU parted, so new filesytems would be supported anyway, but not in the GUI.

At least that means it would be easier than I thought to maintain it.

---

### Post by ice60 on 2008-03-07
i'm certain PartedMagic went through the same thing about 5 months a go, he said he wasn't going to carry on because no one was helping, he must have found someone though.

i read recently about a fork of gparted, i think it was gparted anyway. does anyone know what it's called? it has added features.

---

### Post by Sef on 2008-03-07
> i read recently about a fork of gparted, i think it was gparted anyway. does anyone know what it's called? it has added features.

Is it [Parted Magic 2.0]("http://www.linuxpromagazine.com/online/news/parted_magic_2_0_with_new_visparted_tool") that you were thinking of?  From the article: > The program is a fork of the graphical Gparted 0.3.3 tool.

[Parted Magic Home Page]("http://partedmagic.com/wiki/PartedMagic.php?action=browse")

---

### Post by sloggerkhan on 2008-03-07
PartedMagic doesn't boot properly on my computer, though gparted has always worked fine.

---

### Post by ice60 on 2008-03-08
> **Sef said:**
> Is it [Parted Magic 2.0]("http://www.linuxpromagazine.com/online/news/parted_magic_2_0_with_new_visparted_tool") that you were thinking of?  From the article: 

[Parted Magic Home Page]("http://partedmagic.com/wiki/PartedMagic.php?action=browse")
actually, i think that could be it! i didn't think it was anything to do with Parted Magic, but when i think about it i thought the name was something very close to visparted. so, i must have slightly misread it and thought it was just called Visparted. maybe i just skimmed through it and didn't really read it at all! :lolflag: anyway, you are right, that's what i was thinking of lol

---

### Post by ice60 on 2008-03-08
hold on, it is called Vis Parted isn't it, and it's a fork. i think i've gone crazy lol

---

### Post by Sef on 2008-03-09
>  hold on, it is called Vis Parted isn't it, and it's a fork. i think i've gone crazy lol


Visparted is the front end for Parted Magic.  Below is from [Linux  Pro Magazine]("http://www.linuxpromagazine.com/online/news/parted_magic_2_0_with_new_visparted_tool?category=13395"):

> The Parted Magic Linux Live System gives users the ability to manipulate hard disk partitions in various formats. Version 2.0 is the first to rely on the Visparted GUI tool .

Yes, it's a fork of GParted.

If you have gone crazy, I have a strait jacket you can borrow.  :lolflag:

---

