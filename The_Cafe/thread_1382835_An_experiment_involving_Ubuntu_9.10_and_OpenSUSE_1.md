---
title: "An experiment involving Ubuntu 9.10 and OpenSUSE 11.2"
date: 2010-01-16
forum: The Cafe
---

### Post by blueshiftoverwatch on 2010-01-16
A few weeks ago I tried OpenSUSE 11.2 (with Gnome) using almost the same hardware configuration I have now. Two 1TB Samsung Spinpoint F3's raided with fake RAID0, 8GB of Kingston DDR3 RAM clocked at 1333, an Nvidia GTX 260 GPU, and a Phenom II x4 965 CPU.

The only difference is that today I'm using Ubuntu 9.10, I overclocked my CPU to 3.5GHz (100MHz higher than stock), and RAM to 1600 speed. Which is what the RAM is actually supposed to be running at. The RAM is 2000 speed and my motherboard supports up to 1600 before you need to overclock to get additional speed gains. For some reason it was underclocked to 1333 before by default.

Both were using the Ext4 file system. Both read Divx encoded AVI files around 350MB in size with a default resolution of about 650x350 off of an Ext4 partition separate from the my main OS partition using VLC Media Player.

Now that we have that out of the way. Under OpenSUSE I wanted to see how many videos I could have open at once before my computer would slow down to a crawl. I managed to get about 12 of them playing at once in VLC before there was no more room left on my 22" monitor. I had to reduce the size of the videos by about 50% to even get that many to fit onto the screen. And there was still enough CPU and RAM left over that I could have been doing other things while all of those videos were playing.

I just tried to do the exact same thing on Ubuntu 9.10 and my system froze up after opening up the third video. Not froze up as in requiring a hard restart. But I had to ctrl+f7 and close out of the videos with the 'ps -e' command because the GUI would not respond. Which is the exact same thing that happened when I tried this experiment with 1 non-raided HD on Ubuntu 9.10 and only 4GB of RAM, before I upgraded.

What exactly is the reason for this? The 2 Linux based OS's on almost exactly the same hardware should be able to perform equally as well. If anything, Ubuntu should have performed better because I had increased the speed of my CPU and RAM since trying this experiment out with OpenSUSE. Was there a flaw in my experiment? Is OpenSUSE just coded so much better than Ubuntu? What's the deal?

---

### Post by samh785 on 2010-01-16
I'm not sure why you're having this problem. I just filled my screen with videos on vlc and noticed no lag at all. Could it possibly be something that you have edited in your ubuntu config that is causing this problem?

---

### Post by m4tic on 2010-01-16
On a machine with 64mb SiS intergrated graphics and 512mb RAM i'm getting 9 movies i ripped legally to run till the screen fills. my ram is maxed out tho but there are no lags

---

### Post by buddyd16 on 2010-01-16
> **blueshiftoverwatch said:**
> ... If anything, Ubuntu should have performed better because I had increased the speed of my CPU and RAM since trying this experiment out with OpenSUSE. ...

There is your answer right there. Your system may currently not be stable at the overclock settings you are running.

Also your experiment is slightly flawed since you changed the base configuration of your system between the openSUSE and Ubuntu installs. I'd suggest redoing your experiment with both operating systems running under the same default or overclocked hardware settings to get a closer representation of the difference in system performance between the two operating systems.

---

### Post by blueshiftoverwatch on 2010-01-17
> **buddyd16 said:**
> There is your answer right there. Your system may currently not be stable at the overclock settings you are running.
I just set my overclock settings back to the defaults and the test performs exactly the same. Two videos will run, but when the third is launched the GUI becomes unresponsive.

---

### Post by konqueror7 on 2010-01-17
> **blueshiftoverwatch said:**
> I just set my overclock settings back to the defaults and the test performs exactly the same. Two videos will run, but when the third is launched the GUI becomes unresponsive.

did you too, install the exact same version of the packages?

---

### Post by blueshiftoverwatch on 2010-01-17
> **konqueror7 said:**
> did you too, install the exact same version of the packages?
Are you referring to VLC Media Player?

