---
title: "Windows audio programs other than Reaper/Ardour VST support?"
date: 2010-05-01
forum: Ubuntu Studio
---

### Post by hxcobd on 2010-05-01
After a long period of time now having my audio work split between linux and Windows (linux primarily for composition in Renoise, Windows for any/all editing/recording), I'm at the point where I almost want to venture and delete my Windows partition entirely.

I was driven to this point after downloading raw tracks from a friend's band yesterday and obtaining a myriad of spyware in the process, despite not doing anything even remotely questionable on my computer.

I know there are a handful of Windows audio programs that legitimately work very well in linux; obviously Reaper is a prime example.

Are there any others known to work extremely well? I've noticed Melodyne and Samplitude both look to work quite well in Ubuntu. Adobe Audition apparently doesn't, though, which sucks.

As far as Ardour goes, does it have pretty decent support for Windows VSTs? I know it can be built with VST support... Is it an endeavor worth pursuing?

---

### Post by sgx on 2010-05-01
Hi, I briefly tested MU Lab, loaded a few windows vsts, and play,
record, and editing seemed to work in a brief test. The gui is nothing like Reaper, it has a free version here:

[http://www.mutools.com/downloads.html](http://www.mutools.com/downloads.html)

Cantabile also works in many cases, a free version is here:

[http://www.cantabilesoftware.com/lite/](http://www.cantabilesoftware.com/lite/)

To be sure, I just tested the latest version with drumcore and synth1,
wine 1.43, wineasio 7.3

Windows Energy XT2 also works, and a free version is on the
Computer Music Magazine dvd each month.

(If you don't have one,
the dvd contains a dozen great plugins, and dozens more that others
think are great, that I have not tried, plus a nice multi-timbral
rompler, with different sample sets for it each month.
Each issue has special giveaway apps, (some are excellent lite, or end-of-life versions, very useful and purposely tempting) and some demo apps, and
a library of common freeware for convenience. Its an excellent bargain for $17. I buy 3 or 4 issues a year, depending on the giveaways, samples offered, and additions to the monthly plugin collection.)

There is a thread here of folks using FLS 9, almost ready, I'd
guess from reading the posts, stable use is still about 6 linux months
away. Earth months are different  ;) FLS 7 is rumoured to work, I can't confirm that myself.

I also tested Podium, that was on a CMM cover dvd recently, and after some serious dear-in-the-headlights moments and a google or three, I figured out
where and how to load plugins, but it was late, and I have not tested more.
Many windows people like it.

A windows style all-around DAW is not in the cards for ardour in the near future, the author is focused on excellent audio production, so midi and vst support will be limited, unless the plans change, or a crew shows up that can add such support at the high quality that ardour maintains.

Reaper is the best choice for me, but you may find needed features
or workflow in the others I mentioned. Cantabile will get more use this week, the new version, and the new wine seems to play well together,
I have used the older cantabilelite1.2 version  many times.

Cheers

---

### Post by hxcobd on 2010-05-02
Great post, thanks a lot, sgx.

Definitely looks like a lot of the smaller-sized DAWs will work fairly well; Reaper, Podium, EnergyXT (I actually own licenses for the latter 2, also)

I'm more concerned with being able to:

1.) Use my mixing/mastering VSTs (limiters, EQ, compressors)

2.) Use my really large-sized VSTis (Omnisphere, Superior Drummer 2.0)

3.) Most of all, being able to use a host with extensive editing features, like a Melodyne, Audition, Sound Forge, etc.

---

### Post by AutoStatic on 2010-05-02
Hello hxcobd, do you really want to run approx. $2500,- worth of software in an emulated environment? Or is Wine really better than Windows itself at the moment? Just a personal reflection, I'd find it weird if someone wants to fit a Volkswagen engine into a Toyota.

---

### Post by hxcobd on 2010-05-02
Yeah, that's the million-dollar question, Auto.

I mean, I can make adjustments to my workflow without a problem, especially if the majority of my software is supported fairly well under WINE.

Other than my audio software, most of which seems to run pretty well in WINE according to WineHQ.com, I have absolutely no need for Windows at all. I wouldn't even HAVE a Windows partition if it weren't for audio stuff...

---

### Post by sgx on 2010-05-02
> **hxcobd said:**
> Yeah, that's the million-dollar question, Auto.

I mean, I can make adjustments to my workflow without a problem, especially if the majority of my software is supported fairly well under WINE.

Other than my audio software, most of which seems to run pretty well in WINE according to WineHQ.com, I have absolutely no need for Windows at all. I wouldn't even HAVE a Windows partition if it weren't for audio stuff...
I have ezdrummer, Amplitube2 Live, the Wusikstation, a few Native Instruments freebies and their demos, they all install, authorize, and work as expected. The ntfs-3g app/config has never failed to read/write from an xp partition that holds a few apps I use that don't install in linux. 
I link the xp-side  15 gig Wusikstation folder to the wine vst folder to save disk space. You'll have to test things one by one. A few will work in one host, but not another. A few require the exact path

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins

a few require .fxb outside the plugins folder, but lots of smooth sailing. Cheers 
You'll want a separate /home partition, to ease reinstalls, without reconfiguring the farm, and set up synaptic to save installed files in its cache, to safely hoard and burn to media what may be needed in a dark night in the future.

---

### Post by sgx on 2010-05-02
> **AutoStatic said:**
> Hello hxcobd, do you really want to run approx. $2500,- worth of software in an emulated environment? Or is Wine really better than Windows itself at the moment? Just a personal reflection, I'd find it weird if someone wants to fit a Volkswagen engine into a Toyota.
You'll find lots more windows users willing to learn and use linux for most, if not all of their computing. I have a small high-mileage travel
car, and a big suv for work, 6 passenger excursions, firewood cutting trips, things not possible in the little car. 

