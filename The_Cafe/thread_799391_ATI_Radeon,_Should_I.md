---
title: "ATI Radeon, Should I?"
date: 2008-05-19
forum: The Cafe
---

### Post by rab4567 on 2008-05-19
AMD seems to be really pushing their radeon cards these days, and I was wondering how good they work with compiz-fusion. Does Ubuntu provide a quick driver install and how stable are they. I'm in the market for one of these babies.

---

### Post by Kinst on 2008-05-19
Bad. Nvidia is infinity times better.

---

### Post by Anduu on 2008-05-19
With enough mucking about ATI works however I have to recommend NVidia.

---

### Post by cardinals_fan on 2008-05-19
Stick with NVIDIA.

---

### Post by FuturePilot on 2008-05-19
Yes stick with Nvidia. I know ATI has promised open source driver, but it could still be a long time until we see them. And by then, any card you would buy now may be out of date seeing how fast things move these days. Save yourself a headache.

---

### Post by rab4567 on 2008-05-19
Its a shame ATI won't release the specs on these cards their losing money on this. I was lucky when got into linux HP 1450a AMD 4200 2GB 500HD Nvidia 6150 LE, Acer AMD 4400 1GB 320HD Nvidia 6100, thanks guys good to know.

---

### Post by Canis familiaris on 2008-05-19
> **rab4567 said:**
> AMD seems to be really pushing their radeon cards these days, and I was wondering how good they work with compiz-fusion. Does Ubuntu provide a quick driver install and how stable are they. I'm in the market for one of these babies.
AMD is working hard on their ATi drivers for Linux and that is why I purchased the motherboard with ATi integrated graphics but compiz does not work well at all. Games run decently though.
I would recommend an nVidia for Linux for now. They are much better than ATi drivers. However by far Intel are the best if you do not plan on gaming, seriously. They work out of the box with Compiz but for Intel Graphics you need an Integrated Intel graphics Motherboard and an Intel processor. There are no Intel integrated graphics for AMD processors though.

---

### Post by PmDematagoda on 2008-05-19
> **rab4567 said:**
> Its a shame ATI won't release the specs on these cards their losing money on this. I was lucky when got into linux HP 1450a AMD 4200 2GB 500HD Nvidia 6150 LE, Acer AMD 4400 1GB 320HD Nvidia 6100, thanks guys good to know.

They have done that already, the [radeonhd]("http://www.radeonhd.org/") project is an open source ATi driver(there maybe more) that uses these specifications opened up by ATi.

---

### Post by Afkpuz on 2008-05-19
YES!  GO WITH NVIDIA!  You will save yourself so much time and energy, especially if you decide to switch distros. Nvidia is far ahead of ati in compatibility and power.  Even though Ubuntu has taken great leaps forward in ATI technology since I started using it, nvidia has also done the same and remains far ahead.

**My Ubuntu ATI Video Card experience**
in Dapper Drake (6.04)
There was a driver package in the repos, but could never make it to a gui to get it.  Took a long time to find out how to download and install the correct driver via the command line.  Compiz would not work for me, although that was 2 years ago.  Live boot CD wouldn't work, even with safe mode: had to use alternate install disc.

in Edgy Eft (6.10)
Pretty much the same thing as above I think.  I'm fuzzy on the details of Edgy.

in Feisty Fawn (7.04)
Same.  Safe mode live boot wouldn't work, but compiz became possible, or at least I discovered that with the help of xserver-xgl, it would run.  However, xserver-xgl seemed to caused lots of little problems all over the place, so thumbs down for that.  Still using alternate CD.

in Gutsy Gibbon (7.10)
Mostly the same.  Still using alternate install disc.  Safe graphics install still won't work.  bugs with compiz and xgl fixed a little.


in Hardy Heron (8.04)
Finally, I can use the live boot CD which is AMAZING.  I also don't need to use crappy xserver-xgl.  WTG hardy!  This was what I've been waiting for.



