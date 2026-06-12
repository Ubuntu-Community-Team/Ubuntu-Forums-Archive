---
title: "Could this kill linux gaming?"
date: 2006-12-13
forum: The Cafe
---

### Post by MetalMusicAddict on 2006-12-13
[http://lwn.net/Articles/213976/](http://lwn.net/Articles/213976/) 

[Linus's response.]("http://lkml.org/lkml/2006/12/13/370")

[Patch removed with apology. ]("http://lkml.org/lkml/2006/12/14/63")

---

### Post by maniacmusician on 2006-12-13
[facefault] ban binary modules? What will this mean for the world :-k this could have pretty huge consequences...unless I'm reading it wrong...

---

### Post by Polygon on 2006-12-14
are these kernel developers talking here? and if so, o damn. This can go one of two ways, all teh companies that just send out binary modules (aka video drivers) can comply and release gpl drivers, or it can go the other way and just stop producing drivers totally and we will be out of luck....

hope its the former

and also, it wont make it so that non gpl games cant be run, its talking about kernel modules, aka drivers... i believe

---

### Post by tribaal on 2006-12-14
Yes, but the action they intend to make is 
> ... spit out kernel log messages whenever such a module is loaded so
that people have some warning

I guess it's not really the end of linux gaming... except if you really pay close attention to your kernel log file.

That's how I understand it...

- trib'

---

### Post by drphilngood on 2006-12-14
> **tribaal said:**
> I guess it's not really the end of linux gaming... except if you really pay close attention to your kernel log file.

That's how I understand it...

- trib'

I hope you´re right...I can stand anything but laggy graphics.

---

### Post by MetalMusicAddict on 2006-12-14
> **tribaal said:**
> I guess it's not really the end of linux gaming... except if you really pay close attention to your kernel log file.'

"Give people 12 months warning (time to work out what they're going to do, talk with the legal dept, etc) then make the kernel load only GPL-tagged modules."

So in 12 months, if both sides dont find a solution, we're F'ed.

---

### Post by delfick on 2006-12-14
can someone clarify this for me?

if this goes the bad way, we won't have proprietary drivers ??

or am i misunderstanding as i so dearly hope i am :D ??

---

### Post by DoctorMO on 2006-12-14
There is a legal problem with the GPLed Linux Kernel, it says that you can't distrobute parts of the code in a propritory way. but to compile binary drivers you have to include GPL files (header files) and thus you taint your binary and can no longer legaly distrobute it without copyright infringement. no one has yet sued the makers of propritory drivers even if everyone agrees that it's not ok with the GPL.

What they're doing here is giving people and ultimatum. we don't want the kernel and other important parts of this secure system to be tained by hidden parts. either you play ball and let everyone see what it's done on my computer or you bog off.

Personaly I'd be sad if nVidia stoped producing updates to their binary drivers, but I'd be glad in a way because the free version would get quite a lot of support after the initial set back. and it wouldn't be the end of the world, just the start of a diferent one.

---

### Post by MetalMusicAddict on 2006-12-14
> **DoctorMO said:**
> it wouldn't be the end of the world, just the start of a diferent one.

Yes, but in the time it takes this new world to emerge it could kill projects that need a fanbase/community that needs full use of their cards.

I dont think this will be a good thing. There needs to be a middle ground.

---

### Post by DoctorMO on 2006-12-14
unfortunatly middle ground in this case is not possible. we may suffer initialy but the correction will save us a lot of grief later on.

Do you want us to suffer so in the future so you can play your games now? I don't think the wait will be very long. worse care sanario is that RH, Novell, Conical and a bunch of others have to put lots of their programmers on the foss driver.

---

### Post by yabbadabbadont on 2006-12-14
The kernel already spits out a message when it is tainted by a binary blob.  Futhermore, since this is OSS, any changes they make to the kernel to prevent non-gpl modules from being loaded, will simply be removed by a patch set that will soon follow those changes.

---

### Post by tuxcantfly on 2006-12-14
Hmm... could this mean problems for the feisty composite-by-default roadmap?

---

### Post by DoctorMO on 2006-12-14
yabbadabbadont, I bet it's annoying having to do that for every release. why can't these companies just play fair; we don't need to defend their actions.

---

### Post by yabbadabbadont on 2006-12-14
> **DoctorMO said:**
> yabbadabbadont, I bet it's annoying having to do that for every release. why can't these companies just play fair; we don't need to defend their actions.

It won't be the companies creating the patch sets...  All sorts of distributions apply their own custom set of patches to the kernels they deploy.  I've lost count of the number of different kernel patch sets that are actively maintained in the Gentoo world.  If the kernel devs really changed things such that the kernel couldn't be made to work with non-gpl modules, then I'm sure someone will simply fork it from the last version that did allow them.  Failing that, it would probably mean that the various BSD's would get a large influx of users.  ;)

---

### Post by po0f on 2006-12-14
[quote=yabbadabbadont]... Failing that, it would probably mean that the various BSD's would get a large influx of users.[/quote]

Not to be fatalistic or anything, but I am already dual-booting Ubuntu and FreeBSD, just in case.  ;)

---

### Post by yabbadabbadont on 2006-12-14
> **po0f said:**
> Not to be fatalistic or anything, but I am already dual-booting Ubuntu and FreeBSD, just in case.  ;)

How do you like FreeBSD?  I tried it a while back, but ended up back with Gentoo.  I haven't tried any of the recent releases.

---

### Post by po0f on 2006-12-14
yabbadabbadont,

Beyond getting it booted, I really haven't played with it much (Linux ain't dead just yet.)  But it is definitely different.  (WTF is a slice?)  :)

[EDIT]

I know what a slice is now, just commenting on the installation process.

---

### Post by DoctorMO on 2006-12-14
*shrug* what ever floats you boat in this case. at least the kernel devs are doing the right thing and you shouldn't critisise someone for standing up for what they believe in.

obviously and saddly most people I've found are shallow and will jump to anything so long as it works now.

---

### Post by po0f on 2006-12-14
DoctorMO,

Right now, Linux floats my boat.  :P  And where did I criticize anyone for what they believe in?  Please point it out to me; it is late, and I have bad eyesight.

I am glad that the kernel devs (or whoever) are making a push for this.  I would *love* open source drivers for my video card.  But I did not pay $150 for a piece of silicon that can only render a 1024x768 desktop, with no 3D acceleration whatsoever.  I guess we'll see how it all pans out.

---

### Post by MetalMusicAddict on 2006-12-14
> **DoctorMO said:**
> obviously and saddly most people I've found are shallow and will jump to anything so long as it works now.

Thing is, if this were 2 years or so it would have been better timing. I think "now" is desktop linux's time. Ubuntu has dont wonders for that.

I just dont see the open GFX drivers being as good (thats what I want. equal) as the binary ones in the short term. I worry about the long term as well.

This will have a _major_ impact on linux gaming. People like me who buy the latest cards and run linux. I have a 7900GT. If the new cards dont work linux gamers wont buy em and our market becomes even smaller. 

What about apps like Blender?

I just prey a miracle happens in the next 12 months.

---

### Post by DoctorMO on 2006-12-14
I agree it is bad timing and it should have been done directly. but I can't help feeling that a sense of pragmatism has lead up into this trouble.

> Please point it out to me; it is late, and I have bad eyesight.

I inffered it, it's quite late here too, sorry for jumping to conclusions.

> I just prey a miracle happens in the next 12 months.

I hope so too.

---

### Post by yabbadabbadont on 2006-12-14
At least with Nvidia, my understanding from reading some of their releases, is that their cards make use of 3rd party technology, the patents to which they only have a license.  They either have to get all the 3rd parties to agree to open their technology, or redesign their cards to not use that tech.  (assuming that they even want to open their own tech up)  And since it is all hidden by NDA's, there isn't any way to tell how difficult either proposition would be.  Quite frankly, even though the Linux market is growing, it is still a tiny portion of their market share.  If they are slapped with an ultimatum, I'm sure no one will be surprised if they just stop providing drivers.

---

### Post by delfick on 2006-12-14
i like linus' take on this [http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824](http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824) :D

