---
title: "Ubuntu on a slippery slope?"
date: 2006-11-13
forum: The Cafe
---

### Post by moneypenny on 2006-11-13
I was just reading an article titled [Ubuntu should reconsider](http://www.nuxified.org/blog/ubuntu_down_the_drain) and it's certainly food for thought.  If the article is correct, then it's certainly a concern.
> First they start shipping non-free software by default, then the edgy upgrade turns into a disaster and now I read about plans for including more non-free software and a 3D desktop by default in feisty
What's up with this?  I thought the whole point of Ubuntu was to have a working, pretty operating system that is free and open by default, where you only got non-free things if you installed them yourself.

---

### Post by earobinson on 2006-11-13
fyi most distros ship no free sw (drivers) this includes debian. edgy upgrades have been bad :( and im not a fan of the 3d desktop but then im not a fan of gnome so I just install and uninstall what i want.


over all I think we are moving in the correct direction

---

### Post by midwinter on 2006-11-13
Numerous threads about this already, but I think this is a definitely a slippery slope.  I'll surely stop recommending Ubuntu to people, sad..

---

### Post by earobinson on 2006-11-13
> **midwinter said:**
> Numerous threads about this already, but I think this is a definitely a slippery slope.  I'll surely stop recommending Ubuntu to people, sad..
links?

---

### Post by mostwanted on 2006-11-13
I think it's an alarming trend. Ubuntu is the biggest desktop distro and by undermining the years of abstaining from releasing proprietary drivers practiced by many other major distros, you're sending a message to the video card manufacturers that we don't really care if it's proprietary or not. And as long as it's proprietary, they have us by the balls.

---

### Post by midwinter on 2006-11-13
[http://ubuntuforums.org/showthread.php?t=297392](http://ubuntuforums.org/showthread.php?t=297392)
[http://ubuntuforums.org/showthread.php?t=298640](http://ubuntuforums.org/showthread.php?t=298640)
[http://ubuntuforums.org/showthread.php?t=296029](http://ubuntuforums.org/showthread.php?t=296029)

Probably a few I missed..

---

### Post by jamyskis on 2006-11-13
It is an alarming, but unfortunately inevitable trend. I think time has shown that despite opposition to the closed-source nature of some drivers, the manufacturers won't give in very easily, and would rather just stop supporting Linux. And having no drivers is far worse than having closed source.

As far as the 3D desktop is concerned: I can't believe that they would include an XGL desktop or 3D desktop by default on *all systems* - surely they aren't that daft. There will probably be a script built-in to the installation process which will detect if the computer has hardware for which there are 3D drivers (Intel, NVIDIA or ATI) and consequently install them together with XGL, otherwise leaving the whole 3D thing out.

I think it would be a good idea to supply two versions of Ubuntu if this is a direction that Canonical are willing to take á la OpenSuSE - one with only free software, and one including non-free software.

---

### Post by earobinson on 2006-11-13
I do agree with you that free software is better, but one of the goals is to make ubuntu as functional as possible and I believe it has included proprietary software from the start. Also launchpad is proprietary.

As long as the including of proprietary packages is a temporary fix that we intend to remove in the future I have no problem with it.

But I do see the concern.

---

### Post by PriceChild on 2006-11-13
> **jamyskis said:**
> There will probably be a script built-in to the installation process which will detect if the computer has hardware for which there are 3D drivers (Intel, NVIDIA or ATI) and consequently install them together with XGL, otherwise leaving the whole 3D thing out.Yeah... the spec for this is on launchpad and approved.

The installer should detect your cards, ask you whether you want to install any available proprietary software.

If your hardware's good enough for composite, it'll turn it on.

---

### Post by P_Badger on 2006-11-13
I'd **** a brick if ubuntu came with drivers easily available and ready to go. I don't like digging around for things that should be easily available.

Just because it's linux doesn't mean is HAS to be a **** to set up.

And oh, this bit was precious: 

*"Also, by including proprietary video card drivers in Ubuntu for these desktop effects Ubuntu as the leading GNU/Linux distribution is telling video card manufacturers that the GNU/Linux community can live with their drivers being proprietary **meaning so much less pressure on them releasing those drivers as Free Software.**"*

Not going to happen. Try to get that not EVERYTHING will be made open source.

---

### Post by SunnyRabbiera on 2006-11-13
I think proprietary support is a good thing, as right now very little supports linux anyhow so you might as well backhack and get it over with otherwise nothing will work.
I think over opensource idealisim is getting in the way here

---

### Post by dbbolton on 2006-11-13
hmm. i might have to think about getting a mac now.

---

### Post by ComplexNumber on 2006-11-13
welcome to canonical/ubuntu and their plans to grab as much market share at any cost by enabling 3D desktop by default and having every single *buntu imaginable.
their iniitial ideas were sound, but now its just getting silly.

---

### Post by SunnyRabbiera on 2006-11-13
ComplexNumber i agree, I think this is a good thing as you know open source is still looked at as inferior by most hardware companies and backhacking is going to be our ally...
It will tell those big wigs they should support us rather if they like it or not as Linux is here and its here to stay.

---

### Post by Henry Rayker on 2006-11-13
> **P_Badger said:**
> I'd **** a brick if ubuntu came with drivers easily available and ready to go. I don't like digging around for things that should be easily available.

Just because it's linux doesn't mean is HAS to be a **** to set up.

And oh, this bit was precious: 

*"Also, by including proprietary video card drivers in Ubuntu for these desktop effects Ubuntu as the leading GNU/Linux distribution is telling video card manufacturers that the GNU/Linux community can live with their drivers being proprietary **meaning so much less pressure on them releasing those drivers as Free Software.**"*

Not going to happen. Try to get that not EVERYTHING will be made open source.

Well, the drivers and the like won't be open sourced if they don't have to do it; however, if there is a large enough demand for open sourced drivers, there is no reason why it wouldn't be done.

---

### Post by SunnyRabbiera on 2006-11-13
Well even if the drivers for certain things are not open sourced there can be at least support for linux, this backhacking is going to help all those bigwigs realise that we can do whatever we want with thier precious drivers.

---

### Post by sander marechal on 2006-11-13
> **P_Badger said:**
> I'd **** a brick if ubuntu came with drivers easily available and ready to go. I don't like digging around for things that should be easily available.

And again with the same flawed statement. Making something easy to install does not mean you should install it by default.

Ubuntu should enable AIXGL on computers where it will work with a free driver. Also, there should be an "enable 3D effects" option on the preference panel/menu. When a user ticks the box and his hardware isn't supported freely, he should get a message educating him about binary drivers. After that the user should be able to click "Yes, install. I'm sure!" and the drivers, Beryl and AIXGL should all come alive automagically. No commandline work, no adding of repositories, no extra work.

---

### Post by OffHand on 2006-11-13
They will NOT be installed by default. If you press no you will have a system without any prop drivers/software. I do not see the problem?

---

### Post by jamyskis on 2006-11-13
> **ComplexNumber said:**
> welcome to canonical/ubuntu and their plans to grab as much market share at any cost by enabling 3D desktop by default and having every single *buntu imaginable.
their iniitial ideas were sound, but now its just getting silly.

[QUOTE="Launchpad Bug 1"]
Microsoft has a majority market share.
[/QUOTE]

Is trying to get a bigger market share with a Linux desktop such a *bad* thing?

---

### Post by ago on 2006-11-13
> **sander marechal said:**
> And again with the same flawed statement. Making something easy to install does not mean you should install it by default.

Ubuntu should enable AIXGL on computers where it will work with a free driver. Also, there should be an "enable 3D effects" option on the preference panel/menu. When a user ticks the box and his hardware isn't supported freely, he should get a message educating him about binary drivers. After that the user should be able to click "Yes, install. I'm sure!" and the drivers, Beryl and AIXGL should all come alive automagically. No commandline work, no adding of repositories, no extra work.

I agree

---

### Post by MetalMusicAddict on 2006-11-13
Everyone who want to spout off about the decision to go with the non-free drivers could have been at the UDS/MV meetings. It was open to everyone. You could walk right in. Talk on IRC or over VoIP.

You have more power than you know.

---

### Post by midwinter on 2006-11-13
> **jamyskis said:**
> Is trying to get a bigger market share with a Linux desktop such a *bad* thing?

At the cost of compromising sound principles? Yes, I think so.

---

### Post by PriceChild on 2006-11-13
> **Henry Rayker said:**
> if there is a large enough demand for open sourced drivers, there is no reason why it wouldn't be done.The one big problem about open sourcing drivers, is that by its very nature, it reveals EXACTLY how your hardware works.

This means that it's incredibly easy for the closed-source competition to steal loads of your secrets, leaving them one up.

---

### Post by MetalMusicAddict on 2006-11-13
> **PriceChild said:**
> The one big problem about open sourcing drivers, is that by its very nature, it reveals EXACTLY how your hardware works.

This means that it's incredibly easy for the closed-source competition to steal loads of your secrets, leaving them one up.

This is at the heart of it. I for one am glad nVidia do such a great job at drivers for linux. Our world will _never_ consist of a completely Stallman view or a MS view. Free software will _need_ to co-exist as much as proprietary software will have to adapt. Id buy a open card if it works as well as a proprietary one but that doesnt exist yet.

---

### Post by yabbadabbadont on 2006-11-13
Also, supposedly some of the technology in nvidia cards does not belong to them.  They just have a license to use it and cannot open it up unless the other copyright/patent holders all agree to as well.

---

### Post by shining on 2006-11-13
> **PriceChild said:**
> The one big problem about open sourcing drivers, is that by its very nature, it reveals EXACTLY how your hardware works.

This means that it's incredibly easy for the closed-source competition to steal loads of your secrets, leaving them one up.

I'm not sure that's really a big problem in itself. It's probably a problem though for the mentality and philosophy of the business world.
But what if every graphic driver was opened, so no one would have any secrets. And why are secrets needed anyway in this case? They still have to make the hardware, and they will keep selling them, because there is a need.

---

### Post by emarkay on 2006-11-13
But as the little boy said to the assembled crowd:  "Who needs a 3D desktop to begin with?"

How does this increase productivity, stability and simplicity of this (or any) software?

Aren't we falling into the bloatware trap here?

Serious answers would be greatly appreciated!

---

### Post by Polygon on 2006-11-13
so... people are getting mad about closed source drivers being included in a linux distro, when usually a first thing a person does when they install a linux distro is install those closed source drivers themselfs? 

and not to mention it IS going to ask you whether you want to install them or not... so its the best of both worlds.

i dont understand what the fuss is all about. If you want a free pure open source system, then simply click "no" when it asks to install closed source drivers. its that simple.

---

### Post by shining on 2006-11-13
> **emarkay said:**
> But as the little boy said to the assembled crowd:  "Who needs a 3D desktop to begin with?"

How does this increase productivity, stability and simplicity of this (or any) software?


I don't think it does, so it's indeed pointless. And there is obviously a lot of work to be done in other areas for improving productivity, stability and simplicity.

---

### Post by shining on 2006-11-13
> **Polygon said:**
> 
i dont understand what the fuss is all about. If you want a free pure open source system, then simply click "no" when it asks to install closed source drivers. its that simple.

That's in the case you actually have the choice.

---

### Post by ComplexNumber on 2006-11-13
some more about it:
[http://www.jejik.com/articles/2006/11/is_ubuntu_set_to_become_non-free](http://www.jejik.com/articles/2006/11/is_ubuntu_set_to_become_non-free)

---

### Post by Buffalo Soldier on 2006-11-13
My only fear is when this scenerio happens:

The year is 2008. Let say I have been using an Nvidia or ATI graphic card. Ubuntu has been working nicely beautifully with these graphic card using non-free binary drivers. Little or no work has been done on the free drivers for years because majority of Ubuntu and other major distro users are using the non-free drivers. No update on the free drivers (especially on latest hardware).

After years of being comfortable with Ubuntu and thinking I am proficient enough in using GNU/Linux, I decide to jump to another distro. (flashback to the wonderful experience I had when I jump to Ubuntu in 2004).

Let say I'm trying a new distro (Distro X). Everything else works perfectly fine. The distro, the work i want to do, and my hardware is like a perfect match. EXCEPT, it has a little bit of problem with my graphic card.

As usual, I go screaming at the developers of Distro X. *"Why aren't your distro working with my graphic card??? Ubuntu works just fine!!!"*

One of them replied, *"I'm so sorry dude, nothing much we can do about that, you have to wait until Nvidia/ATI release a non-free binary driver for Distro X."*

There's nothing much the developer can do. Once again i have to re-live the experience of transition of non-free closed-source OS to a free and open source OS. Held hostage by the hardware manufacturer.

I hope we all could think of the long term implication of this move. Free and open source drivers are not only for the freedom to developers, but to us as end-users.

[[img]http://geekz.co.uk/lovesraymond/wp-content/ep029.jpg[/img]](http://geekz.co.uk/lovesraymond/wp-content/ep029.jpg)

---

### Post by josys36 on 2006-11-13
Personally, and I know that this going to cause mass panic, but I would pay for Ubuntu if they charged. 

I run Linux because I think it is better then Windows. Not because it has free software. Heck I can get a ton of free software for Windows! There is even the time when I like a piece of software so much I pay for it! I love the idea of the free software movement, but let's fact it is just not very practical. People have house payments, car payments and other bills they need to pay. If I had an OS that was great, and everyone wanted an alternative to what is out there, why not just charge 20 bucks for it? It would be worth it if you hate your current OS or Windows enough. Like I said before I run Linux because I feel it is superior to Windows.

Just for the math let's set 200,000 people install Ubuntu. At 20 bucks a pop they would have 4,000,000! Four freaken million could buy a large amount of talented developers. 

I run Ubuntu because of the community, the simple install, and the one CD principal. Believe me I looked at Fedora and Mandriva long and hard before I choose Ubuntu. Ubuntu one because of it's simple straight foward approach to Linux. Are there things that could improve? Well sure! You can say that for just about everything! I do however feel that they are on the right track and not the slippery slope. 

First, a 3D desktop and all the other graphical stuff is coming because of customer demand. At least that is how I see it. I don't care for them myself, but then again I don't like KDE either. This does not mean that I go on a I hate KDE and KDE should die campaign. KDE fills it nitch for the folks who love it. I find that XFCE suits me much better. That is part of the freedom in Linux. 

Second, Let's face it windows runs the earth. We may not like it, but hardware companies see it that way. That is why it is so much easier to get windows drivers then linux drivers. The best way to get them to see our need is to take more and more market share away from Windows. From what I have seen Visa might not do well, so this may be right around the corner. 

Third, one thing that may be holding hardware folks back is that there are so many linux flavors out there. I saw a post ( I think from HP ) that stated that they were having problems because there were just so many linux installs to choose from. I guess maybe they could just choose a select few to work from. Then create .DEB, .RPM and then .TAR for the folks to do need to compile. This is the case with my modem on my T60. I did have to pay for this driver.

To conclude I feel that Ubuntu is doing a great job! I love using this product and I am looking foward to the future! Just remember, even Microsoft has had bad releases. Anyone remember WindowsME?

Thanks!

Jason

---

### Post by Polygon on 2006-11-13
im confident that the developers will still have the best intrests of linux in mind

it is the best intrest for everyone if ati/nvidia would open source their stupid drivers, but i dunno if this will happen soon, if at all

but i still dont think that we should be getting worked up and claling ubuntu bad evil people because we are including binary drivers (optional) with the distro, with an explination and a choice in installing them.

---

### Post by o_fortuna on 2006-11-14
Well, I agree that shipping binary drivers by default is a less-than-ideal situation, but I don't agree it's a slippery slope. We haven't increased the amount of proprietary software/drivers that Ubuntu ships. We're merely offering the *option* to have them enabled by default.

Seriously, Ubuntu has shipped proprietary drivers for ages. In fact, Ubuntu has shipped the nvidia and fglrx modules since I've been using it (since 5.04). Now, in 7.04 (how time flies ;)), they are enabling these modules by default to give people the best possible experience with their desktops.

I just can't see what's wrong with it. They have always shipped these drivers, and most people install them immediately after installation. Those who don't want them, uninstall them. Free software is definitely better than proprietary software, but you can't have everything in life. Take what you got and run with it ;)

---

### Post by Sushi on 2006-11-14
> **emarkay said:**
> But as the little boy said to the assembled crowd:  "Who needs a 3D desktop to begin with?"

How does this increase productivity, stability and simplicity of this (or any) software?

Are you saying that we should only do things that increase "productivity, stability and/or simplicity"? If something simply makes the system more beautiful it should not be done?

That said, if you want a 100% free Ubuntu-distro, try out the new FSF-distro (it's name escapes me at the moment).

> [Aren't we falling into the bloatware trap here?

Just because something is pretty does not mean that it's "bloated".

---

### Post by steven8 on 2006-11-14
I think it is purely semantics.  To allow the users a one-click (or so) option to enable/install the proprietary drivers and 3d doohickeys is no less righteous than having them enabled by default with a blurb about why they're bad and giving the user a one-click (or so) option to disable/unistall them.

I believe that having them there at our fingertips, yet not on by default, merely gives the 'impression' of righteousness.

This is a design decision, not an ethical decision, I believe.

The FSF distro is called gNewSense, and has been ridiculed for it's name being too close to 'Nuisance', in another thread.

---

### Post by 3rdalbum on 2006-11-14
What it comes down to is this: Mandriva has taken the first step by including 3D drivers by default. Ubuntu has got to keep up with the competition.

I'm not happy that this is being done, and I pray that the Ubuntu installer at least gives you the option to install as clean a system as possible. But in reality, if you really want a completely Free Ubuntu replacement, gNewSense is the distro for you (unless, of course, you need commercial support...)

---

### Post by Kernel Sanders on 2006-11-14
I really dont understand why everyone has such a problem with this? :-k 

As long as ubuntu is free, I dont care in the slightest whether its made up of open or closed source software?

---

### Post by The Grum on 2006-11-14
Theres a lot of talk about this removing the incentive for hardware manufacturers to release open source drivers and how that leaves us "hostage to the hardware companies" and abandoning all ethics and morality.

What about everyone here (me included) who, despite using Linux and wanting 100% open source drivers **and** knew that NVidia or ATI released binary drivers only, went out and ***bought* the hardware anyway**? Thats stating that binary-only drivers are acceptable far more than including them in the distro.

---

### Post by Velotix on 2006-11-16
**Pre-emptive edit:**[i] As I wrote this post out I started to see exactly what was wrong with the logic behind people who solely support closed-source business models and that my opinion was **really** hammy! But I decided to post it anyway because it highlights the faulty logic a lot of people have and use on this matter.

Regardless, people and businesses still should have the right to keep their IP secure and under their control, which the open source business model is in danger of undermining and is the critical problem preventing its widespread adoption.

I still maintain that the open-source model is as open to corruption as the closed-source model; it simply depends on the decency and integrity of the developers as to the decency and integrity of the model.[/i]

====================================================================================================

For me, the issue is simple. If I pay £150+ for a graphics card, I want it to work at its optimum ability. Period. **I don't care how it's distributed, so long as I don't have to pay for it.**

nVidia's position is different from Microsoft's: with Microsoft, they're making software that runs on hardware that isn't their property, they're essetially making a tool, and the specifications of a tool should be freely shared. It has no bearing nor any effect on them if they make their software open-source, so long as they use a competent business model, and Microsoft have competent business sense in spades.

With nVidia, not only are they creating driver software, they're creating it **for their own brainchild**. It's like telling a writer to get their book published and give out the full set of drafts, private notes, letters to friends and relatives, **anything** that enabled them to write their book to completion. nVidia have an intrinsic right to secure the wellbeing of their property, which goes beyond the amount of money they may lose to competitiors. Yes, a graphics card is also a tool, which is the key counter-argument to my analogy, but I believe that software's value as an artform overrides its value as a tool - if software has little or no such creative value, it is better suited to open source.

Not that I'm saying that programmers aren't creative - I know that isn't true! From my personal experience, though, the kind of creativity needed to produce quality art and music is wholly different from the creativity required to produce a powerful and competent program, though each form of creativity is of equal quality and value to society in general. ^^

---

### Post by hizaguchi on 2006-11-16
As innocent as a video driver seems, I think it is important to remember that we're not talking about a codec here... we're talking about a part of the kernel.  We're talking about putting closed source software into the core of our operating system.  That's really going beyond "slippery slope" all the way down toward "rock bottom".

With Edgy this is possible with a simple "apt-get install _____", with Feisty it'll be as simple as "yes or no".  So with Feisty+1 I fully expect it to be the default.  I don't like where this is heading.

---

### Post by dca on 2006-11-16
No matter what Ubuntu/Canonical and the space cadet say or do will be frowned upon and possibly bashed on the forums.  I'm kind of upset for them about it...  If you want the free Ubuntu, go d/l Gnew-sense or whatever it's called.  You want all the multi-media illegal (in the US) crap, d/l the Linux Mint...  Etc, etc, they're all based on Ubuntu which is a darn fine Debian-based distro if I do say so my darn self.  IMHO, much better than RPM-based like Fedora or Suse for that matter.
 
Bottom line, they're not charging you for it, nor will they ever for d/l & installing their Linux.  If the FOSS or anything proprieary or non-open, whatever ruffles you move to something else...  For now, let them put whatever they want into it because the money they make is on the service & support side not anything else...

---

### Post by dca on 2006-11-16
...and one more thing, don't worry about Linux replacing anything on the desktop so long as conversations about what's free and what's not keep going on...  That's why there is a Fedora and a RHEL for servers.  They gave up on the desktop because the money is with enterprise servers.  
 
I'm an American and I want my illegal codecs.  I want to play my encoded DVDs.  I want things to work out of the box.  I DO NOT want to pay $199 for M$ and whatever else for certain application software, nor do I want to buy a PC from BestBuy and have however much of the manf's money go to M$...  
 
Maybe that's why Bill Gates has turned full-time philanthropist.  He feels guilty...  At least he is now giving something back, I guess.  I bet it's nice for Bill to wake up in the morning and make a phone call to Bono asking where to meet him in Zimbabwae...

---

### Post by Jimmy_r on 2006-11-16
I agree with what dca said.

Also, for the "conversations about what's free and what's not", I am still of the opinion that if something is 'forced to be open source', it is not free. Just open source. Forced open or forced closed is equally bad, and neither is really free (Other than in Stallmans opinion, that is). And that is what is holding back linux in my opinion.

---

### Post by prizrak on 2006-11-16
One simple fact is that neither nVidia nor AMD give a rat's arse what driver you use. They don't sell the drivers they sell the cards. If you want to send the message to those companies to open up the drivers you need to stop supporting their products. If you keep buying closed hardware you will not give any incentive to the manufacturer to open up the driver. If there is a large enough number of people who will let nVidia/AMD know that despite Linux drivers they will not pay money for their products unless the specs are open they might start carring and at least open up some part of the driver.

---

### Post by Jimmy_r on 2006-11-16
I said something similar here: [http://www.ubuntuforums.org/showthread.php?p=1767603#post1767603](http://www.ubuntuforums.org/showthread.php?p=1767603#post1767603)

---

### Post by chaosgeisterchen on 2006-11-16
I like the inital article and I also see the point in it. It's true that Ubuntu is now aiming towards the false way, the way of accepting closed source drivers as the status quo forever - as pointed out the in the article.

We should strongly reconsider the inital goals of spreading free software. Closed software should be ready to be installed by the user but not shipped with the distribution. It taints the ideals and image of Ubuntu als free software distribution.

And it would be very sad if we will miss our goal by far in the future...

---

### Post by emarkay on 2006-11-16
> **Sushi said:**
> Are you saying that we should only do things that increase "productivity, stability and/or simplicity"? If something simply makes the system more beautiful it should not be done?

That said, if you want a 100% free Ubuntu-distro, try out the new FSF-distro (it's name escapes me at the moment).

Just because something is pretty does not mean that it's "bloated".

The default installation should be based on functionality, simplicity and stability!
Let the bloat (Gee-Whiz effects and all that)  come from the repositories, along with the non-free/proprietary programs.

Keep the shady side demarcated from the sunny side, and provide clear directions for both sunglasses and flashlights, and let the users decide what they need and want.

---

### Post by Turin Turambar on 2006-11-20
So some of you will stop enjoying Ubuntu just because it'll (possibly) use proprietary, non-free software? Was that the main reason you started using Ubuntu?

Sorry, but that's the biggest BS I've read in a long time.
How many of you have virginally clean systems anyway? Be honest!

How about handy MP3 players, DVDs & practically all multimedia? How about Flash & Java? How about drivers for many peripherals?
Even (at least what I've heard) the linux kernel have some proprietary stuff.

Ubuntu's philosophy is, well, good, but not entirely real. I guess more than 90% of Ubuntu users will need/have some/use non-free software. At least from time to time.

What's more ridiculous, that "non free" stick has nothing to do with paying someone a cash for using the software. It's just that  it's not free to modify or whatever. You are free to use it. That has nothing to do with end-users.

Yes, I wish we could live in open source world, but hey, I don't have an Ogg player in my pocket, my legally bought DVDs need some drivers&codecs in order to play, the videos I made with my digital camera also need some other stuff too, oh and the JPG format..., my video card needs closed fglrx driver, my modem needs proprietary driver, my.... the list goes on and on.

If I'd stick to the open-free software only, my PC would be totally useless.

---

### Post by aysiu on 2006-11-20
> **Turin Turambar said:**
> So some of you will stop enjoying Ubuntu just because it'll (possibly) use proprietary, non-free software? Was that the main reason you started using Ubuntu?

Sorry, but that's the biggest BS I've read in a long time.
How many of you have virginally clean systems anyway? Be honest! Based on surveys I've seen here in the past, I'd say about 4%.

All the rest of us run "dirty" systems.

---

### Post by ZylGadis on 2006-11-20
The main reason I started using Ubuntu was because I was tired of configuring other Linux distributions (including self-made). Perhaps it will come as a surpirse to you, but the reason I went to Linux in the first place is free as in freedom.
I do not buy DVDs. I do not use Flash. Java just went GPL (which was actually a nice surprise, I thought they would do SPL or something similar). I do have a mp3 collection, but I'm doing my best to replace it with ogg of the same quality.
If Ubuntu starts shipping with proprietary software by default, I'll immediately move to another distro. If Linus Torvalds does not see the danger Linux is in and continues rejecting GPL3 and accepting DRM, I'll move away from Linux completely.
The way I see things right now is - Ubuntu in particular and Linux in general are moving towards replacing Windows. And I mean fully replacing Windows - having DRM, being proprietary, being spyware-laden, etc. If that is what Mark Shuttleworth wants with his bug #1, he may have it - without me. If that is what Linus Torvalds wants with his "engineer-only" view, again he may have it - without me. Compromising your principles just for having more widespread adoption (or more money, or more fame, or whatever) is what I sense in both cases, and I do not respect that.
In 10 years Microsoft will probably be dead. But we are not fighting Microsoft. We are fighting the proprietary innovation-stifling parasitic ideology of Microsoft. If Linux turns into Windows, then we have lost the battle. Not the war, for surely something else will spring and start fighting Linux on ideological grounds in turn, but we will have lost the battle.

---

### Post by prizrak on 2006-11-20
> **ZylGadis said:**
> The main reason I started using Ubuntu was because I was tired of configuring other Linux distributions (including self-made). Perhaps it will come as a surpirse to you, but the reason I went to Linux in the first place is free as in freedom.
I do not buy DVDs. I do not use Flash. Java just went GPL (which was actually a nice surprise, I thought they would do SPL or something similar). I do have a mp3 collection, but I'm doing my best to replace it with ogg of the same quality.
If Ubuntu starts shipping with proprietary software by default, I'll immediately move to another distro. If Linus Torvalds does not see the danger Linux is in and continues rejecting GPL3 and accepting DRM, I'll move away from Linux completely.
The way I see things right now is - Ubuntu in particular and Linux in general are moving towards replacing Windows. And I mean fully replacing Windows - having DRM, being proprietary, being spyware-laden, etc. If that is what Mark Shuttleworth wants with his bug #1, he may have it - without me. If that is what Linus Torvalds wants with his "engineer-only" view, again he may have it - without me. Compromising your principles just for having more widespread adoption (or more money, or more fame, or whatever) is what I sense in both cases, and I do not respect that.
In 10 years Microsoft will probably be dead. But we are not fighting Microsoft. We are fighting the proprietary innovation-stifling parasitic ideology of Microsoft. If Linux turns into Windows, then we have lost the battle. Not the war, for surely something else will spring and start fighting Linux on ideological grounds in turn, but we will have lost the battle.
You do realize that Ubuntu already ships with non-free software, right? In case you did not, guess what, the Atheros (madwifi) driver is not "free". 

This has been debated to death, Ubuntu WILL install non-free drivers if no free driver is available. In fact you will end up using proprietary drivers even in gNewSense if you run closed hardware. 

Also what part of Ubuntu is closed source? The kernel is open so is the GUI. Canonical isn't trying to create closed source improvements to the code they allow you all the source to what they create. They also stated that whenever possible free software will be used.

Want a free OS? Don't buy non-free hardware! Don't b*tch about a distro trying to be as functional as possible out of the box.

---

### Post by ZylGadis on 2006-11-20
If functionality (as you call it) directly contradicts my principles (and the supposed principles of the creator), I will bitch about it, yes. And if the creator does not heed, I will move to something else. It is a matter of value systems. You put ideology and higher cause quite low, while I put them quite high.
I don't buy non-free hardware (as much as I am aware of). Forcing non-free software on me, just because someone out there is stupid and does buy non-free hardware, is not something I appreciate.

---

### Post by aysiu on 2006-11-20
> **ZylGadis said:**
> If functionality (as you call it) directly contradicts my principles (and the supposed principles of the creator), I will bitch about it, yes. And if the creator does not heed, I will move to something else. It is a matter of value systems. You put ideology and higher cause quite low, while I put them quite high.
I don't buy non-free hardware (as much as I am aware of). Forcing non-free software on me, just because someone out there is stupid and does buy non-free hardware, is not something I appreciate.
I think you should move to Debian. They're all free, as far as I can tell.

---

### Post by prizrak on 2006-11-20
> **ZylGadis said:**
> If functionality (as you call it) directly contradicts my principles (and the supposed principles of the creator), I will bitch about it, yes. And if the creator does not heed, I will move to something else. It is a matter of value systems. You put ideology and higher cause quite low, while I put them quite high.
I don't buy non-free hardware (as much as I am aware of). Forcing non-free software on me, just because someone out there is stupid and does buy non-free hardware, is not something I appreciate.

I would be very careful calling other people stupid. I could argue it is stupid of you to buy only open hardware as, at least in video cards, the best hardware is closed. 

If you cared enough to read the spec that is basically being discussed and the Ubuntu website, you would realize that if you do not have that hardware the driver will not be installed. So what is the problem then? If all your hardware is 100% open, you will have a "free" system regardless. For those who does buy closed hardware it will install the non-free driver to help them get the most out of it. 
> I think you should move to Debian. They're all free, as far as I can tell.
Actually according to people who made gNewSense, both Debian and Ubuntu include non-free firmware as part of the kernel (that no one really gives a damn about it seems, not even the kernel hackers) so maybe he would be better with gNewSense. 

As for ideology and higher cause, a PC is a collection of semi-conductors, conductors and insulators. The software is alot of 1's and 0's, catch my drift?

---

### Post by Lster on 2006-11-20
I am, although an expert at Windows, a newbie on Ubuntu. For me Windows drivers were installed by default for me, but on Ubuntu I still havent located the driver for my ATi GPU. Also, as I currently only have dial-up connection, I probably could not download the 20MB file anyway.

In this case I have to put up with sluggish graphics performance.

Sure it would be _nice_ if drivers became open, but why does it matter? I could even go as far as saying NVidia/ ATi have a _right_ to release non-free drivers.

In the end what do _we_ lose from closed sources drivers?

---

### Post by ZylGadis on 2006-11-20
The problem is that I will be using a distribution that installs proprietary drivers by default in the general case. When I fill in surveys, or when someone asks, I will say I use it, because that is the honest thing to do. It logically follows that I support it and its ideology. For the above reasons, I will probably move away from Ubuntu (and probably towards Debian for now) when Dapper becomes old. It looks like you can't have the best of both worlds (the user world and the hacker world).
I don't catch your drift. Care to explain? As far as current science knows, everything is made of elementary particles. Does that mean intelligent beings can't abstract away higher concepts such as molecules, chairs, information, and freedom?

---

### Post by 56phil on 2006-11-20
My laptop, a Gateway M680, ran poorly until ATIs proprietary video driver was installed. If Ubuntu provides the option to load/update proprietary drivers and codecs, so much the better. I care more about functionality than high-minded ideals. All software would be free in a perfect world. I'm just not going to hold my breath. 

I can live without the codecs; just don't ask me to accept substandard video performance. Ubuntu with proprietary drivers is better than Windows XP - which I still must use at work. I'm not sure I would stick with OSS software in general and Ubuntu in particular on my laptop if it did not have a good video driver. Performance is that important to me and I'm not a gamer. I just want a decent scroll rate.

---

### Post by prizrak on 2006-11-20
> I don't catch your drift. Care to explain? As far as current science knows, everything is made of elementary particles. Does that mean intelligent beings can't abstract away higher concepts such as molecules, chairs, information, and freedom?
Reply With Quote
The drift is that compared to quite a few things out there computers are meaningless. Even when it comes to certain things where computers are a great aid (say science) then it still boils down to functionality as opposed to ideology. In other words if a scientifically centered Linux distribution came with proprietary software that is needed to develop the cure for cancer would you really expect people to turn away from it?

---

### Post by Buffalo Soldier on 2006-11-20
> **Turin Turambar said:**
> So some of you will stop enjoying Ubuntu just because it'll (possibly) use proprietary, non-free software? Was that the main reason you started using Ubuntu?

Sorry, but that's the biggest BS I've read in a long time.
How many of you have virginally clean systems anyway? Be honest!

```
$ vrms
              Non-free packages installed on ubuntu

sun-java5-bin             Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-demo            Sun Java(TM) Development Kit (JDK) 5.0 demos and examp
sun-java5-jdk             Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-jre             Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-plugin          The Java(TM) Plug-in, Java SE 5.0

  5 non-free packages, 0.3% of 1519 installed packages.
```
The best way to avoid proprietary drivers is to avoid the FOSS unfriendly manufacturers. Think and research before buying new hardware/system. But I agree that not everyone have the luxury to to that.

---

### Post by darkhatter on 2006-11-20
java is open source now...

---

### Post by kuja on 2006-11-20
If I remember right it won't be 'til March. ish.

---

### Post by darkhatter on 2006-11-20
its going to be soon, so I'm happy. I'm waiting for flash to go open source now

---

### Post by deanlinkous on 2006-11-20
> Ubuntu WILL install non-free drivers if no free driver is available.
I thought it would install whatever is needed for acceleration which means that ATI/Nvidia would get the binary drivers. Not sure about others.

> In fact you will end up using proprietary drivers even in gNewSense if you run closed hardware. 
WRONG!

> They also stated that whenever possible free software will be used.
Thay also have stated it is libre, and could be modified and distributable.

> Want a free OS? Don't buy non-free hardware!
? Maybe I am happy with the nv driver, maybe I just have one laying aroud. Actually, you may have a point but I still don't want those drivers included in the distro.

> Don't b*tch about a distro trying to be as functional as possible out of the box.
Then you can take that argument all the way to doing a deal with microsoft. Lets install codecs and everything. (probably what is down the road anyway)

---

### Post by deanlinkous on 2006-11-20
> the best hardware is closed. 
best if you want to do something that requires that hardware
happy with my onboard Via

> For those who does buy closed hardware it will install the non-free driver to help them get the most out of it. Can you tell me a open/free video card. Why cant I buy a nvidia and use free drivers.

> Actually according to people who made gNewSense, both Debian and Ubuntu include non-free firmware as part of the kernel (that no one really gives a damn about it seems, not even the kernel hackers) so maybe he would be better with gNewSense.  Debian does care and is suppose to do something about it immediately after teh release of etch.

> As for ideology and higher cause
Then you shouldn't care about Ubuntu becoming as buggy and having as much lock-in because without ideology you are begging for the proprietary run around.

---

### Post by prizrak on 2006-11-20
> I thought it would install whatever is needed for acceleration which means that ATI/Nvidia would get the binary drivers. Not sure about others.
How many times have I told you the same damn thing? If an open driver can do compositing (in case of AMD there are actually quite a few cards that can) it will be installed. nVidia is really the only one that can't do 3D without the binary drivers.
> WRONG! 
Oh really? Well how about you put a Broadcom wi-fi card in your gNewSense and get it to work w/o NDISwrapper (that uses a Windows driver). 
> Then you can take that argument all the way to doing a deal with microsoft. Lets install codecs and everything. (probably what is down the road anyway)
Why should I? If Ubuntu provides the needed functionality I will use it, it's a great OS. It also allows me to install all the codecs and flash, Windows doesn't come with them out of the box either. 
> best if you want to do something that requires that hardware
happy with my onboard Via
That is obviously a given, is Via open btw or was it just reverse engineered?
> Can you tell me a open/free video card. Why cant I buy a nvidia and use free drivers.
Intel is one I know about, don't know of anything else. If you are so adamant about being free, why support a company that sells proprietary hardware? Remember nVidia/AMD get your money when you pay for the card not when you install the driver. 
> Debian does care and is suppose to do something about it immediately after teh release of etch.

Hahahaha, sorry but Debian's development cycle is so slow that it's not even funny. By the way Ubuntu is based on Debian so if Debian changes it so will Ubuntu.
> Then you shouldn't care about Ubuntu becoming as buggy and having as much lock-in because without ideology you are begging for the proprietary run around.
Why does it have to have lock-in and become buggy? For now the drivers will be there, it has been stated that if the nouveau project gets some good results it will be considered for Feisty+1.

---

### Post by darkhatter on 2006-11-20
the nv driver supports my geforce 6100, the nv driver is good, I actually have a more stable system when I use it instead of the nvidia drivers (I think it has something to do with the shared memory).

Including Binary drivers isn't going to force nvidia to make open drivers, and not including them isn't going to do anything different. I don't think it matters. What they are saying with the mini lesson is alot better then not including them all together.

sorry if that doesn't make sense I'm getting tired, I'll do a better post tomorrow.

---

### Post by ubuntu27 on 2006-11-20
> **josys36 said:**
> Personally, and I know that this going to cause mass panic, but I would pay for Ubuntu if they charged. 

I run Linux because I think it is better then Windows. Not because it has free software. Heck I can get a ton of free software for Windows! There is even the time when I like a piece of software so much I pay for it! I love the idea of the free software movement, but let's fact it is just not very practical. People have house payments, car payments and other bills they need to pay. If I had an OS that was great, and everyone wanted an alternative to what is out there, why not just charge 20 bucks for it? It would be worth it if you hate your current OS or Windows enough. Like I said before I run Linux because I feel it is superior to Windows.

Jason

I like the way you think. I am not against paying for software either. But, this discussion, this issue is not about that. 

It is about Free software. Free = FREEDOM. 

> ***John* said:**
> I really dont understand why everyone has such a problem with this? :-k 

As long as ubuntu is free, I dont care in the slightest whether its made up of open or closed source software?


Can people pause for a moment and read what is  FREE software?

Here are the links:

[http://www.fsf.org/](http://www.fsf.org/)

[http://www.gnu.org/philosophy/philosophy.html](http://www.gnu.org/philosophy/philosophy.html)

[http://www.gnu.org/](http://www.gnu.org/)


**Resumed:**

What is [Free Software]("http://www.gnu.org/philosophy/free-sw.html")?

**&#8220;Free software&#8221; is a matter of liberty, not price. **To understand the concept, you should think of &#8220;free&#8221; as in &#8220;free speech&#8221;, not as in &#8220;free beer&#8221;.

[Free software]("http://www.gnu.org/philosophy/free-sw.html") is a matter of the users' freedom to run, copy, distribute, study, change and improve the software. More precisely, it refers to four kinds of freedom, for the users of the software:

    * The freedom to run the program, for any purpose (freedom 0).
    * The freedom to study how the program works, and adapt it to your needs (freedom 1). Access to the source code is a precondition for this.
    * The freedom to redistribute copies so you can help your neighbor (freedom 2).
    * The freedom to improve the program, and release your improvements to the public, so that the whole community benefits (freedom 3). Access to the source code is a precondition for this.

---

### Post by steven8 on 2006-11-21
Free Beer doesn't mean the drinker can go into the brewery and change the mixture to their taste.  That is the difference.  I have made freeware, but I have not given the sourcecode out with.  To be honest, my code is such a mess I'd be embarrassed to have anyone see it.  Free as in Freedom means the user can take the code for that software and change it as they wish.

Simple as that.

---

### Post by prizrak on 2006-11-21
> **darkhatter said:**
> the nv driver supports my geforce 6100, the nv driver is good, I actually have a more stable system when I use it instead of the nvidia drivers (I think it has something to do with the shared memory).

Including Binary drivers isn't going to force nvidia to make open drivers, and not including them isn't going to do anything different. I don't think it matters. What they are saying with the mini lesson is alot better then not including them all together.

sorry if that doesn't make sense I'm getting tired, I'll do a better post tomorrow.

Hmmm, the nv driver is quite unstable on my Go 6200 card (I'm assuming that's what you have since it's shared memory) the binary driver works well though. I guess it is very dependant on alot of different things.

---

### Post by bailout on 2006-11-21
I have no objection to closed drivers as long as they are free. I think it is pretty clear that ATI/nvidia are not going to open up all their secrets by going open. I just want good drivers like I get for windows that don't cost me extra.

As to the 'if we use closed drivers there won't be any pressure on them to open their drivers' argument, I don't think it makes any sense. How does it put pressure on them if we use open independent drivers? The only effect of that is the companies will see it as pointless to spend resources developing linux drivers that no one wants to use and we will only have open drivers that wont work as well as closed drivers from the manufactures could.

---

### Post by tomcheng76 on 2006-11-21
after reading the pessage in [Ubuntu should reconsider]("http://www.nuxified.org/blog/ubuntu_down_the_drain")
I strongly aggree with the writer Danijel Orsolic. Free is a very important part for a linux distro. A linux distro should not include any non free package by default as it may faces illegal problem and i think that it is contradict to the GPL. It is because if distro includes nonfree package by default, it encourages people to use those non free things which acturally has a free alternative. Also, a 3D Desktop by default is not good for those old pc user. If users want to install, they will ask help in Ubuntu Comnunity. By promoting PC seller to use Ubuntu as OS and giving a better support and a better (bug free) Ubuntu. Non free and 3D Desktop is not what i what!

Proprietary software is software that is not free or semi-free. Its use, redistribution or modification is prohibited, or requires you to ask for permission, or is restricted so much that you effectively can't do it freely.
Ubuntu Developers, Please read this again......
The Free Software Foundation follows the rule that we cannot install any proprietary program on our computers except temporarily for the specific purpose of writing a free replacement for that very program. Aside from that, we feel there is no possible excuse for installing a proprietary program.
[http://www.gnu.org/philosophy/categories.html](http://www.gnu.org/philosophy/categories.html)

---

### Post by Turin Turambar on 2006-11-21
Calm down, whiners! ;)

Ubuntu Feisty will NOT support 3D desktop if your video card/system cannot do it!! You will probably be asked if you want to install it or not. It's an optional thing. Same is with non-free codecs/drivers. You WILL be asked if you want them!

That's how I got it anyway. You will NOT be persuaded to use something you don't like.

And I strongly disagree with Danijel.
He said that *"the current popularity of Ubuntu will be marked as its peak, before it consolidates and starts falling back."*

Take a look at [www.distrowatch.com](www.distrowatch.com) list and set the date to "last 7 days". You'll notice the Mint as a no.1 distro.

Do you know why?
It's Ubuntu on steroids - it has the stuff people want- codecs and other "dirty" software. But basically it's Ubuntu.
So, no, I don't think Ubuntu will fall back with Feisty. To the contrary, I think it'll attract more users, especially those that are now on Mint.

---

### Post by hanzomon4 on 2006-11-21
I think this is great, especially since it will ask you first and then install if you want it. No evil here folks, it's just making it easier to do what most of us do anyway. 

If you want oss drivers help build them or stop buying software that has sh*tty oss support. I like the oss philosophy, but you can't force others to believe in it. Vote with your dollars folks.

---

### Post by jdq997 on 2006-11-21
The majority of people in the real world don't care about if something is open or closed source.  You guys need to grow up and get over this immature notion of "software freedom" with your petty demand that everyone should give up the source code to the software that THEY wrote.  It is nice that some are willing to do this, but those who demand it are childish.  The easier Ubuntu is to use the better.  I am glad they are incorporating some of these options into the installation.

 - Jason

---

### Post by Keith_Beef on 2006-11-21
> **PriceChild said:**
> The one big problem about open sourcing drivers, is that by its very nature, it reveals EXACTLY how your hardware works.


It also reveals how you made absolutely flaky hardware, and "fixed" it in the software.

---

### Post by Henry Rayker on 2006-11-21
I don't think inclusion of non-free software is the answer. It's not a matter of "growing up" that you're talking about, it's a matter of "giving up". The idea that your software should be transparent isn't childish, in fact, I'd say it's more mature.

When you were a child, your parents would tell you something happens "just because" or similar. They don't explain to you all of the things behind it. As you mature and age, they will tell you more and more of the details. That's the way it is with software.

Open software isn't a sort of thief's notion; we don't want the code so we can steal it. We want the code so we can see what is going on, repair or slightly alter it. For isntance, I have a program on my Windows machine that completely blocks usage of the ALT+Number keys; If the program that did this were open source, I could get a look at it and try to find out WHY. The program doesn't actually USE the ALT key, so I'm baffled. Contacting the person who made the app was fruitless.

There is nothing childish about wanting to know how code is affecting your system.

---

### Post by deanlinkous on 2006-11-21
> How many times have I told you the same damn thing?About the same number of times you have told me that Ubuntu is free software I guess. I was just reading the spec and seen this part - **Both NVIDIA and ATI proprietary drivers will be installed by default** 
 
> Oh really? Well how about you put a Broadcom wi-fi card in your gNewSense and get it to work w/o NDISwrapper (that uses a Windows driver). That isn't what you said. Sure I can choose to run closed hardware and a closed driver but nothing says I **WILL** do that. You made it sound as if it would automatically install closed drivers if my hardware was closed.

> is Via open btw or was it just reverse engineered?a little bit of both I think :) Can you imagine any company choosing to go open when they see everyone buying nvidia and using the proprietary drivers. So maybe you are right we should boycott nvidia products.

> Intel is one I know about, don't know of anything else. If you are so adamant about being free, why support a company that sells proprietary hardware? Remember nVidia/AMD get your money when you pay for the card not when you install the driver. 
Intel video **CARD**? Nobody makes one so what can I choose.... I have to pick a closed one and refuse to use their drivers. It is still a great card. Oh and I have never bought a NEW video card so someone paid nvidia but I only paid my five bucks to the dude on ebay. :) But you have a good point, no more buying proprietary cards at all. 

> Hahahaha, sorry but Debian's development cycle is so slow that it's not even funny. 
Really? Yea ok.... Dont confuse the development cycle with actual official releases okay.
> By the way Ubuntu is based on Debian so if Debian changes it so will Ubuntu. Loosely based and you honestly think if debian removes the non-free firmware that ubuntu will leave it out? Nah I don't think so.

---

### Post by deanlinkous on 2006-11-21
I think Ubuntu has seen the pinnacle of their popularity stint and will now just level out. Seems like a lot of users only use it because everyone else does.

---

### Post by steven8 on 2006-11-22
> Seems like a lot of users only use it because everyone else does.

Actually, if you want any distro to be a challenger in the market, that's the way it will be.  Otherwise we will only have even more scattered fragments.  There is strength in numbers, but those numbers have to be united.

---

### Post by deanlinkous on 2006-11-22
what market? 

scattered fragments == united

100 debian users
100 ubuntu users
100 gNewSense users
-----------------
300 linux user
----------------
(hopefully) 300 less windows users :)

---

### Post by steven8 on 2006-11-22
Well, I'd guess I was thinking the OS market.  :-)

I'd guess, anytime we ring up a minus against the windows market we have won, eh.

---

### Post by steven8 on 2006-11-22
Now, what we need is this:

100 debian users - not fighting with
100 ubuntu users - not fighting with
100 gNewSense users - not fighting with the aforementioned 2 groups of users =
-----------------
300 united and happy linux users

:-)

---

### Post by prizrak on 2006-11-22
> About the same number of times you have told me that Ubuntu is free software I guess. I was just reading the spec and seen this part - Both NVIDIA and ATI proprietary drivers will be installed by default

nVidia will have binary unless the card is known to not support compositing at all. ATI will get free drivers if they support compositing on that particular card (or if there is no compositing possible) and binary if that's the only way to get compositing to work. 
> That isn't what you said. Sure I can choose to run closed hardware and a closed driver but nothing says I WILL do that. You made it sound as if it would automatically install closed drivers if my hardware was closed.

Misunderstanding on your part, I meant to say that if you choose to run gNewSense on closed hardware you will have to install the non-free drivers to get it to work (provided no free driver is available). Sometimes there is no choice, the laptop I got has a Broadcom based Bluetooth adapter (not something that was possible to find out till I got it). 
> Loosely based and you honestly think if debian removes the non-free firmware that ubuntu will leave it out? Nah I don't think so.
From what I read about the issue is that the said firmware does have the source available for it, it just hasn't been taken care off yet.  Ubuntu for the most part uses the Debian kernel so it's quite likely. It also very much depends on that firmware, if it's basically useless at this point there isn't much reason to keep it there.
> 
what market?

scattered fragments == united

100 debian users
100 ubuntu users
100 gNewSense users
-----------------
300 linux user
----------------
(hopefully) 300 less windows users

I agree.

---

### Post by easyease on 2006-11-22
i detect an air of the old "linux snobbery" in some of these replies....:D

---

### Post by Kittie Rose on 2006-11-22
The slippery slope is a logical fallacy used by conservatives. There is no reason to presume it without directly comparable historical precedence.

---

### Post by wayne_za on 2006-11-22
Well I will take all I can open source or not, just as long as it works.

---

### Post by OttifantSir on 2006-11-26
Being a new user of Ubuntu, and just four months out of a three-year absence of computers, I can`t point to anything in particular, except my own knowledge on the subject. And it`s scant.

I received a very old laptop from my sister. I was complaining about not having a computer, and she was at the time using a seven-year-old laptop my dad had used for work that long ago. It`s an original Pentium 300 Mhz with 192 MB RAM, crappy touchpad and 6.2 GB HDD. I installed Windows XP Pro on it (it actually had 95 still) and the Office suite. I was out of storage space, it took 15 minutes to boot, and connecting to the Web? Well, I needed to install drivers to use the USB connection on my cable modem, but I didn`t have the space to do so. Complained some more around me, and my mother`s boyfriend gave me his old server, a P3 1.26 Ghz, 1536 MB RAM, HP NC3163, 4 RAID-drives of 200+ GB total. Having tried a few options, I eventually found this version of Ubuntu 6.10 (for machines with less than 192 MB RAM).
The whole package, with an office suite and ability to connect to the Web, and watching movies and playing music, well anything I wish to use it for, takes about 2 GB of storage on this old laptop. But, that`s still a whole lot less than when installing Microsoft system, and..... (drum roll) This very old and tired laptop now performs as good, and when listening to music, better than the P3.

What`s this got to do with Ubuntu being on a slippery slope? Well, I for one love having a laptop I can carry with me. I know of nothing else that could have brought this old laptop back to good use. Only gripe I have on Ubuntu is that I didn`t discover it sooner.

I remember reading about Linux when Linus first made it. I was immediately drawn to it. Even back then when Windows 95 was fresh, I hated it and wanted to move to Linux. Got a copy of RedHat (6.2 I believe it was) and wanted to install it. But, I was still using a family computer, and the family was pleased with the ease of use Windows offered. I wasn`t allowed to install it.

The point to all this? I know Ubuntu is better than Windows. I will continue to use it. I will advice anyone I know to use it. As has been said here before, we will prevail when our numbers grow. The ideology behind it will be a hard one to accomplish, possibly even impossible, but the starting point is one that`s so much better than Microsoft from a pure performance stand point.

When we realise that it might be impossible to achieve the goal of GNU/Public License, we will still do our best to make the best of both worlds. A world where the following scenario might happen: Take Microsoft`s Office suite. They still charge money for it, but the source is open for people to see. They are free to make alterations to it and post it on a public server, as long as they report the alteration to Microsoft. Microsoft retains the right to make the Office suite better by including alterations users/developers have made. The users/developers have agreed to this because Microsoft has made a contract with the users saying that all work that is included in future updates/releases will be credited to the user/developer that made the alteration. If the alteration is of a certain usefulness and/or size, Microsoft will make contact with the user/developer and the user/developer will receive a financial gratitude for the work.

This will probably never happen with Microsoft or Apple or any of the largest software firms in existence today, but it was also just an example of what might happen. Now, heap on the comments on what I haven`t thought of. It`s alot, I know. But is the basic idea so bad? Wouldn`t this combine the best of what we have today (payment for our work) and what we want (ability to change the program/system to our liking and distributing the alterations to help our neighbours)?

---

