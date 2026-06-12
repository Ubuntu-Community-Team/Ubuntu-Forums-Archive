---
title: "You have choice - if you have the right hardware!"
date: 2013-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by DisappearingOak on 2013-04-10
I'm on AMD 3.4ghz quad core with 4GB ram and IGP radeon 4250 (512mb shared). I first tried Ubuntu 11.10 back in early 2012, but gave up because my webcam wouldn't work, system would lag, mobile broadband would only work when using third party scripts, and Unity was basically featureless at the time. I was forced to use the open drivers because Catalyst has horrible 2d AND 3d performance on this chip. The open drivers are adequate but there are bugs with the desktop environemnts. I tried afterwards 12.04 which has a very pretty colourful interface, but again horrible performance with the laggy dash and laggy effects. To get it to be usable I had to use tweaks to disable features like blur, without which the dash text is unreadable, and had to disable the laggy compiz effects. 

I tried E17 but it has the worst application support out of all desktops. Chrome won't work without system borders, basically rendering cutomizability function useless. Other apps have similar problems. KDE has a horribly ugly look and feel but I tried using it, but it has choppy opengl performance due to redraw bug which has been reported. It's not that my hardware can't handle it because every desktop effect runs fast if I switch on the FPS counter. The problem is to make any desktop usable, I have to tweak and disable half the features because of various bugs. Gnome Shell had great smooth performance in 3.2, but later versions were laggy. 

I know that I should have chosen properly supported hardware from the beginning but some of these bugs seem to crop up afterwards. I've read reports of some hardware working beautifully when the older versions were released, and then problems when new versions are released. The bugs are OK but why does it take so long to fix them? Is the video chip I'm on very uncommon? I had bug reports from many months but no word on them at all. KDE is still unusable with desktop effects, so to use any DE, I have to disable features because of bugs which aren't fixed for so long. Now that gnome 3.8.1 is out, it has acceptable performance again and I like using it now, thankfully, because I don't like windows.

What are your hardware horror stories?

---

### Post by andrew.46 on 2013-04-10
> **DisappearingOak said:**
> What are your hardware horror stories?

None really :). I run an Ubuntu VM on a *very* modern desktop that I built myself and have had no trouble. My backup laptop (a bog standard Latitude D520) also used to run older versions of Ubuntu with no trouble at all. Sounds like you have been very unlucky!

---

### Post by Algus on 2013-04-10
I don't have any really bad hardware horror stories.  I never could get video to play right on my old Dell notebook though.  I had to fiddle with gstreamer and invert all the colors.  This had the effect of making the image display properly if I was watching a movie but if I took a picture or used Skype or something, then my video would be inverted.   

I try to check out the hardware in a machine before I buy it now because I care more about knowing that my computer is going to have Linux support than I do about the performance or value of the parts.  I am willing to pay a little extra if I have to in order to know the computer is going to work for me.

---

### Post by evilsoup on 2013-04-10
I've always been pretty lucky with hardware. I had some serious problems setting up a printer once, but that was in 2008. Also, one laptop's brightness controls didn't work properly.

---

### Post by mastablasta on 2013-04-11
> **DisappearingOak said:**
> I know that I should have chosen properly supported hardware from the beginning but some of these bugs seem to crop up afterwards. 


it's the problem i've been noticing as well. furthermore bugs that were once already solved and patched reappear.

10.04 - sound not working propperly
10.10 installed - sound working, after a few updates sound no longer works normally, sound chip is often recognised wrongly.
12.04 - fresh install sound working, Skype cam pic upside down
12.04 month later - sound not working, suspend not working, hibernate not working
12.04 almost 1 year later - trouble with update - "generic" logitech mouse not working. had to replace the interface to make it work again. keyboard recognised wrongly - had to reconfigure the whole thing.

these sort of things shouldn't happen. if something worked in 10.10 first install it should continue to work. the patches shouldn't create new bugs. furthermore if these bugs were solved by new release updates again should not reintroduce them.

---

### Post by mips on 2013-04-11
I don't have horror stories.

Laptop - Everything works out of the box except for the onboard softmodem but we all know those don't work in Linux and the last time I used dialup was in 2004 I think.
Desktop - Everything works out of the box
Printer - Multifunction HP works fine via the LAN or USB.

Before I got into linux I purchased a webcam which is now old and it does not work but apparently there is a way to make it work but I can't be bothered.
I'll NEVER buy a ATI/AMD GPU for use in linux, NEVER. It's just looking for trouble.

---

### Post by Jonathan Andrew Upton on 2013-04-12
I run Ubuntu successfully on two devices: The Toshiba NB100 12-A netbook and the Dell Optiplex GX-620 desktop tower; however, I tried to run Ubuntu on my Toshiba Satellite C670 notebook computer but it is really buggy. On the notebook if I run Ubuntu through Wubi it will not connect to the keyboard and recently I partitioned the drive but it will not switch off - only reboot ALL THE TIME. Why is Ubuntu (or most Debian Linux distros) not successful with Toshiba?

