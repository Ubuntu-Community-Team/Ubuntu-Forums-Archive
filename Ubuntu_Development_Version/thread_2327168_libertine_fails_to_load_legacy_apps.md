---
title: "libertine fails to load legacy apps"
date: 2016-06-08
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-06-08
Here is libertine bug that fails to load legacy apps. It will load firefox but fails on gnome-screenshot and gnome-terminal.

[https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1590142](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1590142)

---

### Post by amano on 2016-06-09
Marked "Affects me too" to gain some developer focus.

---

### Post by ventrical on 2016-06-09
Thanks .  I uploaded the two failed app logs but they still have it marked as incomplete. It is very early in the cycle.

Regards..

---

### Post by mc4man on 2016-06-09
> **ventrical said:**
> Thanks .  I uploaded the two failed app logs but they still have it marked as incomplete. It is very early in the cycle.

Regards..
If you fulfilled the request to provide info then mark the bug back to New yourself.

---

### Post by ventrical on 2016-06-09
> **mc4man said:**
> If you fulfilled the request to provide info then mark the bug back to New yourself.

Ahh .. thanks .

Done

Regards..

---

### Post by ventrical on 2016-06-09
As per Stephan Webb,

> 
                        Many Gnome  applications will only work on a Gnome desktop session and rely on a  session D-Bus providing D-Bus activated Gnome services inside the  container.  Among those applications are Gnome Terminal and Gnome  Screenshot.
 The solution is to use alternative applications that are designed to  work standalone without close integration with a full session management  suite, at least until there is some way to support containing session  management (which is not a goal of Libertine).
 I'm marking this as low priority, because the problem stems from  trying to run applications designed to run in a completely different  environment than Libertine provides.  The preferred solution is that  Gnome apps be run natively on Unity 8 and not using XMir in a Libertine  container, and that is being worked on outside of the Libertine project.

              
                               [TABLE="class: bug-activity"]
[TR]
         [TD="colspan: 2"]Changed in libertine (Ubuntu): [/TD]
       [/TR]
          [TR]
       [TD="align: right"]         **importance**:       [/TD]
       [TD]         Medium &#8594; Low       [/TD]
     [/TR]
     [TR]
       [TD="align: right"]         **status**:       [/TD]
       [TD]         New &#8594; Triaged       


That explains a lot. 

regards..
[/TD]
[/TR]
[/TABLE]

---

### Post by amano on 2016-06-10
Well, that seems to make sense.

Unity 8 and GNOME apps will run directly on Unity 8/MIR as they have to interact closer with each other. And more "alien" packages like Firefox, LibreOffice, Audacious etc can be run through Libertine which by concept limits interaction for probably a gain in security.

---

### Post by grahammechanical on 2016-06-10
I see Libertine as a stop-gap solution. The ideal situation for Mir + Unity 8 is for all applications to be packaged as snap packages. We are a long way away from having many useful applications packaged as snaps and Canonical does not want to take on the task of converting all deb packaged applications to snap packages. Canonical wants application developers see the benefits of having their applications packaged as snaps. Canonical would also like users to take on the task of snapping existing deb apps.

And then we have to consider those people who are worried that Ubuntu moving to Mir + Unity 8 will mean that Ubuntu will no longer have deb packages in its repositories. Seeing a vision is the easy part. Implementing the vision rarely goes according to plan.

And so we have two hybrid methods. Libertine on Unity 8 running deb packaged applications and snapd on Unity 7 running snap packages. Not to mention Snappy Ubuntu Desktop Next. "Here there be dragons."

Regards.

---

### Post by ventrical on 2016-06-10
Choice words of wisdom. But how can we ride the dragon if it doesn't have wings? How can we forge the bare metal  if it is not breathing fire?  It is true. Libertine+unity8 and snapd on Unity7 are ambitious. It will keep a lot of people busy. They snuggled in a super fast hypervisor but we only have Puff the Magic Dragon ( and I too love that dragon, Puff) but we want a real dragon running on Mir. (and the only way I see it feasible is to send Mark back to the space station - then there will be a real dragon running on mir ) :) .. but perhas we are not thinking outside the box here . Perhaps we should bring Mir to the dragon ..!! then .. yes.."here there be dragons". 

regards..

---

### Post by ventrical on 2016-06-24
I have another libertine fail on nVidia machine and want to reference errors here with screenshots.

edit:  fix commited

[URL="https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020"]https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020


[/URL]

---

### Post by ventrical on 2016-07-27
> **ventrical said:**
> I have another libertine fail on nVidia machine and want to reference errors here with screenshots.

edit:  fix commited

[URL="https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020"]https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020


[/URL]

got this in e-mail...

[SIZE=2]* Changed in: libertine/trunk
       Status: Fix Committed => Fix Released

** Changed in: libertine/devel
       Status: Fix Committed => Fix Released
[/SIZE]

---

### Post by ventrical on 2016-07-27
This has been a successful fix on nVidia graphics desktop. No lockups, You tube working fine on firefox ..etc..but there are ntification bugs with libertine as it delays informing the user that the container was successfully created until next reboot or log on, log off.

