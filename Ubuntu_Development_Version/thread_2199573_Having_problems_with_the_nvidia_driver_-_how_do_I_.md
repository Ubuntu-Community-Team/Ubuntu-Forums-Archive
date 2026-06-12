---
title: "Having problems with the nvidia driver - how do I debug?"
date: 2014-01-14
forum: Ubuntu Development Version
---

### Post by jmmL on 2014-01-14
I'm up-to-date with all the latest trusty updates. In addition I have the xorg-edgers and bumblebee ppa installed, although this bug also existed before I added those repos. I have an nVidia GTX 640M GPU, and an Intel i5 Ivy-Bridge CPU.

Attempting to install nvidia-331-updates + bumblebee-nvidia (and their dependencies) results in booting into the low-graphics mode prompt (incidentally, I have no mouse cursor at this stage). The only way to get my usual graphical environment back is to uninstall the packages. Additionally, I have found that I need to delete ~/.Xauthority after this to prevent a login loop with lightdm.

I am very willing to provide logs etc, if only I knew which ones would be relevant. The only message that is displayed on the screen that would indicate a problem is that nvidia-prime has failed to set a power-saving mode of some sort. Any help would be brilliant!

---

### Post by mc4man on 2014-01-16
Do you have both nvidia-prime & bumblebee/primus/nvidia-bumblebee installed?

---

### Post by jmmL on 2014-01-16
> **mc4man said:**
> Do you have both nvidia-prime & bumblebee/primus/nvidia-bumblebee installed?
Yes, when I have nvidia-331-updates, nvidia-prime (which is pulled in as a dependency), and bumblebee-nvidia.

Is this likely to be an issue? Thanks for the reply!

---

### Post by deadflowr on 2014-01-16
> **jmmL said:**
> Yes, when I have nvidia-331-updates, nvidia-prime (which is pulled in as a dependency), and bumblebee-nvidia.

Is this likely to be an issue? Thanks for the reply!

Yes, you'll need to purge bumblebee to use nvidia-prime
Looky Here
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
Towards the bottom has the command to run to uninstall bumblebbe and then which nvidia packages to install.

---

### Post by jmmL on 2014-01-16
> **deadflowr said:**
> Yes, you'll need to purge bumblebee to use nvidia-prime
Looky Here
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
Towards the bottom has the command to run to uninstall bumblebbe and then which nvidia packages to install.
Ok, cheers. I do quite like the bumblebee way of doing things though (which, as I understand it, only powers up the nvidia GPU when optirun is called, as opposed to nvidia-prime, which uses the dedicated GPU for everything). Would you expect nvidia-331 to function without -prime, but with bumblebee instead?

---

### Post by jmmL on 2014-01-16
I've found what I think are relevant errors.

kern.log:

```
Jan 16 22:53:29 robot kernel: [    7.256585] bbswitch: version 0.8
Jan 16 22:53:29 robot kernel: [    7.256592] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
Jan 16 22:53:29 robot kernel: [    7.256598] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
Jan 16 22:53:29 robot kernel: [    7.256608] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
Jan 16 22:53:29 robot kernel: [    7.256694] bbswitch: detected an Optimus _DSM function
Jan 16 22:53:29 robot kernel: [    7.256701] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
Jan 16 22:53:31 robot kernel: [    8.766276] nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
Jan 16 22:53:31 robot kernel: [    8.772096] NVRM: failed to copy vbios to system memory.
Jan 16 22:53:31 robot kernel: [    8.774118] NVRM: RmInitAdapter failed! (0x30:0xffffffff:720)
Jan 16 22:53:31 robot kernel: [    8.774125] NVRM: rm_init_adapter failed for device bearing minor number 0
Jan 16 22:53:31 robot kernel: [    8.774143] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5
Jan 16 22:53:31 robot kernel: [    9.132267] r8169 0000:05:00.2 eth1: link up
Jan 16 22:53:31 robot kernel: [    9.132275] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 16 22:53:43 robot kernel: [   21.246776] nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
Jan 16 22:53:43 robot kernel: [   21.252543] NVRM: failed to copy vbios to system memory.
Jan 16 22:53:43 robot kernel: [   21.254600] NVRM: RmInitAdapter failed! (0x30:0xffffffff:720)
Jan 16 22:53:43 robot kernel: [   21.254607] NVRM: rm_init_adapter failed for device bearing minor number 0
Jan 16 22:53:43 robot kernel: [   21.254622] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5
```

