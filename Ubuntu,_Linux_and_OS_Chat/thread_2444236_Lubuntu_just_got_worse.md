---
title: "Lubuntu just got worse"
date: 2020-05-27
forum: Ubuntu, Linux and OS Chat
---

### Post by rdh61 on 2020-05-27
Lubuntu just got worse. I hope developers keep an eye on these forums to glean some feedback. I would like to ask them, "Why did you take a nice, lightweight, functional system and make it bloated, complicated and buggy?" I refer of course to 20.04 LTS. I have to say that previously I had 18.04 LTS so I cannot say at exactly what point this change occurred. Next time I'll move to Mint with XFCE.

---

### Post by Autodave on 2020-05-27
Are you asking for help or just complaining?  I really haven't seen other complaints about Lubuntu 20.04.  Perhaps if you tell us what is going on, someone here may be able to help you!

---

### Post by ajgreeny on 2020-05-27
It's the move of DE that is the reason behind this.

Lxde used gtk2 toolkit but Lxqt uses qt5 I believe, much more up to date and flexible.

You could try Debian 10 and add the Lxde DE yourself as I did on an old netbook.

---

### Post by rdh61 on 2020-06-04
@Autodave Thanks for your response. Just complaining actually! Or to be less facetious, just waving a flag at the developers, if they're watching. It is a general complaint. Lubuntu 20.04 is slow and comes with numerous things that don't work out of the box without hours of troubleshooting and tinkering. I've got it all working now, it's just slow. 18.04 was fast.

---

### Post by rdh61 on 2020-06-04
@ajgreeny Thank you for your response and suggestion. I'll bear with it for now because I don't want the trouble of setting up a new system all over again right now. As said, I'll try Mint next time. I have it on another computer and it works really well.

---

### Post by ajgreeny on 2020-06-04
I'm running Lubuntu-20.04 as a VM in VirtualBox just to have a good look at it and so far I have to admit I really like it.

OK, it's very different from the 18.04 version because of the DE change, and I do accept that it might be a little bit heavier than the LXDE version you used previously but there comes a point when developers withdraw upkeep of distros that have a very small number of users, and little chance of keeping up to date, LXDE not having moved to gtk3, or not yet (see below).

As I understand the current situation it's the LXDE developers who have moved from that to LXQt, which uses the Qt toolkit in place of gtk2.  There is some work on moving LXDE to gtk3 but it is happening slowly, I believe, and has not been without problems.
The Arch wiki reports at [https://wiki.archlinux.org/index.php/LXDE#GTK_3_version](https://wiki.archlinux.org/index.php/LXDE#GTK_3_version)
> GTK 3 version
An experimental GTK 3 build of LXDE can be installed with the lxde-gtk3 group.
While it works mostly, there are some known issues with gpicview, lxappearance-obconf, lxlauncher and lxpanel. 

You could, of course, use the [minimal install CD]("https://help.ubuntu.com/community/Installation/MinimalCD") version to install a cli version and then add LXDE as you own choice of desktop, or perhaps be even more radical and move to Debian 10, using the netinstall version and again choosing LXDE (and other packages) as you install; I have done that on a netbook from 2011 with Atom-N270 cpu and just 1G of ram. It works quite well for such a low powered macine, and a lot faster than Lubuntu 18.04 did.

NB:
I've just noticed that there is no 20.04 version of the minimal install CD so that may not be such a good idea, and I would suggest that the Debian 10 version would be the better choice.

---

### Post by guiverc on 2020-06-04
No, this is not a great place to be seen by Lubuntu developers.

PCman, the developer of `pcmanfm`, the file manager used by LXDE which also handles much of the desktop itself ported the GTK2 code to GTK3 and blogged on how much heavier GTK3 was on his own blog. His blog was (being a developer) rather technical and heavy.. but it's there. PCman then ported it to Qt5 and it was much lighter/faster... which eventually lead to many of the LXDE team joining with Razor-Qt team members on a new LXQt project.

I do testing of Ubuntu flavors, and still use x86 laptops (eg. IBM Thinkpad t43, pentium M & 1gb ram using Lubuntu 18.04 LTS), and used to use Ubuntu-MATE on that t43. However back ~16.04 when MATE moved from GTK2 to GTK3, I no longer wanted to use MATE on that laptop as it was too heavy for it (it was just slow). Xubuntu or XFCE (I also love) also slowed down as it ported from GTK2 to GTK3.  XFCE didn't complete it's GTK3 move until 19.10 (not much fun on x86 anyway, but I had to try it!)

Lubuntu was the last to move from GTK2, and I feared how good it would be on my really old x86 boxes with 1GB of RAM; and I was pleasantly surprised. I'd seen MATE and then XFCE slow down as they moved to GTK3, but Lubuntu with LXQt was comparatively much faster & leaner (Lubuntu 18.10 & 19.04). I also use pentium-4 machines in testing, and it was very similar (I've only used all GTK3/19.10 Xubuntu on pentium 4; though I increased ram once x86 ISOs stopped being produced during 19.04 cycle; RAM being kept limited for testing purposes)

Yes on those limited systems (single core pentium M cpu, 1GB of ram) I'm careful with application choice, and the switch from GTK to Qt does require changing applications (unless you're willing to waste resources by having two libraries in memory that do the same thing, one for DE, one just for app which isn't a good idea with 1GB ram), changes I make for my own usage, thus did for testing purposes too.

I was very impressed with Lubuntu using LXQt on various single core pentium M & pentium 4 boxes in 18.10 & 19.04 (both of which are EOL now, so now 18.04 is the only supported release for x86). 

Yes I tested the same on better hardware too, but I think Lubuntu did a really good job.

 End-users maybe don't think about their application choice (thus use apps that don't share libraries used by desktop thus wasting memory/resources, destroying any leanness of their desktop, and could be better suited making a different desktop choice to begin with given their application choices (*or having more than one desktop installed and selecting at login depending on what you want to do in that session; my used boxes have*)).


