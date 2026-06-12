---
title: "Seriously guys, when wireless N or 802.11n will be properly supported on Ubuntu?"
date: 2009-05-10
forum: The Cafe
---

### Post by edvar on 2009-05-10
Seriously guys, when wireless N (or 802.11n if you will) will be properly supported out of the box on Ubuntu? 

It's about time, don't you think?

---

### Post by shad0w_walker on 2009-05-10
Seriously, it's about time people realise that the wireless problems on all Linux versions (Linux is not Ubuntu) are because of the companies. 

Complain to them, it's not our fault they don't create drivers or give us specs to make them ourselves. The community works hard to provide drivers as best it can for cards, but it's not easy when they have to figure out how it works internally by working backwards. 

Once again, complain to the companies and check your hardware before you start complaining it's our fault. You don't buy a windows only piece of hardware then complain it doesn't work on Macs, so don't do it for Linux.

---

### Post by edvar on 2009-05-10
I agree with you. The hardware vendors should release official versions of their drivers for Linux. I acknowledge it's not easy to reverse engineer and create a driver in a couple of days but this is what hardcore linux guys from old times used to do... maybe not in a couple of days though...

However 802.11n has been around since 2004 and now, 5 years down the track, it is on Draft 9.0. So since this is a standard I believe its documentation should show pretty clear how it works.

Other than that, doesn't ubuntu support Atheros drivers since Hardy? Atheros is the main Wireless N chip on most of the main wireless cards.

I am no kernel/driver developer/coder/curious but after 5 years and a well documented draft  maybe someone could have worked out how to make it work properly on Linux.

---

### Post by Tycho on 2009-05-10
So 802.11n doesn't work on ubuntu?

Or is there a documented process somewhere to enable it?

---

### Post by edvar on 2009-05-10
By the way shad0w_walker, what do you mean? Of course Linux is Ubuntu! And Ubuntu is Linux!

---

### Post by edvar on 2009-05-10
What I can tell from the things I read on several forums, Ubuntu still doesn't support Wireless N.

I have a Mac with Airport (Wireless A/B/G/N) and a Linux box running Jaunty with a Linksys PCI Wireless A/B/G Card. I usually stream video from my Ubuntu box to my Mac. My wireless network is running Wireless G because of my Linux Box but I want to buy some Wireless N gear (new Wireless N router and new Wireless N PCI card for my Linux Box) to upgrade my network and speed up the video streaming.

Unfortunately the histories I read about Wireless N on Ubuntu are not good ones...

---

### Post by herdwick on 2009-05-10
> However 802.11n has been around since 2004 and now, 5 years down the track, it is on Draft 9.0. So since this is a standard

so it still isn't a ratified standard if it's only a draft ?

That apart, it's the vendor specific implementations and control of chipsets etc that will matter - and they won't be in the standard. Atheros is a chip maker, not a specific chip, and the built-in drivers are the a/b/g chip ones in widespread use.

So I think you're stuck waiting for the standard to be ratified (due next year ?) and for vendors to release chipset and device specifics before anyone could get their teeth into it.

---

### Post by edvar on 2009-05-10
Yes, you are right... It's not a full standard yet but despite of the proprietary implementations, I was under the impression at least 70 to 80% or even 90% of them are still based on the standard's draft. Meaning there are lots in common between them.

Again, I'm not a developer and I'm not sure about it.

Anyway, to be honest I was hoping there would be some obscure project like the Radeon free driver for ATI cards or the Nouveau driver for NVIDIA cards that would address the support to Wireless N on Linux somehow while we don't have the official standard ratified and the vendors chipset specifications.

---

### Post by dmizer on 2009-05-10
Since this is not a support request, I've moved this to the cafe.

Enjoy.

---

### Post by SunnyRabbiera on 2009-05-10
The blame goes to hardware not linux, I reather blame companies like broadcom then Ubuntu

---

### Post by Polygon on 2009-05-10
it is most likely a kernel problem. If its not supported in the kernel, no linux release gets it.