Regards..

will not mark as solved yet as it may break again.

---

### Post by grahammechanical on 2016-07-27
As you have installed Libertine see what you get when you run

```
ifconfig
```

You should see something like this

> lxcbr0    Link encap:Ethernet  HWaddr 7a:ed:93:43:54:73  
          inet addr:10.0.3.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::78ed:93ff:fe43:5473/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10604 (10.6 KB)


That is the network bridge between the container & the host.

Regards

---

### Post by ventrical on 2016-07-27
I get:

ok.. still can't copy n' paste with ff+terminal so here is screenshot.

---

### Post by ventrical on 2016-07-27
Here is running firefox seperately from two containers:

---

### Post by ventrical on 2016-07-27
Libertine workaround for nVidia: other

For now it seems you have to open the libertine-scope after each reboot and then go to Desktop Apps to run your installed apps.

Regards..

---

### Post by mikodo on 2016-07-27
Again, bits per Stephan Web on:

[https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1590142](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1590142)
> 
"*The preferred solution is that Gnome apps be run natively on Unity 8 and  not using XMir in a Libertine container, **and that is being worked on  outside of the Libertine project***".
I wonder if that is what Martin Wimpress is speaking of from his involvement at [Snappy Sprint]("https://plus.google.com/+MartinWimpress/posts/HKkAETn3Rkh"):

> "*A platform snap for GNOME 3.20 is nearly complete and the race is on to see if I can land the MATE 1.15 platform snap first*."

If this not on XMir but, a Gnome platform that runs natively on MIR, this seems to be materializing quickly. Or, is that too much to hope for and just a platform that runs on Unity8 using XMir.

---

### Post by ventrical on 2016-07-27
> **mikodo said:**
> Again, bits per Stephan Web on:

[https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1590142](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1590142)

I wonder if that is what Martin Wimpress is speaking of from his involvement at [Snappy Sprint]("https://plus.google.com/+MartinWimpress/posts/HKkAETn3Rkh"):



If this not on XMir but, a Gnome platform that runs natively on MIR, this seems to be materializing quickly.

 The few gnome apps that are working now are working just fine (nVidia). I do not think the problem was  with my bug that you referred. I think it had to do with another bug I reported that they released the fix today.

 Yes .. I am confident that they will be able to bind a desktop platform through mir but for lower end hardware - emphasis on lower end - the gnome based deb apps that do work  in desktop apps are an option for those end_users. In essence my point being that nobody will be comletely  shut out of the unity8/xmir/snappy experience unless the hardware is  over a decade old by about 2 to 3 years. I guess that is why we have to keep testing it and see where it goes.

regards..

---

### Post by grahammechanical on 2016-07-29
Today I logged into my Unity 8 session on Yakkety. And surprise, surprise I got a working Unity 8 on my Nvidia GT220. It had app indicators, a launcher and a Scopes scope that seemed to be useful & a mouse pointer that moved.

It did not have a feature to set up WiFI and it seemed to need WiFi. So, I restarted into Unity 7, set up WiFi. which has become more tricky than it used to be and then restarted into Unity 8 and it was back to no indicators, no launcher, a Scope that was empty and a mouse pointer stuck centre screen.

For a few minutes I thought that I was back in the game.

Oh, I would not bet on Gnome.org patching any code from Canonical into their Gnome apps so that they would run natively on Mir. I wonder just how much of Gnome 3 DE does Unity 8 use? Could the future be a Ubuntu not built on Gnome DE and using any utility that has been snap packaged? Why use Gnome Terminal when there is a fine terminal application for Unity 8 on the phone/tablet? I ask that question as an example of a possible alternate future for Ubuntu.

Regards.

---

### Post by rrnbtter on 2016-07-29
Greetings,
Unity8 desktop apps and all is totally in the hacking stage. I'm getting some limited results but just don't have the necessary time to spend on it. I have been hacking the click apps and have a few installed in spite of the error messages. It seems to me that the scripts (click and .py) need work. The devs admit this. If I find some dependable procedure that I can articulate I will post it. So far I'm depending on accidental success. I'm using Unity8 alternate on an Intel machine with Yakkety Unity7.

---

### Post by grahammechanical on 2016-07-29
I was able to log into Unity 8 again. It definitely fails to see itself connected to the internet when it has a wired connection and there is no method to set up a WiFi connection.

It froze when I tried to use Browser. I am beginning to wonder if Unity 8 needs more RAM than I have (1GB). Or, if the failure to connect to the internet is messing things up. Or, if the phone overlay PPA is bringing in a phone version of Unity 8 when there should be a desktop version.

I had better success more than a year ago with Unity 8 on 14.04. 

Regards.

---

