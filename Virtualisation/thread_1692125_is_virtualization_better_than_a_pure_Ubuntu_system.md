---
title: "is virtualization better than a pure Ubuntu system?"
date: 2011-02-20
forum: Virtualisation
---

### Post by slowtrain on 2011-02-20
I'm wondering whether using Ubuntu in VirtualBox on a Windows computer is better than having a pure Ubuntu system?

That question emerges out of painful experience with Ubuntu problems with hardware.

I'm on the market for a new home desktop because my older HP system froze once every 3-5 suspends or hibernates since Ubuntu version 9.04.  I wasted a week of effort trying out BIOS updates and so forth to get rid of the problem, without success.  Given how I use the computer at home and feeling somewhat compelled to be 'green' and not have my machine on continuously, this is a big problem.  It's doubly a problem because when Ubuntu freezes and I hard restart, this seems to corrupt configuration settings and possibly worse.

I'm now trying a box built by a well-known company that specializes in building machines for Ubuntu.  The machine costs 40-50% again as much as comparable hardware from a company like HP.  I thought what I would get for the price difference was hardware that would actually work with Ubuntu.  After 5 suspends / hibernates, the machine now freezes whenever I use suspend.  Am likely going to send the computer back.

So I'm beginning to wonder whether the sweet spot for an Ubuntu user is to buy something like an HP computer and then run Ubuntu within Windows--just so Windows can handle the hardware?  Seems to work well on my Dell laptop.  And, on the occasions where I need a Windows machine, it's right there.

Anyone have any thoughts on the advantages or disadvantages of going this route?  One thing I'm wondering about is graphics cards.  If the card maker doesn't support linux, I guess that Virtualbox still handles this?  But, is it possible that if I hang on to the machine for, say, 6-7 years, newer versions of Virtualbox will stop working w/ either the old Windows version or the old hardware?

---

### Post by Hedgehog1 on 2011-02-21
I am running Ubuntu in Virtual box with Win7 as a host.

I am also running Win7 in Virtual box with Ubuntu as the host.

The newest Virtual box (Now 4.0.4 as of a day or two ago) will support compiz with Ubuntu as the guest operating system (the one inside th Virtual box).  This video card must be one that both Windows and Ubuntu like (mine is an NVidia), but the fancy Ubuntu graphics will function inside Vbox.

If you have a ton of horse power and lots of RAM, both combinations run well.  However, in your situation, I would either Dual-Boot OR run Ubuntu inside Virtual box with Win7 as the host.

Because Ubuntu uses less resources, it is just a better fit in a 'MS Windows' world.

Hope this helps...

:KS

---

### Post by HermanAB on 2011-02-21
Howdy,

The notorious Ubuntu freezes are mostly due to bad video drivers.  You can fix it, if you are willing to experiment for a weekend or two, to find a video driver version that works properly.

An alternative simpler solution, is to quit using Ubuntu till Canonical gets their QA problems sorted out.  OpenSuse or Fedora would both be good alternatives.

---

