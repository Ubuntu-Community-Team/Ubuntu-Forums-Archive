---
title: "Should Adobe open source Flash?"
date: 2010-06-25
forum: The Cafe
---

### Post by lotharjade on 2010-06-25
Should Adobe make Flash and open source project, backed by their paid Flash developers?  

The development of Flash seems to drag along slowly compared to other software, even Adobe's own software suite (Photoshop, Dreamweaver, etc..).  Some have speculated that not only does Adobe not put much investment in developing Flash, that it doesn't care a whole lot about how it is doing.

What effect would Flash as an open source project have both on Flash and its impression to users?  Would it get developed and updated quicker?  Do you think Adobe has a good vested interest in keeping Flash proprietary?

I guess seeing as I am a 64-bit user currently entering Flash Hell, I have to ask my self..  Is there a better way??

---

### Post by samalex on 2010-06-25
[Gnash]("http://www.gnu.org/software/gnash/") is an attempt to create an open source Flash player, but I hear it's not quite there.  I'm really looking at it though since it has a MUCH slimmer memory footprint than Adobe Flash plus they have a 64-bit version for Linux.

FLOSS Weekly [interviewed the guys behind Gnash]("http://twit.tv/floss94") last year, and it looks like Adobe did release some specifications which helped them make it more compatible.  I don't think it's 100% there, but it might be a good alternative to Adobe Flash for 64-bit users.

I'm planning on installing 64-bit 10.04 in the upcoming week (still running 64-bit 9.04), so I'll try to install it then. 

But to answer your question specifically, yes I think Adobe needs to either open source Flash all together or at least release all the standards so Gnash and others can create 100% compatible players.

Sam

---

### Post by Sporkman on 2010-06-25
Adobe sells expensive flash development tools, maybe that factors into why they haven't open-sourced it.

---

### Post by lukeiamyourfather on 2010-06-25
It matters little what happens to Flash as far as I care because there are alternatives and improvements everyday. HTML5 is nowhere close to finalized but already in a draft state it offers much of the same functionality of Flash (canvas element, video and audio elements). Having said that I think it would be good if Flash were suddenly open source, but its not necessary and I don't think that'll ever happen. Cheers!

---

### Post by samalex on 2010-06-25
> **Sporkman said:**
> Adobe sells expensive flash development tools, maybe that factors into why they haven't open-sourced it.

If they at least opened the standards for players, they could still develop their tools but others could focus on players.  Granted others may use the standards to create another authoring tool, but I doubt any will rival what Adobe has thus far... though this could open the door to open source Flash authoring tools since Adobe doesn't make them for Linux anyway.

Sam

---

### Post by Frogs Hair on 2010-06-25
Adobe has on going security issues with flash , so making the code open source may not be the best idea. I read one article stating that Adobe wants to move to a silent automatic updates to avoid posting all the security issues every time a new version of flash is released . This is only talk at the moment and I don't know what the implications would be for Ubuntu users that update via the repository.

---

### Post by samalex on 2010-06-25
> **Frogs Hair said:**
> Adobe has on going security issues with flash , so making the code open source may not be the best idea. I read one article stating that **Adobe wants to move to a silent automatic updates** to avoid posting all the security issues every time a new version of flash is released . This is only talk at the moment and I don't know what the implications would be for Ubuntu users that update via the repository.

Yeah this wouldn't go down very well.  I loath apps that call home behind my back, so this would turn many more people off to Adobe.

Sam

---

### Post by McRat on 2010-06-25
I think when you have a program that does things without the user's permission it's called a Trojan or something? :confused:

---

### Post by Frogs Hair on 2010-06-25
> **McRat said:**
> I think when you have a program that does things without the user's permission it's called a Trojan or something? :confused:

There would be an automatic update notification at least for Windows.

---

### Post by mickie.kext on 2010-06-25
I hope Adobe keep Crash propriatary and even put a price tag on player. That would make it die faster. It is broken beyond repair and opensourcing it would just turn it into zombie... or new COBOL, or something.

---

### Post by MCVenom on 2010-06-25
I like Flash because it's always worked well for me, even on Linux; and I like Flash games. :P

It would be a good idea, I should think. :)

---

### Post by tgalati4 on 2010-06-25
No.   It can die quietly.  No reason to prolong the agonal period.

gurgle . . . gurgle

---

### Post by lotharjade on 2010-06-26
How about making it die loudly? (as opposed to quietly)  