### Post by rrnbtter on 2016-07-29
Greetings,
I have 4Gig of Ram and a 4Gig swap file. Running TOP from a terminal in Unity8 I am showing only 380Meg being used with Unity7 being swapped out at 1.7Gig. I would say that 1Gig of RAM would be enough as long as the swap file is big enough to do the caching on the sleeping part of the system. I expect that the need would be less on one of the non Unity flavors (don't know).

---

### Post by ventrical on 2016-07-29
> **grahammechanical said:**
> I was able to log into Unity 8 again. It definitely fails to see itself connected to the internet when it has a wired connection and there is no method to set up a WiFi connection.

It froze when I tried to use Browser. I am beginning to wonder if Unity 8 needs more RAM than I have (1GB). Or, if the failure to connect to the internet is messing things up. Or, if the phone overlay PPA is bringing in a phone version of Unity 8 when there should be a desktop version.

I had better success more than a year ago with Unity 8 on 14.04. 

Regards.

I have basically been following the link instructions from the dogfooding  site authored by mHall that you put up in the forums.

 Yes .. defintely 2 GBs of RAM at the least.  When I had libertine loaded yesterday and working  , htop showed me it was using 1.3GB of RAM. The phone overlay from the ppa is what is suggested by the devs for desktop usage for now.  The other ci-train ppa had to be removed or  the system will break, so I am doing fresh installs of yakkety amd64 (because they will not purge clean).. which seems to be most suited atm.

regards..

---

### Post by rrnbtter on 2016-07-29
Greetings,
I just ran a mid day update and got a nice Unity8 update.

The following NEW packages will be installed:
  address-book-app camera-app gallery-app libmediainfo0v5 libtinyxml2-3
  libzen0v5 mediaplayer-app qml-module-qtcontacts
  qtdeclarative5-buteo-syncfw0.1 qtdeclarative5-online-accounts-client0.1
  qtdeclarative5-qtcontacts-plugin qtdeclarative5-ubuntu-addressbook0.1
  qtdeclarative5-ubuntu-contacts0.1 qtdeclarative5-ubuntu-history0.1
  qtdeclarative5-ubuntu-keyboard-extensions0.1
  qtdeclarative5-ubuntu-thumbnailer0.1 qtdeclarative5-ubuntu-ui-extras0.2
  qtdeclarative5-window-plugin qtdeclarative5-xmllistmodel-plugin
The following packages will be upgraded:
  libgtk2.0-common libpcre16-3 libpcre3 libvlc5 libvlccore8 libwxbase3.0-0v5
  libwxgtk3.0-0v5 openssh-client snap-confine ubuntu-core-launcher
  unity8-desktop-session vlc vlc-data vlc-nox vlc-plugin-notify

It has some nice additions for the faux desktop.

---

### Post by ventrical on 2016-07-29
I got libertine/desktop apps working on xenial installs now after that update. It's a really tweaky thing you have to do.  When you startup libertine it will open install screen. You fill out info and name your container but it will bounce back to install screen. THE CONTAINER is being created in the background so just watch your modem light and hdd light until it is done. Then quit libertine or log off /log on or both and then open libertine again in the same session and you will see created container. The "+" add icon will work.  Use the top dialog box for install debian apps. I choose firefox, nautilus, gedit and psensor which all work. Then you can try other stuff. *note* Installing snap  packages will most likely break your after a time because I tried. so you might have better luck getting snaps working from terminal.

Most of all .. be patient while container is being created.

Its not a fix but just a temp workaround that works for me.

The modem lights start and stop a couple of times probably due to heavy load. Just be patient. 

regards..

---

### Post by ventrical on 2016-07-31
@graham

  I swapped out a hdd and got unity8/libertine running on this 10 year old HP/nVidia proprietary machine.

```

ventrical@ventrical-wolfdale-nvidiahybrid:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
03:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
ventrical@ventrical-wolfdale-nvidiahybrid:~$ 

```

and..
```


ventrical@ventrical-wolfdale-nvidiahybrid:~$ inxi -Fxz
System:    Host: ventrical-wolfdale-nvidiahybrid Kernel: 4.4.0-33-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.5.0 (Gtk 3.18.9-1ubuntu4) Distro: Ubuntu 16.10
Machine:   System: HP-Pavilion product: RK574AA-ABA a1730n
           Mobo: ASUSTek model: NODUSM3 v: 1.05
           Bios: Phoenix v: 5.04 date: 12/15/2006
CPU:       Dual core AMD Athlon 64 X2 5000+ (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 svm) bmips: 4008
           clock speeds: max: 2600 MHz 1: 1000 MHz 2: 1000 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 02:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8
           GLX Version: 3.0 Mesa 12.0.1 Direct Rendering: Yes
Audio:     Card NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 02:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-33-generic
Network:   Card: NVIDIA MCP51 Ethernet Controller
           driver: forcedeth port: c800 bus-ID: 00:14.0
           IF: enp0s20 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (14.2% used)
           ID-1: /dev/sda model: WDC_WD800HLFS size: 80.0GB
Partition: ID-1: / size: 71G used: 7.8G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.22GB used: 0.01GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 51.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 224 Uptime: 10 min Memory: 930.8/1999.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.3.0 
ventrical@ventrical-wolfdale-nvidiahybrid:~$ 

```

I had to grab this info from ubuntu-desktop as terminal.click will still not copy n' paste.

regards..

---

