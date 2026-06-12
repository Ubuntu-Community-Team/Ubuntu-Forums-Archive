---
title: "Sorry for the Noob Question, but I have 20.04 LTS, and it's....   heavy? What to do?"
date: 2021-03-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Swan_DB on 2021-03-12
I have a desktop from 2012, and a laptop from 2008.  I'm looking at some lightweight Linux, maybe Peppermint, Stax, Q4OS, Lubuntu, Kubuntu, or something, for the Laptop.

But now, I'm wondering if I wouldn't benefit from swapping my Desktop from Ubuntu 20.04 to some other, lighter weight, distro.

Anyone here do the distro swapping often, and can tell me: 1) is it worth swapping just for the learning?  2) Will I miss anything going to a minimal distro or lighter weight distro?  

I use "Document Scan", "Libre Calc", VS CODE and G++ compiler, Google Chrome, Blender/Gimp, "Screenshot" utility, and *very importantly* I can hook up my iPhone 5 (or maybe it's a 6?) and my Ubuntu 20.04 just works and I can almost seamlessly upload iPhone pictures/videos to my Desktop.

Can I get all of these programs/functionality from something like Q4os or Lubuntu or Peppermint or Parrot?  Is Parrot a distro?   Idk.  "16 Best Lightweight Linux Distributions for Older Computers" :   [https://itsfoss.com/lightweight-linux-beginners/](https://itsfoss.com/lightweight-linux-beginners/)
Any insight, input is appreciated.

PS.  I live with an untreated brain injury, and "just google it" is not easy for me to do due to serious cognitive issues, hence this post to get relatively simple questions answered.  Thank you in advance in case I forget :guitar:

---

### Post by guiverc on 2021-03-12
I'm on a 2009 dell desktop, and whilst I'd love something newer/faster, the largest hassle I've had is with disk size (it's a 160GB hard disk that I've split into two, containing my two systems)
- 18.04 LTS  (my *stable* release if I ever stuff up my primary used
- *hirsute* (or what will be 21.04 when it's released next month; this system stays on the *development* cycle, is upgraded every six months and is next due to jump next month)

I'm currently using the *hirsute* and using Lubuntu/LXQt (my default).   But I can logout & login again using either Xubuntu/XFCE or Ubuntu/GNOME. They'll all run, my preference is LXQt or XFCE really (GNOME is good on occasion).

The 18.04 system likewise has those three (Lubuntu/LXDE, Xubuntu/XFCE, Ubuntu/GNOME & also Ubuntu-MATE/MATE as I removed that from *hirsute *awhile back due disk space issues).  Note RAM does matter, you didn't say how much.  I like this old desktop as it has 8GB ram (a newer laptop only has 4GB & even though it's an i5-m520 [*this box pre-dates i-series CPUs*] it's slower due to less ram]

I still use on occasion, a 2005 IBM Thinkpad T43, and it likewise has many desktops (running 18.04).  That old thinkpad has only 1.5GB of RAM, but I still don't care about the extra desktops, but I'm careful with what programs are being used at the same time (even more so on 2x older thinkpads that only have 1GB of RAM)

Having multiple desktops uses more disk space, it'll only use more resources if you have programs that use different libraries/toolkits running (ie. in memory) at the same time (ie. as user that's completely under your control). 

All Ubuntu *flavors* can use programs from other Ubuntu *flavors*. The only drawback is if they're designed for a different desktop, they'll require different libraries/toolkits to share RAM, why different desktops provide programs that do the same thing

e.g. text editor

Lubuntu/LXDE = leafpad
Lubuntu/LXQt = featherpad
Xubuntu/XFCE = mousepad
Ubuntu/GNOME = gedit
Ubuntu-MATE/MATE = pluma

All programs do the same thing really, but are written to use different libraries etc thus are lightest when used with the Desktop they are designed for.

I don't consider Lubuntu a minimal distro; it's lighter yes than other desktops (it's a goal of Lubuntu & the LXQt desktop now being used), but it's not [minimal or really lightweight]("https://lubuntu.me/taking-a-new-direction/"). 

*Note: sorry this probably isn't written as the easiest to understand... pre-brain injury my job reviews all said I "didn't waste words" "frugal with words" "didn't mince words" etc.. but I struggled since ABI*

---

### Post by mikewhatever on 2021-03-12
1) ...depends on what you want to learn. In case it is to learn about other distros, then yes.
2) That is an impossible question to answer. Who can know what and if will be missed?

PS: It is generally recommended to use Ubuntu Mate, Xubuntu or Lubuntu on old hardware. Ubuntu with Gnome3 is a more RAM and CPU intensive distro.

---

### Post by CatKiller on 2021-03-12
> **Swan_DB said:**
> But now, I'm wondering if I wouldn't benefit from swapping my Desktop from Ubuntu 20.04 to some other, lighter weight, distro.

You don't need to change **distro**, but you might prefer a different **desktop environment**. They aren't remotely the same thing, but websites need clicks.

If you want to try different distros for the learning - something Debian-based like Ubuntu, something Red Hat-based, something Arch-based for the bleeding edge, and something that builds everything from source like Gentoo - then go for it. You'll probably find that running them in a VM is an easier way to check out a bunch than having to reinstall on bare metal all the time. 

*Independently of your distro choice* you can pick a desktop environment like Gnome, KDE Plasma, LXQt, Xfce, Mate, Budgie, and so on. Or no desktop environment at all, and just use a window manager to manage your windows.

---

### Post by Swan_DB on 2021-03-12
Oof, I opened the can of worms, lol.

I didn't realize the differences between Linux versions was more than just "distro".

I guess each distro has multiple desktop environments I can choose from?  I'm gonna do some more reading and figure this out, and will look into setting up a VM to start trying out different installs.  Thank you all for the input.

---

### Post by CatKiller on 2021-03-12
> **Swan_DB said:**
> I guess each distro has multiple desktop environments I can choose from?

There may well be a particular distro and a particular desktop environment that are developed entirely hand-in-glove so that you can't use one without using the other, but for the most part desktop environments (which, for the sake of a rough concept are a collection of utilities, libraries, and applications that together will provide the functions you'd expect from a desktop computer) can be replaced wholesale with another.

You can use applications that would be included with one desktop environment with a completely different desktop environment with no problem other than having a slightly higher RAM usage (if the libraries used by the application are different to those used by everything else, you need both loaded into RAM). And they might look different, because one desktop environment's way of decorating windows (GTK) can work differently to another desktop environment's way of decorating windows (Qt). KDE does a better job of making applications fit in visually than Gnome does. 

At the end of the day, the desktop environment is just a collection of software that you can use or not. The distro, though, determines things like packaging format, release schedule, support policy, and so on.

---

### Post by CatKiller on 2021-03-12
For a concrete example, let's consider Debian, Ubuntu, and Pop OS. They're very closely related distros.

Debian is a distro that's been around for a long time. They have a stable branch that (deliberately) hardly ever changes, a testing branch that has packages that will eventually go into stable, and an unstable branch that tracks the upstream projects. You can install whatever desktop environment that you want. I have no idea if there's a default. 

Ubuntu takes packages from Debian's unstable branch every six months and polishes them up for release. Every fourth release (the first release of even years) is a Long Term Support release, which gets 5 years of support instead of nine months. Some patches from Ubuntu go upstream to Debian (if they want them) and some are just maintained by Ubuntu. 

There are teams that polish up a particular desktop environment to work with a particular Ubuntu release, which become the flavours. The default Ubuntu flavour comes with Gnome, with heavy patching from upstream Gnome to make it behave more like Ubuntu's prior Unity desktop environment. Gnome used to be Ubuntu's only flavour, and the six month release schedule was to synchronise with Gnome's release schedule. You can start with any flavour and install the desktop environment (or any other application) from a different flavour. You can even remove the DE from the original flavour and just use the new one (I've done this before). It all uses the same software repositories. 

