---
title: "Ubuntu 23.10 will be Mantic"
date: 2023-04-25
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-04-25
[https://launchpad.net/ubuntu/mantic](https://launchpad.net/ubuntu/mantic)

---

### Post by zika on 2023-04-26
Sources files (via devel) ready for new stuff... :)

---

### Post by zebra2 on 2023-04-26
Source files via (mantic) ready for new stuff.  Not a drip so far.

---

### Post by IanW on 2023-04-27
Mantic Mynah or riot!

[IMG]https://worldofspectrum.org/files/thumb/a3f7c343f9e043d/4[/IMG]

---

### Post by este.el.paz on 2023-04-30
Cool.  I have my sources.list now set for "lunar" rather than "devel" . . . because I run apt dist-upgrade weekly, so I don't want to worry about the transition phase when that might cause issues, etc.

When will I be able to edit them to "mantic" to get started in the latest stuff for my ubuntu squeeze of choice . . . Lubuntu?

---

### Post by grahammechanical on 2023-05-01
The mantic repositories/sources exist but nothing is being put in them. Not even a lsb_release text file reporting 23.10 (development). Changing the sources to mantic does not trip anything up. But all is quiet in the mantic front at the moment.

Regards

---

### Post by este.el.paz on 2023-05-01
> **grahammechanical said:**
> The mantic repositories/sources exist but nothing is being put in them. Not even a lsb_release text file reporting 23.10 (development). Changing the sources to mantic does not trip anything up. But all is quiet in the mantic front at the moment.

Regards

@grahammechanical:

Thanks for the reply . . . so no worries on it . . . .  I haven't jumped the gun on the editing sources until stuff is "in the tubes" . . . .  But, are you saying that changing them now to "mantic" would still bring in regular system upgrades . . . and then when the mantic stuff comes into play there might be a "balloon" of upgrades to bring it to 23.10??? 

Or, best to wait on changing the sources until stuff is ready to go into play?

---

### Post by #&amp;thj^% on 2023-05-01
If interested, mine:
```
Repos:
  Active apt repos in: /etc/apt/sources.list
    1: deb https://mirrors.ustc.edu.cn/ubuntu/ devel main restricted universe multiverse
    2: deb-src https://mirrors.ustc.edu.cn/ubuntu/ devel main restricted universe multiverse
    3: deb https://mirrors.ustc.edu.cn/ubuntu/ devel-security main restricted universe multiverse
    4: deb-src https://mirrors.ustc.edu.cn/ubuntu/ devel-security main restricted universe multiverse
    5: deb https://mirrors.ustc.edu.cn/ubuntu/ devel-updates main restricted universe multiverse
    6: deb-src https://mirrors.ustc.edu.cn/ubuntu/ devel-updates main restricted universe multiverse
    7: deb https://mirrors.ustc.edu.cn/ubuntu/ devel-backports main restricted universe multiverse
    8: deb-src https://mirrors.ustc.edu.cn/ubuntu/ devel-backports main restricted universe multiverse

```

---

### Post by este.el.paz on 2023-05-01
@1fallen:

Thanks . . . so far I haven't set mine to "devel" . . . because my understanding is that in the time between system release and system freeze, that apt dist-upgrade using "devel" shouldn't be run, because it will cause problems???  Since I run upgrades weekly, in a multi-boot machine, I have 7 distros to maintain, so paying attention to any one of them is problematic in that regard.

So, I try to get into the "next" option as soon as it is "available" . . . like "pre-alpha" . . . .

---

### Post by #&amp;thj^% on 2023-05-01
Wise choice, but with added info...I've been on "devel" for over a year now and I'm well aware of possible pitfalls or breakage.
So far it's been pretty boring....[https://ubuntuforums.org/showthread.php?t=2481166&p=14130766#post14130766](https://ubuntuforums.org/showthread.php?t=2481166&p=14130766#post14130766)
I'm aiming at a rolling release. ;)