---

### Post by monkeybrain2012 on 2013-04-13
I have not had any problem with hardware at all, I have different versions of Ubuntu installed in an external hard drive and boot it off computers of different specs and never experienced any problem except once at work it froze when skype started, turn out there was some incompability with the usb webcam this guy gave me, borrowed another one from another guy in the same room and everything worked. I have also instaledl Ubuntu on a few laptops, from about 7-8 year old ones to the newest one which is only one year old and all work great (For 12.10 wifi doesn't work on an old hp netbook with a broadcom wifi card, but 12.04 worked great, maybe the new kernel doesn't support the card anymore?). I haven't tried anything with "secure" (restricted) boot yet. 

Got an old Epson scanner-printer, worked out of the box since 11.04 (need to download drivers for 10.04 and 10.10, but they are .deb packages so installation was a piece of cake) Tested on hp printers at work, they work out of the box (but Win7 doesn't work!)

---

### Post by forrestcupp on 2013-04-13
I realized this when I first started messing with Linux a long time ago. So since then, I've always intentionally bought computers and peripherals that are known to work well with Linux. I don't really think it's unreasonable. It's the same with MacOS X. It runs on supported hardware, and if you try to make a Hackintosh, you expect it not to work well with just any hardware.

---

### Post by Erik1984 on 2013-04-13
> **andrew.46 said:**
> None really :). I run an Ubuntu VM on a *very* modern desktop that I built myself and have had no trouble. My backup laptop (a bog standard Latitude D520) also used to run older versions of Ubuntu with no trouble at all. Sounds like you have been very unlucky!

Doesn't sound like a fair comparison. With a VM your host OS takes care of all the annoying hardware stuff. Or is your host OS also Linux?

---

### Post by Version Dependency on 2013-04-13
Over the years, I've learned to stick with buying components from companies with good Linux support (HP printers and accesories, Nvidia GPUs)  and stay away from those with bad or non-existent support for Linux (AMD/ATI, Canon, Lexmark, etc).

---

### Post by JayKay3OOO on 2013-04-13
Most of my early problems were down to my own incompetence because I had no idea what I was doing and would give up easily.

Although I the first board I picked up for this current machine was doa. I told the website, they came with a courier the next day and picked it up for free and once they tested it and confirmed it was broken I got to choose another. Radion graphics for 1080p video had been a problem, but graphics drivers seem better. After the doa it has survived being knocked off my desk while on by a drunk house m8. It stayed on even though the case was smashed. No data loss. Still using the same drives two years later with a new case of course. I then dropped the current setup on the sidewalk in the rain and dark moving it to the car and apart from scuffs and small bends in the case the system is fine even with a delicate zalman cooler that tells you to be really, really careful when moving the box as the weight could tear it off the cpu. It's fine though. My system is the same as the OP except with a zalman cooler and a better radeon graphics card.

I've run Linux from flash drives on old dell laptops, single core amd chips, pentiums, amd fusion, atoms all without problems. Slowness is normally because the mechanical hard drives have been on their last legs.

---

### Post by lykwydchykyn on 2013-04-16
I first installed Linux ten years ago.  Back then you were lucky to find a video card that X would even talk to.  I had a stack of scavenged video, sound, and network cards I kept around that had at least minimal functionality in Linux just in case I ran into some hardware that was impossibly incompatible.  I even ran across one video card that caused a kernel panic just by being in the machine.

If you have issues with newer hardware you might want to try a newer kernel from the kernel PPA.  Hardware drivers live in the kernel, and only a very few get backported to the kernel shipped with an Ubuntu release when a new kernel comes out.

For video drivers, there's also the xorg-edgers PPA that  pushes out newer versions of Xorg and video drivers.

---

### Post by mastablasta on 2013-04-17
> **Version Dependency said:**
>  bad or non-existent support for Linux (AMD/ATI, Canon, Lexmark, etc).

i though linux based steam box is going to have AMD card. i could be wrong though. 
Also isn't AMD one of the main backers of linux?

---

### Post by slickymaster on 2013-04-17
Until now I can also consider myself lucky. Beyond a higher battery consumption, up to now never came across with any particular issues on my Toshiba Tecra A7.

> **mastablasta said:**
> these sort of things shouldn't happen. if something worked in 10.10 first install it should continue to work. the patches shouldn't create new bugs. furthermore if these bugs were solved by new release updates again should not reintroduce them.
Agree. I think that's something developers should regard as a priority to be solved.

> **mips said:**
> I'll NEVER buy a ATI/AMD GPU for use in linux, NEVER. It's just looking for trouble.
+1

---

