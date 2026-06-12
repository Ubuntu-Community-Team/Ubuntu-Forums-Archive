---
title: "Rolling Release vs. Fixed Release"
date: 2023-11-22
forum: The Cafe
---

### Post by Shibblet on 2023-11-22
Ubuntu is classified as a "Fixed" release Distro... but is it really?

Think about it... Software updates come out on a regular schedule.  Even Kernel updates come out when they are available.
There are "milestone" (SuSE phrasing) releases for the LTS versions as well.  22.04.1, 22.04.2, 22.04.3, etc.

I run Manjaro as well, and the software releases come out when available.  Same with Kernel updates.
There are full "updates" in the ISO as well.  21.3.0, 22.1.3, 23.0.3, etc.  The releases aren't just every April and October.  ;-)

So, I ask, what's REALLY the big difference in running a rolling release, or having a fixed Distro?

---

### Post by #&amp;thj^% on 2023-11-22
> **Shibblet said:**
> 
So, I ask, what's REALLY the big difference in running a rolling release, or having a fixed Distro?

Stability for the most important parts. Rolling Distro's, and you mention Arch or Arched/based are of a higher tested than say Point releases.
Fixed also includes A big hassle upgrading from version to version 20.04 to 22.04 to 24.04 with PPA's and Hardware differences. rolling is almost seamless. :P
I'm actually running a Mock rolling Ubuntu now, and it keeps me very busy fixing and mending (stitching it back together).
Now I can't speak on Manjaro, but my Arch systems just keep banging away. Very Happy with that out come.
BTW My Arch install is over 7 years old now. Little fuss and less muss. ;)
Let the foul worded reply's begin. IJDK :D

---

### Post by Shibblet on 2023-11-22
> **1fallen said:**
> Stability for the most important parts. Rolling Distro's, and you mention Arch or Arched/based are of a higher tested than say Point releases.
Fixed also includes A big hassle upgrading from version to version 20.04 to 22.04 to 24.04 with PPA's and Hardware differences. rolling is almost seamless. :P
I'm actually running a Mock rolling Ubuntu now, and it keeps me very busy fixing and mending (stitching it back together).
Now I can't speak on Manjaro, but my Arch systems just keep banging away. Very Happy with that out come.

I didn't know Arch's repos were "higher tested" than other releases.  This makes it understandable as to why it's so stable.

So, it's fair to say you prefer a rolling release?

> **1fallen said:**
> BTW My Arch install...
Translation:  [COLOR="#0000FF"][SIZE=4]**"BTW, I use Arch."**[/SIZE][/COLOR]  ;-)

---

### Post by #&amp;thj^% on 2023-11-22
> **Shibblet said:**
> 
Translation:  [COLOR="#0000FF"][SIZE=4]**"BTW, I use Arch."**[/SIZE][/COLOR]  ;-)

Is that your "Translation" see my signature.
And it is no secrete that I prefer Rolling Arch, and some Arch Based, just not Manjaro, they don't follow Arch.
Don't get me wrong here, I think Phil is a gifted Programmer. (Lead Developer on Manjaro) it's just not for me. :)
I use or test a handful of OS's, but my production machines are most certainly Arch. ;)

---

### Post by deadflowr on 2023-11-22
> So, I ask, what's REALLY the big difference in running a rolling release, or having a fixed Distro?


Support ends eventually on a fixed release.

---

### Post by guiverc on 2023-11-22
> **Shibblet said:**
> Ubuntu is classified as a "Fixed" release Distro... but is it really?

There are "milestone" (SuSE phrasing) releases for the LTS versions as well.  22.04.1, 22.04.2, 22.04.3, etc.


I'll just give my thoughts on parts.

Ubuntu I see as using a *stable release* model, rather than *fixed*; but that's probably only wording.

Ubuntu 22.04 is always 22.04; regardless of 22.04.1/22.04.3; with the last detail showing only the re-release of an updated ISO.

eg. quoting from a [22.04.3 release statement]("https://fridge.ubuntu.com/2023/08/11/ubuntu-22-04-3-lts-released/") there is