---

### Post by este.el.paz on 2023-05-01
> **1fallen said:**
> Wise choice, but with added info...I've been on "devel" for over a year now and I'm well aware of possible pitfalls or breakage.
So far it's been pretty boring....[https://ubuntuforums.org/showthread.php?t=2481166&p=14130766#post14130766](https://ubuntuforums.org/showthread.php?t=2481166&p=14130766#post14130766)
I'm aiming at a rolling release. ;)

@1fallen:

Cool.  Usually things go smoothly, but then, when they don't it can be time consuming.  I do like actual rolling distros . . . which I do have a few of them.  So far ubuntu isn't rolling . . . but a few minutes to edit the source's list gets it close.

---

### Post by xyz-t on 2023-05-01
Mantic shows signs of life. There's a new Kernel to start with.

```
$ grep VERSION= /etc/os-release | cut -d ' ' -f 2-  | tr -d '"'
(Mantic Minotaur)

```
```
$ ls /lib/modules
6.2.0-21-generic  6.3.1-060301-generic
```

```
$  grep "upgrade " /var/log/dpkg.log
...
2023-05-01 20:38:33 upgrade base-files:amd64 12.3ubuntu2 12.3ubuntu3
2023-05-01 20:38:34 upgrade distro-info-data:all 0.57 0.58
2023-05-01 20:38:35 upgrade ubuntu-minimal:amd64 1.501 1.502
2023-05-01 20:38:35 upgrade ubuntu-standard:amd64 1.501 1.502
2023-05-01 20:38:35 upgrade alsa-ucm-conf:all 1.2.6.3-1ubuntu8 1.2.6.3-1ubuntu9
2023-05-01 20:38:41 upgrade linux-generic:amd64 6.2.0.20.20 6.2.0.21.21
2023-05-01 20:38:41 upgrade linux-image-generic:amd64 6.2.0.20.20 6.2.0.21.21
2023-05-01 20:38:52 upgrade linux-headers-generic:amd64 6.2.0.20.20 6.2.0.21.21
```

---

### Post by este.el.paz on 2023-05-02
MAN-tic does not live by kernel alone . . . there should be a few more packages to put GUI flesh on the minotaur . . . ????   :-k:cool:

---

### Post by loftwyr on 2023-05-03
We have a schedule! [https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989](https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989)

---

### Post by IanW on 2023-05-03
Official development codname is Mantic Minotaur

