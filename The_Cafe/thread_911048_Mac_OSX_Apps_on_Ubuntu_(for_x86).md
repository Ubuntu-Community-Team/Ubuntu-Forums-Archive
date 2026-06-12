---
title: "Mac OSX Apps on Ubuntu? (for x86)"
date: 2008-09-05
forum: The Cafe
---

### Post by luckyuser on 2008-09-05
Does anyone know of (or is anyone interested in) any current projects for running Mac OSX based apps on x86 computers with Linux?

I don't know anything about Mac codes, so I don't even know if it is possible. 

(Mac-on-Linux not only looks silent but it is for PowerPCs that already have the Mas OS, so that obviously wouldn't be of much help for users with x86  computers.)

---

### Post by billgoldberg on 2008-09-05
> **luckyuser said:**
> Does anyone know of (or is anyone interested in) any current projects for running Mac OSX based apps on x86 computers with Linux?

I don't know anything about Mac codes, so I don't even know if it is possible. 

(Mac-on-Linux not only looks silent but it is for PowerPCs that already have the Mas OS, so that obviously wouldn't be of much help for users with x86  computers.)

If it's possible I haven't heard of it.

---

### Post by Tindytim on 2008-09-05
You do know that Mac OSX mainly support x86? Macs have had intel processors for a while now. Unless you want to run Mac OS9 software?

What do you want to run? things from iLife? Garage Band?

---

### Post by the yawner on 2008-09-05
You mean, a MAC counterpart of Wine? I'm not sure, but I think that would be harder to implement.

---

### Post by luckyuser on 2008-09-05
> **Tindytim said:**
> You do know that Mac OSX mainly support x86? Macs have had intel processors for a while now. Unless you want to run Mac OS9 software?

What do you want to run? things from iLife? Garage Band?

Yeah, I know they've been using intel processors and all but i'm not about to buy a mac when Ubuntu is meeting my needs. 

To answer your question about the apps, I'm interested in Scrivener:
[http://www.literatureandlatte.com/scrivener.html]("http://www.literatureandlatte.com/scrivener.html")

But I made this thread really for the purpose of seeing if there really is an interest in or knowledge of a project that's working towards getting Mac apps to run on linux. (I know mac os isn't linux, but I've been doing research into this and I've heard people say it's possible...but I haven't seen any thing to show it.)

---

### Post by ronnielsen1 on 2008-09-05
> But I made this thread really for the purpose of seeing if there really is an interest in or knowledge of a project that's working towards getting Mac apps to run on linux.

The only thing I can find are the following and I haven't tried them

[http://mac-on-linux.sourceforge.net/](http://mac-on-linux.sourceforge.net/)
[http://www.heise.de/ix/artikel/E/1996/11/064/](http://www.heise.de/ix/artikel/E/1996/11/064/)

As far as Scrivener is concerned, Writers Cafe should be in the repositories. Not sure if that's close enough or not

[http://www.writerscafe.co.uk/](http://www.writerscafe.co.uk/)

---

### Post by Tindytim on 2008-09-05
> **luckyuser said:**
> Yeah, I know they've been using intel processors and all but i'm not about to buy a mac when Ubuntu is meeting my needs.

I'm not telling you to get a Mac, why do you think I was? I was simply stating you wouldn't have to emulator a PowerPC processor to get something to run, thus making it easier.

I would think it would be easier (Than Windows), consider Mac OSX is *nix and OpenGL.

---

### Post by Iceni on 2008-09-05
can you run osx in vmware?

---

### Post by mips on 2008-09-05
> **Iceni said:**
> can you run osx in vmware?

Depends. OS X server I think you can but only if vmware is running on a genuine apple server. Part of the EULA.

---

### Post by Tindytim on 2008-09-05
^If you care about about the wishes of the company.

---

### Post by mips on 2008-09-05
> **Tindytim said:**
> ^If you care about about the wishes of the company.

It's not that, I'm merely limiting my response to be in line with forum rules.

---

### Post by anatolica on 2008-12-04
> **luckyuser said:**
> Does anyone know of (or is anyone interested in) any current projects for running Mac OSX based apps on x86 computers with Linux?

I don't know anything about Mac codes, so I don't even know if it is possible. 

I would love to see Mac OSX apps run on linux, but my searches are in vain up to now. I remember reading that it's not impossible, but I have no idea how to.

(edit: PS. and for the most part, I want this to use Scrivener.. I have had a look at writers' cafe and it is recently updated but still scrivener seems more promising)

---

### Post by dannytatom on 2008-12-04
I don't really have a need to run any mac apps, but it'd be nice to know I can. :P
f there was anything, I'd try [EventBox]("http://thecosmicmachine.com/") in a heartbeat.

& the [Mac-on-Linux]("http://mac-on-linux.sourceforge.net/") site hasn't been updated since 2007. :/

---

### Post by lyceum on 2008-12-04
If I understand correctly, aren't Apple Apps written in JavaScript? I would rather see a program made for Gnome that could run Apple Apps, or any other apps written in JavaScript. That way we are not borrowing the program, just the apps. If the Apps program for Ubuntu is not set up to use apps written in JavaScript, I would not care if it were there or not. I would want anyone to be able to write apps, and JavaScript is a common enough language that is not too hard to learn. Personally, I do not like to "steal" programs with wine. I would rather we made our own and made it better.

---

### Post by Erunno on 2008-12-04
> **lyceum said:**
> If I understand correctly, aren't Apple Apps written in JavaScript

Wrong, most Apple applications are written with the Objective-C programming language and use a proprietary API called Cocoa. In order to run Apple applications on Linux the whole Cocoa API would have to be reimplemented using techologies available on Linux. This would be monumental endeavour with little gain. JavaScript is one of the techologies to create Dashboard widgets.

---

### Post by ankursethi on 2008-12-04
I use a Mac and I've tried (unsuccessfully) to learn writing apps for OS X.

You generally use the Objective-C programming language along with the Cocoa API to write apps for the Mac. The compiler used is good ol' GCC. It's noteworthy that Cocoa descends from the API used on the NeXtSTEP operating system. In fact, a large part of OSX also derives from NeXtSTEP. Interestingly, NeXt (in partnership with Sun) once made an effort to get the NeXtSTEP API running on Windows and UNIX systems and called the result of their efforts OpenSTEP. Both NeXtSTEP and OpenSTEP were very popular with the scientific community. In fact, they were so popular that an open source project sprung up to clone the NS API. The project is called GNUStep and the code is available from [http://gnustep.org](http://gnustep.org)

In theory, it should be possible to make GNUStep as compatible with Cocoa as possible, which will allow open source Mac apps to compile flawlessly on Linux/Windows. In practice this would be very difficult to do because Apple has added many undocumented and/or propreitary features to Cocoa which are not available on other platforms. But yeah, you *can* make simple apps work flawlessly on Linux.

---

### Post by 3rdalbum on 2008-12-04
What we really need is for Macintosh application developers to use X11 and libraries that are available on open platforms. Then those programs would virtually just be a recompile away from Linux, and would work on OS X if the user had XFree86 installed.

Obviously we couldn't get Apple to write their programs like that, but who really need iTunes anyway?

---

### Post by bp1509 on 2008-12-04
d

---

### Post by anatolica on 2008-12-04
> **lyceum said:**
> Personally, I do not like to "steal" programs with wine. I would rather we made our own and made it better.
I totally agree with that, if only I could learn how to do it;)

---

### Post by jdong on 2008-12-04
(1) The Mach-O executable format was attempted to be ported to NetBSD and Linux but both efforts stalled 2-3 years ago because of lack of interest.


(2) As far as I know, there is no API-compatible or ABI-compatible reimplementation of OS X's CoreFoundation, which will be the biggest roadblock to getting OS X applications working on Linux. Apple hasn't exactly been sleeping for the past 8 or so years OS X has been in development; producing a compatible ABI will not be an easy task.

---

### Post by conundrumx on 2008-12-04
Short answer: no.

Longer answer: Still no, unless you're patient and not afraid of breaking Apple's EULA.  OSx86 has been around for a while, and I know a guy who knows a guy who's run OSx86 inside VMs before.

yeah.

---

### Post by eternalnewbee on 2008-12-04
> Short answer: no.
+1
The Ubuntu Community and developers are (imho) in a unique position. Why (to speak in football terms) focus on the opponent's tactics? Let's focus on our own.

---

### Post by MikeTheC on 2008-12-04
I think the fundamental difference here starts with the corporate attitude.

Obviously, selling Windows is sort of Microsoft's bread-and-butter. However, assuming you go the "legitimate" route (which many but not all do), then if you're running pure Wine or Crossover Office, then you're doing that for the benefit of running purchased win32 apps, including Office, etc. Which means you're *still* Microsoft's customer.

On the other hand, Apple wants you as a customer only on the terms they've set forth, and I don't think they're really interested (for better or worse can be argued) in having you as a customer if you're willing to follow their rules. "Love me, love my hardware" is kind of the attitude.

I think Apple would absolutely have a cow if someone managed to start implementing Mac OS X APIs independently, like Wine/Crossover Office.

---

### Post by jdong on 2008-12-04
Does Apple have any sort of IP claim on the CoreFoundation APIs? Is there legal precedent in notable jurisdictions for IP/patent violation simply for implementing compatible APIs without any sharing of code?

---

### Post by ssam on 2008-12-04
this has been asked before. it would need an equivalent to wine. a reimplementation of all the mac os x APIs.

wine has taken 15 years to get to where it is now. a mac equivalent would presumably take about the same time to make (it might be a slightly easier task due to mac os x being more unixy than windows, but there may be other issues that make it harder).

however, i have not seen even the beginnings of a project to do this.  expect that the number of people who would find it useful is smaller than for wine, so the number of developers interested is probably smaller.

---

### Post by MikeTheC on 2008-12-04
While I can understand the desire, from a purely "enthusiast" perspective, I believe this to be a fundamentally flawed proposition. Here's why:

People run Windows (as a platform, forget the implementation) *out of necessity* for compatibility with the world's de-facto standard OS platform.

People run Mac OS X *out of choice, **not** need* (with, of course, some few exceptions).

People run Linux *also out of **choice***.


Consequentially, there is a greater "compelling need" to have access to the win32 "platform" than there is for pretty much *any* other platform.

Moreover, people who run Mac OS X are *already* "not" running Windows, so to speak. And if you're *already* not using the "great evil platform", the perceived need to move away from what you've got is probably *substantially* less. You don't see significant numbers of Mac users complaining about what they're using, which of course is a *significant* portion of why anybody changes *anything* in life.


It's not that it wouldn't be a great *achievement* to get the OS X framework re-implemented in Linux, but it's probably a reasonable bet to make that it would be easier to *port* desired Mac OS X apps *to Linux* -- or, conversely, to *replace those apps entirely* -- than it would be to clean-room re-implement Mac OS X, *especially* with Apple's hell-bent-for-leather attitude vis a vis controlling the entire widget and not "letting" users have a non-Apple-generated Mac OS X experience.

And *that's* entirely different from Microsoft, inasmuch as while Microsoft would rather people be running a "real" copy of Windows, they ultimately understand that ***all** eyeballs are **good** eyeballs*, since their profit is not so much in selling Windows (in the direct-to-customer sense) but in selling Office.

---

### Post by lyceum on 2008-12-04
> **Erunno said:**
> Wrong, most Apple applications are written with the Objective-C programming language and use a proprietary API called Cocoa. In order to run Apple applications on Linux the whole Cocoa API would have to be reimplemented using techologies available on Linux. This would be monumental endeavour with little gain. JavaScript is one of the techologies to create Dashboard widgets.

Then I want to change my vote to no.

---

### Post by frenchn00b on 2009-09-18
Hey guys, realize, that Mac OS 7 had already a notepad that talks ;)
try Mac is better than Linux (but not free)

[here the emulator made for you ]("http://ubuntuforums.org/showthread.php?t=1265153") I made there an howto to use macintosh under linux.
Find and google this : [[IMG]http://img245.imageshack.us/img245/4400/setupmac.jpg[/IMG]](http://img245.imageshack.us/i/setupmac.jpg/)
and you have sound in your notepad and lot of features :)

---

### Post by Tibuda on 2009-09-18
> **frenchn00b said:**
> Hey guys, realize, that Mac OS 7 had already a notepad that talks ;)
try Mac is better than Linux (but not free)

[here the emulator made for you ]("http://ubuntuforums.org/showthread.php?t=1265153") I made there an howto to use macintosh under linux.
Find and google this : [[IMG]http://img245.imageshack.us/img245/4400/setupmac.jpg[/IMG]](http://img245.imageshack.us/i/setupmac.jpg/)
and you have sound in your notepad and lot of features :)

have you tried espeak?

---

### Post by fela on 2009-09-18
I'd like to be able to run OSX apps on Linux (or ubuntu if that was my chosen distro). But not like Wine.

The only way I'd want to run them is by Apple porting all their GUI APIs such as Cocoa, Quartz, etc etc to Linux, and then I'd happily run OSX apps on Linux. I don't want to run them on a clunky mess of an API copy such as Wine.

---

### Post by pookiebear on 2009-09-18
Why don't we push it this way.

Say we want a WINE like API for running Mac apps. 
Say we purchase the APP from Apple. 
And it comes with the MACWINE
So apple makes this MACWINE API but to get it you have to buy the apple app. They could sell more applications like garage band. But I guess they might potentially sell less hardware. They could port that macwine to BSD and Linux and maybe charge $20 for it. But you can't get to the website to buy it unless you have a code from the sale of the software.

---

### Post by DeadSuperHero on 2009-09-18
Here's a thought: how about just support some of the upcoming multimedia projects on Linux and help them become better applications? Less stress, less mess.

---

### Post by Skripka on 2009-09-18
> **pookiebear said:**
> Why don't we push it this way.

Say we want a WINE like API for running Mac apps. 
Say we purchase the APP from Apple. 
And it comes with the MACWINE
So apple makes this MACWINE API but to get it you have to buy the apple app. They could sell more applications like garage band. But I guess they might potentially sell less hardware. They could port that macwine to BSD and Linux and maybe charge $20 for it. But you can't get to the website to buy it unless you have a code from the sale of the software.

You didn't actually read what anyone said before you posted, now did you?  If you had, you wouldn't have even bothered posting this as it was shot down--last year.

---

### Post by RealG187 on 2009-10-27
> **conundrumx said:**
> Still no, unless you're patient and not afraid of breaking Apple's EULA.I'm not afraid of braking Apple's EULA because it's not legally binding and is actually illegal by antitrust laws.

I'm sure Microsoft wants to sue the makers of Wine, they can't so why should Apple?

---

### Post by Chronon on 2009-10-27
> **RealG187 said:**
> I'm not afraid of braking Apple's EULA because it's not legally binding and is actually illegal by antitrust laws.

I'm sure Microsoft wants to sue the makers of Wine, they can't so why should Apple?

The EULA prohibits running OSX as a guest, unless it's on a Mac host.  I believe that's what the previous poster was referring to.

---

### Post by koshatnik on 2009-10-27
> **luckyuser said:**
> Yeah, I know they've been using intel processors and all but i'm not about to buy a mac when Ubuntu is meeting my needs. 

To answer your question about the apps, I'm interested in Scrivener:
[http://www.literatureandlatte.com/scrivener.html]("http://www.literatureandlatte.com/scrivener.html")

But I made this thread really for the purpose of seeing if there really is an interest in or knowledge of a project that's working towards getting Mac apps to run on linux. (I know mac os isn't linux, but I've been doing research into this and I've heard people say it's possible...but I haven't seen any thing to show it.)

Scrivener is awesome. That and Capture NX keeps me on OSX. I'd really love to have scriv on linux.

---

### Post by RealG187 on 2009-10-28
> **Chronon said:**
> The EULA prohibits running OSX as a guest, unless it's on a Mac host.  I believe that's what the previous poster was referring to.So they are forcing you to buy their brand of computers. That's very anti-free trade.

---

### Post by koshatnik on 2009-10-28
Does anyone actually pay any attention to the EULA?

---

### Post by Pasdar on 2009-10-28
I'd rather any possible developers wanting to work on such a project spend their time helping wine make windows apps fully compatible on Linux. For the few apps that are only available on Mac, we can make look alikes, etc.

---

### Post by steev182 on 2009-10-28
Really, it's that easy huh?

OK, Could there be some compatible, comparable and Linux native applications for Garageband and iPhoto please then? These are the only things I really miss from OSX.

---

### Post by SuperSonic4 on 2009-10-28
Apple's programs are crap at best

---

### Post by Pasdar on 2009-10-28
> **steev182 said:**
> Really, it's that easy huh?

OK, Could there be some compatible, comparable and Linux native applications for Garageband and iPhoto please then? These are the only things I really miss from OSX.

Doesn't Picasa 3.5 do more than IPhoto? Much much more actually... I think the only possitive thing that can be said mac apps is that they look quite nice.

---

### Post by Johnsie on 2009-10-28
I would like to see OSX and Windows programs working seemlessly and flawlessly on Linux. I also think Ubuntu should be shipped with Wine out of the box make things more seemless. 

I find it frustrating that there are some programs I can't run because I've booted into the wrong OS.

Also, there's no point re-inventing the wheel every time a killer app comes along on another platform. Yeah you can make an 'equivilent' but 9 times out of 10 the 'equivilent' is not equivilent or as professional as the original... Have a look at The GIMP compared to Photoshop. Why re-invent the wheel and replace it with something less rounded?


The main problem with getting OSX programs to run on Linux is that Apple would probably do whatever they could to sue you and shut you down. They are very, very protective about which environment or hardware you can run software in. They'd probably get you for breaching some kind of patent that they've registered to prevent competitors competing against them.

---

### Post by RealG187 on 2009-10-28
> **koshatnik said:**
> Does anyone actually pay any attention to the EULA?Doubt it to be honest...

---

### Post by Frak on 2009-10-28
> **koshatnik said:**
> Does anyone actually pay any attention to the EULA?
Yes, I do. That's why I don't run OS X on my non-Mac computers. I don't care if it "isn't legally binding". Apple says it's legally binding, and I won't be the next one to fight them for it.

---

### Post by jonian_g on 2009-10-28
> **Frak said:**
> Yes, I do. That's why I don't run OS X on my non-Mac computers. I don't care if it "isn't legally binding". Apple says it's legally binding, and I won't be the next one to fight them for it.

Give the man his candy!

---

### Post by phrostbyte on 2009-10-28
You kind of can already. I am not sure how compatible it is with the current OS X. GNUStep implements Cocoa, and GCC has an Obj-C frontend. So in theory at least simple OS X apps can be recompiled with and for Linux.

Here is one such example: [http://en.wikipedia.org/wiki/TextEdit](http://en.wikipedia.org/wiki/TextEdit)

---

### Post by Frak on 2009-10-28
> **phrostbyte said:**
> You kind of can already. I am not sure how compatible it is with the current OS X. GNUStep implements Cocoa, and GCC has an Obj-C frontend. So in theory at least simple OS X apps can be recompiled with and for Linux.

Here is one such example: [http://en.wikipedia.org/wiki/TextEdit](http://en.wikipedia.org/wiki/TextEdit)
That theory is correct. Very simple programs work fine with GStep and GO-CC. Anything past that, such as implementing graphics, breaks terribly. Understandable.

---

### Post by Skripka on 2009-10-28
> **Frak said:**
> That theory is correct. Very simple programs work fine with GStep and GO-CC. Anything past that, such as implementing graphics, breaks terribly. Understandable.

So what you're saying is that a graphical "Hello World" is not presently ported from OSX to Linux? :)

---

### Post by Frak on 2009-10-28
> **Skripka said:**
> So what you're saying is that a graphical "Hello World" is not presently ported from OSX to Linux? :)
Yes.

---

### Post by juancarlospaco on 2009-10-28
This thing already exist, its named **CocoTron**, a wine-like to run OSX apps, 
ATM only for developer purposes, on +10 years maybe can be just like Wine.

Wine has started to try to run Win 3.0 apps on linux and see today, who knows...

:)

---

### Post by 3rdalbum on 2009-10-29
> **juancarlospaco said:**
> This thing already exist, its named **CocoTron**, a wine-like to run OSX apps, 
ATM only for developer purposes, on +10 years maybe can be just like Wine.

No, it's not like that. Cocotron is a set of APIs similar to Cocoa. A Mac OS programmer could write their program for Cocotron with a relatively gentle learning curve and the source code could be compiled for other platforms where Cocotron is available.

Wine runs unmodified Windows programs. Cocotron allows OS X developers to write source code that can be compiled for other platforms.

---

### Post by fslezak on 2010-11-11
I heard that WindowMaker uses the Cocoa and/or <whatever the other one is> for its applications. Would this mean that we could just build an application that can interpret Objective-C and uses the WMaker libraries?

---

### Post by Quadunit404 on 2010-11-11
Woah, over a year old and revived just like that!

---

