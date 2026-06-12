---
title: "If not Ubuntu ~ which distro?"
date: 2023-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by sports fan Matt on 2023-07-08
If ya'll don't use Ubuntu (with the many flavors) what distro do you use?  So far I have Mint running on two laptops for the aesthetics. I like the look of Vera and while I CAN change the layout, I feel like Mint suits me better so far.  Anyone feel the same about snaps?

---

### Post by Rubi1200 on 2023-07-08
I don't think there is a right or wrong answer to this (at least I hope not). I have used many distros over the years, too many to recall at the moment.

I would say that right now one of my favorites is Bodhi Linux, which I have running on a 1GB Intel Atom netbook.

I also like using ArcoLinux, Fedora, Debian, and I keep coming back from time to time to the very first distro I ever tried, Knoppix.

---

### Post by guiverc on 2023-07-08
I don't think I get through a single day without touching at least two operating systems.

Most of my time each day will of course be spent on my *primary desktop*, which is dual boot, and contains Ubuntu *development* release (ie. *mantic* currently), and has  the dual boot option being the current LTS (*ie. jammy or 22.04*).

Today, and in fact most of the last almost two weeks I've been using the Ubuntu Desktop (GNOME), however my install was a Lubuntu system (ie. LXQt) initially, on which I added Xubuntu-desktop (Xfce), the Ubuntu-desktop (GNOME) that I'm currently using.. ie.  is a multi-desktop system (*multiple DEs or flavors co-exist on the same install*)

The machine I'm using now, that I use 1-3 hours a day runs Debian *testing* (ie. *trixie* currently). I'm logged into KDE Plasma currently, though its not my usual desktop (*this system is actually more bloated than my primary machine, with >20 different DE & WM options at login to choose from*).

The machine I usually touch *last* in the day is another Debian system, but it's a *stable* system, but I've also used a laptop today for awhile and it was a *jammy*/22.04 system (*using Lubuntu from memory; but I consider Lubuntu a Ubuntu system anyway**; it'll have multiple desktops installed too, most my systems are*)

I'm very much stick to Ubuntu & Debian for what I use (*I have other systems, but they're rarely used*). I started using Debian GNU/Linux before the Ubuntu project actually started; though didn't start using Ubuntu until 2010 - so was rather late to Ubuntu.

