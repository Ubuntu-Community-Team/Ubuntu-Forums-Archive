---
title: "Intel releases new graphics driver"
date: 2006-08-09
forum: The Cafe
---

### Post by imagine on 2006-08-09
Don't know if this has been already posted, but I just came across it. If it's old news, merge/close/delete please =)

[quote=Keith Packard]The Intel Open Source Technology Center graphics team is pleased to announce the immediate availability of free software drivers for the Intel 965 Express Chipset family graphics controller. These drivers include support for 2D and 3D graphics features for the newest generation Intel graphics architecture. The project Web site is [http://IntelLinuxGraphics.org](http://IntelLinuxGraphics.org).
[...]
This release represents the start of a long term effort by Intel to work with the X.org and Mesa communities to continuously improve and enhance the drivers.[/quote]
From LWN: [http://lwn.net/Articles/194724/](http://lwn.net/Articles/194724/)

Maybe someone from NVIDIA or AMD should have a look at that.

---

### Post by ubuntu_demon on 2006-08-09
This is great news!

I believe you are the first to post this on the forums :)

I linked to this thread on my blog :

Intel releases open source i965 drivers
[http://ubuntudemon.wordpress.com/2006/08/09/intel-releases-open-source-i965-drivers/](http://ubuntudemon.wordpress.com/2006/08/09/intel-releases-open-source-i965-drivers/)

---

### Post by beuno on 2006-08-09
Well, I hope this puts some pressure on ATi and Nvidia to start opening up their own drivers so we can start making better use of the hardware we pay for  :-D

---

### Post by petervk on 2006-08-09
Id really like to know the significance of this.

Didn't intel already have opensource drivers? 
Is this a release of previously unavailable code? 
How mature are these drivers? 
Are these drivers competely free of any non-free binary blobs or code?
Is this finally something to compete with the Radeon 9200?
Will this finally be a way to compete with Nvidia's OpenGL hardware acceleration?

---

### Post by ubuntu_demon on 2006-08-09
> **beuno said:**
> Well, I hope this puts some pressure on ATi and Nvidia to start opening up their own drivers so we can start making better use of the hardware we pay for  :-D
That's what I thought :)

**update :**
I hope this puts **at least a little bit** of pressure on AMD and NVIDIA to eventually open up their drivers. I thought a bit about it and I don't think they will open source their drivers unles they do it together. IMHO if they do this then they will both produce drivers which are more powerful, more secure and more stable in the long run (for all platforms). They can still compete on the hardware front ofcourse.

---

### Post by imagine on 2006-08-09
If someone prefers articles over mailing list entries: [Intel aims for open-source graphics advantage](http://news.com.com/Intel+aims+for+open-source+graphics+advantage/2100-7344_3-6103941.html)



There are also [rumours](http://www.infoworld.com/article/06/08/02/32OPcurve_1.html) that AMD might open up "a functional subset of its graphics drivers", whatever this is. But rumours are just that, rumours.

> **petervk said:**
> Id really like to know the significance of this.
Didn't intel already have opensource drivers? Is this a release of previously unavailable code?
The i965 is the new chipset for the Core 2 Duo processor, which was introduced into the market exactly two weeks ago. (Compare that to [other vendors](http://www.driverheaven.net/~pete/article5.htm).)
There were already opensource drivers for older Intel graphic chips available, so Intel is "just" extending its work in opensource drivers here.
However the announcement and the new website also look as if Intel would strengthen its efforts in Linux drivers, but of course only the future can tell that.

> **petervk said:**
> How mature are these drivers?
I don't have a Core 2 Duo yet. :/ I think it is as stable/unstable as very first releases tend to be.

> **petervk said:**
> Are these drivers competely free of any non-free binary blobs or code?
Yes.

You can read more about opensource graphics drivers in the transcript of David Airlies speech at the Ottawa Linux Symposium: [http://www.linuxsymposium.org/2006/linuxsymposium_procv1.pdf](http://www.linuxsymposium.org/2006/linuxsymposium_procv1.pdf) (March 2006) starting at page 19.

---

### Post by bobbybobington on 2006-08-09
so do the intel graphics drivers work support opengl? :-?

---

### Post by G Morgan on 2006-08-09
> **beuno said:**
> Well, I hope this puts some pressure on ATi and Nvidia to start opening up their own drivers so we can start making better use of the hardware we pay for  :-D

I can't see it, Intel aren't a real player in this market. They could only pressurise each other and at the moment they are at a standoff.

---

### Post by prizrak on 2006-08-09
> **beuno said:**
> Well, I hope this puts some pressure on ATi and Nvidia to start opening up their own drivers so we can start making better use of the hardware we pay for  :-D

It won't for a few reasons. 
1) Intel is a niche manufacturer when it comes to graphics hardware. It is mostly confined to mobile and low cost PC's that have no need for powerful graphics. 
2) Intel's graphics chips are very basic and while they do have OpenGL and DD/D3D capabilities they are strength is mostly in 2D office stuff. 
3) Intel doesn't get significant revenue from the graphics sales, their cash cow is the CPU's they also have a very established market for the intergrated video solutions and have virtualy no competition in it. 
4) ATI and nVidia make their money mostly on their graphics cards (both also make chipsets). They are in a huge competition in both high end and budget markets. The biggest difference between the two lies in software not hardware. Opening up their drivers would be akin to shooting themselves in the foot, as it would enable the competitor to discover what makes the other one tick. Right now there is massive reverse engineering going on in both camps but as we know it's not the same as actual open specs (re: NTFS write, .doc in OO and so on).

---

### Post by Hotaru on 2006-08-10
[http://intellinuxgraphics.org/]("http://intellinuxgraphics.org/")
Intel has obout 40% of graphics market thanks to their built-in solutions. He's not a niche player at all!

---

### Post by imagine on 2006-08-10
I disagree.

> **prizrak said:**
> Intel is a niche manufacturer when it comes to graphics hardware.
Intel is the market leader with a market share of 35%.
> **prizrak said:**
> It is mostly confined to mobile and low cost PCs that have no need for powerful graphics.
True, but those PCs present the vast majority of all PCs.
> **prizrak said:**
> Intel doesn't get significant revenue from the graphics salesThis couldn't be further from the truth. Intel sold Chipsets (where their graphics chips are integrated) for 8,15 billions Dollar last year, that's more than AMD and ATI made *together* with *all* their products.


Ok, I deliberately ignored the point you wanted to make here. You're right that Intel is no competition in the high-end graphics market. However that doesn't mean that their graphics chips are useless or that they are no competition to anyone at all. The computer world cannot be divided in 1. people who play 3D shooters and need high-end graphics cards, and 2. people who do office work and don't need 3D at all. There's more than that, just have a look at X.org/AIGLX.

---

### Post by prizrak on 2006-08-10
> Intel has obout 40% of graphics market thanks to their built-in solutions. He's not a niche player at all!
The built-in solutions market is a niche market in the graphics market ;)

> This couldn't be further from the truth. Intel sold Chipsets (where their graphics chips are integrated) for 8,15 billions Dollar last year, that's more than AMD and ATI made *together* with *all* their products.
Yes but how much did Intel make on the sale of their CPU's? 

> Ok, I deliberately ignored the point you wanted to make here. You're right that Intel is no competition in the high-end graphics market. However that doesn't mean that their graphics chips are useless or that they are no competition to anyone at all. The computer world cannot be divided in 1. people who play 3D shooters and need high-end graphics cards, and 2. people who do office work and don't need 3D at all. There's more than that, just have a look at X.org/AIGLX.
I got XGL working on my Intel chip before and it sucked :) I don't think you got all of my point actually. Yes the first point was that Intel has no pressure on ATI and nVidia as their in two different markets (or rather different niches in the same market). The second part of the point (or second point if you will) was that Intel doesn't have much competition in the budget/built-in market. There are the nForce and ATI X series but they are not really on the same level as far as price and performance goes as Intel, not to mention that the nForce is mostly an AMD platform anyway and Intel doesn't make AMD chipsets (would be weird if they did). 

Intel chips aren't useless, it's solid hardware that does what it needs to quite well. It's great that the drivers are open as it helps Linux on laptops (re: Centrino, Viiv) and lower end desktops but sadly has no bearing on the high end market.

---

### Post by poofyhairguy on 2006-08-10
> **petervk said:**
> 

Didn't intel already have opensource drivers? 

Yes. And Intel has been hiring some big names in the Xserver world over the past few years (including the biggest one in Xorg's recent history- Keith Packard.

> 
Is this a release of previously unavailable code? 

Mostly for the upcoming GMA3000. 

> 
How mature are these drivers?

I don't think anyone has a GMA3000 to test, but my GMA950 (the current top offering) can run XGL (and the rain effect-something Nvidia 5200FXs have trouble with) without problems.
 
> 
Are these drivers competely free of any non-free binary blobs or code?

I think so. So far they have been.

> 
Is this finally something to compete with the Radeon 9200?

Already the GMA950 is more than competition for the 9200. It has features the 9200 does not (advanced Pixel Shaders). The GMA3000 should blow a 9200 away if Intel gets half of their promises with it right.

> 
Will this finally be a way to compete with Nvidia's OpenGL hardware acceleration?

Not on the high end.

---

### Post by BoyOfDestiny on 2006-08-11
Sorry if this has been posted before.

[http://lwn.net/Articles/194724/](http://lwn.net/Articles/194724/)

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

Anyway, now I'd hope they release standalone cards... Although if I build a new machine, there is a chance there may be an intel chipset. 

It would be nice if AMD and Ati would follow suit...

---

### Post by s6dalane on 2006-08-11
There is a thread about this [here]("http://www.ubuntuforums.org/showthread.php?t=233105&highlight=intel+graphics+driver"). :)

---

### Post by prizrak on 2006-08-11
> How mature are these drivers?
According to Intel not very they did say that this is the first revision and as any first revision will require some tweaking. Also the chipset isn't around in the real world yet so of course that will uncover some issues that didn't show up in the lab.

---

### Post by timfelgentreff on 2006-08-12
Am i the first one to ask this? When do we get a package in the repository? I  have an i915GM and as far as I've understood this, the current X.org drivers only have limited support for the i9xx series (as thy were originally written for the i8xx series)
Cheers!

---

### Post by prizrak on 2006-08-13
> **timfelgentreff said:**
> Am i the first one to ask this? When do we get a package in the repository? I  have an i915GM and as far as I've understood this, the current X.org drivers only have limited support for the i9xx series (as thy were originally written for the i8xx series)
Cheers!

Probably not till it makes it into Edgy. Remember each Ubuntu version is frozen after it is released, so no new features are introduced. There is a backports project that will introduce newer software if it doesn't break anything.

---

### Post by kripkenstein on 2006-08-13
Personally, I don't play 3D games very much these days. So if this new offering by Intel will be sufficient to run XGL, I will certainly buy it. Since it's open source, it should be more stable than NVidia and ATI products - eventually, at least. So, I think this is (the continuation of) very good policy at Intel.

In fact, it might even convince me to buy a Core 2 Duo - open-source graphics drivers for the accompanying chipset are that important to me. I've bought AMDs in recent years, so this might break that trend... unless AMD do something smart after buying ATI :)

---

### Post by Hotaru on 2006-08-13
No open graphics driver from AMD... sorry guys :(.
[http://www.osnews.com/story.php?news_id=15472]("http://www.osnews.com/story.php?news_id=15472")

---

### Post by ubuntu_demon on 2006-08-13
Don&#8217;t buy a videocard from ATI/AMD
They are not going to open source their drivers.

There are lots of people who have a lot of trouble to get ATI&#8217;s proprietary drivers working properly. Check out the Video and Sound section.

[http://ubuntudemon.wordpress.com/2006/08/13/dont-buy-atiamd](http://ubuntudemon.wordpress.com/2006/08/13/dont-buy-atiamd)

---

### Post by bjweeks on 2006-08-13
> **ubuntu_demon said:**
> Don’t buy ATI/AMD
They are not going to open source their drivers.

[http://ubuntudemon.wordpress.com/2006/08/13/dont-buy-atiamd](http://ubuntudemon.wordpress.com/2006/08/13/dont-buy-atiamd)

Thats like saying don't buy a Ford they use gas.

---

### Post by ubuntu_demon on 2006-08-13
> **bjweeks said:**
> Thats like saying don't buy a Ford they use gas.
There are lots of people who have a lot of trouble to get ATI&#8217;s proprietary drivers working properly. Check out the Video and Sound section.

---

### Post by bjweeks on 2006-08-13
> **ubuntu_demon said:**
> There are lots of people who have a lot of trouble to get ATI’s proprietary drivers working properly. Check out the Video and Sound section.

I know :( Just the way you worded it :neutral:

Edit: Plus there is always hope for my ATI 9800 :roll:

---

### Post by zenwhen on 2006-08-13
I'll never buy an ATI card until their drivers compare on some level to Nvidia's.

This was a great move by Intel, but niether ATI or NV will be open sourcing their drivers any time soon. 

With Nvidia, this only poses a moral issue, since their drivers are pretty nice. With AMD, this poses both a technical issue and a moral issue. ATI doesn't seem to be able to fix their drivers and it would be nice if the open source community could do it for them.

---

### Post by ubuntu_demon on 2006-08-13
> **bjweeks said:**
> I know :( Just the way you worded it :neutral:

Edit: Plus there is always hope for my ATI 9800 :roll:
I've rephrased the blog post a little.  It is my **personal** opinion. I advise people not to buy ATI/AMD videocards.

---

### Post by ubuntu_demon on 2006-08-13
> **zenwhen said:**
> I'll never buy an ATI card until their drivers compare on some level to Nvidia's.

This was a great move by Intel, but niether ATI or NV will be open sourcing their drivers any time soon. 

With Nvidia, this only poses a moral issue, since their drivers are pretty nice. With AMD, this poses both a technical issue and a moral issue. ATI doesn't seem to be able to fix their drivers and it would be nice if the open source community could do it for them.
I fully agree.

Let's make some noise together. Let's not buy ATI. Let's recommend the new intel chipset to non-gamers. Let's recommend NVIDIA to gamers only.

---

### Post by zenwhen on 2006-08-13
> **ubuntu_demon said:**
> I fully agree.

Let's make some noise together. Let's not buy ATI. Let's recommend the new intel chipset to non-gamers. Let's recommend NVIDIA to gamers only.
I'll also have to recommend Nvidia to anyone who wants decent XGL performance or decent dual head support.

---

### Post by ubuntu_demon on 2006-08-13
> **zenwhen said:**
> I'll also have to recommend Nvidia to anyone who wants decent XGL performance or decent dual head support.
I hope the motherboards with that new chipset come with dualhead.
I imagine the new intel driver will have decent XGL and dualhead(if available) support

---

### Post by imagine on 2006-08-13
Update:

[http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2](http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2)
> **petervk said:**
> Are these drivers competely free of any non-free binary blobs or code?
The driver is not completely free. According to the developers there will be a binary blob in the userspace, containing stuff like content protection (note to self: DRM is the spawn of all evil). This binary blob doesn't exist yet and the driver also works without it. However then some functions won't be available of course.

This sucks but I'm afraid there's nothing developers can do about it, since opensourcing DRM algorithms renders them useless: The whole point of DRM is stopping the user from things he wants to do and forcing him into things he doesn't want. If the user then gets access to the sourcecode of the DRM functions he will simply comment them out and thereby getting rid of them.

---

### Post by bjweeks on 2006-08-13
Well in theory you could have open source DRM.

---

### Post by petervk on 2006-08-13
Open source DRM? Sorry, but that is just stupid. DRM is a bad idea no matter the implementation.

IMO.

---

### Post by bjweeks on 2006-08-13
> **petervk said:**
> Open source DRM? Sorry, but that is just stupid. DRM is a bad idea no matter the implementation.

IMO.

That is in the eye of the beholder.

---

### Post by prizrak on 2006-08-13
> **bjweeks said:**
> Well in theory you could have open source DRM.

Well sure the software itself could be FOSS but the keys still have to be closed so it won't be very FOSS. DRM is not a horrible idea (from a standpoint of the owner of IP) but the implementation is broken. So far it hurts the legal user alot more than the illegal one.

---

### Post by slimdog360 on 2006-08-22
I dont know if this has already been posted or not, I tried searching the fourms but couldn't find anything. So sorry in advance if it has.


[http://www.linuxworld.com.au/index.php?id=141452509&eid=-50]("http://www.linuxworld.com.au/index.php?id=141452509&eid=-50")

"With the release of the G965 drivers, Intel hopes to enter into the Linux market. Already, the release has received some very positive feedback."

Without doubt it would.


edit: Could a mod fix the title. thanks :)

---

### Post by ewaguespack on 2006-08-24
sooo... as far as actual products using these drivers with the "4th gen" video features, is this the only mobo currently on the market?


[http://www.newegg.com/Product/Product.asp?Item=N82E16813121048](http://www.newegg.com/Product/Product.asp?Item=N82E16813121048)

Further, I guess it is a silly question to ask how one would go about configuring dual head with this hardware / drivers... (since there is only one port, and no stand-alone cards...)

---

### Post by ubuntu_demon on 2006-08-25
I found a (unconfirmed) list of hardware which will work with this new driver here : [http://www.digitalcitizen.info/2006/08/10/is-intels-965-chipset-going-to-be-your-next-video-hardware/](http://www.digitalcitizen.info/2006/08/10/is-intels-965-chipset-going-to-be-your-next-video-hardware/)

can somebody confirm it or find this information on the intel site ?

Hardware Support Matrix
[http://www.intellinuxgraphics.org/user.html](http://www.intellinuxgraphics.org/user.html)

---

### Post by ubuntu_demon on 2006-08-25
Here's a review of "Conroe&#8221; but now goes by the names Core 2 Duo and Core 2 Extreme : [http://www.linuxhardware.org/article.pl?sid=06/08/22/0415251&mode=thread](http://www.linuxhardware.org/article.pl?sid=06/08/22/0415251&mode=thread)

Will all intel chipsets with integrated graphics designed for this Core 2 be able to run this new graphics driver ?

Does anybody know whether they will also release non-G65 chipsets designed for the Core 2 with integrated graphics ?

---

### Post by ubuntu_demon on 2006-08-25
> **imagine said:**
> Update:

[http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2](http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2)

The driver is not completely free. According to the developers there will be a binary blob in the userspace, containing stuff like content protection (note to self: DRM is the spawn of all evil). This binary blob doesn't exist yet and the driver also works without it. However then some functions won't be available of course.

This sucks but I'm afraid there's nothing developers can do about it, since opensourcing DRM algorithms renders them useless: The whole point of DRM is stopping the user from things he wants to do and forcing him into things he doesn't want. If the user then gets access to the sourcecode of the DRM functions he will simply comment them out and thereby getting rid of them.
from [http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2](http://marc.theaimsgroup.com/?l=linux-kernel&m=115536806403908&w=2) :

> 
On Wed, 2006-08-09 at 23:21 -0700, Nicholas Miell wrote:

> More importantly, where's the source to intel_hal.so?

This module contains stuff which Intel can't publish in source form,
like Macrovision register stuff and other trade secrets. It's optional,
so if you don't want to use a binary module, you don't get to use code
written by Intel agents for these features. And, we also haven't figured
out how and when to release this binary blob, so there's no way you can
use it today. The driver remains completely functional in the absense of
the binary piece, and in fact has no reduction in functionality from
previous driver releases.

One important note -- the interface for the binary module exists only in
user-mode code which is licensed under the MIT license, not the GPL.

--=20
[email]keith.packard@intel.com[/email]


---

### Post by curuxz on 2006-08-25
This is great news, well done to Intel for opensourcing drivers!

My laptop uses one of their extream mobile graphics cards, and by default in kubuntu I have 2d and 3d working perfectly out of the box :)

---

### Post by kopinux on 2006-08-25
has this been posted before?
anyone confirm?

> Lastly, and remember you heard it here, AMD is strongly considering open-sourcing at least a functional subset of ATI’s graphics drivers. It’s time for X Window System, OpenGL, and client virtualization for which ATI binary drivers aren’t available to escape the ghetto of the 1980s-era framebuffer. And what a boon for PR. If AMD’s graphics cards were the only ones with open device drivers, it might affect a buying decision or two.
[infoworld]("http://www.infoworld.com/article/06/08/02/32OPcurve_1.html")

---

### Post by jwl007 on 2006-08-29
I hope these drivers are included in the upcoming release of Ubuntu.  I and many other Ubuntu enthusiasts have had a hard time dealing with (somewhat) older laptops using intel integrated cards.    The main issue I had (am having) is a shared memory bios and intel i810 problem (see: Gateway m305crv).   I haven't tried compiling the new *nix intel driver yet ([http://intellinuxgraphics.org/index.html)](http://intellinuxgraphics.org/index.html)), but this definitely sounds promising, and sounds like something many Ubuntu enthusiasts need.
-jwl007

---

### Post by Clogger on 2006-09-07
jwl007, I am in the same situation as you are regarding Intel i810.  Have you, or anyone else, tried to compile this yet?

A step by step how to would be a "gift".

Thanks in advance guys.

Cloggs.

---

