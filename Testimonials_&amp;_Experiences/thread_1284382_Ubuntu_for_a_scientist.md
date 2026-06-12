---
title: "Ubuntu for a scientist"
date: 2009-10-06
forum: Testimonials &amp; Experiences
---

### Post by Warthaug on 2009-10-06
So after a few years of this I thought I'd share my thoughts on Ubuntu; from the point of view of someone who does biology for a living.

I've known of, and used on occasion, linux for a number of years.  Many scientific instruments run off of one linux distro or another (usually redhat).  While I was comfortable using linux for those purposes, I never really considered it for day-to-day use.

Fast forward to fall 2007.

In 2007 I moved onto a new position, one which involved intensive use of matlab.  Matlab (a mathematical processing program) is quite computationally intense, and we are running matlab scripts that take days - literally - to complete.  While matlab is available for windows, as I'm sure many can appreciate, getting anything to run in windows for several days without crashing isn't exactly easy.  Switching to ubuntu solved that problem, but left me looking at a linux screen most of the time.

This forced me to regularity use ubuntu, and I soon found that even when I wasn't using matlab that I wanted to use ubuntu as much as possible.  After about 1 year I was a true convert, and use ubuntu for all but about 5% of my computing needs.  Its fast, stable, intuitive, and has a great selection of science-y programs available.  One hardware issue aside (my laptops intel video card has occasional openGL issues), ubuntu has been flawless.  I've also played with the various "flavors" - xubutu, kubutu, etc, but still prefer the gnome desktop (although ubuntus brown theme could afford to go).

All of the goodness aside, there are a few outstanding problems that necessitate keeping windows.  Notably, there is a real lack of video editing and presentation software - openoffice's "impress" just isn't upto powerpoints level, there is no good illustrator equivalent, and no linux video editor can touch premiere in terms of capabilities.  The same holds true for some of the science software I use - there are no good linux equivalents for packages like prism, and some supposed linux packages (scaffold) only work in red hat, forcing me to stick with the windows versions.

Not that any of the above are ubuntu's fault, but it is a limiting factor.  That said, we're setting up virtualization on all our dual-boot systems, so at least we'll soon be able to avoid dual-booting and have better data flow from windows to linux...

Bryan

---

### Post by Ms_Angel_D on 2009-10-06
Yes there are a few areas in which linux is still limited due to lack of software being designed for it. I personally am not too familiar with presentation like software, but if by prism your referring to the application which mozilla makes, it's available in the repository. Hopefully with time more software will be designed for linux in the future.

---

### Post by Sef on 2009-10-06
Then there is the [Education and Science]("http://ubuntuforums.org/forumdisplay.php?f=169") subforum.

---

### Post by slakkie on 2009-10-06
Maybe you can get those red hat specific apps to work with alien:

alien - convert and install rpm and other packages

---

### Post by Warthaug on 2009-10-07
> **Ms_Angel_D said:**
> if by prism your referring to the application which mozilla makes, 

Unfortunately, no.  Prism is made by graphpad, and is avialble in mac and PC format only :(  It doesn't run under wine, and while parts of it can be replaced with linux software (R in particular), there is no real equivalent on any platform which replaces it outright.

Bryan

---

### Post by Warthaug on 2009-10-07
> **slakkie said:**
> Maybe you can get those red hat specific apps to work with alien:

alien - convert and install rpm and other packages

I tried that.  Unfortunately, its not an RPM, but rather a .sh.  The problem appears to be that the install program assumes certain components (Java among others) will be located in specific directories, and unfortunately, there is no way (as far as I can tell) to find out where it is looking for those components, nor to change the paths it looks at.

Bryan

---

### Post by Ms_Angel_D on 2009-10-07
Warthaug, I truly wish I could be of more assistance. Have you considered writing the developer and asking about a ubuntu friendly version?

In in end I understand it can be frustrating to have to use windows when you really don't want to. Hopefully in the future that will change.

---

### Post by hashimoto on 2009-10-07
> **Warthaug said:**
> ...there are no good linux equivalents for packages like prism...

Wine?
[http://ubuntuforums.org/showpost.php?p=5650554&postcount=10](http://ubuntuforums.org/showpost.php?p=5650554&postcount=10)

---

### Post by Tibuda on 2009-10-07
> **Warthaug said:**
> Unfortunately, no.  Prism is made by graphpad, and is avialble in mac and **PC** format only :(  It doesn't run under wine, and while parts of it can be replaced with linux software (R in particular), there is no real equivalent on any platform which replaces it outright.

Bryan
What do you mean by PC?

---

### Post by bubblehead74 on 2009-10-07
> **Warthaug said:**
> there is no good illustrator equivalent

Biologist here. I really like Scribus for preparing figures for publications.

---

### Post by Warthaug on 2009-10-08
> **danielrmt said:**
> What do you mean by PC?

Windoze, my bad...

---

### Post by Warthaug on 2009-10-08
> **hashimoto said:**
> Wine?
[http://ubuntuforums.org/showpost.php?p=5650554&postcount=10](http://ubuntuforums.org/showpost.php?p=5650554&postcount=10)

Lucky gal - both wineHQ and my own experience say that prism doesn't work with wine.  I wonder what she was using it for - parts of it do work, but many of the statistical functions cause a crash.

Bryan

---

### Post by solwic on 2009-10-08
> **Warthaug said:**
> Windoze, my bad...

Good save.  I saw the lynch mob forming up and lighting their torches.  :P

---

### Post by Dullstar on 2009-10-11
What do you guys mean that Impress isn't at the level of powerpoint?  I really thought impress was easier to use when I tried it, and I could only find one feature lacking - one feature that I really don't see the point of.  And I think I may have figured out how to do it, but I forget how.  In case anyone is interested, the feature was making a show loop infinitely until escape is pressed.

---

### Post by Warthaug on 2009-10-11
> **Dullstar said:**
> What do you guys mean that Impress isn't at the level of powerpoint?  I really thought impress was easier to use when I tried it, and I could only find one feature lacking - one feature that I really don't see the point of.  And I think I may have figured out how to do it, but I forget how.  In case anyone is interested, the feature was making a show loop infinitely until escape is pressed.

There are two areas which, for me, are central to presentations which impress does very poorly.  One is control of media (particularity video).  I've had extensive problems getting simple things (in power point) to work in impress - setting a video to loop until I click on it for example.

The second place it is quite weak is in making custom animations.  I've always found this feature in powerpoint to be very useful for presenting complex diagrams piece-by-piece.  While impress does have this capability, it is a faint shadow of what you can do with powerpoint.

Bryan

---

### Post by Ms_Angel_D on 2009-10-12
The op has stated his reasons, I suggest we let this thread dwindle....

---

