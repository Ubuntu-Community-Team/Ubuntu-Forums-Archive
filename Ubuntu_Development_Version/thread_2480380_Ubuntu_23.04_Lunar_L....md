---
title: "Ubuntu 23.04 Lunar L?..."
date: 2022-10-28
forum: Ubuntu Development Version
---

### Post by corradoventu on 2022-10-28
[https://launchpad.net/ubuntu/lunar](https://launchpad.net/ubuntu/lunar)

---

### Post by QIII on 2022-10-28
"Lobster", if the internet monkeys are to be trusted.

---

### Post by osse7 on 2022-10-28
crunch jobs for Lunar are on :guitar:

---

### Post by Bashing-om on 2022-10-28
Yup --- lobster !
Ubuntu 23.04 Development Gets Started As The "Lunar Lobster"
[https://www.phoronix.com/news/Ubuntu-23.04-Lunar-Lobster](https://www.phoronix.com/news/Ubuntu-23.04-Lunar-Lobster)

-sometimes I do wonder-

---

### Post by mIk3_08 on 2022-10-29
> **corradoventu said:**
> [https://launchpad.net/ubuntu/lunar](https://launchpad.net/ubuntu/lunar) 
Thanks a lot for sharing. Regards and cheers.

---

### Post by zika on 2022-10-31
```
[COLOR=#000000]Calculating upgrade... Done[/COLOR]The following packages will be upgraded:
  base-files
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 73,4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu lunar-proposed/main amd64 base-files amd64 12.3ubuntu1 [73,4 kB]
Fetched 73,4 kB in 0s (248 kB/s)   
(Reading database ... 243807 files and directories currently installed.)
Preparing to unpack .../base-files_12.3ubuntu1_amd64.deb ...
Unpacking base-files (12.3ubuntu1) over (12.2ubuntu3) ...
Setting up base-files (12.3ubuntu1) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
motd-news.service is a disabled or a static unit not running, not starting it.
Processing triggers for cracklib-runtime (2.9.6-4) ...
Processing triggers for plymouth-theme-ubuntu-text (22.02.122-1ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for install-info (6.8-6) ...
Processing triggers for man-db (2.10.2-2) ...
Processing triggers for initramfs-tools (0.140ubuntu17) ...
update-initramfs: Generating /boot/initrd.img-6.1.0-3-generic
```

---

### Post by bsniadajewski on 2022-10-31
Any idea when the kernel updates to the 6 series as well as those of KDE Plasma (to 5.26) will arrive into Lunar without having to resort to PPA's?

---

### Post by TenPlus1 on 2022-11-01
Thanks Zika, am using new sources.list for 23.04 and eager for updates :)

---

### Post by zika on 2022-11-01
Nice coincidence:
```
[COLOR=#000000]systemd:[/COLOR]  Installed: 252~rc3-2+202210281638~ubuntu22.10.1
  Candidate: 252~rc3-2+202210281638~ubuntu22.10.1
  Version table:
 *** 252~rc3-2+202210281638~ubuntu22.10.1 500
        500 https://ppa.launchpadcontent.net/ddstreet/systemd-upstream/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
     251.4-1ubuntu7 500
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
```
[https://www.phoronix.com/news/systemd-252](https://www.phoronix.com/news/systemd-252)

---

### Post by IanW on 2022-11-02
Lunar release schedule has been posted

[https://discourse.ubuntu.com/t/lunar-lobster-release-schedule/27284](https://discourse.ubuntu.com/t/lunar-lobster-release-schedule/27284)

---

### Post by corradoventu on 2022-11-24
1St ISO available: [https://cdimage.ubuntu.com/daily-live/pending/](https://cdimage.ubuntu.com/daily-live/pending/)
```
corrado@corrado-b6-ll-1124:~$ inxi -SCx
System:
  Host: corrado-b6-ll-1124 Kernel: 5.19.0-21-generic arch: x86_64 bits: 64
    compiler: N/A Desktop: GNOME v: 43.0 Distro: Ubuntu 23.04 (Lunar Lobster)
CPU:
  Info: dual core model: Intel Core i3-4130 bits: 64 type: MT MCP
    arch: Haswell rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 812 high: 854 min/max: 800/3400 cores: 1: 798 2: 798
    3: 798 4: 854 bogomips: 27135
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
corrado@corrado-b6-ll-1124:~$ 
```

---

### Post by zebra2 on 2022-11-24
I used zsync and copied over the final Kinetic ISO.  It was 74% complete so I only needed a 1G download.

```

Read /home/zebra1/kinetic-desktop-amd64.iso. Target 74.2% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/lunar-desktop-amd64.iso:


Read /home/zebra1/kinetic-desktop-amd64.iso. Target 74.2% complete.      
downloading from http://cdimage.ubuntu.com/daily-live/current/lunar-desktop-amd64.iso:
#################### 100.0% 571.5 kBps DONE       


verifying download...checksum matches OK
used 3314143232 local, fetched 1150381972
zebra1@zebra1-320-15IAP:~$  
```

PS: Installing now

---

### Post by zebra2 on 2022-11-24
Just did an install of the 2022-11-24[SIZE=2][COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR][/SIZE]Lunar pending ISO and it works perfect on my Intel system. 
FYI

---

### Post by ajgreeny on 2022-11-24
> **zebra2 said:**
> Just did an install of the 2022-11-24[SIZE=2][COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR][/SIZE]Lunar pending ISO and it works perfect on my Intel system. 
FYI
I have also installed the daily from today, November 24, but in my case it's Xubuntu and using a VM in KVM/QEMU.

It is working superbly so far with no difficulties.  I have completely removed all snaps and the full snap infrastructure, again with no problems as I do in all my installations because of the older, slower hardware I run, and have used the .tar.gz direct download from Mozilla for Firefox.

To save download size I also zsynced but used an early downloaded iso of kinetic from some time in June 2022, so my input file was only 34% instead of the 74% that zebra2 saw. Still quite a saving and it dies check the iso as it downloads.

---

