---
title: "jaunty 64 bit users: how much ram are you using?"
date: 2009-05-12
forum: The Cafe
---

### Post by Polygon on 2009-05-12
I posted this in the jaunty development forum, and its still kinda confusing me

with jaunty 32 bit, i used like what, no more then 500 mb of ram on daily usage at most. Usually its around 300-400...now i'm running almost the exact same setup, only 64 bit, and now im using 800-900mb?

I know that 64 bit means programs use more memory, but in both arch linux and windows 7 64 bit, i still use around the same amount of memory that i did with their respective 32 bit versions

but why is it with ubuntu that i'm suddenly using 300+ more MB of ram just by using 64 bit?

See attached screenshots.

ALSO, the way gnome-system-monitor works, it only shows the ram actually being used. it does NOT show cached ram. Because if it did, it would say that i have all of my memory used =P

And  also, side note =P Why does it say i have 3.8 gb of ram, when i am running 64 bit?

---

### Post by Skripka on 2009-05-12
Do I Spy With My Little Eye, a Firefox with a memory leak?  229MB for a web browser?

---

### Post by Polygon on 2009-05-12
well it was steady at 200 mb, and i had it running for a while, so it was most likely just keeping things cached.

but even without firefox, i'm hovering at around 800 mb =/

---

### Post by Perfect Storm on 2009-05-12
> **Polygon said:**
> well it was steady at 200 mb, and i had it running for a while, so it was most likely just keeping things cached.

but even without firefox, i'm hovering at around 800 mb =/

Doesn't seem normal as far I can see. I'm running kubuntu 9.04 64-bit with alot of bling bling atm. annd I don't come near 500MB except when having alot of stuff open at the same time.

---

### Post by Polygon on 2009-05-12
then what am i doing wrong :O

---

### Post by Perfect Storm on 2009-05-12
Can we get the full list to see?

---

### Post by hyperdude111 on 2009-05-12
You are utilizing your full RAM with 3.8, the maximum for 32bit is 3.3. I don't know why it says 3.8 instead of (i presume) 4. I have a similar issue, it says 1.8 when i have 2.

Running compiz and flash and rythmbox and some other high resource apps i am using 659mb of RAM and 0mb of swap.

---

### Post by Muffinabus on 2009-05-12
I'm pretty sure the RAM size discrepancy is caused by the manufacturer using the decimal value for bytes as opposed to the software using the binary value.

Not sure why you're using so much ram though :3

EDIT:

There has been considerable confusion about the meanings of SI (or metric) prefixes used with the word "byte", especially concerning prefixes such as kilo- (k or K) and mega- (M) as shown in the chart Prefixes for bit and byte. Since computer memory is designed with dual logic, multiples are expressed in power of two, rather than 10, the software and computer industries often use binary estimates of the SI-prefixed quantities, while producers of computer storage devices prefer the SI values. This is the reason for specifying computer hard drive capacities of, say, "100 GB" when it contains 93 GiB (or 93 GB in traditional units) of addressable storage. Because of the confusion, a contract specifying a quantity of bytes must define what the prefixes mean in terms of the contract (i.e., the alternative binary equivalents or the actual decimal values, or a binary estimate based on the actual values).

