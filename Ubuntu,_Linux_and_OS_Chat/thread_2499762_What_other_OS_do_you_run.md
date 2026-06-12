---
title: "What other OS do you run?"
date: 2024-08-09
forum: Ubuntu, Linux and OS Chat
---

### Post by sports fan Matt on 2024-08-09
I'm trialing Mint which is not bad ~ but I'm unsure if I will keep it.  What others are the community running?

Matt

---

### Post by werewulf75 on 2024-08-09
Mint for my tastes is too conservative - with a big capital 'C'! - and backward-looking. But some  people just love it, and I've set it up for a number of Linux newbies who preferred it. It certainly made them dump Wind* for good, and they're still like kids let loose in a sweet shop. :D

Myself, I mainly run Ubuntu. On this Lenovo T520, 22.04 LTS Pro is main OS, but I also have a small Win 10 partition for just a few odd specialist apps and specialist hardware support not available on Linux, plus Ubuntu Unity 22.04, Mate 22.04, and Fedora 40. On the Windows side, I have VMs with Ubuntu 18.04 Pro, Ubuntu 22.04, and Fedora 40. These latter get used for everything other than the specialist Win stuff.

On my main jerrybuilt tower PC again, Ubuntu 22.04 is king, plus Unity, Fedora, and Debian.

---

### Post by ajgreeny on 2024-08-09
For me it has to be Xubuntu!

The default Ubuntu with its (for me) unusable version of gnome is a complete non starter; I still prefer and must have a traditional DE so Xubuntu fits my ends completely.
Mint-Xfce is OK and I've tried cinnamon but just couldn't get on with it so quickly dumped that version for Mint Xfce.

---

### Post by guiverc on 2024-08-09
I started as a Debian GNU/Linux user back in the mid-late 90s, and its a habit I've never kicked.

I may spend most of my time on Ubuntu boxes, with this my primary PC running Ubuntu *oracular* (Lubuntu/LXQt session which is my most used), but my secondary PC runs Debian *testing*, as does my primary file-server. I have a number of boxes I use for other purposes (inc. media players), and they are  running Ubuntu as its just easier for me.

(*one such system had run Debian for more than a decade happily using Debian;** but changes Debian made had me switch it to Ubuntu noble/24.04**; that box almost always uses Xfce desktop**; my Debian usage is declining very slowly*)

I consider the Ubuntu* flavors* as Ubuntu systems, and most of my boxes are multi-desktop installs, so I'm not always using the same desktop; though I do tend to use the same desktop for specific tasks (eg. a box I do little else but control backups  runs the Ubuntu Desktop (GNOME) almost always)

---

### Post by &amp;KyT$0P# on 2024-08-09
> **sports fan Matt said:**
> What others are the community running?

... where "others" means OSes other than...what?

My secondary systems run Arch Linux.  I also keep a live USB of Pop!_OS 22.04 handy.

---

### Post by werewulf75 on 2024-08-09
> **guiverc said:**
> I consider the Ubuntu* flavors* as Ubuntu systems, and most of my boxes are multi-desktop installs, so I'm not always using the same desktop; though I do tend to use the same desktop for specific tasks (eg. a box I do little else but control backups  runs the Ubuntu Desktop (GNOME) almost always)
Using multi-desktop setups would drive me to distraction, I must admit. You're a very brave guy! :) I find it confusing enough running separate different Ubuntu flavours, if I'm honest. Much as I still have a lot of time and even affection for the old Unity DE, being used to the 'vanilla' Gnome DE somehow makes Unity seem somewhat quaint now and slightly awkward in use. (Maybe it's just that I don't run it enough.) Mate - err, not really for me, too old-fashioned somehow. But has its uses. Where I have Fedora and Debian, they're also 'vanilla' Gnome DE.

The thing is, to me, Gnome is simply the optimal DE there is at present. Far from perfect, and I'd really like to see something completely new and innovative. But then, I'd really like for Linux to become far more radical, completely renew and re-invent itself, with the major distros coming together and eliminating nonsense like multiple different dependencies, etc.  etc. Single standards, and strong Linux brand image would help move Linux forward.

---

### Post by sports fan Matt on 2024-08-09
Other then standard Ubuntu.

---

### Post by Rubi1200 on 2024-08-09
In no particular order, I use:

Ubuntu
Kubuntu
Ubuntu MATE
EndeavourOS

Also constantly playing around with or testing other distros in VMs.

Don't shoot me, but I have to say I really love EndeavourOS. Uses Xfce desktop by default and updates are smooth and trouble-free.

