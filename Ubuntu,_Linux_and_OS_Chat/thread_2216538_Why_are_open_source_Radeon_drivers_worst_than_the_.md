---
title: "Why are open source Radeon drivers worst than the official ones?"
date: 2014-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Carllacan on 2014-04-12
Hi.

I recently had a talk about Ubuntu & Linux with a non-computer-savvy person, and eventually it came to graphical performance. I explained how there are both open and privative source drivers for Ubuntu for most graphical cards and I admitted that the privative ones are superior (read: better performance), at least on my personal case, Radeon cards. Then came a question that I couldn't answer, which I'd like to pose to you.

Why is it that privative source drivers for graphic cards are better than the open source ones? Is it that the companies don't give the opensource developers enough specifications about their hardware? Or is it lack of knowledge and expertise (in this domain at least) from the devs?

---

### Post by RadicaX on 2014-04-12
That is a good question! I would figure it is because the privative ones from the company, being closed source as they are, know of the hardware they are dealing with, and the secrets. While the Open-source drivers are not private, and anyone can look at it, even other companies, so you might lose trade secrets if you gave too much information out. (And explains why there is an open source version, and a closed source version). But it could also be, that the Open-source teams that make the drivers, have absolutely no information on the cards and are figuring it out themselves. (It is hard to get any information from a company, much more so for something that is free, or open-source). It would be in the sense then that it is like those people that try and figure out the recipe to Coke-cola. They give the information out of things they are trying, but they are never given information from Coke-cola about it really.

---

### Post by monkeybrain20122 on 2014-04-12
Well actually other than gaming the open source radeon driver is better than fglrx in my experience. Much easier to maintain for start (kernel upgrade may break fglrx though it is not supposed to and installing it is kind of a hit and miss experience comparing to Nvidia). 

For most things other than gaming  the open driver is actually faster and smoother, fglrx always has some weird glitches on 3d desktops. 

With a recent enough  card and up to date mesa I even get vdpau. For recent kernels I can get dynamic power control so the laptop no longer overheats and the fan no longer blows nonstop(needs to be enabled manually though) Since I only do light gaming and don't care for a few extra fps I will not even bother with fglrx (with a nvidia card I would use the blob over noveau though, as the gap there is much bigger)

---

### Post by Gnawnsense on 2014-04-13
> **monkeybrain20122 said:**
> 
For recent kernels I can get dynamic power control so the laptop no longer overheats and the fan no longer blows nonstop(needs to be enabled manually though) Since I only do light gaming and don't care for a few extra fps I will not even bother with fglrx (with a nvidia card I would use the blob over noveau though, as the gap there is much bigger)

If I could figure out how to get this AMD 6800 to tone down it's constant fan use, I'd be in paradise.

---

### Post by craig10x on 2014-04-13
AMD's have always tended to run much hotter then intels (which is why in more recent years, i now only buy computers with intel chips)...however, i have read that there have been huge improvements for the open source amd drivers in ubuntu in the kernel that ubuntu 14.04 uses, so when it's released next week, i suggest you give that a go and perhaps you may find your computer running a lot cooler with the fan coming on less often...

If you do, make sure you use the open source driver and not the fglrx one...that's the one the will likely show improvements for you...

---

### Post by mips on 2014-04-13
> **monkeybrain20122 said:**
> Well actually other than gaming the open source radeon driver is better than fglrx in my experience.

So if you expect performance from your hardware you are kinda screwed when it comes to ati/amd. Even though I reckon amd provides better gpu vs price at the moment I will not buy one simply due to the driver support in linux. If I was a windows only user I would be buying ati/amd right now. Unfortunately I have to stick to nvidia because their closed drivers perform well in linux.

Open source drivers will always face an uphill battle due to the full hardware specifications not being available. Hopefully both amd & nvidia become more open, I would love to see mantle for example in linux to counter DX12, amd should simply opensource it to get more market share. their chips can be found in most consoles these days and if they can extend that to the desktop with opensource stuff (think valve steambox etc) it would be great.

---

### Post by su:bhatta on 2014-04-13
> **Gnawnsense said:**
> If I could figure out how to get this AMD 6800 to tone down it's constant fan use, I'd be in paradise.

Did you give this a shot:
[http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)

---

### Post by d-cosner on 2014-04-13
RadicX, I like what you wrote, it makes a lot of sense! The used laptop I got last week has an AMD A1 processor with ATI/AMD on-board graphics. I have noticed that with 14.04 the laptop never really gets hot. I am using the open source drivers and they work just fine for me. I am not a gamer and I do not often do anything very demanding with the laptop though.

I figure too by sticking with the open source drivers I can most likely avoid any problems with system updates. I had tried using proprietary drivers on the last laptop I had but the open source drivers seemed to give me a lot less trouble. My former laptop was running Ubuntu 12.04 x64 and ran pretty hot.

14.04 seems to have much better hardware support and a lot more fine tuning.

---

### Post by Gnawnsense on 2014-04-13
> **bhattabhishek said:**
> Did you give this a shot:
[http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)

Thanks so much for sharing.

Gave it a go, but doesn't seem to of made a difference with my particular setup.

---

### Post by silex89 on 2014-04-13
> **mips said:**
> amd should simply opensource it to get more market share. their chips can be found in most consoles these days and if they can extend that to the desktop with opensource stuff (think valve steambox etc) it would be great.

