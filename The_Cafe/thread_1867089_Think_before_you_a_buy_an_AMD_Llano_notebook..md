---
title: "Think before you a buy an AMD Llano notebook."
date: 2011-10-22
forum: The Cafe
---

### Post by hotweiss on 2011-10-22
I just purchased an AMD A6-3400m based Toshiba notebook.  Great reviews, great benchmark results and a great price.

First off, Ubuntu 11.10 doesn't boot at all.  You have to first install 11.04 and then upgrade to Ubuntu 11.10.  There seems to be some sort of kernel regression, and if you don't have the proprietary driver installed the screen will shut off.

Second of all, the Catalyst driver performs terribly.  It feels as if I'm doing everything at 15 FPS.  My 4 year old Core 2 Duo performed better in Ubuntu.

Mind you the notebook performs great in Windows.  And I will be waiting for Ubuntu 12.04. Hopefully the issues will be worked out by then.

If you want a nice Ubuntu experience, think twice.

**Edit:** The poor Catalyst driver performance has been fixed: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68)

Now all that is left is the mic problem: [https://bugs.launchpad.net/ubuntu/+bug/882427](https://bugs.launchpad.net/ubuntu/+bug/882427)

---

### Post by Pithikos on 2011-10-22
> **hotweiss said:**
> I just purchased an AMD A6-3400m based Toshiba notebook.  Great reviews, great benchmark results and a great price.

First off, Ubuntu 11.10 doesn't boot at all.  You have to first install 11.04 and then upgrade to Ubuntu 11.10.  There seems to be some kernel regression, and if you don't have the proprietary driver installed the screen will shut off.

Second of all, the Catalyst driver performs terribly.  It feels as if I'm doing everything at 15 FPS.  My 4 year old Core 2 Duo performed better in Ubuntu.

Mind you the notebook performs great in Windows.  And I will be waiting for Ubuntu 12.04. Hopefully the issues will be worked out by then.

If you want a nice Ubuntu experience, think twice.

Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.

---

### Post by del_diablo on 2011-10-22
> **Pithikos said:**
> Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.

My Fujitsu Siemens Amilo Pa 3553 with a broken bios disagrees with you.
The same performance as under Windows, and no problems beyond the fact that the BIOS was bugged beyond some veil of the galaxy.

OPs case: Completely botched and broken BIOS that likely run a lot of hacks to even get power managment to run in Windows.
Nothing new, it has been like this for ages.
Nothing will be fixed or adressed from Ubuntus side: Users have requests that Ubuntu included hacks to get power managment for the entire Turion X2 series of CPUs, which never got around.
Why there has not been compiled a list of "Good and bad laptop motherboards/BIOS for AMD" is beyond me.

---

### Post by LowSky on 2011-10-22
> **Pithikos said:**
> Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.

Don't spew that nonsense. I have a few PCs with AMD/ATI chipsets running great. The new stuff just needs some time to mature.

I was actually looking into a A6 lappy for myself, as my Netbook doesn't really cut it for me anymore. The power/battery/gaming ratio seems great. And I need a Windows lappy for some of my work/play.

Kernel regression happens. When I installed 11.04 my TV tuner card failed to work because of new ways the kernel handled firmware files, which worked fine form 9.04 up. Used 10.10 and then upgraded and the issue went away. Plenty of people had the same issue with wireless drivers, including myself, and it was Intel hardware that failed on that front, I recall the new Intel Sandybridge chips having an issue a while back too.

Lets not forget Nvidia Optimus issues too, some sound cards, or how about Don't choose Linux if you want to play games at full settings, or use Netflix streaming, or Apple's ipod.

Give it time for the community to catch up and most this stuff works. Just don't say things that are not true. It may be your opinion that AMD/ATI makes bad drivers, special thanks to a bad idea  awhile back to not support some models only 18 months old at the time. But that was years ago. The drivers now are pretty good and even on par with Nvidia offerings.

What is funny is when Ubuntu moves to Wayland. Say goodbye to Nvidia proprietary drivers as the company said they would stick with only X.

---

### Post by mr.generic.user on 2011-10-22
I have been using ATI/AMD graphics in Linux for a few years now, and aside from a little delay from launch to good drivers for new products I've had good luck.  I switched because Nvidia drivers got real bad in Linux a few years back, though to be fair, they have probably fixed it by now.

Your problems are likely 'new architecture' related with the APU and possible switchable graphics on FM1 boards.

Another similar issue I've seen with the ASUS Sabertooth for AM3+ is IOMMU.  This may also have made its way into the FM1 (I don't know) but it causes a similar issue and requires a kernel flag to enable support in desktop distributions.

