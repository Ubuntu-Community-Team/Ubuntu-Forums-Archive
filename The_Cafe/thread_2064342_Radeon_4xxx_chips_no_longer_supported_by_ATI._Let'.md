---
title: "Radeon 4xxx chips no longer supported by ATI. Let's start a petition."
date: 2012-09-29
forum: The Cafe
---

### Post by DisappearingOak on 2012-09-29
People, the open source driver is not fast enough. So all of those of us who have these 4xxx chips are left hanging without fglrx since ATI has dropped support for them. I made a big mistake getting a board with a radeon chip. Sick. I hope someone starts a petition. What say you.

---

### Post by MadCow108 on 2012-09-29
can't you just use the old drivers?
if new xorg is an issue, why must you use the newest of the new software with legacy hardware?

so far I know 12.04 still has support for the cards, that gives you 5 years to update your hardware or to improve the open source drivers to your liking.

---

### Post by DisappearingOak on 2012-09-29
> **MadCow108 said:**
> can't you just use the old drivers?
if new xorg is an issue, why must you use the newest of the new software with legacy hardware?

so far I know 12.04 still has support for the cards, that gives you 5 years to update your hardware or to improve the open source drivers to your liking.

I own a 4250 and this is not supposed to be legacy hardware. ATi still supports it in Windows 8, but they have dropped "Linux" support much to our chagrin.

---

### Post by neu5eeCh on 2012-09-29
> **DisappearingOak said:**
> People, the open source driver is not fast enough. So all of those of us who have these 4xxx chips are left hanging without fglrx since ATI has dropped support for them. I made a big mistake getting a board with a radeon chip. Sick. I hope someone starts a petition. What say you.

Petition? Complete, utter, total, consummate, perfect, absolute waste of time. They want your money, not your petitions. Get enough Linux users together, donating $10,000 each, and then maybe you will get their attention.

It's tempting to write that if you want want speedy, reliable, supported and long term high end graphics performance in Linux, use Windows; but my understanding is that both AMD and NVIDIA **do** offer proprietary drivers in Linux with good performance (for how long and how it measures up to Windows or Apple is the question).

Personally, I think the Linux world would be far better served making the switch to Wayland (rather than petitioning graphics companies).

---

### Post by mips on 2012-09-29
> **VTPoet said:**
> 
Personally, I think the Linux world would be far better served making the switch to Wayland (rather than petitioning graphics companies).

It's coming and will eventually happen but the opensource drivers still don't deliver the same level of performance yet. I reckon another 1-3 yrs and we will all be using wayland & opensource drivers.

I think I should go and try the nouveau drivers again just to see how they fare....

---

### Post by angryfirelord on 2012-09-29
Petitions don't do anything since a petition isn't much more than someone complaining on a message board. AMD implemented this short 3-year life cycle because they want you to continually buy their newest cards. If you want decent support for open-source graphic drivers, Intel is your best bet at this point.

That said, you can still use the Catalyst driver in the repositories for 12.04. The default one won't change for the life cycle of Precise.

---

### Post by neu5eeCh on 2012-09-29
> **mips said:**
> It's coming and will eventually happen but the opensource drivers still don't deliver the same level of performance yet. I reckon another 1-3 yrs and we will all be using wayland & opensource drivers.

I think I should go and try the nouveau drivers again just to see how they fare....

Just noticed that a [new Wayland CD, using Ubuntu 12.10]("http://www.phoronix.com/scan.php?page=news_item&px=MTE1Nzc"), was released in August.

---

### Post by DisappearingOak on 2012-10-02
> **VTPoet said:**
> Just noticed that a [new Wayland CD, using Ubuntu 12.10]("http://www.phoronix.com/scan.php?page=news_item&px=MTE1Nzc"), was released in August.

Will open source drivers on Wayland perform better than on X? What about performance of Gnome Shell. And 3d games?

---

### Post by neu5eeCh on 2012-10-02
> **DisappearingOak said:**
> Will open source drivers on Wayland perform better than on X? What about performance of Gnome Shell. And 3d games?

Okay, answering this question is *way* above my pay grade, but my understanding is that, yes, open source drivers will perform better on Wayland, but closed source drivers will not (and will _not work at all_). In theory though, any new closed source drivers should work better with Wayland.

Here are three useful links:

[WIkipedia]("http://en.wikipedia.org/wiki/Wayland_(display_server_protocol)") 
[Jeff Hoogland]("http://jeffhoogland.blogspot.com/2010/11/wayland-vs-x-some-perspectives.html")
[Why is Wayland Better]("http://askubuntu.com/questions/11537/why-is-wayland-better")

---

### Post by mips on 2012-10-02
> **DisappearingOak said:**
> **Will open source drivers on Wayland perform better than on X?** What about performance of Gnome Shell. And 3d games?

My logic says not really seeing they both still use the same underlying driver. X probably has more layers to it which would make it slightly slower but I don't see the actual drivers improving in performance between the two.

---

### Post by FlameReaper on 2012-10-02
For the record, especially for users running newer kernels (I suppose starting from 3.3 and above), AMD's drivers break a lot to the point you *have* to use updated drivers from AMD's own site and not from repositories, if you still want to run the newer kernel AND not break the current AMD driver in your machine. And by "breaking" I'm saying that DKMS has troubles building the driver modules for these newer kernels (and I've been having this kind of problem a lot).

Sure, this is no problem if you stick to the stock kernels supplied by Ubuntu's repositories, but in the long run, this will pose a problem especially as kernel versions get one step higher.

For me, not only the OSS drivers aren't fast enough (though I never bothered to run anything past desktop composition and effects), they cause increased operating temperatures for the GPU (+ ~10°C in my case) and I can't accept that running in my system.

But then again, I'm neither against nor am I for any kind of petition. Jokingly speaking, we should already be able to know that this is one of the hints a hardware maker is giving users to start upgrading their hardware (much to our own chagrin and against our protest of not wanting to). While they might hear it's still up to them to decide.

---

### Post by AllRadioisDead on 2012-10-02
Let's Riot!

---

### Post by alzen on 2013-05-03
I totally agree! I have X1950 XT card, and it is enough for me. Why shouldn't I be able to use it with the newest Xorg with fglrx? Currently I use open source radeon driver.

I think petition is an awesome idea.

---

### Post by mips on 2013-05-03
And this should be another reason not to buy AMD/ATI. They don't support their cards for very long. The HD 4xxx cards came out in 2008, nVidia still supports their GeForce 6 series cards that came out in 2004!!!

---

### Post by DisappearingOak on 2013-05-03
The petition thing was actually a joke. I doubt that would actually have any effect. The Radeon IGPs were actively sold on mainstream boards in March 2012, I used mine to play Source games. The discrete cards in the series are still powerful enough to run just about any modern games at high settings. Hardware that actively sold just a couple years back. They just declare it legacy and refuse to at the very least update it to newer X versions. What point is there then in buying AMD when you get driver support for such a short time.   My next machine will be an Intel when I buy it in a few years.

---

### Post by EgoGratis on 2013-05-03
If you want to make a difference report bugs and do campaigns for the FOSS driver because improved FOSS driver is what you really need for this hardware and don't say you cant make a difference sure you can!

---

### Post by mips on 2013-05-03
> **DisappearingOak said:**
> The petition thing was actually a joke. I doubt that would actually have any effect.

I agree, won't get you anywhere.


> **EgoGratis said:**
> If you want to make a difference report bugs and do campaigns for the FOSS driver because improved FOSS driver is what you really need for this hardware and don't say you cant make a difference sure you can!

For the foreseeable future I don't see any open source drivers catching up to the proprietary ones, they will always lag behind.

---

### Post by EgoGratis on 2013-05-03
> For the foreseeable future I don't see any open source drivers catching up to the proprietary ones, they will always lag behind.

Wait a second where exactly does FOSS "Radeon 4xxx chips driver" lag behind the blob? You got it wrong didn't you it's the other way around this time. And i don't see the blob catching up in foreseeable future. And yes basically everybody can make a difference when it comes to FOSS don't set some artificial barriers that don't exist.

---

### Post by Paqman on 2013-05-03
I suspect he's talking about performance, EgoGratis, rather than support for individual cards.

---

### Post by codingman on 2013-05-03
I don't see why people dislike NVIDIA, they have great Linux support, even though debates are everywhere. Nouveau is great. AMD/ATI cards have never been my choice, because I tried installing Ubuntu on an ATI system, and ended up with graphic errors. I tried everything, but I gave up, and stuck with NVIDIA from then on.

---