Pop OS (made by a company that sells Linux computers) takes the Ubuntu LTS base (rather than the most recent release) and applies their own patches to Gnome (which are different to Ubuntu's).  Again, you can install a different desktop environment from Pop OS's repositories if you want to.

---

### Post by TheFu on 2021-03-12
Changing DEs will be a never-ending effort to re-re-relearn things because every few years, the DE makers feel they need "new".  I suppose if you are GUI-centric, that's in your nature.

OTOH, if you truly learn the OS and ignore the GUI, things don't change nearly as much.  The shell commands are relatively stable. They don't change. Things from 20+ yrs ago work exactly the same today as they did in the 1990s.

I would use virtual machines to try out different distros. Then here is little risk to a properly working install on the real hardware.  Any Core2 Duo or better CPU with 4GB RAM or more can easily handle running 1 or a few VMs with desktop Linuxen.  I ran 8 VMs on multiple first-gen Core2 Duo CPUs with 8G of RAM in 2010. Most were servers, without any bloated GUIs, but 1 bloated GUI should work fine.

---

### Post by O)9(yo&amp;# on 2021-03-12
Linux Lite would be a good choice for the desktop. It is based on Ubuntu, and uses the XFCE desktop. It's considered a very user-friendly distro. I have used it a lot, but even it is too heavy for my 2009 desktop. but a 2012 machine should be fine with it. 

for the laptop you might need an ultra-lite system, such as Puppy, Bodhi, Peppermint etc. although a lot depends on the machine's graphics capability. On a machine that old, Nvidia drivers would not work as they are no longer supported for such old equipment. That means open-source drivers, and in my experience only the lightest distros work on computers that old. that's largely what they are for, to extend the life of old computers.

---

### Post by grahammechanical on 2021-03-12
> can tell me: 1) is it worth swapping just for the learning?