> As usual, this point release includes many updates and updated  installation media has been provided so that fewer updates will need to  be downloaded after installation. These include security updates and  corrections for other high-severity bugs, with a focus on maintaining  stability and compatibility with Ubuntu 22.04 LTS.

If you're using the [*hardware enablement* stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), that upgrade does mean a change of kernel (*22.04.2 used the kernel from 22.10, 22.04.3 replaced it with the kernel from 23.04*) but that's just an alternate kernel stack option provided by Ubuntu LTS releases (*default for Ubuntu Desktop since 20.04*) that has been offered for more than a decade now.

The .1, .2 etc. is not really part of the Ubuntu cycle; only relating to media being respun.

Ubuntu 23.10.1 Desktop media already exists; because *translation* *flaws* were found on the 23.10 media; thus causing the creation of 23.10.1 media for Ubuntu Desktop (*ubuntu-desktop-installer ISO only*), and Ubuntu Budgie (*ubuntu-desktop-installer only*), but I don't see that as related to any *milestone*. Ubuntu 17.10.1 also needed to exist too.

I'm on the *development *release of Ubuntu, currently *noble* which will be deemed as stable when it reaches *Release Candidate* stage and thus renamed to Ubuntu 24.04 LTS.  My release is as pretty much close to what I can get to *rolling* on Ubuntu (*like my Debian testing/sid box is*), but its still not a *rolling *system (*in my eyes anyway; both Debian & Ubuntu are stable release based*).

An OpenSuSE *tumbleweed* box besides me is *rolling*, in my case the GUI is broken, and I've currently little desire to spend energy on it. Rolling systems in my experience are more work, even more than my sitting on a *development* release (*testing for Debian*) of a *stable release* model distribution. 

Due to the constant change of upstream, the closer you are to *cutting edge* the more problems you'll encounter, where as on *stable release* systems most of those issues are only encountered when you *release-upgrade*  (*though can also be experienced with HWE kernel stack changes too, but that is optional on Ubuntu and one reason why my LTS boxes have both GA + HWE installed*).

Both *rolling *and *stable* release systems involve changes, but those using *rolling* incur changes constantly, where as *stable* release users choose to have them on a table they can predict (*ie. release-upgrade and/or kernel stack change for HWE users**; both of which are predictable in month maybe plus/minus a week for a Ubuntu release, and two-three weeks for HWE stack change*).  My choice of using Ubuntu *development* (or Debian *testing/sid*) puts me between *rolling* and *stable*, but its still closer to *stable* in my view than *rolling*.

---

### Post by ajgreeny on 2023-11-23
A couple of years ago I ran an instalation of the Arch derivative Arcolinux.
It ran well for quite a few months, maybe a year, but then out of the blue everything went wrong and I could not get it to run any further updates. 
I searched for a long time but it all got to be just too much trouble compared to my main box running Xubuntu 20.04 at that time which never let me down.
So for me the stability of the Ubuntu "fixed release" system is more dependable an thatvis where i shall stay.

---

### Post by Rubi1200 on 2023-11-23
@ajgreeny

I, too, tried ArcoLinux briefly until running into too many issues, both with installs and upgrades. I had the feeling the developer was spreading himself too thin with all the various versions.

I highly recommend you give EndeavourOS a spin. Good community and solid system with very few issues (at least for me).

---

### Post by ajgreeny on 2023-11-24
Yes, I tried Endeavour after Arcolinux and it was good but I'm happy to report that Xubuntu remains my tried and tested solid system that has never caused problems for me.
I totally remove the complete snap infrastructure so don't have any of the difficulties some users see with them!

---

### Post by grahammechanical on 2023-11-24
How would this question be answered by those administering computers for a commercial organisation?

I imagine the preference would be for a User Interface that stays the same for a number of years. It would delay the re-training of employees. Which is why Ubuntu Long Term Support releases (5 years) are better for commercial organisations than the standard (9 month) releases. With a Ubuntu Pro subscription the User Interface would be fixed for 10 years.

