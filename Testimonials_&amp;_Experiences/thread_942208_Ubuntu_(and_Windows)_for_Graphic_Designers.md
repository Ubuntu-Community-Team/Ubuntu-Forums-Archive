---
title: "Ubuntu (and Windows) for Graphic Designers?"
date: 2008-10-08
forum: Testimonials &amp; Experiences
---

### Post by gwessendorf on 2008-10-08
Hi-
A while back I played with previous releases of Ubuntu and really liked it. So much that eventually, I would like to make a complete move. But there are a few windows programs I still need for graphic design jobs (fonts, font manager, quarkxpress, etc). They are actually the only reason I still have windows around. 

I was wondering if there were any other ubuntu users who have dealt with commercial fonts and graphic design tools before as well, what their experiences were, and how they solved it and made it all work on a Ubuntu platform.

I tried a dual-boot configuration before. It worked okay but it was a pain to exchange files between windows and ubuntu, especially when you have everything else including office, web & email set up on ubuntu. On Windows I had to use a special driver to access ext3 partitions, and I wasn't able to access my ubuntu apps while I was working in windows and vice versa.

I tried windows in a virtual machine before. It worked great, even with windows from a dual boot configuration (with two hardware profiles). I could use ubuntu and windows apps whenever I needed them, without having to boot from one system to another. But file exchange and different file systems were still a bit of a pain, and in addition, graphic software in a virtual machine just wasn't as quick and responsive as it was when you ran them in windows on the physical machine. Plus, USB 2.0 devices (e.g.. Scanner) didn't work right in the virtual machine. (I used VMware Server)

I played with wine, too... but it wasn't nearly as stable as the virtual machine.

Are there any other options that might work without having to buy a mac and new software? 
Any hints, links, recommendations, ideas would be very appreciated.

Thanks in advance! :)
Gerrit

---

### Post by factotum218 on 2008-10-28
In all honesty, if your a professional and dropped all that money on PC software like Quark, stick with Windows.

On the other hand, if your just a pirate and won't really do anything significant with the software in the future then stick with the virtual machine on Ubuntu.

---

### Post by arglborps on 2008-10-29
If you're serious about graphic design and you also want to do print then there's little other choice than the Mac for now. I have seen people do print on Windows, but even there it's just too much of a hassle, because it's usually a slapped on solution and the colour calibration is not a integral part of the whole display engine, so there's a huge margin of error on Windows. Also font management is quite a pain there.

The font rendering on Windows is also a problem, because it doesn't resemble the appearance of the letters in printed format well, on Ubuntu you can at least tweak those settings, to make the fonts look more like the designer intended them to look like.

Then the big issue with doing print stuff in a virtual machine is that you have no control over the colour whatsoever, even calibrating your Linux machine won't help you much for the virtual machine, which just doesn't know what colour spaces the physical monitor (in contrast to the virtual monitor it thinks is using) has.

If you do print and you know your printer can use PDF-X data, you might be able to set up a Ubuntu box for that purpose, but there is no real workflow in most apps for that. So you'd have to setup the workflow yourself, maybe use ghostscript to create your PDF-X compliant files, and then there are no Open Source applications (AFAIK) to do pre-flighting and such on Linux.

There are some commercial solutions for print design also for Linux, but they are quite costly, so you might then as well just get a Mac and be done with it. Print is such a complex thing and the margins nowadays are so small doing that kind of work, nobody bothers to make inroads on Linux, because offering a solution on a new (any new) platform would just cost too much and the prospects of making money with it would be too tiny.

HOWEVER
If you're only into on-screen design (Web, Games, 3D), you might have much better chances to stay Linux only, though. There's a wealth of software for post-production, be it open source or commercial (Blender, Maya, Houdini) or [check this list]("http://www.linuxmovies.org/software.html").

Tons of image editors, 2D animation programmes are becoming more and better, too.

---

