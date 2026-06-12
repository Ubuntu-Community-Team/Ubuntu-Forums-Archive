---
title: "How are the ATI drivers doing these days?"
date: 2009-10-20
forum: The Cafe
---

### Post by AllRadioisDead on 2009-10-20
Hey guys, I built a new rig last december with an HD 4850 GPU. I soon realized that the ATI proprietary drivers are less than impressive, not performing well and spitting out artifacts all over the place when compiz or a game starts. Since then I've kept Ubuntu on my laptop, and I'm looking to install Ubuntu back on my desktop once Karmic rolls out. I'm just wondering if any progress has been made. If not, I'll probably craigslist my ATI card and go on the hunt for a Nvidia card.

---

### Post by JDShu on 2009-10-20
Word on the street is that the catalyst drivers have had tremendous improvement. The open source drivers are also developing rapidly, and many people (forum goers) speculate that there will be decent 3D support in maybe half a year. However, I don't think ubuntu forums is a good place to ask and if I were you, I would lurk around the Phoronix forums where the people are far more knowledgeable. (it seems to be a popular place for the ati open source driver devs to hang around haha)

---

### Post by NoBugs! on 2009-10-20
That would probably depend on what Linux version you are using. The latest versions (2.6.30 and 2.6.31) mention some improvements to ATI compatibility:
[http://kernelnewbies.org/Linux_2_6_31](http://kernelnewbies.org/Linux_2_6_31)
[http://kernelnewbies.org/Linux_2_6_30](http://kernelnewbies.org/Linux_2_6_30)

---

### Post by AllRadioisDead on 2009-10-20
Thanks, maybe I will be impressed when I make it back. 
I'm just kind of on the fence right now about buying a Nvidia card or just take a leap of faith and hope that the ATI drivers improve.

---

### Post by JDShu on 2009-10-20
They will most certainly improve, but it  depends on how patient you are :)

---

### Post by JDShu on 2009-10-20
btw, you may find this interesting:

[http://xorg.freedesktop.org/wiki/RadeonProgram](http://xorg.freedesktop.org/wiki/RadeonProgram)

---

### Post by AllRadioisDead on 2009-10-20
> **JDShu said:**
> btw, you may find this interesting:

[http://xorg.freedesktop.org/wiki/RadeonProgram](http://xorg.freedesktop.org/wiki/RadeonProgram)
Thank you, bookmarked. I will have to try both drivers in couple of weeks.:P

---

### Post by starcannon on 2009-10-20
XV support is still a pita.

---

### Post by misfitpierce on 2009-10-20
Major improvements with them. The opensource ones have gotten better as well which is what I use now. I think they will both (fglrx prop, and opensource) keep getting better. But yeah there have been improvments that I have seen and am pretty happy.

---

### Post by handy on 2009-10-20
> **ihermit said:**
> Hey guys, I built a new rig last december with an HD 4850 GPU. I soon realized that the ATI proprietary drivers are less than impressive, not performing well and spitting out artifacts all over the place when compiz or a game starts. Since then I've kept Ubuntu on my laptop, and I'm looking to install Ubuntu back on my desktop once Karmic rolls out. I'm just wondering if any progress has been made. If not, I'll probably craigslist my ATI card and go on the hunt for a Nvidia card.

It is an interesting time as far as the ATi GPUs are concerned:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

***[Edit:]** There are a number of worthwhile links at the end of the first post of the above linked to thread.*

---

### Post by taavi on 2009-10-20
> **ihermit said:**
> Thanks, maybe I will be impressed when I make it back. 
I'm just kind of on the fence right now about buying a Nvidia card or just take a leap of faith and hope that the ATI drivers improve.

I was in the situation like you more than half a year a go. I hadn't had any experiences with catalyst drivers and thought how bad can it be... But situation right now is quite awful. I can't list everything that has been bothering me, but to mention few -- everything hands when you start second X (like switch user). I tried to play Braid over wine few days ago and it left me with ****** up resolution where i couldn't do anything but boot several times and reset my configuration. I enabled radeon drivers at the end to go to sleep... 

But still I have my hopes up, that those free drivers will be blast...

ATI is doing best in their minds, but not with those busy hands.

I have HD3875 card -- will it have those new free drivers too?

---

### Post by Exodist on 2009-10-20
They have got alot better. But I will say that 2.6.31 kernel has been out over a month and I am still stuck using 2.6.30 since cat 9.10 drivers have not been released. But from what I was told nVdias drivers are not out for that kernel yet also..  

Way it stands right now.

ATI: Runs Cooler and last long time for the user hardware wise.
NV: Runs HOT and doesnt seem to last as long (I burned up 3 past 2 years).
ATI: Drivers are good on Linux but dont perform anywhere as good as the win drivers.
NV: Drivers perform top notch.

So IMHO its a trade off on both ends.

---

### Post by OmegaAI on 2009-10-20
Since the 8.x series they have become SO much better

---

### Post by K.Mandla on 2009-10-20
> **taavi said:**
> But situation right now is quite awful. I can't list everything that has been bothering me, but to mention few ... 
Hmm. My experience has been completely opposite, but I haven't been using anything newer than four or five years old, technologywise. I've been quite pleased with the way drivers have improved, considering that four years ago, I could barely get X working with a Radeon XPress 200M. Now that card gets full acceleration, by default, with no more than an extra click or two.
> **misfitpierce said:**
> Major improvements with them. The opensource ones have gotten better as well which is what I use now. I think they will both (fglrx prop, and opensource) keep getting better. But yeah there have been improvments that I have seen and am pretty happy.
Me too. I'd probably buy an ATI card over an Nvidia one now, considering the way things are moving.

---

### Post by taavi on 2009-10-20
> **K.Mandla said:**
> I've been quite pleased with the way drivers have improved, considering that four years ago, I could barely get X working with a Radeon XPress 200M. Now that card gets full acceleration, by default, with no more than an extra click or two.OFC you are pleased when you can use your computer, but what I would like more is the feeling of safety -- an emotion that I do not have while using ATI drivers atm. Lockups are awful and they are not uncommon when you start messing around with something more that just surfing web and listening to music, watching movies. I would tolerate it more, if I could switch to console and kill died X, but usually all the user interface hangs blank. 

But I'm happy to hear that things are moving...

---

### Post by Xbehave on 2009-10-20
I use radeon drivers and have for over a year. Excluding a small period when modesetting was enabled they have been rock solid (with KMS a firefox bug could trigger a pretty nasty bug). 
[LIST]
[*]For everyday use they are great, for compiz/effects not so fast (e.g i can use KDE4's effects but stuff is a bit more sluggish)
[*]When it comes to 2D they are faster than catalyst
[*]when it comes to 3D they are not too good
[/LIST]

If you don't care about compiz/effects and don't play 3D games, then radeon drivers are a safe bet, 
If you need your compiz then give them a try but you will probably end up moving to catalyst
If you play 3D games then you will need catalyst

---

### Post by ublintu on 2009-10-20
Hi K.Mandla,

I have the same card (ati 200m). Please tell me how did you do that, how did you get full acceleration? Is it working in Karmic too?

---

### Post by gnuvistawouldbecool on 2009-10-20
> **ublintu said:**
> Hi K.Mandla,

I have the same card (ati 200m). Please tell me how did you do that, how did you get full acceleration? Is it working in Karmic too?

In Karmic, the x200m runs nicely.  glxgears reports about 500-600 fps, and I've got armagetronad working.  I'm currently about to test Extreme Tux Racer.*

I've had it run Compiz since 8.10 (with proprietary drivers), and in 9.04 (with free ones).  However, 3D games didn't work in 9.04...

Actually, I'm reconsidering my hate for ATi's linux support. which I thought I wouldn't for a long time.

Edit: not sure about the current state of compiz support, since I use KDE/Openbox.  *Works, but with glitches.  Something weird happens with it's Skybox, but is playable at around 30fps on 800*600.

---

### Post by ublintu on 2009-10-20
Yes I have/had the same experience since 7.10, 8.04, ..long break.. , return to ubuntu 9.04. 
I`m thinking to make a clean install with Karmic 9 days later, but until that I want to collect all of the experiences with 200m and hopefully this time I wont have any serious problem with it. How did you install it? Can you tell me, can you post the link?
Thank you

---

### Post by gnuvistawouldbecool on 2009-10-20
> **ublintu said:**
> Yes I have/had the same experience since 7.10, 8.04, ..long break.. , return to ubuntu 9.04. 
I`m thinking to make a clean install with Karmic 9 days later, but until that I want to collect all of the experiences with 200m and hopefully this time I wont have any serious problem with it. How did you install it? Can you tell me, can you post the link?
Thank you

My expeience posted previously is with the default Kubuntu 9.10 Beta install.  No drivers were added by me, and I got 3D acceleration.  That easy.

---

### Post by ublintu on 2009-10-20
mmmm sounds good. Thank you

---

### Post by AllRadioisDead on 2009-10-21
I actually just installed Karmic yesterday, I downloaded the fglrx drivers via the restricted drivers manager, and I'm still getting artifacts like crazy when gnome compiz starts or I launch a wine app. Sigh.

---

### Post by Nerd King on 2009-10-21
Don't forget it's beta. Once the final Karmic comes out it should be better. I've found proprietary NVIDIA and ATI drivers to cause lock-ups and it seems the open-source drivers are much more stable at this point.

---

### Post by Nerd King on 2009-10-21
Btw seriously Karmic has to be the worst beta yet in terms of stability. I mean when it's working it's a thing of beauty, really fast, polished, beautiful. But by god does it have a nice collection of bugs.

---

### Post by AllRadioisDead on 2009-10-21
> **Nerd King said:**
> Don't forget it's beta. Once the final Karmic comes out it should be better. I've found proprietary NVIDIA and ATI drivers to cause lock-ups and it seems the open-source drivers are much more stable at this point.
More stable perhaps, but I play a fair amount of games, I'm not sure how good the open source drivers are in terms of performance.

---

### Post by handy on 2009-10-21
> **ihermit said:**
> More stable perhaps, but I play a fair amount of games, I'm not sure how good the open source drivers are in terms of performance.

The ATi open-source related packages are getting a lot of work done on them.  This has been motivated by the poor quality & unreliable results with each upgrade of the proprietary packages.

Over the coming year 3D support provided by open-source drivers for many ATi GPUs will increase dramatically.  The 2D performance is already superior to the proprietary software.

If I were buying a new graphics card, I would now go with ATi, as it won't be too long & they will be the darling of the FOSS world.

---

### Post by doorknob60 on 2009-10-21
On Arch I'd say the ATI proprietary drivers are in great shape as of late. I would expect the same situation under Karmic. [http://doorknob60.is-a-geek.org/wordpress/?p=6](http://doorknob60.is-a-geek.org/wordpress/?p=6)

---

### Post by AllRadioisDead on 2009-10-21
There's always that possibility, but I'm getting quite frustrated with my HD 4850. Perhaps because it's one of the newer cards. I hate the flickering, and I can only get a max of 60 fps in halo, while in windows I can get over 500. This is a little frustrating. Thanks for the blog, it was a good read, but I'm still not really convinced.

---

### Post by Nerd King on 2009-10-21
Gaming in the open ATI drivers isn't really there yet, but I think if the 2D performance is anything to go by (and it's a massive leap from older versions) we'll be there soon enough.

---

### Post by AllRadioisDead on 2009-10-21
I just wish AMD would step up to the plate and do something.

---

### Post by handy on 2009-10-22
> **ihermit said:**
> There's always that possibility, but I'm getting quite frustrated with my HD 4850. Perhaps because it's one of the newer cards. I hate the flickering, and I can only get a max of 60 fps in halo, while in windows I can get over 500. This is a little frustrating. Thanks for the blog, it was a good read, but I'm still not really convinced.

Get a cheap nVidia card then to tide you over.  The ATi open-source drivers are truly going to rock & be reliable, it is just a matter of maintaining patience until your GPU is supported for both 2D & 3D.

---

### Post by handy on 2009-10-22
> **ihermit said:**
> I just wish AMD would step up to the plate and do something.

They are; they are providing the open-source dev's with technical info'.  It is only a matter of time & AMD/ATi most likely won't make any drivers at all.  At least not for Linux, as there will be no need.  They will just feed the open-source dev's the technical info' & let them do all the hard work...

---

### Post by ublintu on 2009-10-22
Hi handy,

" The ATi open-source related packages are getting a lot of work done on them. This has been motivated by the poor quality & unreliable results with each upgrade of the proprietary packages.

Over the coming year 3D support provided by open-source drivers for many ATi GPUs will increase dramatically. The 2D performance is already superior to the proprietary software."
With this comment, you made my day much more better.
I think most of the people don`t want to choose linux on desktop comp., because graphic card and wireless problems (games, legends/old stile experiences, like "I need to type all day...", "it`s difficult"). I think the first 2 is the key to the success. The others will be better right after them.

---

### Post by Pasdar on 2009-10-22
phoronix is a better source for info on ATI cards and drivers on linux... most users on this forum have either lame intel im(r)eds or NVIDIA cards.

---

### Post by handy on 2009-10-22
> **Pasdar said:**
> phoronix is a better source for info on ATI cards and drivers on linux... most users on this forum have either lame intel im(r)eds or NVIDIA cards.

I posted a link in post_10 of this thread, which in the first post of the linked to thread, includes multiple worthwhile links regarding the ATi GPUs, it also includes a link to phoronix:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by AllRadioisDead on 2009-10-22
I also read an interview between an NVidia dev, and phoronix. It does seem like ATI is stepping up, but NVidia currently has much better support and they seem motivated to continue supporting linux.

---

### Post by natgab on 2009-10-23
This thread is very helpful for me, as I am looking at components to build a new primary computer.  

I will probably use Ubuntu multimedia, but also will try my luck at making it dual-boot to Hackintosh.  I currently have a Mac as my main computer, it has an ATI Radeon 9600 XT w/ 128MB.

I know Nvidia usally has better drivers for Linux, but in the Hackintosh forum they have more ATI cards listed.  And I expect the Hackintosh part to be more of a hassle. (guess that counts as a complement to Linux right?)

I am not a gamer, my biggest video intensive app. would be iMovie & iDVD equivalents, video playback in Linux.  

Would a pretty basic 256MB ATI card work well for my needs? ($45-65USD video card)  Otherwise I would go with a Nvidia card and make sure the MB has Intel video for the Hackintosh. :(

---

### Post by JDShu on 2009-10-23
> **natgab said:**
> This thread is very helpful for me, as I am looking at components to build a new primary computer.  

I will probably use Ubuntu multimedia, but also will try my luck at making it dual-boot to Hackintosh.  I currently have a Mac as my main computer, it has an ATI Radeon 9600 XT w/ 128MB.

I know Nvidia usally has better drivers for Linux, but in the Hackintosh forum they have more ATI cards listed.  And I expect the Hackintosh part to be more of a hassle. (guess that counts as a complement to Linux right?)

I am not a gamer, my biggest video intensive app. would be iMovie & iDVD equivalents, video playback in Linux.  

Would a pretty basic 256MB ATI card work well for my needs? ($45-65USD video card)  Otherwise I would go with a Nvidia card and make sure the MB has Intel video for the Hackintosh. :(

The r300 series cards, which are pretty old, are currently the best supported. The newer your card the longer you'll probably have to wait for all the features to be supported. I'll reiterate that the phoronix forums are the best source of news.

---

### Post by AllRadioisDead on 2009-10-23
> **JDShu said:**
> The r300 series cards, which are pretty old, are currently the best supported. The newer your card the longer you'll probably have to wait for all the features to be supported. I'll reiterate that the phoronix forums are the best source of news.
Yeah, thanks. I do check there occasionally.

---

### Post by handy on 2009-10-23
> **ihermit said:**
> I also read an interview between an NVidia dev, and phoronix. It does seem like ATI is stepping up, but NVidia currently has much better support and they seem motivated to continue supporting linux.

Did the nVidia dev mention anything about open-sourcing their code?  Or providing the open-source community with technical details regarding their GPUs to assist in the development of open-source drivers?

---

### Post by Pasdar on 2009-10-23
> **handy said:**
> Did the nVidia dev mention anything about open-sourcing their code?  Or providing the open-source community with technical details regarding their GPUs to assist in the development of open-source drivers?

They said its highly unlikely they would ever decide to open source because 90% of their linux driver is the same as the windows driver and release the 10% linux only part would be useless. They would not release it because of competition.

---

### Post by handy on 2009-10-23
> **Pasdar said:**
> They said its highly unlikely they would ever decide to open source because 90% of their linux driver is the same as the windows driver and release the 10% linux only part would be useless. They would not release it because of competition.

It is interesting, as AMD are supplying technical info' to the open-source community.  It will be interesting to see if eventually this causes nVidia (& others) to do the same.

Why spend the time/money building your drivers, when there are people that will do a better & more comprehensive job, for free?

---

### Post by Pasdar on 2009-10-23
Well I can understand it in this case. ATI owns everyone on windows systems and on Linux they suck horribly (compared to what they provide on windows). Now NVIDIA gives drivers on windows, and their drivers on linux are good enough not to complain and the advancements on each version are quite evident and out in the open.

AMD on the other hand provides significant aid to the open-source drivers, in fact they write much of it and contribute. The development of their closed drivers have been going slow but it seems to be picking up pace. I find it doubtful we'd have the problems we have now in less than a few months from now.

Anyway, what I mean to say is that when the guys at NVIDIA see ATI laggin behind on linux so much and with them saying 90% of their drivers being the same on windows it would be quite unwise to open-source it.

Remember, even ATI didn't open source their main drivers, they made new ones and released those... and help on making that better. If ATI is serious about Linux, then the open-source version will never manage to catch up to the closed-source drivers and the gap should become larger and larger during each version release.

---

### Post by edin9 on 2009-10-23
> **Pasdar said:**
> Well I can understand it in this case. ATI owns everyone on windows systems and on Linux they suck horribly (compared to what they provide on windows). Now NVIDIA gives drivers on windows, and their drivers on linux are good enough not to complain and the advancements on each version are quite evident and out in the open.

AMD on the other hand provides significant aid to the open-source drivers, in fact they write much of it and contribute. The development of their closed drivers have been going slow but it seems to be picking up pace. I find it doubtful we'd have the problems we have now in less than a few months from now.

Anyway, what I mean to say is that when the guys at NVIDIA see ATI laggin behind on linux so much and with them saying 90% of their drivers being the same on windows it would be quite unwise to open-source it.

Remember, even ATI didn't open source their main drivers, they made new ones and released those... and help on making that better. If ATI is serious about Linux, then the open-source version will never manage to catch up to the closed-source drivers and the gap should become larger and larger during each version release.

nVIDIA's Linux drivers are awesome.

---

### Post by handy on 2009-10-23
> **Pasdar said:**
> Well I can understand it in this case. ATI owns everyone on windows systems and on Linux they suck horribly (compared to what they provide on windows). Now NVIDIA gives drivers on windows, and their drivers on linux are good enough not to complain and the advancements on each version are quite evident and out in the open.

AMD on the other hand provides significant aid to the open-source drivers, in fact they write much of it and contribute. The development of their closed drivers have been going slow but it seems to be picking up pace. I find it doubtful we'd have the problems we have now in less than a few months from now.

Anyway, what I mean to say is that when the guys at NVIDIA see ATI laggin behind on linux so much and with them saying 90% of their drivers being the same on windows it would be quite unwise to open-source it.

Remember, even ATI didn't open source their main drivers, they made new ones and released those... and help on making that better. If ATI is serious about Linux, then the open-source version will never manage to catch up to the closed-source drivers and the gap should become larger and larger during each version release.

The open-source drivers are already superior to the AMDs closed drivers in 2D.  I expect that the same thing is going to happen with 3D.  & we will have drivers that can keep up with the development of the rest of the core components of the Linux system & hopefully that of BSD as well.

---

### Post by edin9 on 2009-10-23
> **handy said:**
> The open-source drivers are already superior to the AMDs closed drivers in 2D.  I expect that the same thing is going to happen with 3D.  & we will have drivers that can keep up with the development of the rest of the core components of the Linux system & hopefully that of BSD as well.

They also works properly with Xv. It's kind of funny that the opensource guys can do better than the company who invented the cards.

---

### Post by JDShu on 2009-10-23
> **handy said:**
> It is interesting, as AMD are supplying technical info' to the open-source community.  It will be interesting to see if eventually this causes nVidia (& others) to do the same.

Why spend the time/money building your drivers, when there are people that will do a better & more comprehensive job, for free?

They said that releasing driver specifications to public would be a monumental effort for the company so they have no plans for doing so. One can of course argue that ATI had the same problem yet still released them.

---

### Post by markbuntu on 2009-10-23
ATI did run into a lot of problems releasing info on their cards. A lot of the code they used for their older cards was written by others so ATI was unable to release it due oi intellectual property concerns. Things like the tv capture of the all-in-one cards. They do not own that code so cannot release it.

Nonetheless, they released as much as possible and no longer use third parties to write their code so for all cards from the r600 on they are able to release all the info available. But still, the legal department review takes a while so this slows info releases up some.

The proprietary driver is still to protect their newest technology from competitors but also to provide working drivers for new hardware that the open source drivers would take a long time to support.

I think it is the best that can be hoped. Open source drivers for old hardware and proprietary drivers for new hardware until the open source drivers are capable, though dropping the r300-500 cards from fglrx was a little premature it did seem to light a fire under the open source driver development and the latest open source drivers are better that fglrx for those cards and some people testing the latest radeonhd driver report superior perfomrance for their r600 cards.


People need to keep in mind that the driver in their distro is not the latest. Distributions do not update drivers until the next distribution release and that one is usually a few months old by then.

Nvidia has started contributing to the open source noveau driver but nowhere near the extent that ati isto the ati and radeon driver efforts. I would suspect that nvidia would face a serious intellectual property rights problem releasing driver specs. They still use a lot of third party code.

---

### Post by handy on 2009-10-23
Catalyst 9.10 was released a couple of days ago.  I expect that it is for use in the upcoming Ubuntu release of the same numerical designation.

---

### Post by markbuntu on 2009-10-23
> **handy said:**
> Catalyst 9.10 was released a couple of days ago.  I expect that it is for use in the upcoming Ubuntu release of the same numerical designation.

No, it can be used with any distribution.

---

### Post by AllRadioisDead on 2009-10-24
> **handy said:**
> Catalyst 9.10 was released a couple of days ago.  I expect that it is for use in the upcoming Ubuntu release of the same numerical designation.
I'm using the 9.10 driver, but honestly I haven't seen any noticeable improvements.

---

### Post by handy on 2009-10-26
> **markbuntu said:**
> No, it can be used with any distribution.

I know that.  I used to use it in Arch, before I dumped it for the open-source drivers.

Under certain circumstances, Ubuntu gets special treatment due to its popularity.  

The release of this proprietary Catalyst version would certainly be timed for Ubuntu's benefit.

---

### Post by handy on 2009-10-26
> **ihermit said:**
> I'm using the 9.10 driver, but honestly I haven't seen any noticeable improvements.

The results depend on which ATi GPU is being used, as well as which version of the kernel & other associated packages.

Some people get a black screen, others still get artefacts, especially when using compiz, & the list goes on to include those that can now run it, when the previous Catalyst release wouldn't work.

It is going to be so good when the open-source drivers get 3D working as well as they have got 2D working now... :)

---