### Post by EgoGratis on 2013-05-03
> I suspect he's talking about performance, EgoGratis, rather than support for individual cards.

I see in areas where FOSS driver does better job it's not important we should only limit ourselves to situation where blob supposedly does something better and performance is or should be the only one variable in the game? AFAIK majority of desktop users couldn't care less about little bit more or less performance they just want their desktop to work and FOSS drivers does generally speaking better job at this and blobs will probably lag behind for foreseeable future.

What i am trying to say is yes anybody can make a difference and no giving some vague statements how blobs are superior in all aspect and FOSS drivers are always catching up is plain wrong.

---

### Post by EgoGratis on 2013-05-03
And i doubt if AMD would change their mind and offer the blob again for this cards that they would put much effort in performance area. They would probably just make it compatible with never Xorg server every once in a while. I doubt they would do much bug fixing too... 

In the end it would probably end up in a way some users would install the blob "just because" they probably heard somewhere blob is "always better" and FOSS driver "is always catching up" ...

---

### Post by DisappearingOak on 2013-05-03
Performance is one aspect of it. The majority of desktop users who you say care less about 3d performance probably don't even own any new hardware. There is no point in buying new hardware with faster and more powerful performance and feature set if you can't leverage it to it's full potential and are stuck with 'barely getting by' community managed drivers. If I buy hardware, I expect support for at least a reasonable number of years, not to have the company selling the product today through licensed motherboard vendors, and in just two years or even three years make it impossible for you to use recent software. Some users do need the 'blob' to avoid issues with power management, overheating, even if you are willing to stick with lower performance. I tend to be a free software purist where I can be, but in the current situation, the foss drivers are not optimal for all users. I have had overheating issues and lots of rendering latency on the free driver, so I cannot use KDE, I cannot use Unity, Gnome runs but there are issues. AMD's policy is not very good or convenient for Linux platform. I have made up my mind to avoid any graphics products from them in the future. CPU-wise, AMD is still bang-for-buck. Intel is too costly for same amount of beef.

---

### Post by EgoGratis on 2013-05-03
> 'barely getting by' community managed  drivers

> If I buy hardware, I expect support for at least a reasonable  number of years, not to have the company selling the product today  through licensed motherboard vendors, and in just two years or even  three years make it impossible for you to use recent software.

You do know that AMD officially supports FOSS driver and the only "community managed " driver on the desktop is nouveau? Therefore you can still say you have official support from AMD.

> I tend to be a free software purist where I can be, but in the current  situation, the foss drivers are not optimal for all users. I have had  overheating issues and lots of rendering latency on the free driver, so I  cannot use KDE, I cannot use Unity, Gnome runs but there are issues.  AMD's policy is not very good or convenient for Linux platform. I have  made up my mind to avoid any graphics products from them in the future.  CPU-wise, AMD is still bang-for-buck. Intel is too costly for same  amount of beef.

Let's be honest and say currently AMD is just not the best company when it comes to drivers and it has less to do with blobs vs. FOSS. But i will say it again if you want to make any (small) difference in foreseeable future for your hardware your best bet is FOSS driver and not the blob.

---

### Post by EgoGratis on 2013-05-03
Maybe AMD should drop blobs for more GPUs and focus more on FOSS driver. Like Intel for example where things are great.

Then stuff like improving power management and performance increase would happen sooner. Think again what campaign you would really want to be running...

---

### Post by codingman on 2013-05-03
I have had horrible results with AMD drivers.

Point: I'm glad they dropped it, cause they'd probably screw it up eventually. Leaving it to the community was a better idea, as new series' start to come in.

---

### Post by EgoGratis on 2013-05-04
Yes actually i agree and i do believe FOSS driver from AMD has much better chance to become something that works OK and users like to use. I don't think the blob will be there anytime soon.

It will be interesting to see what happens after Intel next gen GPUs that will supposedly be from 2 to 3 times faster than current generation ones and will have great FOSS driver right from the start. I think AMD should follow this road if they want to stay competitive because their blob will be much less attractive compared to Intel and if Intel GPUs will allow playing games on Steam in good quality...

---

### Post by codingman on 2013-05-04
I don't exactly think this thread is getting anywhere, it was resurrected from September.

---

### Post by EgoGratis on 2013-05-04
I agree. But at least now we and especially OP are aware OP already has what he wants/needs.

And that in the end is something. We made a difference in at least the awareness!