and i thought that the atheros 9000 series is open source actually (and uses wireless n), or am i mistaken?

---

### Post by Bios Element on 2009-05-10
> **edvar said:**
> Seriously guys, when wireless N (or 802.11n if you will) will be properly supported out of the box on Ubuntu? 

It's about time, don't you think?

It is supported. I'm making this post via wireless N. I'm sorry to hear your having problems but please don't bash an entire feature just because it doesn't work for you.

---

### Post by perce on 2009-05-11
Since wireless N is or is not (I don't know) supported on the kernel, you should not complain in the Ubuntu forum, but in the Linux kernel mailing list [http://lkml.org/]("http://lkml.org/")

---

### Post by skymera on 2009-05-11
> **edvar said:**
> I agree with you. The hardware vendors should release official versions of their drivers for Linux. I acknowledge it's not easy to reverse engineer and create a driver in a couple of days but this is what hardcore linux guys from old times used to do... maybe not in a couple of days though...

However 802.11n has been around since 2004 and now, 5 years down the track, it is on Draft 9.0. So since this is a standard I believe its documentation should show pretty clear how it works.

Other than that, doesn't ubuntu support Atheros drivers since Hardy? Atheros is the main Wireless N chip on most of the main wireless cards.

I am no kernel/driver developer/coder/curious but after 5 years and a well documented draft  maybe someone could have worked out how to make it work properly on Linux.

You make one.
Chop chop, i'm waiting to use my N.

---

### Post by 3rdalbum on 2009-05-11
If you want Draft N but you can't be bothered to search out a chipset that is supported at the higher speed, then buy another Draft N router, plug it into your Ubuntu machine, and set it up to bridge with your existing router. Ubuntu will treat the connection as an Ethernet connection, and the router will operate the radio side of things.

---

### Post by edvar on 2009-05-11
> It is supported. I'm making this post via wireless N. I'm sorry to hear your having problems but please don't bash an entire feature just because it doesn't work for you.

No one is bashing any features. You are the first person I heard with Wireless N working. I researched on several forums and I always got the same thing: "Wireless N doesn't work on Ubuntu". Even here on this same post:

> That apart, it's the vendor specific implementations and control of chipsets etc that will matter - and they won't be in the standard. Atheros is a chip maker, not a specific chip, and the built-in drivers are the a/b/g chip ones in widespread use.

Tried here and [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) there are no Wireless N cards. Posted a similar question last year: [http://ubuntuforums.org/showthread.php?t=902114](http://ubuntuforums.org/showthread.php?t=902114) ... no responses. 

So what card are you using and how did you set it up? Did you use NDISwrapper? Did Ubuntu recognize it out of the box? Share your experience with us!

> Since wireless N is or is not (I don't know) supported on the kernel, you should not complain in the Ubuntu forum, but in the Linux kernel mailing list [http://lkml.org/](http://lkml.org/)

I'm not complaining. Just wanted to open a discussion about the subject. It's a technology that has been around for quite some time and I'm sure if it was supported on Ubuntu, more Windows users would come to the good side of the force.

> You make one.
Chop chop, i'm waiting to use my N.

Well, if I was a developer I would make one and would share with all the community. That's the spirit. Maybe you expect every Linux user to be a kernel developer. But unfortunately I'm no developer (I believe I'm repeating myself). Anyway keep up with the nice attitude, kid.

> ...buy another Draft N router, plug it into your Ubuntu machine, and set it up to bridge with your existing router. Ubuntu will treat the connection as an Ethernet connection, and the router will operate the radio side of things

I thought about it but I was trying to avoid having mixed Wireless G and N on my network. I wanted a full N implementation but I think I'll have to bear with Wireless G for a while longer...

---

### Post by Paqman on 2009-05-11
> **3rdalbum said:**
> If you want Draft N but you can't be bothered to search out a chipset that is supported at the higher speed, then buy another Draft N router, plug it into your Ubuntu machine, and set it up to bridge with your existing router. Ubuntu will treat the connection as an Ethernet connection, and the router will operate the radio side of things.

That's really only a practical solution for a desktop machine though.

---

### Post by fatality_uk on 2009-05-11
> **edvar said:**
> I am no kernel/driver developer/coder/curious but after 5 years and a well documented **draft** maybe someone could have worked out how to make it work properly on Linux.

Lets also have support for draft S,T,U and V as well please!!! Unless and until it is ratified, N is still draft and subject to change at any time so even if it is supported right now in a draft form, I would speak to your hardware provider and ask when thay plan to support Linux. That way, we all win!

---

### Post by 3rdalbum on 2009-05-11
> **Paqman said:**
> That's really only a practical solution for a desktop machine though.

True, but I don't know why you'd need N speeds on something as low-powered as a laptop.

---

### Post by edvar on 2009-05-11
Yeah, I agree with your point. It is a draft. However I don't think it's going to change that much after 5 years. It's been running fine on Mac and Windows for quite some time now. If they change it drastically there'll be lots of people really pissed off.

One thing is to work on a draft X,Y,Z that just started and can definitely change a lot. Other thing is to work on a stable draft with lots of people using it and really happy with its high speeds.

If you wanna talk about "drafts", what about ext4? It's totally bleeding edge but all the big distributions are supporting it now. Are people waiting for ext4 to be "ratified"? Give it 1 or 2 years and maybe Red Hat will use it as their default file system on RHEL 6 or 7 but their Fedora 11 is using it right now. I am using it on a Fedora box at work and I am very happy with the ext4 boot speed - but of course I am taking the risks... But I believe using Wireless N nowadays is not as risky at all.

---

### Post by edvar on 2009-05-11
> but I don't know why you'd need N speeds on something as low-powered as a laptop.

I have a Macbook Pro 17 inches (Core 2 Duo 2.33Ghz, 3Gb RAM and an ATI Graphic Card with 256Mb of memory) and I use it as my main desktop. It's too big to carry it around. And as you can see by the specs it's definitely not low-powered at all. I need N speeds because streaming video at G speeds is not giving me the throughput I need.

---

### Post by praveenmarkandu on 2009-05-11
> **SunnyRabbiera said:**
> The blame goes to hardware not linux, I reather blame companies like broadcom then Ubuntu

im sorry i totally disagree with this. we live in a capitalist civilization. you cant expect a company to shell out extra money to write drivers for desktop linux (which from recent news is just 1% of the PC market)

if you are going to blame the companies, you are going about it the wrong way. advocates of linux should write their own drivers first. more support = more users. only then can we make linux have more traction and then companies will start paying attention.

the whole free software thing has a strong hippie mentality to it like "lets stick it to the man/companies". i fully support open source software, if not i wouldnt be on this forum. but people have to be realistic.

---

### Post by lykwydchykyn on 2009-05-11
> **praveenmarkandu said:**
> im sorry i totally disagree with this. we live in a capitalist civilization. you cant expect a company to shell out extra money to write drivers for desktop linux (which from recent news is just 1% of the PC market)

if you are going to blame the companies, you are going about it the wrong way. advocates of linux should write their own drivers first. more support = more users. only then can we make linux have more traction and then companies will start paying attention.

the whole free software thing has a strong hippie mentality to it like "lets stick it to the man/companies". i fully support open source software, if not i wouldnt be on this forum. but people have to be realistic.

The great thing is, they don't have to shell out a red cent to support Linux.  They just need to provide the information necessary.  Check this out:

[http://www.linuxdriverproject.org/twiki/bin/view](http://www.linuxdriverproject.org/twiki/bin/view)

We have over 200 developers ready and waiting to make drivers for any piece of hardware.  Cost to hardware vendor: $0 and a little information (specs, API's, etc). 

Seems there's no excuse, as far as I'm concerned.  So yeah, we need to "blame" the manufacturers and get them to take a few simple steps to see that their stuff works on Linux.

And if we're just so insignificant as a user base that no company should wast R&D dollars on us, why do Nvidia, ATI, Adobe, Intel, and dozens of other software & hardware vendors do so?  They must be run by hippies, I guess.

---

### Post by pwnst*r on 2009-05-11
"you make one".  what a pathetic thing to say.

---

### Post by richg on 2009-05-11
You guys need to try Mint 6. Wireless works right out of the box for my desktop and laptop. Also, I can play commercial DVDs right out of the box.

Rich

---

### Post by perce on 2009-05-11
According to this page [http://wireless.kernel.org/en/users/Drivers]("http://wireless.kernel.org/en/users/Drivers") support for n wireless varies form card to card.

---

### Post by Paqman on 2009-05-11
> **3rdalbum said:**
> True, but I don't know why you'd need N speeds on something as low-powered as a laptop.

A lot of corporate laptop users connect to large amounts of data on network shares routinely. Hotdesking and such. For a lot of people a laptop is their main productivity machine.

---

### Post by pwnst*r on 2009-05-11
> **Paqman said:**
> A lot of corporate laptop users connect to large amounts of data on network shares routinely. Hotdesking and such. For a lot of people a laptop is their main productivity machine.

exactly. where i work, execs as myself exclusively use laptops w/ docking stations.  it makes more sense.

---

### Post by edvar on 2009-05-11
> You guys need to try Mint 6. Wireless works right out of the box for my desktop and laptop. Also, I can play commercial DVDs right out of the box.

Wireless working out of the box is not a big deal anymore. I had lots of problems with wireless on Ubuntu with the 7.x versions (Feisty and Gutsy). However after Hardy and Intrepid, the developers did a great job and now it's normal to get the wireless adapter working right after the installation. I haven't had any problems since Hardy. 

The issue is: if you have a Wireless N adapter it's possible you are connected at Wireless G speeds as Ubuntu might not support Wireless N (unless our friend who said Wireless N is working fine on Ubuntu is right and everyone else who says it doesn't work is wrong).

In regards to DVD playback and proper audio/video codecs, just add the medibuntu repository to your Ubuntu software sources and you are in business. Other than that, Mint is based on Ubuntu. I do like its looks tough but never tried it.

> According to this page [http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers) support for n wireless varies form card to card.

Hey, this is great! It shows the ath9k driver does support Wireless N. Can anyone confirm?

If this link is correct, someone needs to get [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) updated.

---

### Post by Polygon on 2009-05-12
> **edvar said:**
> 


Hey, this is great! It shows the ath9k driver does support Wireless N. Can anyone confirm?

If this link is correct, someone needs to get [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) updated.

i have pretty much said that in every 'WIRELESS N DOES NOT WORK OMG' thread, and every time i have been [ignored]("http://ubuntuforums.org/showpost.php?p=7254870&postcount=11"). For the 50 millionth time, if you want wireless N support out of the box, atheros and their 9k drivers are your best bet right now

---

### Post by FuturePilot on 2009-05-12
> **Polygon said:**
> i have pretty much said that in every 'WIRELESS N DOES NOT WORK OMG' thread, and every time i have been [ignored]("http://ubuntuforums.org/showpost.php?p=7254870&postcount=11"). For the 50 millionth time, if you want wireless N support out of the box, atheros and their 9k drivers are your best bet right now

Intel also supports wireless N in their drivers for their wireless N capable cards.

---

### Post by Polygon on 2009-05-12
id still be iffy using intel anything, as their 'open source' drivers for other things (like their graphics cards) are still amazingly bad. No open gl 2.0 or 3.0 support? honestly?

---

### Post by Paqman on 2009-05-12
> **Polygon said:**
> id still be iffy using intel anything, as their 'open source' drivers for other things (like their graphics cards) are still amazingly bad. No open gl 2.0 or 3.0 support? honestly?

Their wifi stuff is pretty reliable though. I used to use Intel cards as drop in replacements for annoying Broadcomm ones that wouldn't play nicely with Linux. Never had any issues at all.

---

### Post by blastus on 2009-05-12
Wireless is great for casual Internet use but anything more than that requires a hard line. For casual Internet use wireless G is fast enough (unless you have say a 25 mbs ISP.) Even with a DD-WRT router setup as a wireless bridge to wireless N router, speed and reliability is not that great, especially in multi-unit dwellings. Wireless N is not a huge improvement over G. If WiGig ever gets standardized we could get better speeds.

The fastest wireless G I've gotten is about 2.5 megabytes per seond.
The fastest wireless N I've gotten is about 10 megabytes per second.

In short, you aren't missing much of anything without wireless N. Isn't the N standard still in draft anyway?

---

### Post by Tipped OuT on 2009-05-12
> **shad0w_walker said:**
> Seriously, it's about time people realise that the wireless problems on all Linux versions (Linux is not Ubuntu) are because of the companies. 

Complain to them, it's not our fault they don't create drivers or give us specs to make them ourselves. The community works hard to provide drivers as best it can for cards, but it's not easy when they have to figure out how it works internally by working backwards. 

Once again, complain to the companies and check your hardware before you start complaining it's our fault. You don't buy a windows only piece of hardware then complain it doesn't work on Macs, so don't do it for Linux.

A Men. :|

---

### Post by FuturePilot on 2009-05-12
> **Polygon said:**
> id still be iffy using intel anything, as their 'open source' drivers for other things (like their graphics cards) are still amazingly bad. No open gl 2.0 or 3.0 support? honestly?

True their graphics cards may not be the best performance wise, but their wireless cards are pretty darn good. I've only had one small problem with this card and it was a long time ago when the iwl driver was still young. It's not an N card but it still works great.

---

### Post by edvar on 2009-05-12
> 
[QUOTE]Originally Posted by Polygon  
i have pretty much said that in every 'WIRELESS N DOES NOT WORK OMG' thread, and every time i have been ignored. For the 50 millionth time, if you want wireless N support out of the box, atheros and their 9k drivers are your best bet right now

Intel also supports wireless N in their drivers for their wireless N capable cards.[/QUOTE]

That's all I wanted to know!! I did do my homework and researched a lot but this is the very first time someone actually tells me it's working on Ubuntu. Thanks a lot!

Is there someone here with an ath9k card using Wireless N? Is it working fine? Any issues to get it working?

> Wireless is great for casual Internet use but anything more than that requires a hard line. For casual Internet use wireless G is fast enough (unless you have say a 25 mbs ISP.) Even with a DD-WRT router setup as a wireless bridge to wireless N router, speed and reliability is not that great, especially in multi-unit dwellings. Wireless N is not a huge improvement over G. If WiGig ever gets standardized we could get better speeds.

The fastest wireless G I've gotten is about 2.5 megabytes per seond.
The fastest wireless N I've gotten is about 10 megabytes per second.

In short, you aren't missing much of anything without wireless N. Isn't the N standard still in draft anyway?

Even with these figures it's still 4 times faster than Wireless G and, in my opinion, this is pretty damn good! 10 Mbps will be more than enough for my needs. I agree an ethernet connection is better, more reliable and faster but I'm talking about 2 different rooms and I have no intention of being in a cable nightmare, running cables all over my apartment. Doesn't matter if it's still a draft if it's able to give me more speed in a reliable way (i.e. no connection drops).

---

### Post by edvar on 2009-05-12
If it's confirmed, I'm leaving the office now and buying this D-link DWA-547 RangeBooster N adapter ([http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=11&Sub2=19&PID=275](http://www.dlink.com.au/Products.aspx?Sec=1&Sub1=11&Sub2=19&PID=275)), an Airport Extreme (or maybe a Time Capsule... if the government deposit the Stimulus money on my bank account) , connect it via ethernet to my router and enjoy the N speed boost between my boxes! 

And, of course, tell my friends their days of mocking Ubuntu for not supporting Wireless N are over!

---

### Post by jespdj on 2009-05-13
> **FuturePilot said:**
> Intel also supports wireless N in their drivers for their wireless N capable cards.
Well, it does not seem to be working on my XPS M1530 with Intel 4965 WiFi, on Ubuntu 9.04, using the iwlagn driver. I've never seen the speed go higher than 54 Mbit/s (G speed). I do have an N router and in Windows Vista N speed works without problems.

[Bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203506).

---

### Post by 3rdalbum on 2009-05-13
> **edvar said:**
> I have a Macbook Pro 17 inches (Core 2 Duo 2.33Ghz, 3Gb RAM and an ATI Graphic Card with 256Mb of memory) and I use it as my main desktop. It's too big to carry it around. And as you can see by the specs it's definitely not low-powered at all. I need N speeds because streaming video at G speeds is not giving me the throughput I need.

Two things:

1. I'd pretty much define that machine as low-powered, compared to the fairly modest desktop I built 18 months ago. It's a laptop, it's designed with low-power components. Low-power == low performance.

2. If you use it as your main desktop, you can connect an N router. Or, as we've all just been informed, an Atheros N card.

---

### Post by edvar on 2009-05-13
Ok, I can understand your point. It's not a normal desktop, the disk is slower, doesn't have all the cooling, the processor is not as fast as a desktop version. But still it does its job pretty well despite of being a 2.5 years old notebook. 

My Ubuntu box is more robust and it is a proper desktop: Intel Quad Core 2.4Ghz, 4Gb RAM, 1Tb disk on RAID5 (3x 500Gb SATA Drives), NVIDIA GeForce 8800 GTS and a crappy Linksys Wireless G card (I was sick of running network cables all over my living room). I use it manly as my HTPC running XBMC.

All macbooks have Wireless N enabled out of the box. I believe they use Atheros chips as well.

---

### Post by edvar on 2009-05-18
I bought and installed the D-Link wireless N card on my Jaunty box. Ubuntu recognized the driver straight away and right after reboot I was back in business. This is the output of iwconfig:

> wlan1     IEEE 802.11bgn  ESSID: "xxxxx"
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx : xx : xx : xx : xx : xx
          Bit Rate=36 Mb/s   Tx-Power=20 dBm
          Retry min limit:7   RTS thr : off   Fragment thr=2352 B
          Power Management: off
          Link Quality=45/100  Signal level:-75 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It's still connected to a Wireless G router but, have you noticed the "IEEE 802.11bgn" descriptor? Looks good!

I just got my Airport Extreme Wireless N router and will set it up tonight. I'll post a new iwconfig output with the new router and hopefully I'll get a better bit rate (fingers crossed!).

---

### Post by edvar on 2009-05-19
Airport Extreme Base Station installed and configured for Wireless N networking only. Unfortunately I cannot use 5Ghz because the damn D-Link card I bought only supports 2.4Ghz. Anyway... Ubuntu is connected at 300Mbps!!!!!! Awesome!!!!

Only one funny thing: The bit rate on iwconfig is showing 0Kbps and Network Manager shows the speed as Unknown. Not a big deal. The Airport Utility on the Mac is showing the connection steady at 300Mbps.

Bottom Line: if you want Wireless N on Ubuntu go for Atheros Chipset!

---

### Post by Johnsie on 2009-05-19
The simple solution to this problem is to use Windows.

There's no point using an operating that doesn't work properly with the hardware you want to use. Ubuntu is free and nice and all that but if it limits what hardware you can use or buy then you need to take that into consideration. I use whichever operating system works best with the software/hardware I want to use. If that is Ubuntu then good, but if it's Windows it's not that big a deal. Different operating systems are good at different things.

If I wanted to limit my hardware choices then I would buy a Mac :-)

---

### Post by edvar on 2009-05-19
You should buy a Mac. After all everything Microsoft do is copying Apple since the company started. Stick with the original!

Now with my Ubuntu (second best OS nowadays) running smoothly at 300Mbps just like my Mac (the best one IMHO), no virus, no malware, lots of stability, reliability, rock solid unix basis, boot in 30 seconds and so on... why should I ever bother using a crappy OS like Windows?

Other than that, several vendors have Atheros chips on their wireless cards (even the Apple Macbooks). Take a look at [http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

---

