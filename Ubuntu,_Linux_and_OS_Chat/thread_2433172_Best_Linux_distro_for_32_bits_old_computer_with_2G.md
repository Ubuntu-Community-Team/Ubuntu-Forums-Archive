---
title: "Best Linux distro for 32 bits old computer with 2GB ram?"
date: 2019-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by j2ee on 2019-12-15
I just find out none of the Ubuntu distro will support 32 bits. Which distro would you suggest? I would use it for years so hope it has long term support. I just start to use Linux so I need something user friendly. Thx.

---

### Post by guiverc on 2019-12-15
Lubuntu 18.04 LTS is supported until 2021-April using x86/i686/i386
Xubuntu 18.04 LTS is supported until 2021-April using x86/i686/i386
Ubuntu-MATE 18.04 LTS is supported until 2021-April using x86/i686/i386
Kubuntu 18.04 LTS is supported until 2021-April using x86/i686/i386
Ubuntu Budgie 18.04 LTS is supported until 2021-April using x86/i686/i386

and there very well could be more, can be downloaded from [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) or [http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)  (where you replace the lubuntu with the flavor you want)

[http://ubuntu-news.org/2019/08/08/ubuntu-18-04-3-lts-released/](http://ubuntu-news.org/2019/08/08/ubuntu-18-04-3-lts-released/) which states

"[COLOR=#333333]**Maintenance updates will be provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Base. All the remaining flavours will be supported for 3 years.**"

[/COLOR]with the 3 years starting from release, ie. 2018-April (thus 2021-April)

FYI:   I'm using Lubuntu 18.04 LTS on a IBM Thinkpad t43 which has 1.5gb of ram, though it also has xubuntu-desktop (Xubuntu) installed too. I also have it installed on a dell latitude d610 (1gb ram)...

---

### Post by sudodus on 2019-12-15
If you want a 32-bit Ubuntu flavour [for Intel/AMD PCs] that will be fully supported after April 2021, there is only Ubuntu Server, that you can get directly. You can create Ubuntu Desktop from the 32-bit [FONT=Courier New]**mini.iso**[/FONT] file, but I think it is a bad idea because

- standard Ubuntu Desktop has a desktop environment that is too heavy for old 32-bit computers
- 32-bit versions of some application programs are no longer supported (developed/maintained)

So if you intend to use your old computer after April 2021, I think it is a better idea to get another linux distro, a distro with a 32-bit version that is still developed and maintained, and where there should be a set of application programs that are also fairly well developed and maintained.

- The security aspects are particularly important. You should not run a distro and application programs, that lack security updates.

Debian is a 'full size' linux distro that still develops and maintains 32-bit versions.

There are also some linux distros, that focus on really old computers, for example Tiny Core and Puppy Linux. 

See also the 'mega'-link [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640).

---

### Post by The Cog on 2019-12-15
I agree with sudodus. 
I am going to have to migrate several of my computers from Xubuntu to Debian in the near future. Debian is the rock that Ubuntu is bult on anyway.
I use Xubuntu on them at the moment, and as a personal choice will go for XFCE because I'm reasonably familiar with it, and know it can manage with limited memory.
I can't comment on Tiny Core and Puppy Linux, I've never tried them. They may be better or worse for you.

---

### Post by ajgreeny on 2019-12-15
Yes, Debian is probably the best way to go.

I installed Debian-10 (Buster) on an old 32bit netbook with an Atom 270N cpu, 1G ram and a 160G HDD, and whilst not fast it is definitely faster than Lubuntu was on the same machine.

I installed using the netinstall iso which you get from [https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-10.2.0-i386-netinst.iso](https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-10.2.0-i386-netinst.iso) and then during installation I chose to add the LXDE desktop to it, along with epiphany browser which is a lot faster and smaller than firefox. I could have simply added openbox as that is what I am now using on it rather than LXDE itself.

Definitely worth a try; just avoid the standard huge packages and go for smaller faster ones, eg **abiword** and **gnumeric** instead of libreoffice, and one of the much lighter image managers than GIMP.

---

### Post by CatKiller on 2019-12-15
Getting a Raspberry Pi will give you a much faster computer that uses way less power than something that old, and with far fewer headaches.

---

### Post by bernard010 on 2019-12-15
Antix-19 i386 full iso. Debian based O.S.  Needs 256 MB and up RAM. 4 GB Hard drive space.
Lubuntu still has 18.04 Bionic LTS - LXDE desktop
I have not tried Raspberry Pi
Linux Lite is now 64 bit OS. except older the version.
Their is LXLE 32 bit OS 18.04 which stays with the LTS of Ubuntu and Lubuntu   I have not tried.

---

### Post by j2ee on 2019-12-18
> **guiverc said:**
> Lubuntu 18.04 LTS is supported until 2021-April using x86/i686/i386
Xubuntu 18.04 LTS is supported until 2021-April using x86/i686/i386
Ubuntu-MATE 18.04 LTS is supported until 2021-April using x86/i686/i386
Kubuntu 18.04 LTS is supported until 2021-April using x86/i686/i386
Ubuntu Budgie 18.04 LTS is supported until 2021-April using x86/i686/i386

and there very well could be more, can be downloaded from [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) or [http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)  (where you replace the lubuntu with the flavor you want)

[http://ubuntu-news.org/2019/08/08/ubuntu-18-04-3-lts-released/](http://ubuntu-news.org/2019/08/08/ubuntu-18-04-3-lts-released/) which states

"[COLOR=#333333]**Maintenance updates will be provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Base. All the remaining flavours will be supported for 3 years.**"

[/COLOR]with the 3 years starting from release, ie. 2018-April (thus 2021-April)

FYI:   I'm using Lubuntu 18.04 LTS on a IBM Thinkpad t43 which has 1.5gb of ram, though it also has xubuntu-desktop (Xubuntu) installed too. I also have it installed on a dell latitude d610 (1gb ram)...

2020 just few days away, you think using something that will be outdated in a year is a good idea?

---

### Post by Irihapeti on 2019-12-18
BunsenLabs also looks interesting, if you're OK with Openbox. It's the new incarnation of CrunchBang.

I've switched my own EeePC 900 from Ubuntu command-line plus Openbox to Debian Buster command-line plus Openbox. I find it hard to tell the difference most of the time.

---

### Post by cpt-ankitsharma on 2019-12-21
Lubuntu

---

### Post by poorguy on 2019-12-21
**Peppermint 9 and Peppermint 10 are 32 bit and 64 bit and supported until 2023 Ubuntu 18.04 LTS underneath.**

[https://peppermintos.com/2019/05/peppermint-10-released/](https://peppermintos.com/2019/05/peppermint-10-released/)

[https://peppermintos.com/](https://peppermintos.com/)

[https://peppermintos.com/previous/](https://peppermintos.com/previous/)


**There Is also MX-19 which is 32 bit and 64 bit Debian based and works great.**

[https://mxlinux.org/](https://mxlinux.org/)

[https://mxlinux.org/download-links/](https://mxlinux.org/download-links/)

[https://mxlinux.org/wiki/system/iso-download-mirrors/](https://mxlinux.org/wiki/system/iso-download-mirrors/)


**Can't go wrong with either choice imo.**

---

### Post by j2ee on 2019-12-21
> **poorguy said:**
> **Peppermint 9 and Peppermint 10 are 32 bit and 64 bit and supported until 2023 Ubuntu 18.04 LTS underneath.**

[https://peppermintos.com/2019/05/peppermint-10-released/](https://peppermintos.com/2019/05/peppermint-10-released/)

[https://peppermintos.com/](https://peppermintos.com/)

[https://peppermintos.com/previous/](https://peppermintos.com/previous/)


**There Is also MX-19 which is 32 bit and 64 bit Debian based and works great.**

[https://mxlinux.org/](https://mxlinux.org/)

[https://mxlinux.org/download-links/](https://mxlinux.org/download-links/)

[https://mxlinux.org/wiki/system/iso-download-mirrors/](https://mxlinux.org/wiki/system/iso-download-mirrors/)


**Can't go wrong with either choice imo.**

Need to reinstall the MX once there is major Debian upgrade, doesnt make any sense.

---

### Post by Skaperen on 2019-12-24
i do have an old computer.  but i don't really need to use it.  so, i'm thinking to give it to my niece.  i would want something to be on it ready to rock and roll.  but i won't spend more then $25 on it.  so i'm watching this thread.  she's a very bright girl who just turned 13.  i figure she could learn to use LXDE or XFCE depending on what the best answer is for a light-weight, secure, 32-bit, distro that will still be supported for a few more years.

---

### Post by guiverc on 2019-12-24
I personally wouldn't use anything downstream of Ubuntu built on 'universe' packages beyond when they are EOL on Ubuntu, ie. 18.04 LTS reaches EOL in 2021-April for most 'universe' packages (Ubuntu Studio packages are already EOL as it wasn't a LTS; extended support is provided via PPA until 2021-April).  *I bet downstream minty releases don't pick up the slack of Ubuntu no longer maintaining 'universe' packages they rely on.  For anyone reading this, use `ubuntu-support-status` to check your own support status. *

if you didn't want Lubuntu/Xubuntu - I'd more likely go upstream to debian.

@Skaperen
I wonder how useful a x86 (32-bit) laptop will be for someone that age though (13). They are likely to have other kids around looking at it, expecting touch-screen, wanting to load this & that, and will find it slow. I fear they'd likely *rubbish* it and could turn the bright girl off it.  Yes it would be useful for coding projects, if the girl is interested in that, but I suspect most will want to search the web, social media, youtube & many sites that expect 4gb+ of ram.  Yes I can do those things on my old x86 laptops, but they can be a little slow.

I would pick between XFCE & LXDE by what it'll be used for.  LXDE is lighter yes, but if you're using many GTK+3 programs the lightness is wasted and often XFCE appears better (if not the same; it's very close).

If both Xubuntu, Lubuntu are easy to install & work on the machine *out of the box*, provide it with one installed, and thumb-drive(s) (or DVDRs if you still have some) so she can install & try the other and decide for herself.  I suspect the learning experience of installing will help her to 'own' the device, and will help with peer-pressure from other kids *[possibly; of course note I'm no expert*] 

The other option is to install both; choose at login which DE she wants to use. I do this myself, though it's not without it's costs (more bandwidth used for upgrades, more crowded menus & some DEs group programs differently; eg. `evolution` [MUA] is internet to me, not a office tool (despite it's calendar/scheduling/.. functions)...

---

### Post by bunny9000 on 2019-12-25
2GB DDR2 RAM costs 10$ on ebay. Then you can easily use ubuntu mate or lxde without worrying about the ram issue.

---

### Post by j2ee on 2019-12-26
> **bunny9000 said:**
> 2GB DDR2 RAM costs 10$ on ebay. Then you can easily use ubuntu mate or lxde without worrying about the ram issue.

How about after buying it, find out it is a $1 fake ram from China doesnt even work, and then cannot find the seller, 10 dollars and effort total lose.

---

### Post by j2ee on 2019-12-26
> **bunny9000 said:**
> 2GB DDR2 RAM costs 10$ on ebay. Then you can easily use ubuntu mate or lxde without worrying about the ram issue.

Mate and lxde 32 bits stop having update after like 365 days, you ask someone to use it?

---

### Post by Skaperen on 2019-12-26
yeah, RAM is cheap!  and fake RAM is even cheaper!  if the deal is too good to believe, don't believe it.

the old computers can only understand RAM up to a limited size.

@guiverc
i think she has her eyes on my 16 GB laptop.  but i think it's better she have SSD and this laptop has spin drives.  OTOH, i have my own aging eyes on a 128GB 4K laptop with 4TB of SSD.  maybe we'll just make this netbook into a portable music machine to share around.  if i find a nice FOSS jukebox GUI i might go for it.

---

### Post by j2ee on 2019-12-27
My old laptop has 2gb ram and I just update the topic.

---

### Post by mörgæs on 2019-12-27
> **j2ee said:**
> Mate and lxde 32 bits stop having update after like 365 days, you ask someone to use it?

Yes. All the standard Buntu releases are born with around 270 days so 365 (well, actually it's closer to 400) is a luxury.

---

### Post by j2ee on 2019-12-27
> **mörgæs said:**
> Yes. All the standard Buntu releases are born with around 270 days so 365 (well, actually it's closer to 400) is a luxury.

Then what do I do after 400 days and out of update?

---

### Post by sudodus on 2019-12-27
Install another linux distro, the best alternative at that time :-)

Edit: This is particularly easy, if you keep your data (documents, pictures, music, video) in a separate **data partition**, that you can keep untouched when you install new operating systems.

---

### Post by wolftrax on 2019-12-27
arch linux or Debian.   both supports 32 bit .

---

### Post by j2ee on 2019-12-27
> **mörgæs said:**
> 
Edit: This is particularly easy, if you keep your data (documents, pictures, music, video) in a separate **data partition**, that you can keep untouched when you install new operating systems.

Then why dont I just choose a non ubuntu distro now?

---

### Post by j2ee on 2019-12-27
> **wolftrax said:**
> arch linux or Debian.   both supports 32 bit .


arch linux is too complicated

---

### Post by Irihapeti on 2019-12-27
> **j2ee said:**
> Then why dont I just choose a non ubuntu distro now?

No reason at all - go for it if it works for you.

You could look at Debian or CentOS. I have Debian on my EeePC900 (as mentioned earlier) and I just might try CentOS on an external disk and see what happens.

---

### Post by kurt18947 on 2019-12-28
> **j2ee said:**
> arch linux is too complicated

Isn't Manjaro an easier to use Arch? You could look at Distrowatch if you haven't, see which distros offer 32 bit.

---

### Post by j2ee on 2019-12-28
> **kurt18947 said:**
> Isn't Manjaro an easier to use Arch? You could look at Distrowatch if you haven't, see which distros offer 32 bit.

I install Manjaro last night and it is really good. Just little bit update issue and I can google all answers in its forum. I tried Debian but I need to manually install display and wifi drivers, I couldnt figure out how to install that old ATI driver for gnome. Manjaro installation was so smooth and easy, the performance is good too even with 2006 laptop. I could run Debian with KDE but it looks so bad, the login screen look like any random person just used 5 minutes to create it. Manjaro look pro.

---

### Post by kurt18947 on 2019-12-29
> **j2ee said:**
> How about after buying it, find out it is a $1 fake ram from China doesnt even work, and then cannot find the seller, 10 dollars and effort total lose.
I guess that's a risk but I've bought memory off Ebay and had no problems. I usually buy pulls/used from US based sellers and make sure the seller accepts returns. As soon as possible after receiving it I install it and run memtest for at least a couple hours. If a seller has at least 20 transactions - more is better - I feel it's worth the risk.

---

### Post by j2ee on 2019-12-29
> **kurt18947 said:**
> I guess that's a risk but I've bought memory off Ebay and had no problems. I usually buy pulls/used from US based sellers and make sure the seller accepts returns. As soon as possible after receiving it I install it and run memtest for at least a couple hours. If a seller has at least 20 transactions - more is better - I feel it's worth the risk.

I agree buying second hand ram from a good rating seller is a solution, especially some ram brands have life long warranty. But for my T60 notebook, there is 1GB ram vs 2 to fill out all slots already. It is such an old notebook that I don't want to spend any money on it especially its cpu only supports 32bits so 3GB ram is max anyway. It still runs pretty smooth with manjaro and normal HDD.

---

### Post by Harvey_Artz on 2020-01-05
> **cpt-ankitsharma said:**
> Lubuntu

Agreed, [https://lubuntu.net/](https://lubuntu.net/) , 2nd choice Debian. A ubuntu distribution (lubuntu) would probably be better for a newer user.

I've tested many distributions, mostly as virtual machines, and lubuntu takes less ram after boot, which leaves you with more to use for apps, and it runs very efficiently.

---

### Post by guiverc on 2020-01-06
> **Harvey_Artz said:**
> Agreed, [https://lubuntu.wrong/]("https://lubuntu.net/") , 2nd choice Debian. A ubuntu distribution (lubuntu) would probably be better for a newer user.

I agree with you, though I'd suggest downloading from a Lubuntu/Ubuntu site.  If you can't remember the official site I'd recommend [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)  (ie. ask ubuntu.com which is the official site instead of a search engine).

---

### Post by kevdog on 2020-01-06
I luv luv Arch however I don't think it support 32 bits anymore.

I can't believe I'm the only one saying this but honestly I'd recommend retiring your hardware.  1-2Gb of RAM? -- Honestly I don't think your are going to be happy with the performance and the energy requirements of the machine are likely to be high. Call me an old man -- I used to repurpose a lot of older hardware and over the years I grew tolerant of the process less and less.  Just because something like installing Debian on the device "CAN BE DONE", doesn't mean it "SHOULD BE DONE".  Retire the hardware and look for something a little bit more modern.

---

### Post by mörgæs on 2020-01-06
Lubuntu dot net is best forgotten, and [www.lubuntu.me]("http://www.lubuntu.me") should have all the attention possible.

Harvey_Artz and Guiverc, would you be OK with editing your posts so there is no link to the net domain?

---

### Post by guiverc on 2020-01-06
> **mörgæs said:**
> and [www.lubuntu.me]("http://www.lubuntu.me") should have all the attention possible.

Thank you :)

---

### Post by jmartin9 on 2020-01-20
I have had several older machines, and have experimented with Puppy (and also Quirky and a 32-bit version of EasyOS), TinyCore and CorePlus, Lubuntu and AntiX.  for various reasons I've landed on AntiX, but I understand that it and MX are both based on Debian and descended from the now defunct Mepis.

I'm using Lubuntu 18 on an old machine that hosts an old SCSI document scanner - but I find it really slow and may change as Lubuntu is already phasing out 32 bit support.  So, that machine may get retooled as AntiX or MX.

---

### Post by Artim on 2020-01-20
MX is lots heavier than antiX, even if you add Xfce desktop onto antiX.

---

### Post by him610 on 2020-01-21
I have 32 bit Xubuntu 18.04 installed on an Acer Aspire One ZG5 (bios: 2008) that was upgraded from 512 MB to 1.5 GB RAM. Operates fine; don't use it much anymore though. It used to be my main travel computer for years. Hate to give it up, but one of these days I will.

---

### Post by CorporateMonkey on 2020-01-21
I was just wondering, wouldn't Debian be the better choice for a such old device?

---

### Post by him610 on 2020-01-22
> ...wouldn't Debian be the better choice for a such old device?
There's nothing wrong with trying.

---

### Post by hurtstotalktoyou on 2020-01-23
> **CorporateMonkey said:**
> I was just wondering, wouldn't Debian be the better choice for a such old device?

For an advanced user, perhaps so.  But for a user asking a question like this in ubuntuforums, almost certainly not.  I mean, I'm not a newbie anymore since I've been using linux for over a decade.  But Debian still gives me chills.  I stick to ubuntu-based distros.

A while back I used Lubuntu 18.04 LTS on an old 32-bit Celeron laptop with 2GB RAM, and it worked fine.  Maybe there's an even lighter-weight ubuntu-based distro that would be better?

---

### Post by j2ee on 2020-02-10
If I install the latest 32 bits Ubuntu, is it safe without updates or upgrades in future? Will keep using it for years after support expires.

---

### Post by wildmanne39 on 2020-02-10
Not if you connect it to the internet, no operating system is safe without updates if connected to the internet.

---

### Post by j2ee on 2020-02-15
Sad that windows 10 has 32 bits version

---

### Post by guiverc on 2020-02-15
I've already given my thoughts re: Lubuntu and Xubuntu  (*I was testing both of them with old x86 machines until they stopped spinning ISOs back in Dec-2018 or the 19.04 cycle*). They were both pretty good on single-core laptops with 1GB of ram.

Not all 32-bit laptops though equal.  Debian and Ubuntu may class all x86 as i386, but upstream Linux kernel distinguishes between i386, i486, i586 & i686; which at times is important.I did a far bit of testing of Lubuntu 18.04.4 LTS on various x86 things (thinkpad t43, dell latitude d610, hp dx6120 etc (pentium m/4/d; minor Xub & Kub testing too).

 I tried booting up Lubuntu 18.04.4 LTS on a thinkpad r50p (*usually ignored as it's always on*), but Lubuntu 18.04 wouldn't boot to my surprise!  Whilst it too had a pentium M processor like the d610/t43/.., it had only a i586 class cpu & thus couldn't boot the 18.04.4 LTS flavors :(    (*I hadn't used it in testing in ages; it had >560 days uptime so it's been awhile since I tried booting anything on it; power in the street was disconnected longer than it's battery could stand*)

Anyway, I booted Debian 10/buster LXQt & then XFCE (with non-free) on the r50p, and it's great on it.  Debian still has support for i586 too :)   (*I knew it'd run debian old-old-stable (8) as it's run that for years; but it's EOL is approaching rather fast)*

*I don't see Debian as much different to Ubuntu; esp. since the ISOs with non-free have been available; but having started with Debian I probably don't notice the differences (there are just many situations where Ubuntu is easier and I'll skip Debian, though other circumstances I'll pick Debian too)*

---

### Post by j2ee on 2020-02-15
> **guiverc said:**
> I've already given my thoughts re: Lubuntu and Xubuntu  (*I was testing both of them with old x86 machines until they stopped spinning ISOs back in Dec-2018 or the 19.04 cycle*). They were both pretty good on single-core laptops with 1GB of ram.

Not all 32-bit laptops though equal.  Debian and Ubuntu may class all x86 as i386, but upstream Linux kernel distinguishes between i386, i486, i586 & i686; which at times is important.I did a far bit of testing of Lubuntu 18.04.4 LTS on various x86 things (thinkpad t43, dell latitude d610, hp dx6120 etc (pentium m/4/d; minor Xub & Kub testing too).

 I tried booting up Lubuntu 18.04.4 LTS on a thinkpad r50p (*usually ignored as it's always on*), but Lubuntu 18.04 wouldn't boot to my surprise!  Whilst it too had a pentium M processor like the d610/t43/.., it had only a i586 class cpu & thus couldn't boot the 18.04.4 LTS flavors :(    (*I hadn't used it in testing in ages; it had >560 days uptime so it's been awhile since I tried booting anything on it; power in the street was disconnected longer than it's battery could stand*)

Anyway, I booted Debian 10/buster LXQt & then XFCE (with non-free) on the r50p, and it's great on it.  Debian still has support for i586 too :)   (*I knew it'd run debian old-old-stable (8) as it's run that for years; but it's EOL is approaching rather fast)*

*I don't see Debian as much different to Ubuntu; esp. since the ISOs with non-free have been available; but having started with Debian I probably don't notice the differences (there are just many situations where Ubuntu is easier and I'll skip Debian, though other circumstances I'll pick Debian too)*

All ubuntu based disto with 32bits will be out of support and update very soon so I would not cobsider. I will try Debian iso witj non free, had hard time tried to install wifi driver and display driver.

---

### Post by him610 on 2020-02-15
> **bunny9000 said:**
> 2GB DDR2 RAM costs 10$ on ebay. Then you can easily use ubuntu mate or lxde without worrying about the ram issue.
Could be that he is at RAM limit now. RAM limitation is determined by CPU/MB constraints.

---

### Post by him610 on 2020-02-15
There is also Debian Stretch with Raspberry Pi Desktop that can be downloaded here, [https://www.raspberrypi.org/downloads/raspberry-pi-desktop/]("https://www.raspberrypi.org/downloads/raspberry-pi-desktop/")
The Raspberry Pi Desktop (for x86 machines) has a logically conceived desktop - easy to setup and configure. Don't know if they have a version based on Buster yet. 
I will probably install it on my atom-powered Acer netbook when Xubuntu 18.04 (x86) support is no more next year.

Added 26feb2020: Yes, the latest release is based on Buster

---

### Post by Portaro on 2020-02-26
Based in my latest tests I think that the best distro in 32 bits that I test in live mode in my computer of 2004 are :
Slackel [http://www.slackel.gr/forum/about.htm](http://www.slackel.gr/forum/about.htm)
Debian Dog [https://debiandog.github.io/doglinux/zz03busterdog.html](https://debiandog.github.io/doglinux/zz03busterdog.html)
Minino Galpon [https://minino.galpon.org/en](https://minino.galpon.org/en)
Wattos [https://planetwatt.com/new/index.php/downloads/](https://planetwatt.com/new/index.php/downloads/)
Puppy Linux [http://puppylinux.com/](http://puppylinux.com/)

There are a good reason to test Slackel is very stable, the Slackware kernel have a more solid method of upgrade (more time of tests) the kernel have a long time of corrections and the software added compared with other Distros is older. In one word Slackware is very stable and because he uses a long term of development probably is a better distro type to addapt on a older machine.

---

