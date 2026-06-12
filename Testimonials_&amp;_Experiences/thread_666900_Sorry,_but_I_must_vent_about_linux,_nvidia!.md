---
title: "Sorry, but I must vent about linux, nvidia!"
date: 2008-01-13
forum: Testimonials &amp; Experiences
---

### Post by beczka2005 on 2008-01-13
I love Linux! I have been using it for 8 years now (sparc-proprietary , debian, redhat, gentoo, and now Ubuntu).

BUT I have to say that 99% of my headache with linux has been BECAUSE of proprietary drivers such as nvidia!

A couple of years ago I said to myself "Don't complain about it, step up and do something to fix it." So I spent a good month filing bug reports with nvidia to develop the ultimate driver as far as I am concerned. The 8776 driver did it all for me! Fast opengl, suspend, exceptional uptime. I used that driver for a year refusing to upgrade.

Now I'm with ubuntu. Don't really have any choice (I tried) but using the latest nvidia driver available. This latest nvidia driver is BAD. Crashes every day, can't suspend, can't hibernate. It has gotten so bad that I am now using the nv driver which is VERY slow but at least my system is usable and rock-solid.

Sorry for the rant, but how am I supposed to convince others to switch over to Linux with these kind of problems?! It is just amazing to me that *ONE* driver can ruin the experience of linux which is a conglomerate of so much effort from so many people.

---

### Post by bkelly on 2008-01-13
I am not quite a the point of ranting, but am having problems.  I purchased my machine preloaded from Eracks.  I just asked for dual monitor and they picked all the hardware.  The video card is marked ASUS and has nvidia GeForce 7300 SE chip set.  It was mostly working from the vendor, but the screen kept scrolling. (When the cursor moved to the edge of the screen, the entire screen and its contents would slide over in the other direction.  Some of the screen is always hidden indicating the size of the image is greater than the size of the physical display device.)

After trying to fix that for two days, the video won't set to better than 800 x 600 and the two monitors duplicate rather than extend.  I have followed advice per another thread in this section but so far to no avail.  

To be fair, Eracks has not yet had a chance to respond and I should have saved some files.  Problem is, I did not and do not yet know what files I should save.

So yes, Linux is quite fragile in terms of consistent video displays.  That is the single most visible and first aspect of a system when evaluating it.

---

### Post by Melcar on 2008-01-13
Yeah.  Proprietary display driver (either from nvidia or ATI) tend to suck.  Open source drivers end up being much better in terms of stability and sometimes feature implementation and support, but unfortunately, if you want to run the current generation hardware or have top performance out of your card, proprietary seems the only way to go.

---

### Post by Sef on 2008-01-13
Moved to Testimonials and Experiences.

---

### Post by wolfen69 on 2008-01-14
i solved the problem by not using the nvidia driver. if i want 3D gaming, i just boot to xp.

---

### Post by xpod on 2008-01-14
i`ve not been using Linux(Pc`s even) 2 years yet but i must have been one of the lucky ones with Nvidia and the propriety drivers.
Mainly used *buntu in that time and had a few different (older though)Nvidia cards along the way and thankfully never had a real problem,bar my TVout on an FX5500 i suppose.
Currently using the onboard Geforce 7 series on a new/er motherboard and even thats been fine so far,both in 32Bit & 64bit versions of Xubuntu.

I`ve aslo had a couple of ATI cards as well as a few onboard S3 savage type cards on various pc`s along the way and everything has usually just worked,out the box so to speak,with only the newer(relatively speaking) cards requiring any restricted drivers managers and the like.

---

### Post by Whiffle on 2008-01-14
Maybe you should try a different distro then.  I've been using linux for 6 years now and have had very very  few issues with nvidias drivers, to the point of almost having no issues.  Maybe I'm just lucky, but I don't see what all the fuss is about.

---

### Post by zero244 on 2008-01-15
I am using a 7600 GS........and haven't really had any problems with the proprietary drivers.
Sometimes you need to do some xorg tweaking to get everything running fast and stable.....especially if your using Compiz or something.
One thing I do have to do.......is turn off Beryl when running Linux games.
Once I figured out how to adjust the xorg etc.....and to properly install the drivers I haven't had any problems.
In fact I haven't really had any problems with Linux for months.......it just keeps running without effort on my part.
Good luck.

---

### Post by 3rdalbum on 2008-01-15
I agree, binary drivers are EVIL.

I started off with Linux using an ATI card... big mistake. I had to run XGL if I wanted Compiz, and performance was really terrible.

