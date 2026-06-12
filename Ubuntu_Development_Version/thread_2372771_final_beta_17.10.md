---
title: "final beta 17.10"
date: 2017-09-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-09-28
Hi Testers. :)

Final Beta  today. If you get time , check out the latest  current daylies of 17.10.

regards..

---

### Post by flocculant on 2017-09-28
too late - marked ready - as are most other beta2's

they'll be finishing up soon I suspect.

(The time to point milestones out is when they land, usually 2 days before they release)

---

### Post by P-I H on 2017-09-28
I installed the 27/9 version and that worked OK. However I haven't marked it as passed in the ISO tracker.
Had a problem with the search function in gnome-software. For some searches no results are presented, but if you right click outside the window , the results are shown.

---

### Post by Frogs Hair on 2017-09-28
I've been on the same installation since 9/6 without the proposed repositories enabled. There hasn't been anything reportable bug wise at all. Added a gimp wallpaper today. ;)

---

### Post by wildmanne39 on 2017-09-28
I am updating right now, so it will automatically update to the final beta correct?

---

### Post by Frogs Hair on 2017-09-28
> **wildmanne39 said:**
> I am updating right now, so it will automatically update to the final beta correct?
Yes

---

### Post by wildmanne39 on 2017-09-28
> **Frogs Hair said:**
> Yes
Thanks Frogs Hair.

---

### Post by Chanath on 2017-09-28
Didn't download  the daily today. Simply upgraded all installs. No problems in any of them.
Don't have a default Ubuntu.

---

### Post by ventrical on 2017-09-29
> **flocculant said:**
> too late - marked ready - as are most other beta2's

they'll be finishing up soon I suspect.

(The time to point milestones out is when they land, usually 2 days before they release)

Oh. I was going by this:

---

### Post by flocculant on 2017-09-29
> **ventrical said:**
> Oh. I was going by this:

Yea that's always a bit confusing.

Basically:

Cron stops for participating flavours on Tuesday at some point. (Dependent on tz of person dealing with the Canonical side of things)
Testing.
Release milestone Thursday.

---

### Post by Chanath on 2017-09-29
Downloaded the latest daily just for testing. Wanting to experiment took over common sense. Kept the Dock and the top panel intact for the moment.

1) I find the Activities button is useless, where it is. All what it does is open the Skippy-xd like "spread all open windows" and show the dock, whatever its name is. Its ok, if you have a tiny screen, like in a netbook, but for any other screen its a wrist-killer. The best place for it would've been on the bottom left corner (for right hand users).

2) I also find less use of the top panel. Just because its holding the clock and notification area, doesn't mean its valuable, where it is. Oh, you have to go to the top right corner to logout, reboot or shutdown. Not enough reasons to have a practically useless top panel. In Unity, it held the Global Menu. 

3) Why do I need a Dock? Just to hold some icons? If I can minimize, maximize from the Dock, it would be somewhat useful. Okay, it holds the "Show Applications" button. Not enough to be useful. If what's on top right on the top panel is also fixed to the dock, it would be more useful. Just holding icons on the dock doesn't help much. You can only click on an icon to open an  app, but can't minimize it. Some one might say, you can open more instances of the same app from the dock. You can, of course. But you can also do that from the full screen menu. If you know what applications you have in your system, then it doesn't really matter, if you don't have the "Show Applications" button. 

Okay, now that I have this default Ubuntu, how can I make it easy for my wrist? 

By installing (1) a hotcorner to the bottom left corner. One way is to use an available extension, Custom Corner (quite old, but very good) or use an old script for Openbox using xdotool. And by (2) auto hiding the top panel and the Dock. None of them are needed for day to day work. You can even logout, reboot and shutdown from the bottom left corner and the ful screen menu. If you want to use the eye-candy swarming effect, you can always click on the "Show Applications" button, which comes out, when you move the cursor to the left bottom corner.

Clock? Well, I have one on the wrist, one on the table and one on the wall.

So, considering that I didn't get rid of the Dock or the top panel, and that I'd "test" the default Ubuntu, I made myself an easy method, a wrist saving method. I can quite easily forget that I am using Gnome-Shell as a shell, but just a full screen (eye-candy) menu and a bottom left "hotcorner" with a menu button ( Show Applications) also near that corner. And, everything is hidden from the view, leaving me with full screen to use. When the cursor goes there, everything jumps out, even though I won't touch most of the stuff that jumps out for the whole working time. Lovely!

---

### Post by slickymaster on 2017-09-29
@Chanath:
Please keep the thread on topic, which is about testing the upcoming *buntu release and not personal views on how any specific flavor should come.

---

### Post by Chanath on 2017-09-29
Contd...

Some screenies.

1st picture: when nothing is there, it looks somewhat ugly with the Dock going under the top panel. Well, who is going to keep looking at a empty screen whole day?!

2nd picture: with open apps, and when the cursor goes to the bottom left corner. Still the Dock is under the top panel, bit ugly, but I am not looking at it, all I want is to move from one app window to the other or open another app. I can do that by writing, maybe two letters.

3rd picture: with logout, without going up to the top right corner. All I have to do is push the Enter key. Same with reboot and shutdown.

I haven't gone with cursor to any higher than bottom left corner. This way, I used the default Ubuntu the whole working day. Never touched the Dock and the top panel. Opened an app bu going to the left bottom corner and 2-4 letters.

---

### Post by Chanath on 2017-09-29
> **slickymaster said:**
> @Chanath:
Please keep the thread on topic, which is about testing the upcoming *buntu release and not personal views on how any specific flavor should come.

Okay!
I have commented on Unity, Gnome, Xubuntu, Kubuntu and default Ubuntu. Maybe, enough testing.:)