(The effect of GTK2 to GTK3 move wasn't as apparent on c2d, c2q & better cpus, so maybe the results will vary on your CPU in use; it was most noticeable by me on the older single core pentium M cpus, or single/dual-core pentium 4s)

---

### Post by DuckHook on 2020-06-05
> **ajgreeny said:**
> …NB:
I've just noticed that there is no 20.04 version of the minimal install CD so that may not be such a good idea, and I would suggest that the Debian 10 version would be the better choice.
It's still around, but buried in an obscure location that Canonical makes every effort to hide: [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/)

I believe that they have committed to one more netboot image in 22.04 but not thereafter. Canonical wants to kill off the mini.iso.

---

### Post by VMC on 2020-06-05
Can you please list your hardware: CPU, RAM, HD, GRAPHICS.
I have a newer system, so I'm not experiencing your issue.
Also ask your questions here:
[https://discourse.lubuntu.me/](https://discourse.lubuntu.me/)
As some council members hang out there.

---

### Post by Chanath on 2020-06-05
> **guiverc said:**
> Have you tried Kubuntu 20.04 on your older machines?

---

### Post by guiverc on 2020-06-05
> **DuckHook said:**
> It's still around, but buried in an obscure location that Canonical makes every effort to hide: [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/)

I believe that they have committed to one more netboot image in 22.04 but not thereafter. Canonical wants to kill off the mini.iso.


As an aside, I've been having trouble in recent days with my thumb-drive used for Lubuntu testing (*currently groovy*), and today's ISO just booted up

"Unable to find a medium container a live file system
Attempt interactive netboot from a URL?
yes no (default yes):"

ie. it appears to be a fallback now for media with issues...  ie. we could create our own by butchering a working ISO maybe :)

(Lubuntu groovy-desktop is my ISO; it lets me enter any URL but has default for 
[http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/groovy-live-server-amd64.iso](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/groovy-live-server-amd64.iso)
(but also lists groovy-desktop-amd64.iso, alas not the Lubuntu I want to test..)

---

### Post by DuckHook on 2020-06-06
> **guiverc said:**
> …we could create our own by butchering a working ISO maybe :)…
Although this might be possible, my thoughts are: "Why bother?" Ubuntu's lack of a 32-bit image has already forced me to look at the Debian mini.iso. Since the Ubuntu netboot image is just a slightly modified verion of the Debian one, Debian feels comfortably familiar.

---

### Post by rdh61 on 2020-06-07
> **guiverc said:**
> No, this is not a great place to be seen by Lubuntu developers.

PCman, the developer of `pcmanfm`, the file manager used by LXDE which  also handles much of the desktop itself ported the GTK2 code to GTK3 and  blogged on how much heavier GTK3 was on his own blog. His blog was  (being a developer) rather technical and heavy.. but it's there. PCman  then ported it to Qt5 and it was much lighter/faster... which eventually  lead to many of the LXDE team joining with Razor-Qt team members on a  new LXQt project.

I do testing of Ubuntu flavors, and still use x86 laptops (eg. IBM  Thinkpad t43, pentium M & 1gb ram using Lubuntu 18.04 LTS), and used  to use Ubuntu-MATE on that t43. However back ~16.04 when MATE moved  from GTK2 to GTK3, I no longer wanted to use MATE on that laptop as it  was too heavy for it (it was just slow). Xubuntu or XFCE (I also love)  also slowed down as it ported from GTK2 to GTK3.  XFCE didn't complete  it's GTK3 move until 19.10 (not much fun on x86 anyway, but I had to try  it!)

Lubuntu was the last to move from GTK2, and I feared how good it would  be on my really old x86 boxes with 1GB of RAM; and I was pleasantly  surprised. I'd seen MATE and then XFCE slow down as they moved to GTK3,  but Lubuntu with LXQt was comparatively much faster & leaner  (Lubuntu 18.10 & 19.04). I also use pentium-4 machines in testing,  and it was very similar (I've only used all GTK3/19.10 Xubuntu on  pentium 4; though I increased ram once x86 ISOs stopped being produced  during 19.04 cycle; RAM being kept limited for testing purposes)

Yes on those limited systems (single core pentium M cpu, 1GB of ram) I'm  careful with application choice, and the switch from GTK to Qt does  require changing applications (unless you're willing to waste resources  by having two libraries in memory that do the same thing, one for DE,  one just for app which isn't a good idea with 1GB ram), changes I make  for my own usage, thus did for testing purposes too.

I was very impressed with Lubuntu using LXQt on various single core  pentium M & pentium 4 boxes in 18.10 & 19.04 (both of which are  EOL now, so now 18.04 is the only supported release for x86). 

Yes I tested the same on better hardware too, but I think Lubuntu did a really good job.

 End-users maybe don't think about their application choice (thus use  apps that don't share libraries used by desktop thus wasting  memory/resources, destroying any leanness of their desktop, and could be  better suited making a different desktop choice to begin with given  their application choices (*or having more than one desktop installed  and selecting at login depending on what you want to do in that  session; my used boxes have*)).


(The effect of GTK2 to GTK3 move wasn't as apparent on c2d, c2q &  better cpus, so maybe the results will vary on your CPU in use; it was  most noticeable by me on the older single core pentium M cpus, or  single/dual-core pentium 4s)





Hi,

I have no idea what gtk2, gtk3, Qt5, Razor-Qt are and to be honest I don't see any reason why I should know. If I am not mistaken Ubuntu was designed to make Linux accessible to people like me who just want to use their computer without worrying about esoteric technicalities. And I had understood that Lubuntu was supposed to make it light in order that it could easily run on older machines. My laptop (Lenovo B590) is old (8 years, I'm guessing) but not ancient. And Lubuntu 20.04 does run but it's slow. My question I suppose is a wider philosophical one. Why the urge perpetually and in a mad rush to upgrade to 'better' technology if things are working just fine as they are for the average user? Surely that is one of the things we hate about Windows! I do accept that I am in a minority of one here so far as my Lubuntu 20.04 complaint is concerned and in my attitude to 'development', and probably also a bit of a Luddite.

---

### Post by rdh61 on 2020-06-07
> **Chanath said:**
> Have you tried Kubuntu 20.04 on your older machines?

No, what's the reasoning?

---

### Post by rdh61 on 2020-06-07
> **VMC said:**
> Can you please list your hardware: CPU, RAM, HD, GRAPHICS.

Sure. Please could you tell me how I can get that information with a terminal command?

---

### Post by ajgreeny on 2020-06-07
Run command ```
inxi -Fzx
``` and copy the output back here.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by Chanath on 2020-06-07
> **rdh61 said:**
> No, what's the reasoning?

I wasn't asking you, sorry. I was asking @guiverc. I don't have any old machines any more, so the interest.

---

### Post by rdh61 on 2020-06-08
```
robert@roberts-work-laptop:~$ inxi -Fzx
System:
  Kernel: 5.4.0-31-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: LXQt 0.14.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 37613JG v: Lenovo B590 
  serial: <filter> 
  Mobo: LENOVO model: 37613JG v: 31900003 Std serial: <filter> 
  UEFI: LENOVO v: H9ET74WW(1.11) date: 06/26/2013 
Battery:
  ID-1: BAT0 charge: 35.1 Wh condition: 35.2/42.8 Wh (82%) 
  model: SMP 45N1045 status: Unknown 
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M185 
  charge: 55% (should be ignored) status: Discharging 
CPU:
  Topology: Dual Core model: Intel Celeron 1005M bits: 64 type: MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 7582 
  Speed: 1198 MHz min/max: 1200/1900 MHz Core speeds (MHz): 1: 1197 
  2: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 2500 (IVB GT1) 
  v: 4.2 Mesa 20.0.4 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-31-generic 
Network:
  Device-1: Broadcom and subsidiaries BCM43142 802.11b/g/n vendor: Lenovo 
  driver: wl v: kernel port: efa0 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Lenovo driver: r8169 v: kernel port: 2000 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
  IF-ID-1: br-031ef41d3be2 state: up speed: N/A duplex: N/A mac: <filter> 
  IF-ID-2: docker0 state: down mac: <filter> 
  IF-ID-3: veth10dc389 state: up speed: 10000 Mbps duplex: full 
  mac: <filter> 
  IF-ID-4: veth9661eb3 state: up speed: 10000 Mbps duplex: full 
  mac: <filter> 
Drives:
  Local Storage: total: 313.00 GiB used: 51.81 GiB (16.6%) 
  ID-1: /dev/sda vendor: Seagate model: ST320LT012-9WS14C 
  size: 298.09 GiB temp: 35 C 
  ID-2: /dev/sdc type: USB vendor: Verbatim model: STORE N GO 
  size: 14.91 GiB 
Partition:
  ID-1: / size: 126.53 GiB used: 49.42 GiB (39.1%) fs: ext4 
  dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: 31.0 C 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 195 Uptime: 1h 07m Memory: 3.70 GiB used: 921.7 MiB (24.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 
  inxi: 3.0.38 
robert@roberts-work-laptop:~$[CODE]
```[/CODE]

