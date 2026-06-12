---
title: "Bodhi 5 And Nvidia 6150se Graphics"
date: 2020-09-30
forum: Ubuntu, Linux and OS Chat
---

### Post by O)9(yo&amp;# on 2020-09-30
I have finally found a Ubuntu-18-based distro that works for these rather ancient on-board graphics, which I am now using due to my video card dying. Previously, I could only get Ubuntu-16-based distros to work, and then only if I installed the Nvidia 304 driver. It appears impossible to install that driver on systems later than Ubuntu 16. Nvidia stopped supporting it after kernel 4.4, and Ubuntu 18 and downstream distros no longer have the necessary dependencies. The only still-supported systems I could get working were Ubuntu 16.04 and Linux Lite 3.8. the problems involved open-sourced drivers being problematic for 6150se graphics, causing display crashes, browser problems, etc. 

Now, I have finally found a distro that works with open-sourced drivers and this 12 year old Gateway desktop. However, I did have to disable hardware acceleration in Vivaldi. This was hard to do, as there was screen tearing, so I couldn't find the box to uncheck for this. I finally did so by choosing the "show all" option in Preferences. This allowed me to sneak up on the relevant section, so to speak. As soon as I unchecked the acceleration box, Vivaldi settled down and has been perfect ever sine. As has Bodhi 5. 

I post this in case anyone else is using a system with these graphics, and has run up against the Ubuntu-18 "barrier." Bodhi 5 is supported until 2023, and who knows, Bodhi 6 may also work, when it comes out. Just remember to disable hardware acceleration. 

I know of no other DE that is light enough to be compatible in this situation. And it's also beautiful and very fast. It has quickly become my favorite Linux distro. I plan to put it on a SSD soon. It should be blazingly fast then. It's quite respectable now even on an old HDD.

---

### Post by poorguy on 2020-09-30
I'm not the only one with several of these unsupported ** NVIDIA C61 [GeForce 6150SE nForce 430]** I'm running this LIVE DVD just to see if it would work. :-k

[https://www.pclinuxos.com/](https://www.pclinuxos.com/)

```


[guest@localhost ~]$ inxi -Fxz
System:    Kernel: 5.6.19-pclos1 x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: LXQt 0.15.1 Distro: PCLinuxOS 2020 
Machine:   Type: Desktop System: Compaq-Presario product: BM411AA-ABA CQ5600F v: N/A serial: <filter> 
           Mobo: PEGATRON model: NARRA5 v: 5.00 serial: <filter> BIOS: Phoenix v: 5.59 date: 05/20/2010 
CPU:       Topology: Dual Core model: AMD Athlon II X2 B24 bits: 64 type: MCP arch: K10 rev: 2 L2 cache: 2048 KiB 
           flags: lm nx pae sse sse2 sse3 sse4a svm bogomips: 12054 
           Speed: 800 MHz min/max: 800/3000 MHz Core speeds (MHz): 1: 800 2: 800 
Graphics:  Device-1: NVIDIA C61 [GeForce 6150SE nForce 430] vendor: Hewlett-Packard driver: nouveau v: kernel 
           bus ID: 00:0d.0 
           Display: x11 server: X.Org 1.20.8 driver: nouveau,v4l resolution: 1280x800~75Hz 
           OpenGL: renderer: NV4C v: 2.1 Mesa 20.1.2 direct render: Yes 
Audio:     Device-1: NVIDIA MCP61 High Definition Audio vendor: Hewlett-Packard driver: snd_hda_intel v: kernel 
           bus ID: 00:05.0 
           Sound Server: ALSA v: k5.6.19-pclos1 
Network:   Device-1: NVIDIA MCP61 Ethernet vendor: Hewlett-Packard type: network bridge driver: forcedeth v: kernel 
           port: fc00 bus ID: 00:07.0 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 149.05 GiB used: 16.1 MiB (0.0%) 
           ID-1: /dev/sda vendor: Hitachi model: HTS543216L9SA00 size: 149.05 GiB 
Swap:      Alert: No Swap data was found. 
Sensors:   Missing: Required tool sensors not installed. Check --recommends 
Info:      Processes: 143 Uptime: 17m Memory: 3.61 GiB used: 757.0 MiB (20.5%) Init: SysVinit runlevel: 5 Compilers: 
           gcc: 9.3.0 clang: 10.0.0 Packages: 1581 Shell: Bash v: 4.4.23 inxi: 3.1.04 
[guest@localhost ~]$ 


```

I've been running **LXLE** Linux distro and it works most of the time however display crashes sometimes.

[https://www.lxle.net/](https://www.lxle.net/)

I have a few of these setting around that are capable if I change the power supply from a 20 pin to a 24 pin and then add a decent cheap graphics card.

I've run **Bodhi** on these and it works but again display crashes sometimes.

I have zero dollars in these as they're put together from spare parts I have.

Just thought I'd post how this Linux disto works with this particular unsupported **NVIDIA C61 [GeForce 6150SE nForce 430] **integrated graphics adapter.

The **open source nouveau driver** works well most of the time.

---

