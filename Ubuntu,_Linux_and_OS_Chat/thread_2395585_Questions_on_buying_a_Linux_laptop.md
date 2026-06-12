---
title: "Questions on buying a Linux laptop"
date: 2018-07-04
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-07-04
Say for example I go into a Dell Store and find a laptop preinstalled with Ubuntu.

1) is the version of Ubuntu preinstalled the latest version? Or do they use LTS versions?

2) what if I don't want Ubuntu and want Lubuntu instead? What usually happens? Can I offer to bring them a LiveUSB of Lubuntu to install on my purchased laptop? Or does Dell offer different Ubuntu flavors already?

3) and if I install Lubuntu, will there be any issues? Like drivers and such?

---

### Post by mastablasta on 2018-07-04
> **ardouronerous said:**
> Say for example I go into a Dell Store and find a laptop preinstalled with Ubuntu.

1) is the version of Ubuntu preinstalled the latest version? Or do they use LTS versions?

usually LTS. i believe sometimes their version are slightly modified for hardware compatibility.

> 
2) what if I don't want Ubuntu and want Lubuntu instead? What usually happens? Can I offer to bring them a LiveUSB of Lubuntu to install on my purchased laptop? Or does Dell offer different Ubuntu flavors already?


you have two options either install the lubuntu-desktop package from software center or (this is IMO a better option) simply install just the LXDE (not sure what the exact package name is).

> 
3) and if I install Lubuntu, will there be any issues? Like drivers and such?

nope. Lubuntu is JUTS Ubuntu with LXDE desktop and some selected programs. ofcourse it is then also tested to make sure all stuff works well. you can try it in virtual machine.

drivers in Linux are part of kernel or patches to kernel (firmware). they have nothing to do with desktop environment.
e.g. server image will have same drivers as desktop image etc.

---

### Post by ardouronerous on 2018-07-04
Thanks for the reply.
All the computers that I've ever owned and used Lubuntu on are all hand-me-downs from relatives and I have 0 experience in purchasing a Linux laptop.

So, if I decide to buy a Ubuntu laptop from Dell and install Lubuntu 18.04 on it, there's a risk that there's hardware capability issues?

Also, I forget to ask, if I install Lubuntu, does that void warranty?

---

### Post by sudodus on 2018-07-04
An alternative that will often

- give you more computer for the money (compared to a brand new computer)

- provide good compatibility between the linux drivers and the hardware components

is to buy a **refurbished enterprise class computer**, a second hand computer from a well known company, that is offering at least 6 months guarantee (enough for you to make sure that it is working in a stable way after the bumps during the delivery).

---

### Post by TheFu on 2018-07-04
Dell has online chat.  Ask the questions there?

Only seen LTS releases on their systems. Looked last week and they were still using 16.04; hadn't moved to 18.04 yet. I think that is smart.  Personally, I only use LTS releases.

Wouldn't expect them to install Lubuntu, but you never know. Probably depends on the specific employees at the location and whether company policy prohibits that effort.  If you take Lubuntu into an Apple store, would they help you install it onto a Mac?

I've had a few Dell laptops over the years. Usually drivers just work, unless the underlying motherboard or networking chips are really, really, new.
I've had good luck with Dells. Never had one pre-installed with Linux, but have put Linux onto 3 of them. At the time, the video drivers were the hardest part, but that was 8+ yrs ago. With onboard Intel GPUs, the drivers are all automatic.  I've seen the XPS 13 running different Linuxen a few times, so doubt there's be huge issues with that specific line.

If you walk into a Dell store with Lubuntu on a flash drive, they should let you boot it and "Try Lubuntu" to test out that everything important you want is working.  Make a checklist - video, audio, wired NIC, wifi, video-playback, ... make sure everything works the way you want. I'd check the USB3/USB-c ports handle booting too.  My current non-Dell laptop won't boot from USB3 ports.  If anything doesn't work well, run a full **lshw** and **inxi -Fx** to capture the system information to a file and do some research on those chips back home.  It might be really easy to get it working.

And if wifi is important to you, buy the $20 upgraded wifi card they sell. I didn't on my last laptop and it is stuck at 150 Mbps connections as the top speed, though I only connect at about 70 Mbps no matter what I do.  My fault for going cheap.

---

### Post by sudodus on 2018-07-04
> **ardouronerous said:**
> So, if I decide to buy a Ubuntu laptop from Dell and install Lubuntu 18.04 on it, there's a risk that there's hardware capability issues?