I imagine with a rolling release changes to the Gnome desktop would come through with any update and without warning. There is a difference between the UI of Ubuntu 20.04/22.04 and Ubuntu 23.10.

Balance that advantage against the disadvantage of upgrading the Ubuntu version to the latest LTS on every computer the organisation uses.

Does anyone have experience of the risks and benefits of using rolling release in the commercial setting?

Regards

---

### Post by Shibblet on 2023-11-24
> **1fallen said:**
> Is that your "Translation" see my signature.
Dude... just playing with you.

> **1fallen said:**
> And it is no secrete that I prefer Rolling Arch, and some Arch Based, just not Manjaro, they don't follow Arch.
Don't get me wrong here, I think Phil is a gifted Programmer. (Lead Developer on Manjaro) it's just not for me. :)
I use or test a handful of OS's, but my production machines are most certainly Arch. ;)
No, they don't.  The only "following" that Manjaro does, is access the AUR.

> **deadflowr said:**
> Support ends eventually on a fixed release.
But doesn't that follow the LTS Kernel support?  Wouldn't that be the same for a rolling release?

---

### Post by #&amp;thj^% on 2023-11-24
> **Shibblet said:**
> Dude... just playing with you.


Just stop it then, I'm a snowflake. :lolflag::lolflag:
I just feel Arch gets a nasty rapport from those other Non following Arch/based distros.

