---
title: "Gnash 0.8.3 the little player that could"
date: 2008-08-31
forum: The Cafe
---

### Post by drascus on 2008-08-31
I have found a bunch of ways of playing Flash format in ubuntu without having to resort to using Adobe. however I always thought it would be great to just get flash content in my browser. well Gnash 0.8.3 definitely delivers. I have been able to play just about every video sharing site that I could throw at the thing. What's more is I notice much more flash content is now supported that wasn't supported in previous versions yay! they are nearly on the verge of having a fully supported version that could mirror the technology of Adobe Flash player. While at the same time having an amazing community support and provide freedom like other Foss projects. Why is development taking so long and why hasn't this been done yet?  here is why: [http://www.youtube.com/watch?v=zoNvsiBTQDE](http://www.youtube.com/watch?v=zoNvsiBTQDE)   according to this developer if they had only a few more developers they could finish it within a year no problem! I personally am gong to donate some money to this project. if you can donate money or effort to support Gnash please do so. With the high volume of Flash content on the internet today this is a high priority Free software Project. you can find out how to install the latest version of the free player here: [http://ubuntuforums.org/showthread.php?t=837448&page=3](http://ubuntuforums.org/showthread.php?t=837448&page=3)

---

### Post by kevin11951 on 2008-08-31
when anything besides adobe supports [http://www.hulu.com/]("http://www.hulu.com/"), let me know

---

### Post by drascus on 2008-08-31
they are working on flash 9 to be implemented in the next version which is rumored to be out this month. Should work then.

---

### Post by Redache on 2008-08-31
I've always pronounced it "Nash" now I know the G isn't silent :) You learn something new every day.

---

### Post by swoll1980 on 2008-08-31
I say nash too, and I call gnu "new", so don't feel bad.

---

### Post by mrgnash on 2008-08-31
I like the name (except my 'G' IS silent :P ), but I've had consistently better results with swfdec, so that's what I use.

---

### Post by SomeGuyDude on 2008-08-31
> **kevin11951 said:**
> when anything besides adobe supports [http://www.hulu.com/]("http://www.hulu.com/"), let me know

Holy crap that's an amazing site.

---

### Post by drascus on 2008-09-01
I added a link to my signature where you can go and vote for ubuntu to further support Gnash...

---

### Post by voteforpedro36 on 2008-09-01
Why not use Adobe? Other than the fact that it's not open-source, which while I understand, what difference does that really make? "No freedom"? What kind of freedoms are you going to take with a flash video anyway? I get the freedom of using Linux, but going to levels of not using Adobe's flash because it's not open-source is absurd IMO.

---

### Post by qazwsx on 2008-09-01
> **voteforpedro36 said:**
> Why not use Adobe? Other than the fact that it's not open-source, which while I understand, what difference does that really make? "No freedom"? What kind of freedoms are you going to take with a flash video anyway? I get the freedom of using Linux, but going to levels of not using Adobe's flash because it's not open-source is absurd IMO.

Architechture independent. In 64 bit nspluginwrapper is huge resource hog. I am sure that someone wants to use PPC (PS3) as well or SPARC.

And everyone can try to fix its problems. There are many bugs in Adobe Linux port.

I remeber the day when Adobe broke Konqueror support (and KDE community had to fix support for closed source app!). It works now.

---

### Post by jomiolto on 2008-09-01
> **voteforpedro36 said:**
> Why not use Adobe? Other than the fact that it's not open-source, which while I understand, what difference does that really make? "No freedom"? What kind of freedoms are you going to take with a flash video anyway? I get the freedom of using Linux, but going to levels of not using Adobe's flash because it's not open-source is absurd IMO.

It's buggy (crashes very regularly for me) and it's slow as molasses on Linux (watching Flash videos in full screen is just a distant dream for me). Oh, and it not being open source also has some issues; it's not supported by anyone but Adobe (bad for security, portability, bug-fixing, etc.), it isn't packaged by default on most Linux distributions, and then there's the fact that you can't tinker with the source yourself, which is part of the fun :)

Sadly, Gnash and Swfdec haven't been much better experiences for me, so I just try to avoid Flash as much as I can.

---

### Post by rybu on 2008-09-01
How are you getting Gnash 0.8.3 to play Youtube videos?    

