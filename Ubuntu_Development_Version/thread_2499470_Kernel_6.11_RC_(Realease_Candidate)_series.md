---
title: "Kernel 6.11 RC (Realease Candidate) series"
date: 2024-07-28
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-07-28
[Kernel 6.1-rc1]("https://kernel.ubuntu.com/mainline/v6.11-rc1/") is available. The mainline compile seems to have worked for AMD64.

Just starting this thread. It'll be later before I can try it.

EDIT: Just trying it now:
```
doug@s19:~$ uname -a
Linux s19 6.11.0-061100rc1-generic #202407281809 SMP PREEMPT_DYNAMIC Sun Jul 28 22:21:22 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by corradoventu on 2024-07-29
```
corrado@corrado-n02-oo-0718:~$ uname -a
Linux corrado-n02-oo-0718 6.11.0-061100rc1-generic #202407281809 SMP PREEMPT_DYNAMIC Sun Jul 28 22:21:22 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-n02-oo-0718:~$ inxi -SCGxc
System:
  Host: corrado-n02-oo-0718 Kernel: 6.11.0-061100rc1-generic arch: x86_64
    bits: 64 compiler: gcc v: 13.3.0
  Desktop: GNOME v: 46.3.1 Distro: Ubuntu 24.10 (Oracular Oriole)
CPU:
  Info: quad core model: 12th Gen Intel Core i3-12100 bits: 64 type: MT MCP
    arch: Alder Lake rev: 5 cache: L1: 320 KiB L2: 5 MiB L3: 12 MiB
  Speed (MHz): avg: 800 min/max: 800/4300 cores: 1: 800 2: 800 3: 800 4: 800
    5: 800 6: 800 7: 800 8: 800 bogomips: 52838
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-S GT1 [UHD Graphics 730] vendor: ASUSTeK
    driver: i915 v: kernel arch: Gen-12.2 bus-ID: 00:02.0
  Device-2: Logitech QuickCam Pro 9000 driver: snd-usb-audio,uvcvideo
    type: USB bus-ID: 1-1:2
  Display: wayland server: X.Org v: 24.1 with: Xwayland v: 24.1.0
    compositor: gnome-shell driver: dri: iris gpu: i915
    resolution: 1920x1080~60Hz
  API: EGL v: 1.5 drivers: iris,swrast platforms:
    active: wayland,x11,surfaceless,device inactive: gbm
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa v: 24.0.9-0ubuntu2
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel UHD Graphics 730 (ADL-S
    GT1)
corrado@corrado-n02-oo-0718:~$ 

```

---

### Post by IanW on 2024-08-05
[Kernel 6.11rc2]("https://kernel.ubuntu.com/mainline/daily/2024-08-05/") has landed

---