---

### Post by &amp;KyT$0P# on 2024-08-09
> **sports fan Matt said:**
> Other then standard Ubuntu.

Thanks for clarifying.  In that case, to add to my previous post:

I mainly use Xubuntu 22.04.  Tried Lubuntu 24.04 briefly and am planning to add a Lubuntu 24.04 VM.

---

### Post by Dennis N on 2024-08-10
I keep familiar with 4, which are installed in a multiboot, maintenance-free setup. And I only use Gnome:
Ubuntu
Fedora
Debian
Manjaro

---

### Post by TheFu on 2024-08-10
WinXP, Win7, FreeBSD, Debian, Ubuntu, Linux Mint, Raspian, OSMC, OPNSense.  Mint is my main desktop.  Ubuntu/Debian are for servers.  OSMC for media playback. OPNSense is on my routers.  WinXP is for old games (runs inside a VM). Win7 is for some personal finance/stock tools).

Probably a few others.  I can run a report using Ansible to get the exact releases.

Just attempted to  update OPNsense to a new release, 24.7, this morning. Seems to have failed. Need to connect a serial port to see what's really happening. The new OS was released 2-3 weeks ago, so I waited to avoid early beta testing. That was the plan.

I don't dual boot.  Most run in virtual machines, but about 8 are on hardware.

---

### Post by sports fan Matt on 2024-08-10
@thefu what is your experience with mint? I’m dual driving it at the moment

---

### Post by TheFu on 2024-08-10
It works well enough.  I swapped out the GUI for my WM, fvwm.  It is also a ZFS test system for me for the last 14 months or so.  
Just so you know, I don't run Mint directly on hardware. It is a virtual machine.
```
$ lsblk 
NAME   TYPE FSTYPE      SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
sr0    rom             1024M                      
vda    disk              40G                      
&#9500;&#9472;vda1 part               1M                      
&#9500;&#9472;vda2 part vfat        513M  495.2M     3%       /boot/efi
&#9500;&#9472;vda3 part swap        1.8G                      [SWAP]
&#9500;&#9472;vda4 part zfs_member    2G                bpool 
&#9492;&#9472;vda5 part zfs_member 35.7G                rpool 
```


I upgrade Mint to 21.3 Virginia a few weeks ago.  Since I don't use their GUI, I had to do it the manual, debian, way. That went fine.

I use Mint to avoid Canonical's fetish with snap packages everywhere. I have some use for snap packages, just never on a desktop. Actually, only 1 snap package do I actually appreciate. All the others are just problems to be worked around/solved.

---

### Post by him610 on 2024-08-10
> ++For me it has to be Xubuntu!
On five machines.

Raspbian on two Raspberry PI devices; one Debian (32bit) on Acer AOA netbook from 2008.

---

### Post by sports fan Matt on 2024-08-10
That’s quite honestly the only reason why I’m debating between Ubuntu and Mint at this point ~ I’m not a fan of snap at all, but not sure if I’ll lose any real features going with one or the other. I want to be able to pick one and just can’t do it yet

---

### Post by Dennis N on 2024-08-10
> **sports fan Matt said:**
> That’s quite honestly the only reason why I’m debating between Ubuntu and Mint at this point ~ I’m not a fan of snap at all, but not sure if I’ll lose any real features going with one or the other. I want to be able to pick one and just can’t do it yet

Remember that Mint does not officially offer a Gnome desktop version. If I wanted a snap-free OS similar to Ubuntu which also offers Gnome, I would use Debian.

---

### Post by TheFu on 2024-08-10
> **sports fan Matt said:**
> That’s quite honestly the only reason why I’m debating between Ubuntu and Mint at this point ~ I’m not a fan of snap at all, but not sure if I’ll lose any real features going with one or the other. I want to be able to pick one and just can’t do it yet

If a typical home desktop user, I don't think there's any question - Linux Mint.
For people running servers, I'd never use Mint or any Linux with a GUI.

Of course, your skills will determine some of this and your comfort level with different distros.  Mint seems to smooth out the fire rough edges that Ubuntu still has for normal people.  Their anti-snap stance is reassuring too.  Don't forget there are Ubuntu-based Mint versions and Debian-based Mint versions.  Try both. See which is more comfortable for you, but don't be afraid of the other one. Package management and upgrades are just a little  different.

---

### Post by TheFu on 2024-08-10
> **Dennis N said:**
> Remember that Mint does not officially offer a Gnome desktop version. If I wanted a snap-free OS similar to Ubuntu which also offers Gnome, I would use Debian.

