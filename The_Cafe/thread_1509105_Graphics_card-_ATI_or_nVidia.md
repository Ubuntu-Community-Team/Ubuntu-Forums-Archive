---
title: "Graphics card- ATI or nVidia?"
date: 2010-06-13
forum: The Cafe
---

### Post by Dustin2128 on 2010-06-13
I've been wanting a new graphics card for a while, so I took the chance to look at a few when I went to best buy, and, as expected I saw only 2 main brands, ATI & nVidia. I've heard about major problems with ATI cards in linux, but unlike last time I bought a graphics card (forgetting to check if it was compatible with my motherboard; it wasn't) none of the nVidia cards specifically said linux or opengl compatible, which disturbed me. Yet several of the ATI cards I looked at said 'OpenGL 3.1 compatible'. In addition to this, I can get twice the amount of video RAM for the same price on a lower-end radeon card (1GB video ram for 69$). But again, driver problems I've been reading about are troubling.. I just want to know, having never used an ATI card, is it as bad as it sounds?

---

### Post by coolbrook on 2010-06-13
I have 3 different models of NVIDIA cards and no problems.  My ATI card works, but the support isn't the same.

---

### Post by NightwishFan on 2010-06-13
Open source drivers are farther for ATI I think, but Nvidia has them coming with the Nouveau project.

---

### Post by pwnst*r on 2010-06-13
Nvidia.

---

### Post by handy on 2010-06-13
Have a look here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by JPorter on 2010-06-13
If you're going to be using the proprietary driver from the GPU manufacturer, Nvidia really does have excellent driver support overall.

ATI lost my business about a year and a half ago when they orphaned 2/3 of their userbase by ceasing proprietary-driver support for everything but their newest "Radeon HD" series products.  At that time, my Thinkpad was barely 2 years old and the integrated ATI X1400 GPU used in my unit was still being sold in new laptops from a variety of manufacturers until less than 6 months before ATI suddenly abandoned all of those users and ceased driver support entirely for what they called "legacy" hardware.  At that time, the open source driver didn't even have fully bug-free Xv video acceleration, so that was a major problem.  

The other issue is that ATI's proprietary driver development has been very slow to respond to upstream changes in the kernel or in the X.org xserver, so they're often behind the distributions in terms of supporting current shipping X config and kernels. More than once, the Ubuntu devs have had to customize the ATI proprietary driver's packaging themselves in order to be able to ship it at launch.  To me, that's ridiculous.

The ATI open-source drivers have really come a long way in the last year, to the point that it's really very usable and largely bug-free on production systems, but they still don't have the kind of full 3D and power-management support that was present in the proprietary driver.

Nvidia seems much better about maintaining support for their products over a reasonable period of time, and their proprietary drivers work very, very well on all of my systems.  Their GUI configuration tool also works very well; I have several multimonitor systems that I administer and it has proven very reliable in setup and configuration of multi-display layouts without any config file editing needed. The third major bonus on Nvidia is their VDPAU hardware video-acceleration support, which is really stellar even on very inexpensive video hardware.  A sub-$40 Nvidia card that supports VDPAU will do full-screen accelerated 1080p video playback with very low CPU utilization.  That can be done with ATI hardware, but not as easily and without anywhere near the broad file-format and player software support that VDPAU offers.

My vote is +1 for Nvidia on Ubuntu.  ATI still needs to get their act together and make some basic driver support commitment to their customers, because there's no telling whether they'll suddenly drop support for current cards the way they did the last time.  My $0.02.

See the [forums at Phoronix]("http://www.phoronix.com/forums/") if you want to find the best discussions on video-driver-related issues under Ubuntu or other distributions.  Many devs from ATI and Nvidia also participate there, from both the proprietary driver teams and the open-source driver projects.

---

### Post by marcoftheknight on 2010-06-13
ATI is getting to the top but it's still behind Nvidia I beleive. It's only worth it to get ATI if you get a good deal. If they improve the ATI catalys soom like better crossfire support with extra performance and Better open 3d GL on dual monitor setups they will finaly reach the level they need to.

Thanks.

I ahve dual monitors 23inch and 19inch with latest ATI 10.5 ati catalyst drives and it works almost perfect seems to be a few bugs at startup and preformance issues seams to be really heavy on my computer. Same with watching DVD seems to have performance issues when it shouldnt.

I have HD radeon 5770 with 965 black AMD CPU with UDH3 gigabyte (built in HD4300 ati  card) I dont know how to utilize them to there full potential which is pisses me off then again I think I dont have the sudo skills needed really.

---

### Post by marcoftheknight on 2010-06-13
ATI is getting to the top but it's still behind Nvidia I beleive. It's only worth it to get ATI if you get a good deal. If they improve the ATI catalys soom like better crossfire support with extra performance and Better open 3d GL on dual monitor setups they will finaly reach the level they need to. And Please ati ati (now its just amd) go all out open source please please

Thanks.

I ahve dual monitors 23inch and 19inch with latest ATI 10.5 ati catalyst drives and it works almost perfect seems to be a few bugs at startup and preformance issues seams to be really heavy on my computer. Same with watching DVD seems to have performance issues when it shouldnt.

I have HD radeon 5770 with 965 black AMD CPU with UDH3 gigabyte (built in HD4300 ati  card) I dont know how to utilize them to there full potential which is pisses me off then again I think I dont have the sudo skills needed really.

---

### Post by KingYaba on 2010-06-13
ATI has the better price / performance ratio. How much are you looking to spend? Those 40nm cards are quite cool and power efficient so definitely look into 'em.

---

### Post by WinterRain on 2010-06-13
Nvidia.

---

### Post by mr.farenheit on 2010-06-13
from what i've seen ati semms better for linux.

---

### Post by RiceMonster on 2010-06-13
Nvidia, because it has good Linux drivers. I'll probably start buying ATI if the open source drivers ever get as good as the nVidia proprietary drivers.

---

### Post by |I|I|I|I| on 2010-06-14
At the moment I'm using an ATI 4850 card running dual 22" monitors. Havn't had any problems with the ATI open source drivers at all. Doing all the basic web surfing/videos/image editing etc and it's been fine.

---

### Post by khelben1979 on 2010-06-14
**nVidia** if you're on a low budget and don't like when things don't work as expected from the start.

One thing to note though, and that is the cards itself. Check closely on how the cooling solution looks like, if it uses aluminium or copper is essential for proper cooling and a more quiet operation.

If the ATi have a better cooling solution for a lower price I would recommend that instead and make sure to have 2 Linux kernels installed before proceeding, because otherwise you can end up with a X server which locks up your display upon booting if you're unlucky about how the ATi driver behaves about your video hardware.

ATi should work good with Linux nowadays if you choose a good model which is well supported by the ATi Catalyst software.

---

### Post by philinux on 2010-06-14
nVidia 8600GT here no problems at all. I see more problems on here with ATI. Maybe it's the older models.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Kazade on 2010-06-14
This is becoming a more and more difficult question to answer...

Nvidia's binary drivers are far better than ATI's binary drivers, that much is true. However, Nvidia's drivers aren't flawless, I've got two laptops with Nvidia chipsets, one suffers corruption when compiz is enabled, the other misdetects the monitors resolution so I have to use a custom EDID (may not be directly Nvidia's fault I'm not sure).

The other thing with Nvidia is that they *still* don't support Xrandr which allows you to set the screen resolution with Ubuntu's built-in tools. ATI has had that a while. ATI hardware generally has better performance for the price, even still Nvidia wins out when you are considering the closed driver...

However, ATI are actively releasing specifications for their hardware *and* employ people to work full time on the open source drivers. These drivers are rock solid stable in comparison to both Nvidia's and ATI's drivers but they suck on performance and features at the moment (but that's improving fast). Nvidia basically couldn't care less about open drivers or specifications. 

Once the open source ATI drivers move over to the Gallium3D framework they will start inheriting features (like video acceleration etc.) automatically when they are implemented for Intel or Nouveau. Nouveau is the open source Nvidia driver, but progress is slower than the open ATI ones because they don't have specifications to work from.

I think if you aren't intending on buying another card for some time, and you aren't playing cutting edge games, or you want to support an OSS friendly company. ATI will be your best bet. If performance matters a lot to you, or if you don't have the patience to wait out for the rapid improvements in the open source ATI drivers, then go with Nvidia.

I guess to summarize:

ATI:
   Binary:
       - Supports Xrandr
       - Good performance
       - Crazily buggy and don't support recent kernels/X
       - Supports GL 3.x and 4.x
       - Doesn't support KMS
   Open source:
       - Release specifications for everything
       - Employ developers
       - Rock solid stable
       - Improving REALLY fast
       - 2D and 3D acceleration
       - Not great on performance, lacking features, only support GL 2.x
       - Supports KMS
       - Will inherit a bunch of features and performance improvements in the upcoming move to Gallium3D

Nvidia:
   Binary:
       - Really stable
       - Good performance
       - Doesn't support xrandr
       - Doesn't support KMS
       - Regular releases, supports recent kernels
   Open source:
       - Nvidia don't release any specifications or open source drivers
       - Nouveau is reverse engineered, slower progress
       - Nouveau supports KMS
       - Nouveau has limited 3D acceleration support on some chipsets
       - Nouveau has 2D acceleration

Incidentally, I've been running the xorg-edgers OSS ATI drivers on an R700 for some time to do 2D/3D programming. Aside from loading textures into GL quite slowly I've not had any issues. I've played a bunch of games from Osmos to Lugaru and Penumbra with no problems and smooth gameplay (granted, they are hardly pushing the limits of 3D graphics though).

---

### Post by Linuxforall on 2010-06-14
Even cheapest nvidia with proprietary drivers will do VDPAU and unload all HD movie load to GPU, something that till today ATI can't do, no matter how high end it is. ATI has no VDPAU or its equivalent and none of the media players in Ubuntu have anything for ATI either, my dual GPU ATI 4850 runs like junk compared to my cheap nvidia 8400GS.

---

### Post by xsandz on 2010-06-14
In respect to cost u may have to spend a litlle bit more in NVIDIA but from the performance respectives...i wud like to go for NVIDIA blindly. With some proprietary drivers NVIDIA is simply awesome and the performance is simply flawless. And if i compare both the cards in respect to the heating during running high resource eating applications ....again NVIDIA wii be the one to be the coolest :) even without having much expensive cooling system. So overall my vote simply goes for NVIDIA as everybody knows that the GPUs' performance is really inversely proportionate to the heating during running high end applications.

---

### Post by fluteflute on 2010-06-14
I think from the number of people here with differing opinions the truth is clear: it doesn't matter all that much. 

(But I would recommend googling the card you intend to buy, just to check there's not lots of people with problems on Linux.)

---

### Post by NCLI on 2010-06-14
nVidia cards are more expensive, but they are stable, and definitely have the bet Linux drivers ATM.

---

### Post by 98cwitr on 2010-06-14
my 8600GT still has framing issues @ 1680x1050 with the latest prop. driver :(

---

### Post by philinux on 2010-06-14
> **98cwitr said:**
> my 8600GT still has framing issues @ 1680x1050 with the latest prop. driver :(

I got the same card. What are the symptoms?

---

### Post by 98cwitr on 2010-06-14
> **philinux said:**
> I got the same card. What are the symptoms?

video playback (VLC, Mplayer, etc...doesnt matter), high frame rates have a horizontal split or two per frame. It is like the GPU will write the top half of the frame first and then the bottom half afterward (replace half with third if HD content is present). This only happens at high frame rates...screen is set @ 52Hz (default).

---

### Post by philinux on 2010-06-14
> **98cwitr said:**
> video playback (VLC, Mplayer, etc...doesnt matter), high frame rates have a horizontal split or two per frame. It is like the GPU will write the top half of the frame first and then the bottom half afterward (replace half with third if HD content is present). This only happens at high frame rates...screen is set @ 52Hz (default).

Righto, not seen that here.

---

### Post by BrokenKingpin on 2010-06-14
Nvidia

---

### Post by cascade9 on 2010-06-14
> **98cwitr said:**
> video playback (VLC, Mplayer, etc...doesnt matter), high frame rates have a horizontal split or two per frame. It is like the GPU will write the top half of the frame first and then the bottom half afterward (replace half with third if HD content is present). This only happens at high frame rates...screen is set @ 52Hz (default).

Same card here, and I havent had that problem.

---

### Post by Dustin2128 on 2010-06-14
well my budget is about 100$, an the ATI cards had the most bang for the buck under a hundred but the other card I was looking at was the nvidia 8400 for about 70$

---

### Post by limestone on 2010-06-14
I think I read somewhere that Ubuntu got better support for Nvidia.. I got ATI in my laptop ant got no problems, then again.. which is better? Something tells me ATI is faster for some reason..

---

### Post by JPorter on 2010-06-14
> **Kazade said:**
> Once the open source ATI drivers move over to the Gallium3D framework they will start inheriting features (like video acceleration etc.) automatically when they are implemented for Intel or Nouveau.

If the ATI open source drivers actually go to Gallium3D in the next year, I will be very, very surprised.  The devs have done really amaazing work on the driver in the last year, but the switch to Gallium will be anything but trivial.  They really need to get their (significant) KMS gremlins worked out before tackling that.

I fully agree with everything else you posted, though!

---

### Post by Shining Arcanine on 2010-06-14
I use Nvidia. The last time I used ATI was a disaster for me.

---

### Post by cascade9 on 2010-06-15
> **Dustin2128 said:**
> well my budget is about 100$, an the ATI cards had the most bang for the buck under a hundred but the other card I was looking at was the nvidia 8400 for about 70$

$70 for a 8400?!!??!!?? They should be half that.

---

### Post by Kazade on 2010-06-15
> **JPorter said:**
> If the ATI open source drivers actually go to Gallium3D in the next year, I will be very, very surprised.

Prepare to be surprised :) 

The Gallium3D driver for R300-R500 chips is almost done and it's performance is already better than the classic one[1]. It's not unlikely that it becomes the default by 11.04. The R600g driver is still WIP progress but work is flying along. Can't wait :D

[1] [http://www.phoronix.com/scan.php?page=article&item=ati_r300g_june&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r300g_june&num=1)

---

### Post by handy on 2010-06-15
From the look of it the r300g (Galium) driver is being incorporated by the guys who play on the cutting edge ATi GPU wise in the Arch forum. There is also talk of using r600g. Which is cool as I'm using a R600 series. :)

---

### Post by Starks on 2010-06-16
The 10:1 ATI to Nvidia laptop offering ratio these days is pissing me off.

---

### Post by handy on 2010-06-16
> **Starks said:**
> The 10:1 ATI to Nvidia laptop offering ratio these days is pissing me off.

What you wrote really made no sense. Could you use more words & actually say what you mean. You might even attract a reply that means something back at you.

---

### Post by cascade9 on 2010-06-16
> **handy said:**
> From the look of it the r300g (Galium) driver is being incorporated by the guys who play on the cutting edge ATi GPU wise in the Arch forum. There is also talk of using r600g. 

Woohoo! Cool, I've got a 9600XT (r300). 

> **handy said:**
> Which is cool as I'm using a R600 series. :)

Thats right, rub in your superiour GPU :lolflag:

---

### Post by handy on 2010-06-16
> **cascade9 said:**
> 
Woohoo! Cool, I've got a 9600XT (r300). 

I hope the Gallium stuff helps already?

> **cascade9 said:**
> 
Thats right, rub in your superiour GPU :lolflag:

You must be the first person that has ever called my HD2600Pro superior at anything! lol

Have a look at the last 5->8 posts in this thread to see what has inspired my post?

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

---

### Post by joshmuffin on 2010-06-16
I love my nvidia

---

### Post by cascade9 on 2010-06-16
> **handy said:**
> I hope the Gallium stuff helps already?

I havent been running it lately, but since I gave the old nVidia Ti 4200 to my mum today, its going back into a system in the next few days. 

> **handy said:**
> You must be the first person that has ever called my HD2600Pro superior at anything! lol

Have a look at the last 5->8 posts in this thread to see what has inspired my post?

[http://bbs.archlinux.org/viewtopic.php?id=79509](http://bbs.archlinux.org/viewtopic.php?id=79509)

Honesty, those last few posts are just leaving me wondering how exactly I get gallium going. :| 

I'll figure it out though ;)

---

### Post by Starks on 2010-06-16
> **handy said:**
> What you wrote really made no sense. Could you use more words & actually say what you mean. You might even attract a reply that means something back at you.
By almost a 10:1 ratio, great ATI-based notebooks are more readily available than great Nvidia-based notebooks. The issue is further compacted by the lack of diverse, cost-effective performance cards for notebooks.

If things aren't better for the Nvidia scene by the Fall, I may have to endure the nightmares of fglrx.

---

### Post by handy on 2010-06-16
> **Starks said:**
> By almost a 10:1 ratio, great ATI-based notebooks are more readily available than great Nvidia-based notebooks. The issue is further compacted by the lack of diverse, cost-effective performance cards for notebooks.

If things aren't better for the Nvidia scene by the Fall, I may have to endure the nightmares of fglrx.

Thanks, my slow old brain got it that time. :)

The guys on the Arch forum are pretty happy with what Catalyst 10.6 is doing at the moment.

It is using much less RAM & CPU usage. The 2D acceleration is apparently really working incredibly well also.

---

### Post by Starks on 2010-06-17
I want a strong dual-boot machine and Nvidia proprietary drivers are right up my alley (not to demean Gallium development).

Plus with VDPAU and PhysX, it's really no contest.

---

### Post by cascade9 on 2010-06-17
> **Starks said:**
> I want a strong dual-boot machine and Nvidia proprietary drivers are right up my alley (not to demean Gallium development).

Plus with VDPAU and PhysX, it's really no contest.

ATI has its own version of VDPAU- XvBA (4000 series or higher ATI cards.) Probably not as mature as VDPAU, but its working. 

I *think* you can hack ATI cards to do PhysX, but since I'm not that much of a gamer I've never really looked into it.

---

### Post by Starks on 2010-06-18
xvba and vaapi are a joke right now.

---

### Post by JPorter on 2010-06-20
> **Starks said:**
> xvba and vaapi are a joke right now.

Agreed.  I wish it were otherwise, considering I have an ATI X1400 in my Thinkpad, but agreed.

For video decode and acceleration, Nvidia is the absolutely undisputed top dog right now.  VDPAU works flawlessly on several different systems for me, with several different generations of Nvidia cards.

---