---

### Post by forrestcupp on 2013-05-04
I still have an HD 2600 lying around somewhere. I still think of the 4xxx series as being new. :)

---

### Post by alzen on 2013-05-04
@forrestcupp

As I said, I have X1950 XT. And it's still new to me. Some users just know their needs and they don't need to use the latest cards to have fun with their computers.

@codingman

Doesn't matter; AMD's behaviour in that matter is unacceptable. How can they force people to buy new products this way?!

I will use open source driver, it's crazy to me that such a big company doesn't care about such large amount of their users. Of course we are smaller group than MS products users but still.

And seriously, a petition will probably not change anything; but it won't hurt anyone either. I will sign it if it's online.

---

### Post by EgoGratis on 2013-05-04
But is it true they don't care about us AFAIK they do support FOSS driver? That is good enough for me to be honest and it doesn't make much sense to put blobs on older hardware as long FOSS driver does it's job OK.

It's actually easier to use FOSS driver in my opinion and i do believe majority of users prefers it over blob as long it does it's job OK.

---

### Post by alzen on 2013-05-04
Of course it does and I really doubt they help at all; that's why open source driver still has some rendering bugs and lacks performance when compared to catalyst I guess.

To be honest I don't want them to put their fingers into open source driver; they've done so much for all these years for us and all I can say to them is "Stay away from one good driver, please".

Still, I want them to do their job and support all the major models, not only the latest one. It's always good to have and alternative and I wouldn't complain if I can use fglrx as I suppose I will gain performance in games.

---

### Post by codingman on 2013-05-04
They are not forcing Linux users to buy new products, but to rather make us use our own drivers, which are much better in the first place.

Why don't you try NVIDIA? I have never had any problems with their proprietary drivers, or nouveau.

---

### Post by RJARRRPCGP on 2013-05-04
I agree that this is ridiculous! It's not an 8500 for cryin' out loud!

---

### Post by codingman on 2013-05-04
To be honest, if you want fglrx or game acceleration, I wouldn't use the AMD 4xxx series. ATI went down in quality after AMD bought it. They were more business motivated.

---

### Post by alzen on 2013-05-04
Hmm, not at all. If they want the community to develop the driver they wouldn't write any linux driver and rather share the important information that would make it easier to write good driver so community could've done it earlier. And yes, in my opinion they partly want users to upgrade more often.

Community driver isn't what AMD wants us to do. Community driver is the reaction to AMD's behaviour. And yes, it's good for AMD that community driver is there so they can always tell "you have good community driver" or "we wouldn't be able to give you better driver than the community one". Still, it's also good for users as AMD doesn't give a f*ck.

And why didn't I use NVidia? I did for quite some time. But after a while I got a good price on ATI card and bought it, it's much more faster than my NVidia card. I read about open source driver so I tried to use ATI for the second time. I'm satisfied with community driver, still, AMD's behaviour is totally not right.

---

### Post by EgoGratis on 2013-05-04
I don't think it's correct AMD doesn't want to be involved in development of FOSS driver. AFAIK they help develop it and for example this is just one of their latest nice things implemented in FOSS driver:

[http://www.phoronix.com/scan.php?page=news_item&px=MTM2MTE](http://www.phoronix.com/scan.php?page=news_item&px=MTM2MTE)

They sponsored implementation of OpenCL in GIMP if i am not mistaken and that is something that goes beyond just developing FOSS driver for their cards and that is why i said it not just about performance in the end it's much more to it performance being just one of the aspects.

---

### Post by codingman on 2013-05-04
Be glad they are still supporting the new ones! They could have left Linux in the dust!

---

### Post by EgoGratis on 2013-05-05
> **codingman said:**
> Be glad they are still supporting the new ones! They could have left Linux in the dust!

No i don't think they could afford that. Linux market is to important for any big hardware company these days. And they actually support "new ones" and "old ones" with FOSS driver.

---

### Post by JasonGriffee on 2013-05-09
I don't agree with major product life-spans. I feel that 3 years is plenty. When Linux goes mainstream (Wait for it, it will happen) devs will be pushing all there games on to it. Do you think it is fair for them to have to program for a card's hardware, when it's 5+ years old? I don't. Developers need a resonable amount of hardware to work with, so they can be free to create, rather then worry about performance on a card owned by someone who refuses to upgrade.

---