### Post by icodeme on 2008-10-29
Yeah. The main problem of those professionals who want ubuntu is the lack of softwares that they need to get their job going. I am a web developer. BUT I SWITCHED TO UBUNTU (FULL). I left windows and started to crawl over these forums and community websites and I think I made the right move.

For my Adobe programs like photoshop, dreamweaver, I got WINE / Crossover to handle those ( That program runs windows applications ) :)

Everything's doing fine except some incompatibilities which i think, will be fixed in new Intrepid :)

Try it first in dual boot and eventually, learn the basics and I'm sure you'll leave windows in no time.:guitar:

---

### Post by Geekkit on 2008-10-29
Two versions of my answer: short version, long version

**Short version:** buy an Apple Mac, buy required Mac software.

**Long version:**
Linux is open source (with a massive influence for and about free software - free meaning, shouldn't have to pay for ANY software ... not all users agree with this but anyways). Therefore, support for anything (in Linux) that requires closed source is usually shunned and most companies don't bother to consider a ROI for writing software for Linux - they stick with Mac and Windows.

**Scribus** (DTP e.g., Like Quark Xpress, Pagemaker ... if you remember it)
Scribus is actually quite a useful (KDE) tool which allows you to create layouts that are quite complex. I've used it to create business cards, letterhead, and posters. It's not perfect, has bugs, but if you can work around them, you can create some nice artwork. It supports outputting files for color separation.
Downside(s) of Scribus: no Pantone support although if you REALLY know what you're doing you can create your own custom colors that represent your PMS spot colors.

**GIMP** (Image Manipulation)
An image manipulation program although with image pipes you can use it as a paint program (minus the wet brush, mixing of colors, simulating particular types of mediums such as canvas, etc.). GIMP, like Scribus lacks support for Pantone colors. GIMP also lacks procedural layer support, and native 16 bit per channel support although that's (the 16 bits per channel) in the works since they've adopted GEGL as their underlying rendering framework (it will most likely take several months to convert the entire code-base over to GEGL ... Note: the CinePaint people are quite quick to point out that they've supported 16 bits per channel for some time now).

**FontForge** (Creating Fonts)
FontForge: I have not used this program (I haven't made fonts in years) and so I cannot vouch for this software although it appears to support ... font creation.

**Inkscape** (Vector Drawing)
Inkscape is the OSS version of Illustrator/Freehand. It works quite well although it does have a few bugs (prepare to get familiar with SVG in case a layer gets "inivisiblized" and you have "un-invisiblzie" the layer).

Inkscape is another app that does not know anything about Pantone. It does however have some very interesting features including superior bitmap vectorizing tools (very cool), as well as the ability to perform boolean operations. I've used Inkscape to create logos, diagrams, and artwork for the web.


**Summary**
If you have no particular Pantone demands, you're open to spending several hours scouring web sites for clues to unlock features, and you feel brave, you may be able to do it all with OSS. However, if these things I've just mentioned scare you, like I said above, just get a Mac and the accompanying software and save yourself the grief.

The Windows versions of Mac products have always seemed to me to be the sloppy seconds. The Mac versions (e.g., Photoshop, Premiere, Flash) have crashed less for me than the Windows counterparts. I might be one of the very few unlucky in that scenario ... but then again, maybe not.

Just my subjective opinion and that's all.

---

### Post by icodeme on 2008-10-29
i already made my way through things. But what you posted here is definitely an extra knowledge. Somehow, GIMP can do basic image manipulations. Photoshop is quite easy and gives more professional outcome. But Im using GIMP too :):lolflag:

---

### Post by Geekkit on 2008-10-29
> **arglborps said:**
> If you're serious about graphic design and you also want to do print then there's little other choice than the Mac for now. I have seen people do print on Windows, but even there it's just too much of a hassle, because it's usually a slapped on solution and the colour calibration is not a integral part of the whole display engine, so there's a huge margin of error on Windows.

I think this is the most succinct way of putting it.


> **arglborps said:**
> Tons of image editors, 2D animation programmes are becoming more and better, too.

I wouldn't say there's a ton of image editors. There's GIMP. For paint programs there's myPaint, Krita, Gogh, DrawPile, and that's it. GIMP and myPaint are about the best choices for image manipulation and painting respsectively.

2D animation programs are even harder to find. There's Synfig, KToon (which hasn't been updated for over a year now and the project seems to be dead), Pencil, and Plastic Animation Paper (PAP) ... horrible name BTW, and they all have horrible interfaces, missing basic drawing/animation features (NONE of them except Synfig support motion graphs/ease-in/ease-out), or all of the above. Flash 4 Linux (F4L) died a long time ago (or never really even got off the ground).

Video support is even worse although a new project called Lumeria appears to be addressing this void. They look like they've "got it" since they're trying to address this hodge-podge UI design that all the NLE apps in Linux seem to suffer from.

---

### Post by Geekkit on 2008-10-29
> **icodeme said:**
> Somehow, GIMP can do basic image manipulations.

GIMP can also help you to create art. I did this in about 10 minutes after spending about a half an hour creating/tweaking Image pipes (AKA image hoses). I'm not saying I'm Bob Ross or anything but it (GIMP) definitely has more power than people give it credit for.

:)

