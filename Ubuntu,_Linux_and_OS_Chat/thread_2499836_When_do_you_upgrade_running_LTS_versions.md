---
title: "When do you upgrade running LTS versions"
date: 2024-08-12
forum: Ubuntu, Linux and OS Chat
---

### Post by sports fan Matt on 2024-08-12
When do you upgrade to a new version of the operating system?  I tend to wait a month or more between LTS releases.

---

### Post by Irihapeti on 2024-08-12
For me, it depends on what the OS is for. For most of the ones at home, which aren't mission-critical, I might even upgrade prior to release. With my main box, I'll usually wait until release, though that depends on stability. With my VPS, I usually hang back until the first point release, which is about 3 months out.

---

### Post by guiverc on 2024-08-12
I don't have a set time, it'll vary on *box* (*hardware*) and what I use that *box* for, as I had many boxes.

My *primary* box is dual boot; my default system runs *development* thus is currently *oracular*, with the dual boot choice my LTS, which currently is 24.04 so a quick look tells me (*I thought it was still on jammy/24.04*)

```

guiverc@d7050-next:~$   cat /lts/etc/os-release 
PRETTY_NAME="Ubuntu 24.04 LTS"

```

If I recall [now] correctly; I recently (*one month ago*) had an issue on my *dual boot OS*, and decided to be lazy and *fix* it via *non-destructive re-install*, thus the 22.04/*jammy* system was moved to 24.04 that is there now (*non-destructive re-install allowed me to achieve release-upgrade **and fix issue at same time*), but **normally** that system wouldn't be *release-upgraded* until late this year or early 2025 (*ie. 6-9 months after LTS release*).

A *media player* I use heaps is running 24.04, but it was only installed last year (*running Debian for more than a decade before that*) and I opted to install using 23.10 media, as I want to run a LTS release & saw no reason for an older 22.04 on that install (*and the upgrade from 23.10 to 24.04 is far easier than LTS to LTS*).

I have a *media player* in my lounge that'll be running 22.04; but I don't often use it, so I'm not worried about it (*that install was running EOSS for some time, before I release-upgraded it a number of times to get to the now 22.04*).  

I also have two systems that are still running 20.04 LTS as those devices are *low-resource* old boxes (*one has only 2GB of RAM*) where the older *software stack* tends to perform better, so I'm in no hurry on upgrading them. I'll *release-upgrade* them when I see a need, or benefit to it (*though often non-destructively re-install thus skipping many LTS cycles*).

---

### Post by Tadaen_Sylvermane on 2024-08-12
I'd like to think I wait till the next LTS is thoroughly stable, a year or two later. No real rush as long as the one I'm using is still supported. That being said I haven't got the self control. My aforementioned plan holds out for a couple weeks then I do it manually the hard way because the official upgrade isn't supported yet.

---

### Post by him610 on 2024-08-13
I can't seem to recall what I did in the past, but about a month after first point release seems about right to me with no mission critical devices.

---

### Post by Rubi1200 on 2024-08-13
I usually wait 6 months after the first release.

Will upgrade my systems in October.

---

### Post by lammert-nijhof on 2024-08-14
Usually I run the dev edition, just out of curiosity.  I run all my Linux and Windows releases in a VirtualBox VM.  When April approaches, I start to add the apps I normally use and on the release date I switch from the older 22.04 LTS VM to the new 24.04 LTS VM.  If needed I can always run something in 22.04 LTS VM again.  This year it caused a problem for the first time in say 10 years, because Ubuntu 24.04 LTS stopped booting as a Virtualbox VM completely in August.  Since April it booted, but sometimes only the second boot worked, but now no boot works, only via the recovery mode.  So I use 22.04 LTS again :(   I did produce a bug report, that has been confirmed.  I think it is a leftover from the chaos during the XZ bug handling, they also delayed the coming 24.04.1 release with 2 weeks. 

You don't not need expensive hardware for moving to VMs, my HW did cost me $349 in April 2019.  It has a Ryzen 3 2200G; 16GB DDR4; 512 GB nvme-SSD (3400/2300 MB/s) and I reused a 2TB HDD and an 128GB sata-SSD as cache for the HDD.  The Host OS is a minimal install of Ubuntu 24.04 LTS, supported by VirtualBox and I use OpenZFS to store all VMs and Data.  The firewall of Host and VMs are all closed for inbound traffic. For data exchange between VMs I use the shared folders of VirtualBox.  The system has >60 VMs often very old ones, but for daily use I use 6 VMs stored on the nvme :
- Xubuntu 24.04 LTS for Social Media, the only VM with some open ports.
- Ubuntu 16.04 ESM for banking.  It is used exclusively for banking and has been encrypted by VirtualBox. It runs the newest snaps from Firefox and LibreOffice (Calc)  :) :)
- Ubuntu Budgie 24.04 LTS for Multimedia.
- Ubuntu 22.04 LTS for try outs of new stuff and other experiments. 
- Windows 11 Pro, you never know, when you might need it.
- Windows XP Home to play the wma copies of my CDs and LPs with WoW and TrueBass effects.  Note that the VM has been installed and activated in March 2010 and it survived 2 VBox owners; 3 desktops and 4 CPUs :) :)

The fastest VM boot time is 7 seconds for Xubuntu and the slowest is Windows 11 in 45 seconds, all Ubuntu flavors boot within 12 seconds and XP Home (1 core) in 25 seconds.  Xubuntu is always loaded, and Ubuntu 16.04 and Windows XP I also use frequently. Windows 11 I boot once per week for the weekly update :)

---

### Post by Shibblet on 2024-08-14
The ultimate form of safety would be 2 years in-between incremental releases of the RTS.

i.e. 20.04.1 upgrade to 22.04.1

In other words, wait for the LTS .1  ;-)

---

### Post by werewulf75 on 2024-08-15
I prefer waiting 1-2 years before upgrading at a minimum, downloading the new version around 1 year after release. Sometimes wait till current version gets close to end of standard support.

---

### Post by TheFu on 2024-08-16
It depends on the software on the machine already.  Sometimes it takes 1-2 yrs for some software to be ported to the "new" LTS, so I'll wait at least that long.  Sometimes I only switch LTS when there's less than 6 months left of standard support time remaining.  So for 20.04 ... I'll move to 22.04 or 24.04 around January 2025.  

For me, stability is more important than "new".  I did my "chasing new" in the 1990s.  Back then, getting the newest stuff was required for a working system. That isn't really been a problem for my needs since 2010.  I'd still be running Ubuntu 10.04 today if it was supported.  That was the last Canonical release that "felt" right - felt like Linux should, IMHO.  Of course, there are lots of new features that I love, but there are lots of new features that seem to break things for little payback too.

I do play with the newest releases for a few days/weeks when they come out to see if they are phenomenal.  Canonical has decided to make the defaults new stuff rather than just let people interested in testing choose it.  They learned that 99% of the users stick with their default and not enough people were testing the new, not-ready-for-production code.  Many people are captive audiences, so they gain more testers, get notified of more bugs, by doing this and people will not switch distros.  There's something to be said for getting more free testing, I suppose.

The key for me is to always run a release that is under standard support and upgrade/migrate (I seldom believe newer releases are any upgrade) to newer release before support ends.

---

### Post by werewulf75 on 2024-08-16
> **TheFu said:**
> It depends on the software on the machine already.  Sometimes it takes 1-2 yrs for some software to be ported to the "new" LTS, so I'll wait at least that long.  Sometimes I only switch LTS when there's less than 6 months left of standard support time remaining.  So for 20.04 ... I'll move to 22.04 or 24.04 around January 2025.  ...

For me, stability is more important than "new".  I did my "chasing new" in the 1990s.  Back then, getting the newest stuff was required for a working system. ...

The key for me is to always run a release that is under standard support and upgrade/migrate (I seldom believe newer releases are any upgrade) to newer release before support ends.
Spot on! And I'd say much the same about hardware, too. For both, "If it ain't broke, don't fix it" makes sense.

---

### Post by Shibblet on 2024-08-16
> **werewulf75 said:**
> Spot on! And I'd say much the same about hardware, too. For both, "If it ain't broke, don't fix it" makes sense.

I just found my old MSI Wind (10" Netbook) running Ubuntu 10.04 on it!  Still works GREAT!

---

### Post by werewulf75 on 2024-08-16
> **Shibblet said:**
> I just found my old MSI Wind (10" Netbook) running Ubuntu 10.04 on it!  Still works GREAT!
I'm getting very envious now! ;) I'd love to go back to running around the last Unity LTS release, got space on one machine but alas, lost all my old, pre-2018 install archives when the disk they were on died horribly. :( Still, at least have the current Unity running nicely.

---

