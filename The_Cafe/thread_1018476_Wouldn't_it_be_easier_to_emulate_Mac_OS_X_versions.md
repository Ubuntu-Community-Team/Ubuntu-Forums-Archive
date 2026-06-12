---
title: "Wouldn't it be easier to emulate Mac OS X versions of apps like Adobe InDesign?"
date: 2008-12-22
forum: The Cafe
---

### Post by ricky22 on 2008-12-22
Hey all,
I've been using Ubuntu for 3 years now, got a hell of a lot of help from this forum and the Ubuntu community in general, for which I am eternally grateful:-)
I read somewhere that the single biggest obstacle to wider Linux adoption on desktop is the lack of Linux ports of Adobe applications like InDesign and Photoshop. Also, even though we have OpenOffice, having a free, working solution for running MS Office under Linux would make it easier for many users to migrate.
Since Mac OS X is essentially a Unix system, wouldn't it be easier to make those applications available under Linux using the Mac versions and a Mac OS emulator rather than running the Windows versions with WINE, which at least for me doesn't work as smooth as it should?
Just a thought, I'm not an expert on emulation, virtualisation etc. If the above doesn't make sense, please ignore. I would still very much like to know what you think. Cheers,
Patrick

---

### Post by DeadSuperHero on 2008-12-22
Well, to do so you would need to reverse engineer Cocoa, and most likely also Carbon.

From what I know, Coco is an application layer for apps written in a language called Objective-C. The language itself is derived from Steve Job's NeXTSTEP project when he was kicked out of Apple for a while.

NeXTSTEP WAS in fact, reverse engineered by the GNU project, as well as several others. I know that GNUSTEP has a fairly good documentation on what is the basis of Objective-C, but Apple owns the Objective-C language, which can only be compiled or used on an Intel Mac.

My personal stance is to help existing open source projects by suggesting a feature that you happened to like in a proprietary app. GIMP, for example, has gotten a much more usable interface due to user request.

Edit: Oh yeah, and also Mac OSX is locked down by so many EULA's, you'd get sued by Apple just for attempting to emulate their products and proprietary codes on a system. Just look at how they're trying to fight Psystar.

---

### Post by Hangwire on 2008-12-22
Interesting idea. 
Apple will kill us all though...

---

### Post by MikeTheC on 2008-12-22
@ OP

With all due respect, I think you're failing to understand the underlying political differences here.

While Microsoft would *prefer* to sell you Windows, they'd rather have you run the Win** platform one way or another so that you'll buy their software, and so that Microsoft's partner developers and others still make money through selling you products to use with that platform.

Apple, on the other hand, has zero interest in you using the Mac OS X platform in any way, shape or form that didn't involve them selling it to you as part of a total "Mac experience". They want your money and your contribution to the Mac OS user-base headcount, but *only* on ***their*** terms.

Whether you like, dislike, or even agree with Apple's position on this is irrelevant. That simply is how it is. It's not in their perceived "best interest" to allowing the means to run Aqua/Cocoa apps without a "Mac OS X-on-Apple Hardware" business transaction first. Think of it a bit like shopping at SAM's Club, or Costco, or BJ's -- they only want your money (for products) ***after*** you've paid for the right to buy from them.


Now, none of this is to say that it's technologically impossible to re-implement Aqua/Cocoa on Linux. Here's the thing, though. Wine and CrossoverOffice already exist and are already perfectly viable products; products which have taken years and years (I think Wine itself has been around for what, like almost 10 years?) to make. One can only assume, legal challenges aside, that it would take about as long to do the same for Aqua/Cocoa apps. Why would you want to wait?

I mean, Microsoft keeps changing things to try to break compatibility. Surely Apple, under similar circumstances, would do the same thing. And if you're *already* not "running Windows" by using Wine or CrossoverOffice, isn't "running the Mac platform" kind of redundant?

---

### Post by ricky22 on 2008-12-28
Mr. Psychopath, MikeTheC, 
I thought the biggest problems with software emulation are technical, and emulating a Unix system under a Unix-like system would pose less challenges. I missed the whole legal aspect, restrictions by companies etc. As I said before, I'm not an expert, just curious:-) Thanks a lot to both of you for clarifying that, happy new year!
Patrick

---