### Post by slowtrain on 2011-02-22
Howdy HermanAB:  I do suspect the video card is involved, at least on my new system.  Problem is I uninstalled the video drivers (going back to Ubuntu's own) and the problem was still there.  Very odd though--I also tried running from a USB startup disk, and the system froze systematically at startup, which is not something it was doing to start with.  

Maybe it does have something to do w/ the drivers, but then the drivers must be making some kind of permanent change somewhere.

I have been thinking of trying an alternative to Ubuntu.  Just worried that an alternative may not work as well and have a steep learning curve.  At least from what you're saying Fedora and OpenSuse are more robust than Ubuntu?  I wonder if Debian is? (Less learning curve I expect.)

---

### Post by slowtrain on 2011-02-22
Hi Hedgehog1:  The configuration I was considering was buying a Windows machine and then running Ubuntu in VirtualBox within Windows, using Windows to handle the hardware, which Ubuntu seems to have trouble with.

You seem to be saying, though, that when it comes to video cards I have to make sure that the card has drivers both for Windows and ubuntu under such a configuration?  Doesn't VirtualBox create an abstraction layer that allows Ubuntu to use the Windows graphics card driver or some such?  If not, I guess I'll have to make sure I get Nvidia.

Sounds like you have some experience with Ubuntu under virtualization.  Good to hear that my crazy idea of giving up on pure Ubuntu and running it within Windows so Windows can just deal with the hardware doesn't sound too crazy to you.

Thanks!

---

### Post by Hedgehog1 on 2011-02-24
> **slowtrain said:**
> 
You seem to be saying, though, that when it comes to video cards I have to make sure that the card has drivers both for Windows and ubuntu under such a configuration?  Doesn't VirtualBox create an abstraction layer that allows Ubuntu to use the Windows graphics card driver or some such?  If not, I guess I'll have to make sure I get Nvidia.


As best as I can tell, the video card is an abstraction layer **however the real card** the abstraction layer calls must be one that supports 3D.  So yes, you are quite right that the abstraction layer does separate things.  But I know NVidia works for sure.  If you have a buying choice, that reduces risk.

The windows nVidia drivers are most excellent, too.

:KS

p.s. I run Ubuntu in Vbox on my Office computer when I need it - this allows me to run a non-windows OS without breaking the IT rules...  No Compiz on that system, video card is too weak.

---

### Post by slowtrain on 2011-02-27
Hey Hedge:  I've had good experiences w/ Nvidia as well.  Will have to stick to that.  I wonder what will happen once the new i7-2600's start real mass production.  They're supposed to have decent on board graphics.

Am experimenting now w/ Debian to see if it really is more stable than Ubuntu.  Doesn't fix the hibernate / suspend issues, but it doesn't crash (just doesn't work)--which is a big plus because Ubuntu has been busy corrupting config files (at least) like this.  As far as I can tell, Debian is basically the same thing as Ubuntu, basically, just more solid.  A lot of rather annoying bugs in Maverick that I've had to work around just don't occur in Debian.

I've also tried, from USB drive only (live), OpenSUSE.  Just checking to see if I could suspend or hibernate.  Absolutely nothing happens when I try that.  Makes me wonder if there was something I needed to do to enable suspend / hibernate.  But, as I was trying to read up online about whether there is some special trick, OpenSUSE just froze.  If the live usb is any indication of the stability of OpenSUSE more generally, I think I'll have to avoid it.

My impression from reading more widely on the net about different flavor of Linux is that they all have problems with suspend / hibernate.  Ultimately, they seem to depend on more or less the same kernels, so maybe not a surprise.  I wonder why there are such widespread issues.  Maybe hardware vendors aren't providing the necessary info. to linux developers.  If so, I wonder if that's a quid-quo-pro with Microsoft.

Cheers!

---

### Post by Hedgehog1 on 2011-02-27
I am very pleased that you are experimenting and researching BEFORE loading.  It is a sign of an organized mind.

We ***hedgies ***prefer that...

> **slowtrain said:**
> 
Am experimenting now w/ Debian to see if it really is more stable than Ubuntu.  Doesn't fix the hibernate / suspend issues, but it doesn't crash (just doesn't work)--which is a big plus because Ubuntu has been busy corrupting config files (at least) like this.  As far as I can tell, Debian is basically the same thing as Ubuntu, basically, just more solid.  A lot of rather annoying bugs in Maverick that I've had to work around just don't occur in Debian.


Whatever Linux distro works for you is OK by me.  If you end up in OSX or Windows 7, that is OK too.  I use everything but OSX - and that is because I cannot justify the 5 grand for the 12 Core Mac Pro! (but I really WANT one!!!)

> **slowtrain said:**
> 
My impression from reading more widely on the net about different flavor of Linux is that they all have problems with suspend / hibernate.  Ultimately, they seem to depend on more or less the same kernels, so maybe not a surprise.  I wonder why there are such widespread issues.  Maybe hardware vendors aren't providing the necessary info. to linux developers.  If so, I wonder if that's a quid-quo-pro with Microsoft.


In all honestly, many Windows PC's suspend & hibernate modes really didn't work very well for the first few years it was offered.  It was not until the two Win7 laptops we have now that it has been dependable for us - and I still don't use it out of habit.

Ubuntu boots so quick that suspend & hibernate seems almost silly to me, but that is really personal taste.  My wife likes the functionality.  She is always right, so it must be good.

:KS

---

### Post by slowtrain on 2011-02-28
> **Hedgehog1 said:**
> 
Ubuntu boots so quick that suspend & hibernate seems almost silly to me, but that is really personal taste.  My wife likes the functionality.  She is always right, so it must be good.

:KS

Huh!  My wife too!  

I was thinking about the quick boot, but that doesn't seem yet at the point where I can use the machine as I would like.  I work usually with a *lot* of stuff open--nature of the work I do.  While some of that will open again with the Linux 'save session' capacity, there seem to be a few limitations:  a) at least in 9.10 materials would generally open in random workspaces, not the one in which they originally were, b) some things that I work with extensively, like JGR and jedit, don't open at all, c) OpenOffice restarts by trying to recover files that were freshly saved when I shut down and on recovery does not send them to the right workspaces.  Can take a while for me to get back to exactly where I was (if I can remember).  Haven't really systematically sought to determine how much of a struggle it'll be with Maverick.  It does look like material is being sent to the right workspaces at least.  I suspect, though, that b and c are still an issue.  If the suspend / hibernate issues will take time to address, I wonder if linux developers can find some way to reconstitute exactly what is on the desktop at shutdown and without OpenOffice 'recovery'?

There's also the fact that, esp. when working at home, I am frequently called away from my computer for 5-10 minutes, though sometimes what I think will that 5 minutes will turn into 30-60 minutes.  So, suspend would be helpful.

But, maybe I'm being overly particular here.  Thanks for the perspective on suspend / hibernate being a problem with windows as well, initially.  One thing I found odd in Ubuntu is that suspend / hibernate worked perfectly in 8.10 on my old home computer but then started with periodic system freezes in 9.04 through 10.10.  Odd that a capability would regress like that.

---

### Post by slowtrain on 2011-03-02
Say, does anyone have any thoughts on whether, if my main use of Windows will simply be to house a Virtualbox version of Ubuntu, I should get Windows Pro or can settle for Windows Home Edition?  Kind of hate to spend an extra $100 (or whatever) for a copy of Pro of Home will do.  On the other hand, my old Home edition was awful (one reason I moved to Ubuntu).  I wonder if there are performance limitations on the Home edition that would impact the Ubuntu in Virtuabox?

---

### Post by Hedgehog1 on 2011-03-02
> **slowtrain said:**
> Say, does anyone have any thoughts on whether, if my main use of Windows will simply be to house a Virtualbox version of Ubuntu, I should get Windows Pro or can settle for Windows Home Edition?  Kind of hate to spend an extra $100 (or whatever) for a copy of Pro of Home will do.  On the other hand, my old Home edition was awful (one reason I moved to Ubuntu).  I wonder if there are performance limitations on the Home edition that would impact the Ubuntu in Virtuabox?

If you are talking Windows 7 Home or PRO, there is not advantage to PRO.  There is a HUGE advantage to 64 bit windows over 32 bit windows as a host system.

Here is why:  When a guest OS runs, the 512k to 4 gig of memory given to it are taken over by the guest system and the host OS cannot use it.  I run 12 gigs of ram; both my Win7 and Ubuntu hosts are 64 bit.  This means I can give my Win 7 guest 4 gigs, and (running at the same time) my Mint guest OS 1 gig, and (running at the same time) my Fedora guest 2 gigs, and still have plenty for the Ubuntu host.

When Win7 is the host, it eats up 2-4 gig on it's own, then I need 1-4 gig for each guest OS I run simultaneously. 

If your host OS is 32 bit, it can access just under 4 gigs total.  That is all it can see.  So your options of large a guest OS in a 32 bit host OS are limited.

***The Hedge***

:KS

---