[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

---

### Post by Polygon on 2009-05-12
well, i know windows reports me as having 4 gb of ram, but i am unsure on if it is just rounding up.

and here is the full list. Ignore the fact that i am running handbrake at the moment =P

but the only extra things i am running:

handbrake
shutter
vlc
pidgin
dropbox
gwibber
gm-notify

I would hardly call that a ton of programs....and like i said, in 32 bit ubuntu, even with all those running, i never go over 400-500 mb....

---

### Post by FuturePilot on 2009-05-12
Well I can also say that I too am using around 800MB on Ubuntu 64bit whereas on the 32bit it would be rare that I would cross over 500MB. Though I'm not sure how much of a problem this is, I thought it was just due to the fact that using 64bit integers meant more memory usage.

---

### Post by Dropbear on 2009-05-12
> **hyperdude111 said:**
> You are utilizing your full RAM with 3.8, the maximum for 32bit is 3.3. I don't know why it says 3.8 instead of (i presume) 4. I have a similar issue, it says 1.8 when i have 2.

Most likely an onboard video card. The bios reserves some of the main memory for exclusive use buy the card. (it can usually be adjusted through the the bios setup) Windows tells you how much ram you have installed while Ubuntu tells you how much you can actually use.

---

### Post by BGFG on 2009-05-12
I've only ever used ubuntu 64bit. With Jaunty my system rarely goes over 500 megs on a 2 gig system. To cross the 500 barrier i usually need to have exaile open. I'll attach a screenshot in a bit, i opened a few more tabs in firefox to get my usage up..

A little off topic, could it be that python as a language is a little memory hungry ? the only isolated example i have I'll try to display with my screenshot. Take a look at utorrent(active) + wine server as opposed to Deluge idling.

@polygon, I've also adjusted my running processes using BUM, see attached

---

### Post by djungelmums on 2009-05-12
Then i must be doing some major mistake because im almost always running at 500MB.

Its a 32bit system.

---

### Post by mister_pink on 2009-05-12
It's not something thats causing loads of 32bit libraries to be loaded into memory as well as 64bit ones or something similar?

---

### Post by djungelmums on 2009-05-12
I dont know how to check that :P

---

### Post by Matthewthegreat on 2009-05-12
I use 64-bit and with normal use I hover around 600-700mb. It's strange firefox is using so much, firefox only uses about 85mb on my system.

---

### Post by BuffaloX on 2009-05-12
I'm using 500 MB and Firefox takes 200 MB with just one single tab.
I noticed that when I installed flash it installed some 32 bit libs.
I installed Flash from Synaptix, don't know if it's 32 or 64 bit.
I suspect its 32, and that is why Firefox use so much RAM.

System monitor say I have 1.9 GB total, I don't have any onboard graphics, so it should be 2.0 GB.

---

### Post by blissfulpenguin on 2009-05-12
> **Polygon said:**
> I posted this in the jaunty development forum, and its still kinda confusing me

...

x64 here and the ram is consistent with what i put in the machine.

attached screenshots n stuff.  no idea what it could be, but if you need output from any command, please don't hes. to ask.

---

### Post by samjh on 2009-05-12
I'm using x86_64, and using only 380 MB (been running Firefox for a while).

Oh, and the 3.8 GB memory issue is just the use of metric prefixes.  4,000,000,000 bytes divided by 1,048,576 bytes equals 3,815 MB = 3.8 GB. :)

---

### Post by Polygon on 2009-05-13
> **Dropbear said:**
> Most likely an onboard video card. The bios reserves some of the main memory for exclusive use buy the card. (it can usually be adjusted through the the bios setup) Windows tells you how much ram you have installed while Ubuntu tells you how much you can actually use.

i'd hope that my 160 dollar nvidia 9800 gtx came with some video card ram installed so it did not steal from my main system memory =)

but the fact that its just the decimal problem makes sense now.

and i have 64 bit everything...i hope. I made sure i installed 64 bit flash and java and all that.

Its late here, i shall check everyone's screenshots in the morning to compare

---

### Post by Skripka on 2009-05-13
> **samjh said:**
> I'm using x86_64, and using only 380 MB (been running Firefox for a while).

Oh, and the 3.8 GB memory issue is just the use of metric prefixes.  4,000,000,000 bytes divided by 1,048,576 bytes equals 3,815 MB = 3.8 GB. :)

That is all well and good...except for the fact that Arch reports that I have 3951MB of memory....and I installed 4X1024 DIMMs of memory, so I have 4096MB of memory-which I think most folks who buy memory buy just that.

---

### Post by OutOfReach on 2009-05-13
537 MB currently. Using banshee, gnome-do, conky, dropbox and firefox with 20 tabs open (yes I am using all of those tabs). It usually does get a little higher when I continue to use it.

---

### Post by Roasted on 2009-05-13
I'm running Ubuntu 9.04 64 bit on my home computer with a total of 4gb of RAM.

I think my RAM, if memory serves me (da da, psh!), that the total was 3.9 or so as well. I don't ever recall seeing on ANY computer that has 2gb of RAM - You have exactly 2 gigabytes of RAM, or 4gb of RAM - exactly 4 gigabytes of RAM. I've always seen slight differentials.