---

### Post by VMC on 2020-06-08
> **rdh61 said:**
> ...so I cannot say at exactly what point this change occurred. Next time I'll move to Mint with XFCE.

Here's one reasoning : "LXDE used GTK2 which is EOL, they didnt like GTK3 thus switched to QT"

---

### Post by poorguy on 2020-06-08
> **rdh61 said:**
> 
[Snip]
"Why did you take a nice, lightweight, functional system and make it bloated, complicated and buggy?" I refer of course to 20.04 LTS.


Interesting.

I'm running** Lubuntu 20.04 LTS** on this old desktop and it's specs aren't much different from yours specs. 

I pieced this desktop together with spare parts and installed **Lubuntu 20.04 LTS** and it works great and not buggy at all.

(specs listed in this thread link 2nd window 1st post).

[https://ubuntuforums.org/showthread.php?t=2444335](https://ubuntuforums.org/showthread.php?t=2444335)

I found** LXQT **to have a little bit of a learning curve for me but easy to overcome with the documentation offered here.

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

---

### Post by DuckHook on 2020-06-08
> **rdh61 said:**
> …My question I suppose is a wider philosophical one. Why the urge perpetually and in a mad rush to upgrade to 'better' technology if things are working just fine as they are for the average user? Surely that is one of the things we hate about Windows! I do accept that I am in a minority of one here so far as my Lubuntu 20.04 complaint is concerned and in my attitude to 'development', and probably also a bit of a Luddite.
I'm afraid that this assessment is not accurate, or at least, it is highly misleading. Like all OSes, Ubuntu has many different goals, and what you call ease of use, while desirable, is not its primary purpose. Other goals include security, stability, capability, flexibility, power, performance, universality, currency, support for new hardware, cross-platform functionality, future-proofing…

Were Canonical devs to be forced into an either/or choice, I daresay that any of the above would take precedence over "ease of use". Some of these goals are not incompatible with ease of use; others are. There's a reason Linux has garnered a reputation as a geek OS.

The average user is not Canonical's target user. It is clearly gravitating towards the enterprise (especially cloud). It assumes that its average user base is more knowledgeable than the average Windows user (because this is, in fact, the case). It is not interested in displacing Windows (because such a goal is unrealistic). It even defines ease of use in very different terms than do non-technical users (when it comes to system maintenance, I now find the CLI to be easier to use than any GUI).

I'm not trying to be argumentative. Mrs DuckHook, bless her, is in the same strictly non-technical cohort. Like you, she will never learn the difference between gtk2 vs gtk3 and would never ever want to. So let me phrase it in non-technical terms: the old Lubuntu uses a foundation that is no longer maintained. An unmaintained foundation will quickly fall into such disrepair that it will become an outright menace to safety and security. Therefore, there is no choice but to make the leap to a different foundation. Since it makes no sense to go to all the trouble of building new foundations for obsolete hardware, it is also a given that the new foundation will be more sophisticated and complex. In the same sense that modern internal combustion engines are far more sophisticated and complex than the ones my father drove, modern OSes have no choice but to follow the same arc.

Ergo, the evolution of Lubuntu into Focal.

---

### Post by guiverc on 2020-06-08
> **rdh61 said:**
> Hi,

I have no idea what gtk2, gtk3, Qt5, Razor-Qt are and to be honest I don't see any reason why I should know. If I am not mistaken Ubuntu was designed to make Linux accessible to people like me who just want to use their computer without worrying about esoteric technicalities.
..
My question I suppose is a wider philosophical one. Why the urge perpetually and in a mad rush to upgrade to 'better' technology if things are working just fine as they are for the average user? Surely that is one of the things we hate about Windows! I do accept that I am in a minority of one here so far as my Lubuntu 20.04 complaint is concerned and in my attitude to 'development', and probably also a bit of a Luddite.

Yeah I agree, my desktop is older than your laptop, and I wouldn't use Lubuntu if it wasn't fast and usable on my equipment.   My point was because I use it on limited equipment, I take my software choices into account..

GTK2 is ~DEAD, has been for years now; all maintenance and security fixes for it are gone (except those related to GIMP). GTK started as the GIMP toolkit, and which changed to GTK+ (GIMP+GNOME Toolkit), but since GNOME upgraded to GTK3, only GIMP used features of GTK2 are maintained. LXDE used that old technology which didn't have all flaws fixed, so it was a potential security issue.

The option was LXDE that used GTK3 (the devs went that way; then due to performance hits I tried to describe), switched and joined a different team (Razor-Qt) and created a lighter LXQt.

The move was necessary for security reasons, the GTK developers are now working on GTK4, and gtk2 being treated as EOL

Our computer software is built on a series of stacks. The DESKTOP/GUI has stacks below it that are necessary... To be secure we need all stacks patched.

Bottom level stack is the linux kernel, above that ... (eventually toolkits be it GTK/Qt) .. then desktop (GUI) and finally the end-user programs above it all.  In effect a chain.  A chain is often said to be as weak as the weakest link.

*"Urge  .. mad rush*" 

It wasn't quick. The first Lubuntu LXQt image came out in 2015 ([https://www.phoronix.com/scan.php?page=news_item&px=LXQt-Lubuntu-UOS-15.10](https://www.phoronix.com/scan.php?page=news_item&px=LXQt-Lubuntu-UOS-15.10)) taking years before it was decided it was "ready" for prime-time.

---

### Post by rdh61 on 2020-06-09
OK, I take all your points (on the chin). It's still a bug that on my system Lubuntu 20.04 takes up to 10 seconds to respond after I have typed in my login password, and that some software (like Libreoffice) takes an age to open, to mention just a couple of things. But I'll go with it, for now. Thanks for the chat. I have one practical take home (can't remember who mentioned it, but thanks): get used to using the software shipped with the distro, rather than alternatives that I may have become used to from previous versions, as the former are more likely to be less demanding of resources with the new technology.

---

### Post by VMC on 2020-06-09
Sounds like something else is going on. Check journal logs, dmesg. Also what does ```
systemd-analyze
``` show?

---

### Post by Chanath on 2020-06-10
> **guiverc said:**
> Yeah I agree, my desktop is older than your laptop, and I wouldn't use Lubuntu if it wasn't fast and usable on my equipment. 


Have you tried Kubuntu 20.04 on your older computer?

---

### Post by poorguy on 2020-06-10
> **guiverc said:**
> Yeah I agree, my desktop is older than your laptop, and I wouldn't use Lubuntu if it wasn't fast and usable on my equipment.


How old is old and what kind of system specs do you have.

I just installed** Lubuntu 20.04** on this **13 year old desktop** and it runs great OOTB.

The few bits of additional software is all from the default repositories.


```


thomas@hp-compaq:~$ inxi -Fxz
System:    Kernel: 5.4.0-37-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: LXQt 0.14.1 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Hewlett-Packard product: HP Compaq dc7800p Small Form Factor v: N/A 
           serial: <filter> 
           Mobo: Hewlett-Packard model: 0AA8h serial: <filter> BIOS: Hewlett-Packard v: 786F1 v01.04 
           date: 07/18/2007 
CPU:       Topology: Dual Core model: Intel Core2 Duo E6550 bits: 64 type: MCP arch: Core Merom rev: B 
           L2 cache: 4096 KiB 
           flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 9310 
           Speed: 1995 MHz min/max: 1998/2333 MHz Core speeds (MHz): 1: 1995 2: 1995 
Graphics:  Device-1: Intel 82Q35 Express Integrated Graphics vendor: Hewlett-Packard driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.8 driver: intel unloaded: fbdev,modesetting,vesa 
           resolution: 1152x720~60Hz 
           OpenGL: renderer: Mesa DRI Intel Q35 v: 1.4 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: Intel 82801I HD Audio vendor: Hewlett-Packard driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.4.0-37-generic 
Network:   Device-1: Intel 82566DM-2 Gigabit Network vendor: Hewlett-Packard driver: e1000e v: 3.2.6-k 
           port: 1100 bus ID: 00:19.0 
           IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 149.05 GiB used: 6.47 GiB (4.3%) 
           ID-1: /dev/sda vendor: Western Digital model: WD1600AAJS-22L7A0 size: 149.05 GiB 
Partition: ID-1: / size: 145.71 GiB used: 6.47 GiB (4.4%) fs: ext4 dev: /dev/sda1 
Sensors:   System Temperatures: cpu: 46.0 C mobo: 42.0 C 
           Fan Speeds (RPM): cpu: 1753 fan-2: 0 fan-3: 1228 fan-4: 995                                          
Info:      Processes: 164 Uptime: 12h 08m Memory: 3.77 GiB used: 1007.8 MiB (26.1%) Init: systemd               
           runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 inxi: 3.0.38                                 
thomas@hp-compaq:~$ 


```

---

### Post by rdh61 on 2020-06-10
> **VMC said:**
> Sounds like something else is going on. Check journal logs, dmesg. Also what does ```
systemd-analyze
``` show?

I am afraid I do not know what journal logs and dmesg are, where to find them or what to look for.

```
robert@roberts-work-laptop:~$ systemd-analyze
Startup finished in 20.347s (firmware) + 13.710s (loader) + 8.484s (kernel) + 1min 9.577s (userspace) = 1min 52.120s 
graphical.target reached after 1min 9.551s in userspace
robert@roberts-work-laptop:~$ 
```

---

### Post by guiverc on 2020-06-10
> **Chanath said:**
> Have you tried Kubuntu 20.04 on your older computer?

I ran Kubuntu *focal* *fossa* a few times on varying hardware including my main box; my intention was to reply with '*groovy*' from my depreciated (old primary) box in a QA-test, but I've been having issues with *groovy* ISOs since Sunday (7-Jun) :(

> **poorguy said:**
> How old is old and what kind of system specs do you have.
[/code]

My primary box is a 2009 dell optiplex d960. Specs as I note them on iso.qa.ubuntu.com are 
```
dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
```

(I have 23 boxes listed in a text file, specs taken from `lshw` that I copy into iso.qa when I run a QA test on one).  Your box is probably closest to 
```
hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
```
though if I'd successfully got Kubuntu daily to boot, and reply on that it'd have been on
```
dell [optiplex] 755 (c2d-e6850, 5gb, amd/ati radeon rv516/x1300/x1550)
```
and have another HP somewhat similar spec'd
```
hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)
```

My hp dc7700 did a huge proportion of my *focal* (likely *eoan* & earlier too) QA-test installs  (it's a box that shares two screens [of the six] on this desk)

---

### Post by DuckHook on 2020-06-10
> **rdh61 said:**
> OK, I take all your points (on the chin).
I do hope that no one here gives the impression that we are browbeating you. We all started from the same place you are now. No one is born knowing shell commands.

I think it might help to extend my car analogy:

People who don't care to be proficient in automotive knowledge buy Fords and Toyotas. There's nothing at all wrong with this. Perfectly respectable. Applies to most of the population in fact. That's why the majority of cars sold are consumer branded. In the IT world, Windows and Apple fulfill this role.

But running Linux is like driving a race car, a specialty car or an antique. It assumes that the user is at least interested in the technicalities. And while it doesn't require that such enthusiasts be able to actually work on such cars, it *is* based on the expectation that the user knows the concepts and can speak the lingo—horsepower, torque, spark-plugs, carburetors and turbochargers. With Linux, such concepts reside on the command line. Sorta like getting in under the hood.
> **rdh61 said:**
> I am afraid I do not know what journal logs and dmesg are, where to find them or what to look for.

If you would like to now go beyond this thread to a real help request, I would recommend that you start a new thread in the "New To Ubuntu" subforum. I'm sure that the forum members who have already chimed in would be happy to assist you there. We want to keep this subforum an "around the water cooler" thing.

---

### Post by poorguy on 2020-06-11
@guiverc

Interesting assortment of computers you're using.

It's good to see I'm not the only one using older computers.

I to have 20 plus old desktops that consist of oem factory builds and home builds.

The hardware ranges from dual core processors and quad core processors and 4.0 GB and 8.0 GB DDR2 and DDR3 memory and integrated graphics adapters and discrete graphics adapters and mechanical hard drives.

I have a couple of brand new desktops with an AMD APU and Intel HD Processor Graphics which the Wife uses with Windows 10 and which leaves the older computers for Linux which works very well on them.

I have several connected online which allows me to run and learn about different distros.

---

### Post by Chanath on 2020-06-11
> **guiverc said:**
> I ran Kubuntu *focal* *fossa* a few times on varying hardware including my main box; 
 

I have a feeling that Kubuntu runs better on these older computers, than Lubuntu. And, much better looking too. :)

---

### Post by mmoseeker on 2020-06-12
> **Chanath said:**
> I have a feeling that Kubuntu runs better on these older computers, than Lubuntu. And, much better looking too. :)


i also recommend use kubuntu,better UI looking.Last time I made a gamer trade website which is available here at [playermall.com]("https://www.playermall.com") I wish that I will open company in few months. From start, I want to reduce costs so it is natural that I think about Linux because I do not want to pay for the licenses like Win, Antivirus, MS Office etc. My question is which one distribution will be the best for new users. Mint, Ubuntu or something else? I am thinking about people whose will be working for me. Maybe the first time in Linux. The second question is any viruses on Linux? Do I need have AntiVir? Finally what with software for multimedia like MS Office, PDFs or other. What can be problematic?

---

### Post by ajgreeny on 2020-06-12
> **mmoseeker said:**
> i also recommend use kubuntu,better UI looking
But I imagine it uses more RAM when booted than Lubuntu.  I have Lubuntu 20.04 running as a VM in virtualbox and after boot it uses 220M of ram; I don't have Kubuntu but I suspect it will be higher than 220M.

---

### Post by Chanath on 2020-06-15
> **ajgreeny said:**
> But I imagine it uses more RAM when booted than Lubuntu.  I have Lubuntu 20.04 running as a VM in virtualbox and after boot it uses 220M of ram; I don't have Kubuntu but I suspect it will be higher than 220M. 

Why not try them both on a bare metal tell which one is better? 

One is pure KDE Plasma, the other is part of KDE on Openbox. One has a fully fledged file manager Dolphin, while the other PCManFM-Qt has much less features. And, there's a mismatch of GTK Openbox with Qt, I believe, if not today, in the future.

---

### Post by poorguy on 2020-06-15
@rdh61

Here's my suggestion.

If LXDE is what you really want and what really works than download this and install this.

LXLE based on Ubuntu 18.04 LTS and uses LXDE user interface and supported until 2023.

[https://lxle.net/](https://lxle.net/)

[https://www.lxle.net/download/](https://www.lxle.net/download/)

[https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-64/lxle-18043-64.iso/download](https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-64/lxle-18043-64.iso/download)

[https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-32/lxle-18043-32.iso/download](https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-32/lxle-18043-32.iso/download)

---

### Post by rdh61 on 2020-06-18
@poorguy Thank you! I may well do that. I see it is an .iso file. How do I install it? Also, what happens then to my current desktop environment? Can I keep it to compare? How do I choose which desktop is selected on start up? Thanks.

---

### Post by sudodus on 2020-06-18
LXLE is a separate operating system, a re-spin originally based on Lubuntu.

You install it like any Ubuntu flavour (typically from a bootable USB pendrive) in a separate partition alongside the other operating system(s) (dual boot or multi boot). Do not try to mix it with your current operating system.

---

### Post by rdh61 on 2020-06-19
Ah... Thanks. No I don't want to do that... cannot deal with the hassle of setting up my computer all over again for a while. But what about if I just install the LXDE desktop alongside LXQT in order to try it out. Is there any reason why that would be a bad idea?

---

### Post by sudodus on 2020-06-19
It may or may not work. It would probably work well, but there might be some clashes between the settings of the two desktop environments, and it might be next to impossible to fix. So I can *not* recommend that you mix a new desktop environment into your main operating system.

---

### Post by guiverc on 2020-06-19
> **rdh61 said:**
> ...But what about if I just install the LXDE desktop alongside LXQT in order to try it out. Is there any reason why that would be a bad idea?

I can't advice sorry, but they may not sit perfectly together.

Upgrading Lubuntu 18.04 to 18.10 (or later releases) is unsupported due to problems (*thus the Lubuntu team recommends a re-install*). Yet on this box I did it (*following the instructions the Lubuntu team created for the purpose, though it noted it didn't deal with every situation and problems should be expected; yeah I had problems for about 3 weeks before it suddenly was perfect*).  I then had LXDE & LXQt on this box perfectly...

18.10 moved to 19.04, 19.10,  20.04 before the current 20.10 (*or really groovy - I stay on the development cycle*). Sometime during a cycle something on my system removed all my LXDE system, and I suspect it was dependency rules, so at least in one cycle LXDE & LXQt clashed and LXDE was removed.  I don't know if these rules still apply, but I do recall a reason being given on #lubuntu-devel (IRC) for the removal.  The clash may still apply in *focal* (20.04), or it may not apply, but I'd not be surprised if there are problems (there have been/were in prior releases/cycles; I just forget details sorry)

If you cherish your system, I'd do it first on a VM or secondary/test machine (& watch for removal of packages during the install; ie. ensuring **not** to use a `-y` in your `apt install` command..)

---

### Post by poorguy on 2020-06-20
> **rdh61 said:**
> Ah... Thanks. No I don't want to do that... cannot deal with the hassle of setting up my computer all over again for a while. 

Please don't take this the wrong way.

What is so major to set up in Linux.
LXLE Distro does most of the set up for you OOTB although you may want / need to tweak a setting or two.

> **rdh61 said:**
> 
But what about if I just install the LXDE desktop alongside LXQT in order to try it out. Is there any reason why that would be a bad idea?

As already stated by the wiser than I mixing desktops is not a good idea and will be way more of a PITA than setting up a new Linux install.

I use old desktop computers and LXLE works great on them without problems OOTB.

Create a LXLE bootable usb and give LXLE a live test drive and see what you think of it.

---

### Post by Chanath on 2020-06-21
Something interesting, [https://fosspost.org/reviews/distributions/lubuntu-20-04-review](https://fosspost.org/reviews/distributions/lubuntu-20-04-review)

---

### Post by poorguy on 2020-06-21
I don't hold much faith in magazine type reviews.

A lot of users seem to have a lot of problems with*** Lubuntu 20.04*** on their computers.
 
I'm happily running ***Lubuntu 20.04*** on ***12 year old ***and*** 13 year old*** computers I pieced together from spare parts from other computers  ***(Frankenstein Builds)  ***with ***zero complaints ***and ***zero problems ***OOTB.

I install and update and install very little additional software which comes from the repository and perhaps a bit of minor tweaking and use it pretty much as it comes OOTB without problems.

Kinda makes me wonder if the problem may be something other than the computer or the distro or perhaps I'm the luckiest user in the world.

OH well I'm having a good time using*** Lubuntu 20.04*** on my old ***Frankenstein computers*** and that's what it all about for me. ;)

---

### Post by Chanath on 2020-06-23
> **poorguy said:**
> 

A lot of users seem to have a lot of problems with*** Lubuntu 20.04 ***on their computers.
 


Lubuntu as it was is not there. What we now have is Lubuntu-Qt, and should be named as such. It is actually diminishing the good name Lubuntu was!

---

### Post by poorguy on 2020-06-23
> **Chanath said:**
> Lubuntu as it was is not there. What we now have is Lubuntu-Qt, and should be named as such. It is actually diminishing the good name Lubuntu was!
[SIZE=5][I][B]
[SIZE=4]OMG.[/SIZE][/B][/I][/SIZE]

[I][B]Perhaps you should straighten out the developers.

[https://lubuntu.me/](https://lubuntu.me/)[/B][/I]

---

### Post by Chanath on 2020-06-23
> **poorguy said:**
> [SIZE=5][I][B]
[SIZE=4]OMG.[/SIZE][/B][/I][/SIZE]

[I][B]Perhaps you should straighten out the developers.

[https://lubuntu.me/](https://lubuntu.me/)[/B][/I]

You posted a link, but there's another also named Lubuntu, [https://lubuntu.net](https://lubuntu.net). They sort of don't won't hand over the former Lubuntu web site to the newcomers. The guys, who created Lubuntu and kept it going had gone, together with the LXDE. What we have now is sort of a smaller brother of Kubuntu, using a massive amount of KDE packages, like a franken distro.

You see, if you have an older machine, 64bit of course, Kubuntu 20.04 would run better in it, rather than Lubuntu 20.04. Don't just believe me, try and see. :)

---

### Post by poorguy on 2020-06-23
> **Chanath said:**
> You posted a link, but there's another also named Lubuntu, [https://lubuntu.net](https://lubuntu.net). They sort of don't won't hand over the former Lubuntu web site to the newcomers.

The link you posted is no longer an official Lubuntu supported link.

> **Chanath said:**
> 
 The guys, who created Lubuntu and kept it going had gone, together with the LXDE. What we have now is sort of a smaller brother of Kubuntu, using a massive amount of KDE packages, like a franken distro.

You see, if you have an older machine, 64bit of course, Kubuntu 20.04 would run better in it, rather than Lubuntu 20.04. Don't just believe me, try and see.:) 

I've tried Kubuntu many different versions and not impressed.
If you like Kubuntu 20.04 better than Lubuntu 20.04 Cool use it.

I like Lubuntu 20.04 and have zero problems with it or LXQT user interface.

I don't always like new change however I adapt to it well and move forward.

---

### Post by Chanath on 2020-06-23
> **poorguy said:**
> The link you posted is no longer an official Lubuntu supported link.



Or, that was the official one from the beginning, until when the old fellows left Lubuntu.
 :) Have a good day!

---

### Post by poorguy on 2020-06-23
> **Chanath said:**
> What we have now is sort of a smaller brother of Kubuntu, using a massive amount of KDE packages, like a franken distro.

You see, if you have an older machine, 64bit of course, Kubuntu 20.04 would run better in it, rather than Lubuntu 20.04. Don't just believe me, try and see. :)

Don't take me the wrong way Kubuntu is an awesome distro for users who like the eye candy and its features.

I don't care for all of the many different settings that all lead to the same place and do the same thing.

More settings means more opportunity to accidentally change something and unknowingly screw things up.

One of the beauties of Linux is choice of distros to suit any user so use what works best and what you are most comfortable with.:)

---

### Post by sudodus on 2020-06-23
> **poorguy said:**
> One of the beauties of Linux is choice of distros to suit any user so use what works best and what you are most comfortable with.:)

+1 :-)

---

### Post by poorguy on 2020-06-23
> **Chanath said:**
> Or, that was the official one from the beginning, until when the old fellows left Lubuntu.
 :) Have a good day!

Perhaps this will explain.

[https://ubuntuforums.org/showthread.php?t=2360662](https://ubuntuforums.org/showthread.php?t=2360662)

[https://ubuntuforums.org/showthread.php?t=2438521](https://ubuntuforums.org/showthread.php?t=2438521)

---

### Post by VMC on 2020-06-23
Its uglier than at first thought. I found the AUG16 thread that had the nasty discussion:
[https://lists.ubuntu.com/archives/lubuntu-users/2016-August/010846.html](https://lists.ubuntu.com/archives/lubuntu-users/2016-August/010846.html)
follow to "Next" message to see the progress. You'll begin to understand the situation better.
Don't know who *Mario Behling *is, but getting new people to find the "real" lubuntu site:
[https://discourse.lubuntu.me/](https://discourse.lubuntu.me/)
will be a plus.

---

### Post by poorguy on 2020-06-23
I use the Ubuntu Forum **"Ubuntu Community" **tab and its always sent me to the link below.

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by Chanath on 2020-06-24
> **VMC said:**
> 
Don't know who *Mario Behling *is, but getting new people to find the "real" lubuntu site:


Just google the name Mario Behling, and you'd find quite a lot of results. He is known for lot of good work around the world, especially FossAsia. 

And, also as;

[COLOR=#202122][FONT=sans-serif]"In March 2009, the Lubuntu project was started on [/FONT][/COLOR][Launchpad]("https://en.wikipedia.org/wiki/Launchpad_(website)")[COLOR=#202122][FONT=sans-serif] by Mario Behling, including an early project logo. The project also established an official Ubuntu wiki project page, that includes listings of applications, packages, and components."

And that surpassed an invitation; [/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]

"[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif]In February 2009, [/FONT][/COLOR][Mark Shuttleworth]("https://en.wikipedia.org/wiki/Mark_Shuttleworth")[COLOR=#202122][FONT=sans-serif] invited the LXDE project to become a self-maintained project within the Ubuntu community, with the aim of leading to a dedicated new official Ubuntu derivative to be called [/FONT][/COLOR][I]Lubuntu."


@poorguy
[/I][COLOR=#202122][FONT=sans-serif]Have alook from here, [/FONT][/COLOR]https://lubuntu.net/blog/page/17/

---

### Post by poorguy on 2020-06-24
> **Chanath said:**
> [I]
@poorguy
[/I][COLOR=#202122][FONT=sans-serif]Have alook from here, [/FONT][/COLOR]https://lubuntu.net/blog/page/17/


I looked at the link you posted from 2009 however over the years many new developments and changes come about and therefore what once was no longer seems to work and changes are made.

As we already know these days very few users are using computers that run only a single core processor or run less than 4.0 GB of ram.

I run old computers as far back as 2008 and all of them a run dual core processor and at least 4.0 GB of ram which make them very capable of running LXQT and many other desktops without problems.

From what I've read LXDE desktop has become outdated which is why LXQT desktop is now being used.

I'm not a Linux developer or a Linux guru and what I know about Linux is enough to keep me confused. :lol:

I've always liked the simplicity of LXDE and now I like the simplicity of LXQT which had a slight learning curve for me although with the excellent user manual / documentation available was easily conquered.

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

Lubuntu 20.04 is different and a lot of users hate new change myself included however I like the challenge of a new adventure. :)

---

### Post by jet-bundle on 2020-07-07
I'd like to add a comment about my experience with the move to Lubuntu 20.04 (details in [https://ubuntuforums.org/showthread.php?t=2446644](https://ubuntuforums.org/showthread.php?t=2446644)).

The specific problem I've had concerns the export of LibreOffice files to pdf; this is a "known bug" (see [https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/)). However the work-around suggested in that last link has a tendency to crash LibreOffice; the only satisfactory solution I've found has been to replace qt5 by gtk3 in SAL_USE_VCLPLUGIN.

It's a little worrying that LibreOffice comes bundled with Lubuntu 20.04, but the interoperability of the two seems not to have been tested before release. I suppose one might say that exporting documents to pdf is a minority interest; but I believe that the problem is also present with printing to old-fashioned paper. (I have one sheet which has a well-placed photograph together with a collection of randomly-placed characters, and another sheet which left the printer completely blank despite text appearing on the preview. I didn't investigate further, to avoid wasting too many trees.)

I have a feeling that this is a case of "it's all right leaving me, so it must be up to you to fix this"!

(But apart from this, I rather like 20.04 with LXQt.)

---

### Post by poorguy on 2020-07-09
I personally like Lubuntu 20.04 and for the most installs / updates / works OOTB and have noticed a few minor quirks here and there and figure the next point release will clear those quirks up.

I look at LXQT like trying to use Chevy parts on your Ford or Ford parts on your Chevy and expecting them to bolt on and work.

This is only my warped view and opinion.

---

### Post by guiverc on 2020-07-10
> **jet-bundle said:**
> I'd like to add a comment about my experience with the move to Lubuntu 20.04 (details in [https://ubuntuforums.org/showthread.php?t=2446644](https://ubuntuforums.org/showthread.php?t=2446644)).

It's a little worrying that LibreOffice comes bundled with Lubuntu 20.04, but the interoperability of the two seems not to have been tested before release. I suppose one might say that exporting documents to pdf is a minority interest; but I believe that the problem is also present with printing to old-fashioned paper. 

All flavors are tested prior to release, including Lubuntu, and that testing had discovered issues which is why it was mentioned in the release notes.  Yes the Lubuntu team would love to find & fix every issue found, but it's not always possible, which is why the unfixed issues are mentioned in the release notes.

Not every found issue gets listed in the release notes, some are considered very minor or not expected to impact end-users or very few end-users (*I expected the floppy issue to be unlisted for this reason as an example, but it was listed too*).

We cannot test every circumstance or feature though, there are far to few of us, nor enough time. Myself, I moved to *focal* (what became Ubuntu 20.04 LTS) in October 2019 after 19.10 was officially released, and used Lubuntu every day as my normal desktop, and I wasn't alone. Further to my normal use, I'm recorded on is.qa.ubuntu.com as conducting 342 *focal* QA-tests.

Right now I'm using Lubuntu *groovy* (ie. after* focal* was released, Friday my local time, the following day I *bumped* my release to *groovy* or the next 20.10 release), so this answer to you is actually part of my 20.10 testing, though it's not formally recognized as such (I'm recorded as having done 101 QA-tests of *groovy*/20.10 so far though)

Trying to test every use case is next to impossible. The floppy bug was found not because I decided to test for it, but in supporting a user having trouble with floppies, I used a floppy and opted to leave it in the machine post-testing/post-support (*it wouldn't impact me I thought & would save me having to hunt for another floppy if user came back with more issues*). On the next QA-test using that box however, the install failed because of  the *left-behind* floppy which lead to bug  report, and eventually its being listed in Lubuntu's 20.04 release notes.

If we (*Lubuntu team*) were doing it as a job, maybe it'd be planned for (*a floppy test would take less than 20 minutes to perform on real hardware*), but that still costs *money*, and I doubt a company would fund it given how few people today use floppies. We're not paid for it though, so I didn't plan a test for it, and it was just by accident after a Lubuntu user had issues with floppy drives...  Anyway upstream (`calamares`) have reported the bug is now squashed, so it won't be in the Lubuntu 20.10 release notes as it'll be gone in a few days :p

I've many times printed to PDF, but it's not done very often. It's not covered in any QA-test, that sort of issue would be caught only by us using our end-product, and I've not encountered it.   To expect volunteers to test for, find and fix every issue is asking a bit much, we're using our product though before it gets released.

Since you have issues with LibreOffice, maybe you could also try Calligra ([https://packages.ubuntu.com/focal/calligra](https://packages.ubuntu.com/focal/calligra)). It's not installed in this Lubuntu, but I've used it before and parts of it are really nice (*for some tasks I preferred it over LibreOffice, though I used LibreOffice for other tasks*). It's intended for KDE, so I'd expect it to be good on LXQt/Lubuntu (I'm installing it now in the background, I'll have a play with it shortly, but I don't expect issues).

---

### Post by jet-bundle on 2020-07-10
I’d like to thank guiverc for taking the trouble to respond to my comment. I’m writing this as a user, not a developer. (Though I understand where developers are coming from. Thirty years ago I wrote a corporate email system. All by myself! Ah, those were the days …)
 
 Basically, I’ve been using LibreOffice (in various versions) with Lubuntu 16.04 and 18.04 for the past few years, and haven’t encountered any problems. With both LTS versions I’ve installed LibreOffice myself as a download package. So I was delighted to see that a version of LibreOffice was included in the 20.04 download. I imagined that it would work “out of the box”.

 A few weeks ago, I noticed that sometimes, in LibreOffice Writer, parts of the toolbar failed to repaint after having been obscured by another window, but that a repaint could be forced by minimizing and then maximizing. I could live with that (but I guess it’s another manifestation of the  LibreOffice qt5 problem).
 
 However the problem with creating pdf files, whether by exporting or by printing to pdf, was more of a concern, and at one stage I reverted to 18.04 (I was using a dual-boot machine) to obtain the output file. I was relieved to find that the problem was known to the Lubuntu development team, but then disappointed to find that the suggested workaround (using cairo) was only suitable for new documents and crashed when opening existing documents.
 
 Upon reflection, I’m not sure that creating pdf files from LibreOffice documents (Writer documents in particular) is actually a minority interest. For what would anyone do with an .odt file when they needed to communicate with someone outside the open source community, and where editing wasn’t needed? The answer is either to print on paper, or to make a pdf file. And I’m not convinced that printing on paper works “out of the box” either, though I haven’t carried out extensive tests.
 
 For the moment, I’m using LibreOffice with gtk3 rather than qt5, implemented by a simple change of environment variable in the LXQt settings. I’m happy with that, and although I’ve taken a look at Calligra, I won’t switch to using it. But it’s particularly disappointing that the general issue with qt5 was known to the LibreOffice development team in early 2019, yet it hasn’t been resolved, and that the proposed workaround for the specific pdf problem isn’t really adequate. This wasn’t a problem when Lubuntu 18.04 was the current LTS version, but but is now with the LXQt desktop, and I hope that one or other development team will be able to fix it.

---

### Post by wilfy100 on 2020-10-01
I wonder if I could just give my initial impressions of Lubuntu. On the positive side installation was very straight forward and ran quite quickly. I am running Lubuntu on old hardware, specifically a Pentium dual core G2020 which came out in 2013 and 4Gb of ram. It boots up very quickly, I was suprized how quick this was. I had previously running Elementary which I really like but I thought I would give Lubuntu a try out. I have to say that I will be going back to Elementary mainly because the desktop just seems rather clunky and un-intuitive. While I expect it is possible to have shortcuts to programs you use regularly there does not seem to be any obvious way to do that. In elementary you just launch the program and tick retain in dock (Simples!). I installed GtkStressTesting (a Brilliant program, highly recommended) in Lubuntu via Flatpak and it launched. but now it has disappeared and I have no way at a all of launching it. Lubuntu seems to come with a shed load of programs preinstalled but I do not have a clue what a lot of them are for and would probably never use most of them. My overriding feeling is that Lubuntu is not at all aimed at beginners, I have been using Linux for years and can generally work things out but so far Lubuntu has been disappointing. I admit this is just my personal opinion, it is good that we have the choice. I would imagine Lubuntu can be customised to the users preference but it seems like sanding down a square peg to fit in a round hole. My understanding is that Lubuntu is moving away from running on old hardware ( though I am running the latest version and it seems very responsive on my old hardware), I'm not quite sure then who it is targetting or what makes it better than other alternatives. I understand I have been harsh here and that given time I could probably work around things, but I can just go back to Elementary, Mint, or Pop OS and not have that situation. Yes I do have to do a bit of customisation in those but it is usually quick and straightforward. I would genuinely like to know what  benefits people find in Lubuntu, very possibly there is something I have not found. I do tend to either get on well with an OS or just struggle. The struggle is normally a learning process and it's good to learn but why struggle for struggles sake.

---

### Post by guiverc on 2020-10-01
> **wilfy100 said:**
> While I expect it is possible to have shortcuts to programs you use regularly there does not seem to be any obvious way to do that. My overriding feeling is that Lubuntu is not at all aimed at beginners

LXQt/Lubuntu 20.04 provides a *Quick Launch* facility, covered in the manual

[https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html?highlight=quick%20launch](https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html?highlight=quick%20launch)

I would expect beginners to find things like the [Lubuntu Manual]("https://manual.lubuntu.me/stable/index.html") handy.

> **wilfy100 said:**
> 
My understanding is that Lubuntu is moving away from running on old hardware ( though I am running the latest version and it seems very responsive on my old hardware)

Yes Lubuntu [documented a New Direction ]("https://lubuntu.me/taking-a-new-direction/")but what really qualifies as old hardware?  The last Lubuntu I could boot on a 2003-2005 pentium M/4 laptop/desktop was Lubuntu 19.04, but few people are using those *old* computers anyway (though some still do!, including myself). Lubuntu 19.04 is EOL, however Lubuntu 18.04 LTS is still supported, so I'm running Lubuntu 18.04 LTS on my old IBM Thinkpad t43 from 2005.

The desktop I'm typing this reply into is my main desktop, and it's a more modern 2009 dell desktop and it runs Lubuntu *groovy* (what will be 20.10 rather soon). Maybe this box is old, but it's what I've got, and it's great with Lubuntu.

```
dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
```

It turns out most Lubuntu users are using 3-4 year old boxes though, however yes there are still some using older boxes like myself. Whilst Lubuntu may not cater much longer for my really old pentium M laptops (I still use IBM r50p, t42p & the t43 I already mentioned), those boxes really are struggling with modern linux (older pentium Ms don't seem to like the 5.4 kernel and it's not just limited to Lubuntu; it's all OSes).

**Why use Lubuntu?**

- Lubuntu is light on resources. 

This is rather obvious and badly shown in some vids as booting up the desktop and looking at how much RAM is used. However in real life you don't use the desktop itself, but run programs on the desktop, and those programs use libraries/toolkits/frameworks that use resources. LXQt uses the Qt5 toolkit which is far lighter than GTK3, and is lighter than KDE (which also uses Qt5 but with KF5 that adds weight). Use GTK3 apps on Lubuntu and you'll lose some of the lightness though (esp. if you've limited RAM), just like using Qt apps on a GTK desktop will waste resources (esp. RAM). Even despite this Lubuntu is light on resources (cpu & RAM).  This matters to me as I use old hardware!

I liked MATE, however it became heavier as it moved from GTK2 to GTK3 so used Xubuntu & XFCE more. Xubuntu likewise became heavier as it ported from GTK2 to GTK3. I expected the same when Lubuntu moved from LXDE (GTK2) to LXQt (Qt5), but no that's far lighter than GTK3.

I like my GTK3 apps, having grown attached to them decades ago in GNOME2 days, but with 8GB on my primary desktop I don't worry (I do select apps carefully when using 1GB or 2GB of RAM, even somewhat carefully on 4GB)

- desktop configuration; can get it to how I like it

I have a normal looking panel top & bottom of monitors, and on the side of monitors I have a Unity-7 like *Quick-Launch* dock like panel that's usually hidden but allows me to quickly launch apps. Docks achieve this too, but use way more resources than the desktop doing it itself (without additional program). LXQt isn't the only DE that can achieve this, my current setup is a clone of my XFCE setup anyway.  I've been happy on KDE, was happy on GNOME2, alas struggle with GNOME3 .. but here I'd be happy on a number of DEs.

**Why not use it?**

- taste

We all have tastes, and like different flavors of ice-cream, and different user interfaces.  LXQt is designed to be light & efficient (resource wise) and only adding features where the (resource) cost is minimal. If you've got a good enough machine, plenty of resources for your apps & can afford to use a heavier base desktop, go for it if it's more to your taste.

- app chioce

If you love your GTK apps, a Qt desktop may not be more efficient for you anyway. It's the reason each desktop provides their own editor (`mousepad` for XFCE, `pluma` for MATE, `leafpad` for LXDE, `featherpad` for LXQt, `gedit` for GNOME etc) when all those apps really do the same thing, but achieve the result using different libraries/toolkits and are most efficient because they can use libs/toolkits already in RAM because the desktop itself uses it too. Choosing a desktop that matches your apps is resource efficient.

Lubuntu is the lightest of the Ubuntu *flavors* anyway, for my *oldish* hardware.

---

### Post by wilfy100 on 2020-10-02
Thanks guiverc for a well considered and informative reply. I will hold my hands up and say I did not look at the documentation. Since I only have to unplug the data cable on the hard drive with Elementary installed and connect another drive to the Sata/power pass through cables it would be easy to install Lubuntu and give it a more considered try.  I would like to do this, as a learning process as much as anything. Although dual boot normally works well, I would prefer the second drive way. I wonder if you would mind commenting on the pre-installed programs in Lubuntu. Do you make much use of these and do you leave them there or uninstall them. I suppose apart from taking a small amount of hard drive space (not really a problem) they could be left in place and explored at leisure. I will put some time and effort into this and report back in the future with hopefully a balanced and considered assessment. I have a small form factor single core pentium 2Ghz pc that would be a good candidate to put Lubuntu on but its being rather recalcitrant at the moment so its become a project to sort it out.

---

### Post by wilfy100 on 2020-10-02
Despite my optimism in my previous post, I have just spent the last 3 1/2 hours trying to get to grips with Lubuntu. It has not been fun.  I installed the Cairo dock which is very much what I am used to from other Linux distro's. Unfortunately this locks up regularly and has a thick black background stripe to it that is related to the compositor I think. I could not work around this at all. I tried to install Lubuntu tweaks but I could not do it from Discover and the terminal commands failed with a can't find it error. Other programs also failed to install as well. I admit I am at the level of google the commands and copy and paste them into the terminal in sequence. I have Lubuntu installed to a mechanical hard drive and it boots very slowly now, I know an ssd is quicker but launch is 6 times slower from the spinning rust. Discover seems rather basic compared to other program installers. While it is simple to change to another desktop background Lubuntu only seems to have one by default. All this is to say I will go back to elementary on the main drive while installing Pop os on the external one. Full disclosure is that Pop did suffer from some random reboots on this particular pc but I will give it another try. All this is just my personal choice but I don't think Lubuntu is for me.

---

### Post by guiverc on 2020-10-02
[QUOTE=wilfy100;13990040]I installed the Cairo dock which is very much what I am used to from other Linux distro's./QUOTE]

Cairo dock is a strange choice for LXQt. Did you consider how it works before adding?  ie. if you look at 

[https://packages.ubuntu.com/focal/cairo-dock](https://packages.ubuntu.com/focal/cairo-dock)

you'll note it's very tied into GNOME and GTK3, meaning it's great on a GNOME, MATE, XFCE, Cinnamon etc type base (where GNOME services and GTK3 are being used), but...  don't forget LXQt is Qt5 based

[https://packages.ubuntu.com/focal/latte-dock](https://packages.ubuntu.com/focal/latte-dock)

Latte dock makes more sense, as it's Qt5 based, however that'll still introduce KF5 (K frameworks of KDE 5) and add weight, but would be my choice if I absolutely needed to use a dock.

I use the default panels to create my 'dock' saving resources.

I mentioned I created my setup in XFCE, and my LXQt setup is just a clone (or of that setup); my box still has XFCE/Xubuntu installed, along with GNOME, so if I logout of Lubuntu/LXQt, I can login to Xubuntu/XFCE and have mostly the same look & feel. My box is also the 2009 box, so I'm not going to waste resources on cairo-dock, or even latte-dock

I mentioned toolkits & libraries in my prior post; consider the tools and programs you consider essential, and if `cairo-dock` is something you consider essential, LXQt is likely not your best DEsktop.  This has nothing to do with Lubuntu, but the desktop & application choice doesn't match (ie. you'd have the same issue with debian, opensuse, fedora..)

(*I test Lubuntu and do comparisons on issues with Debian sid firstly (but even on sid it's generally behind Lubuntu, Fedora is ahead of Debian** sid, but Fedora is not usually ahead of Lubuntu (Lubuntu's LXQt coming from Github and not upstream Debian), and finally OpenSUSE tumbleweed which is rather often ahead of Ubuntu testing. Other than differences caused by software stack age, plus the use of openbox|xfwm|.., differences are non-existent. Distribution make little difference in my opinion; the four mentioned here being the systems I have here that I use)*

Lubuntu tweaks?   Sorry I don't know what you mean here. There is no Lubuntu tweaks. I did a `apt-cache search lubuntu` to look for what you could mean and there is no tweaks in the results.  There is LXQt settings, but that still won't contain everything, as Lubuntu uses `openbox` as it's WM (window manager) however LXQt doesn't have a set WM thus no WM settings are wired into LXQt settings.

A number of wallpapers are included; 7 maybe (I forget; [one winner of the competition ]("https://lubuntu.me/lubuntu-focal-fossa-20-04-lts-wallpaper-contest/")didn't provide their HD image so it was not included), they are found in

 ```
/usr/share/lubuntu/wallpapers/
```

though that is not the directory automatically opened by LXQt wallpaper changer (this was changed with an update, but I forget when that was done), which is why you probably didn't see them.

Lubuntu booting can be made faster by disabling the snap daemon, you are comparing to non-Ubuntu's (*Ubuntu derivatives*) that have done that. Lubuntu though being a Ubuntu flavor has it enabled by default.

Not the distribution for you?  Not a problem, and understandable given the details you provide do imply a GTK+ environment/desktop sure sounds like it is more what you're used to and will be best with.

---