I think that ati is about a year or 2 behind nvidia in linux support.  Plus, the word on the street is that they don't play as well with the linux community as nvidia does.  On the more functional side, Nvidia cards are able to handle more load, do prettier effects, do the dishes, etc.  I highly recommend them.  I have an nvidia 8400 GT and it really cooks on my linux MCE PC, which by the way, refused to do anything on a different ATI-vid-card PC.  Just by nvidia man

---

### Post by uraldinho on 2008-05-19
once you get the ATI drivers working, the card itself is OK. I installed beryl last year, it was fun. So, I don't see why compiz shouldn't work. 

I believe the display drivers that are labeled as "radeon" and "ati" are the open source version of ATI drivers. I used to use radeon drivers in fedora. I never managed to make them work properly in ubuntu, gave up trying and used fglrx for almost 2 years now.

---

### Post by SupaSonic on 2008-05-19
Go with NVidia. I've had my share of disappointments with ATI, including driver installation and inferior performance. It's not worth it.

---

### Post by jespdj on 2008-05-19
> **Anurag_panda said:**
> AMD is working hard on their ATi drivers for Linux and ...
A long time ago (about a year ago or so?) there was some news on the Internet from ATI, they were explaining that they were rewriting their drivers and promising that their support for Linux would become much better. Now it's a year later and there still doesn't seem to be much improvement, there hasn't been much news about new ATI drivers the past year. So don't hold your breath.

---

### Post by Perfect Storm on 2008-05-19
+1 @ Nvidia

nvidia: If you want easy, good performance. Also if you want to game on linux wether it's natively or through wine. + eyecandy
Intel: ok, if you only do office/e-mail and so on and want to pep up your Desktop. Bad gaming card - usually trouble to get decent out of these cards.
ATI: Headache. When it's sets, it can some gaming - but there's alot to be desired from the driver. Most gaming trouble threads you'll find is regarding ATI cards.

---

### Post by PmDematagoda on 2008-05-19
> **Artificial Intelligence said:**
> +1 @ Nvidia

nvidia: If you want easy, good performance. Also if you want to game on linux wether it's natively or through wine. + eyecandy
Intel: ok, if you only do office/e-mail and so on and want to pep up your Desktop. Bad gaming card - usually trouble to get decent out of these cards.
ATI: Headache. When it's sets, it can some gaming - but there's alot to be desired from the driver. Most gaming trouble threads you'll find is regarding ATI cards.

Yep, those points are true, except of course you can't generalise that ATi cards are trouble, there are cards that do work out-of-the-box and with the radeonhd driver, the situation can improve quite a lot. 

About Intel, yep, they don't have much performance and are really meant for the office workers, etc. But since the Intel driver is open source it does mean that they tend to be a bit more bleeding edge than other closed drivers like Nvidia. Of course, this doesn't necessarily mean that Nvidia does a bad job, they do a very good job and a better one than that in fglrx:).

For now, you are just better off getting an Nvidia since they tend to support new GPU's on Linux much more faster and more properly than ATi does.

---

### Post by Mazza558 on 2008-05-19
If you go ATI, go for Gutsy. A bit more setup but the Gutsy driver's much faster.

---

### Post by rab4567 on 2008-05-19
OK I'll stick with nvidia so whats the best laptop brand I should look for?

---

### Post by PmDematagoda on 2008-05-19
> **rab4567 said:**
> OK I'll stick with nvidia so whats the best laptop brand I should look for?

You can get a good powerful laptop from [System76]("http://system76.com/"), it even has Ubuntu preloaded so it would mean some good, official support as well;).

You can even try Dell, but from my understanding, their choice is less(in terms of Ubuntu preloaded ones).

---

### Post by Perfect Storm on 2008-05-19
> **PmDematagoda said:**
> Yep, those points are true, except of course you can't generalise that ATi cards are trouble, there are cards that do work out-of-the-box and with the radeonhd driver, the situation can improve quite a lot. 