On Ubuntu, when I first boot up it seems to take very minimal RAM - only 400 or so. But once I get all of my applications running, I normally sit in the 600-900 area, depending on what I'm doing.

The other day, I was trying to see what I could max out as.

I had:

Pidgin
Thunderbird
Two instances of Firefox with multiple tabs on each
Exaile Media Player
Google Earth 5.0
Gimp

Along with several other small programs running. As I would zoom in at a high rate of speed with Google Earth 5.0, my RAM got soaked up by it. I maxed at 2.2gb of RAM used as I would be zooming in/out with it. Once I closed Google Earth, the overall usage settled down, but I still had a lot running and my system was running for long enough that I'm sure a lot of it was being cached.

---

### Post by OutOfReach on 2009-05-13
> **Roasted said:**
> 
I think my RAM, if memory serves me (da da, psh!), that the total was 3.9 or so as well. I don't ever recall seeing on ANY computer that has 2gb of RAM - You have exactly 2 gigabytes of RAM, or 4gb of RAM - exactly 4 gigabytes of RAM. I've always seen slight differentials.


Yes this is true, I have 3gb of RAM installed but it shows 2.8 GB. I think it is because of the BIOS and the kernel taking up some ram, also the fact that the memory sticks don't come with exactly that amount of memory, like hard drives.

---

### Post by Roasted on 2009-05-13
> **OutOfReach said:**
> Yes this is true, I have 3gb of RAM installed but it shows 2.8 GB. I think it is because of the BIOS and the kernel taking up some ram, also the fact that the memory sticks don't come with exactly that amount of memory, like hard drives.

My 250gb drive is only 233gb in actual usable size.

My 500gb drive is like 478 or something.

PS - This is true with Windows too. In Vista, which dual boots on the same rig I talked about above with Jaunty 64 hitting 2.2gb of RAM used, also shows the RAM as an offset number too. I.e. - not a solid 4.00 gigabytes.

---

### Post by Skripka on 2009-05-13
> **Roasted said:**
> My 250gb drive is only 233gb in actual usable size.

My 500gb drive is like 478 or something.



Yes but harddrive capactiry is openly sold as being a decimal number with disclaimers of, "actual capacity will be less".  I have ***_NEVER_*** seen RAM capacity termed as a decimal number.  ***_Never_***.

---

### Post by marco123 on 2009-05-13
total       used       free     shared    buffers     cached
Mem:          3905       2514       1391          0         51       1824
-/+ buffers/cache:        638       3267
Swap:          956          0        956

---

### Post by Joeb454 on 2009-05-13
> **Skripka said:**
> Yes but harddrive capactiry is openly sold as being a decimal number with disclaimers of, "actual capacity will be less".  I have ***_NEVER_*** seen RAM capacity termed as a decimal number.  ***_Never_***.

RAM is marketed as GB or MB

That means it's decimal, if it was the proper binary equivalent it should be marketed as GiB :)

And I'm currently using 596MB with aMSN, Firefox (2-4 tabs), Rhythmbox, Dropbox & gnome-terminal :)

---

### Post by Skripka on 2009-05-13
> **Joeb454 said:**
> RAM is marketed as GB or MB

That means it's decimal, if it was the proper binary equivalent it should be marketed as GiB :)


No it doesn't, it means they are using prefixes in their binary meaning rather than their SI powers of ten meaning, and playing it fast and loose.  When someone says they have 4GB of RAM, they _mean_ they have _4096_ megabytes of RAM-NOT _4000_ MB.  This goes for computer retailers, hardware manufacturers everywhere.

I purchased 4x1024 megabyte of RAM.  My RAM packages were sold as 2 packages of 2 GB RAM each, each package containing 2x1024 RAM.  That is 4,194,304 kilobytes total--NOT 4,000,000 kilobytes.

For disambiguation:

[http://en.wikipedia.org/wiki/JEDEC_memory_standards](http://en.wikipedia.org/wiki/JEDEC_memory_standards)

[http://linuxreviews.org/dictionary/Gigabyte/](http://linuxreviews.org/dictionary/Gigabyte/)

---

### Post by cudjoe on 2009-05-13
866 MB used, doing nothing special. 

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1978       1896         82          0        217        811
-/+ buffers/cache:        866       1112
Swap:         1215          0       1215

```

Top ten processes by memory >
```
ps aux | sort -nrk 4 | head
cudjoe   3989 11.0 10.5 776052 213816 ?       Rl   01:09   5:29 /usr/lib/firefox-3.0.10/firefox
cudjoe   4411  0.7  5.8 505136 118088 ?       S    01:16   0:17 python /usr/lib/exaile/exaile.py
root      3161 11.0  3.0 195692 61508 tty7     Rs+  01:07   5:39 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
cudjoe   4354  4.6  2.4 485048 50168 ?        Sl   01:12   2:09 /usr/bin/liferea-bin
cudjoe   4062 15.3  2.7 250736 55028 ?        Sl   01:09   7:36 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/3989-2
cudjoe   3751  0.6  2.4 345536 49508 ?        Sl   01:07   0:18 /usr/bin/cli /usr/lib/gnome-do/Do.exe
cudjoe   3732  0.8  2.2 529548 46296 ?        S    01:07   0:27 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 10f0a292d6d1d431ca124225607221711300000035050027 core ccp
cudjoe   3838  0.2  1.3 287036 28292 ?        S    01:08   0:07 python /usr/lib/gnome-applets/computertemp --oaf-activate-iid=OAFIID:GNOME_ComputertempApplet_Factory --oaf-ior-fd=37
cudjoe   3797  0.0  1.8 343280 37124 ?        Sl   01:08   0:01 mono /usr/lib/tomboy/Tomboy.exe --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=18
cudjoe   3750  0.0  1.0 190656 22184 ?        S    01:07   0:01 easystroke

```

---

### Post by Xbehave on 2009-05-13
ram is sold in binary units 1GB is 1GB but your graphics card on a laptop will eat up to 512MB

Im on debian and im getting similar usage on my 64bit system
```
             total       used       free     shared    buffers     cached
Mem:          1473       1430         43          0         33        563
-/+ buffers/cache:        833        639
Swap:          951          9        942

```
but if im reading it right its 1430-833&#8776;600M (most of it is amarok 15% (huge playlist) and firefox 8% (lots of flash). 

I really don't see a problem though, ram is there to be used, ram usage is only a problem if you have performance problems on low end systems and i rarely saw any issues on a system with 256MB so i dont think they're significant!

---

### Post by aeiah on 2009-05-13
728mb used of 2gb. i never used this much with 32bit, but then again i was on 7.10 x86 before installing 9.04 x64. this pc has also been on for two days with deluge, exaile and firefox doing their thing. even so, its a fair bit of load but it doesn't bother me too much. if things start to get serious ill just crack out crunchbang

---

### Post by dagrump on 2009-05-13
348 M a steady 8%. Only a single page in firefox. Only time I see alot of ram use is if Virtualbox is running. Win2k ain't using much of what I gave it, so that's a pointless. It will run on 512M fine. It sure ain't purrty!!
Win2k is running in VBox, it hasn't been played with in weeks. Want to see if some old games are going to play nicely.
I don't have any effects running, that would push it up.

---

### Post by skygazer on 2009-05-14
Just installed Dual boot Hardy 8.04 LTS and Jaunty 9.04 with 1GB RAM and 160GB HDD

Ram usage increases from 15% to 49%
Processor Usage increases from ~10% to 25% 

Now i need 387 MB ram even with firefox window open and no other app running.. Its Strange and the system feels slightly heavy and solid as opposed to Hardy.. I had some lag before installing the nvidia proprietory drivers but now it seems to be cured..

---

### Post by HavocXphere on 2009-05-14
Firefox mem usage is very deceptive. e.g. When I saw this thread, it was at ~200mb. After restarting FF its at 60mb (Similar # of tabs).

Also, I was under the impression this is a general FF issue not specific to Jaunty x64. I've seen 300mb+ usage on XP, Vista etc too.

If its used for cache then thats great. If its a mem leak then its not great.

---

### Post by coldReactive on 2009-05-14
I must be doing something right, this is with compiz enabled.

But scrolling firefox causes the CPU to hike incredibly.

---