---

### Post by sloggerkhan on 2008-10-29
Inkscape is supposed to eventually get animation features. Probably a long way off, still. I just wanted to note that there are a few font manager programs to classify and group fonts as well as to preview them. I think an example is fonty pthyon, but there are at least 1 or 2 more simlar programs.

So far as open source goes, inkscape, scribus, and gimp are what really take care of you w/ regard to design. They're all great programs, but they don't really compare to Adobe CS when taken as a group. That said, on an individual level they're all competitive, and I really believe that you can do just as much with them. It's just not as easy, particularly because outside of inkscape they've got more of a learning curve.

---

### Post by CBrendan on 2008-10-29
Hi Everyone

I also do alot of graphic design with commercial products like Photoshop, Illustrator, InDesign and CorelDraw and I found the best way to keep these programs within quick access in Ubuntu is to use Virtual Box.  It's much faster than VMWare in my opinion and as long as you have enough RAM to share with your virtual machine you can still have the best of both worlds.

Another thing, Virtual Box installs and works like a charm on my Kubuntu 8.04.  I installed the extra software for my virtual Windows machine to see my Linux shares and it works with no issues.

Maybe give it a try.

---

### Post by icodeme on 2008-10-29
> **Geekkit said:**
> GIMP can also help you to create art. I did this in about 10 minutes after spending about a half an hour creating/tweaking Image pipes (AKA image hoses). I'm not saying I'm Bob Ross or anything but it (GIMP) definitely has more power than people give it credit for.

:)


I'll give you a credit for that result. Definitely good. But still, it isn't that good when it's done in photoshop.

and yet you're right, I've been underestimating GIMP. Sorry bout that :)
I somehow found a thread about GIMP that looks like photoshop.. Im not sure of the thread though I left a comment there. It think it reads like GIMP 1.4.3 not so sure guys 
ROCK ON!:guitar:

---

### Post by MNICY on 2008-10-29
I will take GIMP over photoshop any day :P

In highschool, we had photoshop and gimp installed. Whenever i wanted to edit an image (or draw), i would use GIMP. Everyone else was using photoshop, and i was producing work as good or better as them..

Of course, I am not a graphics designer, and my needs are basic. 

Although --- remember you can get photoshop to run in wine :)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)

---

### Post by alwez_loner_TZ on 2008-10-29
It the main thing i still have a dual boot on my PC, other wise i would have switched to linux a while back. And the Virtual box, Crossover are not stable on the Adobe programs.

---

### Post by mesobeautiful on 2008-10-29
Combined with proper dietary habits it will help keep weight at desired levels.[Long Island mesotherapy]("http://www.mesobeautiful.com/")

---