I'd love to see this as well, but it may never happen unfortunately because a good part of the Catalyst code is based upon Microsoft's DirectX API, so if they open-source it, they could risk being sued by M$ for publishing without permission important code of the 3D architecture which happens to be closed source (obviously).

What I personally see with much much promise is [this possible new strategy]("http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_kernel&num=1") from AMD to make the kernel module development more open.

Since I don't play heavy duty OpenGL game titles on my Linux machine, the open source driver is more than enough for my AMD Richland APU. The latest mesa code has wonderful gains in performance so Catalyst no more!, just open source goodness :D.

Best regards!

---

### Post by monkeybrain20122 on 2014-04-13
> **Gnawnsense said:**
> If I could figure out how to get this AMD 6800 to tone down it's constant fan use, I'd be in paradise.

If you have a recent enough kernel (3.11+?) you can edit /etc/default/grub
and change the line 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"                      
```
to
                             ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"                       
```
save, run
```
sudo update-grub
```
and reboot.

It works like a charm on this machine with hd6310 (kernel 3.13 and 3.14)

---

### Post by monkeybrain20122 on 2014-04-13
> **mips said:**
> So if you expect performance from your hardware you are kinda screwed when it comes to ati/amd. Even though I reckon amd provides better gpu vs price at the moment I will not buy one simply due to the driver support in linux. If I was a windows only user I would be buying ati/amd right now. Unfortunately I have to stick to nvidia because their closed drivers perform well in linux.

Open source drivers will always face an uphill battle due to the full hardware specifications not being available. Hopefully both amd & nvidia become more open, I would love to see mantle for example in linux to counter DX12, amd should simply opensource it to get more market share. their chips can be found in most consoles these days and if they can extend that to the desktop with opensource stuff (think valve steambox etc) it would be great.

Well I don't buy amd. But I am able to get my greasy hands on other people's amd machines and test them. :) I always thought I should avoid amd but after checking out a few machines recently they are not as bad as I thought provided you use recent enough open driver (not the outdated versions packaged by Ubuntu, e,g vdpau decoding is availiable for the latest mesa drivers so I can watch 720p effortlessly on this rather weak hp netbook in flash or any supported player--mplayer/mpv/vlc,  don't get that in Ubuntu's packaged deal) 

For performance I suppose Nvidia is the king. But I use only laptops since desktops take up too much space and I move/travel a lot, Nvidia laptops are plagued with optimus and the ones without (e.g system 76) cost a lot. Not being a gamer it is hard to justify paying that much even if I could afford one (and I can't at the moment) That leaves amd and intel. I have a relatively old intel (iron lake) on my current laptop, graphic wise it is ok, but not as good as the amd machines I have tested with using open source drivers (use vaapi for hardware decoding on intel). Not sure about newer intel hd graphics.

---

### Post by craig10x on 2014-04-13
If you upgrade or install 14.04, it just might do it for you...it's only a week away now ;)

---

### Post by monkeybrain20122 on 2014-04-13
> **craig10x said:**
> If you upgrade or install 14.04, it just might do it for you...it's only a week away now ;)

Why would I trade in my working system heavily tweaked to perfection for something just out of beta? I have more updated kernel and graphic driver than stock 14.04 as well as all the software I use regularly (thourgh ppas not yet in 14.04 or self compile). :) I will be staying on 13.10 until late july when it reaches eol unless there is something spectacular in 14.04 before that.

I will just put 14.04 on an external hd and take my time to optimize/customize it and wait for bug fixes. In the end of july I will just clone it and restore to my working machine to replace 13.10. No "upgrade", no nasty surprises, and no 'clean install' necessary either. :)

---

### Post by Gnawnsense on 2014-04-13
> **monkeybrain20122 said:**
> If you have a recent enough kernel (3.11+?) you can edit /etc/default/grub
and change the line 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"                      
```
to
                             ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"                       
```
save, run
```
sudo update-grub
```
and reboot.

It works like a charm on this machine with hd6310 (kernel 3.13 and 3.14)

I rebooted and walked away for a bit. Came back and it seems to of been a positive thing, after all. Finally a quiet GPU :)

---

### Post by RadicaX on 2014-04-13
I am glad you enjoyed that D-cosner! 

Since my computer was cheap when I got it, I did go the intel route when I bought it years ago. It was this machine, or a Pentium four with a nicer graphics card, (Like ATI or Nvidia or something), but when I seen this was a dual processor, I had to go with it. Using Xubuntu, I have never had much trouble in doing anything I needed. Since I do not really game on the computer, (Console Gamer) I have never really needed to worry about the drivers. I use the OpenGL for a PS1 Emulator mind you (I have quite a few PS1 games, but my PS1 is broke), and that does not seem to have any problems. But that is not the latest and greatest of games or anything.

I think this is going to change somewhat soon though, what with the SteamBox coming out, and using Debian as a base. While I do not expect a ton of the stuff to translate over, I feel like that will probably be the standard from now on for PC gaming. So it is going to be interesting how that affects Linux in Large. I know they must be adding all kinds of stuff to their Distro, the minimum requirement was 4 GB of Ram I seen. Mama mia that is a lot of Ram.

---

### Post by su:bhatta on 2014-04-16
> **Gnawnsense said:**
> I rebooted and walked away for a bit. Came back and it seems to of been a positive thing, after all. Finally a quiet GPU :)

See, the Webupd8 article on Radeon DPM does its work :)

Seems like first time around you didn't do a update-grub?

Also, I am getting far better battery life than i ever did !

---