(*I've used RedHat/Fedora awhile, was using OpenSuSE for many years - Ubuntu replaced those.. and have always had a thumb-drive with Knoppix on it !*)

---

### Post by lpoli on 2023-07-08
After years of testing and deploying many distros (mostly Debian based, and FreeBSD), I've found a solid solution in Mint with XFCE for desktop and Ubuntu Server for this purposes.

The reasons, respectively, are because of the styling and the stability and support.

---

### Post by TheFu on 2023-07-08
> **sports fan Matt said:**
> If ya'll don't use Ubuntu (with the many flavors) what distro do you use?  So far I have Mint running on two laptops for the aesthetics. I like the look of Vera and while I CAN change the layout, I feel like Mint suits me better so far.  Anyone feel the same about snaps?

I separate the idea of distro from the gui.  The GUI is just another program to be loaded, configured, selected.  The OS is not the GUI.

Most of my systems are running ubuntu server. No GUI.  Some of these are VMs while others are LXC containers.

Some systems run debian without any GUI.

Some systems run Ubuntu Server with a light window manager setup. I got tired of the bloat from all the DEs. They load 50 huge GUI programs that I'll never use, seldom the GUI programs I prefer.
My main desktop is a Linux Mint 21.1 with the GUI removed, rather has fvwm installed as the Window Manager. It is light, fast, completely customizable and I don't have to relearn the wheel every 2 years because some GUI program manager got a hair in their **** about "new" or "change" being better.

I still remember running Linux in 4MB of RAM systems using 20MB of storage AND having a great GUI.  The idea that a system needs GB of RAM and 35GB of storage to be useful is slightly offensive.  More code means more bugs. Every programmer knows that.  If the code is 100x larger, then there are 100x more bugs.

I have great dislike of snaps, except for very specific needs, which I generally don't have. Until there is local control over the constraints applied, snaps will be something that I avoid.  This was THE primary reason I moved to Linux Mint.  IT wasn't the GUI. It wasn't dislike of APT or Canonical.  It was the strong push, nearly mandated use of snaps, that forced me to switch.

I'd hoped that lxd under Debian would be my way out. I really like lxd, but Canonical runs that project and only releases it as a snap package.  Just this week, Canonical announced they were pulling lxd back from F/LOSS and going to do development in-house.  [https://www.phoronix.com/news/Canonical-Pulls-In-LXD](https://www.phoronix.com/news/Canonical-Pulls-In-LXD)  That move is very concerning.
> The Linux Containers project announced today that the LXD project is no longer part of them but Canonical has now moved from the source repository from the LXC Git repository to under Canonical's GitHub account. The LXD website is also no longer to be on LinuxContainers.org but will be under Ubuntu.com. Canonical is also taking control of the LXD YouTube channel, LXD community forum sunset in favor of Ubuntu Discourse, and the LXD CI infrastructure will move under Canonical management. 
[https://linuxcontainers.org/lxd/](https://linuxcontainers.org/lxd/) has a different statement, but basically the same.  Seems that Canonical wants LXD under their control and might be trying to de-FLOSS it.

---

### Post by exploder on 2023-07-08
Debian 12. Problem free, stable and no snaps!

---

### Post by CharlesA on 2023-07-08
I'm running Debian on all my Linux boxes unless I specifically need Ubuntu for something.

---

### Post by Dennis N on 2023-07-08
I keep and use 4 top-tier distros on this computer (multi-booted) and only use the Gnome Desktop. There are pros and cons for each. In no particular order.

1) Fedora
2) Manjaro
3) Ubuntu
4) Debian (newly added).

---

### Post by DuckHook on 2023-07-08
I'm going to approach your question from a slightly different angle:

I've tried out so many distros over the years (decades even? yeesh!) and I like pretty much all of them. I still play with a few from time to time in either VMs or containers. I've settled on Ubuntu for all of my boxes not because it is inherently "superior", but only because of the following:

[LIST=1]
[*]I'm completely familiar with it, so it is very comfortable: like a pair of old well&#8209;loved slippers.
[*]I have come to rely on LXD which is most completely implemented and documented in Ubuntu.
[*]Because of its popularity, it is easy to find help in the form of tutorials, examples, blogs and, not least, these forums.
[/LIST]
None of these considerations are deal breakers. It wouldn't take me long to get comfortable with another distro, LXD is available in many other distros, and distros like Arch have even better technical documentation and support.

If Ubuntu should do something that really offends me, I would not find it difficult to migrate to another distro. That's one of the most valuable and wonderful aspects of the Linux ecosystem that we don't appreciate enough—that we are not locked in to any one company—unlike those poor proprietary addicts who must suffer major withdrawal pain to make such switches.

To be frank, I've never understood the overwrought, even vehement disagreements among Linux people over which distro is "better". To me it's like getting all bent out of shape about whether a Ferrari, Maserati or Lamborghini is better. Compared to driving around in a Microsoft Chevy, such disagreements are surreal.

---

### Post by lammert-nijhof on 2023-07-08
I'm from May 1945.  Ubuntu forever. My Host OS is a minimal install of Ubuntu 22.04 LTS and I run all stuff in Virtualbox VMs:

- Xubuntu 22.04 LTS for all communication apps with snaps for WhatsApp, Skype and Messenger.
- Ubuntu 16.04 ESM exclusively for banking (encrypted by VBox) running the latest stable snaps for Firefox and LibreOffice (Calc). Ubuntu 16.04 already had snap support out-of the box. 
- Ubuntu Studio 20.04 LTS for multimedia.
- Ubuntu 22.04 LTS for try-outs and experiments.
- Windows XP Home to play the wma copies of my CDs and LPs.
- Windows 11 Pro just in case :)

