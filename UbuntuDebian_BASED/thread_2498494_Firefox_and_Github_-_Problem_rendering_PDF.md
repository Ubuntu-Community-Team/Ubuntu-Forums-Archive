---
title: "Firefox and Github - Problem rendering PDF"
date: 2024-06-16
forum: Ubuntu/Debian BASED
---

### Post by leon-pozzati on 2024-06-16
Hi all,

As I already wrote in the title, I am currently experiencing problems when I try to visualize any PDF in any of my repository.
The problem happens when using Firefox, not with other web browsers like Chromium though.

I get this error
```

Error rendering embedded code
Invalid PDF

```

I tried looking online but could not find a working solution.

Regards



p.s.: I hope this is the right section for this question :-)

---

### Post by ajgreeny on 2024-06-16
Yes, correct section for now at least.

Is your firefox the default snap version?
What do you mean by "PDF in any of my repository"?  Do you mean a PDF i your filesystem?

The snap version of firefox cannot by default open files that are not in certain folders within your home, though I believe that behaviour can be changed; I remove all snaps so don't know more details of the needed action from you so wait for other replies and you should get more help from users who keep snaps i their system.

---

### Post by leon-pozzati on 2024-06-16
Sorry for not being precise in describing the issue.

Firefox is installed with apt-get.
I mean the pdf in my repositories folders online. Then yes, my filesystems.

The issue appeared a couple of days ago.

---

### Post by ajgreeny on 2024-06-17
Assuming you're using a supported version of Ubuntu, using apt-get to install Firefox still pulls in the snap version and not the .deb version.
To be sure where we are starting from please show us the outputs from these three commands
```
inxi -Fzx
apt policy firefox
snap list
```
Please use code tags for the copied output.
See my signature below for a how-to of code tags.

---

### Post by leon-pozzati on 2024-06-18
Forgot to mention I am using Pop os, double sorry :KS

Hereby the output
```

$ inxi -Fzx
System:
  Kernel: 6.4.6-76060406-generic x86_64 bits: 64 compiler: N/A
    Desktop: GNOME 42.5 Distro: Pop!_OS 22.04 LTS base: Ubuntu 22.04 LTS Jammy
Machine:
  Type: Laptop System: HP product: Victus by HP Gaming Laptop 15-fa0xxx
    v: N/A serial: <superuser required>
  Mobo: HP model: 8A4F v: 37.54 serial: <superuser required> UEFI: AMI
    v: F.24 date: 10/26/2023
Battery:
  ID-1: BAT0 charge: 65.4 Wh (100.0%) condition: 65.4/70.1 Wh (93.4%)
    volts: 17.4 min: 15.4 model: HP Primary status: Full
CPU:
  Info: 12-core (4-mt/8-st) model: 12th Gen Intel Core i5-12500H bits: 64
    type: MST AMCP arch: Alder Lake rev: 3 cache: L1: 1.1 MiB L2: 9 MiB
    L3: 18 MiB
  Speed (MHz): avg: 1836 high: 3100 min/max: 400/4500:3300 cores: 1: 1123
    2: 2079 3: 400 4: 3100 5: 996 6: 3100 7: 442 8: 3100 9: 844 10: 3100
    11: 3100 12: 3100 13: 1700 14: 1681 15: 401 16: 1120 bogomips: 99532
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: Hewlett-Packard
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GA107M [GeForce RTX 3050 Mobile] vendor: Hewlett-Packard
    driver: nvidia v: 535.86.05 bus-ID: 01:00.0
  Device-3: Luxvisions Innotech HP Wide Vision HD Camera type: USB
    driver: uvcvideo bus-ID: 3-6:2
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1: 1920x1080~60Hz 2: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 23.1.3-1pop0~1689084530~22.04~0618746 direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    vendor: Hewlett-Packard driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: Hewlett-Packard driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Sound Server-1: ALSA v: k6.4.6-76060406-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 0.3.74 running: yes
Network:
  Device-1: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 04:00.0
  IF: wlp4s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus-ID: 05:00.0
  IF: eno1 state: down mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 3-7:3
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 2.29 TiB used: 1.22 TiB (53.4%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVL2512HCJQ-00BH1
    size: 476.94 GiB temp: 41.9 C
  ID-2: /dev/sda type: USB vendor: Western Digital model: WD Elements 1048
    size: 1.82 TiB
Partition:
  ID-1: / size: 34.15 GiB used: 24.65 GiB (72.2%) fs: ext4
    dev: /dev/nvme0n1p7
  ID-2: /boot/efi size: 1022 MiB used: 282.9 MiB (27.7%) fs: vfat
    dev: /dev/nvme0n1p5
  ID-3: /home size: 68.35 GiB used: 32.55 GiB (47.6%) fs: ext4
    dev: /dev/nvme0n1p8
Swap:
  ID-1: swap-1 type: partition size: 16 GiB used: 0 KiB (0.0%) dev: /dev/dm-0
    mapped: cryptswap
  ID-2: swap-2 type: zram size: 15.28 GiB used: 0 KiB (0.0%)
    dev: /dev/zram0
Sensors:
  System Temperatures: cpu: 45.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 381 Uptime: 24m Memory: 15.28 GiB used: 5.36 GiB (35.1%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2314 Shell: Bash
  v: 5.1.16 inxi: 3.3.13


```

```

$ apt policy firefox
firefox:
  Installed: 1:116.0~1690930389~22.04~4fb419c
  Candidate: 1:126.0.1~1716934688~22.04~33890f8
  Version table:
     1:126.0.1~1716934688~22.04~33890f8 1001
       1001 http://apt.pop-os.org/release jammy/main amd64 Packages
 *** 1:116.0~1690930389~22.04~4fb419c 100
        100 /var/lib/dpkg/status
     1:1snap1-0ubuntu2 500
        500 http://apt.pop-os.org/ubuntu jammy/main amd64 Packages

```