I am surprised that Apple and Google don't provide some "free" developers for the Gnash project, if it would help Adobe Flash die quicker.  True, Apple thinks that QuickTime competes with it (and worry that Gnash might take customers away from them), but I am not sure how much.

While Microsoft has Silverlight as a competitor, I rather don't think people want to replace one proprietary program linked to a major corporation with another proprietary program linked to a major corporation.  They might take a bit of market share, but I suspect people are all hoping for an open system, even if that system is an alternative to Flash (as opposed to open Flash).

---

### Post by NightwishFan on 2010-06-26
I just tried swfdec in lucid 64-bit. It works with Youtube. Gnash looked more promising to me but it does not play the videos.

---

### Post by murderslastcrow on 2010-06-26
Thanks NightwishFan- I've only ever tried Gnash and it had issues with YouTube, so I gave up on it. It would be awesome if one of those projects comes to full compatibility in the coming years. You know, to ease the transition to HTML5- after all, Gnash can be compiled and run under Windows itself.

---

### Post by NightwishFan on 2010-06-26
The only flash I use is for video links my friends give me so I deleted flash and am keeping swfdec. I plan on giving bug reports to the project, as well as gnash and lightspark. Gave me something else to do in my spare time.

---

### Post by khelben1979 on 2010-06-27
Yes, they should.

---

### Post by phrostbyte on 2010-06-27
> **NightwishFan said:**
> I just tried swfdec in lucid 64-bit. It works with Youtube. Gnash looked more promising to me but it does not play the videos.

swfdec works better with YouTube and Gnash works better with typical Flash animations. From my experience at least.

---

### Post by murderslastcrow on 2010-06-27
Ah- is there any reason why the Swfdec and Gnash projects can't be consolidated? I do remember listening to the main Gnash developer commenting on how his project is fairly recent and didn't get tons of support until mobile device vendors got interested, and then it started to catch on.

But yeah, if they can get some help filling in the version 9 and 10 specifications, I think it would be beneficial to everyone. What's the best way to go about doing this? I mean, do they take donations for help in hiring extra developers? Is the best way to help just to learn the language they're using and code along with them?

I'd really like to see this turn out sooner than later, but I'm not sure if it's a time-related issue or a knowledge-related issue that's keeping it from being a complete solution. Of course, I'm sure these seem like fairly stupid questions considering how open source usually works, but I don't want to make assumptions of how these projects are operating at the moment.

In fact, I might just get on their mailing lists and figure it out, but it'd be nice if these projects got a bit more support from the community. Sure, we want to encourage open formats, but being able to adopt more formats into our open specifications and programs would also be a good idea. Maybe some day we won't have to reverse-engineer all this stuff anymore.

I guess with Flash on 32-bit and with the wrapper in 64-bit, most people don't see a compelling reason to support a project like Gnash?

---

### Post by NightwishFan on 2010-06-27
I believe Gnash actually uses hardware acceleration. That is a big plus.

---

### Post by geoken on 2010-06-27
> **lotharjade said:**
> 
The development of Flash seems to drag along slowly compared to other software, even Adobe's own software suite (Photoshop, Dreamweaver, etc..).  Some have speculated that not only does Adobe not put much investment in developing Flash, that it doesn't care a whole lot about how it is doing.

Why would you say it develops slow? From what I can see it's capabilities match and exceed everything browsers are doing, and even proposing to do.


-Video support is, and has been for some time, more comprehensive than HTML 5

-Font support has been ahead of HTML for years and will continue to be more comprehensive even when a all browsers support web fonts

-Support for vectors based animations back when very few browsers fully supported svg

-fully supports 3d, browsers are only starting to talk about/support this

---

### Post by phrostbyte on 2010-06-27
> **geoken said:**
> Why would you say it develops slow? From what I can see it's capabilities match and exceed everything browsers are doing, and even proposing to do.


-Video support is, and has been for some time, more comprehensive than HTML 5

-Font support has been ahead of HTML for years and will continue to be more comprehensive even when a all browsers support web fonts

-Support for vectors based animations back when very few browsers fully supported svg

-fully supports 3d, browsers are only starting to talk about/support this

There is a difference between supporting something, and supporting something well.

[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]

---

### Post by phrostbyte on 2010-06-27
> **murderslastcrow said:**
> Ah- is there any reason why the Swfdec and Gnash projects can't be consolidated? I do remember listening to the main Gnash developer commenting on how his project is fairly recent and didn't get tons of support until mobile device vendors got interested, and then it started to catch on.