Please don't just blame the hardware right away on a system that is less than 6 months old running a completely new architecture.  With drastic hardware changes, the support takes a little time and there will be some glitches initially.

---

### Post by ubupirate on 2011-10-22
> **Pithikos said:**
> Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.

Please stop with the FUD, thanks.

AMD/ATI works perfectly fine on Linux. I'm running Radeon HD4200 with 11.9 Catalyst on 10.04.3 and everything works like it should.

---

### Post by AloofObserver on 2011-10-22
> **Pithikos said:**
> Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.

There are plenty of AMD based laptops that work just fine. Mine for instance which has an HD 4250. My desktop which has an HD 6950 also works just fine under Ubuntu. 

On-topic: Avoiding AMD APU's for the time being would be a smart idea. They are great but unfortunately only under Windows 7. Maybe in a six months to a year everything will be properly ironed out.

---

### Post by kaldor on 2011-10-22
> **ubupirate said:**
> Please stop with the FUD, thanks.

AMD/ATI works perfectly fine on Linux. I'm running Radeon HD4200 with 11.9 Catalyst on 10.04.3 and everything works like it should.

Yep. Typing this from my main production machine which is powered by an AMD Radeon HD 6450. Apart from some minor issues in Catalyst (which are apparently fixed in the later versions) I can't complain. 

Their open source drivers far surpass NVIDIA's or Intel's at this point. If you want a good "out of the box" Linux experience a 3000 or 4000 series ATI/AMD card will probably be the best option.

---

### Post by hotweiss on 2011-10-22
This is the same issue I think:

[http://inebium.com/post/catalyst-11-9-gnome-shell-broken](http://inebium.com/post/catalyst-11-9-gnome-shell-broken)

---

### Post by Pithikos on 2011-10-22
> **kaldor said:**
> Yep. Typing this from my main production machine which is powered by an AMD Radeon HD 6450. Apart from some minor issues in Catalyst (which are apparently fixed in the later versions) I can't complain. 

Their open source drivers far surpass NVIDIA's or Intel's at this point. If you want a good "out of the box" Linux experience a 3000 or 4000 series ATI/AMD card will probably be the best option.

Who does really use the open source drivers? The point is that ATI has the worst support. Even if the driver works at the moment in a few years it won't. I had the worst experience with ATI and since I switched to nVidia I had zero. It's quite known that ATI doesn't care about Linux users as much as nVidia does.

---

### Post by collisionystm on 2011-10-22
> **Pithikos said:**
> Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.

+1 times infinity.

AMD can suck it.

I love Intel and their Sandy-Bridge is actually very very good. Not to mention... what works perfect on Linux 99% of the time?? Oh that's right, INTEL DOES.

---

### Post by JDShu on 2011-10-22
> **Pithikos said:**
> Who does really use the open source drivers? The point is that ATI has the worst support. Even if the driver works at the moment in a few years it won't. I had the worst experience with ATI and since I switched to nVidia I had zero. It's quite known that ATI doesn't care about Linux users as much as nVidia does.

What are you talking about? AMD actively works upstream with mesa and the Linux kernel to ensure awesome out of the box experience with their GPUs.

---

### Post by kaldor on 2011-10-22
> **Pithikos said:**
> Who does really use the open source drivers?  The point is that ATI has the worst support. Even if the driver works at  the moment in a few years it won't. I had the worst experience with ATI  and since I switched to nVidia I had zero. It's quite known that ATI  doesn't care about Linux users as much as nVidia does.

I do, on one machine. Also I know of a few others who used it while they used Linux. If you're not a gamer or laptop user the OSS driver works fine. Same goes for Intel, but Intel does have better Power Management. 

Nvidia cares about Linux users more than AMD does? Strange, considering AMD investing some resources into the open source Radeon project. NVIDIA did not do that with nv or Nouveau.

> **collisionystm said:**
> +1 times infinity.

AMD can suck it.

I love Intel and their Sandy-Bridge is actually very very good. Not to  mention... what works perfect on Linux 99% of the time?? Oh that's  right, INTEL DOES.

When was the last time you used an AMD/ATI card? If it was prior to 2009, your argument is most likely invalid.

---

### Post by wolfen69 on 2011-10-22
I have a strict rule now about laptops/netbooks. I will only buy them if they are Intel based. AMD/Ati doesn't give a rat's behind about linux users. And my desktops from now on will be a combo of Intel/Nvidia.

---

### Post by JDShu on 2011-10-22
I should clarify that the OP is right however. Llano is a very new chip and open source development being what it is, launch day support is incredibly difficult. Intel only just barely got it down this year with Sandybridge. An impressive feat, and one they've been working towards for a couple years now. If anybody remembers, Intel support two years ago was shaky and plagued with regressions.

Basically, I wouldn't  get a Llano chip yet for Linux because the support is not mature yet. Comments against AMD in general however, are uncalled for as the older cards (such as my HD4350) work very well.

---

### Post by ubupirate on 2011-10-22
> **wolfen69 said:**
> AMD/Ati doesn't give a rat's behind about linux users. 

Again, PLEASE STOP with the FUD. AMD/ATI works perfectly fine on Linux. Hell my HD4200 works better on Linux than it ever did when I had Windows.

---

### Post by wolfen69 on 2011-10-22
> **kaldor said:**
> 
Nvidia cares about Linux users more than AMD does? Strange, considering AMD investing some resources into the open source Radeon project. NVIDIA did not do that with nv or Nouveau.


AMD can kiss my....

They invested *some* resources? Wow. :roll: Their drivers are still garbage.

---

### Post by kaldor on 2011-10-22
> **JDShu said:**
> Comments against AMD in general however, are uncalled for as the older cards (such as my HD4350) work very well.

My old 300 Xpress (or whatever it was called) works quite flawlessly with the open source drivers also and has done so since Ubuntu 9.04. My new 6000 series GPU works with the open source drivers as well, but I use Catalyst because I happen to enjoy gaming.

I'm not saying there are no issues with AMD cards, but the FUD against AMD is insane.

> 
They invested *some* resources? Wow. :roll: Their drivers are still garbage.


And Intel is any better?

---

### Post by ubupirate on 2011-10-22
> **kaldor said:**
> I'm not saying there are no issues with AMD cards, but the FUD against AMD is insane.

I agree, the FUD against AMD/ATI is getting annoying.

> **kaldor said:**
> And Intel is any better?

Hell, Intel has problems running games on Windows, never mind on Linux.

My Intel GPU on my laptop, couldn't even run Urban Terror over 10FPS. My HD4200 plays WoW on Wine with Fair/Good graphics at a decent resolution and I am capped at my refresh rate which I couldn't do on Windows. And Urban Terror? Solid 125fps.

---

### Post by kaldor on 2011-10-22
> **ubupirate said:**
> I agree, the FUD against AMD/ATI is getting annoying.

Which AMD card do you use (if you do) btw? Just for comparison.

---

### Post by wolfen69 on 2011-10-22
> **ubupirate said:**
> Again, PLEASE STOP with the FUD. AMD/ATI works perfectly fine on Linux. Hell my HD4200 works better on Linux than it ever did when I had Windows.

FUD? I think not. I have had very bad experiences with ati and linux. Do you install OS's for a living? I do. 

I've done 100's of linux installs on every imaginable hardware under the sun. Guess what I have the most trouble with? Ati. 

Believe what you want, but *my* experience is worth a lot more (to me) than someone's opinion on a message board.

---

### Post by ubupirate on 2011-10-22
> **kaldor said:**
> Which AMD card do you use (if you do) btw? Just for comparison.

ATI Radeon HD4200 running Catalyst 11.9.

---

### Post by kaldor on 2011-10-22
> **wolfen69 said:**
> Believe what you want, but *my* experience is worth a lot more than someone's opinion on a message board.

That just sounds arrogant.

---

### Post by ubupirate on 2011-10-22
[delete me]

---

### Post by a2j on 2011-10-22
I just put together AMD A8-3850 2.9GHz Llano based desktop for personal use. Works fine with ubuntu 10.04LTS, but issues with 11.04 and 11.10

I guess I will try Debian or something...

---

### Post by wolfen69 on 2011-10-22
> **kaldor said:**
> That just sounds arrogant.

I meant *to me*, not anyone else. I edited it, OK?

---

### Post by collisionystm on 2011-10-23
> **kaldor said:**
> I do, on one machine. Also I know of a few others who used it while they used Linux. If you're not a gamer or laptop user the OSS driver works fine. Same goes for Intel, but Intel does have better Power Management. 

Nvidia cares about Linux users more than AMD does? Strange, considering AMD investing some resources into the open source Radeon project. NVIDIA did not do that with nv or Nouveau.



When was the last time you used an AMD/ATI card? If it was prior to 2009, your argument is most likely invalid.

Not invalid at all sir. Not invalid at all....

---

### Post by Pithikos on 2011-10-23
> **a2j said:**
> I just put together AMD A8-3850 2.9GHz Llano based desktop for personal use. Works fine with ubuntu 10.04LTS, but issues with 11.04 and 11.10

I guess I will try Debian or something...

Have you tryied just keeping some elements(VGA driver, kernel) locked while updating?

Else I would suggest OpenSuse. Debian feels a bit too bland for home use.

---

### Post by hotweiss on 2011-10-27
OK, my AMD graphics problem is fixed thanks to this fine gentleman:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68)