I haven't been able to get Gnash to handle Youtube -- if I use apt-get to install Gnash and the Mozilla plugin, the Youtube video screen is blank.  Moreover, Gnash tends to crash my system when I read BBC articles.  It loads the RAM with data at about 200Mb/s until it starts swapping, frequently freezing my system if I don't catch it early enough. 

I'm running a 64-bit version of Ubuntu. Could that be the problem, that Gnash isn't compatible with a 64-bit architecture?  Could it be something else?

---

### Post by drascus on 2008-09-08
rybu you need to install the latest version of Gnash 0.8.3 which hasn't yet made it into the main repos (I have complained about this ) it can be found here: [https://launchpad.net/~gnash/+archive](https://launchpad.net/~gnash/+archive)  youtube should work after you install that.

---

### Post by Scruffynerf on 2008-09-09
I just added that repo and tried it out on YouTube.

1992 called, they want their 8 bit blockiness back.

That's shockingly bad. Sound is about 5 seconds behind where it should be, the video is rendered in blocks about 8-12 pixels squared, and different parts of the screen update at different rates.

---

### Post by kevin11951 on 2008-09-09
> **Scruffynerf said:**
> I just added that repo and tried it out on YouTube.

1992 called, they want their 8 bit blockiness back.

That's shockingly bad. Sound is about 5 seconds behind where it should be, the video is rendered in blocks about 8-12 pixels squared, and different parts of the screen update at different rates.

could it be your graphics card/processor? because i know of other people with more luck (although the sound issue is pretty common)

---

### Post by Scruffynerf on 2008-09-09
A GeForce 6600GT, 256MB?

Possibly, however consider (for me)
Adobe Flash V9 crashed FF every time a new thing that addressed it appeared.
SwfDec showed a lot of promise, apart from the laggy sound.
Gnash (Official Hardy repo version) - skipped frames, and lagged in the sound.
Gnash (Their repo version) - looked like it was being processed by a Commodore 64.
Adobe Flash v10 (beta) - install from .deb,  crashed FF occasionally.
Adobe Flash v10 (beta) - install from their own tar.gz with installer - works very nicely indeed for me.

I know very well that a solution for one installation might not work well (or at all) for another user, but I thought that I would offer a dissenting opinion on the gushing praise that is in the OP.

---

### Post by sloggerkhan on 2008-09-09
does gnash let you save streaming videos that use flash?

---

### Post by drascus on 2008-09-11
Scruffynerf: umm I haven't experianced the problems you are having and have not heard of others complain of them when using Gnash. So although I can't be sure I suspect it is somethign with your computer. Sloggerkhan: It doesn't let you save flash videos but that might be a good feature to suggest to the Gnash developers. have you tried the unplug firefox plugin? that works well.

---

### Post by drascus on 2008-09-11
hey all watch this video by the lead Gnash developer : [http://www.youtube.com/watch?v=zoNvsiBTQDE]("http://www.youtube.com/watch?v=zoNvsiBTQDE") here he says if they had a few more developers they could finish and have a fully featured flash player within a year. there is a suggestion for this in ubuntu Brainstorm. here is a link : [http://brainstorm.ubuntu.com/idea/1128/]("http://brainstorm.ubuntu.com/idea/1128/") I am sure we can all agree that it would be cool to have a fully functional FOSS player for flash. so Vote it up!

---

### Post by billgoldberg on 2008-09-11
> **jomiolto said:**
> It's buggy (crashes very regularly for me) and it's slow as molasses on Linux (watching Flash videos in full screen is just a distant dream for me). Oh, and it not being open source also has some issues; it's not supported by anyone but Adobe (bad for security, portability, bug-fixing, etc.), it isn't packaged by default on most Linux distributions, and then there's the fact that you can't tinker with the source yourself, which is part of the fun :)

Sadly, Gnash and Swfdec haven't been much better experiences for me, so I just try to avoid Flash as much as I can.

You should five Flash Player 10 RC a try.

It's a lot faster and doesn't crash.

It has a few glitches on some sites, but everything is usable.

---

### Post by Polygon on 2008-09-11
> **voteforpedro36 said:**
> Why not use Adobe? Other than the fact that it's not open-source, which while I understand, what difference does that really make? "No freedom"? What kind of freedoms are you going to take with a flash video anyway? I get the freedom of using Linux, but going to levels of not using Adobe's flash because it's not open-source is absurd IMO.

not to mention flash plugin crashes are the reason for like 90% of firefox crashes, its a huge resource hog,doesnt support 64 bit, etc etc.

---