```

$ snap list
Name               Version                     Rev    Tracking       Publisher       Notes
bare               1.0                         5      latest/stable  canonical&#10003;      base
chromium           126.0.6478.61               2883   latest/stable  canonical&#10003;      -
core18             20240416                    2823   latest/stable  canonical&#10003;      base
core22             20240408                    1380   latest/stable  canonical&#10003;      base
cups               2.4.9-1                     1052   latest/stable  openprinting&#10003;   -
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  198    latest/stable  canonical&#10003;      -
gnome-42-2204      0+git.510a601               176    latest/stable  canonical&#10003;      -
gtk-common-themes  0.1-81-g442e511             1535   latest/stable  canonical&#10003;      -
snapd              2.63                        21759  latest/stable  canonical&#10003;      snapd
teams-for-linux    1.6.1                       614    latest/stable  ismaelmartinez  -


```

---

### Post by ajgreeny on 2024-06-18
OK, you do not have the snap version of firefox installed but I suspect from the output of the apt policy firefox command that you are not using Ubuntu but Pop-OS, based on but very different in many ways about which I know almost nothing.

Is this a real version of Ubuntu or is it Pop-OS?

---

### Post by #&amp;thj^% on 2024-06-18
With ajgreeny pointing out your version of firefox is not a snap package, it still "might" be the problem with that particular version.

Now I prefer to run from the mozilla PPA with specific instructions: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
```
apt list ~nfirefox --installed -a
firefox/oracular 1:1snap1-0ubuntu5 amd64
firefox/mozilla,now 127.0~build2 amd64 [installed,automatic]
firefox/mozilla 126.0.1~build1 amd64
firefox/mozilla 126.0~build2 amd64
firefox/mozilla 125.0.3~build1 amd64
firefox/mozilla 125.0.2~build1 amd64
firefox/mozilla 125.0.1~build1 amd64
firefox/mozilla 124.0.2~build1 amd64
firefox/mozilla 124.0.1~build1 amd64
firefox/mozilla 124.0~build1 amd64
firefox/mozilla 123.0.1~build1 amd64
firefox/mozilla 123.0~build3 amd64
firefox/mozilla 122.0.1~build1 amd64
firefox/mozilla 122.0~build2 amd64

```

However I as well do not know PopOS so adding that or any other PPA might be a bad thing. but easy enough to fix.

This might be better moved to a Debian/other OS sub forum.

EDIT: If it is safe or possible, could you link one of the failed PDF's just to check against.

---

### Post by deadflowr on 2024-06-18
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by leon-pozzati on 2024-06-18
I am using Pop Os indeed, I forgot to specify.

```

$ apt list ~nfirefox --installed -a
Listing... Done
firefox/jammy 1:126.0.1~1716934688~22.04~33890f8 amd64 [upgradable from: 1:116.0~1690930389~22.04~4fb419c]
firefox/now 1:116.0~1690930389~22.04~4fb419c amd64 [installed,upgradable to: 1:126.0.1~1716934688~22.04~33890f8]
firefox/jammy 1:1snap1-0ubuntu2 amd64

```

---

### Post by #&amp;thj^% on 2024-06-18
What about the rest of what was asked? Post #7
> EDIT: If it is safe or possible, could you link one of the failed PDF's just to check against. 

---

### Post by leon-pozzati on 2024-06-18
I completely missed.
Actually it is not safe at the moment.

I will create a safe one in the next days.

---

### Post by #&amp;thj^% on 2024-06-18
It worked for me, with :
```
 firefox --version
Mozilla Firefox 127.0

```
For privacy I've only included the top portion.

My firefox is from the PPA that I linked earlier.

EDIT: If you need me to delete that screenshot just let me know ASAP.

---

### Post by leon-pozzati on 2024-06-18
Therefore it has something to do with my version of Firefox.
Also, I am using Pop Os based on Ubuntu 22.04.

Maybe the solution is checking it again when I will update Pop Os.
The strange aspect is that I could open the PDF until a couple of weeks ago.


p.s.:
yes, please remove the PDF attached :-)
I had removed some personal data from that PDF before opening the repo (even though they were still in the LaTeX code)

---

### Post by ajgreeny on 2024-06-19
You could also try running firefox from the directly downloaded .tar.bz from Mozilla, extracting that and using the executable in the extracted archive.
backup the hidden .mozilla folder in your home first, just in case.

I have been using firefox this way since the start of 22.04 when snaps took over from the .deb install; it has worked without fault since then.

---

### Post by leon-pozzati on 2024-06-19
I need to specify that the pdf is not possible to open the **online** version.

In case it is downloaded, Firefox opens it.

---

### Post by #&amp;thj^% on 2024-06-19
> **leon-pozzati said:**
> 
p.s.:
yes, please remove the PDF attached :-)
I had removed some personal data from that PDF before opening the repo (even though they were still in the LaTeX code)

It was Not the PDF itself but a snapshot only....Removed and all set.

EDIT: If you can't open any PDF files with the built-in PDF viewer, a Firefox extension could be the cause. You can disable all of your extensions, to see if one of them was the problem.

---

### Post by igormachado on 2024-06-20
Just had the same problem on Firefox 112 with Ubuntu 20.04 (PDFs were not rendering anymore on GitHub).
Upgrading it to 126 solved the problem.

---

### Post by leon-pozzati on 2024-06-21
I will try and update you, thanks!

p.s.: I meant snapshot attached, sorry for my lack of proper jargon.

---