I see that as a bonus - anything I can do to avoid the bloat and overly-dumbed-down-GUI that is Gnome the last 10 yrs is a good thing!
There's no accounting for taste, I suppose.  Of course, people say I have terrible taste all the time.  I do wear white shoes with a dark suit. ;)

---

### Post by &amp;KyT$0P# on 2024-08-10
> **sports fan Matt said:**
> That&#8217;s quite honestly the only reason why I&#8217;m debating between Ubuntu and Mint at this point ~ I&#8217;m not a fan of snap at all, but not sure if I&#8217;ll lose any real features going with one or the other.

Years ago I used to run Mint with a KDE desktop, and IIRC the only "real features" difference from *buntu at the time was different primary GUI for installing software updates.  If you update via [FONT=monospace]sudo apt update[/FONT] / [FONT=monospace]sudo apt-get dist-upgrade[/FONT] or via a GUI package manager frontend like Synaptic or Muon, this difference won't affect you.

Also, Mint may handle kernel updates differently from *buntu.

---

### Post by #&amp;thj^% on 2024-08-10
> **Rubi1200 said:**
> 

Don't shoot me, but I have to say I really love EndeavourOS. Uses Xfce desktop by default and updates are smooth and trouble-free.
+100
There is no real need for me to state my fav, just look at my signature. Arch has been rock solid for many years now, no need to look further for myself.

---

### Post by Frogs Hair on 2024-08-10
Solus on two old machines. I wanted rolling releases on those.

---

### Post by bernard010 on 2024-08-15
MX-23.3 XFCE 6.1 kernel. In virtual box I QA test Ubuntu and flavors of. Other boxes are Opensuse15.6 leap.
My laptop I use Antix, due to low memory capacity, 1GB. Wife has windows 10.

---

### Post by ajgreeny on 2024-08-16
> **TheFu said:**
> I see that as a bonus - anything I can do to avoid the bloat and overly-dumbed-down-GUI that is Gnome the last 10 yrs is a good thing!
There's no accounting for taste, I suppose.  Of course, people say I have terrible taste all the time.  I do wear white shoes with a dark suit. ;)
Agreed 100%

I can never figure out why users think Gnome is so wonderful when as far as I'm concerned it makes the desktop just about impossible for me.
OK,  I'm a simple, old fashioned type of guy who never uses a GUI for things such as updating the system that are so much more easily done in terminal, and if done that way also provide me with so much more useful information. 
Years ago when I used synaptic for almost all package management I set it to carry out the actions in terminal as default so now that I've realised how easy the terminal is to use, why then bother with a GUI when it's not needed? 
Xfce gives me the opportunity to use a GUI to do the things that obviously work best  with a GUI but it doesn't add a lot of unneeded graphical effects etc, etc, it just works and works well.

---

### Post by Shibblet on 2024-08-16
I very much like KDE.  And that's what brought me from Ubuntu (Gnome 2) to KDE way back when Ubuntu started their Unity Desktop.  I switched over to Kubuntu around 12.04.

In 2022 though, I switched over to Manjaro KDE.  I like the ease of installation, and the ability to use the AUR if necessary.

I still have a lot of love for Ubuntu though, because it's where I first started learning Linux.  ;-)

---

