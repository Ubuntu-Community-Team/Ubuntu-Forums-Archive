---
title: "The old lappy is happy with 12.10"
date: 2013-03-09
forum: Testimonials &amp; Experiences
---

### Post by drchrist68 on 2013-03-09
I've used various flavors of Linux off & on since the late 90's and this was by far the easiest Linux install, ever.

I see many rants regarding the inability to detect hardware, un-usability of Unity, incompatible software, etc., that my head is spinning. Let me present my experience:

The patient in question is an 'old' Dell XPS m1530 laptop. This machine has experienced several OS transplants over the years but has remained a very solid machine. I did some preliminary reading about others' experiences getting the Broadcom BCM4312 wireless to work, plus pros/cons of various nVidia drivers (GeForce 8600M GT) and installation methods, and thus set off with my first install attempt armed with what I thought was good information. Needless to say after 2 days of fiddling, I ended up with a b43 driver that suffered high latency with no apparent fix, and an unstable beta video driver. I knew I could do better than that.

So, I re-installed 12.10 with a few differences. To alleviate the network issue during install & updates, I began the install with the lappy connected to the 'Net via ethernet. **Having the thing networked, and selecting to download updates** **during install**, was the key to getting everything working the first time. Although I prefer open source drivers for ideological reasons, I just want the drivers that work best; for me the included proprietary Broadcomm STA driver (wl) just works, and works great. I needed to do *nothing* extra to get this functioning as it should, which made me well pleased.

The nouveau video driver worked at full resolution from the beginning, but to reap the full benefits of the hardware, I downloaded the latest driver release directly from nVidia and followed their instructions. Oops! I was missing the current kernel headers... Well, that was mentioned in the instructions and I somehow missed that, so my fault. Fixed that as directed and at reboot the proprietary nVidia drivers were active and working flawlessly. I then proceeded to install Steam, Netflix, Minecraft, and other "necessary" applications.

One major use of this laptop is to use a Juniper VPN for work, and setting up Juniper Network Connect with *any* other distribution proved to be an absolute nightmare comparable to having a root canal and gall bladder surgery on the same day. I expected hell. Then I discovered that in Ubuntu it's as easy as installing the ia32-libs package (just ONE package for the entire 32-bit library!), *un*installing the 64-bit Firefox/JDK/Icedtea and installing their :i386 variants. OMG, if the darn thing didn't just plain work the very first time! 

...For comparison, Windows 7 on this same laptop installed easily, and I installed the video driver directly from nVidia for best performance, exactly the same as I did with Quantal. But I had to buy Windows 7, I had to buy the Office suite for $$$, had to download a driver to get wireless working, had to load security/antivirus software and constantly be vigilant regarding viruses and spyware. I've had some very good luck with Windows 7, but it's not the panacea of ease and stability some people make it out to be. However, compatibility & familiarity was practically guaranteed.

Which brings us to the issue of compatibility. No way to run Windows programs? WiNE just not cutting it? Well, there are some times when you just gotta run Windows, when the software just DOES NOT work in Linux no matter what. That's why I loaded Windows in VirtualBox. Now the kid can run Roblox and ShipSim Extremes without crashing (he can even RDP into my laptop to play games while I am on the VPN working).

I tested Windows 8 in a VM and found it to be far more counter-intuitive than Unity. There's a learning curve with each, but Win8's UI in my opinion is suited very well to touch screens, not to 'old-style' keyboard & mouse systems. Unity also drove me nuts at first, but like going from Windows to OSX; it's different, and the more you use it the easier it becomes. Unity gets such a bad rep, mostly from earlier iterations that were seriously lacking, but I find this latest version to be very usable.

Based on ease of setup, hardware support, ease of use, speed, and stability, I find Ubuntu 12.10 to be a terrific product.

---

### Post by ibjsb4 on 2013-03-09
That old Dell has some pretty good specs.  Congrads and welcome to the forums :)

---

