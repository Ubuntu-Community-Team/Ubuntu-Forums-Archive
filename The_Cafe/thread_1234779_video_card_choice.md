---
title: "video card choice"
date: 2009-08-08
forum: The Cafe
---

### Post by mystmaiden on 2009-08-08
I'm mulling over actually breaking down and buying a video card for my sony Or building a new machine budget permitting. What is the best video card for use with Ubuntu? Right now I am using hardy lts if I do a new build though, it'll be jaunty.

myst

---

### Post by 3rdalbum on 2009-08-08
Get something Nvidia-based. It's not even worth thinking about anything else.*

I'm using an Nvidia GTX260 (Innotek-branded) which is regarded as one of the best bang-for-buck, mid-range graphics cards.

The Nvidia 9000-series cards also work well on Linux; I have a friend who has a 9600 and that works fine. But they're getting a bit old now, although they are still being made.

*Nvidia has more reliable, more efficient drivers on Linux than ATI. You get better performance and you can run Compiz while using 3D programs and video players. In addition, if you have a current version of Mplayer, certain video formats can have their decoding offloaded to the graphics card; only Nvidia supports this at the moment.

---

### Post by mystmaiden on 2009-08-08
Thanks, 3rdalbum - I'll check them out. 

mystmaiden

---

### Post by handy on 2009-08-09
Because AMD/ATi's Catalyst driver has been so unreliable, it is causing a great deal of work to go into the ATi Open drivers & associated packages.

Which from personal experience, is starting to change things.  

The current Open ATi GPU drivers are giving many people the best 2D performance they have ever had on their ATi GPU's, I know because I'm one of them.  

The 3D is improving also, some are saying that they can see in perhaps 12 months the ATi Open drivers will be the best available for any brand of GPU.  Though really being able to say when is impossible I think.

This will give us drivers that keep up with the development of the Linux/BSD kernels, x.server, mesa & all of the other associated packages.

So as far as what brand of video card to buy is concerned, the choice has become a lot more difficult over just the last couple of weeks.

I use Arch, due to its packages being more cutting edge than most, I have been living through the ATi closed source nightmare, & have just very recently finally become free of the closed drivers, as I don't personally need 3D on my Arch box.  

As previously stated, others are using the most current pre-release Open driver packages & they are finding great improvement on 3D, which translates to meaning limited 3D where once there was none for that card at all.  

These changes are happening fast.

---

### Post by stwschool on 2009-08-09
Ok so lots of correct stuff above. My own experience:

NVIDIA: GTX250 on my home pc is beautiful. The proprietary driver is excellent. All my windows games work fine in Wine, and compiz is glitch-free. Games + Compiz + Movies can co-exist and I can have different items on different panels in cube or expo if I wish without hassle.

ATI: Complicated.
   Open-Source: 8.10 drivers were lacking in features but stable for me, with no flickering. The drivers on 9.04 were poor though the newer releases may be better, if handy is right.
   Proprietary: The drivers that jockey/envy will give you are awful. Video + compiz is impossible and forget gaming (even Linux games, forget Wine). Downloaded the latest from ATI and just ran the installer, and it's a hell of a lot better. Linux games are good now, though Wine games are still a problem (for instance even popcap stuff won't run on it, where it'll run on crappy non-gaming Intel hardware).

Intel On-Board: It'll do 3D and games fine but performance badly lags Windows equivalents, judging from my attempts to run World of Goo on Windows and Linux using native versions on identical machines.

---

