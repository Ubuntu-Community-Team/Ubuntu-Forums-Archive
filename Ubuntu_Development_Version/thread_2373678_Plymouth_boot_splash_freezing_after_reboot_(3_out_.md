---
title: "Plymouth boot splash freezing after reboot (3 out of 4 times)"
date: 2017-10-08
forum: Ubuntu Development Version
---

### Post by amano on 2017-10-08
One package update on Thursday or Friday lets Plymouth freeze without bringing up GDM anymore.

I can get to GDM with the recovery option from Grub, but in the GDM cog “Ubuntu“ and “GNOME“ aren't listed anymore then. Just “Ubuntu on Xorg“ and “GNOME on Xorg“.

That could mean that maybe the mesa update to 17.2.2  broke the wayland support for my nv50 card (actually the ION chipset). Has anybody an ION himself and the current Aardvark working?

I wonder how I can debug that more. Switching the kernel from current .12 to .11 still causes the freeze at the end of Plymouth, so it doesn't seem to be caused by the latest kernel upgrade.

---

### Post by amano on 2017-10-08
On second thought, it could be related to jadahls Monitor fixes (headless mode) in Gnome-Shell 3.26.1.

I noticed that the highest resolution for my 16:10 monitor wasn't listing my 1400x900 resolution anymore and the highest available one did some vertical scrolling when choosing the 16:10 resolution. 

Switching to nvidia from nouveau fixed that. This way Plymouth doesn't start up at all, but GDM comes up. And the 1400x900 resolution is available again. Just Wayland still doesn't work anymore, but that was expexted by not being supported by the 340.xx drivers.

---

### Post by amano on 2017-10-12
It seems better after the updates of today. I am on a Wayland session now.

All those seem to be Wayland/Mutter crashes. 

Loading the Plymouth splash --> Loading GDM --> Detecting Wayland --> Crash --> the plymouth splash freezes stops forever

But today Wayland seems in better shape

1st try --> works --> I can get to GDM and choose "Ubuntu" --> 3 times in a row the Ubuntu session crashes when loading, the 4th time works
Reboot
2nd try --> Plymouth freezes and I have to unplug the computer
New boot
3rd try --> Works --> I can geto GDM --> The first time starting the "Ubuntu" session succeeds
Reboot
4th try --> getting to the Ubuntu session on first try.

Not perfect, but better

---

### Post by amano on 2017-10-14
Even after the updates of today (with the new kernel and the gnome-shell crash fix) the boot splash is getting stuck most of the time (certainly 3 out of 4 tries).

Only switching to the nvidia 340 blob fixes that (then it boots reliably, not showing Plymouth at all).

I don't think that it is a Plymouth bug, but GDM crashing when trying to bring up Wayland.

Since it crashes that early I don't think that it is related to mutter or gnome-shell at all. Or does GDM use mutter these days?

[S]Does apport leave a crash log in /var/crash/ with Ubuntu freezing or crashing that early?[/S] EDIT: Nope, no crash log in /var/crash/ at all :(

A regression in X? In Mesa?

---

### Post by cartes2 on 2017-10-14
Hi,

I think i have quite the same problem with a AMD card
gdm is working well  disabling wayland

I've made a beug report on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1723577](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1723577)

---

### Post by ventrical on 2017-10-14
This plymouth to gdm3 handoff on nVidia graphics breakage has been systemic throughout the latter part of this cycle. Finally relented and installed lightdm on one of my problem boxes.

Regards..

---

### Post by amano on 2017-10-14
For me it worked reliably the whole development cycle until the week leading up to the 7th of October. It is borked just for about a week now. On the 5th of October I remember it being fine, it was borked when starting Ubuntu up on the morning of October 7th.

Now it seems like a dealbreaker worth debugging (if I knew where to start).

---

### Post by ventrical on 2017-10-14
@amano

Please take a look at this thread. I just don't get it.  it is behaving like a sort of random malware or it is randomly deciding almost like :
if not BEST then NEXT i

if not NEXT i then toggle best guesstimate

[https://ubuntuforums.org/showthread.php?t=2374208](https://ubuntuforums.org/showthread.php?t=2374208)

regards..

---

### Post by amano on 2017-10-14
Well, personally I can work around the problem by installling the Nvidia blob. But it should be debugged and fixed in the Ubuntu code. Currently I don't even know against which package I should file a bug.

I had a look at the X logs:

> [   170.929] _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
[   170.931] _XSERVTransMakeAllCOTSServerListeners: server already running
[   170.932] (--) Log file renamed from "/var/log/Xorg.pid-1608.log" to "/var/log/Xorg.1.log"
[   170.934] 


That lines are just available in Xorg.1.log but not in Xorg.0.log. Might those give a clue?

My specs...

```

System:    Host: amano-desktop Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.21-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASRock model: AMCP7A-ION serial: N/A
           BIOS: American Megatrends v: P1.60 date: 08/26/2009
CPU:       Dual core Intel Atom 330 (-HT-MCP-) 
           arch: Bonnell rev.2 cache: 512 KB
           flags: (lm nx sse sse2 sse3 ssse3) bmips: 6399
           clock speeds: max: 1599 MHz 1: 1599 MHz 2: 1599 MHz 3: 1599 MHz
           4: 1599 MHz
Graphics:  Card: NVIDIA ION VGA bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.5 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: NVAC version: 3.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card NVIDIA MCP79 High Def. Audio
           driver: snd_hda_intel bus-ID: 00:08.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card: NVIDIA MCP79 Ethernet
           driver: forcedeth port: d080 bus-ID: 00:0a.0
           IF: enp0s10 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 320.1GB (47.3% used)
           ID-1: /dev/sda model: ST9320325AS size: 320.1GB temp: 46C
Partition: ID-1: / size: 21G used: 14G (69%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 1.03GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 77.0C mobo: N/A gpu: 81.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 227 Uptime: 39 min Memory: 1605.8/3256.5MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.3

```

As an attachment my gnome-logs file (though showing the current session that I was able to start):

---

### Post by cartes2 on 2017-10-15
i have a question. For me wayland is working nicely on virtual box but not with the real install on the same computer.

Could it be a normal behavior or not?

---

### Post by ventrical on 2017-10-15
> **cartes2 said:**
> i have a question. For me wayland is working nicely on virtual box but not with the real install on the same computer.

Could it be a normal behavior or not?

Two totally different sets of environment variables that get stacked out. Thats why one set will work in VM and not on bare metal and vis a versa.

regards..

---

### Post by cartes2 on 2017-10-15
Tanks, so it means that my graphic card should be wayland compatible.
(in my second life I would like to be able to speak english)

---

