---
title: "System 76... Good or Bad?"
date: 2015-09-04
forum: System76 Support
---

### Post by jdd.wheeler on 2015-09-04
Can anyone tell me if buying a system 76 laptop would be worth it? I have read reviews online and I have seen more bad than good.

---

### Post by PaulW2U on 2015-09-04
*Thread moved to **System76 Support**.*

I've moved your post here but could you tell us about any particular concerns that you have?

---

### Post by Geoffrey_Arndt on 2015-09-06
System76 is a systems *integrator*.   Clevo Computer Company (a very large computer mfg from Taiwan and China Mainland build some of their PC's. They may have other Asian mfg sources also.)    System76 evaluates the mfg's core offerings, and specifies any engineering and configs required, writes or modifies custom drivers, and supports customers pre & post purchase.  

They've been very responsive re my questions, but I personally have zero issues on a Galago Ultra Pro (loaded) running Ubuntu 15.04.    My system runs  (since Dec 2014) between 4 to 12 hrs daily.    _Absolutely Zero issues_, and everything worked "out of the box".

The only minor issue some have is the Galago (& perhaps other laptops are 100% plastic cases) - - no brushed metal, etc.    But the construction (albeit light) seems more than solid enough for my use & needs.   Outstanding graphics/resolution, average decent quality keyboard, above average trackpad, 2/3 usb ports use v3.    Re the internals, excellent options available for user via the website order process.   All components are first-tier known high quality (intel, samsung, kingston, crucial, etc. (no cheap junk).  

So, it's a decent laptop, and should last for years unless you drop a 2 or 3 pound rock on it.   I plan to buy from System76 in future (desktops and laptops) . . . and no, I have no vested interests in the company.

---

### Post by Kale_Freemon on 2015-09-06
Having been using the Lemur 5 for the last few months (since June), I have to say that System 76 is the way to go if you want a decent computer running Ubuntu from the get go. Runs quickly, smoothly, and everything works without any issues, even after a reinstall due to an SSD upgrade (didn't add one in during my initial purchase since I already had one). Just had to reinstall the System 76 drivers and I was off to the races.

They also offer a payment plan for those of us (i.e. myself) who cannot afford to drop money down on a laptop all at once.

---

### Post by fyfe54 on 2015-09-06
I have had a Gazelle Pro since April 2014 and it has been perfect; fast and reliable.  Purchase process was easy with lots of support.  I would definitely go back for my next laptop, but realistically that will not befor a while as this one just works.

---

### Post by mike353 on 2015-09-10
Pretty good. I got a Kudu Pro a little over a year ago. 

I was at first very skeptical--especially of their choice to support Ubuntu.  However, it appears that this combination of hardware(Clevo)/firmware (They probably changed more than just add the pretty logo in the BIOS.) is really low-maintenance with Linux. (Also, Ubuntu is so widely used now I suspect it is in a position to start defining conventions.)

Kudu runs like a sick dog in FreeBSD but so do most other Haswell/Intel i7 systems. FreeBSD, famous for its stability, locks up hard in painfully slow, unaccellerated Xorg. But they never said it was a good FreeBSD machine....

It also makes a fantastic Hackintosh as Apple STILL does not offer a 17" matte laptop with ENOUGH USB ports. Intel HD4600 is now fully supported in Yosemite, with some minor DSDT hacking.

But I spend most of my time in Ubuntu: This has been the most trouble-free Linux system I have ever used and it is the first serious alternative to Macintosh that I have considered since 2003.  (For me, the dealbreaker with Mac is that there is nothing native that is even close to ZFS for backups and snapshots. Yes, you can install ZFS on mac, but then what's the point if you can't use Spotlight/TimeMachine.... but that's another rant.)

Kudu's video performance is also lacklustre, probably due to corporate hostility to Linux/Open Source more than anything else: Netflix is a little choppy in Chrome/Linux but completely flawless in Mac OS X Yosemite/AnyBrowser. I did not test 3D since there is no dedicated graphics processor. 

The audio quality for some reason is inconsistently not spectacular (VT1802) in Linux but always just fine with Hackintosh Yosemite using the VoodooHDA driver.

 It's good enough for movies and games, but not for quiet-room listening with decent quality headphones. For a while, I thought it had something to do with using Amarok/Rhythmbox/Banshee or their interaction with gstreamer backend(s?) but I give up: too much silly-named, duplicated effort in the Linux audio player world! I'm also suspicious of pulseaudio sound server but it is a big hairy mess I do not feel inclined to learn about. It seems a crazy amount of complexity just to be able to have more than one process access the audio hardware simultaneously, a feature I didn't know I needed.

So in a nutshell,  neither Ubuntu Linux nor Mac EASILY, OOB, is completely satisfactory, but with System76, at least you know you have decent Linux hardware support: You're not going to be spending ages picking apart DSDT/SSDT to make the function keys work; you're not going to be stuck running framebuffer Xorg or dealing with strange hardware problems because only you and about 20 other people have tested your hardware on Linux; sound and video will work tolerably well OOB; unlike in the world of MSFT, AAPL hardware you'll still have the option to be able to boot your computer from a variety of USB/DVD media.

---

### Post by fallenshadow on 2015-09-18
Very good, got myself a Galago UltraPro last year. Never had any issues, runs fast and smooth with everything.  Only complaint I would have is the audio isn't that great on it. (then again laptop audio usually sucks on everything)

Have no idea what support is like but I haven't had any need to contact support just yet.

---

### Post by mike353 on 2015-09-21
I got interested in the audio issue again and now I'm pretty sure it is pulseaudio. I have no idea how to disable this in stock Ubuntu so I booted Lubuntu from a USB stick and sound quality is consistently better using ALSA and any player you want.

 In fact, so much of the annoying U-bloat ("integration" with creepy Facebook, yahoo, amazon, google spyware, worthless disk indexing that never seems to find anything, and silly, ugly clunktackular Unity UI) is gone that I'm considering installing it for real. 

Try it and see how your sound is. With a decent set of headphones, like the Grado SR-80, the sound isn't too bad.

---

### Post by Geoffrey_Arndt on 2015-09-21
Hmm, Mike353 . . did you try Pulse Audio Manager app to fully config/tweak the audio?   

Re your comments about Ubuntu's desktops (DE's) . . . I'm of the school that appreciates user choice and options .   My personal production systems all use Unity.   A couple older test machines run about a dozen variations of cinnamon, mate, openbox, fluxbox, kde/plasma, DDE, and my own customizations.  None are as "elegant" and functional (excluding sysadmin) as Unity (although Gnome3 is now close).   But. let each user decide which DE is best for them and their specific hardware.

(in IT terms, "elegant" refers to a systems capability to achieve a _functional goal_ in a lean, error-free, intuitive manner).

---

### Post by pgte3 on 2015-09-21
I bought a Kudu Pro with quad core i7 processors. I find that the fan is loud and runs more than I expected. No other complaints.

---

### Post by mike353 on 2015-09-22
> **Geoffrey_Arndt said:**
> Hmm, Mike353 . . did you try** Pulse Audio Manager app** to fully config/tweak the audio?   

Re your comments about Ubuntu's desktops (DE's) . . . I'm of the school that appreciates user choice and options .   My personal production systems all use Unity.   A couple older test machines run about a dozen variations of cinnamon, mate, openbox, fluxbox, kde/plasma, DDE, and my own customizations.  **None are as "elegant" and functional **(excluding sysadmin) as Unity (although Gnome3 is now close).   But. let each user decide which DE is best for them and their specific hardware.

(in IT terms, "elegant" refers to a systems capability to achieve a _functional goal_ in a lean, error-free, intuitive manner).

What is "Pulse Audio Manager"? It does not turn up in a search of the software center.  What do I need to apt-get install?

There is nothing functional about transparency effects and background blurring: it's just needless eyecandy to bring older GPUs to their knees, waste battery power, make fans run faster, and ultimately make people buy newer hardware they don't really need.  Great for games, pointless for trying to get things done.

I dunno, with a name like "canonical," (and a DE called "Unity") I wonder how much a company wants to give users choice. 

```

> dict canonical

From WordNet (r) 3.0 (2006) [wn]:

  canonical
      adj 1: appearing in a biblical canon; "a canonical book of the
             Christian New Testament" [syn: {canonic}, {canonical}]
      2: of or relating to or required by canon law [syn: {canonic},
         {canonical}]
      3: reduced to the simplest and most significant form possible
         without loss of generality; "a basic story line"; "a
         canonical syllable pattern" [syn: {basic}, {canonic},
         {canonical}]
      4: conforming to orthodox or recognized rules; "the drinking of
         cocktails was as canonical a rite as the mixing"- Sinclair
         Lewis [syn: {canonic}, {canonical}, {sanctioned}]

```

---

### Post by mike353 on 2015-09-22
> **pgte3 said:**
> I bought a Kudu Pro with quad core i7 processors. I find that the fan is loud and runs more than I expected. No other complaints.

What scaling_driver and scaling_governor  are running? I got my Kudu a while ago, I think around Ubuntu 14.something. It was running ondemand and the fans were very irritating. I upgraded to 15.10 and things got a whole lot quieter with intel_pstate / powersave.

If you do not have long, horrid /proc and /sys paths memorized, just apt-get install tlp (from linrunner.de, although I think it is part of the distribution now) and take a look at its /etc/default/tlp config file.  It can be used to quickly get info about cpu/disk/usb/wifi other power management:

```
sudo tlp-stat -p

--- TLP 0.8 --------------------------------------------

+++ Processor
CPU Model      = Intel(R) Core(TM) i7-4710MQ CPU @ 2.50GHz

/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu4/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu4/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu5/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu5/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu6/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu6/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu6/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/cpu7/cpufreq/scaling_driver    = intel_pstate
/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor  = powersave
/sys/devices/system/cpu/cpu7/cpufreq/scaling_min_freq  =   800000 [kHz]
/sys/devices/system/cpu/cpu7/cpufreq/scaling_max_freq  =  3500000 [kHz]

/sys/devices/system/cpu/intel_pstate/min_perf_pct      = 22
/sys/devices/system/cpu/intel_pstate/max_perf_pct      = 100
/sys/devices/system/cpu/intel_pstate/no_turbo          = 0

x86_energy_perf_policy.cpu0                            = performance
x86_energy_perf_policy.cpu1                            = performance
x86_energy_perf_policy.cpu2                            = performance
x86_energy_perf_policy.cpu3                            = performance
x86_energy_perf_policy.cpu4                            = performance
x86_energy_perf_policy.cpu5                            = performance
x86_energy_perf_policy.cpu6                            = performance
x86_energy_perf_policy.cpu7                            = performance

/proc/sys/kernel/nmi_watchdog                          = 0

+++ Undervolting
PHC kernel not available.

```

btw, we are soooo off topic w/this thread, LOL.

---

### Post by him610 on 2015-10-25
To answer your question, my experience with System76 leads me to say, "Good!"

I have used a Pangolin Performance laptop since I purchased it about 3 years ago. I don't believe System76 offers that particular model any more, but I have been very happy with it. It is the only machine that my spouse uses now. Other than swapping out the original 750GB HDD for a 250GB SSD, it has all of its original parts - Intel Core i5-3210M Processor, Intel HD Graphics 4000, 8 GB DDR3 RAM, Intel Centrino Advanced-N 6235AN 802.11A/B/G/N Wireless +Bluetooth. It came with Ubuntu  12.10 that has since been upgraded to Ubuntu 14.04.3.
Never have I experienced any problems with hardware, drivers, or software since owning this machine; everything has just always worked.

Hope this helps.

---

### Post by Ender Black on 2015-10-27
I recently purchased a Gazelle Pro (i7, 16GB RAM, 500GB SSD w/ 1TB Extra Drive) and have been nothing short of impressed.  I've been running a numerical hydrology model on it for the past seven days and can still sit with it on my lap without feeling like I'm getting cooked.  It's not a bad stress test, though I cannot wait for it to finish so I don't have to hear the fan whirring away ceaselessly.  The fan is only slightly louder than my Surface Pro 2's fan, which isn't bad considering the size difference between their cooling systems.  If I were to have any complaint it would be the lack of a decent key-click detection for the touchpad.  I don't believe that's a System76 thing, more of a linux thing.  I would recommend System76.  Now, if only they would hurry up and get parts in for their Sable line and ship the rest of my order....

---

### Post by ~cyrus~ on 2015-10-27
I've been running a Bonobo Extreme since February 2013 with absolutely no hardware issues at all. My OS of choice is Archlinux and the only issue there is the fingerprint scanner that I tried more than a year ago, which was hit and miss so don't use that feature at all.

---

### Post by courseinmiracles2 on 2015-10-27
Pulse audio
[https://apps.ubuntu.com/cat/applications/precise/paman/](https://apps.ubuntu.com/cat/applications/precise/paman/)

---

### Post by Wraflov on 2015-11-01
So, I'm about to buy my fist Linux machine.  I was looking at Los Alamos, but they only use Lenovo machines, and after all the Superfish and what-not, I think I'm going to go with a System76.  (Price is right.)  Am I making a mistake here?  Reveiws in this thread seem to be mixed.

---

### Post by Geoffrey_Arndt on 2015-11-03
Wraflov . . . the few negative reviews I've read are not especially credible.   

You should be aware System76 is a systems integrator . . . . customizing a well known OEM product built by Clevo Computers and other reliable Asian manufacturers.   They pre-select the right boards, chipsets, gpu, etc.   Additionally they build and maintain the System76 drivers via their PPA.   Last but not least, they offer life of the product OS support.   

The one minor complaint I've expressed about my GalagoPro laptop is simply that the unit is 100% plastic . . . that's not a huge issue for me, but the aesthetics of a metal chassis just seem a bit more durable (but again, if I don't drop my 4 pound rock paperweight on it, I'm not expecting any breakage.)

note that System76 is updating their laptop line with a metal chassis offering ([https://system76.com/laptops/oryx)]("https://system76.com/laptops/oryx")

Just my experience, and I do plan on future purchases from this company (all-in-one desktop for example).

---

### Post by kurt18947 on 2015-11-03
> **Wraflov said:**
> So, I'm about to buy my fist Linux machine.  I was looking at Los Alamos, but they only use Lenovo machines, and after all the Superfish and what-not, I think I'm going to go with a System76.  (Price is right.)  Am I making a mistake here?  Reveiws in this thread seem to be mixed.

For me, the Thinkpad ultranav trackpoint/touchpad type pointing devices are mandatory and System76 doesn't offer a version so i haven't looked seriously at their offerings. Remember that people often don't post reviews about things they're pleased with nearly as often as things they're unhappy with or are looking for solutions/workarounds.) Lenovo does include bloatware in their offerings (as do other 'mainstream' manufacturers) but that bloatware isn't an issue with *buntu installs.

---

### Post by Wraflov on 2015-11-05
I admit that the lifetime support is a selling point.  My only worry is that the machine is put together sloppily.  Loud fans and plastic cases I can deal with.  Hardware that isn't assembled properly is a deal breaker for me as I use my laptop daily and mailing it back and forth for repair would really make things difficult for me.

---

### Post by pauljw on 2015-11-06
> **Wraflov said:**
> I admit that the lifetime support is a selling point.  My only worry is that the machine is put together sloppily.  Loud fans and plastic cases I can deal with.  Hardware that isn't assembled properly is a deal breaker for me as I use my laptop daily and mailing it back and forth for repair would really make things difficult for me.

I would say go for it, I have a Gazelle-Pro that is soon to be 2yrs old and have had zero problems with it.  Yes, it's plastic, but it still feels solid.  I have it on 24/7 and share it with my daughter.  The fan rarely runs and is variable so it's not normally very loud when it does.  Right now I have 26 tabs open in Firefox; Thunderbird; and xchat w/4 channels open.  CPU is showing 3-4 percent usage and 1.44G out of 8G RAM in use.  Everything just works out of the box.

One thing I recommend, pick yourself up an xpad, your lap and your laptop will thank you.

---

### Post by Geoffrey_Arndt on 2015-11-06
Also if you're familiar with Sager Gaming PC's . . . these all come from the same manufacturer.   Quality is excellent (as most Taiwan based companies are).

---

### Post by one.finefellow on 2015-11-08
My Gazelle Pro is one of the best electronic devices I have ever purchased. If there's any negative reviews it's because those who bought their computers were looking for something more than System76 offers. The laptop works out of the box and is seamless with several popular Linux programs. Some things require a little more knowledge to configure, which one would expect working with Linux software.

---

### Post by Wraflov on 2015-11-08
One last question: which System76 laptop would you recommend for gaming through Steam?

---

### Post by Geoffrey_Arndt on 2015-11-09
Looks like System76 has revamped their hardware models for laptops - see link below.   Of the 3 models (seemingly all available), the Oryx or Serval would be great for Steam (with Serval 17" being top choice).   But, each laptop can be customized for your needs:

[https://system76.com/laptops](https://system76.com/laptops)

---

### Post by saamde on 2015-11-23
It's been love hate relationship with the company. I have a Lemur Ultra since 2013, so about two years. I love the idea of what they are doing but haven't been thrilled with the execution. I always had power problems with my laptop, it would go from charging to not charging for no reason and I was always fiddling with the power cord, which finally broke, and the replacement for that was a bit expensive but after replacing the charging cord the connection problems got worse, not better. Then, about two weeks ago smoke started coming from the jack and I quickly unplugged it, the laptop ran fine on the battery but I wasn't about to plug it back in so I sent it back to system76 for a repair. They told me that not only was the jack fried but so was the motherboard, they couldn't explain why the laptop worked fine under battery power, they claimed it didn't work at all. I was ok with all this, the cost was around $300, but because their diagnosis seemed to differ a little from what I witnessed I asked them to give me back the broken motherboard, my dad always said if you don't trust the mechanics replacement ask them for the broken part, system 76 refused to send me back my broken motherboard and that I felt like was a second red flag, first being an overly expensive charger, not to mention the main sin that the power connection was so wonky and finally fried. They were rude and unhelpful the moment I started to ask questions that were outside the box. So in the end, sadly, my Lemur Ultra will be my last System 76 laptop.

---

### Post by Skaperen on 2015-11-24
> **saamde said:**
> ... I asked them to give me back the broken motherboard, my dad always said if you don't trust the mechanics replacement ask them for the broken part, system 76 refused to send me back my broken motherboard ...
try that with a dead car battery; they will refuse.   replacement car batteries are lower in price (maybe not for you) because the lead plates are going to be recycled.  many new battery pricing deals depend on you bringing in an old battery.

many parts can be recovered from a motherboard with a few dead parts; just heat it up and many chips and other parts just fall off.

---

### Post by pauljw on 2015-11-24
> **Skaperen said:**
> try that with a dead car battery; they will refuse.   replacement car batteries are lower in price (maybe not for you) because the lead plates are going to be recycled.  many new battery pricing deals depend on you bringing in an old battery.

many parts can be recovered from a motherboard with a few dead parts; just heat it up and many chips and other parts just fall off.

Apples to oranges there.  The OP bought his laptop giving him ownership of the motherboard in it, so unless Sys76 replaced the mb for free, which he didn't say, then he still owns it and should have it back if he wants it.  Now, if replacement was free, Sys76 owns it and of course wouldn't be obligated to give it back.

When replacing a battery, there's normally a core charge that you do get back for your old battery.

---

### Post by saamde on 2015-11-24
They did, after a couple days of refusing to, agree to send me my broken motherboard.  They told me that typically broken motherboards get sent back to the manufacturer. I saw in another thread that their repair shop, according to the customer, had replaced a few things unnecessarily. What Skaperen said about car batteries does make some sense, I wonder if the manufacturer pays sys76 for the old mb? If they do get money for old boards it wasn't visible in the bill they sent me, they charged me $251 for a new motherboard. I feel like pauljw that unless they are going to pay me for the old mb and I agree to that, the mb belongs to me, and they should send it back if I ask them to, no questions asked.

---

### Post by pauljw on 2015-11-28
Glad to hear you got it worked out.

---

### Post by philbert on 2015-12-02
I purchased a Gazelle Pro 7 three years ago,   Have upgraded to every version of Ubuntu released since then, and am at 15.10 now, and have had no issues with it.

---

### Post by hawkmage on 2015-12-10
From my experience I would say that System76 is a good buy and would recommend them.  Here is an overview of my experience of System76 over the last 2 years.  

In December of 2013 I bought a Bonobo Extreme laptop (bonx7) and have had no major issues with it.  The only thing I would have liked to be better is the trackpad sensitivity, trying to click the pointer often moves so it is not great for precision use.  I have run a number of Linux distros on it without any issue other than distro specific issues with drivers for things like the nVidia card that you do not run into if you stick with Ubuntu that comes on the system.  

A year later replacing an ageing desktop I bought a Leopard Extreme (leox5).  I have been quite happy with this system as well.  I did have one issue after about 10 months where during boot the POST started to take over 2 minutes and I was getting errors during boot about a the status of a USB device couldn't be read.  All of the USB ports seemed to be working when I plugged something into them, after a handful of messages on a support ticket I opened it was decided that there was a hardware problem and that since it was still under warranty they sent me an RMA and shipping label and I sent it in.  It took about 2 weeks to diagnose, fix (replaced the motherboard) and ship my system back to me.

---

### Post by DragonBoy on 2016-07-19
I purchased a Lemur from System 76 over a year ago. This system rocks and been running like a champ. It has no issues with the following Ubuntu releases (15.04, 15.10, and 16.04). The support from System 76 team has been great. I had a few questions that I sent them via their online web support. They responded back quickly.

I would recommend either the Lemur if you want to be portable or the Meerkat if you want a small foot print for desktop. Fairly cheap with good hardware specs.

---

### Post by Replicon on 2016-08-07
I've owned three System76 computers: A Serval P from way back when (2008?), my current main box (Wild Dog Performance), and a new Lemur laptop I got for travel. All three have been great.

(p.s. This is, in part, a test post - I can't post new threads in this forum for some reason (no access to newthread.php) - just testing to see if it's because of the System76 forum, or because newthread is generally broken)

---

### Post by Gremmie on 2016-09-24
I have a Gazelle laptop that I got around January of 2014.

When it arrived, the back cover had not been assembled correctly and it had a bulge in it. I ended up snapping some of the little clips off while trying to re-seat it. System76 sent me a new back cover and some screws for free, which I appreciated.

The computer itself seemed fine. Ubuntu ran great on it, and I always updated to the latest versions without issue.

In March of 2015 it started taking minutes to POST. It was just out of warranty, of course. I ended up sending it back to System76 to replace the motherboard.

Now my display is going bad. It has developed a white spot on the lower right edge where all the pixels are brighter than their surroundings. And I have a thin, 1 pixel, vertical black line that goes down the exact center of the screen. This line appears when the laptop has been on for a while (heat?). It appears even in the bios screen. My laptop is about 2 years and 9 months old at this point. 

So maybe I just got unlucky but I'm not happy with the quality of components. Currently trying to decide if I should send it back for repair again or just move on to another laptop from another vendor.

System76 as a company seems like a great idea. They have a nice, easy to use website and I can't fault them for their customer support. However I haven't had the greatest experience with the hardware they use.

---

### Post by neu5eeCh on 2017-01-02
My experience hasn't been so great. Compared to current laptops made by Dell, HP or Lenovo, System 76's laptops feel outdated and clunky. Within a couple months of buying my Kudu Pro, I noticed a dead pixel. System 76 doesn't cover dead pixels under their normal warranty. So be it. I've owned dozens of other laptops and have flat screen monitors that are over a decade old. None of them have dead pixels. Further, the colors on the Kudu Pro are dull and never compared to brightness or crispness of my Lenovo Yoga. I never liked it.

Just recently, the Kudu Pro has begun hard-rebooting at random. All in all, one gets the impression that System 76 puts their laptops together with second rate parts. 

By comparison, I pulled an old HP desktop out of the metal recycling bin after buying the Kudu. It had been rained on. So had the monitor. Additionally, the case for the HP was missing so that the motherboard had been exposed to the weather. I put in an SSD and it, and the monitor, are humming along beautifully. Outlasted the Kudu Pro.

So, that's my experience. I, personally, will not be returning to System 76. I'll buy the latest laptop from HP, Dell or Lenovo and install  LInux on it myself. I'm typing this on a Lenovo Yoga 2 with no dead pixels and nary an issue.

**Edit: **Hibernate never worked on the Kudu Pro. Seems to me that if one is buying a preloaded Linux machine, everything should just work, otherwise why bother?

---

### Post by Geoffrey_Arndt on 2017-01-04
[http://www.xoticpc.com/](http://www.xoticpc.com/)

[http://www.clevo.com.tw/clevo_pro.asp?lang=en](http://www.clevo.com.tw/clevo_pro.asp?lang=en)

System76 engineers work with Clevo in a similar manner as does xoticpc, and other major brands/names.       

There is another OEM for AIO's and Desktops.     All mainstream stuff and components.  

System76 is a small (15 or so employees) but dedicated company and perhaps their main contribution is knowing what hardware works with Ubuntu and writing/tweaking the Sys76 drivers.

Have two systems with zero issues over several years, and I do plan on buying from them again (rather than go through the quagmire of the HP's etc.)

---

### Post by g33zr on 2017-01-07
I have a System76 Pangolin (Clevo) laptop that's entered its 4th year. I've run several different Linux distros on it since I bought it and am now running Ubuntu MATE on it with no issues. My only complaint about the Pangolin is the battery life isn't great, but the newer System76 laptops have better battery life. I also have a System76 desktop PC, the Sable all-in-one, which is an Asus PC modified for System76. 

Would I recommend System76? Yes. 

Would I buy another one? Yes.

---

### Post by kanyatula on 2017-05-27
I'm considering purchasing a Meerkat with a matte pro IPS display. Anyone here have any experience with the monitors system76 uses in their desktop custom builds? Do they really not allow returns if the display breaks and is within warranty? Thanks for any answers.

---

### Post by april-system76 on 2017-05-29
> **kanyatula said:**
> I'm considering purchasing a Meerkat with a matte pro IPS display. Anyone here have any experience with the monitors system76 uses in their desktop custom builds? Do they really not allow returns if the display breaks and is within warranty? Thanks for any answers.

We use ViewSonic displays in our desktop builds. We allow returns on all purchases including accessories within the first 30 days (as outlined in the [warranty]("https://system76.com/warranty")) but accessories are not explicitly covered by warranty. If it's not working out of the box, we'll replace it for you. Anything after that is covered by the manufacturer's (ViewSonic's) warranty, and you'd contact them for service and support on accessories. I hope that answers your questions!

Also, the Meerkat mounts to the ViewSonic displays quite nicely if you're looking for a good all-in-one solution. Of course, if it's behind the monitor, the sweet S76 logo on the top case is hidden from view ;)

---

### Post by sidewaz on 2017-06-28
What are the true 2017 Lemur or Galago battery life limits (hours with moderate use)?  

I'm currently running Mint / Windows dual booted on a very cheap Lenovo.  I googled Linux laptops and got mainly results for the Dell 13 XPS and System 76, I just want to make a clean break from Windows at home and just deal with it at work.

---

### Post by fallenshadow on 2017-06-30
I've seen people post 4-5 hours for the Galago. For the Lemur some said 4-5 hours and others said 8-9 hours. So I'm not entirely sure but some reviews online did say it comes with excellent battery life.

---

### Post by dshookowsky on 2017-07-13
I may be the odd one out here, but I bought a Gazelle w/16gb RAM in December 2016 and the thing is a dog.  Wifi was constantly dropping out and the fan wouldn't stop blowing under light use.  I ended up buying an Acer with discrete graphics for a third of the price.  Hoping I can get some of my money back selling it on eBay.

---

### Post by kepler-421b on 2017-07-15
I've had no problems with the gazelle

---

### Post by schmudde on 2017-08-30
I have a Lemur. The battery life is in line with my Apple laptop from 2015. Under very heavy usage (some combination of video playing, editing multimedia, web surfing, programming), I get a little under 4 hours. If I'm just editing some text and doing a little browsing, I'm around 8. 

I wouldn't say the battery life is as good as Apple's, but it's not far from it. The ability to easily replace the battery in a few years means that the Lemur will age better, which is a bonus.

/Schmüdde

---

### Post by Cowchip7 on 2017-09-16
> **sidewaz said:**
> What are the true 2017 Lemur or Galago battery life limits (hours with moderate use)?  

I'm currently running Mint / Windows dual booted on a very cheap Lenovo.  I googled Linux laptops and got mainly results for the Dell 13 XPS and System 76, I just want to make a clean break from Windows at home and just deal with it at work.

I bought my lemur last year. It has a SSD and only gets about 3 hours of battery life with light use: web browsing. The battery life is my biggest complaint. Other than that, the computer has been great.

---

### Post by ddraper2 on 2017-09-18
I bought a somewhat loaded Gazelle in the summer of 2013. Here is a somewhat chronological history of events.

09/13 - Machine delivered. 13.04

09/13 - Problems with the keyboard missing keystrokes. Various keys and not consistently missing but enough where it bothered me. Never really found the problem. It seemed to get better and worse over the life of the laptop. Never completely went away ever. Never cared for the feel of the keyboard. Honestly I thought it was a cheap ass keyboard.

09/13 - After a few days I notice noises in the machine when moving it around. Power down and shake it and you can hear stuff inside the machine. Open machine and shake. A few screws fall out. I look around and find where the screws go and put them back in locktite blue. Check other screws and find a bunch that are lose. Basically remove every screw I can find, add locktite blue and reinstall.

11/13 - Upgrade to 13.10 . Sound no longer works through speakers on external monitor plugged into HDMI port. After laptop resume from suspend (close lid, then open lid) and sound no longer works. Reinstall all the ALSA and Pulse audio stuff. Mess with configurations and all that crap. Read a bunch of stuff about others having the same similar problems. Write a shell script to kill of processes and then reload ALSO and restart Pulse audio. This works for the resume/suspend sound issues. For HDMI issues only way to get sound to work is to manually open GUI controls and switch sound output over the HDMI and then switch back to speakers when done.
 
05/14 - Update to 14.04 LTS . HDMI sound problems are now fixed. Suspend/Resume sound problems still there however still can fixed by running my shell script to reset and reload. Suspend/Resume sound problems will never be resolved during the life of the laptop.

12/16 - Right side hinge of screen mount breaks. There are 2 screws on the side of the hinge for the main laptop. They screw into two plastic threaded pylons that are part of the case. These two pylons break off and the hinge is now free floating on that side. I try using epoxy to fix but no go. Each time you open the display the hinge moves and causes the case to separate. Use duct tape to try and hold things together.

08/17 - By now the hinge issue is bad. Case is separating more and more. Intermittent power shut off if you go to open/close the display. Must use one hand to hold case so that it does not separate when opening and closing.

09/17 - Close case to suspend laptop. Laptop never powers on again. Take apart laptop and see the floating hinge has been wearing on a ribbon cable coming off the main power switch and worn it down. Looks like either a power short or a broken connection of some type. Also I suspect a switch in the hinge may not be working correctly and the laptop thinks the display is closed so that is why it won't power on. Regardless I have no plans to fix the laptop. After almost exactly 4 years of almost daily use and extensive travel I figure I got my money's worth out of the machine. I removed the hard drive and put it in an external case with USB cable and read all the data off it and did not lose any data.

So now came the real question. What about a replacement.

My first thoughts were no System 76 for 2 real obvious reasons. I hated the keyboard on the Gazelle and it dropped keystrokes from the day I got it until it dies. Sometimes worse than others but always. My second reason was price. No doubt you can get equivalent hardware cheaper from other vendors. Why stay? For the most part the ease of install and hardware support. Linux is installed and drivers are there and supported for the hardware. With Dell and Lenovo you can install Linux but driver support might not be there or work the way you expect. I am perfectly capable of chasing down drivers and tweking settings and making things work but do i want to. Time is money and I will admit that I am getting older and my tolerance for that stuff is just not there. 

After looking around for a machine and trying my nephew's Sager which has the same keyboard as Oryx Pro. I decided if the Oryx Pro's keyboard was the same as the Sager I would be fine with that. I order an Oryx Pro. I paid for the rush service to get it out as I needed a machine ASAP. I ordered it last Monday and they delivered it Friday. So far, so good.

---

### Post by monkeybrain20122 on 2017-12-12
Got a new job and they bought me an Oryx pro for heavy duty number crunching (deep neuralnet and stuffs) Sweet! It is perfect and it costs $2300, I can't afford that if I have to pay out of my own pocket. The power brick is almost heavier than the laptop, but I am just happy I have it.

---

### Post by vasa1 on 2017-12-13
> **monkeybrain20122 said:**
> Got a new job and they bought me an Oryx pro for heavy duty number crunching (deep neuralnet and stuffs) Sweet! It is perfect and it costs $2300, I can't afford that if I have to pay out of my own pocket. The power brick is almost heavier than the laptop, but I am just happy I have it.
So does it have their OS (Pop! something)?

---

### Post by monkeybrain20122 on 2017-12-13
> **vasa1 said:**
> So does it have their OS (Pop! something)?
It is an option, but I picked vanilla Ubuntu. :)

---

### Post by slava84 on 2018-04-06
I have Kudu, and it sucks in several key aspects for the money I paid (1350$). When I bought it I had it upgraded with SSD, 16GB RAM and i7 core 2500MHz. I decided to see if Linux-dedicated computer will work any better then a random (originally Windows-based) with Ubuntu installed on it. Well, it's not - I see no difference at all. The Clevo brand is a cheap one (if someone didn't know System76 re-brands Clevo),  I guess that's why they chose it. It is all plastic, flimsy-built, very thick, heavy, and very uncomfortable to work on. Touchpad SUCKS completely -  completely unusable! - I have never seen one that was worse.  They told me at system76 when I complained that  I would need to get used to it - well, I could not, neither did anyone else I gave it a try. It is a big problem for me, much bigger then I had thought before.  Even with minor task - the laptop starts to heat-up and turns on its fan - extremely noisy. When Im on Skype and the fan turns one people keep asking what a hell was that?. The charger is huge, and so heavy that can be used as a weapon. The main reason I did not return it - it was too late, and I wanted to make sure I use it long enough to get used to it properly. After 3 years I still didnt. It still feels awkward and I hate it every aspect of the laptop. I had problems with WiFi connectivity too. Overall -  it work - yes it does, but so is the cheap 300$ HP laptop I picked at BestBuy, and installed Ubuntu on it. No problems at all. It used to be an issue in the past , but this days almost every laptop you chose will be compatible with Linux. System76 has a very fancy website and ability to customize the laptops you buy is attractive, but their return rate is huge, and I'm not sure who are the people who write positive reviews about their laptops and why. I suspect now it is a part of their marketing strategy. It still works - after 3 years, but these days it is not enough. I can only use it as a desktop replacement - it is a little more convenient, as I occasionally need to take it from my office back home. But if you think you can travel with it - forget it. I think it is VERY BAD,  for the money they ask for it anyone can build a better laptop. When this piece of crap finally dies I will strip all the parts I upgraded it with to tune-up the cheapest laptop I will find at BestBuy, and I believe it will be a better tool. I will never buy anything else from System76 ever again!

---

### Post by sonsofblades on 2018-04-24
I've personally have been looking at System76 myself, have been rather impressed with their options over what Dell offers for Linux. 

'Course, I'm coming from an Asus G73JH that is almost 8 years old, so almost anything would be an upgrade at this point. :p

---

### Post by monkeybrain20122 on 2018-04-24
I think they use to give support on this thread, but apparently not anymore.

---

### Post by Cowchip7 on 2018-05-02
> **monkeybrain20122 said:**
> I think they use to give support on this thread, but apparently not anymore.

Yeah. That was one of the things I liked about System76. If someone had a simple questions, he/she would post it in the forum and the community and System76 would respond. If the issue could not be resolved, System76 would request a private conversation. Given System76's lack of involvement in this forum nowadays would make me hesitant to buy another one.

---

### Post by pauljw on 2018-05-05
> **Cowchip7 said:**
> Yeah. That was one of the things I liked about System76. If someone had a simple questions, he/she would post it in the forum and the community and System76 would respond. If the issue could not be resolved, System76 would request a private conversation. Given System76's lack of involvement in this forum nowadays would make me hesitant to buy another one.

That's ridiculous, System76 provides lifetime support and they are very responsive, even providing live chat on their website.  They're a small shop doing great things for the community.  Support them or lose them.

---

### Post by bodhin2 on 2018-06-10
well i had terrible tech help when i bought one when they first started.  the guy did not know very much.  more than i do but not enough to fix issues. it was nice looking at that time but since then - eh...

I like my X thinkpads and looking at a 13" asus that is lighter and nicer looking than the thinkpads.  but i have run many thinkpads and linux over the years and i generally do not have too many issues if using a decent distro.

---

### Post by Frogs Hair on 2018-06-10
They have their own operating system now and that maybe why they don't visit here.

[https://system76.com/pop](https://system76.com/pop)

---

### Post by 1clue on 2018-06-10
I haven't bought anything from system76 yet, but have done a few days of research. Not really in the market for laptops and haven't done the research for maybe 4 months, but in looking for a desktop I used the configurator and then tried to find a build-it-yourself parts list which most closely matched what the configurator had, as far as I could tell.

They seem to be a little more expensive than what you could find and build yourself. Which means they have more than average markup. Normally there's no way you could afford to build one for the same price you can buy for, but there are additional considerations. One is that with most off-the-shelf or even configurator-built stuff, you're never really sure what brand or quality of component you'll get, unless they specifically state the make and model of device on the configuration page. So speaking with a few decades of experience the times when you get a random pc or laptop where everything actually works on Linux and is of high quality is pretty rare. Just getting a high quality box with no junk hardware on it (easy enough if you spend money) but also everything works well on Linux is probably worth the markup.

---

### Post by skade88 on 2018-06-16
My 4 year old Bonobo Extreme Laptop is still running great for me. Their support is amazing too.

---

### Post by slava84 on 2018-08-06
I have Kudu and I have to admit that it's really BAD for the money they asked for it. I bought it customized - upgraded memory, SSD and processor. It works, but for the money I spent on it I could've purchased a much better and powerful computer. I was new to linux at this time and bought it to avoid any installation-related problems I anticipated for Ubuntu - just needed a Linux based machine to run smoothly right from the box. As it turned out - nos such problems even exist,  and many forum thread I read claiming System 76 helps to avoid any such complications and does something extraordinary and useful were likely made by the company employees themselves. I installed Ubuntu on Asus laptops afterwards and it works no problem at all. But back to the laptop itself. From the practical standpoint - the computer is Very heavy (I knew it would be), but horrible touch pad - computer is completely unusable without mouse attached. It is unbelievably noisy  - I can not use it for any public presentations for this reason. When the cooling fan starts - I can barely hear myself and people in the room start to laugh. The charger - it's a huge heavy brick. The battery life was not as they advertised - right from the box I could squeeze an hour and a half, and after several full discharge-charge cycles it didn't improve much. It consumes battery power like crazy even at the lowest screen setting, keyboard lights off, and only basic processor load.  Basically - system76 Kudu can not operate without being plugged-in permanently.  I keep this laptop at home now and it has almost no use these days - mostly used as a side for my desktop. Occasionally run quick computations. I really have to give credit to System 76 for the great marketing strategy. Their laptops would be awesome 10-15 years ago, but to sell it these days requires some good advertisement and marketing efforts. Their website is really great for it.

---

### Post by coffeecat on 2019-03-08
Thread closed for three reasons:

[list=1][*]This is an over 3-year old thread in which the OP has not logged in since about a week after starting the thread.
[*]This is a support, not discussion, area as [this sticky makes clear](https://ubuntuforums.org/showthread.php?t=2178557)
[*]The thread is beginning to attract marginally trollish posts and needs to be put to bed.[/list]

---