Now if someone can help me with my mic problem:

[https://bugs.launchpad.net/ubuntu/+bug/882427](https://bugs.launchpad.net/ubuntu/+bug/882427)

---

### Post by satanselbow on 2011-10-27
> **hotweiss said:**
> OK, my AMD graphics problem is fixed thanks to this fine gentleman:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005/comments/68)


Well done for keeping your head and finding a solution while all about you lose their's :D

I've been looking to get a new laptop for a while and the specs on some of the AMD/ATI machines frequently blow Intel out the water as far as bang per buck goes - the link you found might be the deal clincher :popcorn:

---

### Post by oscarivera9 on 2011-10-27
> **wolfen69 said:**
> I have a strict rule now about laptops/netbooks. I will only buy them if they are Intel based. AMD/Ati doesn't give a rat's behind about linux users. And my desktops from now on will be a combo of Intel/Nvidia.
I had read in quite a few places that AMD & ATI Radeon were collectively working on developing support for Linux and so I built my new PC (which I am using right now) with this idea in mind, and I do NOT regret it one bit.  I have an integrated Radeon HD4250 and an ATI Radeon HD 5770 both running in Cross Fire X with no problems at all in my Ubuntu Studio 11.10 setup.  The graphics are great and the 3D also works flawlessly.  The only complaint I have is that Gnome 3's top panel looks kind of funky and the whole desktop flickers when I move the mouse, but all of that I will attribute to Gnome 3 still waiting to mature because when I use Unity (almost always), I have ZERO problems whatsoever.
However, as to the original post:  **Think before you buy an AMD Llano notebook**.   Well, that is exactly what I did when I was doing my research prior to building my new PC.  I DID look into the AMD Llano APU and after doing as much research as I could, I came to the conclusion that AMD's Llano is quite simply too new to be compatible with Linux as of now.  So, I opted against it, instead I decided to go with an AMD Athlon X3 Triple Core 3.2 GHz CPU and an ATI Radeon HD 5770 and so far it's been superior to my previous PC which is Intel based with Nvidia graphics.
All in all, my conclusion is this: Although AMD & ATI Radeon (owned by AMD) have stated that they will be supporting Linux as much as possible by providing the proper drivers for us to use, there is still nothing as effective as doing your research before you go out and buy something and expect it to just work out of the box with no problems whatsoever.  Do your homework and you will always get the best results.  :wink:

---

### Post by kaldor on 2011-10-27
> **oscarivera9 said:**
> All in all, my conclusion is this: Although AMD & ATI Radeon (owned by AMD) have stated that they will be supporting Linux as much as possible by providing the proper drivers for us to use, there is still nothing as effective as doing your research before you go out and buy something and expect it to just work out of the box with no problems whatsoever.  Do your homework and you will always get the best results.  :wink:

This is my point exactly. Google the parts before you buy and you'll have no surprises. 

The GNOME 3 (Shell) issue is due to Catalyst, by the way. That should be fixed ASAP.

---

### Post by a2j on 2011-10-27
> **Pithikos said:**
> Have you tryied just keeping some elements(VGA driver, kernel) locked while updating?