---

### Post by MasterNetra on 2010-01-17
I have one GB of ram and a Intel Core 2 Duo and 12 vids run fine on my Ubuntu System. Accidentally one time opened up all of the episodes of X-Men Evolution. If I remember correctly about 12-15 opened up in separate player windows and despite it trying to open the rest it seemed as though, it couldn't until I closed the ones that where open. It lagged quite a bit..but then again it was trying to open 52 windows lol.

---

### Post by konqueror7 on 2010-01-18
> **blueshiftoverwatch said:**
> Are you referring to VLC Media Player?

well, not specifically, i meant as a whole...because as you've said, they have both the same hardware configuration, so, it could be a software problem...just my thoughts about it...as i see it, they are both linux, but both different systems...

---

### Post by Skripka on 2010-01-18
> **buddyd16 said:**
> There is your answer right there. Your system may currently not be stable at the overclock settings you are running.


Nah, 100mHz OC on a 3.4gHz CPU is nothing.

---

### Post by juancarlospaco on 2010-01-18
VLC got some problems starting/finishing a video playback, i dont know why, 
but i see the same on many PC, kinda resource hog for a moment.

---

### Post by XubuRoxMySox on 2010-01-18
I hear almost nothing but praise for OpenSUSE 11.2. I've ordered a CD to try it out. It looks as as easy to use as any Linux distro in the history of ever. Can't wait to try it out, even though I really like what I'm already using (Debian at home, Crunchbang on a laptop, Xubuntu at work).

-Robin

---

### Post by buddyd16 on 2010-01-18
> **Skripka said:**
> Nah, 100mHz OC on a 3.4gHz CPU is nothing.

True but he/she also tweaked his/her ram settings and without knowing any of the other information as far voltages and ram timing settings its a logical assumption that a system that had no issues before the overclock and issues after may not have been completely stable at the new bios settings.

OP did you also reset your ram to the default configuration before running the test again? Double check that you have the correct bios settings for your specific brand of ram in your motherboard ie. timings, voltage, and speed

I would also suggest running memtest to see if there are any errors.

---

### Post by blueshiftoverwatch on 2010-01-18
> **dixiedancer said:**
> I hear almost nothing but praise for OpenSUSE 11.2.
I would probably be using OpenSUSE rather than Ubuntu if it weren't for my preference for Debian package managment. From my very limited experience with RPM distros, Debian/apt-get seems very organized and user friendly while RPM/Yum seems like complete chaos and plagued with dependency hell issues. I couldn't even get my downloaded copy of Virtualbox up and running. Although, to be fair I didn't give it much of a chance. But I don't want this to turn into an RPM vs Deb thread.
> **buddyd16 said:**
> True but he/she also tweaked his/her ram settings and without knowing any of the other information as far voltages and ram timing settings its a logical assumption that a system that had no issues before the overclock and issues after may not have been completely stable at the new bios settings.
I just went into the BIOS and changed the FSB/DRAM ratio up to the maximum it would go upto. Which increased speed from 1333 to 1600. Why, is that not the proper way to do it? I assumed that any voltage concerns would be taken care of automatically by doing that.

Actually, I wouldn't really even call what I did overclocking. The RAM I bought is rated at 2000 speed, it was running at 1333 by default, and I increased it to 1600. So as far as the actual RAM is concerned, it's actually underclocked even at 1600. Although, the motherboard is advertised as one that is good for overclocking the RAM.
> **buddyd16 said:**
> OP did you also reset your ram to the default configuration before running the test again? Double check that you have the correct bios settings for your specific brand of ram in your motherboard ie. timings, voltage, and speed
Yes, I changed the FSB/DRAM ratio back to the default setting, which is called "auto".
> **buddyd16 said:**
> I would also suggest running memtest to see if there are any errors.
I ran a memtest when I got my original 4GB of RAM and after getting my additional 4GB a few weeks ago. All was fine.

---