One way wine is much better than windows, comes when reinstalling the OS, 
just rename .wine to wineold temporarily, install the chosen linux,
without formatting /home, run the current version of wine, then drag your Steinberg/VstPlugins folder to the new .wine folder. My Reaper folder snoozes thru the whole experience, and wakes up to happily join the party!

Such a reinstall on xp can be an all-day or all-weekend nightmare, that windows-only musicians universally dread. This is eased a bit by modern 'back-up image' apps, but even they have a price and a learning curve.

All in all, musicians have never had it so good :D

---

### Post by hxcobd on 2010-05-03
Sgx, as far as actual performance/speed goes, do the WINE-emulated programs/plugins tend to run pretty quickly?

My system is somewhat underpowered as it is (Dell Adamo; 1.2 ghz Core2Duo, 2 gigs RAM, 120 gig SSD), though it does handle Omnisphere and all the NI plugins in Windows without any problems at all.

I've been seeing tutorials on youtube about people using VSTHOST to actually host their plugins, rather than hosting them directly in a DAW. If I did it this way, would I be able to route the plugins using JACK, or would I still need some WINE-enabled audio system or something?

What I mean is, could I host/open the plugins using the WINE-d VSTHOST and actually route/sequence them in a linux DAW like QTractor or EnergyXT? Or would the DAW have to be a WINE-d Windows version as well?

I haven't used WINE in years, if you couldn't tell, and back when I used it, I could never coax audio into working at all.

---

### Post by sgx on 2010-05-03
> **hxcobd said:**
> Sgx, as far as actual performance/speed goes, do the WINE-emulated programs/plugins tend to run pretty quickly?

My system is somewhat underpowered as it is (Dell Adamo; 1.2 ghz Core2Duo, 2 gigs RAM, 120 gig SSD), though it does handle Omnisphere and all the NI plugins in Windows without any problems at all.

I've been seeing tutorials on youtube about people using VSTHOST to actually host their plugins, rather than hosting them directly in a DAW. If I did it this way, would I be able to route the plugins using JACK, or would I still need some WINE-enabled audio system or something?

What I mean is, could I host/open the plugins using the WINE-d VSTHOST and actually route/sequence them in a linux DAW like QTractor or EnergyXT? Or would the DAW have to be a WINE-d Windows version as well?

I haven't used WINE in years, if you couldn't tell, and back when I used it, I could never coax audio into working at all.

Use Synaptic to install libwine, wine, and wineasio, then I use

winecfg   to open the wine configure panel, and choose alsa for sound
and nothing else. Then run the command

regsvr32 wineasio.dll     you'll see a confirmation of success.

wine reaper34-install.exe     to install it

After that, from what I see, wine just sits in the corner. I start jackd with qjackctl, a gui patchbay for linux, I have reaper installed in

/home/user/Reaper    and start it with

wine reaper/reaper.exe 

Once it is configured for your midi, input/output, and asio driver (wineasio in our case) it will connect automatically when started, assuming you start jackd first. If something zombifies jackd, you can restart the connection by reselecting the wineasio driver in the daw preferences. At that point, using qjackctl (or other patchbays) you can connect a linux drum machine, synthesizers, multi-fx, in the ways you choose. Reaper output is just just another 'linux instrument' to record along
with the rest. Timemachine is a great little recorder, connect everything to it, and press the button.

As for speed, I can't say I've noticed a difference between an RT-kernel
linux and xp, but I use a mixture of linux apps and vsts that is usually between 4 and 10 instruments/fx. There is someone in the Reaper forum who
says his projects often involve 40 or more tracks, and that his linux is
faster than xp. If you use Omnisphere OK, there won't be anything in linux demanding that much cpu. 

It would be good to test Omnisphere ahead of time,
there is a 'wubi' installer to install ubuntu inside the xp partition, when you reboot, you'll choose between xp and ubuntu. You can use ntfs-3g support from linux, it allows normal read/write on the xp partition, from linux filemanagers, (nautilus, konqueror, pcmanfm, dolphin) which can make a symbolic link from your xp vst folder, to the one in .wine. Reaper can then find it when scanning the selected folders. For Native Instruments apps, there were 4 or five xp locations with folders to drag across to their wine equivalents, copies instead of links, in this case, but they were happy when they got there. I just installed the Reaktor 5 demo for the first time tonite, and the Steampipe ensemble is great. I downloaded some others to test later.


Here is a wubi install video from the many at youtube:

[http://www.youtube.com/watch?v=zsJL9tPrzGo&feature=related](http://www.youtube.com/watch?v=zsJL9tPrzGo&feature=related)

[http://wubi-installer.org/](http://wubi-installer.org/)

Cheers

---

### Post by hxcobd on 2010-05-03
Once again, great post/tips, sgx.

Good idea to install Ubuntu via WIBU and see how my plugins handle being run via WINE. I'm pretty confident about 90% of them should run fine, according to my own notions and WineHQ ratings. Omnisphere and Superior Drummer are the only 2 I'm not sure about, so those will definitely be ones I try.

That's great to hear that even the Windows programs/plugins are just viewed as other sources of JACK audio; I'd really like to minimize the impact of Windows software on my system, but for these few VSTs, it's just unavoidable. 

I'll definitely be trying the WIBU technique and installing a bunch of stuff to see how it goes.

---