### Post by ssam on 2009-08-09
ATI are making a serious effort on open source drivers. have a look at this weeks progress [http://www.phoronix.com/scan.php?page=news_item&px=NzQ0MQ](http://www.phoronix.com/scan.php?page=news_item&px=NzQ0MQ)

---

### Post by mystmaiden on 2009-08-11
This is great, I've gotten a short course in video cards!

myst

---

### Post by SolarOnline on 2009-08-11
> **handy said:**
> Because AMD/ATi's Catalyst driver has been so unreliable, it is causing a great deal of work to go into the ATi Open drivers & associated packages.

I have to agree here.

GO nVIDIA! 

I've been using ATI for years now. But since they shelved any decent driver updates for certain cards and because the Catalyst drivers are not a full "blanket" solution def. go for nVIDIA.

---

### Post by DownTown22 on 2009-08-11
Another advocate for nVidia.

I currently run an eVGA 8500GT on my desktop (Ubuntu 9.04) and an XFX 9600GT in my media center (Ubuntu 9.04) and both run compiz, videos, etc worry free.  Now, I have not ran any games on these under Wine, but the 8500 used to run WoW pretty smoothly.

I also have a 9500 in my Asus laptop (Ubuntu 9.04 and Vista), and again, it runs everything wonderfully.  The 9500 also runs Fallout 3 under Vista very smoothly.

---

### Post by mystmaiden on 2009-08-11
I was looking at my motherboard specs today, this is an older machine - no PCI E so, I'm going to be limited on the choices. I was kind of hoping that I could get something that would easily move up to a new build but for now, I'll be happy if it just improves things and maybe let's me use compiz and boosts Poser a bit. I've run on onboard video for a long time - most anything is bound to be an improvement! After reading all the input, I'm thinking nvidia is the way to go.

mystmaiden

---

### Post by handy on 2009-08-11
> **SolarOnline said:**
> I have to agree here.

GO nVIDIA! 

I've been using ATI for years now. But since they shelved any decent driver updates for certain cards and because the Catalyst drivers are not a full "blanket" solution def. go for nVIDIA.

So you don't see that in a short while, ATi will have really good 3D support for their GPU's & via OPEN drivers, that can be maintained by the FOSS community & will therefore be able to be kept up to date with the downstream changes that occur in the kernel, x.server, & any other packages that require the drivers to be modified?

It has been & still is, the ATi Catalyst driver's inability to keep up with these changes that has been causing it to go from being useful (for some GPU's) to dreadful, then back to useful again, though on occasion it has done more than one dreadful in a row. :-|

I use both nVidia & ATi GPU's, & up until very recently I would only recommend nVidia GPU's to people. 

Though now, in the last few weeks the situation has changed.  

***Be prepared to see the ATi GPU's rise to dominance in the FOSS world.  ***

I could not recommend nVidia now because very soon their drivers will be the inferior ones, the nVidia drivers will become the ones that are slow to respond to changes in comparison to those from AMD/ATi, that is until of course nVidia release their code to the FOSS community, which at this stage there has been absolutely no sign of them doing.

---

### Post by Exodist on 2009-08-11
Traditionally nVidia has always been the best choice. BUT lately the last 3 nVidia cards I have purchased have died on me in within 6 to 9 months due to just running to hot. Mind you I dont buy cheap brands and I have excellent air ventilation in my cooler-master centurion case. My most recent purchase was a ATI Radeon 4850. This card runs super cool and very very fast. A Ati4850 can be  a little faster then nv9800 from nVidia depending on the game but very comparable and also MUCH CHEAPER. Now at first soon as you get it installed the ATI drivers in the repositorys is buggy and very unstable. Now the drivers from ATI/AMD website that is super easy to install works rock solid and has excellent performance.

SO IMHO, go with ATI for price and reliability while still having superb performance.

---

### Post by DownTown22 on 2009-08-11
If you don't have a PCI-e slot then you'd have to go with an AGP video card.  I don't think you'd be able to take the card with you if did a system update in the future - as I don't think the new motherboards support AGP anymore.

---

### Post by 3rdalbum on 2009-08-11
> **handy said:**
> So you don't see that in a short while, ATi will have really good 3D support for their GPU's & via OPEN drivers, that can be maintained by the FOSS community & will therefore be able to be kept up to date with the downstream changes that occur in the kernel, x.server, & any other packages that require the drivers to be modified?



AMD is not open-sourcing their drivers. That much is clear. The community is working on open-source drivers with AMD's documentation, but this will be slow to support new GPUs with full functionality.

> 
Though now, in the last few weeks the situation has changed.  


I've been reading Phoronix... what has changed in the last few weeks?

> I could not recommend nVidia now because very soon their drivers will be the inferior ones, the nVidia drivers will become the ones that are slow to respond to changes in comparison to those from AMD/ATi, that is until of course nVidia release their code to the FOSS community, which at this stage there has been absolutely no sign of them doing.

Neither has AMD/ATI. Nvidia has a massive head start on video decoding, a large head start on OpenCL, and a pretty big advantage on multiple GPUs. ATI's proprietary driver doesn't even support the HD 3870x2 - never has done.