---

### Post by ventrical on 2017-09-29
> **Chanath said:**
> Okay!
I have commented on Unity, Gnome, Xubuntu, Kubuntu and default Ubuntu. Maybe, enough testing.:)

Thanks for all the work you have done. All these things added to the knowledge base is what makes ubuntu better and helps QA direct developers on how to make ubuntu more user_friendly.

Regards..

---

### Post by bikerjoe647 on 2017-10-01
Hi all. I've been using 17.10 on an AMD 1700x Gigabyte AB350M-D3H since Alpha 2. I jumped to it because I was having a hell of a time with 17.04 and the new chipset. Just to get 17.04 to install, I had to recompile the kernel with various disabled options, performance wasn't ever right, just a headache.

Since 17.10 alpha 2, it has been pretty solid. I did have one random freeze where I couldn't log back in. I tried to tweak Gnome a bit by installing Gnome Tweaks, and it jacked up my gui (I kinda figured that would happen). So yesterday I tried to update to Beta 2, and it made it to where I could no longer successfully boot. I'd get one of two paths. 1) I would hit login loop. or 2) I'd get the following

```
[  OK  ] Started systemd-resolved-update-resolveconf.service
[FAILED] Failed to start systemd-resolved-update-resolveconf.service.
See 'systemctl status systemd-resolved-update-resolvconf.service' for details.
[  23.263722] r8169 0000:07:00.0: AMD-Vi: Event logged [IO_PAGE_Fault..... 
```This is off of a fresh install, replacing what is on the drive with a fresh Ubuntu install. Is it possible someone can forward me to the best place to report bugs? I'm new to the Ubuntu beta world. I have found this: [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash), but it doesn't really pertain to what I need to report. The rest of the docs I have found have suggested reporting from Ubuntu itself, which I can't get going. 

Otherwise, just wanted to say thanks to everyone who has done a great job on this release. I'm probably a small base with this problem.

---

### Post by Cavsfan on 2017-10-02
I was using Ubuntu with Gnome early on but, have been running Xubuntu since the ISO was able to be installed, about a week ago more or less, and absolutely zero bug popups or any problems.

I take it Xubuntu went with X.org and no option for Wayland.
```
cavsfan@cavsfan-Le-Beast:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu Artful Aardvark (development branch)"
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Artful Aardvark (development branch)"
VERSION_ID="17.10"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful
```

```
cavsfan@cavsfan-Le-Beast:~$ inxi -Fzx
System:    Host: cavsfan-Le-Beast Kernel: 4.13.0-12-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 serial: N/A
           BIOS: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22741
           clock speeds: max: 2842 MHz 1: 2842 MHz 2: 2842 MHz 3: 2842 MHz 4: 2842 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.3 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce 9800 GT/PCIe/SSE2 version: 3.3.0 NVIDIA 340.104 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-12-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: ens33 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (22.9% used)
           ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB
Partition: ID-1: / size: 14G used: 6.3G (47%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.0C mobo: 30.0C gpu: 0.0:44C
           Fan Speeds (in rpm): cpu: 2772 fan-1: 2242 fan-3: 2722 fan-4: 0
Info:      Processes: 174 Uptime: 16 min Memory: 793.2/3948.0MB Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37 
```

[ATTACH=CONFIG]276937[/ATTACH]

---

### Post by Chanath on 2017-10-02
Being using Kubuntu 17.10 beta fully upgraded in an MBR and a UEFI laptop. No trouble at all, even with eye-candy on. Btw, no problem with Xubuntu too.

---

### Post by Chanath on 2017-10-02
> **Cavsfan said:**
> I take it Xubuntu went with X.org and no option for Wayland.

Trying find out what's wrong (or right) with X, I stumbled upon this, [http://www.std.org/~msm/common/protocol.pdf](http://www.std.org/~msm/common/protocol.pdf) with the heading "Why X Is Not Our Ideal Window System."

I'll try to read it, even though I might not understand all that technical stuff in it. 
But, I liked one simple line there, "We  come  to  praise X,  not  to  bury  it."

---

### Post by flocculant on 2017-10-02
> **Cavsfan said:**
> 

I take it Xubuntu went with X.org and no option for Wayland...

No option. Not even  currently discussing it.

---

### Post by lammert-nijhof on 2017-10-02
Loaded and/or updated all to the final Beta, so Ubuntu, Xubuntu, Lubuntu and Ubuntu Mate. I run all distros in Virtualbox and I'm moving all my work to Virtual Machines. Easier to keep laptop and desktop aligned and better security e.g. separate VMs for browsing and banking. Xubuntu, Lubuntu and Ubuntu Mate look very familiar from old times and work perfectly in a VM with 3D acceleration enabled. Ubuntu has an issue with 3D acceleration, the desktop freezes after 10-20 minutes. I have to power off the VM to be able to continue. Is there a relative simple way to generate a crash dump? CTR+ALT+F2 is caught by the Host-Linux not by the VM-Linux. Is there a way to start such a CLI session directly after booting the VM and then switch between CLI and GUI sessions?

---

### Post by Chanath on 2017-10-02
> **lammert-nijhof said:**
> Loaded and/or updated all to the final Beta, so Ubuntu, Xubuntu, Lubuntu and Ubuntu Mate. I run all distros in Virtualbox and I'm moving all my work to Virtual Machines. 

You must be using a Linux distro as the host. Do your problems also there in the host Linux? After all, your problems might be from VirtualBox, rather than from the Linux distros. Btw, you can easily use Linux for banking without much (or any) fear. Maybe, the bank's encryption system is not that secure. Browsing? What's to be worried about browsing?

---