I would not swap. I would dual boot or triple boot. We would need something like 30GB hard disk space for each distribution. I suggest having a main installation of whatever distribution uses your favourite desktop environment. And then not mess with it. In this way you can continue using the installation for whatever you use the installation for.

I presently have Ubuntu 20.04; Ubuntu 20.10; Ubuntu 21.04 (development version); LXLE; Ubuntu web; Ubuntu unity; and Devan, which is a fork of Debian.

A distribution that allows you to select the desktop environment and applications during installation makes the install process more complicated. Ubuntu used to provide something called a mini iso that did just that. If not careful you could end up with a command line Linux or a desktop environment with just a few system utilities and then have to use the terminal to install any application you want. I know. I tried it out of curiosity. Ubuntu seems to have stopped providing the mini iso after 18.04. What you get now is a server installation.

Debian offers individual iso images each with a different desktop environment. Cinnamon; Gnome; KDE; LXDE; LXqt; Mate;  xfce. I think they also offer a mini iso. Also known as netboot install. I have not tested this out. So, I cannot say for sure what we can do with it. You will find that the Debian installer is a lot different from the Ubuntu installer. Can be a bit of a surprise to someone used to installing Ubuntu and its flavours.

[https://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/](https://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/)

Regards

---

### Post by mastablasta on 2021-03-15
add ram or if you already have 8 GB then add and SSD drive, add a well supported GPU card (hard to do on laptop),  and you should be good to go. it's not the OS that is heavy it's the apps actually.

i have single core from 2004 on Kubutnu. it is starting to show it's age. mostly when i want something done fast it is slow. i play old games and few newish ones. it kind of works most of the time. sometimes i get lag and CS:Go takes 8 minutes (curse you last update) to load and 2 more to load a map, but eventually it works well. gmail is ridiculously slow for some reason. maybe because i turned off various scripts.

---

### Post by Swan_DB on 2021-03-15
Thanks for all the replies here : )

> [COLOR=#000000]Debian offers individual iso images each with a different desktop environment. Cinnamon; Gnome; KDE; LXDE; LXqt; Mate; xfce. I think they also offer a mini iso. Also known as netboot install. I have not tested this out. So, I cannot say for sure what we can do with it. You will find that the Debian installer is a lot different from the Ubuntu installer. Can be a bit of a surprise to someone used to installing Ubuntu and its flavours.[/COLOR]
This has me curious, lol.  Thank you.  I'm looking for a GUI version for a computer illiterate type that will be using a laptop from likely 10+ years ago, then for my desktop, I'm going to start messing around a bit; first is the VM and testing distros; then I'll try the dual/triple boot method too.  Right now, I've got the laptop torn apart and trying to get it back together with JB weld because I broke some ribbon clips ):P

---

### Post by TheFu on 2021-03-15
IME, JB weld won't hold in environments with vibration and heat swings.

---

