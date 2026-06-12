---
title: "Ubuntu 24.04 LTS - WOW Fast"
date: 2024-04-27
forum: The Cafe
---

### Post by BBQdave on 2024-04-27
Loaded Ubuntu 24.04 LTS and wow, nicely done :)

The install was very easy. The desktop is fast and cleanly responsive.

Personal preference: I like that I can set desktop colors to sage and the choice of a basic software install - so I can add the applications I need and not have a lot of clutter.
Really great desktop experience :)

Thanks to all that help here on the forum!

---

### Post by donald187 on 2024-05-01
It did seem fast.  Ubuntu 24.04.  But then I'm on a relatively new computer with an ssd so it's hard to tell.  

The installation was smooth.  I like the installer.  

I had a problem with the Main Menu app (alacarte).  A couple of buttons kept crashing the app.  Had to work around that.  

And I use secret-tool (package libsecret-tools) to store passwords but the login keyring hadn't been formed automatically so it didn't work.  After ten minutes of Googling I created a keyring named login.  Logged out and back in and theat's when the system created its own login keyring.  So I deleted mine and then secret-tool worked.  

Anyway I decided to go back to 22.04 since who knew what else might break.

---

### Post by phatton1 on 2024-05-01
I was on 22.04, but did a clean install yesterday of 24.04, and so far have been really impressed with the performance.

---

### Post by currentshaft on 2024-05-07
sl

---

### Post by keshara283 on 2024-05-11
I was extremely impressed with the 23.10 release as well. My primary personal laptop (ThinkPad T470s) tends to get distro-hopped quite often, and when 23.10 released I decided to try out Ubuntu again after years away from it. The install went smooth and fast, and I ended up staying on 23.10 for that machine with no interest in distro-hopping it again.

When 24.04 released, the ThinkPad got the upgrade a day later, which I chose to fresh install instead of forcing the upgrade process. I was so impressed by the experience on 24.04 it sparked me to replace my Arch install on my Desktop for 24.04 as well. I don't think I've ever been happier with Ubuntu as my daily driver, so yeah I agree, great work Canonical devs for the fantastic release!

---

### Post by randomwords2 on 2024-05-12
Overall it's good for me except that I still get random freezes that I need to do a hard reset on.  

I think this is a relevant log message though they seem to vary on occasion:
> nouveau 0000:41:00.0: gr: GPC0/PROP trap: 00000010 [RT_WIDTH_OVERRUN] x = 672, y = 128, format = 11, storage type = 0

I haven't been able to consistently reproduce the issue and I'm trying to figure out how to narrow it down.  I've tried new releases, other graphics cards, verified my RAM is good. etc.  To me, it seems like a bug.

---

### Post by niceflipper8827 on 2024-05-25
I came back to Ubuntu after quite a few distro-hops including Fedora,Debian,Antix,Manjaro and Slackware. I eventually decided  to come back to  Xubuntu even though I have a pretty beefy work station  which could certainly handle both KDE Plasma and GNOME however, I don't like where either the KDE or  GNOME developers have taken either of those desktop environments.

---

### Post by 909mjolnir on 2024-05-29
Yeah, I am comfortable with the recent installer too.  
I think it's the same one.  I installed Ubuntu Mate finally, after so much distro hopping.  
The Debian installer had me freaked out with almost no feedback and no functioning sudo after install(!).  

It's funny to come back to Ubunut after all these years, but it seems worth it.  
I'm liking Mate more than Cinnamon and Manjaro recently dropped Mate ISOs.

---

### Post by poorguy on 2024-06-01
I haven't tried Ubuntu 24.04 LTS although I installed Xubuntu 24.04 LTS on this 17 year old computer and runs great.

```


xubuntu@xubuntu:~$ inxi -Fxz
System:
  Kernel: 6.8.0-31-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
  Desktop: Xfce v: 4.18.1 Distro: Xubuntu 24.04 LTS (Noble Numbat)
    base: Ubuntu
Machine:
  Type: Desktop System: HP-Pavilion product: GN556AA-ABA a6200n v: N/A
    serial: <superuser required>
  Mobo: ECS model: Nettle2 v: 1.0 serial: <superuser required> BIOS: Phoenix
    v: 5.12 date: 06/11/2007
CPU:
  Info: dual core model: AMD Athlon 64 X2 5600+ bits: 64 type: MCP arch: K8
    rev: 3 cache: L1: 256 KiB L2: 2 MiB
  Speed (MHz): avg: 1000 min/max: 1000/2800 cores: 1: 1000 2: 1000
    bogomips: 11251
  Flags: ht lm nx pae sse sse2 sse3 svm
Graphics:
  Device-1: AMD Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    vendor: Pegatron driver: radeon v: kernel arch: TeraScale-2 bus-ID: 02:00.0
    temp: 49.5 C
  Display: x11 server: X.Org v: 21.1.11 driver: X: loaded: radeon
    unloaded: fbdev,modesetting,vesa dri: r600 gpu: radeon
    resolution: 1024x768~75Hz
  API: EGL v: 1.5 drivers: r600,swrast platforms:
    active: x11,surfaceless,device inactive: gbm,wayland
  API: OpenGL v: 4.5 vendor: mesa v: 24.0.5-1ubuntu1 glx-v: 1.4
    direct-render: yes renderer: AMD CAICOS (DRM 2.50.0 / 6.8.0-31-generic LLVM
    17.0.6)
Audio:
  Device-1: NVIDIA MCP61 High Definition Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:05.0
  Device-2: AMD Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM R5
    230/235/235X OEM] vendor: Pegatron driver: snd_hda_intel v: kernel
    bus-ID: 02:00.1
  API: ALSA v: k6.8.0-31-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active
  Server-2: PulseAudio v: 16.1 status: off (using pipewire-pulse)
Network:
  Device-1: NVIDIA MCP61 Ethernet vendor: Hewlett-Packard type: network bridge
    driver: forcedeth v: kernel port: ec00 bus-ID: 00:07.0
  IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 76.69 GiB used: 10.47 GiB (13.7%)
  ID-1: /dev/sda vendor: Hitachi model: HDS721680PLAT80 size: 76.69 GiB
Partition:
  ID-1: / size: 74.93 GiB used: 10.47 GiB (14.0%) fs: ext4 dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: 37.0 C mobo: N/A gpu: radeon temp: 50.0 C
  Fan Speeds (rpm): N/A
Info:
  Memory: total: 8 GiB available: 7.76 GiB used: 1.29 GiB (16.6%)
  Processes: 184 Uptime: 42m Init: systemd target: graphical (5)
  Packages: 1463 Compilers: gcc: 13.2.0 Shell: Bash v: 5.2.21 inxi: 3.3.34
xubuntu@xubuntu:~$ 


```

---

