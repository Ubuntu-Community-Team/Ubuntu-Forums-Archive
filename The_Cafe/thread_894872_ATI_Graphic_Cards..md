---
title: "ATI Graphic Cards."
date: 2008-08-19
forum: The Cafe
---

### Post by Tom--d on 2008-08-19
Hey,

So I was wondering. Where does ATI stand against Nvidia. I mean, the drivers. I heard that Nvidia have great support but the downside its not open source. 
But ATI have open source and closed source. But over time?

If I bought a graphics card. 
What would you recommend, and why?

---

### Post by ssam on 2008-08-19
Nvidia hate freedom (oh how i miss lugradio. sob).

Nvidia have shown no signs of even releasing docs to opensource devs. there is a reverse engineering project [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) , but it is a huge job, and slow going.

ATI have been releasing specs and source code. They are working with Novell (and i think redhat) [http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd). the docs are having to go though lawyers before being made public. some devs are being give early access under NDA, so that on the day the docs are released, there is already code written with them. they are basically doing everything the community has every asked for.

the opensource radeon drivers are not perfect yet. they dont have acceleration on the HD 3xxx and 4xxx cards yet. that is waiting on docs that are expected to be released in september. people in the know seem to expect that be the end of the year there will be some level of acceleration on all current ATI cards.

if you want to play 3d games today though, you will probably need to use the closed source drivers for both nvidia and ati. these both can be problematic, though historically ati has a worse reputation.

[http://www.phoronix.com/](http://www.phoronix.com/) is a very good site to keep up to date.

(personally i have just bought a ati HD 3650, to replace a nvidia 7300)

---

### Post by ODF on 2008-08-19
This is the reason I'm interrested with ATI.

[http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)

Money is not an issue I want an ATI card wich is working good. I have a NVIDIA 8800gts since november and they didn't fix it.

---

### Post by Polygon on 2008-08-19
also, ati is catching up. the newest ati cards have slightly less peformance but a ton cheaper. not to mention the ati drivers are slowly becoming more open =P

---

### Post by nick09 on 2008-08-19
That is good to hear as I'm buying a laptop with a ATI card.

---

### Post by Mateo on 2008-08-19
> **ssam said:**
> Nvidia hate freedom (oh how i miss lugradio. sob).

lol, extremist garbage.



> the opensource radeon drivers are not perfect yet.

lol, understatement of the year.  The opensource radeon drivers are garbage if you actually like having your video card capable of doing 1/2 the things it is designed to do.

> if you want to play 3d games today though, you will probably need to use the closed source drivers for both nvidia and ati. these both can be problematic, though historically ati has a worse reputation.

translation:  the Nvidia work nearly flawlessly for most people, and supports aiglx.  The ATI drivers have improved over time but still have tremendous flaws like shaky tv-out support and no aiglx.

---

### Post by aaaantoine on 2008-08-19
> **Mateo said:**
> translation:  the Nvidia work nearly flawlessly for most people, and supports aiglx.  The ATI drivers have improved over time but still have tremendous flaws like shaky tv-out support and no aiglx.

Flat-out lie.  The ATI drivers have supported AIGLX to some degree since October, and the version available in the Hardy repositories is no exception.

The drivers sure as hell aren't perfect, but be careful about spreading misinformation such as this.

---

### Post by Unicast on 2008-08-20
I don't know how widespread the issue is with other ATI cards, but on my system (Inspiron 1501 with ATI Xpress 1150 graphics) scrolling in FF3 is a right royal PITA with Desktop Effects enabled.

And yet on my workstation, with a lowly GForce FX-5500, scrolling in FF3 is silky smooth with Desktop Effects enabled.

The next laptop I buy will definitely be NVIDEA based - ATI drivers just aren't there yet in my experience.

---

### Post by Ub1476 on 2008-08-20
ATI hasn't worked very well for me yet.. Compiz is fine, but I have to disable it to watch movies. I also notice that Compiz looks horrible with ATI compared to NVIDIA. Also, dual-monitor support is poor. 

I'm buying a laptop with Intel. :)

---

### Post by toupeiro on 2008-08-20
They say a car is only as good as its driver, and the same thing applies to video cards.

I've long believed, and in some benchmark cases over time have proven, that ATi has and frequently does make better consumer-end hardware than Nvidia, but that can only be seen when catalyst has had time to mature a bit and you compare the cards once they are a mature offering.  Out the chute, Nvidia is better, not because of the physical GPU capabilities at all times, but because of how well the Forceware (*refering to the name they gave the unified driver*) platform is written in comparison to catalyst. This is, of course, when compared on Windows based systems. Openness aside, I'm comparing the vendor offerings here.

When it comes to Linux accelerated graphics, nothing touches a Geforce or Quadro-FX card right now.  Except, maybe a Tesla, which again, is Nvidia simply outdoing themselves.  Once you step out of the realm of consumer end into real 3d-performance cards, ATi Fire series doesn't really give the Quadro series any serious competition yet.  Even the ATi FireGL V8650 which has very impressive stats is gimped if you wanted to leverage it in Linux due to ATi's lagging linux driver development in comparison to where the Quadro-FX driver is.  Because Catalyst for linux lags even further behind Catalyst for Windows,  This card will be in its prime around the time the next generation Quadro is well saturated in the High performance Computing world.  Memory I/O will have doubled in that timeframe.

Radeon versus Geforce, however, statistically I have gotten more performance lifecycle out of Radeons on windows systems as catalyst matures for your chipset, whereas Nvidia will rely on stepping up their hardware before ATi to get better performance numbers.  If out of the chute, Nvidia can edge out ATi, but not offer the same performance lifecycle of a specific GPU series in comparison to the ATi, it tells me that the ATi hardware is often times better, just not as completely leverage-able as Nvidia as new hardware is released.

That being said, it has been a long time since I had my hand on a Consumer-end Radeon card to do any testing in Windows.  On linux, I believe Nvidia is still a clear winner until ATi has had more time to mature Catalyst for Linux.  In summary, If ATi hired the Forceware developers to completely rebuild catalyst from the ground up, I think ATi would be killing Nvidia right now on head to head current-gen benchmarks.

Today, if you are running purely linux and thats where you need your video to come through for you, run Nvidia.   If you dual boot, and game a lot in windows, Catalyst drivers will get better and your investment will take you further with the ATi Card, but you will have to be patient in linux to have quasi-comparable performance.

Im sure there are some who will disagree with me or have different experiences, but this is just based on my experiences with the hardware I've owned or have worked with in my job by the two makers over the years.

---

### Post by ssam on 2008-08-20
For those of you with problems with the current ATI proprietary drivers, there has been a new version today. [http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_evolution&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_evolution&num=1)

Also something in that article i did not know, AMD put linux drivers on the CDs that come with the graphics cards.

---