For distro try-outs I have the following VMs; Linux Mint, Zorin OS; Manjaro; Fedora; OpenSuse Leap and Debian 12.0. 

As a collector I have all Windows releases between 1.04 (1987) to Windows 11 Pro (2023) and all Ubuntu LTS releases from 6.06 LTS to 22.04 LTS; the first 4.10 and my first 5.04. I also try the development edition of Ubuntu and some flavors and I run the snap based immutable Ubuntu Core 22.04 prototype in a Virtualbox VM too :)

---

### Post by VMC on 2023-07-08
I have two I use right now, Ubuntu LTS and EndeavourOS-KDE. I use the eos-KDE most of the time. My Ubuntu has Snap removed completely. If It ever gets to the place that I cannot remove Snap, then I will part ways with Ubuntu. Sad since I started with Hoary Hedgehog and will really miss Ubuntu.

---

### Post by makitso on 2023-07-09
I have always enjoyed an aesthetically pleasing desktop. I was using xfce for a number of years but it took just too much time to reconfigure at each new release.  
Then I stumbled on the budgie desktop, it's clean, modern, and looks just about right straight out of the box.  Another thing that often gets overlooked, the developers are accessible on the support site.

---

### Post by gezzer2 on 2023-07-09
if i wasn't using Ubuntu 22.04.2 LTS (now completely snapless) it would be Debian but now that snaps has been --purged from 22.04 it is running smooth as silk and everything is working as it should.
just an add on my Ubuntu (pixel 3a) phone is working pretty good as well. best wishes to all ...

---

### Post by CharlesA on 2023-07-10
> **lammert-nijhof said:**
> 
- Windows XP Home to play the wma copies of my CDs and LPs.


Huh. I would have thought VLC or the like would play a wma file. I think that was the default file format of Windows Media Player.

I've ripped all my stuff to either MP3 or FLAC, but wma is a lossy format, so it's pointless to convert unless you want to lose quality.

FWIW, I still have an XP and Windows 10 VM kicking around for stuff, but they rarely get powered on.

> **gezzer2 said:**
> if i wasn't using Ubuntu 22.04.2 LTS (now completely snapless) it would be Debian but now that snaps has been --purged from 22.04 it is running smooth as silk and everything is working as it should.
just an add on my Ubuntu (pixel 3a) phone is working pretty good as well. best wishes to all ...

How did you get rid of the snaps? I've been on Debian to stay away from snaps.

---

### Post by gezzer2 on 2023-07-10
@CharlesA ... i did a minimum install setting the ssd up with 3 partitions boot/efi, /(root) and home (no swap as i have 64GB of ddr4 installed). 
i also found it best not to do any updates before removing snaps as laid out below.

then followed this ...
[https://danieliser.com/fully-remove-snap-from-ubuntu-22-04/](https://danieliser.com/fully-remove-snap-from-ubuntu-22-04/)

and this ...
[https://haydenjames.io/remove-snap-ubuntu-22-04-lts/](https://haydenjames.io/remove-snap-ubuntu-22-04-lts/)

installed firefox, gnome-software-centre, synaptic and vivaldi by CLI and then deb.

everything is now running smooth as silk and works which i didn't have with snaps.

ps. ive been using ubuntu since 'warty' (still have the install CD) then moved over to LTS where i have staid since ...

---

### Post by lammert-nijhof on 2023-07-10
> **CharlesA said:**
> I would have thought VLC or the like would play a wma file.

Most Linux music players play wma, I also use it with Rhythmbox and Lollypop. Besides for the same sample frequency, wma produces a smaller file (better compression) than mp3. Besides I use the variable sample frequency, mainly because in 2005, when I copied most of those files, the portable music players had small storage space. I can play my music with WoW and TrueBass effects using Windows Media Player 11  :)  
I'm too lazy to copy ~10,000 music files from wma to another less well known format (unknown by Windows users :). 

> **CharlesA said:**
> I've been on Debian to stay away from snaps.

I love snaps I still use Ubuntu 16.04 ESM and because it already supported snaps out-of-the-box, I can use the latest apps for Firefox and LibreOffice Calc in a distro from 7 years ago. 
I also start to try the immutable snap based Ubuntu Core, still based on 22.04, but planned for 24.04 and it is the best change in Ubuntu since Ubuntu 4.10 :)  It is a real improvement of the design, unlike most changes in Linux nowadays, that are mainly fancier bling-bling.

