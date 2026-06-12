---
title: "Ubuntu 20.04 Performance"
date: 2020-05-01
forum: Ubuntu, Linux and OS Chat
---

### Post by makitso on 2020-05-01
Two late model  Intel-based machines running a clean install of 20.04 with the Ubuntu Budgie desktop. I have noticed a general performance improvement in day-to-day usage.  Anyone else notice this?

---

### Post by artergw on 2020-05-07
Yes my new XPS 15 9570 - I7 + 32GB ram installed 20.04 and the performance is everything I could have hoped for, the distro is my now my daily driver having tried many others recently this one just feels right for me.

---

### Post by ActionParsnip on 2020-05-07
Is it the same in lighter sessions like LXDE?

---

### Post by Shibblet on 2020-05-07
> **makitso said:**
> Two late model  Intel-based machines running a clean install of 20.04 with the Ubuntu Budgie desktop. I have noticed a general performance improvement in day-to-day usage.  Anyone else notice this?

Budgie is tight, isn't it?  I want to know how Solus (who invented Budgie) get's their OS to load in like 5 seconds.
XFCE is really good for resource management as well.
The Ubuntu team really tightened up GNOME-3 for this last release, and it runs fantastic also.

But the one I am the most impressed with lately, is KDE.  They have taken the Plasma Desktop from a resource hog, and turned it into one that sips resources like a cup of tea.

---

### Post by lwalper on 2020-05-08
I don't know about the difference between 18.04 and 20.04 since I've also done a hardware upgrade with I7 processor and SSD drives, but boot-up is less than 10 seconds for what used to take 2-3 minutes. Software loads and does "stuff" when I click it - like, nearly instantly. Nice!

---

### Post by poorguy on 2020-05-13
Ubuntu 20.04 runs great on my 2010 desktop and perhaps a little bit faster than Ubuntu 18.04.

```


thomas@Dell-OptiPlex-380:~$ inxi -Fxz
System:    Kernel: 5.4.0-29-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.1 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Dell product: OptiPlex 380 v: N/A serial: <filter> 
           Mobo: Dell model: 0HN7XN v: A01 serial: <filter> BIOS: Dell v: A02 date: 08/27/2010 
CPU:       Topology: Dual Core model: Intel Core2 Duo E7500 bits: 64 type: MCP arch: Penryn rev: A 
           L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx bogomips: 11704 
           Speed: 1596 MHz min/max: 1600/2933 MHz Core speeds (MHz): 1: 1751 2: 1821 
Graphics:  Device-1: Intel 4 Series Integrated Graphics vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1152x720~60Hz 
           OpenGL: renderer: Mesa DRI Intel G41 (ELK) v: 2.1 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Dell driver: snd_hda_intel v: kernel 
           bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.4.0-29-generic 
Network:   Device-1: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe vendor: Dell driver: tg3 
           v: 3.137 port: ece0 bus ID: 02:00.0 
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 149.05 GiB used: 9.08 GiB (6.1%) 
           ID-1: /dev/sda vendor: Fujitsu model: MHW2160BH PL size: 149.05 GiB 
Partition: ID-1: / size: 145.22 GiB used: 9.08 GiB (6.3%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 41.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 182 Uptime: 2h 40m Memory: 3.75 GiB used: 1.22 GiB (32.6%) Init: systemd runlevel: 5 
           Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 inxi: 3.0.38 
thomas@Dell-OptiPlex-380:~$ 


```

---