But yeah, if they can get some help filling in the version 9 and 10 specifications, I think it would be beneficial to everyone. What's the best way to go about doing this? I mean, do they take donations for help in hiring extra developers? Is the best way to help just to learn the language they're using and code along with them?

I'd really like to see this turn out sooner than later, but I'm not sure if it's a time-related issue or a knowledge-related issue that's keeping it from being a complete solution. Of course, I'm sure these seem like fairly stupid questions considering how open source usually works, but I don't want to make assumptions of how these projects are operating at the moment.

In fact, I might just get on their mailing lists and figure it out, but it'd be nice if these projects got a bit more support from the community. Sure, we want to encourage open formats, but being able to adopt more formats into our open specifications and programs would also be a good idea. Maybe some day we won't have to reverse-engineer all this stuff anymore.

I guess with Flash on 32-bit and with the wrapper in 64-bit, most people don't see a compelling reason to support a project like Gnash?

I don't think swfdec is actively maintained. Gnash still is however. Gnash uses C++.

There is also a new contender called lightspark..

---

### Post by Johnsie on 2010-06-28
I like flash and I enjoy that Apple users cannot use it efficiently. I'm and Apple hater, so I say long life flash and stay closed source. 

Flash being closed source is actually good for Android adoption.

---

### Post by KiwiNZ on 2010-06-28
Flash works the same on my Apple machines as it does on my non Apple machines , that is **badly**.
So your misplaced joy is wasted and misplaced hatred is wasted.

---

### Post by NightwishFan on 2010-06-28
My friend has Windows Vista and flash runs poorly on it as well. It lags in full screen and even crashes when adds pop up on youtube.

---

### Post by Johnsie on 2010-06-28
That sounds like a bad video card to me. I've only ever seen flash run badly on badly configured pc's and macs.

---

### Post by NightwishFan on 2010-06-28
Its a Nvidia 7 series. It gets 20,000 on glx gears (live cd).

---

### Post by KiwiNZ on 2010-06-28
> **Johnsie said:**
> That sounds like a bad video card to me. I've only ever seen flash run badly on badly configured pc's and macs.

Again incorrect, I have experienced first hand Flash performing badly on Windows machines that have been configured correctly and have no hardware issues.

I like Adobe product with the exception of Flash , it is bad , especially on mobile devices and NOT just Apple .

---

### Post by Johnsie on 2010-06-28
Works fine on my HTC Desire, My Nokia E63 and all the computers in my work and at home. Maybe you just don't know how to set up the computers properly or are still using dial-up lol ;-) I don't think moving away from flash isn't going to help you, because html 5 will probably lead to similar issues. Good multimedia requires a decent setup and proper resource management.

---

### Post by NightwishFan on 2010-06-28
It works here on my Integrated intel linux 2.12git driver. :) Though I prefer something with acceleration so if flash will be around I will be using gnash/lightspark I hope.

---

### Post by KiwiNZ on 2010-06-28
> **Johnsie said:**
> Works fine on my HTC Desire, My Nokia E63 and all the computers in my work. Maybe you just don't know how to set up the computers properly ;-) I don't think moving away from flash isn't going to help you, because html 5 will probably lead to similar issues. Resource management etc.

No need to insult me . I have built many many  PC's I have managed a 10,000+ PC network and a 15 year + IT veteren so stop the rude crap before I enforce the COC.
The issues with Flash are well documented, they are real , get over it .

---

### Post by NightwishFan on 2010-06-28
:-s =D>
[COLOR="White"]Harsh, but I can understand.[/COLOR]

---

### Post by MCVenom on 2010-06-28
Flash has issues, but if Adobe made *.swf an open format and supported players like Gnash I think we'd see a lot of those issues go away. Gnash already consumes much less resources than Flash Player, for one. ;)

---

### Post by murderslastcrow on 2010-06-29
Yeah, when Windows XP came out, Flash ran like crap on my computer, since it was actually fairly old.

On the same computer with Gnash, I can play Flash games with ease using e17 as a window manager. So yeah, it would seem that Gnash has got something right, which I would expect since it's been built for multiple platforms and for Linux from the very beginning.

=,= I wish I had the time to learn C++ and help them out right now.

---

### Post by dwmcallister on 2010-07-14
> **BlackOtaku said:**
> Flash has issues, but if Adobe made *.swf an open format and supported players like Gnash I think we'd see a lot of those issues go away. Gnash already consumes much less resources than Flash Player, for one. ;)

SWF (the specification of the format) is a published specification with no restrictions. I think the LightSpark project is based on the current spec, in fact.  Gnash is based on an older version.

---