(i found the link to that over here [http://www.osnews.com/story.php?news_id=16720](http://www.osnews.com/story.php?news_id=16720))

....

so if we can't have proprietary drivers, then we can't use beryl or compiz.....that would suck so bad it's not funny....

---

### Post by po0f on 2006-12-14
I'm glad to see that [this](http://wiki.duskglow.com/tiki-index.php?page=Open-Graphics) project isn't dead yet.

---

### Post by maniacmusician on 2006-12-14
well the saddest thing is, commercial companies will never release open source drivers, only binaries. On top of that, we will never be able to develop competent open source drivers that rival the binary ones in a succesful and legal fashion. In addition, any open source clean-room reverse engineering that happens will take so long that newer devices will be released and older drivers will start becoming inconsequential. 

Like it or not, the hardware manufacturers _have_ to be the source of our drivers, because they're the only ones that have the hardware specs. No other solution is feasible, and never will be, until the world finds a way to make money off of open source hardware architecture. And that's pretty much the final word on the whole thing. That is our situation, and face it, it's not going to change. And with the loss of binary drivers, we will have loss of projects like Beryl, and cool 3D games, which can be substantial in luring over a larger user base. 

Alienating the user base by banning binary drivers will solve nothing except having them depart for other alternatives.

---

### Post by DoctorMO on 2006-12-14
We can still use them and condemn them for being wrong. ok so we look like idiots but at least we're not only thinking about what we gain for our machines.

I don't think that the free drivers should be put aside too easily. you are correct that new hardware will come out, but the more code is available and written for the older cards the more specification we have to work with. do you think they rewrite the entire nvidia stack with each new card? I don't think so. being as fast, I don't think they'll be as fast. but at least they'll be more secure.

---

### Post by firenewt on 2006-12-14
No one is forced to install these drivers. No one. Keep your system secure and don't install them. Let those who want to use them do so.

---

### Post by 23meg on 2006-12-14
[QUOTE=maniacmusician]commercial companies will never release open source drivers, only binaries. [/QUOTE]Intel does release open source drivers.

---

### Post by OffHand on 2006-12-14
I'm not native English so I do not fully understand what they are saying... Are they saying they will make it impossible to use binary drivers at all?

---

### Post by kanem on 2006-12-14
> **23meg said:**
> Intel does release open source drivers.

Ha! I was just about to mention this. And they're getting better all the time. My next card is definitely going to be one of their new 3D ones.

No more [spending way too much](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) time [effing around with](http://www.ubuntuforums.org/showthread.php?t=273934&highlight=ati+mesa) around with [manually downloaded](http://www.ubuntuforums.org/showthread.php?t=300336&highlight=ati+mesa) drivers.

---

### Post by macogw on 2006-12-14
> **delfick said:**
> i like linus' take on this [http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824](http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824) :D

(i found the link to that over here [http://www.osnews.com/story.php?news_id=16720](http://www.osnews.com/story.php?news_id=16720))

....

so if we can't have proprietary drivers, then we can't use beryl or compiz.....that would suck so bad it's not funny....

Agreed.  Drivers tell exactly how the piece of hardware works.  Remember, pay for hardware, not for software.  nVidia and ATI have to worry about each other finding out how the other's cards work so they can copy them.  Therefore, they hide the "how to" for the card from their competition.  That's it. If you don't want the kernel to have any binary blobs in it, FINE!  Agreed.  If you want to add them to your pure kernel, FINE! Agreed.  Keep the binary blobs out of the plain kernel, let users add them themselves though.  We want control over our computers.  Don't prevent nVidia users from using their cards properly.

---

### Post by drphilngood on 2006-12-14
> **kanem said:**
> Ha! I was just about to mention this. And they're getting better all the time. My next card is definitely going to be one of their new 3D ones.

No more [spending way too much](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) time [effing around with](http://www.ubuntuforums.org/showthread.php?t=273934&highlight=ati+mesa) around with [manually downloaded](http://www.ubuntuforums.org/showthread.php?t=300336&highlight=ati+mesa) drivers.

I had totally forgotten that we had this option.  If their next generation of GPUs are just _as good_ as my current nVidia, I think my next GPU will be Intel, also.

---

### Post by OffHand on 2006-12-14
I have just read the mailing list and it looks like Linus thinks it is a horrible idea. I totally agree with him.

---

### Post by kripkenstein on 2006-12-14
This will not prevent binary drivers.

1. A distro can simply remove the code that prevents GPL-only drivers from running. This is legal and easy.

2. A binary driver can work like the NVidia driver already does - a binary driver, and a small wrapper ("shim") that IS actually GPL, and only it is loaded by the kernel. (Linus refers more or less to this in the link given before in this thread)

All that this can do is make using binary drivers a little harder, and to force distros to make a choice - i.e. to actually remove the code from the kernel. This might be a good thing, if it raises the issue into debate.

---

### Post by darkninja on 2006-12-14
I think it's pretty pathetic that Linux has come to the point where it is mostly useless without GPL-infringing (but tolerated) binary drivers.

This is exactly what Theo de Raadt and RMS have been warning us about, that if we allow binary blobs we will grow weak and reliant, and become enslaved to ATi/Nvidia/Intel/whoever.

How long has it taken for the graphic card manufacturers to support what we need for AIGLX? How many times has the monthly FGLRX broken our systems? Why can't be have Intel wireless out of the box in more free distros then Ubuntu? Why is X.Org development so slow?

I don't blame the kernel developers for getting pissed off when the closed source drivers break stuff, and I do agree with the idea of having a final deadline to remove all closed source drivers, though one year is far too soon.

I'd wish they'd agree to three or so years and have a proper structured strategy to phase out binary drivers with free alternatives during that period instead of violently ripping them out without substitutes.

If we sacrifice the core values of Linux now for the sake of convenience, I guarantee we will pay the price for it in the future.

---

### Post by 23meg on 2006-12-14
[QUOTE=kripkenstein]
2. A binary driver can work like the NVidia driver already does - a binary driver, and a small wrapper ("shim") that IS actually GPL, and only it is loaded by the kernel. (Linus refers more or less to this in the link given before in this thread)[/QUOTE]Sure, the nvidia kernel module is open source. It's the X module that's proprietary.

---

### Post by kanem on 2006-12-14
From reading the thread where this was proposed it's pretty clear that this is as much a practical decision as anything. As darkninja said above me, the kernel devs are tired of these binary blobs doing stupid shite in their kernel and breaking stuff every month.

Oh look, more [X breakage](http://ubuntuforums.org/showthread.php?t=318206) today involving closed source drivers. Quelle surprise.

---

### Post by OffHand on 2006-12-14
> **kanem said:**
> From reading the thread where this was proposed it's pretty clear that this is as much a practical decision as anything. As darkninja said above me, the kernel devs are tired of these binary blobs doing stupid shite in their kernel and breaking stuff every month.

Oh look, more [X breakage](http://ubuntuforums.org/showthread.php?t=318206) today involving closed source drivers. Quelle surprise.

I don't care. It's my choice to use them or not. I do not want the Linux kernel stop me from using binaries if I want to.

---

### Post by kanem on 2006-12-14
> **OffHand said:**
> I don't care. It's my choice to use them or not. I do not want the Linux kernel stop me from using binaries if I want to.
That's fine. But you don't have the right to tell the kernel devs how they should code. And if they are sick of putting up with binary blobs, then it's their prerogative to not allow them.

---

### Post by OffHand on 2006-12-14
> **kanem said:**
> That's fine. But you don't have the right to tell the kernel devs how they should code. And if they are sick of putting up with binary blobs, then it's their prerogative to not allow them.

I sure do have the right to vent my opinion. Besides that... if they are sick of it they should offer a replacement imo.

---

### Post by argie on 2006-12-14
I don't see how binary blobs would affect the kernel devs. Maybe I don't understand the way it works, but why do they have to "put up with" these drivers? Aren't they outside the whole code, so the kernel devs just keep coding the kernel and leave it to the hardware manufacturers to catch up.

---

### Post by kanem on 2006-12-14
> **argie said:**
> I don't see how binary blobs would affect the kernel devs. Maybe I don't understand the way it works, but why do they have to "put up with" these drivers? Aren't they outside the whole code, so the kernel devs just keep coding the kernel and leave it to the hardware manufacturers to catch up.

I'm no dev, so I don't fully understand either, but [here's](http://thread.gmane.org/gmane.linux.kernel/475654/focus=475695) the thread in which banning the blobs is proposed. The actual proposition doesn't come until a few posts after the one I've linked to.  Before that the discussion is on how to get around a problem that is apparently exacerbated by these drivers. Here's a choice quote:

[quote=ban the blob thread]
>> Embedded systems integrators have enough trouble with chip vendors who
>> think that exposing the device registers to userspace constitutes a
>> "driver".
> 
> Yes, and because of this, they create binary only drivers today.  Lots
> of them.  All over the place.  Doing crazy stupid crap in kernelspace.

So let's come out and ban binary modules, rather than pussyfooting
around, if that's what we actually want to do.[/quote]

Doesn't sound to me like this is just a philisophical decision.

---

### Post by 23meg on 2006-12-14
> **kanem said:**
> 
Doesn't sound to me like this is just a philisophical decision.
It seems to have sprung out of an entirely technical discussion. Note Linus' first reply to the original post.

Anyway, I don't think there's much use in debating this any further; it almost certainly won't happen in mainline. It's notable though that someone as credible and under as much responsibility of the kernel as Andrew Morton is supporting it, and that his view is in total conflict with that of Linus.

---

### Post by PriceChild on 2006-12-14
Even if it were patched.... surely it'd be just as easy to unpatch it?

Its not as if the code change would be hidden?

---

### Post by prizrak on 2006-12-14
Forget video, some of the wi-fi drivers are binary in many parts. If the nv driver while crappy will give you a 2D desktop and all the stuff that doesn't require 3D (at which point there will be no way I'm gonna bother with Linux) an Atheros driver not being installed or working is a much bigger issue.

---

### Post by darrenm on 2006-12-14
You know, I'd be happy to be forced to use only hardware with open specs or open-source drivers.

In the end it would mean all the Linux people would go to the "open" manufacturers who would then do really well out of it.

---

### Post by PriceChild on 2006-12-14
I love ralink :) - open sourced goodness.

---

### Post by Klaidas on 2006-12-14
>  Could this kill linux gaming?
Hmm... was it ever alive?

---

### Post by ZylGadis on 2006-12-14
So finally the kernel devs have decided to do the right thing. And - surprise, surprise - it is none other than Torvalds himself that is getting in their way.
Is it odd that he first announced a firm stance against GPL3 (and convinced most kernel devs that his stance was right), and now this? I don't think so. After all, Torvalds is the holder of the "Linux" trademark. **He has commercial interest in that, unlike all the pure FLOSS ideologists**.
I have followed his announcements for quite some time now, and his opposition to this finally tips the point. I think it is already clear that Torvalds is working for Linux to become as widespread as possible at any cost - **including the cost of Linux becoming non-free**.
I do think a lot of people will be moving over to BSD-based distros (or Hurd - that would be perfect if it only worked in a meaningful way), but for a different reason than lack of 3D shooters in linux.

To the guys who said that it's open-source so anyone can remove the patch that disables binary blobs: true, anyone can remove it. But that person would be **breaking the law** if s/he then proceeds to put a binary driver. The GPL is clear that no binary blobs should be allowed; the fact that the kernel devs have not chosen to enforce the GPL for so long does not mean they can't do it now. Andrew Morton, at least, looks determined.

---

### Post by tbroderick on 2006-12-14
> **ZylGadis said:**
>  But that person would be **breaking the law** if s/he then proceeds to put a binary driver. 

I was under the impression that only distributing it would violate the GPL. If the end user wants to add non-GPL drivers, I don't see how he/she would be breaking the law.

---

### Post by ZylGadis on 2006-12-14
That is true. I was talking about distributions (cough..feisty..cough) and their maintainers. Thanks for clarifying that.

---

### Post by PatrickMay16 on 2006-12-14
I'm glad for binary drivers. At least we get some support for hardware, which is a lot better than nothing at all.

---

### Post by MetalMusicAddict on 2006-12-14
> **PatrickMay16 said:**
> I'm glad for binary drivers. At least we get some support for hardware, which is a lot better than nothing at all.

And better than the open ones in some cases.

---

### Post by Peti29 on 2006-12-14
I'm a noob I know hardly anyting of Linux. But I think it's hightime to tempt a lot of users from Windows to Linux. And that because many don't want to go the Vista way. At least M$'s dictatorial rights protection was the main reason I turned to Ubuntu. I had nothing against Windows XP: it works and it's stable!
I don't use Linux for philosophical reasons. I use it cause it's free and it's good, and because I don't want to use Vista.
But come on, an operating system uncapable of (hardware accelerated) 3D? NO WAY!
If the 12 months had been already over and I had to choose wether to switch to 3D-impotent Linux or not, probably I'd have just sticked with XP as far as I could.

I don't fully understand why is it important to grow the Linux user base (as the product is free), but if you intend to do that, killing 3D support is just NOT AN OPTION!

---

### Post by OffHand on 2006-12-14
> **ZylGadis said:**
> So finally the kernel devs have decided to do the right thing. And - surprise, surprise - it is none other than Torvalds himself that is getting in their way.
Is it odd that he first announced a firm stance against GPL3 (and convinced most kernel devs that his stance was right), and now this? I don't think so. After all, Torvalds is the holder of the "Linux" trademark. **He has commercial interest in that, unlike all the pure FLOSS ideologists**.
I have followed his announcements for quite some time now, and his opposition to this finally tips the point. I think it is already clear that Torvalds is working for Linux to become as widespread as possible at any cost - **including the cost of Linux becoming non-free**.
I do think a lot of people will be moving over to BSD-based distros (or Hurd - that would be perfect if it only worked in a meaningful way), but for a different reason than lack of 3D shooters in linux.

To the guys who said that it's open-source so anyone can remove the patch that disables binary blobs: true, anyone can remove it. But that person would be **breaking the law** if s/he then proceeds to put a binary driver. The GPL is clear that no binary blobs should be allowed; the fact that the kernel devs have not chosen to enforce the GPL for so long does not mean they can't do it now. Andrew Morton, at least, looks determined.
That is total nonsense.

---

### Post by MetalMusicAddict on 2006-12-14
> **OffHand said:**
> That is total nonsense.

I think its more bad timing. 2-3 years from now, this should be worked out. Im worried about the short-term because it can be as important as the long term.

Sometimes, its all about timing.

---

### Post by OffHand on 2006-12-14
> **MetalMusicAddict said:**
> I think its more bad timing. 2-3 years from now, this should be worked out. Im worried about the short-term because it can be as important as the long term.

Sometimes, its all about timing.

I was referring to a couple of (false) statements he made. I agree that timing is an issue though. Sometimes I think the devs need a reality check.

---

### Post by MetalMusicAddict on 2006-12-14
I see. ;)

---

### Post by imagine on 2006-12-14
> **darkninja said:**
> I think it's pretty pathetic that Linux has come to the point where it is mostly useless without GPL-infringing (but tolerated) binary drivers.

This is exactly what Theo de Raadt and RMS have been warning us about, that if we allow binary blobs we will grow weak and reliant, and become enslaved to ATi/Nvidia/Intel/whoever.
[...]
If we sacrifice the core values of Linux now for the sake of convenience, I guarantee we will pay the price for it in the future.
Very well written.
Some users only see the short term consequences: Install eg the proprietary nvidia driver and have some 3D functionality. Don't install it - no 3D functionality.
But how did it come to this situation? How are we so dependent of proprietary drivers and thereby of the goodwill of a company? Already now such a proprietary grahpics driver only works with certain kernel versions, only works with a certain X server version, only works on certain platforms. It's not difficult to imagine that in the future the driver might also only work with patchsets used by certain major distributions, etc. See Arjans article _[Linux in a binary world](http://lwn.net/Articles/162686/)_ for more ideas.

In the long term, accepting proprietary drivers can and will do a lot of damage to Linux. Not only do both users and developers become reliant on some corporations, but its also a wrong signal to companies that already make free drivers available: Why should they continue to give out specifications or source code, when obviously other companies get away with binary-only drivers.
In the end accepting proprietary drivers is a special kind of _[BinaryDriverEducation](https://wiki.ubuntu.com/BinaryDriverEducation)_, just the wrong way round: It teaches people that proprietary drivers are perfectly fine. In this regard I also see the plans to release Ubuntu 7.04 _[together with proprietary graphics drivers](https://wiki.ubuntu.com/AcceleratedX/Comments)_ as highly problematic. This certianly _[won't last for a long time](http://kororaa.org/static.php?page=gpl)_, but probably long enough to damage the free software ecosystem and strengthen the position of AMD, Nvidia and their proprietary drivers.

---

### Post by Hendrixski on 2006-12-14
Why is Torvalds against GPL3?  Does he think it goes too far to an idealogical extreme?

What does Eric Raymond have to say about this?  (I'd ask about Stallman's oppinion, but that doesn't seem to count anymore).

---

### Post by darrenm on 2006-12-14
Thing is, you are assuming that the big companies are not opening their drivers or specs out of spite. If anyone saw the ATi / NV source code from outside then they would suddenly have a whole lot of patent issues to deal with. So the gamble won't work and there will be a stalemate with the only loser being widespread adoption of Linux. At the moment it is the lesser of 2 evils unfortunately. When the Linux user base has more buying power then we can pull the rug from under the feet of the HW manufacturers but not yet we can't.

---

### Post by darrenm on 2006-12-14
> **Hendrixski said:**
> Why is Torvalds against GPL3?  Does he think it goes too far to an idealogical extreme?

What does Eric Raymond have to say about this?  (I'd ask about Stallman's oppinion, but that doesn't seem to count anymore).

I used to value RMS' opinion until I read that he said this was ok:
[http://dansguardian.org/?page=copyright2](http://dansguardian.org/?page=copyright2) which doesn't comply with the GPL

---

### Post by MetalMusicAddict on 2006-12-14
> **imagine said:**
> Very well written.
Some users only see the short term consequences: Install eg the proprietary nvidia driver and have some 3D functionality. Don't install it - no 3D functionality.
But how did it come to this situation? How are we so dependent of proprietary drivers and thereby of the goodwill of a company? Already now such a proprietary grahpics driver only works with certain kernel versions, only works with a certain X server version, only works on certain platforms. It's not difficult to imagine that in the future the driver might also only work with patchsets used by certain major distributions, etc. See Arjans article _[Linux in a binary world](http://lwn.net/Articles/162686/)_ for more ideas.

In the long term, accepting proprietary drivers can and will do a lot of damage to Linux. Not only do both users and developers become reliant on some corporations, but its also a wrong signal to companies that already make free drivers available: Why should they continue to give out specifications or source code, when obviously other companies get away with binary-only drivers.
In the end accepting proprietary drivers is a special kind of _[BinaryDriverEducation](https://wiki.ubuntu.com/BinaryDriverEducation)_, just the wrong way round: It teaches people that proprietary drivers are perfectly fine. In this regard I also see the plans to release Ubuntu 7.04 _[together with proprietary graphics drivers](https://wiki.ubuntu.com/AcceleratedX/Comments)_ as highly problematic. This certianly _[won't last for a long time](http://kororaa.org/static.php?page=gpl)_, but probably long enough to damage the free software ecosystem and strengthen the position of AMD, Nvidia and their proprietary drivers.

To me, this is a "my way or the highway" approach. Its the same one we're used to from big business. We will need to work together. RMS's nor Balmer's view will will out.

"short term consequences" <- This is still important. Dont think its not.

Think about everything going on now. Ubuntu has done AMAZING things for GNU/Linux. People are finding they dont want to go to Vista and are looking at GNU/Linux because their computer can be fully functional under GNU/Linux. If you take away those drivers ie: GFX, WIFI people will not switch to GNU/Linux.

Like I said earlier in the thread "Timing can be everything".

---

### Post by Hendrixski on 2006-12-14
> So the gamble won't work and there will be a stalemate with the only loser being widespread adoption of Linux. At the moment it is the lesser of 2 evils unfortunately. When the Linux user base has more buying power then we can pull the rug from under the feet of the HW manufacturers but not yet we can't.

That sums it up really well.  We don't have the political power to convince the big companies that "well, we don't really need to make money on this stuff anyway, let's give away our trade secrets".  It's almost a necessary evil.

But again, what do people that matter have to say about, like Torvalds and Raymond?

> People are finding they dont want to go to Vista and are looking at GNU/Linux because their computer can be fully functional under GNU/Linux. If you take away those drivers ie: GFX, WIFI.
Well said.  This is the true cost of idealism.  Just like Iraq was the true cost of idealism (the necons who believed, they honestly believed, "we'd be greeted as liberators" and spread democracy to start a period of peace to be known as a "pax americana"... they were idealists too.  now the world pays the cost for idealist BS).  Be a pragmatist, use binary drivers if you need to, don't use them if you don't need to.

---

### Post by MetalMusicAddict on 2006-12-14
Also dont get me wrong, Im all for open software/drivers whatever. I just believe there should be better cooperation, not just black and white.

For me, I have a nVidia 7900GT card and a Dell 24" WS LCD. The nv drivers are shite for this setup. Heres hoping the "nouveau" project does well or Intel comes out with a KILLER open card.

---

### Post by prizrak on 2006-12-14
> **darrenm said:**
> You know, I'd be happy to be forced to use only hardware with open specs or open-source drivers.

In the end it would mean all the Linux people would go to the "open" manufacturers who would then do really well out of it.

You could be happy about it but some of us have hardware that is best for what we do and if it doesn't work under a certain OS we won't use it. I won't use an integrated Intel video card because while I game occasionally I need to work on those occasions. Or in the case of my laptop everything works under Linux except for Bluetooth which is a Broadcom based one. No way to get that info from the manufacturer's site and nothing on Google about my laptop's compatibility/incompatibility with Ubuntu/Linux at least not about bluetooth. Again I don't use it much but when I do use it, it has to work. We can't always check the hardware we get to make sure it's Linux friendly and in some cases binary drivers will be required (Atheros for instance).

---

### Post by darrenm on 2006-12-14
> **prizrak said:**
> You could be happy about it but some of us have hardware that is best for what we do and if it doesn't work under a certain OS we won't use it. I won't use an integrated Intel video card because while I game occasionally I need to work on those occasions. Or in the case of my laptop everything works under Linux except for Bluetooth which is a Broadcom based one. No way to get that info from the manufacturer's site and nothing on Google about my laptop's compatibility/incompatibility with Ubuntu/Linux at least not about bluetooth. Again I don't use it much but when I do use it, it has to work. We can't always check the hardware we get to make sure it's Linux friendly and in some cases binary drivers will be required (Atheros for instance).

Yes I agree with what you said there. My first reply was a little idealistic and wasn't fully thought through.

---

### Post by Hendrixski on 2006-12-14
Slightly off topic, but Darren, I LOVE your signature
>  Ubuntu is the beginning of the end for Microsoft
let's hope driver-wars won't be the begining of the end of linux.

---

### Post by OffHand on 2006-12-14
> **Hendrixski said:**
> Be a pragmatist, use binary drivers if you need to, don't use them if you don't need to.
Exactly, I do not need some FSF hippie decide for me what I can and cannot use. And if they decide to go through with this plan, Linux can kiss his *** goodbye... well, only the terminal junkies will continue using it just like the situation was 10 years ago.

This is the way Linus feels about this issue:

> 
> Numerous kernel developers feel that loading non-GPL drivers into the
> kernel violates the license of the kernel and their copyright.  Because
> of this, a one year notice for everyone to address any non-GPL
> compatible modules has been set.

Btw, I really think this is shortsighted.

It will only result in _exactly_ the crap we were just trying to avoid, 
namely stupid "shell game" drivers that don't actually help anything at 
all, and move code into user space instead.

What was the point again?

Was the point to alienate people by showing how we're less about the 
technology than about licenses?

Was the point to show that we think we can extend our reach past derived 
work boundaries by just saying so? 

The silly thing is, the people who tend to push most for this are the 
exact SAME people who say that the RIAA etc should not be able to tell 
people what to do with the music copyrights that they own, and that the 
DMCA is bad because it puts technical limits over the rights expressly 
granted by copyright law.

Doesn't anybody else see that as being hypocritical?

So it's ok when we do it, but bad when other people do it? Somehow I'm not 
surprised, but I still think it's sad how you guys are showing a marked 
two-facedness about this.

The fact is, the reason I don't think we should force the issue is very 
simple: copyright law is simply _better_off_ when you honor the admittedly 
gray issue of "derived work". It's gray. It's not black-and-white. But 
being gray is _good_. Putting artificial black-and-white technical 
counter-measures is actually bad. It's bad when the RIAA does it, it's bad 
when anybody else does it.

If a module arguably isn't a derived work, we simply shouldn't try to say 
that its authors have to conform to our worldview.

We should make decisions on TECHNICAL MERIT. And this one is clearly being 
pushed on anything but.

I happen to believe that there shouldn't be technical measures that keep 
me from watching my DVD or listening to my music on whatever device I damn 
well please. Fair use, man. But it should go the other way too: we should 
not try to assert _our_ copyright rules on other peoples code that wasn't 
derived from ours, or assert _our_ technical measures that keep people 
from combining things their way.

If people take our code, they'd better behave according to our rules. But 
we shouldn't have to behave according to the RIAA rules just because we 
_listen_ to their music. Similarly, nobody should be forced to behave 
according to our rules just because they _use_ our system. 

There's a big difference between "copy" and "use". It's exatcly the same 
issue whether it's music or code. You can't re-distribute other peoples 
music (becuase it's _their_ copyright), but they shouldn't put limits on 
how you personally _use_ it (because it's _your_ life).

Same goes for code. Copyright is about _distribution_, not about use. We 
shouldn't limit how people use the code.

Oh, well. I realize nobody is likely going to listen to me, and everybody 
has their opinion set in stone. 

That said, I'm going to suggest that you people talk to your COMPANY 
LAWYERS on this, and I'm personally not going to merge that particular 
code unless you can convince the people you work for to merge it first.

In other words, you guys know my stance. I'll not fight the combined 
opinion of other kernel developers, but I sure as hell won't be the first 
to merge this, and I sure as hell won't have _my_ tree be the one that 
causes this to happen.

So go get it merged in the Ubuntu, (Open)SuSE and RHEL and Fedora trees 
first. This is not something where we use my tree as a way to get it to 
other trees. This is something where the push had better come from the 
other direction.

Because I think it's stupid. So use somebody else than me to push your 
political agendas, please.

		Linus


---

### Post by MetalMusicAddict on 2006-12-14
[QUOTE=Linus]If people take our code, they'd better behave according to our rules. But
we shouldn't have to behave according to the RIAA rules just because we
_listen_ to their music.[/QUOTE]

I like this.

---

### Post by darrenm on 2006-12-14
> **Hendrixski said:**
> Slightly off topic, but Darren, I LOVE your signature

let's hope driver-wars won't be the begining of the end of linux.

Its kind of like the Matrix - all these Windows users need to be unplugged but don't realise it.

" I know you're out there. I can feel you now. I know that you're afraid. You're afraid of us. You're afraid of change. I don't know the future. I didn't come here to tell you how this is going to end. I came here to tell you how it's going to begin. I'm going to hang up this phone, and then I'm going to show these people what you don't want them to see. I'm going to show them a world... without you. A world without rules and controls. Without borders or boundaries. A world where anything is possible. Where we go from there, is a choice I leave to you."

OMG I've just realised the Matrix is actually about Linux vs Windows!!! The Wachowski brothers even show us that by Trinity using nmap on Linux...

---

### Post by Hendrixski on 2006-12-14
Wow.  See, there's a reason that Linus is the maintainer of the Kernel.  He is against his code forcing people to use it in one way or another.  That's just good software development.  Has nothing to do with idealogical pricks.  Good software does not confine or confuse its users.

I imagine that Eric Raymond must have a similar message.  If anyone can find it and post it here...

---

### Post by Hendrixski on 2006-12-14
> **darrenm said:**
> Its kind of like the Matrix - all these Windows users need to be unplugged but don't realise it.

" I know you're out there. I can feel you now. I know that you're afraid. You're afraid of us. You're afraid of change. I don't know the future. I didn't come here to tell you how this is going to end. I came here to tell you how it's going to begin. I'm going to hang up this phone, and then I'm going to show these people what you don't want them to see. I'm going to show them a world... without you. A world without rules and controls. Without borders or boundaries. A world where anything is possible. Where we go from there, is a choice I leave to you."

OMG I've just realised the Matrix is actually about Linux vs Windows!!! The Wachowski brothers even show us that by Trinity using nmap on Linux...

So the architect is Bill Gates 2 000 years from now, and the council of elders are the maintainers of the LINUX Kernel... what ever happens to HURD in the matrix anyway.

---

### Post by OffHand on 2006-12-14
> **Hendrixski said:**
> He is against his code forcing people to use it in one way or another.  That's just good software development.  Has nothing to do with idealogical pricks.  Good software does not confine or confuse its users.Correct me if I am wrong but if I remember correctly this is one of the main reasons Linus is against GPLv3 too. Linus is a pragmatist and he beliefs in true freedom. I like him.

---

### Post by Hendrixski on 2006-12-14
> **OffHand said:**
> Correct me if I am wrong but if I remember correctly this is one of the main reasons Linus is against GPLv3 too. Linus is a pragmatist and he beliefs in true freedom. I like him.

Sounds about right.  He speaks to software developers, as a developer so he's pragmatic.  I like it too.  Even though in person he's a prick.  Raymond talks more to the sociologists, and Stallman talks to the wishful thinkers.

But back to the issue.  If users are allowed to have a CHOICE then gaming will be alive and healthy in LINUX (even if it really is just a waste of time).  If we force the user to use the software the way that we as developers believe they should (because we'd all like to think that we know better and that the user is in fact stupid) then yes, it would be a problem for gaming in LINUX... beyond that, it would be a problem for all aspects of Linux.

---

### Post by Peti29 on 2006-12-14
> The silly thing is, the people who tend to push most for this are the
exact SAME people who say that the RIAA etc should not be able to tell
people what to do with the music copyrights that they own
Exactly what was on my mind. Why do you dev guys want to decide wether I can use my _own_ graphics card or not??
I flee from DRM in Vista now I bump into this crap in Linux?

---

### Post by BarfBag on 2006-12-14
I was going to start another topic on this, but decided not to.  This situation is confusing enough and multiple topics merged together would make it even worse.

I don't know much about GPL, the Linux kernel, etc.  The most I know is what I heard from [Revolution OS]("http://www.revolution-os.com/") (which, oddly enough, I saw for the first time minutes before I came across this topic).  Can someone please explain how this will be resolved?  Will it be resolved in the first place?  Is it possible that in twelve months, we'll be stuck with no 3D acceleration and a divided community?  Ease some of the concerns of the non-veterans!

Also, can someone explain what's going on with the kernel and GPL 3?  I tried Googling this, but only found articles written back in January-February.  Can't everyone just sit down and work everything out?

---

### Post by Hex_Mandos on 2006-12-14
I'm with Linus.  I'm a political idealist, but a technical pragmatist. I USE my computer to do things. To me, an OS is a means to an end, not a toy to play with. That's why I use a distro that Just Works. If binary drivers will bring more people to Linux, that's fine. Once Linux has a larger market share, we can push the hardware developers to release free drivers. They wouldn't want to ostracize, say, 20% of the market. But right now we're not in a position to make any demands. They wouldn't lose much if they stopped selling their hardware to us.

Instead, if we bring more users to Linux (with binary drivers and even optional proprietary apps and plugins which are easy to install, if necessary) in a few years we'll be able to pressure the hardware manufacturers. Of course, hardcore FLOSSers can have their own GPL-only distros, and I commend them. It's just that I don't see how Linux can grow if we keep telling people that they can't use hardware acceleration, use wireless devices, listen to their music in mp3 or watch stuff made in Flash because of philosophical differences with them. Imagine how ridiculous it'd be if M$ banned any FLOSS application on Microsoft, because they have an ideological disagreement with it!

Anyway, the Linux is free, right? It can always be forked to allow binary drivers again if the FLOSS Fundies take over.

---

### Post by Saist on 2006-12-14
> **drphilngood said:**
> I had totally forgotten that we had this option.  If their next generation of GPUs are just _as good_ as my current nVidia, I think my next GPU will be Intel, also.

[http://zerias.blogspot.com/2006/12/firefly-mmo-flop-in-progres-or-intel.html](http://zerias.blogspot.com/2006/12/firefly-mmo-flop-in-progres-or-intel.html)

I saw this and figured I might as well link my own blog posting about Intel's graphics cards. Do you really think that Intel is capable of making a decent graphics card after all the others that have tried? let me cut it short: no.

And do you think Intel who normally remains clueless about Open Source is going to open source drivers for a new add-in card? Keep in mind, they only open sourced their drivers for archaic integrated cards that are openly laughed and mocked at by the gaming communities.

Reality check here. Probably not.

Back onto the topic itself, I think this move from Greg KH is already in the process of dying. Also, since I didn't see it while reading through, keep this in mind:

Greg Works for Suse. quote:  gregkh-AT-suse.de

Now, I'm just going to toss a conspiracy theory out here, and this is just a theory.

Who would gain most if binary drivers were outlawed from the Linux kernel?

Who would users have to turn to for reliable and effective 3D acceleration?

Who just signed a deal with Suse, aka, Novell over distribution agreements? (and several other matters, also using the agreement to indicate future lawsuits for those not buying from Novell or this vendor)

see where I'm going with this? I may be over thinking this, but my gut reaction is that this idea is being put foward at the behest of a corporation that has a long history of being anti-open source.

---

### Post by MetalMusicAddict on 2006-12-14
> **Saist said:**
> Now, I'm just going to toss a conspiracy theory out here, and this is just a theory.

Who would gain most if binary drivers were outlawed from the Linux kernel?

Who would users have to turn to for reliable and effective 3D acceleration?

Who just signed a deal with Suse, aka, Novell over distribution agreements? (and several other matters, also using the agreement to indicate future lawsuits for those not buying from Novell or this vendor)

see where I'm going with this? I may be over thinking this, but my gut reaction is that this idea is being put forward at the behest of a corporation that has a long history of being anti-open source.

Like you said "I may be over thinking this" but interesting none the less. Also the blog post has some good points. Good read. ;)

---

### Post by ZylGadis on 2006-12-14
Hex_mandos and the guy fearing DRM: nobody is telling **you**, the user, what to do. You can use binary blobs all you like. The thrust of the argument is that it is prohibited to **distribute** binary blobs linked to GPL code. So Feisty, if it goes as planned, will be **illegal**.

You, as a user, have the right and complete freedom to do anything you like with your hardware - install nvidia drivers, flash, whatever. However, once you distribute the kernel with the nvidia drivers, you'll violate the GPL. The fact that the kernel developers have been ignoring such violations does not mean they will continue to do so.

So, to sum up: if you (as a user) badly need nvidia drivers, nobody is preventing you from installing them. However, it is absolutely illegal for Ubuntu, or any other distro, to ship with binary drivers.

Granted, the kernel devs are going a bit over the top with actually prohibiting binary drivers whatsoever, because that is not in the GPL spirit. What they should do, I think, is start legal action against the distributions that violate GPL - then things will fall into place quickly. Unfortunately technical people fear the idiocies of lawsuits, that is why some of the kernel devs decided to do what is easy for them.

---

### Post by MetalMusicAddict on 2006-12-14
ZylGadis, as I understand it things will be fine for 12 months, then you WILL be prevented from compiling the nVidia/ATI/whatever drivers against a kernel that has this patch applied. It wont work.

---

### Post by tbroderick on 2006-12-14
> 
Who would gain most if binary drivers were outlawed from the Linux kernel?

BSD?

> Who would users have to turn to for reliable and effective 3D acceleration?

Intel?

> Who just signed a deal with Suse, aka, Novell over distribution agreements? (and several other matters, also using the agreement to indicate future lawsuits for those not buying from Novell or this vendor)

What does that have to do with the kernel? 

> ]see where I'm going with this? I may be over thinking this, but my gut reaction is that this idea is being put foward at the behest of a corporation that has a long history of being anti-open source.

I do think you are over thinking this.

---

### Post by MetalMusicAddict on 2006-12-14
[Patch removed with apology. ]("http://lkml.org/lkml/2006/12/14/63")

---

### Post by OffHand on 2006-12-14
> **MetalMusicAddict said:**
> ZylGadis, as I understand it things will be fine for 12 months, then you WILL be prevented from compiling the nVidia/ATI/whatever drivers against a kernel that has this patch applied. It wont work.

Yeah, you are right and ZylGadis is wrong. The plan was to prevent you from using binaries.

---

### Post by Polygon on 2006-12-14
> **MetalMusicAddict said:**
> [Patch removed with apology. ]("http://lkml.org/lkml/2006/12/14/63")

i can see where they are coming from.  But im kinda glad they removed it, but it would of been really cool if more companies would open source their drivers if non gpl drivers wernt allowed.

---

### Post by MetalMusicAddict on 2006-12-14
> **Polygon said:**
> i can see where they are coming from.  But im kinda glad they removed it, but it would of been really cool if more companies would open source their drivers if non gpl drivers wernt allowed.

Yea. I really do see both sides.

I will tell you this, 1st company that comes out with a really good, fully functioning, GFX card with open drivers Ill buy it. nVidia/Intel/ATI/VIA whoever.

---

### Post by Polygon on 2006-12-14
but the problem is that ati / nvidia want to keep their video card hardware specs secret from each other, and if they open source the drivers, they are basically giving the hardware specs to anyone who wants to view them.

maybe they could come to some form of agreement? Open source video drivers would not only benefit linux but all operating systems, windows and mac included.

---

### Post by MetalMusicAddict on 2006-12-14
> **Polygon said:**
> but the problem is that ati / nvidia want to keep their video card hardware specs secret from each other, and if they open source the drivers, they are basically giving the hardware specs to anyone who wants to view them.
Thing is (its been said here already) they license tech from other companies so they couldnt open them up as they are now. I think it would be cool of them to develop a "open" line of cards. Also, as I hear it, its all about the drivers anyway. The hardware isnt really a secret. Could be wrong.
> maybe they could come to some form of agreement? Open source video drivers would not only benefit linux but all operating systems, windows and mac included.
SOME kind of agreement needs to be made on all sides.

---

### Post by ZylGadis on 2006-12-14
> **OffHand said:**
> Yeah, you are right and ZylGadis is wrong. The plan was to prevent you from using binaries.

This is the second time in a row that you are trying to bash me without any apparent reason and without any arguments supplied. The first time I decided not to make a big deal out of it, but you don't learn. Can you please pinpoint where I am wrong, and why? Because if you cannot, I am going to report you.

---

### Post by Daveski on 2006-12-14
Perhaps someone can comment on this, but I cannot understand why an open source driver would be giving away any secrets. Polygon says that the company would be giving away hardware specs to anyone that wants to view them - is this bad? 'This hardware has a cool function: X. This is how you ask the hardware to perform X ... ' The driver might give some clue as to how the function is implemented, but I thought the point about hardware acceleration was that the number crunching was done in the hardware (or probably firmware or microcode - which of course the hardware manufacturer can jealously guard).

We have a graphics library - OpenGL, or the proprietary DirectX in Microsoft land, which interfaces with a driver which initiates functions within the hardware. This is how I broadly understand the process. We are lucky there are decent open graphics libraries, but the real 'property' of the hardware manufacturer should be buried in the hardware itself. If there are functions in the driver that the manufacturers do not want to share (quite rightly), then these functions should be moved to the hardware and the driver simply asks the card to run the internal function called X.

---

### Post by PriceChild on 2006-12-14
> **Daveski said:**
> Perhaps someone can comment on this, but I cannot understand why an open source driver would be giving away any secrets.Open source your driver... and you release the EXACT way in which your hardware works and how the software interfaces with it.

This means that your opposition can copy your design implementations, and along with their own secrets, make a better card than you therefore being seen as "better" and get more money.

Pricey

---

### Post by Daveski on 2006-12-14
I disagree - unless a graphics card is just another general processor and all the functions are implemented in the driver code. I thought this would be like a winmodem which was a very simple interface to the telephone line, all the processing was done by your CPU via the driver code. A 'hardware' modem simply needs a serial interface and all the modulation and error correction in done in the hardware. No secrets of the harware manufacturers design implementation given away with the AT command set. Perhaps I simply do not understand how a hardware graphics system works.

---

### Post by MetalMusicAddict on 2006-12-14
> **ZylGadis said:**
> This is the second time in a row that you are trying to bash me without any apparent reason and without any arguments supplied. The first time I decided not to make a big deal out of it, but you don't learn. Can you please pinpoint where I am wrong, and why? Because if you cannot, I am going to report you.

I dont think this was a bash at all. Read the link on the first post and it explains how it would work.

Remember we all done speak english here so some things could come across differently then they're ment. :)

---

### Post by prizrak on 2006-12-14
As Torvalds himself already pointed out it would accomplish nothing. All that would happen is that the drivers will be moved into userspace and simply call kernel functions. That would not violate the GPL in any way shape or form but still would accomplish the same thing. In fact that is exactly how nVidia does it. There is a FOSS kernel module that invokes a binary X module that is sitting at user level. So instead of an issue at kernel level you get one in user space. As the Russian saying goes "it's like trading a prod for a soap", which basically means that there is no point whatsoever in this.

---

### Post by PatrickMay16 on 2006-12-14
> **ZylGadis said:**
> This is the second time in a row that you are trying to bash me without any apparent reason and without any arguments supplied. The first time I decided not to make a big deal out of it, but you don't learn. Can you please pinpoint where I am wrong, and why? Because if you cannot, I am going to report you.

Whoa, man! COOL IT! Slow your roll. He wasn't attacking you, he just said you were wrong. What's so bad about that?

And while I'm at it, I was thinking.
This seems to be a time when Linux is becoming more ready for the desktop... and just as this is happening, these nutloaders here start pulling their weight and NVIDIA/ATI/Atheros/etc, instead of releasing source code, just stop writing Linux drivers, and so Linux comes crashing down and forgotten as people can't get accellerated 3D or wireless networking any more (or at least without having to do a load of incredibly annoying workaround crap). 
Maybe I have misunderstood the situation, and this is unlikely or impossible. Dunno.

Though this would affect me. I have an nvidia card and use it to play some games. If I was forced to use the nv driver I would be pretty angry about it.

---

### Post by qamelian on 2006-12-14
> **delfick said:**
> so if we can't have proprietary drivers, then we can't use beryl or compiz.....that would suck so bad it's not funny....
Not necessarily. Beryl runs just fine on my laptop with the standard xorg radeon drivers.

---

### Post by Fitzy_oz on 2006-12-14
> **drphilngood said:**
> I had totally forgotten that we had this option.  If their next generation of GPUs are just _as good_ as my current nVidia, I think my next GPU will be Intel, also.

If my crappy 32mb onboard i865 is anything to go by they very well might be - it runs XGL and compiz better than my ATI or Nvidia cards do just a shame about the gaming.
 

It will be a shame to see Non-GPL drivers banned as one of the most significant advantages of Linux for me is Freedom - Not just the lack of a price tag, but the freedom to use it the way I see fit.  I don't want someone telling me what drivers I can and cannot use, I'm a grown adult for god's sake!  If using Non-GPL doesn't fit with your ideologies then don't use them - that's beauty of freedom of choice.  It's a shame that this is coming under threat.   Installing these drivers is straight forward - If it's a legal problem to distribute them - Don't distribute them but don't take way people's freedom to use these drivers if **THEY CHOOSE TO**.  

That's my take on it anyway, I don't claim to be right, this is simply my opinion.

---

### Post by darkninja on 2006-12-14
I am seriously having doubts that I could even call the Linux kernel "Open-Source" anymore with a straight face after reading some of these replies.

Is utterly useless Beryl bling-bling and outdated Windows games worth sacrificing the entire philosophy that got Linux to where it is today?

Binary modules are a bit like a drug addiction, it will be very painful to withdraw now but if we keep waiting it will only get worse, until we reach the point where we can't stop even if we wanted too.

There's another popular *nix OS that allows binary blobs, is more "free" and doesn't have any GPL restrictions and it's called FreeBSD. Perhaps to everyone who's getting so outraged by the kernel developers honestly speaking their mind that enough is enough should pack their bags and leave?

Linus is simply playing to the crowd, focusing on popularity right now rather then thinking about what the future will hold. The plan proposed by Greg KH I agree with in theory, though it needs more structure and time. I'd like to see the kernel developers come out and say "Absolutely no more new binary modules from now on, except updates" and then give a decent time frame to replace them.

Though the developers can't stop you from loading up the binary modules yourself they are more then capable of preventing Ubuntu from distributing them pre-installed and prevent the hardware companies from distributing derivative works based on the Linux kernel. You would still be free to use your current kernel and binary drivers.

</rant>

---

### Post by delfick on 2006-12-14
what if there was a way developed so that opensource drivers could be made, but in a way so that they don't give the hardware developer's competition their secrets, and methods, etc......(basically the reasons why they don't already supply opensource drivers)


or isn't that possible at all......

(excuse my lack of technical knowledge :D)

---

### Post by DoctorMO on 2006-12-14
> nutloaders

How dare you insult programmers that helped your computer do the things it does. what right have you got to say such things!? There are not people who just spout their minds and then go home; these are kernel devs and you should be kissing their feet; not calling them names.

The first thing is that torvalds is right, but not in a way he thinks he is. The action here which has been removed would constitute self remedy of copy right infringement which is technically illegal since if someone if committing copyright infringement they should take it up in court not through their own means. this is the same thing that Microsoft breaks with WGA which is also self remedy.

I don't aprove of binary drivers, they're unstable, dangerous and unsupported. you are always welcome to install them on your computer in the same fashion as you are able to set fire to it. but know that we will enjoy a better world should free drivers be finished and working and your support for binary drivers only hurts the open source world.

---

### Post by 23meg on 2006-12-14
> **Saist]
And do you think Intel who normally remains clueless about Open Source is going to open source drivers for a new add-in card? Keep in mind, they only open sourced their drivers for archaic integrated cards that are openly laughed and mocked at by the gaming communities.

Reality check here. Probably not.[/QUOTE]They have a big name, Keith Packard working for them, and I remember him saying at the last DebConf that every new Intel card will get open source drivers.[QUOTE=prizak] As Torvalds himself already pointed out it would accomplish nothing. All that would happen is that the drivers will be moved into userspace and simply call kernel functions. That would not violate the GPL in any way shape or form but still would accomplish the same thing. In fact that is exactly how nVidia does it. There is a FOSS kernel module that invokes a binary X module that is sitting at user level.[/QUOTE]
Yes, and this entire matter came out of a discussion of whether it's feasible to allow or encourage moving drivers to userspace. To repeat, this is the case with the nvidia driver right now said:**
> 
Is utterly useless Beryl bling-bling and outdated Windows games worth sacrificing the entire philosophy that got Linux to where it is today?1) Beryl isn't just about bling and isn't utterly useless.

2) Beryl doesn't essentially depend on closed source drivers; it so happens that the infrastructure it relies on is delivered by only closed source drivers for *most* hardware, at *this* time.

3) The "entire philosophy of Linux" and its history aren't exempt from compromises. It's not a history written by purists with black-or-white ideological agendas. Even the FSF who are known for their "purism" (a term I disagree with) have resorted to many compromises for good reason: to strengthen their position in order to put out a better fight against the proprietary front. Using proprietary drivers a*t a certain time*, *for certain use cases* isn't necessarily dumping all the gains that Free software proponents fought for. You may very well resort to proprietary goods as part of a broader strategy to get rid of them. The immediate implications of a choice don't necessarily represent its intentions.

4) Given the present attitude of most companies, which we perhaps can't have an effect on with the current popularity of Linux, banning binary modules in the kernel will result in companies doing their thing in userspace, and as Linus puts, this isn't a good thing *for the kernel* to begin with.

[QUOTE=hex_mandos]Anyway, the Linux is free, right? It can always be forked to allow binary drivers again if the FLOSS Fundies take over.[/QUOTE]It would better not happen. It would bring a lot of uncalled for overhead and fuss.

---

### Post by Polygon on 2006-12-15
they already decided against banning kernel binary modules... so no need for anyone to worry. But still, it would be 100% better if a lot more companies open sourced their drivers. i bet 90% of the crashes currently in linux are caused BY binary drivers...

---

### Post by mushroom on 2006-12-15
What's so horrible about binary drivers? There are legal means to have them downloaded and installed with the user's consent at boot (which is what I imagine Feisty's going to do). It would be great if manufacturers freed their drivers, but at this point, they're legally redistributable as long as they're not linked to the kernel upon distribution; they are also free of price, and this is really the best manufacturers can do at this point without revealing trade secrets. If security is your concern, then simply know that there's a potential risk in using them, no one's forcing it. There is nothing wrong with allowing free and proprietary software to coexist, and anything else is non-free in my opinion. This patch was effectively DRM (even worse, it's DRM whose intention is to prevent something that's legal), and I'm glad they removed it.

---

### Post by DoctorMO on 2006-12-15
Read the full thread mushroom, it's about the programmers, not the users. the programmers are getting sick of dealing with problems they can't fix.

---

### Post by mushroom on 2006-12-15
But why deliberately prevent the user from using proprietary software? No one said the devs had to support it.

---

### Post by DoctorMO on 2006-12-15
But no one said the devs had to support it; thus if they remove their support you can no longer use it because it's unlikely each binary driver company will support it in the kernel.

---

### Post by mushroom on 2006-12-15
"Removing their support" doesn't equal "preventing the use of", though. I'm not asking devs to bend over backwards to allow binary drivers to work, that's the manufacturer's job. I just don't want the devs to deliberately disallow it. The right to use such things is really all I want, it's the manufacturer's decision as to whether it wants to continue developing drivers for Linux.

---

### Post by OffHand on 2006-12-15
> **ZylGadis said:**
> This is the second time in a row that you are trying to bash me without any apparent reason and without any arguments supplied. The first time I decided not to make a big deal out of it, but you don't learn. Can you please pinpoint where I am wrong, and why? Because if you cannot, I am going to report you.

Report me for saying you are wrong with your statement? lol... but here you go: [http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824](http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824)

Read the whole discussion here: [http://thread.gmane.org/gmane.linux.kernel/475654/](http://thread.gmane.org/gmane.linux.kernel/475654/)

---

### Post by DoctorMO on 2006-12-15
> "Removing their support" doesn't equal "preventing the use of", though. I'm not asking devs to bend over backwards to allow binary drivers to work, that's the manufacturer's job. I just don't want the devs to deliberately disallow it. The right to use such things is really all I want, it's the manufacturer's decision as to whether it wants to continue developing drivers for Linux.

I know, but if they have code which supports binary drivers such as the user space code or the various hooks and then decide they no longer wish to deal with that code any more and simply remove it. then it really doesn't matter what anyone does to install an nVidia binary driver you would have to recompile the kernel with extras... oooh lovly.

---

### Post by mushroom on 2006-12-15
Have they said anything about removing that sort of code? I'm not a programmer, and I still know very little about low-level processes and such, but would removing that even be practical? This is a genuine question, I'm not trying to prove a point or anything.

---

### Post by Daveski on 2006-12-15
> **delfick said:**
> what if there was a way developed so that opensource drivers could be made, but in a way so that they don't give the hardware developer's competition their secrets, and methods, etc......(basically the reasons why they don't already supply opensource drivers)


or isn't that possible at all......

(excuse my lack of technical knowledge :D)

This is the question I am also asking. Are there any knowledgable people out there who can answer this question? I have never been involved in writing drivers and as I have said before, I thought that the 'clever stuff' was embedded in the hardware, not exposed as functions in the drivers.

---

### Post by prizrak on 2006-12-15
> **Polygon said:**
> they already decided against banning kernel binary modules... so no need for anyone to worry. But still, it would be 100% better if a lot more companies open sourced their drivers. i bet 90% of the crashes currently in linux are caused BY binary drivers...

And you will lose that bet. On my older laptop (may it rest in pieces) crashes were normally caused by the open source video driver. My new laptop (just happens to have nVidia card) works flawlessly with the binary drivers and gives me no issue whatsoever. In fact the open sourced NV driver couldn't even render 2D properly. 

Binary != bad quality. The main problem with a binary driver is that if anything is broken it cannot be fixed by anyone other than the manufacturer, which is why the nVidia driver had a known security hole in it for like 2 years.

---

### Post by prizrak on 2006-12-15
> **Daveski said:**
> This is the question I am also asking. Are there any knowledgable people out there who can answer this question? I have never been involved in writing drivers and as I have said before, I thought that the 'clever stuff' was embedded in the hardware, not exposed as functions in the drivers.

It is possible to use embedded firmware only with an open protocol for communication with the rest of the system. The issue will be updating the driver, few people flash their firmware as often as they update the driver. It is more than possible to brick your hardware with a bad firmware update, with a driver it just has to be reinstalled. 

It will still not satisfy purists however, there is actually a project to replace normal BIOS found in today's computers with an open sourced one because they feel that you should be able to modify your BIOS as well (not that 99.9% of people would) so it would still be an issue. 

All of the other issues apply as well, if there is a problem with the driver they can't fix it. In FOSS world it is not unheard of getting patches hours after a flaw is discovered. There can also be issues like Xorg 7.1 and the old nVidia driver where 7.1 could not work with it. There would still have to be function calls and such and if they change (and they will that's normal) then it would still require the same rewrite as it does now. Not to mention that it is alot harder to test a closed driver than it is an open one for obvious reasons.

---

### Post by prizrak on 2006-12-15
> **ZylGadis said:**
> Hex_mandos and the guy fearing DRM: nobody is telling **you**, the user, what to do. You can use binary blobs all you like. The thrust of the argument is that it is prohibited to **distribute** binary blobs linked to GPL code. So Feisty, if it goes as planned, will be **illegal**.

You, as a user, have the right and complete freedom to do anything you like with your hardware - install nvidia drivers, flash, whatever. However, once you distribute the kernel with the nvidia drivers, you'll violate the GPL. The fact that the kernel developers have been ignoring such violations does not mean they will continue to do so.

So, to sum up: if you (as a user) badly need nvidia drivers, nobody is preventing you from installing them. However, it is absolutely illegal for Ubuntu, or any other distro, to ship with binary drivers.

Granted, the kernel devs are going a bit over the top with actually prohibiting binary drivers whatsoever, because that is not in the GPL spirit. What they should do, I think, is start legal action against the distributions that violate GPL - then things will fall into place quickly. Unfortunately technical people fear the idiocies of lawsuits, that is why some of the kernel devs decided to do what is easy for them.

Please don't talk about things you do not understand. Feisty would not be illegal, the ENTIRE Ubuntu line would be illegal as it comes with the madwifi driver that contains a kernel level binary blob. nVidia driver is 100% legal as it doesn't work in kernel space but rather in user space calling kernel functions. The part of the nVidia driver that actually works at kernel level is 100% open sourced (and contains no information whatsoever about the design of the card).

---

### Post by prizrak on 2006-12-15
> **DoctorMO said:**
> I know, but if they have code which supports binary drivers such as the user space code or the various hooks and then decide they no longer wish to deal with that code any more and simply remove it. then it really doesn't matter what anyone does to install an nVidia binary driver you would have to recompile the kernel with extras... oooh lovly.

Then nVidia will have to come up with another way to install their driver. Basically if you write software for something it is your responsibility to make sure it works. When I develop for Windows I use Windows API's in order for my software to work right. When I program for databases I use a driver that lets me talk to that database and use SQL queries in my code (was pretty cool code too everything was 100% modular and crossplatform). Point is that nothing is stopping nVidia from running 100% from userspace, same with everyone else. The problem is that it would still cause the same issues.

---

### Post by OffHand on 2006-12-15
> **prizrak said:**
> nVidia driver is 100% legal as it doesn't work in kernel space but rather in user space calling kernel functions.
I think you are wrong if I understand the discussion between the devs the right way. 

Source: [http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824](http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824)

---

### Post by MetalMusicAddict on 2006-12-15
Well this is my last post in here. :)

As I see it the topic is done and over with. We've seen the beginning, middle and end of the situation all in this thread.

We are now getting to topics that have many, many duplicates around the forum.

---

### Post by OffHand on 2006-12-15
> **MetalMusicAddict said:**
> Well this is my last post in here. :)

As I see it the topic is done and over with. We've seen the beginning, middle and end of the situation all in this thread.

We are now getting to topics that have many, many duplicates around the forum.

C ya in another thread!  ;)  I'm still not done with this one :mrgreen:

---

### Post by prizrak on 2006-12-15
> **OffHand said:**
> I think you are wrong if I understand the discussion between the devs the right way. 

Source: [http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824](http://thread.gmane.org/gmane.linux.kernel/475654/focus=475824)

No you misunderstand and that is something that Torvalds touches on. The nVidia driver is not loaded into the kernel at all it is a userspace driver it loads into X (I don't know what Xorg's stance on it though). The thing that gets loaded into the kernel is a shim, it's GPL'ed code that uses kernel headers and loads the nVidia driver at X start. This is basically what Torvalds said that if the patch would be introduced into the tree and actually adopted then manufacturers will do exactly what nVidia is doing and put their drivers into userspace (bad idea according to him). He basically feels it is wrong from a tech point of view, the legality is highly questionable too but is a gray area.

---

### Post by Hendrixski on 2006-12-15
> **MetalMusicAddict said:**
> Well this is my last post in here. :)

As I see it the topic is done and over with. We've seen the beginning, middle and end of the situation all in this thread.

We are now getting to topics that have many, many duplicates around the forum.

No doubt many of the things discussed in this thread will pop up again and again in many more threads yet to come.  I think I'm done here too.

Bye bye thread.  It was good while it lasted.

---

### Post by OffHand on 2006-12-15
> **prizrak said:**
> No you misunderstand and that is something that Torvalds touches on. The nVidia driver is not loaded into the kernel at all it is a userspace driver it loads into X (I don't know what Xorg's stance on it though). The thing that gets loaded into the kernel is a shim, it's GPL'ed code that uses kernel headers and loads the nVidia driver at X start. This is basically what Torvalds said that if the patch would be introduced into the tree and actually adopted then manufacturers will do exactly what nVidia is doing and put their drivers into userspace (bad idea according to him). He basically feels it is wrong from a tech point of view, the legality is highly questionable too but is a gray area.

I need some time to process this  ;)

---

### Post by PatrickMay16 on 2006-12-15
> **DoctorMO said:**
> How dare you insult programmers that helped your computer do the things it does. what right have you got to say such things!? There are not people who just spout their minds and then go home; these are kernel devs and you should be kissing their feet; not calling them names.

Cool it, man. Sorry for the "nutloaders". It was meant to be lighthearted, not offensive or anything. You're right, though. I shouldn't have said that. Still, I tell you that if I was more serious, I would use an actually recognised offensive word. Like "bastards" or something.

Let's cool down here.

---

### Post by zetetic on 2006-12-17
We should all avoid bying from ATI and Nvidia.

We need to boicot those companies.

The right decision is to buy the suitable hardware to our prefered software; not the contrary.

zetetic

---

### Post by prizrak on 2006-12-17
> **zetetic said:**
> We should all avoid bying from ATI and Nvidia.

We need to boicot those companies.

The right decision is to buy the suitable hardware to our prefered software; not the contrary.

zetetic

That is what I've said in these kinds of discussions.

---

### Post by 23meg on 2006-12-17
> **zetetic said:**
> We should all avoid bying from ATI and Nvidia.

We need to boicot those companies.

The right decision is to buy the suitable hardware to our prefered software; not the contrary.

zeteticMy next chip will be an Intel.

---

### Post by darrenm on 2006-12-18
> **23meg said:**
> My next chip will be an Intel.

Keep reading that Intel open-source their drivers but the only driver I can see with X that supports Intel stuff is the i810 driver. Does that cover all the 865, 915, 965 etc chips? Are the open-source Intel drivers built into X? I downloaded some drivers from Intel but it looks like I need to rebuild X with them.

---

### Post by OffHand on 2006-12-18
> **prizrak said:**
> He basically feels it is wrong from a tech point of view, the legality is highly questionable too but is a gray area.

I have re-read the discussion between the devs again and I am pretty sure it is not only because of a technical reason Linus is against this patch.

---

### Post by zetetic on 2006-12-19
> **23meg said:**
> My next chip will be an Intel.

Can you please tell me what chip will you choose? I'm interested, because I also want to buy a new graphics card.

The new graphics card (not integrated) should do 3d acceleration and should have open source drivers.

Thanks in advance,

zetetic

---

### Post by KiwiNZ on 2006-12-19
> **zetetic said:**
> We should all avoid bying from ATI and Nvidia.

We need to boicot those companies.

The right decision is to buy the suitable hardware to our prefered software; not the contrary.

zetetic

That would be counter  productive. The way to get a company to produce  and invest is to show there is a demand. If Linux users avoid their products there will be no demand , therefore they will no investment or production .

---

### Post by zetetic on 2006-12-19
> **KiwiNZ said:**
> That would be counter  productive. The way to get a company to produce  and invest is to show there is a demand. If Linux users avoid their products there will be no demand , therefore they will no investment or production .

I don't think so. If the user base don't buy their products because of the lack of a certain quality (in our case because the lack of open source drivers), then, because corporations need to survive and like to earn money, they will start giving the public the mentioned quality (open source drivers).

If they don't give to the public what the public wants, they don't make profits.

We rule, corporations are our slaves... They will do anything to have our money. We just need to open our eyes and be clever.

zetetic

---

### Post by prizrak on 2006-12-19
> **OffHand said:**
> I have re-read the discussion between the devs again and I am pretty sure it is not only because of a technical reason Linus is against this patch.

Too lazy to look up the quote so I'll just say it from memory. Linus says that if we ban binary blobs in the kernel all that will happen is those who make those drivers will put them in userspace, which he feels to be technically incorrect as those drivers shouldn't be running from userspace. 

In any case this is my understanding of what his saying, after all I'm not Torvalds so I can't speak for him. It's quite possible I'm incorrect. 

I do believe that the real reason is pragmatic he would rather deal with some questionable binaries than risk losing users. 

> That would be counter productive. The way to get a company to produce and invest is to show there is a demand. If Linux users avoid their products there will be no demand , therefore they will no investment or production .
> I don't think so. If the user base don't buy their products because of the lack of a certain quality (in our case because the lack of open source drivers), then, because corporations need to survive and like to earn money, they will start giving the public the mentioned quality (open source drivers).

If they don't give to the public what the public wants, they don't make profits.

We rule, corporations are our slaves... They will do anything to have our money. We just need to open our eyes and be clever.


You are both correct in your own way. Yes if a product is not being bought because it is lacking a certain feature an improved product with that feature gets introduced, it can get dropped altogether but only if the company has other successful products. 

If a large number of people stops buying from AMD/nVidia because they don't provide open specs to their hardware they will have to either take a loss or open up the specs. However since Linux is about 3% of the desktop market and out of that 3% about 6% care that something is FREE neither company would lose enough to open up the drivers. 

Remember those drivers are there for the big customers that run render farms and those could care less about FOSS they care that w/e they are using works. Now if we would stop buying wi-fi cards, printes, scanners, ethernet cards, etc... from manufacturers who don't provide open drivers. The competition there is a lot more fierce and each user counts.

---

### Post by DoctorMO on 2006-12-19
Er render farms don't need 3D cards it's all done in memory.

Design labs do however, pixar uses linux design labs from memory.

---

### Post by kanem on 2006-12-20
> **zetetic said:**
> Can you please tell me what chip will you choose? I'm interested, because I also want to buy a new graphics card.

The new graphics card (not integrated) should do 3d acceleration and should have open source drivers.

Thanks in advance,

zetetic
I think all of Intel's new 3D ones are integrated unfortunately. The [GMA x3000](http://en.wikipedia.org/wiki/Intel_GMA#GMA_X3000) is the latest and greatest.  It's pretty new and I've seen only one benchmark.

---

### Post by kanem on 2006-12-20
I found an interesting read on a short history of [video cards and Linux](http://www.linux.com/howtos/Linux-Gamers-HOWTO/x608.shtml).

I wasn't into this stuff back then, so it's news to me that:

The top video card was 3dfx's Voodoo, which had open source drivers for Linux. They lost the game when nVidia and ATI came along.

ATI used to open source their drivers until they and nVidia got into an arms race.

---

### Post by prizrak on 2006-12-20
> **DoctorMO said:**
> Er render farms don't need 3D cards it's all done in memory.

Design labs do however, pixar uses linux design labs from memory.

My apologies for some reason I thought renderfarms went through the video hardware as well. 
> I think all of Intel's new 3D ones are integrated unfortunately. The GMA x3000 is the latest and greatest. It's pretty new and I've seen only one benchmark.
There have been rumors of Intel wanting to release a standalone card to compete with AMD/nVidia. I doubt that they would be able to release something that could compete with those cards but a standalone Intel with open drivers (or at least specs) would be a viable solution for those who want free hardware but can't swap out the motherboard. 

> I found an interesting read on a short history of video cards and Linux.

I wasn't into this stuff back then, so it's news to me that:

The top video card was 3dfx's Voodoo, which had open source drivers for Linux. They lost the game when nVidia and ATI came along.

ATI used to open source their drivers until they and nVidia got into an arms race.
That's interesting because the Voodoo card used special interface called Glide (or was it Glade?) that was completely proprietary and is actually what OpenGL is based on. OpenGL stands for open Glide (Glade?) that was pre DirectX era.

---

### Post by Stormy Eyes on 2006-12-20
> **MetalMusicAddict said:**
> [http://lwn.net/Articles/213976/](http://lwn.net/Articles/213976/) 

[Linus's response.]("http://lkml.org/lkml/2006/12/13/370")

[Patch removed with apology. ]("http://lkml.org/lkml/2006/12/14/63")

Linux gaming? What Linux gaming? The last good big-name commercial game that came out for Linux was *Neverwinter Nights*.

---

### Post by Daveski on 2006-12-20
> **prizrak said:**
> OpenGL stands for open Glide (Glade?) that was pre DirectX era.

Thought it was *Open Graphics Library*.

---

### Post by delfick on 2006-12-20
> **Daveski said:**
> Thought it was *Open Graphics Library*.

so did I :D

---

### Post by Polygon on 2006-12-21
> **Stormy Eyes said:**
> Linux gaming? What Linux gaming? The last good big-name commercial game that came out for Linux was *Neverwinter Nights*.

doom3? unreal tournament 2004? americas army 2.5? quake 4? There have been some commercial games ever since NWN

and 3d labs like pixar only use comps with video cards just to make the scene or whatever, then after they are done creating the scene and putting x model in y position and have all the lighting done, they have a huge server farm complile and render the scene, which is just raw cpu and ram power.

Speaking of which... how much would that suck to have the cpu farm crash on you while its doing that....

---

### Post by prizrak on 2006-12-21
> **Daveski said:**
> Thought it was *Open Graphics Library*.
Actually you are correct it is. Aparently Glide used the same design paradigm as OpenGL so it was actually backwards from what I said Glide was based on OpenGL and was actually open sourced at some point but 3DFX more or less died by then.

---

### Post by christhemonkey on 2006-12-21
Sorry if this has been adressed, but i didnt read the entirety of this thread.

**@delfick**
> can someone clarify this for me?

if this goes the bad way, we won't have proprietary drivers ??

From the kernel developers response/apology/removal of patch:
> [side diversion,** it's not the video drivers that really matter** here
everyone, those are just so obvious.  It's the hundreds of other
blatantly infringing binary kernel modules out there that really matter.
The ones that control filesystems, cluster interconnects, disk arrays,
media codecs, and a whole host of custom hardware.  That's the real
problem that Linux faces now and will only get worse in the future.
[B]It's not two stupid little video drivers, I could honestly care less
about them...[/B]]

So no, he wasnt majorly complaining about the video drivers, and now this code has been removed from his tree, it is not an issue at all.

---

### Post by Perfect Storm on 2006-12-21
> **Polygon said:**
> doom3? unreal tournament 2004? americas army 2.5? quake 4? There have been some commercial games ever since NWN

and 3d labs like pixar only use comps with video cards just to make the scene or whatever, then after they are done creating the scene and putting x model in y position and have all the lighting done, they have a huge server farm complile and render the scene, which is just raw cpu and ram power.

Speaking of which... how much would that suck to have the cpu farm crash on you while its doing that....

Aye, and the next in line for linux is UT2007 and Quakewars.


I know people in this thread have said "What gaming comminuty or games", but I have watch the trend among game developes and companies and there's actually a move towards linux installers for games. Yes it's alot of small companies etc. (plus ID which is big) but everything starts with a small step. It would be rather unrealistc to see a gigantic gaming companies releasing top games for linux with in a day.

---

### Post by Daveski on 2006-12-21
I doubt if Linux will be attractive to games developers as a platform until the market gets much bigger. XBOX makes it easy for a developer to make games for both the WinPC and Console market without too much effort, and video card manufacturers (in the game sector) are bias towards integration with the DirectX library.

Does anyone think that the PS3 - which I read will have a tailored Linux distro - will shift the developers towards more Linux friendly code? I don't know about the PS3, I presume it will have a proprietary graphics library (rather than OpenGL) and so perhaps will not make any real difference.

---

### Post by darkhatter on 2006-12-21
ps3 works with Red Hat Linux (fedora) not a surprise, and I believe it doesn't come preloaded. I believe everything on it except for the video card is open, and it uses OpenGL I beileve

---

### Post by delfick on 2006-12-21
> **christhemonkey said:**
> Sorry if this has been adressed, but i didnt read the entirety of this thread.
So no, he wasnt majorly complaining about the video drivers, and now this code has been removed from his tree, it is not an issue at all.

k then.... cool :D...thnx :D

---

### Post by notebook_ftw on 2006-12-22
> **darkhatter said:**
> ps3 works with Red Hat Linux (fedora) not a surprise, and I believe it doesn't come preloaded. I believe everything on it except for the video card is open, and it uses OpenGL I beileve
The PS3 is capable of booting pretty much any Linux distriubtion so long as the installer is acquired.  Yellow Dog 5 is the only distro officially supported by Sony the last I heard.  And games for PS3 are written using Sony's own proprietary languages and code, not OpenGL, though I'm sure the nVidia-based card is completely capable of supporting OpenGL.

It may be becoming a bit of dead horse now (I realize the patch has been removed), but I've just read most of this thread, and have a few thoughts.  First, of course open source drivers and software is what we all want.  This is the reason most of us came to Linux.  The problem is that we live in a world driven by money.  Software developers have families to feed just like you and me.  While I completely support free and open source software, I'm gonna go against the general concensus and just say that I have no problem with software devs making closed source software that they sell either.  Call me a sell-out, call me whatever you want, but until this world doesn't rely on money, that's the way I feel.  Idealizations have no place in the real world of today, and telling someone that they should go to college for four or five years and pay countless thousands of dollars for an education in software development only to then tell them that they shouldn't make money from that dedication is ludicrous.

That being said, I still promote free and open source software, but I think there should be a balance.  I also believe that closed source software does not have to be evil as in the way DRM is.  Certain software can be closed source but still allow you to use it any way you like and even modify it to a certain extent (aka mods), but only prevent you through license from distributing it (as this would cut out profits for the developer).  The thing about Linux that attracts me is freedom.  And after reading this thread and a few other things around the net, it seems to me that Linux faces becoming what it sought to resist; a license-restricted piece of software that it's developers wish to keep you from altering in any way they don't see fit.  Yeah, GPL and open source is all great, but part of freedom is realizing that you have to respect another person's choices as much as they respect yours.  I don't hate Microsoft for creating Windows and other closed source software (DRM excluded).  I hate Microsoft for trying to kill open source, and that's the only reason.  

I find it funny (and completely agree with Linus on this point) that some of the kernel devs can be so hypocritical.  They claim that they support open source because they support freedom, yet they sought to destroy freedom with this patch.  They now fly this banner of GPL (which I will not go into because I don't pretend to know any of the intricacies of the license), and in doing so limit the rights of not only software and hardware companies, but also the end user.  By making any piece of binary software that attaches itself to the kernel a violation of their license they are making it illegal for the hardware companies to write them and the end user to use them.  This is hardly what I call freedom.  It feels instead like attempted oppression.  Do it the open source way, or it's illegal.  How does that make them any better than Microsoft?  Sure, anyone can edit the kernel.  But only if they promise to stay within the confines of the GPL.  That's like Microsoft saying "Sure you can edit that program so long as you don't violate the EULA."  Correct me if I'm wrong here, as my knowledge of Linux and open source has not yet reached the level of many of you here, but this seems like the pot calling the kettle black.  


To finish off (long post I know), I am a strong believer that the universe is made up of balance.  You can't have good without bad; right without wrong.  Similarly, you can't have open source without closed source or vice versa.  I don't want to see open source die, but I don't want to prohibit anyone from making closed source software either.  If it's a good program, I'll use it, because it's worth it even if I have to pay for it.  Linux as I see it is about freedom; and that means freedom for everyone.  If nVidia wants to maintain only binary drivers to protect their hardware IP and 3rd party patents, they have that right.  If I want to use those drivers, I have that right.  Don't tell me I don't, and don't make it illegal.  That's not freedom.  If it ever gets to that point, there becomes no reason to choose Linux over Windows.  At least with Windows you get support and you aren't breaking the law just by trying to make your graphics card work right.

---

### Post by saulgoode on 2006-12-26
> Correct me if I'm wrong here, as my knowledge of Linux and open source has not yet reached the level of many of you here
Respectfully, you are wrong. 

You start by defending the right of programmers to make money from their efforts and I have no disagreement with you there. But would you not also assert their right to be compensated in other ways? Programmers who license their programs with the GPL do so not because they wish no compensation, but that they desire to be compensated by others contributing software (or improvements to their software) which is free from restriction *with regard to the end user*. 

Any comparison of the GPL to an EULA should boil down to one issue: there are **no** restrictions on what an *end user* can do with any GPL software he obtains. The rest of the GPL is a methodology for assuring those end users' rights. It does this by placing restrictions upon what a *distributor* is permitted to do with the programmer's copyrighted software. You may disagree with the philosophy of the GPL (i.e., you may feel end users' rights should be restricted), or you may disagree with the methodology of the GPL (i.e., you may wish the GPL didn't place restrictions upon distributors); but, just as a "proprietary" programmer has the right to earn money, the GPL programmer has the right to license his software in a manner which provides him the compensation he seeks.

The cited discussion on the LKML should make it very clear, aside from the kernel developer's rejection of "banning" *end users* from installing proprietary drivers, they feel *distribution* of those proprietary drivers with their software is a violation of their copyright. You might argue that there is a "loophole" in the GPL which permits bundling of proprietary drivers with GPLed code; but in so doing, you would be placing yourself at the same moral level of someone who would violate Microsoft's EULAs because of a supposed invalidity of their "shrinkwrap" implementation.

---

### Post by prizrak on 2006-12-26
> **saulgoode said:**
> Respectfully, you are wrong. 

You start by defending the right of programmers to make money from their efforts and I have no disagreement with you there. But would you not also assert their right to be compensated in other ways? Programmers who license their programs with the GPL do so not because they wish no compensation, but that they desire to be compensated by others contributing software (or improvements to their software) which is free from restriction *with regard to the end user*. 

Any comparison of the GPL to an EULA should boil down to one issue: there are **no** restrictions on what an *end user* can do with any GPL software he obtains. The rest of the GPL is a methodology for assuring those end users' rights. It does this by placing restrictions upon what a *distributor* is permitted to do with the programmer's copyrighted software. You may disagree with the philosophy of the GPL (i.e., you may feel end users' rights should be restricted), or you may disagree with the methodology of the GPL (i.e., you may wish the GPL didn't place restrictions upon distributors); but, just as a "proprietary" programmer has the right to earn money, the GPL programmer has the right to license his software in a manner which provides him the compensation he seeks.

The cited discussion on the LKML should make it very clear, aside from the kernel developer's rejection of "banning" *end users* from installing proprietary drivers, they feel *distribution* of those proprietary drivers with their software is a violation of their copyright. You might argue that there is a "loophole" in the GPL which permits bundling of proprietary drivers with GPLed code; but in so doing, you would be placing yourself at the same moral level of someone who would violate Microsoft's EULAs because of a supposed invalidity of their "shrinkwrap" implementation.
You are both wrong in assuming that you can't make money on open source. RedHat and Novell seem to be doing quite well despite providing GPL'ed OS's.

---

### Post by graigsmith on 2007-01-15
i think it would actually help linux in the end. if we don't do it now, we will pay in the future. If you want something that's closed source there is always windows.

---

### Post by prizrak on 2007-01-15
> **graigsmith said:**
> i think it would actually help linux in the end. if we don't do it now, we will pay in the future. If you want something that's closed source there is always windows.

What if I want something that does everything I want/need it to and Linux+closed software is a 100% match?

---

### Post by BoyOfDestiny on 2007-01-15
> **graigsmith said:**
> i think it would actually help linux in the end. if we don't do it now, we will pay in the future. If you want something that's closed source there is always windows.

Anyway, I think this quote is worthwhile and applicable...

In regard to Bitkeeper (that used to be used for managing the source of the kernel):

"It was also, whether intentionally or not, a powerful political PR campaign, telling the free software community that freedom-denying software is acceptable as long as it's convenient. If we had taken that attitude towards Unix in 1984, where would we be today? Nowhere. If we had accepted using Unix, instead of setting out to replace it, nothing like the GNU/Linux system would exist."
[http://www.gnu.org/philosophy/mcvoy.html](http://www.gnu.org/philosophy/mcvoy.html)

Anyway, not in 100% agreement with your comment (I think closed source is ok in a nice controlled emulated/sandboxed environment. Definitely dislike proprietary for any key system aspects.)
If I want the most flexible, stable, and portable system possible... Having little black boxes in the kernel isn't it... 

I think Linux has enough marketshare in mission critical and server arena. Luckily, some of these components are shared with Desktop users... I have a feeling in time if our market share is big enough, we can get away with saying only GPL kernel modules... 

Plenty of users are there right now I'm sure. Wireless on my laptop is using the intel ipw thing... Everything else AFAIK is Free (on board intel is enough for beryl and my games, so I'm happy)

---

