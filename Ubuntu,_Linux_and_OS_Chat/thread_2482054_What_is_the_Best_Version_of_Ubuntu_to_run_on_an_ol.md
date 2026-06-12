---
title: "What is the Best Version of Ubuntu to run on an older Windows 8.1 Machine"
date: 2022-12-17
forum: Ubuntu, Linux and OS Chat
---

### Post by brevardo2 on 2022-12-17
I have an older Windows Computer which is about 8 years old. It has an Intel Processor 3.20 GHz , 16.0 GB installed RAM , System type: 64 bit operating system , x64 based processor and is running Windows 8.1 and as you have probably heard, Microsoft will be ending Support and updates at the beginning of 2023. I am ready to install Ubuntu on this machine. However, I did attempt to install a Ubuntu version once before and it seemed like it just never ran right and crashed frequently. I have had great success with Ubuntu in the past on old Lap tops. Do you think I should install the newest version of Ubuntu on this machine or do you feel I would be better off going with an older version since this machine is about 8 years old? Your recommendations are greatly appreciated.

---

### Post by VMC on 2022-12-17
I've always enjoyed **Xubuntu** on my old PC's.

---

### Post by TheFu on 2022-12-17
If you aren't an expert, the normal advice is to install the latest LTS release, which is 22.04 and use a light DE, which would be XFCE or LXQt.  If you have a Core i3 or better CPU, Mate will run well too.  It is only the Celeron and some low-end Pentiums that really need the lightest DEs.

So, that would be
* Xubuntu
* Lubuntu
* Ubuntu-Mate

However, you need to know that the LTS versions of those releases get 3 yrs of support, so in 24.04, you **must** move to the next LTS.
Best to avoid non-LTS releases. You can google for what is and isn't an LTS.  Non-LTS releases have 9 months of support from the release date, which is typically 6 months of support for most people who don't want to live on the bleeding edge and allow a month or 2 for initial bugs to be addressed.

And always remember that Linux isn't Windows, so if you hope for a MS-Windows replacement, you will be disappointed, just like when I tried to use a MacOS machine with my Linux/Unix background and was terribly disappointed.  Proper expectations and knowing there is a multi-year learning curve will serve you well.  After all, you didn't learn MS-Windows immediately either and this a completely different OS from the inside out.

BTW, around here, "old" means 20 yrs.  Best to just say the model of the CPU that the command 'inxi -b' will show for people to quickly see what type of performance you have.  I have a Core i3-5015U in a laptop and a Core i5-8250U in another.  Those numbers tell people a great deal about the performance without even looking up the specifics.  One is a 5th generation and the other is an 8th generation.  10th and 11th generation Core i3 computers are like Core i5 from just a few years earlier. It is kinda crazy how fast computers have become over the last 14 yrs - really since the Core2 Duos first came out.

---

### Post by guiverc on 2022-12-17
Ubuntu products don't have version numbers.

The have release dates; for example the Ubuntu 2022-April release is called Ubuntu 22.04 LTS (ie. 2000 is subtracted from the year and the format of the release is *year.month*).   The *year.month* products come out in April (.04) and October (.10).

There are also some *specialist* products that use the *year* format with maximum one per year, eg. Ubuntu Core 22 (*it came out in July 2022, as a specialist flavor of 22.04 Server, but with only a single release per year no month is required*).  This format also reminds you this product cannot use *deb* packages (ie. no `apt install` will work).

FYI:   I'm using a 2008 dell desktop; c2q-9400 with 8GB of RAM, and it'll run all.  


 Personally I'd decide more on what applications you'll use, and your tastes to decide which *flavor* you run, and not base it on the hardware (*except if really underpowered; eg. I really consider the hardware when using 2003-2004 made laptops with 1GB RAM & pentium M*).

I'd also consider how long you'll use the install for (*non-LTS releases have 6-9 month cycles between release-upgrades, LTS have 3-5 years*), though some 3rd party apps are built only for LTS or *long term support* releases so that can make you sway towards LTS.  Non-LTS & regular *release-upgrades* will always have the newer software, but do you mind *release-upgrading* every 6-9 months?  Again this isn't related to hardware at all, but your usage & plans for your machine.