Now I've got a shiny new self-built computer with an Nvidia card, and the RDM Nvidia driver caused random kernel panics every few days. Upgrading to the latest version of the drivers fixed it, but a new user would think Ubuntu itself was at fault (it took some detective-work to figure out that it was the Nvidia driver).

---

### Post by Prodromoi on 2008-01-15
> **bkelly said:**
> I am not quite a the point of ranting, but am having problems.  I purchased my machine preloaded from Eracks.  I just asked for dual monitor and they picked all the hardware.  The video card is marked ASUS and has nvidia GeForce 7300 SE chip set.  It was mostly working from the vendor, but the screen kept scrolling. (When the cursor moved to the edge of the screen, the entire screen and its contents would slide over in the other direction.  Some of the screen is always hidden indicating the size of the image is greater than the size of the physical display device.)

I've got an Nvidia 7300SE card as well.  I'm a (still) new user to Linux and I found I had the same two problems when setting up, but I was able (with help from others on this forum) to sort them out.  These are the relevant threads; hopefully they'll help you too:

Dual-head monitor
[http://ubuntuforums.org/showthread.php?t=650730](http://ubuntuforums.org/showthread.php?t=650730)

Mouse scrolling desktops
[http://ubuntuforums.org/showthread.php?t=646561](http://ubuntuforums.org/showthread.php?t=646561)

---

### Post by bufsabre666 on 2008-01-15
ive had problems like this until i started using envy to install my drivers, since its works flawlessly, and is alot easier to configure

---

### Post by MNICY on 2008-01-15
> **bufsabre666 said:**
> ive had problems like this until i started using envy to install my drivers, since its works flawlessly, and is alot easier to configure

envy helped me in Dapper.
I did not need it for Feisty or Gutsy though.

---

### Post by mikeym on 2008-01-16
I'm experiencing your pain. I think I've tracked everything that's bugging me about linux to dodgy proprietary drivers from NVIDIA. 

I've posted on the NV News affiliated forum but so far I've been completely stonewalled despite giving them all the information they asked for in their posting guide.

Oh well. I guess I'm stuck with a (newish) system that doesn't work very well.

---

### Post by RawMustard on 2008-01-17
Remove the resticted drivers manager and install the nvidia drivers from a terminal with no x running and I'm sure your experience will be different.  I'm not backing Nvidia here, but the restricted drivers manager has been a royal pain in the butt for me!

---

### Post by lswest on 2008-01-17
well, i've been using linux for 2-3 years now, never really had much trouble with propriety drivers, cept for ati's driver released shortly after being bought by AMD.  I actually have a chipset that (supposedly) doesn't work well with linux, but i got it working just fine, 1280x800 resolution, stable, actually can play games (when they run lol).  The card is an Nvidia 7150M/nforce 630m (or MCP67M).  i have to say, nvidia's driver works a lot better than ati's did back when i used it (nowadays my PC just runs without ati drivers) and my laptop's hardware works well.  Only issue is the propriety driver from broadcom, which doesnt work for my chip, but i ndiswrappered it:P  my end opinion is that the propriety drivers work well, considering they aren't necessarily a company's top priority.  Actually, i find the driver for Vista for my card worse than the linux one.

---

### Post by Yoke &amp; Chung on 2008-01-18
I have used the followings working nVidia cards:

1.) FX 5500, smooth install, no problem on both Feisty and Gutsy
2.) On board 6100, no problem on Gutsy, not tested on Feisty
3.) 8400M on laptop, works out of the box with Gutsy, problem with Feisty.
4.) 8600 GTS, this gave me a hard time, I was originally booting on on board 6100 which uses the restricted drivers (latest). The screen when black when I switched to 8600 GTS which is supposed to use the same driver. Have to install the nVidia driver from nVidia web site, and it is fine now.

In all fairness, the dual booted Windows XP went into a black screen too after the card was installed :) But when these things happen in Windows, I don't panic that much.

---

### Post by Borbus on 2008-01-18
I can't say I've had any problems with the latest Nvidia drivers and my 8800GT. I even run compiz-fusion and my uptime has been weeks. I used Envy to install, but used the manual mode which I think just downloads the drivers from the site and runs setup.

At least Nvidia actually bother with their linux drivers, look at ATI and Creative to see how bad it can be.

---

### Post by 3rdalbum on 2008-01-19
ATI's not so bad compared to Nvidia at the moment.

I wrote earlier in this thread about random kernel panics with Nvidia's driver from the restricted drivers manager, and that the latest Nvidia driver fixed them. Well, the latest Nvidia driver also causes video playback to go GREEN on my computer, unless you change the output module of your favourite video players.

Do I hate proprietary drivers? Yes, I do!

---