[https://lists.ubuntu.com/archives/ubuntu-devel/2023-May/042555.html](https://lists.ubuntu.com/archives/ubuntu-devel/2023-May/042555.html)

---

### Post by corradoventu on 2023-05-05
Legacy ISO available: [https://cdimages.ubuntu.com/daily-legacy/pending/](https://cdimages.ubuntu.com/daily-legacy/pending/)

---

### Post by sudodus on 2023-05-05
> **corradoventu said:**
> Legacy ISO available: [https://cdimages.ubuntu.com/daily-legacy/pending/](https://cdimages.ubuntu.com/daily-legacy/pending/)

Thanks for the heads up :KS

[hr][/hr]
Edit: Budgie, Cinnamon and Unity Mantic ISOs available via the ISO testing tracker ... and Lubuntu (I'm zsyncing now)

---

### Post by TenPlus1 on 2023-05-06
@IanW - Lolz!

Already upgraded desktop to Mantic and so far all is well, will keep testing...

---

### Post by este.el.paz on 2023-05-07
edited /etc/apt/sources.list to mantic and running update/dist-upgrade just pulled in 161 new packages . . . ??  Off to the races with the Minotaur . . . .

---

### Post by corradoventu on 2023-05-14
Installed Mantic from ISO [https://cdimage.ubuntu.com/daily-live/pending/](https://cdimage.ubuntu.com/daily-live/pending/) dated 2023-05-14 07:19 
Here the screens from my install: [https://drive.google.com/drive/folders/1jWg2ckXno0zeiUbAcQR_7DW1vgwYcs1P?usp=sharing](https://drive.google.com/drive/folders/1jWg2ckXno0zeiUbAcQR_7DW1vgwYcs1P?usp=sharing)
> corrado@corrado-n4-mm-0514:~$ inxi -SCGx
System:
  Host: corrado-n4-mm-0514 Kernel: 6.2.0-21-generic arch: x86_64 bits: 64
    compiler: N/A Desktop: GNOME v: 44.0 Distro: Ubuntu 23.10 (Mantic Minotaur)
CPU:
  Info: 6-core model: 11th Gen Intel Core i5-11400 bits: 64 type: MT MCP
    arch: Rocket Lake rev: 1 cache: L1: 480 KiB L2: 3 MiB L3: 12 MiB
  Speed (MHz): avg: 2450 high: 2600 min/max: 800/4400 cores: 1: 2600 2: 2600
    3: 2600 4: 2600 5: 2600 6: 2600 7: 800 8: 2600 9: 2600 10: 2600 11: 2600
    12: 2600 bogomips: 62208
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel RocketLake-S GT1 [UHD Graphics 730] vendor: Gigabyte
    driver: i915 v: kernel arch: Gen-12.1 bus-ID: 00:02.0
  Device-2: Logitech HD Webcam C615 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 1-5:4
  Display: wayland server: X.Org v: 1.22.1.9 with: Xwayland v: 23.1.1
    compositor: gnome-shell driver: dri: iris gpu: i915
    resolution: 1920x1080~60Hz
  API: OpenGL v: 4.6 Mesa 23.0.3 renderer: Mesa Intel Graphics (RKL GT1)
    direct-render: Yes
corrado@corrado-n4-mm-0514:~$ 


---

### Post by este.el.paz on 2023-05-14
Today booted up in Mantic on my '12 Mac Pro . . . when first logged in the Nvidia 780 graohics card seemed to spin up to "high rpms" such that it was "loud" . . . with just the browser open . . . bunch of tabs, but otherwise no "load" . . . .

Started to think I would have to run an update and reboot out of it . . . and then it dropped down in rpm's to more or less "normal" . . . .  

What's up with that??  Is that the "manticity" in action???

---

### Post by corradoventu on 2023-05-18
New software-properties 0.99.37 uses deb822-formatted .sources files to manage PPA.
[https://discourse.ubuntu.com/t/improvements-to-ppa-management-in-23-10/35783](https://discourse.ubuntu.com/t/improvements-to-ppa-management-in-23-10/35783)
[https://discourse.ubuntu.com/t/spec-apt-deb822-sources-by-default/29333](https://discourse.ubuntu.com/t/spec-apt-deb822-sources-by-default/29333)
so installing Firefox Nightly from [https://gist.github.com/brenopolanski/2a25088801b2de342200](https://gist.github.com/brenopolanski/2a25088801b2de342200)
i have:
```
corrado@n02-mm-0514:~$ cat /etc/apt/sources.list.d/ubuntu-mozilla-daily-ubuntu-ppa-mantic.sources
Types: deb
URIs: https://ppa.launchpadcontent.net/ubuntu-mozilla-daily/ppa/ubuntu/
Suites: mantic
Components: main
Signed-By: 
 -----BEGIN PGP PUBLIC KEY BLOCK-----
 .
 mI0ESYo68wEEAKSgKJImCQIcSP/b+24TS0NYzxpf5Y34WOfQBaGpTVhkSXx2TCcF
 +kC0P3zzwAsrvL8AULpr2Ww33ahnQ7Cg3kzBxTneo6jdvQOBwshSHMey/PhBAu0e
 w9zrt/OuKToMJY2h0TRA2EG6OfcTA8LOm1wkWWadTUG+fqduKKeHDmjdABEBAAG0
......
```

---