Addendum:  I'm involved with QA (*Quality Assurance*) and on some old GPU/video cards; I've experience a *more pleasant* experience with the lighter desktop, and especially fewer graphic *glitches*. LTS releases have kernel stack choice; which is an easy fix for some LTS releases, but an older release may suit some older hardware (*here I'm thinking of issues that can occur with some cards from 2005-2007; somewhat older than you seem to imply*).  If you want a later release, in my experience Xubuntu is least impacted by these *glitches* too.

---

### Post by ian-weisser on 2022-12-17
The various releases and flavors of Ubuntu include a risk-free live "Try Ubuntu" environment specifically so you can test different possibilities before committing to an install.

And installs are easy, so if you change your mind you can simply install something else.

Try a bunch and decide for yourself which is best.

---

### Post by agentl074 on 2022-12-19
While Linux Mint is a separate project, I use Linux Mint 20.3 Cinnamon on this Windows 7 era machine with great results -- like a new machine. For newer machines, I would highly recommend the standard Ubuntu since it has the most modern feel -- which Mint lacks.

---

### Post by bernard010 on 2022-12-29
I will have to agree with Post #5.
Your computer has enough processor and ram for Ubuntu and flavors.
Depends what you need as an OS. 
Ubuntu Studio is for Sound and Graphics, Ubuntu is a good workstation.

---

### Post by grahammechanical on 2023-01-01
> Do you think I should install the newest version of Ubuntu on this  machine or do you feel I would be better off going with an older version  since this machine is about 8 years old?

As pointed out in an earlier post, each version of Ubuntu has a period of time during which it will receive security updates. An eight year old version of Ubuntu will have reached the end of it support life.

Your system has plenty of memory and a reasonably powerful CPU. What Intel CPU is it? We should also consider the video adapter. What model is it? How much video memory does it have? Ubuntu uses the Gnome Desktop Environment which requires a reasonably powerful video adapter. The flavours of Ubuntu use other desktop environments that require a lower specified video adapter.

Regards

---

### Post by oldfred on 2023-01-01
Links to various flavors.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I used Ubuntu with fallback gui which was another lightweight configuration.
But now use Kubuntu which is more of a mid-weight flavor.

For the cost of a bit of time you can download the ISO of any flavor and try it in live mode.

---

### Post by oldos2er on 2023-01-01
Whichever version you decide on be sure it's still supported. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Tadaen_Sylvermane on 2023-01-01
Another thing to note if I may.

Just because it may be "old" doesn't mean it's a slouch and can't do anything decent. My current desktop is an i7 3770 non k with 16gb of ram. It still runs everything I throw at it without breaking a sweat to this day with the exception of a few of the newest games. Even then I think my RX570 is holding me back there more than the rest of the machine. Thats a 3rd gen i7. They are on the 13th gen now I believe. Go by raw specs, not age when making a choice or looking for assistance. Will be easier I'd think.

---

### Post by #&amp;thj^% on 2023-01-01
> **Tadaen_Sylvermane said:**
> Go by raw specs, not age when making a choice or looking for assistance. Will be easier I'd think.

+1 and always.

---

### Post by agentl074 on 2023-01-16
Update -- apparently, the latest Ubuntu will work just fine so long as you meet the recommended requirements -- but I would suggest at least 8GB RAM for comfortable usage instead of 4.

---

### Post by SeijiSensei on 2023-01-17
I've run Kubuntu successfully on many machines, some older than yours. It looks more like Windows than some other Linux variants. I installed it on the laptop of a friend who had never used Linux before. He had no problems doing simple things like web and mail.

[https://cdimage.ubuntu.com/kubuntu/releases/22.04/release/kubuntu-22.04.1-desktop-amd64.iso](https://cdimage.ubuntu.com/kubuntu/releases/22.04/release/kubuntu-22.04.1-desktop-amd64.iso)

---

### Post by monkeybrain20122 on 2023-01-23
The specs sound very good. Any latest flavor of Ubuntu would work, I had Ubuntu 20.04 on a netbook just as old but with half the ram. The netbook was busted finally because of hardware problems in 2022 but it was working great before then. It had Windows 8 on it when I got it years ago, any *buntu is lightning fast comparing to that.

---

