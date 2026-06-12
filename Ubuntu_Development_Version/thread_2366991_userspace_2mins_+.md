---
title: "userspace 2mins +"
date: 2017-07-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-07-24
Just noticing that the same systemd userspace lag happens on xubuntu also.

```


ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 3.518s (kernel) + 2min 14.198s (userspace) = 2min 17.717s

```

---

### Post by #&amp;thj^% on 2017-07-24
> **ventrical said:**
> Just noticing that the same systemd userspace lag happens on xubuntu also.

```


ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 3.518s (kernel) + 2min 14.198s (userspace) = 2min 17.717s

```

I'm not seeing it that bad, but:
```
systemd-analyze
Startup finished in 4.036s (kernel) + 1min 16.859s (userspace) = 1min 20.895s

```
Gnome and Xfce:
I need to add though that I offloaded the Intel Driver to Nvidia prior to rebooting.

---

### Post by ventrical on 2017-07-24
Just updated. Will reboot  and try that.

---

### Post by ventrical on 2017-07-24
Oy vey! :)

```


ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 3.736s (kernel) + 16.421s (userspace) = 20.157s
ventrical@ventrical-System-Product-Name:~$ 



```

 now we're talking turkey :)

Regards..

---

### Post by cariboo on 2017-07-24
On my Intel based laptop:

```
Startup finished in 3.172s (kernel) + 9.885s (userspace) = 13.057s
```

---

### Post by #&amp;thj^% on 2017-07-24
And the winner with the fasted time is cariboo. :)

---

### Post by ventrical on 2017-07-24
ehehehe...

but I'm running quite the geezer of a  test box.

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASUSTeK model: P5B-E v: Rev 1.xx BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11981
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.3) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.89hz
           OpenGL: renderer: Gallium 0.4 on NVD9 version: 4.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (0.5% used)
           ID-1: /dev/sda model: WDC_WD15EURS size: 1500.3GB
Partition: ID-1: / size: 37G used: 6.4G (19%) fs: ext4 dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 35.0C mobo: 37.0C gpu: 39.0
           Fan Speeds (in rpm): cpu: 4218 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 186 Uptime: 1:47 Memory: 692.0/3005.6MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.23 
ventrical@ventrical-System-Product-Name:~$ 


```

so's ya got to give me a few secs handicap eh . :)

hehe ok .. ok .. 2009 is not actually that old :)

---

### Post by cariboo on 2017-07-25
> **1fallen said:**
> And the winner with the fasted time is cariboo. :)

I think the result of a fairly recent upgrade to an SSD (ADATA SP920SS) really shows, with the original HDD times were always over 1 minute.

---

### Post by #&amp;thj^% on 2017-07-25
I seem to find that if I just boot 1 OS daily I get much better times.
Today after a few boots with same partition.
```
Startup finished in 3.203s (kernel) + 15.842s (userspace) = 19.046s
```
And this is with 3 hard drives attached.
```
Drives:    HDD Total Size: 3000.6GB (19.2% used)
           ID-1: /dev/sda model: WDC_WD5000AACS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
           ID-3: /dev/sdc model: 2115 size: 500.1GB

```
Not to bad.
But if i switch out the main drive to another OS then I'm back to over 1:20 startups.

---

### Post by jbicha on 2017-07-25
```
Startup finished in 4.276s (firmware) + 5.475s (loader) + 18.662s (kernel) + 3min 3.530s (userspace) = 3min 31.944s
```

---

### Post by ventrical on 2017-07-26
> **jbicha said:**
> ```
Startup finished in 4.276s (firmware) + 5.475s (loader) + 18.662s (kernel) + 3min 3.530s (userspace) = 3min 31.944s
```

Could you put up the specs to the hardware you are running that on ?

Regards..

---

### Post by jbicha on 2017-07-26
It is a 2016 Lenovo Ideapad Flex4 with 8GB of RAM and Intel i5-6200U CPU and a traditional hard drive, using Wi-Fi.

I have some developer tools installed like schroot/sbuild and VirtualBox.

I'm attaching the output of systemd-analyze-plot > jbicha-boot.svg

---

### Post by ventrical on 2017-07-26
> **jbicha said:**
> It is a 2016 Lenovo Ideapad Flex4 with 8GB of RAM and Intel i5-6200U CPU and a traditional hard drive, using Wi-Fi.

I have some developer tools installed like schroot/sbuild and VirtualBox.

I'm attaching the output of systemd-analyze-plot > jbicha-boot.svg

"traditional hard drive" answers my question .. thanks!

---