### Post by Swan_DB on 2021-03-15
> [COLOR=#000000]add ram or if you already have 8 GB then add and SSD drive, add a well supported GPU card (hard to do on laptop), and you should be good to go. it's not the OS that is heavy it's the apps actually.[/COLOR]


The compaq presario cq50 has 2GB, but 4GB "virtual", whatever that means, I assume it's marketing mostly, and just has ~4GB RAM, or maybe it uses 2 GB from the Hard Drive or something, idk.  The laptop will mainly be for a computer illiterate type, that will be learning Excel sheets, PDF's, and she uses Facebook and YahooMail and Gmail.  So the Applications, assuming she's not browsing the web on 5 tabs, and doing other stuff, should be light weight enough for the 4GB RAM.  If not, well, it's just time to buy another PC because this compaq laptop has busted ribbon clips and a battery that holds no charge, plus other issues.

Thanks for the reply about "it's the apps that use the RAM", makes me less worried about which Linux I install on it, assuming I get it working again (broken ribbon clips + JB weld, and I used Anti-seize lubricant as cpu thermal paste :guitar: ).

---

### Post by TheFu on 2021-03-15
Consider trying a ChromeOS clone.  That is best for non-techy people. Very light.  [https://www.howisolve.com/install-chromium-os-pc/](https://www.howisolve.com/install-chromium-os-pc/) shows how to install.  It is designed for everyone, but kids pick it up fastest.  It is basically a way to have a chromebook-like experience, just with random hardware.

I'd bet it has 2G of RAM and 2G of swap. The iGPU probably steals 256MB of RAM too.

---

### Post by mastablasta on 2021-03-18
> **Swan_DB said:**
> The compaq presario cq50 has 2GB, but 4GB "virtual", whatever that means, I assume it's marketing mostly, and just has ~4GB RAM, or maybe it uses 2 GB from the Hard Drive or something, idk.  The laptop will mainly be for a computer illiterate type, that will be learning Excel sheets, PDF's, and she uses Facebook and YahooMail and Gmail.  So the Applications, assuming she's not browsing the web on 5 tabs, and doing other stuff, should be light weight enough for the 4GB RAM.  If not, well, it's just time to buy another PC because this compaq laptop has busted ribbon clips and a battery that holds no charge, plus other issues.

Thanks for the reply about "it's the apps that use the RAM", makes me less worried about which Linux I install on it, assuming I get it working again (broken ribbon clips + JB weld, and I used Anti-seize lubricant as cpu thermal paste :guitar: ).

Gmail through browser and facebook? it likely won't be a good experience on that laptop.

they were selling HP with Ryzen 3 (3000 series) with no OS loaded here for 330 EUR last year. they are nothing special in terms of screen and disk size. but came with 8 GB ram (2 Gb is taken by GPU) and fast nVme drives. We got a version with Ryzen 5 in it for 411 EUR. i put Kubuntu 20.04 on it. it flies. boots in few seconds, loads webpages fast, he can play his favourite games, he is alt+tabing out of games to play you tube videos in background etc. 

anyway if you can still get a deal on older model of Ryzen 3 or Core i3 this kind of laptops would give good experience to someone new to computers. even one of used laptops with these ocmponents would give a better experience (especially if you can add a bit of ram and add SSD drive)

like i said old desktops (maybe as they can be upgraded in correct areas up to a point), but old laptops will need patience. they work, but the experience they give is more suitable for those that know what to expect. i have laptop with limited resources (2 GB, low powered CPU, normal slow HDD) and while it works for me ( i am used to it being a bit slow) it is not really presentable. gmail and similar (facebook and other script heavy stuff like media pages) are really slow and better accessed via other means (e.g. email client, text browser...). libre office takes time to load. even with latest version.

---

### Post by Swan_DB on 2021-03-19
> [COLOR=#000000]but old laptops will need patience. they work, but the experience they give is more suitable for those that know what to expect.[/COLOR]

I have been made aware of what a 1 core cpu is like, lol.  Trying to figure out boot loading from a old Batman USB drive I found behind the refrigerator when we moved into the trailer 8 years ago, the read/write speeds from that old USB stick are like a 3 legged turtle, plus the 1 core CPU,and the 2GB ddr2 RAM, the process of swapping the operating system is just beating me; so much waiting.  Plus the touchpad thing on the laptop doesn't function, so I have to keep swapping my mouse to do google searches, desktop back to laptop, back to desktop, and back; a second mouse would help, maybe I'll go to a Goodwill soon.

I'm stubborn, and will figure out boot loaders and the ISO file, but it may take a year or two, lol.  I'm looking for, like you said, a newer laptop with an i3 cpu or better, plus 8GB RAM, they are not that expensive, especially used ones.

Thanks for the comment : )

---

