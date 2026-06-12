---
title: "Java Going Open-Source"
date: 2008-04-23
forum: The Cafe
---

### Post by Joeb454 on 2008-04-23
I've just read it on Slashdot, wondering what you guys think?

[http://developers.slashdot.org/article.pl?sid=08/04/23/2037220&from=rss]("http://developers.slashdot.org/article.pl?sid=08/04/23/2037220&from=rss")

---

### Post by user1397 on 2008-04-23
Great news! :guitar:

---

### Post by the_darkside_986 on 2008-04-23
Does this include the GUI toolkit (whatever it's called)? 

Now, we just need a JVM language that supports operator overloading and unsigned vs. signed numbers. And all my other favorite features from C++, D, C#, etc. as well.

---

### Post by SunnyRabbiera on 2008-04-23
Yeh this has been in the works for some time now.
Its great that Sun has decided to open up java, maybe now with issues with it can have some peace.

---

### Post by Joeb454 on 2008-04-23
Now we just need Adobe to support flash on Linux more than they do already and we'll be set for life ;)

---

### Post by Tatty on 2008-04-23
> **Joeb454 said:**
> Now we just need Adobe to support flash on Linux more than they do already and we'll be set for life ;)

And for Nvidia and ATI to make their drivers open source... no doubt thatll happen any day now.  Lol. ;)

---

### Post by SunnyRabbiera on 2008-04-23
Well for flash, I feel that we could see progress for sure if silverlight becomes more popular, adobe might want to be more active on the linux front.
Hey even if flash never becomes open at least adobe can put more effort into making it work better for us.

As for ATI and nvidia, well there will be open drivers for ATI soon and I am sure Nvidia will follow.

---

### Post by GMU_DodgyHodgy on 2008-04-23
Well this is good news and a great move by Sun. 

Since I like to do develop in Java - it make me feel personally good. 

Regarding NVIDIA and ATI Drivers - I thought they were making them open source. Am I mistaken?

---

### Post by the_darkside_986 on 2008-04-23
Not really. I hear that ATI's "open source" drivers suffer from performance problems compared to the official proprietary drivers. And NVidia only releases free 2D drivers. But there is a 3rd party project called "nouveau" that looks promising. It is an open source 3D driver for Nvidia that isn't quite usable but I've read that it already is better than the official 2D driver.

Flash does need some serious competition, but not from MS standards and their DRM'd Windows Media formats. yuck.

If I could ever make any sense of the Mozilla NPAPI I would work on my own client side browser plugin that could access DOM and render vector graphics in a language based on [MiniD]("http://www.dsource.org/projects/minid"). But that is all pointless since I think Adobe and others are trying to move to a new web standard based platform based on Javascript or something. (Can't remember what it's called.) Adobe did donate their Actionscript VM source to Mozilla so I think Linux + the web will only improve. Silverlight and its DRM will certainly NOT improve the situation.

---

### Post by CarpKing on 2008-04-23
ATI decided last fall to start releasing specifications for their hardware while continuing to put out their closed-source driver.  They also put out the base for an additional open-source driver (this became radeonhd, iirc).  As a result of the open specifications, both the original and the new open-source drivers have been rapidly improving (it was always less buggy than the closed source driver, but slower).

---

### Post by toupeiro on 2008-04-23
+1 to Sun Microsystems.  I can remember a time when I loathed them, but over the last few years I have done a full 180 on my opinion of them.  Not just for their open source support, but also for their absolutely killer x64 servers with AMD and Intel chips.  They flat out outperform the HP and Dell server lines, use less power, run cooler, in some cases cost less!

---

### Post by jespdj on 2008-04-24
I'm surprised that this is news on Slashdot.

This is very old news - more than a year old very old news.

---

### Post by billgoldberg on 2008-04-24
Great news.

+1

---

### Post by zmjjmz on 2008-04-24
> **jespdj said:**
> I'm surprised that this is news on Slashdot.

This is very old news - more than a year old very old news.

They still had a few copyrighted parts (by third parties).  The news is that they're getting rid of them.

---

### Post by jespdj on 2008-04-24
> **zmjjmz said:**
> They still had a few copyrighted parts (by third parties).  The news is that they're getting rid of them.
Is that news? The [OpenJDK]("http://openjdk.java.net/") project has existed already for a long time. At [JavaPolis]("http://www.javapolis.com") in December 2007 I attended a talk by one of the Sun people who explained that JDK 6 had 4% code which had to be replaced be open-source alternatives, and that for some parts it was easier to replace them than others. So there isn't really anything new here.

The only thing that's new about it is that Sun seems to have stated their intentions to open-source Java again, and that they want Linux distros to include it by default. That would ofcourse be very good.

OpenJDK is already available on Ubuntu, but not yet in the core repository.

---

### Post by bruce89 on 2008-04-24
> **jespdj said:**
> OpenJDK is already available on Ubuntu, but not yet in the core repository.

Surely it is:

```

bruce@Scooby-Doo:~$ apt-cache policy openjdk-6-jre
openjdk-6-jre:
  Installed: 6b09-0ubuntu2
  Candidate: 6b09-0ubuntu2
  Version table:
 *** 6b09-0ubuntu2 0
        500 http://gb.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
```

Or do you mean not the *main* one?

---