Make a cloned copy of the installed system in the delivered state and test that copy can restore from it to another drive, (or simply remove that drive and let it be backup) and install Lubuntu (into another drive). It will probably work, and if not, you know how to get back to a working system.
> 
Also, I forget to ask, if I install Lubuntu, does that void warranty?

You must ask that question to the vendor (and maybe you need a written answer to be sure).

---

### Post by TheFu on 2018-07-04
> **mastablasta said:**
>  
e.g. server image will have same drivers as desktop image etc.

That has not been my experience.  The server installer includes all the drivers, but on first reboot, I've found it commonly didn't include the network drivers I needed for wifi or USB-GigE adapters.  Which makes installing those a huge pain, since there isn't any network working.  Sure, the same drivers can be used, but "server" doesn't install the same drivers as desktop.  IME.

---

### Post by ardouronerous on 2018-07-04
Thanks for the info.
So basically, it's a better idea to purchase a second hand 64-bit computer than a new because there a greater chance the hardware drivers are already included in the kernel.

Another question, say I do buy a Dell laptop preinstalled with Ubuntu LTS, LTS is supported for 5 years, but what happens if I upgrade to the next LTS?
Based on what I've Googled, Dell says you are basically on your own at that point, so basically, my question is what are your experiences in upgrading a laptop preinstalled with Ubuntu?

---

### Post by sudodus on 2018-07-05
> **ardouronerous said:**
> Thanks for the info.
So basically, it's a better idea to purchase a second hand 64-bit computer than a new because there a greater chance the hardware drivers are already included in the kernel.

According to my experience, yes.
> 
Another question, say I do buy a Dell laptop preinstalled with Ubuntu LTS, LTS is supported for 5 years, but what happens if I upgrade to the next LTS?
Based on what I've Googled, Dell says you are basically on your own at that point, so basically, my question is what are your experiences in upgrading a laptop preinstalled with Ubuntu?

We have a Dell Latitude E7240 with a 4th generation Intel 4th generation i5 CPU (and Intel built-in graphics and wifi). Ubuntu works well without any tweaks.

We have a Dell Precision M4800 with Intel i7 4th generation CPU (and nvidia graphics and Broadcom wifi), where the free linux nouveau graphics driver works well, and I need a proprieatary driver for the wifi chip). Ubuntu works well with the tweak for Broadcom.

---

### Post by treb0r on 2018-07-05
If you buy a Dell laptop that is preinstalled with Ubuntu, you don't need to worry about drivers as long as you are running a sufficiently modern kernel (a kernel released after the laptop).

Back in the day, Dell would ship drivers with their machines, and they also provided a PPA. They now work with upstream to ensure that all the necessary drivers are available in the kernel. This is great because it means that the machines will work with any Linux distro, not just Ubuntu. The latest Dell precision laptops are certified for RHEL even though they ship with Ubuntu preinstalled.

Because of this, you should have no issues upgrading a Dell machine that ships with 16.04 to 18.04.

I have used Dell Ubuntu laptops for a few years now (currently running a Precision m3800) and have had a great experience all round. I particularly enjoy their onsite support. It's like a breath of fresh air to work with a large manufacturer that really gets Linux!

---