### Post by lammert-nijhof on 2024-08-20
[COLOR=#000000]I run all my Linux and Windows releases in a VirtualBox VM. [/COLOR][COLOR=#000000]You don't not need expensive hardware for moving to VMs, my HW did cost me $349 in April 2019. It has a Ryzen 3 2200G; 16GB DDR4; 512 GB nvme-SSD (3400/2300 MB/s) and I reused a 2TB HDD and an 128GB sata-SSD as cache for the HDD. 

The Host OS is a minimal install of Ubuntu 24.04 LTS, supported by VirtualBox and I use OpenZFS to store all VMs and Data. The firewall of Host and VMs are all closed for inbound traffic. For data exchange between VMs I use the shared folders of VirtualBox. The system has >60 VMs often very old ones, but for daily use I use 6 VMs stored on the nvme :[/COLOR]
[COLOR=#000000]- Xubuntu 24.04 LTS for Social Media, the only VM with some open ports.[/COLOR]
[COLOR=#000000]- Ubuntu 16.04 ESM for banking. It is used exclusively for banking and has been encrypted by VirtualBox. It runs the newest snaps from Firefox and LibreOffice (Calc) [/COLOR]:smile::smile:
[COLOR=#000000]- Ubuntu Budgie 24.04 LTS for Multimedia.[/COLOR]
[COLOR=#000000]- Ubuntu 22.04 LTS for try outs of new stuff and other experiments.[/COLOR]
[COLOR=#000000]- Windows 11 Pro, you never know, when you might need it.[/COLOR]
[COLOR=#000000]- Windows XP Home to play the wma copies of my CDs and LPs with WoW and TrueBass effects. Note that the VM has been installed and activated in March 2010 and it survived 2 VBox owners; 3 desktops and 4 CPUs [/COLOR]:smile::smile:

[COLOR=#000000]The fastest VM boot time is 7 seconds for Xubuntu and the slowest is Windows 11 in 45 seconds, all Ubuntu flavors boot within 12 seconds and XP Home (1 core) in 25 seconds. Xubuntu is always loaded, and Ubuntu 16.04 and Windows XP I also use frequently. Windows 11 I boot once per week for the weekly update [/COLOR]:smile:

My other VMs are all Windows Releases from 1.04 to 11 and that includes the NT releases from the nineties, and I have all Ubuntu LTS Releases from 6.06 LTS to 24.04 LTS and, 4.10 the first and 5.04, my first try-out on a spare Pentium II.  I keep an eye on Linux Mint; Zoris OS; Fedora; Manjaro; Debian; OpenSUSE Leap and Peppermint.  I have another set of old OSes from my past like DR-DOS; OS2 Warp; gOS 3.1; Peppermint 7; etc

---

### Post by nicolasdentremont on 2024-08-21
Xubuntu is my main OS. I've been running some really old games on a Windows 98 virtual machine. I had some Magic School Bus games from when I was a kid that I wanted to show my kid but they wouldn't work with Wine. The first family computer my parents got had Windows 98 so it brings back some memories.

---

### Post by TenPlus1 on 2024-08-23
Linux Mint 22 Cinnamon edition on my desktop, and Bodhi Linux 7.0 on my laptop.

---

### Post by Rubi1200 on 2024-08-23
> **TenPlus1 said:**
> Bodhi Linux 7.0 on my laptop.
Big +1 for Bodhi Linux.

Have it running on an old 1GB Intel Atom netbook.

Runs very smoothly for me.

---

### Post by sports fan Matt on 2024-08-23
I have Linux Mint on my Lenovo Thinkpad T470, my new Dell E7450 i7-5600u 16GB 256GB SSD will get Ubuntu 20.04

---

### Post by mechanic on 2024-08-29
This is an interesting item I just came across, and worth replying to as the response on here reveals a spread of OSs that I have had a little experience with.

This is an Ubuntu-focused group which has apparently accepted the Linux baseline as the answer but it may be worth pointing out the other, wider, range of possibilities eg Macos, Windows.
I'm in the middle of setting up a Dell laptop for the umpteenth time, bought on by the change made to the Ubuntu defaults like removing the settings options from the top-level menu to scatter them throughout the desktop. Who voted for this? Getting the menu and menu bar setup right is one of the first level questions in any choice of os. This now rules out ubuntu-unity which is a pity as it was the first choice earlier because it was about the only desktop system that handled HDPI monitors properly. The eyestrain from the screen on installation and bootup (from eg ubuntu-xubuntu) is simply unacceptable in 2024. The other requirement of a modern laptop is the ease of setup and convenience in use of the system encryption feature. Another essential in 2024.

OK those are a couple of areas where linux/ubuntu lags behind the competition (Windows and Macos). The best you can do without giving up and buying a new machine, if you want to stay with the Ubuntu family (Debian is ruled out because it can't handle HDPI properly), is to try MATE as the desktop. This seems to have some of these problems sorted out. There's no alternative to some trial and error with different systems on some USB keys for convenience. Good luck with that!

---

### Post by werewulf75 on 2024-08-29
On the laptop I'm using right now, my main OS is vanilla Ubuntu 22.04 LTS, multi-booted with Ubuntu Mate 22.04 LTS, Ubuntu Unity 22.04 LTS, Fedora 40, and a minimal Windows 10. The latter also has two VMs, Ubuntu 18.04 LTS and Ubuntu 22.04 LTS, all running nicely here. I don't really see where Windows is in any way ahead - let alone that piece of beta sh**e called Windows 11! Not a huge fan of Mate but I'd sooner be confined to that than Windows let alone macOS, that utter perversion of NeXTStep.

---