### Post by toupeiro on 2010-01-18
I'm an old school suse user, years before Novell gobbled them up, and have been eyeballing it hard for consideration of moving back to it.  Debians package management system was the first thing that sucked me in to ubuntu.  Its truly awesome, I will admit.  Redhats and Suse's do not compare IMO.  My problems, however, have grown way beyond package management.  Ubuntu is still a great OS.  I'm considering a change for ethical reasons with its developers and future positioning more than I am any reason in the performance department.

That being said, you might think you're doing an apples to apples comparison, when really you're comparing a fiji apple to a granny smith.  They both taste great, but they come from different trees and appeal to different tastes.  When you compare ubuntu and suse, you're comparing version differences, dependency differences, kernel rev differences and potentially many more things.  Let me tell you, I've put ridiculous loads from a workstation standpoint on ubuntu and it keeps right up with the demands I have for it.  Suse, at the same time, has gotten quite the load put on it as well and its a true workhorse OS, ridiculously stable.  

I think the bottom line is, you have introduced many variables in your test, including doing an install, it sounds like, while overclocked, which that in itself could have compromised your results.  Overclocking is something you should do with a baseline already, not to create a baseline.  I would consider:
1) starting over
2) gather some statistical information about the two environments you are about (patched up to date? PPA's? codecs used?) in the software department beyond "suse" and "ubuntu" so we can be a little more prepared to help you identify where some of the issues you found may be coming from.

Cheers!
-T.

---

### Post by blueshiftoverwatch on 2010-01-18
> **toupeiro said:**
> I think the bottom line is, you have introduced many variables in your test, including doing an install, it sounds like, while overclocked, which that in itself could have compromised your results.  Overclocking is something you should do with a baseline already, not to create a baseline.
As I've said multiple times. I tried the tests out under the following scenarios:
1. With OpenSUSE - all components clocked **at** default speeds.
2. With Ubuntu - CPU and RAM clocked **above** default speeds.
3. With Ubuntu - CPU and RAM clocked **at** default speeds.

#1 and #3 are under the same hardware scenarios and yet Ubuntu performed much worse than OpenSUSE regardless of whether the hardware it was running at was clocked at or above default speeds.

---

### Post by toupeiro on 2010-01-18
> **blueshiftoverwatch said:**
> As I've said multiple times. I tried the tests out under the following scenarios:
1. With OpenSUSE - all components clocked **at** default speeds.
2. With Ubuntu - CPU and RAM clocked **above** default speeds.
3. With Ubuntu - CPU and RAM clocked **at** default speeds.

#1 and #3 are under the same hardware scenarios and yet Ubuntu performed much worse than OpenSUSE regardless of whether the hardware it was running at was clocked at or above default speeds.

And as you've been told multiple times, this is not the only caveat in your tests.  If you want help, great!  Suggestions have been provided.  If you just want to rant, well I guess theres plenty of that going on here too, just let the ones who genuinely want to help know that in advance.

---

### Post by buddyd16 on 2010-01-18
Doble check the ram timings and voltage settings in your bios against the manufacturers specs for your ram. I am by no means an expert at this kind of thing but have been told on a few occasions, not on these forums but on those of my motherboard manufacturer, that not having the correct timings and the correct voltage set per the ram manufacturers spec can sometimes result in errors.

Just out of curiosity which motherboard do you have?

---

### Post by blueshiftoverwatch on 2010-01-18
Under OpenSUSE I downloaded VLC from their website. Since this was Christmas Day and VLC 1.0.4 was released 39 days ago I must have been using version 1.0.4 on OpenSUSE.

On my current Ubuntu installation I appear to be using version 1.0.2. I tried installing VLC 1.0.4 from source. But I kept running into problem after problem with dependencies not being met, the error messages not being specific enough as to what packages I actually needed to fetch, and said packages not being in the Ubuntu repos. Apparently VLC's website won't provide Ubuntu with a binary package even though the Ubuntu repos have version 1.0.2 and we're up to 1.0.4 now. Even though they do provide the newest versions in binary format for Windows and OSX.

---

