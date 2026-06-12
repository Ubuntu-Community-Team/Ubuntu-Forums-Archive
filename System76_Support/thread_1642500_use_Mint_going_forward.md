---
title: "use Mint going forward?"
date: 2010-12-10
forum: System76 Support
---

### Post by tlroche on 2010-12-10
Just wondering, how do folks feel about Mint? E.g. what have been your experiences with Mint? And has System76 considered rebasing on Mint (i.e. making it the default distro)? Why I ask:

I'm [having a video problem]("http://ubuntuforums.org/showthread.php?t=1640450") (not a display problem, but a problem playing video files and DVDs) with my PanP5 running Lucid. As part of my debugging, last night I burned and booted the Mint 10 (aka Julia) [64-bit Live DVD]("http://www.linuxmint.com/edition.php?id=70"). OOTB it solved my video problem, no fiddling with repositories. While there I played a bit--everything seemed to work just fine, no configuration required.

So, granted, my Mint experience is pretty tiny. But I note that Mint seems to be getting good reviews, and it's Ubuntu under the hood anyway. So I'm wondering, esp given

[LIST]
[*]recent problems with Unity, which seems to be Canonical's choice going forward
[*]Mint seems to solve problems configuring proprietary drivers and apps 
[/LIST]

if s/Ubuntu/Mint/ makes sense.

---

### Post by Simian Man on 2010-12-10
Your video problem was almost certainly fixed by Mint coming with libdvdcss, the redistribution of which is illegal in several countries including the United States.  Because System76 undoubtedly wants to do business in such places, I very much doubt they'd ship that particular package.

---

### Post by ajgreeny on 2010-12-10
I agree with Simian Man about the inclusion of libdvdcss2 in Mint's default version probably being the reason for it playing your videos and DVDs.  However, it is the job of about 10 seconds to add that package to Ubuntu, either with a simple shell script provided in the libdvdread package, /usr/share/doc/libdvdread4/install-css.sh, so simply navigate to */usr/share/doc/libdvdread4* and then run the *install-css.sh* shell script with sudo.

I have used both Mint and Ubuntu for the last several years and versions of both, but still I come back to Ubuntu; it just feels more comfortable somehow, though I find it very hard to say exactly why.

There are a few things I dislike about the Mint default setup, however, including that awful menu.  OK, I know a lot of users seem to love it, but to my way of thinking it simply gets in the way, and I certainly don't need all the hand holding help(?) that it gives.  However, I don't use the menu-bar in Ubuntu either, just the main menu with a single panel icon.  Perhaps I'm just very unusual?

---

### Post by isantop on 2010-12-10
Libdvdcss, among others, are definitely part of the reason we don't ship Mint. To be honest, I'm not even sure that what Mint does is legal, since they are redistributing that file.

The other part of it is that System76 sells ubuntu computers. We are the Ubuntu computer guys. Us switching to Mint would be like if Apple distributed Windows on the Macs. It's just not something they'd do. They've built their product up as a whole, and that product includes OS X.

It's a similar story here. We don't just build computers, we build whole, complete products. A big part of that product is the Ubuntu OS, and we plan on sticking with it.