tail Xorg.log | grep EE:

```
[    21.196] Initializing built-in extension MIT-SCREEN-SAVER
[    21.219] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    21.219] (EE) NVIDIA(GPU-0):     check your system's kernel log for additional error
[    21.219] (EE) NVIDIA(GPU-0):     messages and refer to Chapter 8: Common Problems in the
[    21.219] (EE) NVIDIA(GPU-0):     README for additional information.
[    21.219] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
[    21.220] (EE) NVIDIA(0): Failing initialization of X screen 0
[    21.224] (EE) Screen(s) found, but none have a usable configuration.
[    21.224] (EE) 
[    21.224] (EE) no screens found(EE) 
[    21.224] (EE) 
[    21.224] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    21.224] (EE) 
[    21.228] (EE) Server terminated with error (1). Closing log file.

```

---

### Post by mc4man on 2014-01-16
Well you can use bumblebee instead of nvidia-prime, nvidia-331 has a dep, (recommend)  on  - 
"nvidia-prime (>=0.5) | bumblebee" 
So for BB just install bumblebee, nvidia-bumblebee, then  remove nvidia-prime

Here with a 660m I think nvidia-prime isn't worth using, personally can't stand the lack of vsync

---

### Post by jmmL on 2014-01-17
> **mc4man said:**
> Well you can use bumblebee instead of nvidia-prime, nvidia-331 has a dep, (recommend)  on  - 
"nvidia-prime (>=0.5) | bumblebee" 
So for BB just install bumblebee, nvidia-bumblebee, then  remove nvidia-prime

Here with a 660m I think nvidia-prime isn't worth using, personally can't stand the lack of vsync
It seems like nvidia-331 is no longer pulling in nvidia-prime as a dependency, which is handy. So at least I can *install *the nvidia driver and still boot to my normal desktop. Unfortunately at this stage optirun is not working. I'm getting these errors:

```
@robot:~$ optirun -vv glxspheres64 
[  199.078973] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[  199.079305] [DEBUG]optirun version 3.2.1 starting...
[  199.079316] [DEBUG]Active configuration:
[  199.079319] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  199.079322] [DEBUG] X display: :8
[  199.079325] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-331:/usr/lib32/nvidia-331
[  199.079327] [DEBUG] Socket path: /var/run/bumblebee.socket
[  199.079330] [DEBUG] Accel/display bridge: auto
[  199.079333] [DEBUG] VGL Compression: proxy
[  199.079336] [DEBUG] VGLrun extra options: 
[  199.079338] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[  199.079386] [DEBUG]Using auto-detected bridge virtualgl
[  199.719625] [INFO]Response: No - error: [XORG] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[  199.719643] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[  199.719650] [DEBUG]Socket closed.
[  199.719665] [ERROR]Aborting because fallback start is disabled.

```

---

### Post by jmmL on 2014-01-18
This appears to be a known problem with the nvidia driver on kernels 3.13+ [https://devtalk.nvidia.com/default/topic/644906/linux/331-20-on-3-13-rc1-kernel/](https://devtalk.nvidia.com/default/topic/644906/linux/331-20-on-3-13-rc1-kernel/)

EDIT: I can confirm that using 3.12 from the mainline ppa works around this bug.

---

### Post by jmmL on 2014-01-30
This is fixed with the latest updates to nvidia-331 (specifically -ubuntu3)

---

### Post by Amorget on 2014-01-30
Question for you, unrelated to your issue (sort of).  How does the HDMI out work with the Nvidia 331 drivers and Bumblebee?

---

### Post by jmmL on 2014-01-31
> **Amorget said:**
> Question for you, unrelated to your issue (sort of).  How does the HDMI out work with the Nvidia 331 drivers and Bumblebee?

I'm afraid I don't personally have any experience with that (nor a way of testing it).

---

### Post by Amorget on 2014-01-31
No worries, thanks for letting me know!

---