### Post by Geoffrey_Arndt on 2018-07-06
These days, one of the top laptop providers is System 76 (Denver, CO, USA).    They very much "get" it right in my view.   No worries about drivers - - it's all done for you and the setup process takes maybe 10 minutes.   A also like the free liftetime trouble-ticket system they have (software & config type of help).   Also, these systems are optimized for PopOS - a 1st cousin of Gnome3, but you can also get standard Ubuntu 18.04 LTS.    If you don't like either, then you can certainly install Lubuntu (it's your choice).

Maybe these laptops will work for you too:    [https://system76.com/laptops](https://system76.com/laptops)

---

### Post by 1clue on 2018-07-06
Pull the drive out of the system before you turn it on, and then put in another (possibly better) drive. Install what you want. When you sell it or need service, swap the drives back.

I have never owned a laptop which still had the original operating system on it the day after I bought it. I never trust the manufacturer to not put on some sort of "convenience" software that I don't like. I usually have extremely specific preferences on what software is on it and what isn't.

WRT desktops and servers, I have bought a new complete desktop system but the last time was when a Pentium was new technology and 64 MB RAM was huge. Everything for me (not a business I worked for) since then has been hand-built by me, for my specific needs. Then some flavor of Linux installed by me, often multiple times but not so much with repeats any more.

---

### Post by treb0r on 2018-07-06
I really like the the look of System 76 but the problem for me is that I live in the UK so it's hard to get support. That's the real benefit of Dell. They will have an engineer over to my office within 24 hours of reporting an issue. This is why I always go for the Precision range. They are more expensive but they come with 3 years onsite support included.

---

### Post by Geoffrey_Arndt on 2018-07-09
treb0r . . . . yes, that makes 100% sense if your office/company is small to medium size (and doesn't have Linux admins contracted or employed).

---

### Post by TheFu on 2018-07-09
+1 on Dell business systems, if you expect a tech onsite.   Beward that if the OS they ship isn't the one on the system, Dell might not help with software/driver issues.  I always pull the original HDD out and put it on a shelf because I'm likely to end up running some mix of other OSes anyways.

The last 8 months or so, inside the USA, vendors shouldn't be able to refuse hardware warrant support just because the OS is different, but I'd rather not be the 2nd test case thanks to right to repair laws and court rulings. A 500GB laptop HDD is $40 here, so it isn't worth my time to not put in a new one, or one I have lying around.  SSDs in the size I need (64G) have been less than $40.

FWIW, building a laptop from parts doesn't usually make sense.  Last time I looked, that was only possible for 17inch version and resulted in very heavy systems.   For desktops, I stopped buying complete systems in the 1990s after being burned with terrible hardware from a few major PC vendors.  I want to know what is in my desktops and do the research to ensure each part works with the OS I intend to run.  Sometimes even vendors who do support Linux very well will release hardware that isn't supported.  It is best to always check first.  Always.

---

### Post by bodhin2 on 2018-07-09
i have had many thinkpads and when i first got into linux all of the high end linis guys ran thinkpads.  FWIW.....

---

### Post by treb0r on 2018-07-10
> **bodhin2 said:**
> i have had many thinkpads and when i first got into linux all of the high end linis guys ran thinkpads.  FWIW.....

Indeed. I have also had many thinkpads. In fact, when I switched to buying Dell a friend laughed at me for buying a 'hairdresser's laptop'!

No matter. The fact that Dell ship with Ubuntu preinstalled when Lenovo don't tells me all I need to know.

---

### Post by treb0r on 2018-07-10
> **TheFu said:**
> +1 on Dell business systems, if you expect a tech onsite.   Beward that if the OS they ship isn't the one on the system, Dell might not help with software/driver issues.  I always pull the original HDD out and put it on a shelf because I'm likely to end up running some mix of other OSes anyways.

This is an important point. Here in the UK Dell have stated that if you install a different OS they may ask you to reinstall the original that the device shipped with before they will escalate the issue. Although this probably doesn't apply if they ship Ubuntu and you install Windows...

---

### Post by saderror256 on 2018-07-16
System76 Offers Ubuntu preinstalled vendors and is well known for it (they own a fork though called pop-os now).

Dell has some ubuntu laptops.

Your Best bet is to go for a fresh install of ubuntu, straight from the usb. Then you can get a good install of ubuntu and ensure no bloatware is installed.

---

### Post by mIk3_08 on 2018-07-17
I rather go to System76; Your computer hardware chip-set is exactly matches to your Ubuntu OS. That's why I go recommend system76 anyway. They build a hardware machine that will be compatible to Ubuntu O.S.

---

### Post by treb0r on 2018-07-17
I'm the Linux admin around here :).

I was referring to hardware issues. I've had various problems over the years with faulty screens, power supplies etc etc.

This Dell M3800 I'm typing on had a new motherboard fitted two weeks before the on-site warranty expired. I reckon I'll get at least another three years out of it now, fingers crossed!

---

### Post by 1clue on 2018-07-17
> **treb0r said:**
> I'm the Linux admin around here :).


You made me laugh out loud. EVERYONE reading this is the Linux admin around here.

I am gROOT!

[https://www.youtube.com/watch?v=ph_l7Pp_1mk](https://www.youtube.com/watch?v=ph_l7Pp_1mk)

***Edit:** I'm not making fun of you. I think what you said is fantastic. *

---

### Post by treb0r on 2018-07-18
> **1clue said:**
> 

***Edit:** I'm not making fun of you. I think what you said is fantastic. *

Don't worry, I didn't think that you were :p

---

### Post by mIk3_08 on 2018-07-19
What happen here? :-D It seems that something is silly going on here. :-D

---

### Post by treb0r on 2018-07-20
> **mIk3_08 said:**
> What happen here? :-D It seems that something is silly going on here. :-D

I'm just having my Linux admin skillz disparaged :D:D:D

---