It's nice to see that you're hopeful for the future, but I have no idea how ATI is going to overtake Nvidia unless Nvidia stops development on Linux drivers for a year :-)

---

### Post by handy on 2009-08-11
> **DownTown22 said:**
> If you don't have a PCI-e slot then you'd have to go with an AGP video card.  I don't think you'd be able to take the card with you if did a system update in the future - as I don't think the new motherboards support AGP anymore.

The new motherboards do not support AGP.

I have an expensive, (because I didn't want to buy a new motherboard, CPU & RAM XFX 7950GT 512/RAM, which uses an nVidia GPU that was built for PCI-e & was shoehorned into an AGP card.  It works very well, but boy was it hard to work out how to get it to work with Linux.

I had to turn OFF AGP in xorg.conf!

---

### Post by handy on 2009-08-12
> **3rdalbum said:**
> 
AMD is not open-sourcing their drivers. That much is clear. The community is working on open-source drivers with AMD's documentation, but this will be slow to support new GPUs with full functionality. 

I'm not sure if you think I was saying that AMD is open-sourcing their drivers? I wasn't saying that.  Though you probably know that.  

AMD will very likely help the open-source community with new GPU's.  When they find that very functional drivers are being written in open-source, why won't they just give the coders help & save themselves the effort/cost of writing the drivers themselves? As it is a win <-> win situation.

The community is currently working incredibly fast on the open-source AMD/ATi drivers, & great things are happening right now.  My 2D support is better than AMD/ATi have ever provided, this fact changed very quickly.

A quote from an ATi user follows:

*With the latest updates 3D Acceleration with the xf86-video-ati-git is a lot faster. glxgears is now running with 600fps (instead of 30). Compiz is quite usable. But there are still some artifacts.*

The ATi Open drivers are developing at an incredibly fast speed, so I say sit back & watch?

> **3rdalbum said:**
> 
I've been reading Phoronix... what has changed in the last few weeks? 

A few weeks ago I had nowhere to go, as the Catalyst drivers are crap at the moment, & the open drivers were only slightly better.

Then all of a sudden there was a new set of open-source packages which gave me the best 2D this machine has ever had.

The open-source drivers are now providing 3D for cards that it couldn't do it for at all before.  These changes happened very quickly.

> **3rdalbum said:**
> 
It's nice to see that you're hopeful for the future, but I have no idea how ATI is going to overtake Nvidia unless Nvidia stops development on Linux drivers for a year :-)

Do some research, all of the info' is available out there for anyone who wants to look.

You don't have to have the experience (as I have) to find out that things are changing very fast, & that as these open-source drivers develop for the ATi GPU's they are very likely going to end up forcing nVidia to open up there code.

It is all good as I see it. :)

I know that the last thing in the world you want to see is any open-source development slowed down for any reason, so even though after reading what I have just posted, I expect that you still disagree, that's fine :) I say let's not have an argument about it because it is only words, lets just sit back (in your case, I use both nVidia & ATi) & watch what the coming months have to bring.

I'm sure that you too hope that there is a brilliant explosion of ATi open-source drivers that eventually forces AMD/ATi to give support to the FOSS community, after which nVidia eventually realises that it should do the same, which continues the chain reaction of companies opening their code. :KS

---

### Post by dardack on 2009-08-12
> **handy said:**
> 
AMD will very likely help the open-source community with new GPU's.  When they find that very functional drivers are being written in open-source, why won't they just give the coders help & save themselves the effort/cost of writing the drivers themselves? As it is a win <-> win situation.


Will very likely and them actually saying that are 2 totally different things.  If you have actual information that they are going to do this, I would love to see that.  Sorry I've been using Linux for 11 years and have always recommended bought nvidia cards because of their drivers, so what if they are closed source, at least they have worked relatively well.

> 
The community is currently working incredibly fast on the open-source AMD/ATi drivers, & great things are happening right now.  My 2D support is better than AMD/ATi have ever provided, this fact changed very quickly.


SO?  My 2d/3d support in nvidia is phenomenal for a long time now.  They are still very far behind nvidia.

> 
A quote from an ATi user follows:

*With the latest updates 3D Acceleration with the xf86-video-ati-git is a lot faster. glxgears is now running with 600fps (instead of 30). Compiz is quite usable. But there are still some artifacts.*

The ATi Open drivers are developing at an incredibly fast speed, so I say sit back & watch?


Yea watch, and watch nvidia keep putting new things in their drivers, sure ATI may catch them at some point, but why wait a year or 2 or 3 or whatever.  I mean pure video, mpeg2 offloaded, among many other things still sets nvidia far ahead.

> 
A few weeks ago I had nowhere to go, as the Catalyst drivers are crap at the moment, & the open drivers were only slightly better.

Then all of a sudden there was a new set of open-source packages which gave me the best 2D this machine has ever had.

The open-source drivers are now providing 3D for cards that it couldn't do it for at all before.  These changes happened very quickly.

As an end user, quickly to you, how long had someone(s) been working to get this part of the driver working.  I mean I doubt no work has been done on ATI open source drivers for that long.  So i have a hard time believing that it's all gonna be there that quickly.

> 
Do some research, all of the info' is available out there for anyone who wants to look.

You don't have to have the experience (as I have) to find out that things are changing very fast, & that as these open-source drivers develop for the ATi GPU's they are very likely going to end up forcing nVidia to open up there code.

I doubt anything is going to force either company to open their code.  You have high hopes, personally doubt either side is gonna open it up.

> 
It is all good as I see it. :)

I know that the last thing in the world you want to see is any open-source development slowed down for any reason, so even though after reading what I have just posted, I expect that you still disagree, that's fine :) I say let's not have an argument about it because it is only words, lets just sit back (in your case, I use both nVidia & ATi) & watch what the coming months have to bring.

I'm sure that you too hope that there is a brilliant explosion of ATi open-source drivers that eventually forces AMD/ATi to give support to the FOSS community, after which nVidia eventually realises that it should do the same, which continues the chain reaction of companies opening their code. :KS

Sounds good in a perfect world.  Me I'm skeptical that this will actually happen the way you see it happening.  The way I see, nvidia see's the open source drivers progressing so they bump up what their driver can do, and keep crushing ATI in the linux platform.  Yea i used to use ATI, but dropped them long ago, I still keep up on the news, but still read many things of artifacts and other things not working perfectly in their drivers.

---

### Post by handy on 2009-08-12
Sorry man, your attitude is too chauvinistic & therefore negative for me to bother with.  
That is not meant as personally derogatory statement; it is just how I see the situation.

Anyway, I've said what I have to say, those that are interested will keep their ear to the ground & do a little searching, those that are not won't. 

To both crowds I say watch & see, the times are definitely changing re: graphics card drivers & Linux/BSD, & most definitely for the better.

---

### Post by mystmaiden on 2009-08-12
Actually I've found some nvidia based pci cards, I'll probably go with one of those.

myst

edited to add: I was looking at the Sparkle GeForce 9400 GT card  it comes in pci 
[B]
 [/B]

---

### Post by mystmaiden on 2009-08-14
giving this a bump to see if anyone is familiar with the Sparkle GeForce 9400 GT - will it work with Ubuntu?

myst

---

### Post by mystmaiden on 2009-08-31
Nothing like answering my own posts but I was going through the last several pages of the hardware compatibility post and found this post by user11 
[html]http://ubuntuforums.org/showthread.php?t=361236&highlight=SLI&page=53[/html]in which he or she says:

>  Ubuntu, all variants and releases, cannot utilize drivers for PCI video cards. There is no troubleshooting for this anywhere. So as usual, I have to keep windows XP.I haven't found that anywhere else yet, so does anyone know for certain if that is accurate? I may be relegated to agp afterall, makes me glad I didn't buy the card last payday because there is no way I go back to Windows!

myst

---

### Post by cariboo on 2009-08-31
I've used a Linux variant since before there were AGP and PCI-e slots. I've never had a problem getting a PCI video card to work properly.

---

### Post by mystmaiden on 2009-09-01
Thank you, cariboo! I was hoping that would be the case.

mystmaiden

---

### Post by oboedad55 on 2009-09-01
> **mystmaiden said:**
> Thank you, cariboo! I was hoping that would be the case.

mystmaiden

Myst, this may be a stupid question but I didn't see it asked. Is your Sony a laptop?

--Jon

---