By the way, we do offer installation instructions on our knowledge base for all of the restricted codecs, including those for DVD playback. You can find them here: [http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by tlroche on 2010-12-10
> **tlroche said:**
> I'm [having a video problem]("http://ubuntuforums.org/showthread.php?t=1640450") (not a display problem, but a problem playing video files and DVDs) with my PanP5 running Lucid. [Booting] the Mint 10 (aka Julia) [64-bit Live DVD]("http://www.linuxmint.com/edition.php?id=70") [solves] my video problem

though, I might add, only for the duration of the Mint boot. Note the link to the problem case above, because ...

> **Simian Man said:**
> Your video problem was almost certainly fixed by Mint coming with libdvdcss

That Mint ships libdvdcss is very likely true. However it is also clear in the [problem thread]("http://ubuntuforums.org/showthread.php?t=1640450") that my PanP5 already has libdvdcss, libdvdnav, and libdvdread installed, e.g.

> **tlroche said:**
> $ totem --version
> totem 2.30.2
$ totem &
> libdvdread: Using libdvdcss version 1.2.10 for DVD access
> libdvdnav: Using dvdnav version 4.1.3
> libdvdread: Using libdvdcss version 1.2.10 for DVD access


> **ajgreeny said:**
> simply navigate to */usr/share/doc/libdvdread4* and then run the *install-css.sh* shell script with sudo.

Unfortunately that was already not only already done (see totem above), but redone, as [previously requested by isantop]("http://ubuntuforums.org/showpost.php?p=10216151&postcount=2"), and yet the [Lucid problem persists]("http://ubuntuforums.org/showthread.php?t=1640450").

> **isantop said:**
> we do offer installation instructions on our knowledge base for all of the restricted codecs, including those for DVD playback.

I'm aware of that--I used those docs @ box setup. Nevertheless, the PanP5 is currently broken WRT video playback, and the [problem thread]("http://ubuntuforums.org/showthread.php?t=1640450") remains open.

> **isantop said:**
> We are the Ubuntu computer guys. Us switching to Mint would be like if Apple distributed Windows on the Macs.

Your analogy fails, given the close relationship of Mint to Ubuntu. A closer analog for System76 switching to Mint would be  Microsoft switching from DOS to Windows 3.0, although even that latter transition was more significant. Switching from Ubuntu to Mint would certainly involve far less change than did Apple switching from MacOS to OSX, or from Motorola to PowerPC to Intel.

The legal question is more interesting, yet certainly Mint is distributed in the US and has US mirrors.

---

### Post by jml on 2010-12-11
Just to add my two cents.  As isantop states, System 76 has built it's customer base by selling and supporting good hardware teamed up with Ubuntu.  While Mint is based on Ubuntu (the Mint Debian Edition not withstanding,) Mint has it's own repositories.  From a practical point if view, it would be a lot harder to support Mint going forward, and supporting all of their current customers running Ubuntu.  Plus, Ubuntu has a larger market share than Mint, so from a business point of view, it makes sense to use Ubuntu.

One other thing to consider is the fact that System 76 builds Linux friendly hardware.  It's not that difficult to install a different distro on them.  I actually run Debian Stable (5.0) on my third generation Darter, and Debian Testing (6.0) on my first generation Darter.  In fact the only System 76 product I am still running Ubuntu on is my first generation Starling.  I need the System 76 driver to get reasonable wireless performance out of it.

Joe

---

### Post by msrinath80 on 2010-12-12
Nice point jml. There's also this other company called Zareason that sells Linux friendly laptops. Good thing about their philosophy is that they don't bundle "Zareason drivers" in a separate package. They make the effort to ensure that the custom drivers (if any) are actually merged upstream, so that they become part of the usual drivers that come with the kernel/distros. That said, I can't complain about S76 either. It's fairly straightforward to figure out what their python scripts do. I'm a happy user of the Lemu1. I too run Debian squeeze on it. But Ubuntu is far too volatile for my taste. And from the looks of the it, due to their very different visions compared to rest of the distros, they seem to be headed in the same direction as Fedora (read: Kitchen sink distro). But hey, whatever works for each of us is what we use :)

---

### Post by henrydubb on 2010-12-13
I must admit native Linux Mint install was one of the things I was looking at in buying a new computer. All things being equal Zareason would have won me over, but they lost me for other reasons.

I think the legalese is pretty bunk. The courts are making a clear distinction between potential to and probability of using technology for illicit purposes. If one breaks the ability a proprietary code for what would be legal purposes that is fine. But courts have also weakened the distinction between making illegal content available on your PC or just making it available wink, wink by other means. Which is to say Ubuntu is not is any more of a legally purer position than Mint or other distros that include this or that file.

With that said when I get my Starling the first thing I'll do is put Mint on. This is fine by me because I have a lot of particulars in my distro install. The question for me is if it works on Ubuntu will it work on Mint. I think the answer is a resounding yes.  Mint makes Ubuntu better rarely the other way around.    

I will certainly leave ubuntu net edition on and over time it might win me over. Or maybe just add the Mint menu to it. I am very grateful it will not be unitified. Which is all to say Ubuntu installs makes perfect sense in having an expanding pool of customers. While I try a lot of distros, Ubuntu is the base of all of them.

---

### Post by isantop on 2010-12-14
Needless to say, i am a bit biased, though my opinions right here are my own, and not necessarily those of System76, Inc.

I don't really agree with the Zareason philosophy. They do wonderful work, but in order to ensure out of the box compatibility, they may need to use previous generation hardware, or something that isn't of as high a quality as what I want. System76 doesn't make sacrifices like that. We offer top of the line, state of the art hardware like the bigger companies. On top of that, we do take part in the Zareason part of pushing drivers upstream. As of the time of writing, only three of our systems actually have fixes in our driver.

I'll use an example. Our new Bonobo and newer Servals are shipping with a USB 3.0 port. In order to allow Ubuntu to suspend/resume with USB 3, you need to patch it, else it will not suspend/resume.

---

### Post by jml on 2010-12-14
I have to agree with isantop.  When you look at other  companies supplying Linux on computers, they follow one of two paths.  Installing Linux on high end hardware with custom drivers, for a high price, like Emperor Linux.  Or installing Linux on somewhat modest hardware with less driver support for a lower price, like Linux Certified.  Don't get me wrong,  I am not criticizing either of these two companies.  I applaud any company that supports Linux.  But for my money, I like System 76's business model the best.

Joe

---

### Post by bill516 on 2010-12-16
Isantop makes sense here, both in terms of his assertions about legal software and the identity of System 76 with Ubuntu.

Now having said that let me say I run Debian Squeeze on my PanP4, as well as Mepis.  antiX runs from a jump-drive.  They all run cleanly.  Ubuntu 10.4 and Squeeze hibernate and suspend properly.  Mepis and antiX will suspend but not hibernate.

I do not run Mint, having tried it multiple times.  It makes a great initial impression but that menu is just not to my taste.  From a legal point of view it is one thing for an individual to go and get it, I suspect quite another for a company like System 76 to sell it.  If they did they could package the "free" version.  But I do not see the point, honestly.

---

### Post by henrydubb on 2010-12-17
Funny, that was my inclination looking at the two companies. For example, the staring had 2Gb of DDR3 ZaReason 13.1 has 1 Gb of DDR2. 


> **isantop said:**
> I don't really agree with the Zareason phil osophy. They do wonderful work, but in order to ensure out of the box compatibility, they may need to use previous generation hardware, or something that isn't of as high a quality as what I want. System76 doesn't make sacrifices like that. We offer top of the line, state of the art hardware like the bigger companies. On top of that, we do take part in the Zareason part of pushing drivers upstream. As of the time of writing, only three of our systems actually have fixes in our driver.

---