So far I see those who have tried an Arch/Based system that dose not follow Arch, and was left with a bad taste. (There's a hint right there)
So that is a weak excuse to fault Arch when  someone else is at hand deciding what you get and how you get it. (That just has to make sense)

I've put in the time and effort on Arch, and that's where I remain, there are those who put in the time and effort on Ubuntu and want to remain there. (It's all good I don't judge)
I still keep Ubuntu for ZFS it just works better on Ubuntu. (I use the strength's and weakness for my choices)

I've yet to meet a Man, Woman or Child, who's life wasn't changed from a new perspective.

---

### Post by Shibblet on 2023-11-27
> **1fallen said:**
> Just stop it then, I'm a snowflake. :lolflag::lolflag:
Snowflakes use Arch? 

> **1fallen said:**
> I just feel Arch gets a nasty rapport from those other Non following Arch/based distros.
It's from all the snowflakes...  J/K

It's more likely from the fact that Arch has to be "built" during installation, and it's not as simple as a walkthrough GUI.  Could be worse... could be Gentoo.

> **1fallen said:**
> So far I see those who have tried an Arch/Based system that dose not follow Arch, and was left with a bad taste. (There's a hint right there)
So that is a weak excuse to fault Arch when  someone else is at hand deciding what you get and how you get it. (That just has to make sense)
Manjaro, Endeavor, and Garuda are the most popular of the "Arch Based" distros.  And you can learn a LOT from the Online Arch User-Manual... it's one of the best.  Heck, I've learned a ton from it, and  a lot of the information in there applies to other distros as well... e.g. Kubuntu.

> **1fallen said:**
> I've put in the time and effort on Arch, and that's where I remain, there are those who put in the time and effort on Ubuntu and want to remain there. (It's all good I don't judge)
I still keep Ubuntu for ZFS it just works better on Ubuntu. (I use the strength's and weakness for my choices)
That's awesome man... I have similar issues.  It's great that users of different distributions still like to come to the Ubuntu forms to help out.  
I like Manjaro, and Arch, but they're my "tinker" distros.  I always come back to Kubuntu for my "Daily-Driver."

> **1fallen said:**
> I've yet to meet a Man, Woman or Child, who's life wasn't changed from a new perspective.
New Distro... Titanic Linux.  Women and Children First.

---

### Post by #&amp;thj^% on 2023-11-27
> **Shibblet said:**
> Snowflakes use Arch? 

Nope only the elite. :P and you know I'm kidding.

> **Shibblet said:**
> 
It's more likely from the fact that Arch has to be "built" during installation, and it's not as simple as a walkthrough GUI.  Could be worse... could be Gentoo.
Exactly like that, built by you for you. ;)

> **Shibblet said:**
> 
Manjaro, Endeavor, and Garuda are the most popular of the "Arch Based" distros.  And you can learn a LOT from the Online Arch User-Manual... it's one of the best.  Heck, I've learned a ton from it, and  a lot of the information in there applies to other distros as well... e.g. Kubuntu.
From your list for accuracy "Endeavor," is the only one you show there that dose follow Arch.
> **Shibblet said:**
> 
That's awesome man... I have similar issues.  It's great that users of different distributions still like to come to the Ubuntu forms to help out.  
I like Manjaro, and Arch, but they're my "tinker" distros.  I always come back to Kubuntu for my "Daily-Driver."
I started with Arch straight away, also tinkering but grew to love it.

One of the Developers had told me and this is a rough quote "No Self respecting Archer would ever use a GUI installer" (Please Note I don't see it or feel that way)


New Distro... Titanic Linux.  Women and Children First.[/QUOTE]

---

### Post by donald187 on 2023-11-27
What does it mean "to follow Arch"?  I did a quick Google search but didn't come up with anything.

I installed Arch a couple of times for kicks.  Just to see if I could.

---

### Post by #&amp;thj^% on 2023-11-27
> **donald187 said:**
> What does it mean "to follow Arch"?  I did a quick Google search but didn't come up with anything.

I installed Arch a couple of times for kicks.  Just to see if I could.

It means just that, all Arch software/core, it dose however allow for some new to Arch users, a few community tools, mostly GUI's like the Welcome Screen and some preinstalled tools to deal with the pacman software manager and Preinstalled AUR managers. (But they follow Arch and not applications written by others)
Also themes, and customized DE's Plasma, XFCE4, Gnome.
I think I use about 8 GUI's for my Work System, and another, I use a full desktop for the family.

---

### Post by donald187 on 2023-11-27
> **1fallen said:**
> It means just that, all Arch software/core, it  dose however allow for some new to Arch users, a few community tools,  mostly GUI's like the Welcome Screen and some preinstalled tools to deal  with the pacman software manager and Preinstalled AUR managers. (But  they follow Arch and not applications written by others)
Also themes, and customized DE's Plasma, XFCE4, Gnome.
I think I use about 8 GUI's for my Work System, and another, I use a full desktop for the family.
Ok, thanks. :)

---

### Post by kevdog on 2023-11-30
Arch is really nice distro -- I'm using a bunch of Arch and Ubuntu LTS VMs for server management.  I'm not sure if one distro is "better" than the other, however when things break or you need to do some advanced configuration in some /etc config file, the Arch Wiki is my absolute hands down go to source for knowledge.  Although most of the information from the Wiki could be applied to Ubuntu or any other Linux distro, the Arch Wiki is hands down so valuable it makes running Arch just very easy.  Running ZFS on root on most installations which was kind of difficult to set up and it's kind of a pain with kernel upgrades, but systems really work well.

---

### Post by #&amp;thj^% on 2023-11-30
Thanks kevdog I enjoyed your post. ;)
ZFS on arch as you mention, will be at times all hands on deck effort However Ubuntu just had a near show stopper with zfs.
I "try" to do my best with words, but sometimes the bad wolf gets fed instead of the "Good Wolf". (I guess he just needs to came out and play at the wrong time):lolflag:

---

### Post by lammert-nijhof on 2023-12-02
If you understand software development, you know, that a rolling release will create more bugs per year that a fixed release. 
That is, why I use fixed releases.  So I use Ubuntu since 2008.  In 2018 I made 2 important changes, I stored all my data and VMs on ZFS and I moved all my application to 6 VMs (4x Linux and 2x Windows). Those Windows Releases are XP Home and 11 Pro, while the Linux releases are a mix of Ubuntu flavors and releases, like Xubuntu 22.04 LTS; Ubuntu Unity and Ubuntu 23.10 and even Ubuntu 16.04 ESM. For Ubuntu 16.04 ESM I installed the latest stable snaps for Firefox and LibreOffice today :) 

I use Ubuntu 16.04 ESM for banking.  To optimize security; that VM is **encrypted** by Virtualbox; the firewall is **closed** for inbound traffic and most important it is used **exclusively** for banking.  Why that old stuff?  Simply because it only receives security updates. With fewer updates a system will be more reliable, because programmers make errors and a certain percentage of the changes/bug-fixes will result in new bugs. That also explains, why rolling releases will be less reliable than fixed releases.

---

### Post by agentl074 on 2023-12-31
[SIZE=2][FONT=arial]I would just recommend using the zero LTS release when it comes since it will keep you on the LTS kernel; whereas, if you install a point release of LTS, it will install the HWE kernel and keep you on that until the next LTS kernel.

You can install the LTS kernel ([COLOR=#0C0D0E]sudo apt install linux-image-generic[/COLOR][COLOR=#0C0D0E])[/COLOR], grub into that via pressing ctrl+alt+delete after splash screen, and then use sudo apt autoremove to remove the HWE kernel.[/FONT][/SIZE]

---

### Post by TenPlus1 on 2024-01-03
I tend to run a mock rolling release bu updating sources.list when the new  repo's for the next release is available and doing careful updates to make sure my system doesn't break, and so far so good.

Also Rolling Rhino is a good Ubuntu distro that does a good job of this as well: [https://rhinolinux.org/](https://rhinolinux.org/)

---

### Post by #&amp;thj^% on 2024-01-05
> **TenPlus1 said:**
> I tend to run a mock rolling release bu updating sources.list when the new  repo's for the next release is available and doing careful updates to make sure my system doesn't break, and so far so good.

Also Rolling Rhino is a good Ubuntu distro that does a good job of this as well: [https://rhinolinux.org/](https://rhinolinux.org/)

+1
Well it looks like I got my wish a Rolling Model of Ubuntu.

They released it on DW (Distro Watch) on 12/20/2023.
There was a change in the default DE instead of Gnome they went with XFCE another plus for me.
It has the Global Menu Top panel and Rhino features a custom meta package manager which unifies Deb, Pacstall and Flatpak software management. (it dose have an option for snaps as well but not here on mine)

Home Page: [https://rhinolinux.org/](https://rhinolinux.org/)
FTR, I won't encourage anyone to use it as production system. (But I will)

So far I'm very impressed with how Adaptive to any workflow I throw at it.

Note there is a very slight learning curve to it, though most here will sail along just fine.
naming they went with Rhino Linux which I prefer over Rolling Rhino.
```
inxi -Fxxz
System:
  Kernel: 6.6.7-060607-generic arch: x86_64 bits: 64 compiler: N/A
    Desktop: Xfce v: 4.18.1 tk: Gtk v: 3.24.36 wm: xfwm dm: LightDM Distro: Rhino
    Linux 2023.4 (mainline) devel
Machine:
  Type: Laptop System: LENOVO product: 82JW v: Legion 5 15ACH6
    serial: <superuser required> Chassis: type: 10 v: Legion 5 15ACH6
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0T76465 WIN
    serial: <superuser required> UEFI: LENOVO v: HHCN32WW date: 03/07/2023
Battery:
  ID-1: BAT0 charge: 58.4 Wh (95.0%) condition: 61.5/60.0 Wh (102.5%)
    volts: 17.3 min: 15.4 model: Celxpert L20C4PC0 serial: <filter>
    status: not charging
CPU:
  Info: 6-core model: AMD Ryzen 5 5600H with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 3 rev: 0 cache: L1: 384 KiB L2: 3 MiB L3: 16 MiB
  Speed (MHz): avg: 739 high: 2228 min/max: 400/4280 cores: 1: 400 2: 400
    3: 400 4: 400 5: 400 6: 1649 7: 400 8: 2228 9: 400 10: 400 11: 400 12: 1395
    bogomips: 79048
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] vendor: Lenovo
    driver: nvidia v: 545.29.06 arch: Ampere pcie: speed: 5 GT/s lanes: 8 ports:
    active: none off: HDMI-A-1,eDP-1 empty: DP-1,DP-2 bus-ID: 01:00.0
    chip-ID: 10de:25e0
  Device-2: Bison Integrated Camera driver: uvcvideo type: USB rev: 2.0
    speed: 480 Mb/s lanes: 1 bus-ID: 1-3:3 chip-ID: 5986:2137
  Display: x11 server: X.Org v: 21.1.10 compositor: xfwm v: 4.18.0 driver:
    X: loaded: nvidia unloaded: fbdev,modesetting,vesa alternate: nouveau
    gpu: nvidia,nvidia-nvswitch display-ID: :0.0 screens: 1
  Screen-1: 0 s-res: 3840x1080 s-dpi: 96
  Monitor-1: eDP-1 mapped: DP-4 note: disabled pos: primary,left
    model: AU Optronics 0xd1ed res: 1920x1080 dpi: 142 diag: 394mm (15.5")
  Monitor-2: HDMI-A-1 mapped: HDMI-0 note: disabled pos: right model: 32S321
    res: 1920x1080 dpi: 70 diag: 815mm (32.1")
  API: EGL v: 1.5 platforms: device: 0 drv: nvidia device: 2 drv: swrast
    gbm: drv: nvidia surfaceless: drv: nvidia x11: drv: nvidia
    inactive: wayland,device-1
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: nvidia mesa v: 545.29.06
    glx-v: 1.4 direct-render: yes renderer: NVIDIA GeForce RTX 3050 Ti Laptop
    GPU/PCIe/SSE2
Audio:
  Device-1: NVIDIA driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s
    lanes: 8 bus-ID: 01:00.1 chip-ID: 10de:2291
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor vendor: Lenovo driver: N/A
    pcie: speed: 8 GT/s lanes: 16 bus-ID: 05:00.5 chip-ID: 1022:15e2
  Device-3: AMD Family 17h/19h HD Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel pcie: speed: 8 GT/s lanes: 16 bus-ID: 05:00.6 chip-ID: 1022:15e3
  Device-4: DisplayLink UOEOS Laptop Dock driver: cdc_ncm,snd-usb-audio
    type: USB rev: 3.2 speed: 5 Gb/s lanes: 1 bus-ID: 2-2.2.1:5
    chip-ID: 17e9:4307
  API: ALSA v: k6.6.7-060607-generic status: kernel-api
  Server-1: PipeWire v: 1.0.0 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Lenovo driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1
    port: 2000 bus-ID: 03:00.0 chip-ID: 10ec:8168
  IF: eno1 state: down mac: <filter>
  Device-2: Realtek RTL8852AE 802.11ax PCIe Wireless Network Adapter
    vendor: Lenovo driver: rtw89_8852ae v: kernel pcie: speed: 2.5 GT/s lanes: 1
    port: 1000 bus-ID: 04:00.0 chip-ID: 10ec:8852
  IF: wlp4s0 state: down mac: <filter>
  IF-ID-1: enx70b3d55c01b3 state: up speed: 1000 Mbps duplex: half
    mac: <filter>
  IF-ID-2: surfshark_ipv6 state: unknown speed: N/A duplex: N/A
    mac: <filter>
  IF-ID-3: surfshark_wg state: unknown speed: N/A duplex: N/A mac: N/A
Bluetooth:
  Device-1: Realtek Bluetooth Radio driver: btusb v: 0.8 type: USB rev: 1.0
    speed: 12 Mb/s lanes: 1 bus-ID: 3-4:3 chip-ID: 0bda:4852
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 6.15 TiB used: 3.61 TiB (58.7%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 980 PRO 1TB size: 931.51 GiB
    speed: 63.2 Gb/s lanes: 4 serial: <filter> temp: 30.9 C
  ID-2: /dev/sda vendor: Crucial model: CT500P5S SD8 size: 465.76 GiB
    type: USB rev: 3.2 spd: 5 Gb/s lanes: 1 serial: <filter>
  ID-3: /dev/sdb vendor: PNY model: CS2311 1TB SSD size: 931.51 GiB
    type: USB rev: 2.1 spd: 480 Mb/s lanes: 1 serial: <filter>
  ID-4: /dev/sdc vendor: Sabrent model: Sabrent size: 238.47 GiB type: USB
    rev: 2.1 spd: 480 Mb/s lanes: 1 serial: <filter>
  ID-5: /dev/sdd vendor: Western Digital model: WD40NDZW-11MR8S0
    size: 3.64 TiB type: USB rev: 3.1 spd: 5 Gb/s lanes: 1 serial: <filter>
Partition:
  ID-1: / size: 238.17 GiB used: 7.89 GiB (3.3%) fs: btrfs dev: /dev/sdc2
  ID-2: /boot/efi size: 299.4 MiB used: 7.7 MiB (2.6%) fs: vfat
    dev: /dev/sdc1
  ID-3: /home size: 238.17 GiB used: 7.89 GiB (3.3%) fs: btrfs
    dev: /dev/sdc2
Swap:
  ID-1: swap-1 type: file size: 512 MiB used: 0 KiB (0.0%) priority: -2
    file: /swap/swapfile
Sensors:
  Src: /sys System Temperatures: cpu: 42.4 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Processes: 336 Uptime: 53m Memory: total: 16 GiB available: 15.47 GiB
  used: 2.42 GiB (15.6%) Init: systemd v: 253 target: graphical (5)
  default: graphical Compilers: gcc: 13.2.0 alt: 13 Packages: 1458 pm: dpkg
  pkgs: 1451 pm: flatpak pkgs: 7 Shell: Bash v: 5.2.21
  running-in: xfce4-terminal inxi: 3.3.31

```

---

### Post by Dennis N on 2024-01-05
My experience with Rhino (yours may vary)

I installed it in a VM, which completed. Then I completed the setup. After that, right-clicked on the Desktop hoping to find some different wallpaper, and the OS locked up and was unresponsive. Screenshot below taken from host OS. I had to force shut down. Not encouraging. Back to real Ubuntu.

Edit: Started it up again, and this time the OS did not lock up doing the same thing.

---

### Post by #&amp;thj^% on 2024-01-05
Yep it runs a ton better on real installs. I also found it very buggy in any VM's or KVM.
I  was asked to give it another go and it is *perfect so far* I t won't be for everyone, and needs to mature a bit more, released  12/20/2023
I just have this kind of mind set, made for me. ;)

---

### Post by Dennis N on 2024-01-05
Well, so far so good. But I see no guidance on how to find and install new software besides what the Application Grid shows. In the grid, I see no GUI software manager that a new user would expect to see. Also, there is no application menu with applications by category that I can find.

---

### Post by #&amp;thj^% on 2024-01-05
It's a different XFCE experience for sure lol
on the left dock (Plank) is a grid for a Gnome like menu, and above that there is a search Icon for Apps installed.
At least your trying it.
BTW You can add the Whisker Menu to the Top Panel.

---

### Post by Dennis N on 2024-01-05
There was an [article about Rhino]("https://www.zdnet.com/article/rolling-rhino-delivers-a-rolling-release-take-on-ubuntu-desktop/") back in May 2022. So it's been out awhile.

---

### Post by #&amp;thj^% on 2024-01-05
But it stopped for a bit, then they went full tilt on working with it again. (New folks working on it)
Most of that information in the link is outdated now.....progress is fast on this one.
I also posted on it here: [https://ubuntuforums.org/showthread.php?t=2481166](https://ubuntuforums.org/showthread.php?t=2481166)

---

### Post by Dennis N on 2024-01-05
Well, I wish the developers all the best on their work. It isn't going to be easy. I agree with what you said in the other thread:

> New users will find it very confusing. Out of ten New to Linux and Ubuntu 8 of them threw in the towel.
6 out 6 old timers found it useful. 

I do like the rolling release concept. I've had Manjaro in my stable of OSes since 2017.

---

### Post by #&amp;thj^% on 2024-01-05
Thanks for your input Dennis N, I enjoy what and how you post here in UF

---