About Intel, yep, they don't have much performance and are really meant for the office workers, etc. But since the Intel driver is open source it does mean that they tend to be a bit more bleeding edge than other closed drivers like Nvidia. Of course, this doesn't necessarily mean that Nvidia does a bad job, they do a very good job and a better one than that in fglrx:).

For now, you are just better off getting an Nvidia since they tend to support new GPU's on Linux much more faster and more properly than ATi does.

How dare you correct me! This will be reported directly to the Overlord!!! :mrgreen:

Well, I hope ATI (see AMD) really straighten this out soon. Nvidia shouldn't be the only options. My computer is AMD and when the ATI(AMD) card gets superior (and also due to Open Source) I'll switch, even though I have been Nvidia user for many years.

---

### Post by zachtib on 2008-05-19
After 3 years of ATI hell with my laptop's Radeon 9000, I finally purchased a laptop with an Nvidia Quadro card.

I couldn't be happier with it, and I won't be returning to ATI anytime in the foreseeable future.

---

### Post by zachtib on 2008-05-19
> **rab4567 said:**
> OK I'll stick with nvidia so whats the best laptop brand I should look for?

I'm a diehard Thinkpad fan, and I just got a new T61p (specs in sig)

Everything worked out of the box with Ubuntu (although I did have to apt-get install the nvidia driver) including Bluetooth, wifi, SD card reader, and temperature sensors.

---

### Post by PmDematagoda on 2008-05-19
> **Artificial Intelligence said:**
> How dare you correct me! This will be reported directly to the Overlord!!! :mrgreen:

Well, I hope ATI (see AMD) really straighten this out soon. Nvidia shouldn't be the only options. My computer is AMD and when the ATI(AMD) card gets superior (and also due to Open Source) I'll switch, even though I have been Nvidia user for many years.

Hey!! I'm a genie, remember??:-P

Ditto for that, I've been using a 6200 for 3 Ubuntu releases and it worked brilliantly with all of them, no hiccups at all, just great compositing fun and gaming:). When the ATi card gets better support on Linux, obviously, I will not fail to give ATi a shot and maybe use it in place of Nvidia.

---

### Post by aaaantoine on 2008-05-19
I have an integrated ATI chipset, which... works.

The open source drivers don't support 3D for it yet.  The proprietary fglrx drivers that are supplied by Hardy's repos are rather buggy, however.

That said...

1. It has gotten progressively easier to use desktop effects with the restricted drivers since Feisty.  From installing packages and mucking about with conf files in Feisty ... to just installing fglrx and xserver-xgl in Gutsy ... to simply installing fglrx in Hardy.

2. AMD has opened the documentation to just about all of their current ATI chipsets at this point.  It is a matter of time before the open source ATI drivers are up to spec.

---

### Post by gn2 on 2008-05-19
ATI = **[COLOR="Red"]A[/COLOR]** **[COLOR="Red"]T[/COLOR]**housand **[COLOR="Red"]I[/COLOR]**rritations

Nvidia is a far better choice for Linux.

---

### Post by Changturkey on 2008-05-19
Is Intel support even better than ATI?

---

### Post by klange on 2008-05-19
> **Changturkey said:**
> Is Intel support even better than ATI?
Yes. Period.

---

### Post by zachtib on 2008-05-19
> **Changturkey said:**
> Is Intel support even better than ATI?

Intel support is fantastic, as they have fully open source drivers

---

### Post by Sammi on 2008-05-19
Just don't plan on doing any gaming with an Intel card. They're just not engineered for proper 3D. Performance will be horrible and some games can't even start up on an Intel card.

Which ever is the first of ATI or Nvidia to make a functional open source driver, can be sure of getting a few hundred bucks of business from me right away, but for now Nvidia will have to do, as I have to be able to run games :lolflag:

---