Else I would suggest OpenSuse. Debian feels a bit too bland for home use.

actually Kubuntu 11.10 works for me now. with a little bit of tweaking.

---

### Post by monkeydrufy on 2011-11-04
sorry guys,

I have an asus k53ta with llano a6

I can't install ubuntu 11.10 because I get black screen
I have installed 11.04 successfully but if I update the os I get black screen again

any tips?

thanks

---

### Post by BrokenKingpin on 2011-11-04
> **Pithikos said:**
> Dont you EVER, _**EVER**_ buy a laptop/desktop with ATI gpu if you are going to use Linux.
That really is not the case anymore, although I do think the Nvidia driver are still more mature.

The real issue is cutting edge hardware... it doesn't hurt to research the comparability with Linux before buying new hardware.

Give it a few months and the issues will probably be resolved.

---

### Post by wolfen69 on 2011-11-04
> **Pithikos said:**
> Who does really use the open source drivers? The point is that ATI has the worst support. Even if the driver works at the moment in a few years it won't. I had the worst experience with ATI and since I switched to nVidia I had zero. It's quite known that ATI doesn't care about Linux users as much as nVidia does.

I agree. Over the years, I've *never* had a problem with nvidia (15 different video cards) and with ati (about 12 different cards) it's been 50-50 as to whether it will work well. And those cards were just from *my* computers. I could go on about all of the computers I've worked on. Anyone who says ati is better needs to do some actual testing, as in have a stack of nvidia cards, and a stack of ati cards. Have an install fest and get back to me.

---

### Post by bbrg548 on 2011-11-04
> **monkeydrufy said:**
> sorry guys,

I have an asus k53ta with llano a6

I can't install ubuntu 11.10 because I get black screen
I have installed 11.04 successfully but if I update the os I get black screen again

any tips?

thanks

Did you install the proprietary driver / fglrx package in 11.04 before upgrading? That's how I got it to work on my Toshiba with the A6-3400M. From what I've read, it seems the glitch is in the 3.0.x kernel - it tries to run the driver even if it's not actually installed, resulting in the dead screen.

---

### Post by monkeydrufy on 2011-11-05
How can I install driver / fglrx package?

sorry I'm a newbe

---

### Post by hotweiss on 2011-11-06
> **monkeydrufy said:**
> sorry guys,

I have an asus k53ta with llano a6

I can't install ubuntu 11.10 because I get black screen
I have installed 11.04 successfully but if I update the os I get black screen again

any tips?

thanks

There you go, my guide should help you out:

[http://seethisnowreadthis.com/2011/10/31/how-to-install-ubuntu-11-10-on-the-toshiba-l745d/](http://seethisnowreadthis.com/2011/10/31/how-to-install-ubuntu-11-10-on-the-toshiba-l745d/)

---

### Post by monkeydrufy on 2011-11-16
thank you so much :)

---

### Post by oscarivera9 on 2011-11-20
> How can I install driver / fglrx package?

sorry I'm a newbe

I know you asked this a couple of weeks ago, but I had not checked in to the forums since then and it seems like no one has responded to you.  What you want to do is start your own thread if you have a new question that's different from this thread.  But, to answer your question, Ubuntu 11.10 is pretty good at finding the fglrx driver for you.  All you have to do is go to Additional Drivers and the ATI driver should show up as one of your options.  The ATI and the fglrx are basically the same thing.

If that doesn't work for you, or if you need more information, go here:
[https://help.ubuntu.com/community/VideoDriverHowto/ATI](https://help.ubuntu.com/community/VideoDriverHowto/ATI)

I hope this helps you out in case you still need the help.  For future reference just remember to post your own thread with your question if you cannot find another question similar to yours.

---

### Post by kazuya on 2011-12-15
> **hotweiss said:**
> There you go, my guide should help you out:
 
[http://seethisnowreadthis.com/2011/10/31/how-to-install-ubuntu-11-10-on-the-toshiba-l745d/](http://seethisnowreadthis.com/2011/10/31/how-to-install-ubuntu-11-10-on-the-toshiba-l745d/)
 
Hotweiss, you are a God-send., your guide should be on a sticky for Ubuntu and Mint 12 forum as a great deal of users would benefit greatly from this post.
 
It certainly is steering me in the right direction.

---

