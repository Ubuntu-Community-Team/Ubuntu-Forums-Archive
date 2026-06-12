---
title: "gnome classic desktop extension  with xenial xerus daily/current"
date: 2015-11-07
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-11-07
It's news to me  but it looks like 'gnome classic' desktop is now [s]preinstalled[/s] in ubuntu-gnome xenial xerus desktop.

Regards..

---

### Post by sammiev on 2015-11-07
Just tried it and came up with a blank screen after entering in my password. If I clicked certain spots on the screen, I was able to bring up a choose here and there and the shut down.

---

### Post by ventrical on 2015-11-07
> **sammiev said:**
> Just tried it and came up with a blank screen after entering in my password. If I clicked certain spots on the screen, I was able to bring up a choose here and there and the shut down.

Wow .. thanks ! 

 It works like some sort of mini version of gnome-shell in some sort of container. It's really weird but it works great on this hardware:

```

ventrical@ventrical-asus-gnome:~$ inxi -Fxz
System:    Host: ventrical-asus-gnome Kernel: 4.2.0-16-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Gnome 3.18.1 (Gtk 3.16.7-0ubuntu5)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0
           Display Server: X.Org 1.17.2 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8
           GLX Version: 3.0 Mesa 11.0.4 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.2.0-16-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (7.4% used)
           ID-1: /dev/sda model: WDC_WD800JD size: 80.0GB temp: 33C
Partition: ID-1: / size: 33G used: 3.6G (12%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 2.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 33.0C mobo: 33.0C gpu: 33.0
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 180 Uptime: 1:35 Memory: 814.1/2000.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-asus-gnome:~$ 

```


regards..

---

### Post by ventrical on 2015-11-07
Just found out that it is actually running gnome-shell with gnome-classic on top of it so I think this is an experiment with containers. It is using some sort of gdm-session handler but it actually works very smoothly. 

Surprise!

:)

---

### Post by ventrical on 2015-11-07
Another new thing is at the top menu bar where you have Applications/Places .... when you load a program there is this little box that opens up on the menu bar and  it starts to scramble and flash like a little monitor while it is loading up.

Seems stable for now.

---

### Post by ventrical on 2015-11-07
I have been searching  all the new stuff with gnome 3.18 and I cannot find anything that mentions convergence with gnome-classic. Could this be a purely 'ubuntu' convergence development? 

Anyone else see this on their install of ubuntu-gnome xenial xerus?  When you  are at the login greeter there is a little cog and when you click it it comes up with the 'gnome classic' option but it is not running like a seperate desktop but , rather it is running like an app in gnome-shell .. so you can switch back and forth with the mouse. It is really very slick:)

regards..

---

### Post by sammiev on 2015-11-07
After reading all the fun you were having I rebooted my computer and log into gnome then log out and tried classic again.

All is good and I can see what you were talking about.

Need to play a little more.

Thanks

---

### Post by sammiev on 2015-11-07
> **ventrical said:**
> Just found out that it is actually running gnome-shell with gnome-classic on top of it so I think this is an experiment with containers. It is using some sort of gdm-session handler but it actually works very smoothly. 

Surprise!

:)

When you move the mouse to the top left you can see the gnome-shell menu and the desktop boxes on the right.

but all works very smooth as you posted above.

Thanks

---

### Post by mc4man on 2015-11-07
> **ventrical said:**
> Just found out that it is actually running gnome-shell with gnome-classic on top of it so I think this is an experiment with containers. It is using some sort of gdm-session handler but it actually works very smoothly. 


It's a gnome-shell extension provided by the gnome-shell-extensions package, been around for a couple of years. That package is included on Ubuntu Gnome images.

---

### Post by ventrical on 2015-11-08
> **mc4man said:**
> It's a gnome-shell extension provided by the gnome-shell-extensions package, been around for a couple of years. That package is included on Ubuntu Gnome images.

 I hadn't noticed until just recently. Even last cycle, it (gnome-classic) had to be installed to get included into the menu. I must have missed something here. Thanks for the enlightenment.

regards..

---

### Post by ventrical on 2015-11-08
> **sammiev said:**
> After reading all the fun you were having I rebooted my computer and log into gnome then log out and tried classic again.

All is good and I can see what you were talking about.

Need to play a little more.

Thanks

After reading what mac4man posted , it is just a gnome-shell extension. I thought it was something new. I never noticed it in the menu before. False alarm!:)  I thought it was a new convergence gizzmo. :)

regards..

---

### Post by sammiev on 2015-11-08
> **ventrical said:**
> After reading what mac4man posted , it is just a gnome-shell extension. I thought it was something new. I never noticed it in the menu before. False alarm!:)  I thought it was a new convergence gizzmo. :)

regards..

I tried on 15.10 after reading mac4man post to find the same. Used gnome for years and never noticed. lol

Thanks

---

### Post by kansasnoob on 2015-11-08
> **ventrical said:**
> After reading what mac4man posted , it is just a gnome-shell extension. I thought it was something new. I never noticed it in the menu before. False alarm!:)  I thought it was a new convergence gizzmo. :)

regards..

Yep, it's [been that way since Saucy]("http://ubuntuforums.org/showthread.php?t=2185161"):

> In Ubuntu GNOME Saucy you will find a new "GNOME Classic" session when you login without adding any additional packages, but this session is in no way related to the earlier classic or fallback sessions! The new GNOME Classic session runs on top of the Mutter window manager and could perhaps be best described as a 'gnome-shell' session using a popular collection of GNOME Shell Extensions.

Upstream GNOME created it at the request of RHEL. I wish they'd just created a mutter based gnome-panel session with easily editable panels, menus, etc.

---

### Post by ventrical on 2015-11-08
> **kansasnoob said:**
> Yep, it's [been that way since Saucy]("http://ubuntuforums.org/showthread.php?t=2185161"):



Upstream GNOME created it at the request of RHEL. I wish they'd just created a mutter based gnome-panel session with easily editable panels, menus, etc.

Thanks for clearing that up. I just never noticed it before.

Regards...

---

### Post by v3.xx on 2015-11-11
<snip>

Nevermind, this is uGnome

---

