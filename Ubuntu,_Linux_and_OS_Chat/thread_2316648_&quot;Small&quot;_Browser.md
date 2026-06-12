---
title: "&quot;Small&quot; Browser"
date: 2016-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by sumithar on 2016-03-09
I have xubuntu (I think it might be trusty tahr, not sure if the upgrade completed) running on an old gateway laptop, circa 2012.  It has 1 GB RAM.

I want to give it to my 5th grader to do some of his homework assignments which are to be done online but the Firefox browser that comes with the installation is a hog, really slow to refresh and at times unusable.

So is there some other light weight browser I could install instead from software center?
Regards

---

### Post by TheFu on 2016-03-10
All the major browsers are hogs these days.
There are "lighter" browsers, but they usually aren't standards compliant or leave out little security things - like validating certs.

Also - you don't need to limit yourself to software center.  There are many more packages, just not as popular, in the repos.

A few to try - lynx, dillo, chromium-browser - off the top of my head.
Opera is another option, but not in the repos.  [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser) - there is a PPA for it too (which I would prefer over a direct .deb file install) [http://www.ubuntuupdates.org/ppa/opera](http://www.ubuntuupdates.org/ppa/opera)

If you are tight on RAM, there are lighter distros than **any** of the Ubuntu-flavors.  Some will run in 64MB of RAM easily, which means lots of RAM for bloated software like browsers.  [http://tinycorelinux.net/](http://tinycorelinux.net/)  Obviously, they aren't as "pretty" and there are other trade-offs with like different useability, but if you are looking for a 1-trick distro (web browsing), then this is the choice. I use tinycore for online banking, for example, though my systems aren't really very limited.

---

### Post by mörgæs on 2016-03-10
Links2 is one of my favourites but I'm aware that most people find it too light to be of any use. 

I suggest installing adblockers, flashblockers and similar plug-ins in Firefox.

---

### Post by Bucky Ball on 2016-03-10
*Thread moved to **Ubuntu, Linux and OS Chat**.*

If you could be bothered, you could clean install Xubuntu-core. That comes with virtually nothing and is very light and just a basic desktop. No web browser. You could then install Midori or something like that for a web browser. Firefox is going to be resource hungry no matter how you run it (particularly once you open a tab or three).

---

### Post by slickymaster on 2016-03-10
There's also [Midori]("http://midori-browser.org/download/choose/"), licensed under a LGPL 2.1 license. It's fast, lightweight and handles all the latest web technologies like HTML 5 and CSS3.

Also, it's in the repos.

---

### Post by mastablasta on 2016-03-10
>  gateway laptop, circa 2012.  It has 1 GB RAM

I would say the issue is probably the GPU. not ram.

I used chromium on 256 MB, 1.2 Ghz single core CPU. But this was before...on old Chrunchbang/Debian.

Xubuntu tip - use light theme with no fancy graphics (there are a couple simple 2D themes available if I remember correctly). it will help a bit. if you think RAM is the issue then try to upgrade it to 2 GB if you can. however as I said it is likely the GPU that is the issue. I have Kubuntu with all effects turned off on 1 GB RAM old 2.4 Ghz Single core Athlon. it uses Radeon 9200 with 128 MB ram which has partial hardware acceleration support. yet most pages work just fine on Firefox. there is enough RAM available as long as you don't open too many tabs and run too many programs at the same time.

if you can maybe you can post system specs and we might be able to get some tweaking tips. depends really on the hardware we are talking about here.

---

### Post by yoshii on 2016-03-11
Qupzilla is a nice backup to have around.  I can't remember for sure, but I think it's in the Software Center (and/or Synaptic Package Manager) from the normal sources.  
It's still being developed/supported I think so it's alright.  

Also, a lot of the RAM issues with FireFox historically really only come from the Flash support.  Sometimes you can just downgrade the flash to a much smaller version and still have some basic functionality and without all the RAM hogging.  Unfortunately, that approach wouldn't have the security fixes intact, but that's a constantly moving target anyhow.  

Also, you can always browse the web for FireFox configuration tweaks.  It's possible to disable various extra features that FireFox has that you might not need.  Also, if you make sure that your FireFox disk cache is large and active, then it can reduce RAM usage a bit.  But of course there are drawbacks to that as well.

---

### Post by night_sky2 on 2016-03-11
> **yoshi2 said:**
> Also, you can always browse the web for FireFox configuration tweaks.  It's possible to disable various extra features that FireFox has that you might not need.  Also, if you make sure that your FireFox disk cache is large and active, then it can reduce RAM usage a bit.  But of course there are drawbacks to that as well.

This.

Firefox can be trimmed down by removing unecessery 'under-the-hood' features that do not impact the browser's core functionality.

------------------------------------------------------------------------------------------

Here's my list of tweaks that can be performed to make Firefox lighter and faster:

Firefox Hello (built-in app for voice chat and video call): **loop.enabled** -> *false*

Pocket (built-in app to manage reading lists and internet articles): **browser.pocket.enabled** -> *false*

Reader View (extracts web articles and display them like on Android):** reader.parse-onload.enabled** -> *false*

WebRTC (browser-to-browser app to allow voice chat and call): **media.peerconnection.enabled** -> *false*
                                                                                      **media.peerconnection.identity.enabled** -> *false*
                                                                                                                                                                              **media.peerconnection.use_document_iceservers** -> *false*
                                                                                                                                                                              **media.peerconnection.video.enabled** -> *false*
                                                                                         
PDF Reader (built-in reader in Firefox for PDF files): **pdfjs.disable** -> *true*

Tab audio indicator (display icon on a tab when sound is playing from the website):** browser.tabs.showAudioPlayingIcon** -> [I]false

[/I]Geolocalization (allow some websites to request and pinpoint your geographic location):** geo.enabled** -> *false*

---

### Post by sumithar on 2016-03-11
> **mastablasta said:**
> I would say the issue is probably the GPU. not ram.

I used chromium on 256 MB, 1.2 Ghz single core CPU. But this was before...on old Chrunchbang/Debian.

Xubuntu tip - use light theme with no fancy graphics (there are a couple simple 2D themes available if I remember correctly). it will help a bit. if you think RAM is the issue then try to upgrade it to 2 GB if you can. however as I said it is likely the GPU that is the issue. I have Kubuntu with all effects turned off on 1 GB RAM old 2.4 Ghz Single core Athlon. it uses Radeon 9200 with 128 MB ram which has partial hardware acceleration support. yet most pages work just fine on Firefox. there is enough RAM available as long as you don't open too many tabs and run too many programs at the same time.

if you can maybe you can post system specs and we might be able to get some tweaking tips. depends really on the hardware we are talking about here.

Sorry, I thought I'd posted the specs.  Here goes.
It's a Gateway M275 notebook/laptop.
```
-memory
       description: System Memory
       physical id: f
       slot: System board or motherboard
       size: 512MiB
       capacity: 2GiB
     *-bank:0
          description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
          physical id: 0
          slot: DIMM 0
          size: 512MiB
          width: 64 bits
          clock: 333MHz (3.0ns)
     *-bank:1
          description: DIMM SRAM Synchronous 333 MHz (3.0 ns) [empty]
          physical id: 1
          slot: DIMM 1
          clock: 333MHz (3.0ns)
```

```
:~$ cat /etc/issue
Ubuntu 12.04.5 LTS \n \l
```
```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1400MHz
stepping	: 5
microcode	: 0x5
cpu MHz		: 600.000
cache size	: 1024 KB

```

```
sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list

```

```
wmctrl -m
Name: Xfwm4
Class: xfwm4
PID: 1802
Window manager's "showing the desktop" mode: N/A

```

I've sent for 2 1GB modules from amazon since they were fairly inexpensive.

I have just installed Midori, and that already seems to be much more responsive. Thanks for that suggestion.

Is XFCE an appropriate desktop/window manager for these specs?

Thanks!

---

### Post by Bucky Ball on 2016-03-11
Yes.

---

### Post by night_sky2 on 2016-03-12
> **sumithar said:**
> Is XFCE an appropriate desktop/window manager for these specs?

2GB of RAM will be perfectly fine with Xfce.

---

### Post by mörgæs on 2016-03-13
> **sumithar said:**
> I have xubuntu (I think it might be trusty tahr, not sure if the upgrade completed) running on an old gateway laptop, circa 2012.  It has 1 GB RAM.

I want to give it to my 5th grader to do some of his homework assignments which are to be done online but the Firefox browser that comes with the installation is a hog, really slow to refresh and at times unusable.

So is there some other light weight browser I could install instead from software center?
Regards

This is not year 2012 hardware. Looks more like 2002, and the release is 12.04.5, not Trusty Tahr / 14.04.
You have to do your best to trim a decent performance out of it. Upgrading the memory is a good first step but you might need more.

---

### Post by TheFu on 2016-03-13
> **mörgæs said:**
> This is not year 2012 hardware. Looks more like 2002, and the release is 12.04.5, not Trusty Tahr / 14.04.
You have to do your best to trim a decent performance out of it. Upgrading the memory is a good first step but you might need more.

Definitely around 2005 for the hardware.  I had a Pentium M 1.6Ghz around that time.  Compared to computers today, well, there just isn't any comparison.  A $50 used laptop would be much, much, much faster.  An $80 used chromebook would be blazing compared to this laptop.

If you have an old case, PSU, RAM, HDD laying around, a new $50 motherboard + CPU combo would be 6x faster and will play videos using HW decoding.  [http://www.portatech.com/products/product.cshtml?ID=88324&utm_term=AMD+AD640KOKA23HL](http://www.portatech.com/products/product.cshtml?ID=88324&utm_term=AMD+AD640KOKA23HL) - $49. Just 1 example.

Just for comparison, the passmark for the pentium-M box is 369.  A $49 A6-6400K APU passmark is 2279 - day and night.  Just sayin'.  As a point of reference - a new lo-power Core i3 5015U (used in chromebooks) has a passmark of 3167.  Any passmark over 1500 is a responsive system for Linux without Unity as the desktop.

So before adding more RAM - even $10 is too much IMHO - look at CPU+MB replacement.  If you are like many folks here, you have computer parts laying around the house.  Use those with new MB+APU to make a nice, cheap, fast, low-power desktop.  Might not be possible, but an option for lurkers, perhaps?

---

### Post by sumithar on 2016-03-13
Ouch, meant to type 2002.  And as to the OS, I corrected myself in an earlier post, sorry!

---

### Post by sumithar on 2016-03-13
Interesting suggestions.  I actually don't have any bits and pieces anymore and asked around with my friends if they had an older laptop I could buy cheaply before deciding to resurrect this one!
If I could have got a 5 or so year old used computer for 50-75 bucks I'd have been happy to spend it.

Thanks!

---

### Post by goofprog on 2016-03-13
> **slickymaster said:**
> There's also [Midori]("http://midori-browser.org/download/choose/"), licensed under a LGPL 2.1 license. It's fast, lightweight and handles all the latest web technologies like HTML 5 and CSS3.

Also, it's in the repos.

yep yep, midori or text based lynx.  I think there was a file explorer too that could browse too.

---

### Post by sumithar on 2016-03-13
Question about Midori- it's light and fast but on Google websites it complains that I'm using an outdated version of Chrome.  I guess there is a setting in Midori to "fake out" what the server sees as the requesting browser?

---

### Post by mastablasta on 2016-03-14
it probably uses the same base web kit as chrome and its wrongly identified as chrome. anyway browsers: [https://en.wikipedia.org/wiki/Comparison_of_web_browsers](https://en.wikipedia.org/wiki/Comparison_of_web_browsers)

what about Sea Monkey?

anyway the issue is mostly that internet websites want the CPU/GPU. so it's not just browsers but also the websites that will burden the old machines

---

### Post by mr-daniel-lemke on 2016-03-14
> **sumithar said:**
> Question about Midori- it's light and fast but on Google websites it complains that I'm using an outdated version of Chrome.  I guess there is a setting in Midori to "fake out" what the server sees as the requesting browser?

I don't know about Midori, but Opera had such a feature. I don't know if it has bloated any more since the last time I used it in 2013, but it is a decent alternative if Midori isn't quite working properly.

---

### Post by TheFu on 2016-03-14
Opera has definitely added bloated, insecure, features over the last few years.  It is like nobody considers security anymore - so why not make the browser into a file sharing tool too?!!!  Some ideas are just bad, bad, bad.

---

### Post by Irihapeti on 2016-03-15
You can change the user agent string in Midori. I've had to do so a few times to keep certain sites happy.

It's been a while since I used Midori, though, so I don't remember exactly what the setting is called.

---

### Post by Alex_Moonshine on 2016-03-16
Few years ago I inherited (from my work) an old HP Compaq laptop with 512mb of ram. The only 'light browser' I found usable was Qupzilla. Midori kept crashing and using more memory that I would expect from a "light" browser. Still, it's a pain even with Qupzilla. I ended up expanding memory to 4gb on that laptop (out of which it recognized only 2.87, but still).

---

### Post by sumithar on 2016-03-16
Actually now that I've been using Midori for a few days, I too have encountered some crashes.  But after boosting the memory to 2GB, I am able to do stuff with firefox albeit slowly- my son is not complaining too much.

---

### Post by TheFu on 2016-03-16
The other thing you need to do is to increase the swap to 4G.  This is a minimal swap size for most desktops today and I haven't found any reason to go with larger swap even on systems with more RAM.  When the system starts swapping a bunch, it gets slower, but keeps going. It doesn't crash.  This is a warning.  However, if a system runs out of both swap and RAM, then programs tend NOT to do a good job of expecting that and crash.  I had a chromebook running Ubuntu with 2G of RAM and 2G of swap - about once every quarter it would crash after I'd been using it for about a month between reboots.  Doubled the swap size to 4G and the crashes never happened again.

Make the system have 4G of swap.

---

### Post by goofprog on 2016-03-16
Oh and the file browser was nautilus.  It could surf the web as well as the file system.  I think it came with gnome.

---

### Post by Bucky Ball on 2016-03-16
2Gb of RAM is standard unless you're hibernating. Then same as installed RAM or more.

---

### Post by deadflowr on 2016-03-17
> **Bucky Ball said:**
> **2Gb of RAM is standard unless you're hibernating.** Then same as installed RAM or more.

You mean swap?

I mean shouldn't you have the same RAM size as RAM installed?:D

---

### Post by Bucky Ball on 2016-03-17
> **deadflowr said:**
> You mean swap?

I mean shouldn't you have the same RAM size as RAM installed?:D

Yes, my mistake. 2Gb /swap. No. Not necessary. Some users use no /swap at all. The debate continues but the 'same size swap as installed RAM' is somewhat of a myth now. ;)

---

### Post by deadflowr on 2016-03-17
I guess my joke fell flat

---

### Post by Bucky Ball on 2016-03-17
> **deadflowr said:**
> You mean swap?

I mean shouldn't you have the same RAM size as RAM installed?:D

Ha. Right. In a bit of a rush and didn't read fully. Yes, of course you should!!!

---

### Post by sumithar on 2016-03-17
OK, in the process of changing the swap file size, i totally messed up.  I tried to reinstall the OS but ran into problems. I am opening a new thread in the installation forum!
Sorry guys!

---

### Post by TheFu on 2016-03-18
> **Bucky Ball said:**
> Yes, my mistake. 2Gb /swap. No. Not necessary. Some users use no /swap at all. The debate continues but the 'same size swap as installed RAM' is somewhat of a myth now. ;)

On a desktop, running a modern browser, with 4G of less RAM,  4G for swap is my min. Been burned.

On a desktop with 16G of RAM, I don't use swap. With 6, 8, 12G of RAM, 4G of swap seems a happy medium, provided the system doesn't hibernate. I don't due hibernation for security reasons.

On a server, the amount of swap needed is highly dependent on the workload. Since we use virtual machines for almost every server here, we can tune the RAM provided to the workload for that system and have ZERO swap.  In the beginning, when the server is first installed, I'll either provide lots of RAM or 2-4G of swap and let the systems monitoring tell me how much RAM is needed.  There is something nice about taking a 1G system and removing the RAM allocation down to 384MB with zero swap.  
```
$ top
Mem:    503444k total,   273588k used,   229856k free,     6960k buffers
Swap:        0k total,        0k used,        0k free,    36352k cached

```
Looks like I can drop this one down a little. Need to check the monthly and yearly committed RAM graphs to be certain. It is a very specialized server - email gateway - so it is basically a blocker of all-that-is-spam and then forwards real email onto the main server for that. ;)  Make sense?  Ah - looks like someone forgot to setup systems monitoring on that server (me). New task for today, like I needed another.  Ansible ... task for monitoring-client .... 

Hope this clarifies.

---

### Post by mörgæs on 2016-03-20
I guess [these methods]("http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289") carry more impact than adjusting the size of the swap partition.

---

### Post by TheFu on 2016-03-20
> **mörgæs said:**
> I guess [these methods]("http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289") carry more impact than adjusting the size of the swap partition.

That is quite the post. Lots of great info inside it. BTW, there is no need to use both 
```
sudo apt-get upgrade [fixed after the fact]
sudo apt-get dist-upgrade
```

sudo apt-get update is needed before running either upgrade/dist-upgrade or installing packages.  My rule of thumb is if I'd updated in the last 12 hrs, I don't bother doing another update.  Generally, I only patch weekly and rarely install new packages.

Previously, this post incorrectly said that only 1 of these was needed:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
That is wrong. Sorry for the mistake.

**dist-upgrade** does everything that update does according to the manpage:
```
       dist-upgrade
           dist-upgrade* in addition to performing the function of upgrade*,
           also intelligently handles changing dependencies with new versions
           of packages;
```
so - running both upgrade/dist-upgrade isn't needed. It won't do any harm.

---

### Post by montag dp on 2016-03-20
> **TheFu said:**
> That is quite the post. Lots of great info inside it. BTW, there is no need to use both 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

**dist-upgrade** does everything that update does according to the manpage:
```
       dist-upgrade
           dist-upgrade* in addition to performing the function of upgrade*,
           also intelligently handles changing dependencies with new versions
           of packages;
```
so - running both just isn't needed. It won't do any harm.

The man page you quoted says dist-upgrade performs the same function (plus more) as upgrade, not update. You should still update first to sync your system with the current state of the repos.

---

### Post by TheFu on 2016-03-20
Ever had one of those days?  I'm having more and more of them it seems.  My mistake. Yes, both are needed.

update && ( upgrade || dist-upgrade ). 

I was thinking upgrade AND dist-upgrade were written as needed. update is needed daily if new packages are being installed. I'll crawl back under the rock now. ;)  No good excuse for my mistake.

I'll edit the post above to make it clear it was incorrect.

---

### Post by montag dp on 2016-03-20
> **TheFu said:**
> Ever had one of those days?  I'm having more and more of them it seems.  My mistake. Yes, both are needed.

update && ( upgrade || dist-upgrade ). 

I was thinking upgrade AND dist-upgrade were written as needed. update is needed daily if new packages are being installed. I'll crawl back under the rock now. ;)  No good excuse for my mistake.

I'll edit the post above to make it clear it was incorrect.
No worries, I know you knew that. :)

---

### Post by coldraven on 2016-03-20
> **sumithar said:**
> I have xubuntu (I think it might be trusty tahr, not sure if the upgrade completed) running on an old gateway laptop, circa 2012.  It has 1 GB RAM.

I want to give it to my 5th grader to do some of his homework assignments which are to be done online but the Firefox browser that comes with the installation is a hog, really slow to refresh and at times unusable.

So is there some other light weight browser I could install instead from software center?
Regards
Don't be stingy just buy another GB of memory and that old beast will fly :) If you have the funds swap the HDD for a SSD, I have old netbooks that ran XP and they are very usable now.

---

### Post by Bucky Ball on 2016-03-20
> **coldraven said:**
> ... another GB of memory and that old beast will fly :) If you have the funds swap the HDD for a SSD ...

+1. As good as going out and forking out a whole lot more cash for a new machine. The performance on the old one will make you  think you are on a new machine. :D

---

### Post by Malachi_Selesnick on 2016-03-26
> [COLOR=#000000]but the Firefox browser that comes with the installation is a hog, really slow to refresh and at times unusable.[/COLOR]
Try using Lynx

---