---

### Post by CharlesA on 2023-07-11
> **gezzer2 said:**
> @CharlesA ... i did a minimum install setting the ssd up with 3 partitions boot/efi, /(root) and home (no swap as i have 64GB of ddr4 installed). 
i also found it best not to do any updates before removing snaps as laid out below.

Thanks for the info! Seems relatively easy to remove. Hopefully it stays like that.

> **lammert-nijhof said:**
> Most Linux music players play wma, I also use it with Rhythmbox and Lollypop. Besides for the same sample frequency, wma produces a smaller file (better compression) than mp3. Besides I use the variable sample frequency, mainly because in 2005, when I copied most of those files, the portable music players had small storage space. I can play my music with WoW and TrueBass effects using Windows Media Player 11  :)  
I'm too lazy to copy ~10,000 music files from wma to another less well known format (unknown by Windows users :). 

I feel that. I went back and reripped all my CDs to FLAC after originally ripping them to MP3, many, many years ago. That took quite a bit of time and I found some of the CDs had read errors on them too.

---

### Post by mikodo on 2023-07-12
> **gezzer2 said:**
> 
i also found it best not to do any updates before removing snaps as laid out below.

then followed this ...
[https://danieliser.com/fully-remove-snap-from-ubuntu-22-04/](https://danieliser.com/fully-remove-snap-from-ubuntu-22-04/)

and this ...
[https://haydenjames.io/remove-snap-ubuntu-22-04-lts/](https://haydenjames.io/remove-snap-ubuntu-22-04-lts/)

installed firefox, gnome-software-centre, synaptic and vivaldi by CLI and then deb.

everything is now running smooth as silk and works which i didn't have with snaps.


Thank you.

I am sill running Xubuntu 20.04, (I still get security updates until 25.04), when I need to decide what I am going to do about Snaps.

First thing I plan to do before 25.04, is to continue to read up about Debian. Then to install Debian Stable Xfce desktop, and use KVM VMs for the current Xubuntu. Follow current advice like yours, to completely remove Snaps. If all goes well, and Snaps can be completely removed still, (not locked in), then I will probably use the VM of Xubuntu as my daily driver. If all doesn't go well in removing Snaps then, well, I guess my daily driver will be a VM of Debian Stable Xfce desktop, using the KVM snap shot features.

---

### Post by gezzer2 on 2023-07-12
> **mikodo said:**
> Thank you.

I am sill running Xubuntu 20.04, (I still get security updates until 25.04), when I need to decide what I am going to do about Snaps.

First thing I plan to do before 25.04, is to continue to read up about Debian. Then to install Debian Stable Xfce desktop, and use KVM VMs for the current Xubuntu. Follow current advice like yours, to completely remove Snaps. If all goes well, and Snaps can be completely removed still, (not locked in), then I will probably use the VM of Xubuntu as my daily driver. If all doesn't go well in removing Snaps then, well, I guess my daily driver will be a VM of Debian Stable Xfce desktop, using the KVM snap shot features.

debian 12 stable looks and feels very nice with gnome still a bit of a pain getting all the codecs installed unlike ubuntu where is done with a couple of clicks. what i like about ubuntu is its ease of use and install, it just works and has done, for me, from the very beginning. 
putting snaps into the LTS of ubuntu seems to me to be a step too far as snaps doesn't always work as it should, boxes and usb pass through, firefox and gnome extensions are just a couple of examples.
since i have removed snaps all the little niggles and glitches have gone away and ubuntu is just back to its normal useful working self, best of luck with your endeavors.

ps. have a look at ubuntu pro it will give you 10 years of security updates. it does on 22.04 ...

---

### Post by mikodo on 2023-07-12
> **gezzer2 said:**
> 
ps. have a look at ubuntu pro it will give you 10 years of security updates. it does on 22.04 ...

I quickly read about this. It certainly seems something I should investigate more thoroughly. As long as I can install my preferred Desktop (Xubuntu to it), I quite possibly, would like this. I don't need the 'latest and greatest' for just about everything. I am quite happy installing from the Repos I have now.

Thank you, so much!

---

### Post by gezzer2 on 2023-07-12
> **mikodo said:**
> I quickly read about this. It certainly seems something I should investigate more thoroughly. As long as I can install my preferred Desktop (Xubuntu to it), I quite possibly, would like this. I don't need the 'latest and greatest' for just about everything. I am quite happy installing from the Repos I have now.

Thank you, so much!

as you are all ready using ubuntu (whatever flavour) all thats needed with ubuntu pro is to register, its free for personal use for up to 5 computers. then it will give you a key code (token) to insert into the update manager ...
have a look here ...

[https://ubuntu.com/pro](https://ubuntu.com/pro)

and you are very welcome, best of luck ...

---

### Post by sports fan Matt on 2023-07-13
I'm considering putting Xubuntu or Xfce on the Thinkpad.  Any advantages or disadvantages ram wise?

---

### Post by CharlesA on 2023-07-13
> **sports fan Matt said:**
> I'm considering putting Xubuntu or Xfce on the Thinkpad.  Any advantages or disadvantages ram wise?

XFCE is supposed to be pretty lightweight. Depending on how much memory you have, it would probably run fine.

FWIW, I usually use Cinnamon or LXE if I need something with a GUI.

---

### Post by mikodo on 2023-07-14
Unfortunately, Xubuntu's memory usage has soared from what is was a decade ago. (More bling).

10 years ago, Xubuntu at rest for me was in the 200 megabyte range. Debian Xfce was a mere 95 megabytes then. 

Today, I have only Xubuntu installed. Here is its' memory use:

```
MiB Mem :   7767.4 total,   5021.5 free,   1056.6 used,   1689.3 buff/cache
MiB Swap:    947.3 total,    947.3 free,      0.0 used.   5804.2 avail Mem
```

I imagine, the Debian Xfce desktop today, uses quite a bit** less** memory than Xubuntu's. (Less bling). Debian is probably still sticking to Xfce's mandate to be light. (Little mouse).

For anyone wanting to read more about Xfce:

[https://www.makeuseof.com/reasons-why-you-should-try-xfce/](https://www.makeuseof.com/reasons-why-you-should-try-xfce/)

---

### Post by guiverc on 2023-07-14
> **sports fan Matt said:**
> I'm considering putting Xubuntu or Xfce on the Thinkpad.  Any advantages or disadvantages ram wise?

Personally if using a *low resource* machine and using GTK3 apps, I'd opt for Xubuntu.

If using Qt5 apps, Lubuntu which is the *lightest* *flavor* 'out of the box', will be lightest.   But in truth, how many of us use their systems *'out of the box'* and don't add other apps.

I'm about to switch from my current (2017 dell) machine to an older 2008 dell box, which has a lot less *grunt*  than this box, in fact regularly use boxes as old as from 2005, and  occasionally from 2003.. thus I'm always considering what is *light* and what will keep my machines *fast.*

On  my old hardware, I don't care as much about disk space as much as I do RAM (esp.  given a box with only 1GB of RAM may still have 80GB or more of disk)  thus I personally install many DE/WMs and decide at login which I'll use for a session based on what apps I'll run, ensuring they'll all share the same toolkit/libraries.

Xfce used to use GTK2 which was real light (as did LXDE used by Lubuntu). The LXDE *developer* complained about in blogs how much heavier GTK3 was when *porting *LXDE from GTK2 to GTK3, which is what lead to the dropping of GTK3 and replacement desktop being LXQt (ie. using Qt5 which is *lighter*). 

MATE got *heavier* and slower as it ported from GTK2 to GTK3, which I sure noticed on 1GB RAM pentium M (*single core x86-32bit*) so I switched to Xfce when using older boxes... Xfce too got heavier as it ported (*much later*). 

WMs are your other option instead of a heavier desktop... but I do consider Xfce still a *light* desktop (esp. when using GTK3 apps; you won't beat LXDE if using GTK2 apps, but how many GTK2 apps still exist!)

My 2c.

---

### Post by mikewhatever on 2023-07-14
There are way too many distros to list as possible alternatives, but [s]LM[/s] the Dien Bien Phu distro is disqualified. It is silly, and its users are annoying.:P

---

### Post by sports fan Matt on 2023-07-16
I have three possibilities for a laptop need help choosing. 
1. Dell Latitude 7490 14" HD i5-7300U@2.60 GHZ 8GB RAM 250GB M.2 SSD I 28583WK
2. Dell Latitude E5470 | i5-6300U | 8GB RAM | 256 GB HDD | LINUX | 27592MG
3. Lenovo ThinkPad T450 | i5-5300U | 4GB RAM | 256GB SSD | LINUX
Any ones stand out? Any advice would be appreciated

---

### Post by ajgreeny on 2023-07-16
> **mikodo said:**
> Unfortunately, Xubuntu's memory usage has soared from what is was a decade ago. (More bling).

10 years ago, Xubuntu at rest for me was in the 200 megabyte range. Debian Xfce was a mere 95 megabytes then. 

Today, I have only Xubuntu installed. Here is its' memory use:

```
MiB Mem :   7767.4 total,   5021.5 free,   1056.6 used,   1689.3 buff/cache
MiB Swap:    947.3 total,    947.3 free,      0.0 used.   5804.2 avail Mem
```

I imagine, the Debian Xfce desktop today, uses quite a bit** less** memory than Xubuntu's. (Less bling). Debian is probably still sticking to Xfce's mandate to be light. (Little mouse).

For anyone wanting to read more about Xfce:

[https://www.makeuseof.com/reasons-why-you-should-try-xfce/](https://www.makeuseof.com/reasons-why-you-should-try-xfce/)
Just for information I have a VM of Debian 12 Unstable, ie, Debian Sid, using Xfce which running more or less exactly as when installed apart from some added applications which don't run a boot.
After boot it uses a similar amount of RAM as your Xubuntu, and is, incidentally, very similar to the RAM usage of my Xubuntu 22.04.

In years past, I agree that Debian Xfce used less RAM than Xubuntu; as they have both grown older and added more bling it seems they are now fairly similar in RAM usage.

---

### Post by mikewhatever on 2023-07-16
> Unfortunately, Xubuntu's memory usage has soared from what is was a decade ago. (More bling).

10 years ago, Xubuntu at rest for me was in the 200 megabyte range. Debian Xfce was a mere 95 megabytes then. 

Today, I have only Xubuntu installed. Here is its' memory use:

```
MiB Mem :   7767.4 total,   5021.5 free,   1056.6 used,   1689.3 buff/cache
MiB Swap:    947.3 total,    947.3 free,      0.0 used.   5804.2 avail Mem
```


I suspect it has something to do with switching to gtk3. For a memory lean disto try AntiX. It is even better than Xubuntu 10 years ago.

---

