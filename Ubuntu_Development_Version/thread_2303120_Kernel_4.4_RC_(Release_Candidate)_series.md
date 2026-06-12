---
title: "Kernel 4.4 RC (Release Candidate) series"
date: 2015-11-16
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-11-16
Kernel 4.4 RC1 does not build for me. It seems the [Ubunutu PPA version]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc1-wily/") has the same issue. My error message:```
  DEPMOD  4.4.0-rc1-stock
depmod: WARNING: found 2 modules in dependency cycles!
depmod: WARNING: /home/doug/temp-k-git/linux/./debian/tmp/lib/modules/4.4.0-rc1-stock/kernel/drivers/staging/lustre/lnet/lnet/lnet.ko in dependency cycle!
depmod: WARNING: /home/doug/temp-k-git/linux/./debian/tmp/lib/modules/4.4.0-rc1-stock/kernel/drivers/staging/lustre/lustre/libcfs/libcfs.ko in dependency cycle!
./scripts/depmod.sh: line 57: 18619 Killed                  "$DEPMOD" "$@" "$KERNELRELEASE" $SYMBOL_PREFIX
make[3]: *** [_modinst_post] Error 137
make[2]: *** [bindeb-pkg] Error 2
make[1]: *** [bindeb-pkg] Error 2
make: *** [__build_one_by_one] Error 2
```PPA error message (copied from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc1-wily/BUILD.LOG.amd64")):```
  DEPMOD  4.4.0-040400rc1-generic
depmod: ERROR: Found 2 modules in dependency cycles!
depmod: ERROR: Cycle detected: lnet -> libcfs -> lnet
/home/kernel/COD/linux/Makefile:1139: recipe for target '_modinst_post' failed
make[2]: *** [_modinst_post] Error 1
make[2]: Leaving directory '/home/kernel/COD/linux/debian/build/build-generic'
Makefile:146: recipe for target 'sub-make' failed
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory '/home/kernel/COD/linux'
debian/rules.d/2-binary-arch.mk:93: recipe for target 'install-generic' failed
make: *** [install-generic] Error 2
```Has anyone figured out how to proceed?

EDIT 1: [https://lkml.org/lkml/2015/11/2/388](https://lkml.org/lkml/2015/11/2/388)
EDIT 2: [https://lkml.org/lkml/2015/11/6/987](https://lkml.org/lkml/2015/11/6/987)
EDIT 3: Patch applied, building now.
EDIT 4: Kernel compile completed. Running now. Some errors and warnings during boot.

---

### Post by tokyobadger on 2015-11-20
Late to the party but [Phoronix had an article on this](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-rc1-Ubuntu-Spin)

He's also hosting a patched kernel linked in the same article <-- haven't tried myself

---

### Post by QDR06VV9 on 2015-11-20
> **tokyobadger said:**
> Late to the party but [Phoronix had an article on this]("http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-rc1-Ubuntu-Spin")

He's also hosting a patched kernel linked in the same article <-- haven't tried myself
Decided to take this route, But no headers so it will break Nvidia of course.
I also noticed that he has one with the AMD GPU, might give that one a go a little later today.
Can't wait to see this one bench out.
So far so Good dose not seem to generate a lot of heat on my Nvidia card, And CPU Power consumption is just slightly higher with clock speed @2600Ghz 
```
me@me-Aspire-M3300:~$ inxi -bSystem:    
Host: me-Aspire-M3300 Kernel: 4.4.0-rc1-phoronix x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.0.5
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 1000.2GB (5.7% used)
Info:      Processes: 245 Uptime: 11 min Memory: 828.0/5967.2MB
           Client: Shell (bash) inxi: 2.2.28 



```
 Yee Haa! Now to start Benching.
**EDIT1:**Video is getting slightly better on [COLOR=#111111][FONT=Ubuntu]nouveau.
[/FONT][/COLOR]```
Running synchronized to the vertical refresh.  The framerate should beapproximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.343 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.002 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.001 FPS
300 frames in 5.0 seconds = 59.802 FPS
301 frames in 5.0 seconds = 59.993 FPS
300 frames in 5.0 seconds = 59.958 FPS
301 frames in 5.0 seconds = 60.049 FPS
300 frames in 5.0 seconds = 59.980 FPS
300 frames in 5.0 seconds = 59.995 FPS
301 frames in 5.0 seconds = 60.026 FPS
301 frames in 5.0 seconds = 60.008 FPS
300 frames in 5.0 seconds = 59.997 FPS
301 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.001 FPS
301 frames in 5.0 seconds = 60.004 FPS
301 frames in 5.0 seconds = 60.000 FPS

```[COLOR=#111111][FONT=Ubuntu]
Web using Chromium 4 Tabs with Video going.
And Kpat running.
[/FONT][/COLOR]**EDIT2: **Been running now for a couple hours with high to moderate usage, Very Pleased.
```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +36.0°C  (crit = +127.0°C)
temp2:        +46.0°C  (crit = +127.0°C)


nouveau-pci-0100
Adapter: PCI adapter
temp1:        +47.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +39.8°C  (high = +70.0°C)



```

Regards

---

### Post by P-I H on 2015-11-20
I been using Phoronix's  AMD GPU 4.3 kernel with re-clocking support for some days in Xenial. It supports re-clocking of tonga and fiji graphic cards. Unigen Heaven with a Radeon R9 380 without re-clocking runs with 7.2 FPS and with re-clocking 34.7 FPS.

---

### Post by Doug S on 2015-11-22
Kernel 4.4-rc2 is available (but not on the Ubuntu PPA yet).
In terms of ability to compile, it has the same issue as rc1.

As some others mentioned above, it can be made to compile via kernel config file changes only, instead of the patch method I used for rc1.
The kernel config file differences:```
doug@s15:/media/sda/home/doug/temp-k-git/linux$ [COLOR="#FF0000"]diff .config-4.4-rc1 .config-4.4-rc2[/COLOR]
6882,6889c6882
< CONFIG_LUSTRE_FS=m
< CONFIG_LUSTRE_OBD_MAX_IOCTL_BUFFER=8192
< # CONFIG_LUSTRE_DEBUG_EXPENSIVE_CHECK is not set
< CONFIG_LUSTRE_LLITE_LLOOP=m
< CONFIG_LNET=m
< CONFIG_LNET_MAX_PAYLOAD=1048576
< CONFIG_LNET_SELFTEST=m
< CONFIG_LNET_XPRT_IB=m
---
> # CONFIG_LUSTRE_FS is not set
```

Edit: actually, it appeared in the [ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2-wily/") (along with the compile issues) while I was writing this post.

---

### Post by Doug S on 2015-11-24
There are now completed builds in a special directory on the [Ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/"). 
I have some issues with my test server at the moment, and am unable to try the Ubuntu version of the 4.4-rc2 kernel, but I have been running my compile of 4.4-rc2 for a day or two now.

---

### Post by QDR06VV9 on 2015-11-24
Thanks Doug S
Everything seems to be fine.
Got Nvidia installed, Bonus!
I used this PPA  [B]ppa:graphics-drivers/ppa

[/B]```
$ inxi -b
System:    Host: me-Aspire-M3300 Kernel: 4.4.0-040400rc2-lowlatency x86_64 (64 bit)
           Desktop: MATE 1.12.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 500.1GB (28.6% used)
Info:      Processes: 228 Uptime: 3 min Memory: 466.7/5966.9MB
           Client: Shell (bash) inxi: 2.2.28 
```
Regards

---

### Post by fooman on 2015-11-24
thanks Doug S and runrickus....4.4 and nvidia running nicely here :D

```
Current Date/Time: Tue Nov 24 13:37:19 EST 2015
Distro Release: Ubuntu Xenial Xerus (development branch)
Kernel Release: Linux 4.4.0-040400rc2-generic
Gnome Release: GNOME Shell 3.18.2
Unity Release: unity 7.4.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.5.0 NVIDIA 358.16
```

---

### Post by lonniehenry-gmail on 2015-11-25
Doug S  I used the build in the ubuntu ppa and it loaded once, ran well with no issues.  I shut down and tried to restart and it crashed with a kernel panic.  I restarted with a previous kernel - no issues.  I tried restart to the 4.4 kernel and again got the kernel panic.   I restarted and purged the 4.4 kernel,   rebooted to 4.3 kernel.  I again installed the 4.4 kernel, rebooted.  4.4 came up and ran with no issues.  Rebooted and got the kernel panic.  Where to start looking for a solution?  Using Xenial Gnome 16.04

---

### Post by Doug S on 2015-11-25
> **lonniehenry-gmail said:**
> Doug S  I used the build in the ubuntu ppa and it loaded once, ran well with no issues.  I shut down and tried to restart and it crashed with a kernel panic.  I restarted with a previous kernel - no issues.  I tried restart to the 4.4 kernel and again got the kernel panic.   I restarted and purged the 4.4 kernel,   rebooted to 4.3 kernel.  I again installed the 4.4 kernel, rebooted.  4.4 came up and ran with no issues.  Rebooted and got the kernel panic.  Where to start looking for a solution?  Using Xenial Gnome 16.04The only thing I know to do in your situation is to bisect the kernel to identify the exact commit the caused the issue, and then report it (myself, I typically bypass launchpad and report it directly upstream). Bisecting the kernel can take a lot of time (I am in the middle of a bisection right now), and you need to be comfortable compiling the kernel. Since we are still relatively early in the RC series, you could also just wait and try rc3, rc4 ... to see if your issue gets resolved by someone else. The kernel should be fairly stable by about rc6.

Someone else might have some other suggestions.

---

### Post by lonniehenry-gmail on 2015-11-25
Thanks, I will wait then.  I tried compiling the kernel earlier, but was not successful.  I looked at the kern log but I really didn't know what I was looking at.  I appreciate your reply.

---

### Post by nikoszr on 2015-11-26
Hello! 
Is there someone available in giving me some istruction on how to update/isntall kernel 4.4?
The reason I want to try this is [here]("http://ubuntuforums.org/showthread.php?t=2303644"). 
Thank you very much!

---

### Post by zika on 2015-11-26
> **nikoszr said:**
> Hello! 
Is there someone available in giving me some istruction on how to update/isntall kernel 4.4?
The reason I want to try this is [here]("http://ubuntuforums.org/showthread.php?t=2303644"). 
Thank you very much!Let us assume that You're using amd64 PC.```
cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/linux-headers-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/linux-headers-4.4.0-040400rc2_4.4.0-040400rc2.201511231054_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/linux-image-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_amd64.deb
sudo dpkg -i linux-headers-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_amd64.deb linux-headers-4.4.0-040400rc2_4.4.0-040400rc2.201511231054_all.deb linux-image-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_amd64.deb
```After reboot choose 4.4 and You're done.

---

### Post by nikoszr on 2015-11-26
> [COLOR=#000000]Let us assume that You're using amd64 PC.[/COLOR]
Well to be honest I've no idea about that! :/ 
I think mine it's Intel (?). How can I finf out? I think it's stated during boot? 
In that case I should change it in the commands line I guess? 
Thank you!

---

### Post by zika on 2015-11-26
> **nikoszr said:**
> Well to be honest I've no idea about that! :/ 
I think mine it's Intel (?). How can I finf out? I think it's stated during boot? 
In that case I should change it in the commands line I guess? 
Thank you!Many ways. Let us start in simplest manner:```
uname -a
```

---

### Post by nikoszr on 2015-11-26
It returned this:
```
Linux nz-Satellite-L300D 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:49 UTC 2015 i686 i686 i686 GNU/Linux
```

---

### Post by Doug S on 2015-11-26
> **nikoszr said:**
> It returned this:
```
Linux nz-Satellite-L300D 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:49 UTC 2015 i686 i686 i686 GNU/Linux
```That is the 32 bit kernel. so zika's instructions would become:
```
cd /tmp
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/linux-headers-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/linux-headers-4.4.0-040400rc2_4.4.0-040400rc2.201511231054_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/linux-image-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_i386.deb
sudo dpkg -i linux-headers-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_i386.deb linux-headers-4.4.0-040400rc2_4.4.0-040400rc2.201511231054_all.deb linux-image-4.4.0-040400rc2-generic_4.4.0-040400rc2.201511231054_i386.deb
```Also, I always use a long timeout on grub, so that I have plenty of time to select the correct kernel. So my /etc/default/grub file has:```
GRUB_TIMEOUT=20
```

---

### Post by nikoszr on 2015-11-26
Thank you guys, but no, it didn't work for me  on my system. It seemed to download and isntall just fine (as far as I can tell) but then when I try to boot it's either a black screen or other kind of ubuntu screens (lol) which wont let me enter my password and log on (they freeze). After that, booting with 3.19 as soon as I log on I get the "system program probleme detecetd etc" sign but I don't see any distinct system problem while I run on 3.19. Any idea or advice?

---

### Post by Doug S on 2015-11-26
> **nikoszr said:**
> Thank you guys, but no, it didn't work for me  on my system. It seemed to download and isntall just fine (as far as I can tell) but then when I try to boot it's either a black screen or other kind of ubuntu screens (lol) which wont let me enter my password and log on (they freeze). After that, booting with 3.19 as soon as I log on I get the "system program probleme detecetd etc" sign but I don't see any distinct system problem while I run on 3.19. Any idea or advice?You might have some crash stuff from your Kernel 4.4-rc2 attempts left over in /var/crash. Just delete whatever is there and try again, you should then not get the "system program problem detected etc" pop up  box. As for Kernel 4.4, try waiting until later in the RC cycle, after things have settled down a little more.

---

### Post by nikoszr on 2015-11-26
> [COLOR=#000000]You might have some crash stuff from your Kernel 4.4-rc2 attempts left over in /var/crash. Just delete whatever is there and try again, you should then not get the "system program problem detected etc" pop up box.[/COLOR]
Oh thanks, yes I'll do that.
> [COLOR=#000000]As for Kernel 4.4, try waiting until later in the RC cycle, after things have settled down a little more.[/COLOR]
Okay I will, but what should I do for now? I mean do I have to remove/uninstall something from the 4.4. and how?
Thank you very much!

---

### Post by Doug S on 2015-11-26
> **nikoszr said:**
> Okay I will, but what should I do for now?You don't have to do anything for now. If it were me, I would go back to [here]("http://ubuntuforums.org/showthread.php?t=2303644&page=2&p=13396229#post13396229") and try to continue get that stuff to build.

> **nikoszr said:**
> I mean do I have to remove/uninstall something from the 4.4. and how?If you mean should you uninstall the 4.4-rc2 kernel, then I suppose yes. I have several installed kernels I need to delete at the moment. I'll copy and paste removal of one below (but keep in mind, you will have one other package to delete in your case):

First, I get a list of the kernels I have installed, so that I can just copy and paste the exact text identifying the packages (my list is a bit of a long mess at the moment):
```
doug@s15:~/temp$ [COLOR="#FF0000"]sudo dpkg -l | grep linux-[/COLOR]
ii  linux-firmware                            1.127.18                              all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                  3.16.0.53.44                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-50                   3.16.0-50.67~14.04.1                  all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-50-generic           3.16.0-50.67~14.04.1                  amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-51                   3.16.0-51.69~14.04.1                  all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-51-generic           3.16.0-51.69~14.04.1                  amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-53                   3.16.0-53.72~14.04.1                  all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-53-generic           3.16.0-53.72~14.04.1                  amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-4.1.0-rc6-tbad              4.1.0-rc6-tbad-82                     amd64        Linux kernel headers for 4.1.0-rc6-tbad on amd64
ii  linux-headers-4.1.0-rc6-tgood             4.1.0-rc6-tgood-83                    amd64        Linux kernel headers for 4.1.0-rc6-tgood on amd64
ii  linux-headers-4.3.0-040300                4.3.0-040300.201511020846             all          Header files related to Linux kernel version 4.3.0
ii  linux-headers-4.3.0-040300-generic        4.3.0-040300.201511020846             amd64        Linux kernel headers for version 4.3.0 on 64 bit x86 SMP
ii  linux-headers-4.3.0-bi                    4.3.0-bi-122                          amd64        Linux kernel headers for 4.3.0-bi on amd64
ii  linux-headers-4.3.0-ck-mod-fix            4.3.0-ck-mod-fix-106                  amd64        Linux kernel headers for 4.3.0-ck-mod-fix on amd64
ii  linux-headers-4.3.0-doug-new              4.3.0-doug-new-102                    amd64        Linux kernel headers for 4.3.0-doug-new on amd64
ii  [COLOR="#FF0000"]linux-headers-4.3.0-rc4-b[/COLOR]i                4.3.0-rc4-bi-123                      amd64        Linux kernel headers for 4.3.0-rc4-bi on amd64
ii  linux-headers-4.3.0-rc4-new5              4.3.0-rc4-new5-97                     amd64        Linux kernel headers for 4.3.0-rc4-new5 on amd64
ii  linux-headers-4.3.0-rc4-new6              4.3.0-rc4-new6-98                     amd64        Linux kernel headers for 4.3.0-rc4-new6 on amd64
ii  linux-headers-4.3.0-rc5-bi                4.3.0-rc5-bi-129                      amd64        Linux kernel headers for 4.3.0-rc5-bi on amd64
ii  linux-headers-4.3.0-rc5-prarit            4.3.0-rc5-prarit-88                   amd64        Linux kernel headers for 4.3.0-rc5-prarit on amd64
ii  linux-headers-4.3.0-rc5-stock             4.3.0-rc5-stock-85                    amd64        Linux kernel headers for 4.3.0-rc5-stock on amd64
ii  linux-headers-4.3.0-rc5-subad             4.3.0-rc5-subad-130                   amd64        Linux kernel headers for 4.3.0-rc5-subad on amd64
ii  linux-headers-4.3.0-rc5-sugood            4.3.0-rc5-sugood-132                  amd64        Linux kernel headers for 4.3.0-rc5-sugood on amd64
ii  linux-headers-4.3.0-rc6-bi                4.3.0-rc6-bi-118                      amd64        Linux kernel headers for 4.3.0-rc6-bi on amd64
ii  linux-headers-4.3.0-rc6-doug-new          4.3.0-rc6-doug-new-100                amd64        Linux kernel headers for 4.3.0-rc6-doug-new on amd64
ii  linux-headers-4.3.0-rc7-bi                4.3.0-rc7-bi-120                      amd64        Linux kernel headers for 4.3.0-rc7-bi on amd64
ii  linux-headers-4.3.0-rc7-doug-new          4.3.0-rc7-doug-new-101                amd64        Linux kernel headers for 4.3.0-rc7-doug-new on amd64
ii  linux-headers-4.3.0-stock                 4.3.0-stock-104                       amd64        Linux kernel headers for 4.3.0-stock on amd64
ii  linux-headers-4.4.0-040400rc2             4.4.0-040400rc2.201511231054          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-040400rc2-generic     4.4.0-040400rc2.201511231054          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-rc1-circular          4.4.0-rc1-circular-108                amd64        Linux kernel headers for 4.4.0-rc1-circular on amd64
ii  linux-headers-4.4.0-rc1-pb                4.4.0-rc1-pb-110                      amd64        Linux kernel headers for 4.4.0-rc1-pb on amd64
ii  linux-headers-4.4.0-rc1-pl                4.4.0-rc1-pl-109                      amd64        Linux kernel headers for 4.4.0-rc1-pl on amd64
ii  linux-headers-4.4.0-rc2-ck-mod-fix        4.4.0-rc2-ck-mod-fix-115              amd64        Linux kernel headers for 4.4.0-rc2-ck-mod-fix on amd64
ii  linux-headers-4.4.0-rc2-pl2               4.4.0-rc2-pl2-114                     amd64        Linux kernel headers for 4.4.0-rc2-pl2 on amd64
ii  linux-headers-4.4.0-rc2-stock             4.4.0-rc2-stock-111                   amd64        Linux kernel headers for 4.4.0-rc2-stock on amd64
ii  linux-headers-generic-lts-utopic          3.16.0.53.44                          amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-50-generic             3.16.0-50.67~14.04.1                  amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-51-generic             3.16.0-51.69~14.04.1                  amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-53-generic             3.16.0-53.72~14.04.1                  amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-4.1.0-rc6-tbad                4.1.0-rc6-tbad-82                     amd64        Linux kernel, version 4.1.0-rc6-tbad
ii  linux-image-4.1.0-rc6-tgood               4.1.0-rc6-tgood-83                    amd64        Linux kernel, version 4.1.0-rc6-tgood
ii  linux-image-4.3.0-040300-generic          4.3.0-040300.201511020846             amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.3.0-bi                      4.3.0-bi-122                          amd64        Linux kernel, version 4.3.0-bi
ii  linux-image-4.3.0-ck-mod-fix              4.3.0-ck-mod-fix-106                  amd64        Linux kernel, version 4.3.0-ck-mod-fix
ii  linux-image-4.3.0-doug-new                4.3.0-doug-new-102                    amd64        Linux kernel, version 4.3.0-doug-new
ii  [COLOR="#FF0000"]linux-image-4.3.0-rc4-bi[/COLOR]                  4.3.0-rc4-bi-123                      amd64        Linux kernel, version 4.3.0-rc4-bi
ii  linux-image-4.3.0-rc4-new5                4.3.0-rc4-new5-97                     amd64        Linux kernel, version 4.3.0-rc4-new5
ii  linux-image-4.3.0-rc4-new6                4.3.0-rc4-new6-98                     amd64        Linux kernel, version 4.3.0-rc4-new6
ii  linux-image-4.3.0-rc5-bi                  4.3.0-rc5-bi-129                      amd64        Linux kernel, version 4.3.0-rc5-bi
ii  linux-image-4.3.0-rc5-prarit              4.3.0-rc5-prarit-88                   amd64        Linux kernel, version 4.3.0-rc5-prarit
ii  linux-image-4.3.0-rc5-stock               4.3.0-rc5-stock-85                    amd64        Linux kernel, version 4.3.0-rc5-stock
ii  linux-image-4.3.0-rc5-subad               4.3.0-rc5-subad-130                   amd64        Linux kernel, version 4.3.0-rc5-subad
ii  linux-image-4.3.0-rc5-sugood              4.3.0-rc5-sugood-132                  amd64        Linux kernel, version 4.3.0-rc5-sugood
ii  linux-image-4.3.0-rc6-bi                  4.3.0-rc6-bi-118                      amd64        Linux kernel, version 4.3.0-rc6-bi
ii  linux-image-4.3.0-rc6-doug-new            4.3.0-rc6-doug-new-100                amd64        Linux kernel, version 4.3.0-rc6-doug-new
ii  linux-image-4.3.0-rc7-bi                  4.3.0-rc7-bi-120                      amd64        Linux kernel, version 4.3.0-rc7-bi
ii  linux-image-4.3.0-rc7-doug-new            4.3.0-rc7-doug-new-101                amd64        Linux kernel, version 4.3.0-rc7-doug-new
ii  linux-image-4.3.0-stock                   4.3.0-stock-104                       amd64        Linux kernel, version 4.3.0-stock
ii  linux-image-4.4.0-040400rc2-generic       4.4.0-040400rc2.201511231054          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-rc1-circular            4.4.0-rc1-circular-108                amd64        Linux kernel, version 4.4.0-rc1-circular
ii  linux-image-4.4.0-rc1-pb                  4.4.0-rc1-pb-110                      amd64        Linux kernel, version 4.4.0-rc1-pb
ii  linux-image-4.4.0-rc1-pl                  4.4.0-rc1-pl-109                      amd64        Linux kernel, version 4.4.0-rc1-pl
ii  linux-image-4.4.0-rc2-ck-mod-fix          4.4.0-rc2-ck-mod-fix-115              amd64        Linux kernel, version 4.4.0-rc2-ck-mod-fix
ii  linux-image-4.4.0-rc2-pl2                 4.4.0-rc2-pl2-114                     amd64        Linux kernel, version 4.4.0-rc2-pl2
ii  linux-image-4.4.0-rc2-stock               4.4.0-rc2-stock-111                   amd64        Linux kernel, version 4.4.0-rc2-stock
ii  linux-image-extra-3.16.0-50-generic       3.16.0-50.67~14.04.1                  amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-51-generic       3.16.0-51.69~14.04.1                  amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic       3.16.0-53.72~14.04.1                  amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-utopic            3.16.0.53.44                          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                      3.13.0-68.111                         amd64        Linux Kernel Headers for development
doug@s15:~/temp$

```
uninstall the headers package and uninstall and purge the kernel package:
```
doug@s15:~/temp$ [COLOR="#FF0000"]sudo dpkg -r linux-headers-4.3.0-rc4-bi[/COLOR]
(Reading database ... 824904 files and directories currently installed.)
Removing linux-headers-4.3.0-rc4-bi (4.3.0-rc4-bi-123) ...
doug@s15:~/temp$ [COLOR="#FF0000"]sudo dpkg -P linux-image-4.3.0-rc4-bi[/COLOR]
(Reading database ... 804797 files and directories currently installed.)
Removing linux-image-4.3.0-rc4-bi (4.3.0-rc4-bi-123) ...
update-initramfs: Deleting /boot/initrd.img-4.3.0-rc4-bi
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-040400rc2-generic
Found initrd image: /boot/initrd.img-4.4.0-040400rc2-generic
Found linux image: /boot/vmlinuz-4.4.0-rc2-ck-mod-fix
Found initrd image: /boot/initrd.img-4.4.0-rc2-ck-mod-fix
Found linux image: /boot/vmlinuz-4.4.0-rc2-stock
Found initrd image: /boot/initrd.img-4.4.0-rc2-stock
Found linux image: /boot/vmlinuz-4.4.0-rc2-pl2
Found initrd image: /boot/initrd.img-4.4.0-rc2-pl2
Found linux image: /boot/vmlinuz-4.4.0-rc1-pl
Found initrd image: /boot/initrd.img-4.4.0-rc1-pl
Found linux image: /boot/vmlinuz-4.4.0-rc1-pb
Found initrd image: /boot/initrd.img-4.4.0-rc1-pb
Found linux image: /boot/vmlinuz-4.4.0-rc1-circular
Found initrd image: /boot/initrd.img-4.4.0-rc1-circular
Found linux image: /boot/vmlinuz-4.3.0-doug-new
Found initrd image: /boot/initrd.img-4.3.0-doug-new
Found linux image: /boot/vmlinuz-4.3.0-ck-mod-fix
Found initrd image: /boot/initrd.img-4.3.0-ck-mod-fix
Found linux image: /boot/vmlinuz-4.3.0-040300-generic
Found initrd image: /boot/initrd.img-4.3.0-040300-generic
Found linux image: /boot/vmlinuz-4.3.0-stock
Found initrd image: /boot/initrd.img-4.3.0-stock
Found linux image: /boot/vmlinuz-4.3.0-bi
Found initrd image: /boot/initrd.img-4.3.0-bi
Found linux image: /boot/vmlinuz-4.3.0-rc7-doug-new
Found initrd image: /boot/initrd.img-4.3.0-rc7-doug-new
Found linux image: /boot/vmlinuz-4.3.0-rc7-bi
Found initrd image: /boot/initrd.img-4.3.0-rc7-bi
Found linux image: /boot/vmlinuz-4.3.0-rc6-doug-new
Found initrd image: /boot/initrd.img-4.3.0-rc6-doug-new
Found linux image: /boot/vmlinuz-4.3.0-rc6-bi
Found initrd image: /boot/initrd.img-4.3.0-rc6-bi
Found linux image: /boot/vmlinuz-4.3.0-rc5-sugood
Found initrd image: /boot/initrd.img-4.3.0-rc5-sugood
Found linux image: /boot/vmlinuz-4.3.0-rc5-subad
Found initrd image: /boot/initrd.img-4.3.0-rc5-subad
Found linux image: /boot/vmlinuz-4.3.0-rc5-stock
Found initrd image: /boot/initrd.img-4.3.0-rc5-stock
Found linux image: /boot/vmlinuz-4.3.0-rc5-prarit
Found initrd image: /boot/initrd.img-4.3.0-rc5-prarit
Found linux image: /boot/vmlinuz-4.3.0-rc5-bi
Found initrd image: /boot/initrd.img-4.3.0-rc5-bi
Found linux image: /boot/vmlinuz-4.3.0-rc4-new6
Found initrd image: /boot/initrd.img-4.3.0-rc4-new6
Found linux image: /boot/vmlinuz-4.3.0-rc4-new5
Found initrd image: /boot/initrd.img-4.3.0-rc4-new5
Found linux image: /boot/vmlinuz-4.1.0-rc6-tgood
Found initrd image: /boot/initrd.img-4.1.0-rc6-tgood
Found linux image: /boot/vmlinuz-4.1.0-rc6-tbad
Found initrd image: /boot/initrd.img-4.1.0-rc6-tbad
Found linux image: /boot/vmlinuz-3.16.0-53-generic
Found initrd image: /boot/initrd.img-3.16.0-53-generic
Found linux image: /boot/vmlinuz-3.16.0-51-generic
Found initrd image: /boot/initrd.img-3.16.0-51-generic
Found linux image: /boot/vmlinuz-3.16.0-50-generic
Found initrd image: /boot/initrd.img-3.16.0-50-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu Xenial Xerus (development branch) (16.04) on /dev/sdb1
done
Purging configuration files for linux-image-4.3.0-rc4-bi (4.3.0-rc4-bi-123) ...
doug@s15:~/temp$

```

---

### Post by nikoszr on 2015-11-27
> [COLOR=#000000]You don't have to do anything for now. If it were me, I would go back to [/COLOR][here]("http://ubuntuforums.org/showthread.php?t=2303644&page=2&p=13396229#post13396229")[COLOR=#000000] and try to continue get that stuff to build.[/COLOR]
I did, it got built but the tablet it's still not recognised. I concluded there's no option (with this specific model I own) other than kernel 4.4. 
> [COLOR=#000000](but keep in mind, you will have one other package to delete in your case)[/COLOR]
Which one? Could you clarify?
Thanks for all of your instructions anyway! It was very helpfull, very much appreciated!

---

### Post by Doug S on 2015-11-27
> **nikoszr said:**
> Which one? Could you clarify?The Ubuntu PPA kernel was 3 packages. The example I did was a kernel I compiled myself, and was only two packages. I did not use the Ubuntu PPA kernel as a remove example because I don't want to remove it. So for your case it should be these 3:```
ii  linux-headers-4.4.0-040400rc2             4.4.0-040400rc2.201511231054          all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-040400rc2-generic     4.4.0-040400rc2.201511231054          amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc2-generic       4.4.0-040400rc2.201511231054          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
```Edit: You need to remove the header packages in the correct order, or you will get some dependency error. I never bother to remember the correct order (generic first), but rather just go "oh, ya" and do it the other way around when I get the error.

---

### Post by zika on 2015-11-27
```
sudo apt-get purge linux-headers-4.4.0-040400rc2 linux-headers-4.4.0-040400rc2-generic linux-image-4.4.0-040400rc2-generic
```Order is completely irrelevant.
To clean all cruft You could use also```
dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
```Carefull: command I gave You to clean cruft could clean also other cruft. I do not know what is the state of Your install so, about second code all is on Your responsibility... ;)

---

### Post by nikoszr on 2015-11-27
> [COLOR=#000000]my list is a bit of a long mess at the moment):[/COLOR]
As I found out mine is also very long although I've never  manually installed any kernels others than 3.19 and 4.4.
 > [COLOR=#000000]You need to remove the header packages in the correct order[/COLOR]
So the correct order im my case would be (I paste form my terminal):
> ii  linux-image-4.4.0-040400rc2-generic                   4.4.0-040400rc2.201511231054                        i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-040400rc2-generic                 4.4.0-040400rc2.201511231054                        i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-040400rc2                         4.4.0-040400rc2.201511231054                        all          Header files related to Linux kernel version 4.4.0

Is that right?

---

### Post by zika on 2015-11-27
> **nikoszr said:**
> As I found out mine is also very long although I've never  manually installed any kernels others than 3.19 and 4.4.That does not change length of the list. That changes only suffix at start of each entry in list.
> **nikoszr said:**
> So the correct order im my case would be (I paste form my terminal):There is no &#8222;right&#8220; order, apt will sort that for You.
> **nikoszr said:**
> Is that right?Define &#8222;right&#8220; ... ;) Mainline kernels does not have all components of dependency and, more important, headers are not sine qua non for kernel image, contrary to popular belief.
It seems that command(s) I gave You were my futile effort... ;)

---

### Post by nikoszr on 2015-11-27
> [COLOR=#000000]There is no &#8222;right&#8220; order, apt will sort that for You.[/COLOR]
OK I understand that. But here:
> [COLOR=#000000]Define &#8222;right&#8220; ... [/COLOR]:wink:[COLOR=#000000] Mainline kernels does not have all components of dependency and, more important, headers are not sine qua non for kernel image, contrary to popular belief.[/COLOR]
[COLOR=#000000]It seems that command(s) I gave You were my futile effort... [/COLOR]:wink:
I don't quite get you! I'm not a native speaker and also I have a very low level of knowledge on computing. ;)

---

### Post by zika on 2015-11-27
> **nikoszr said:**
> I'm not a native speaker. ;)That makes (at least) two of us. No need to shout... ;)

---

### Post by Doug S on 2015-11-27
Order matters for the method I use. zika uses a different method, where I gather order doesn't matter.

It is not clear to me why you would have a long list of kernels, as I understood your installation to be fairly new.

---

### Post by zika on 2015-11-27
> **Doug S said:**
> Order matters for the method I use. zika uses a different method, where I gather order doesn't matter.
It is not clear to me why you would have a long list of kernels, as I understood your installation to be fairly new.Command given lists all available packages, not only installed ones, those that are installed are marked appropriately.
If different switch were to be used for dpkg different result would occur.. ;)```
:~$ dpkg -l|grep -v "sys"|grep linux-
ii  [COLOR=#CC0000]**linux-**[/COLOR]firmware                                        1.153                                                     all          Firmware for Linux kernel drivers
ii  [COLOR=#CC0000]**linux-**[/COLOR]firmware-nonfree                                1.16                                                      all          Non-free firmware for Linux kernel drivers
ii  [COLOR=#CC0000]**linux-**[/COLOR]headers-4.3.0-0                                 4.3.0-0.8                                                 all          Header files related to Linux kernel version 4.3.0
ii  [COLOR=#CC0000]**linux-**[/COLOR]headers-4.3.0-0-lowlatency                      4.3.0-0.8                                                 amd64        Linux kernel headers for version 4.3.0 on 64 bit x86 SMP
ii  [COLOR=#CC0000]**linux-**[/COLOR]headers-4.3.0-xanmod3                           2.151119                                                  amd64        Linux kernel headers for 4.3.0-xanmod3 on amd64
ii  [COLOR=#CC0000]**linux-**[/COLOR]headers-lowlatency                              4.3.0.0.0                                                 amd64        lowlatency Linux kernel headers
ii  [COLOR=#CC0000]**linux-**[/COLOR]image-4.3.0-0-lowlatency                        4.3.0-0.8                                                 amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  [COLOR=#CC0000]**linux-**[/COLOR]image-4.3.0-xanmod3                             2.151119                                                  amd64        Linux kernel, version 4.3.0-xanmod3
ii  [COLOR=#CC0000]**linux-**[/COLOR]image-lowlatency                                4.3.0.0.0                                                 amd64        lowlatency Linux kernel image
ii  [COLOR=#CC0000]**linux-**[/COLOR]libc-dev:amd64                                  4.3.0-0.8                                                 amd64        Linux Kernel Headers for development ii  [COLOR=#CC0000]**linux-**[/COLOR]lowlatency                    
```

---

### Post by nikoszr on 2015-11-27
> **Doug S said:**
> 

It is not clear to me why you would have a long list of kernels, as I understood your installation to be fairly new.
Well, neither is it clear to me but then I'm not an expert after all... I don't think it's a fairly new installation. Actually it's an upgrade from ubuntu12, 2 years ago(?) then some months ago my laptop broke down and I transfered all of its HD content on a desktop PC machine. Here is all of the stuff it returns from command line:

```
ii  linux-firmware                                        1.127.18                                               all          Firmware for Linux kernel driversii  linux-generic                                         3.13.0.68.74                                           i386         Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                               3.19.0.33.20                                           i386         Complete Generic Linux kernel and headers
ii  linux-generic-pae                                     3.13.0.68.74                                           i386         Transitional package.
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-40                               3.13.0-40.69                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                       3.13.0-40.69                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                               3.13.0-67.110                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                       3.13.0-67.110                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                       3.13.0-68.111                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-33                               3.19.0-33.38~14.04.1                                   all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-33-generic                       3.19.0-33.38~14.04.1                                   i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-040400rc2                         4.4.0-040400rc2.201511231054                           all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-040400rc2-generic                 4.4.0-040400rc2.201511231054                           i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.68.74                                           i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       3.19.0.33.20                                           i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                             3.13.0.68.74                                           i386         Transitional package
rc  linux-image-3.13.0-36-generic                         3.13.0-36.63                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                         3.13.0-67.110                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-68-generic                         3.13.0-68.111                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-33-generic                         3.19.0-33.38~14.04.1                                   i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-generic-pae                      3.2.0-29.46                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic-pae                      3.2.0-32.51                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic-pae                      3.2.0-33.52                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic-pae                      3.2.0-34.53                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic-pae                      3.2.0-35.55                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-36-generic-pae                      3.2.0-36.57                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic-pae                      3.2.0-37.58                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-40-generic-pae                      3.2.0-40.64                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-41-generic-pae                      3.2.0-41.66                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-43-generic-pae                      3.2.0-43.68                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-48-generic-pae                      3.2.0-48.74                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-49-generic-pae                      3.2.0-49.75                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-51-generic-pae                      3.2.0-51.77                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-52-generic-pae                      3.2.0-52.78                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-53-generic-pae                      3.2.0-53.81                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-54-generic-pae                      3.2.0-54.82                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-55-generic-pae                      3.2.0-55.85                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-56-generic-pae                      3.2.0-56.86                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-57-generic-pae                      3.2.0-57.87                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-58-generic-pae                      3.2.0-58.88                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-59-generic-pae                      3.2.0-59.90                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-60-generic-pae                      3.2.0-60.91                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-61-generic-pae                      3.2.0-61.93                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-65-generic-pae                      3.2.0-65.99                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-67-generic-pae                      3.2.0-67.101                                           i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-68-generic-pae                      3.2.0-68.102                                           i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-69-generic-pae                      3.2.0-69.103                                           i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-040400rc2-generic                   4.4.0-040400rc2.201511231054                           i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                   3.13.0-68.111                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-33-generic                   3.19.0-33.38~14.04.1                                   i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.68.74                                           i386         Generic Linux kernel image
ii  linux-image-generic-lts-vivid                         3.19.0.33.20                                           i386         Generic Linux kernel image
ii  linux-image-generic-pae                               3.13.0.68.74                                           i386         Transitional package
ii  linux-libc-dev:i386                                   3.13.0-68.111                                          i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                   all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                   i386         Bootloader for Linux/i386 using MS-DOS floppies

```  
Does this seem natural? :shock:

---

### Post by nikoszr on 2015-11-27
> **zika said:**
> No need to shout... ;)
I don't! :p
So, to sum up, it doesn't make any differance if I use either your method or Doug's if I want to uninstall is that right?

---

### Post by zika on 2015-11-28
> **nikoszr said:**
> Well, neither is it clear to me but then I'm not an expert after all... I don't think it's a fairly new installation. Actually it's an upgrade from ubuntu12, 2 years ago(?) then some months ago my laptop broke down and I transfered all of its HD content on a desktop PC machine. Here is all of the stuff it returns from command line:
```
ii  linux-firmware                                        1.127.18                                               all          Firmware for Linux kernel driversii  linux-generic                                         3.13.0.68.74                                           i386         Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                               3.19.0.33.20                                           i386         Complete Generic Linux kernel and headers
ii  linux-generic-pae                                     3.13.0.68.74                                           i386         Transitional package.
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-40                               3.13.0-40.69                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                       3.13.0-40.69                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                               3.13.0-67.110                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                       3.13.0-67.110                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                       3.13.0-68.111                                          i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-33                               3.19.0-33.38~14.04.1                                   all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-33-generic                       3.19.0-33.38~14.04.1                                   i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-040400rc2                         4.4.0-040400rc2.201511231054                           all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-040400rc2-generic                 4.4.0-040400rc2.201511231054                           i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.68.74                                           i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       3.19.0.33.20                                           i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                             3.13.0.68.74                                           i386         Transitional package
rc  linux-image-3.13.0-36-generic                         3.13.0-36.63                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                         3.13.0-67.110                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-68-generic                         3.13.0-68.111                                          i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-33-generic                         3.19.0-33.38~14.04.1                                   i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-generic-pae                      3.2.0-29.46                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic-pae                      3.2.0-32.51                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic-pae                      3.2.0-33.52                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic-pae                      3.2.0-34.53                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic-pae                      3.2.0-35.55                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-36-generic-pae                      3.2.0-36.57                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic-pae                      3.2.0-37.58                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-40-generic-pae                      3.2.0-40.64                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-41-generic-pae                      3.2.0-41.66                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-43-generic-pae                      3.2.0-43.68                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-48-generic-pae                      3.2.0-48.74                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-49-generic-pae                      3.2.0-49.75                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-51-generic-pae                      3.2.0-51.77                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-52-generic-pae                      3.2.0-52.78                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-53-generic-pae                      3.2.0-53.81                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-54-generic-pae                      3.2.0-54.82                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-55-generic-pae                      3.2.0-55.85                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-56-generic-pae                      3.2.0-56.86                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-57-generic-pae                      3.2.0-57.87                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-58-generic-pae                      3.2.0-58.88                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-59-generic-pae                      3.2.0-59.90                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-60-generic-pae                      3.2.0-60.91                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-61-generic-pae                      3.2.0-61.93                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-65-generic-pae                      3.2.0-65.99                                            i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-67-generic-pae                      3.2.0-67.101                                           i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-68-generic-pae                      3.2.0-68.102                                           i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-69-generic-pae                      3.2.0-69.103                                           i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-040400rc2-generic                   4.4.0-040400rc2.201511231054                           i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                   3.13.0-68.111                                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-33-generic                   3.19.0-33.38~14.04.1                                   i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.68.74                                           i386         Generic Linux kernel image
ii  linux-image-generic-lts-vivid                         3.19.0.33.20                                           i386         Generic Linux kernel image
ii  linux-image-generic-pae                               3.13.0.68.74                                           i386         Transitional package
ii  linux-libc-dev:i386                                   3.13.0-68.111                                          i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                   all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                   i386         Bootloader for Linux/i386 using MS-DOS floppies

```  
Does this seem natural? :shock:[IMG]http://cdn5.howtogeek.com/wp-content/uploads/gg/up/sshot508026f7ab35e.jpg[/IMG]
There are (easy) ways to clean that... ;)
> **nikoszr said:**
> I don't! :pYou do... ;)

---

### Post by tokyobadger on 2015-11-28
well finally got round to trying 4.4-rc2 - no dice - well some dice

boots into GUI, enter password, but no mouse

[First attempt with these files]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2+cod1-wily/")
[Second attempt with alternative headers]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2-wily/")
[Third attempt with alternative alternative headers]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc2-wily-keep/")

With each the result was keyboard ok, mouse dead as a dead thing (yep checked the batteries); it's a Logitech S510 USB wireless mouse + KB set (and ancient I know), I wouldn't consider it esoteric; never had problems with rc kernels before - maybe everyone develops on laptops these days and I'm a dinosaur?

So long to short - boots fine, Unity (16.04) comes up fine, login fine, mouse no-go, KB ok (terminal and dash will come up with the usual key combos) and reboot.

Fully aware that a fix is unlikely here and a bug report would be better but just interested to know if anyone else experienced something similar.

**Edit** Forgot that I wanted to comment on the cruft image from Zika - dust bunnies move over, that looks like a dust sauropod (just to milk the dinosaur theme a little more)

---

### Post by nikoszr on 2015-11-28
> **zika said:**
> 
There are (easy) ways to clean that... ;)

lol. Will you be doing me the kindness and mention them?

---

### Post by nikoszr on 2015-11-28
> **tokyobadger said:**
> 
Fully aware that a fix is unlikely here and a bug report would be better but just interested to know if anyone else experienced something similar.

I did. I think the whole thing has to do with graphic cards incompetence with  4.4. I tried to update the nvidia drivers but didn't succed.

---

### Post by zika on 2015-11-28
> **nikoszr said:**
> lol. Will you be doing me the kindness and mention them?1.```
sudo apt-get update
sudo apt-get autoremove
```
2. let us see if 1. does the job and proceed from there...
There are numerous threads about that, I do not want to go as much off-topic here...
Be carefull, not only kernels could be offered for deletion...
For cleaning cruft I gave hint above, already.

---

### Post by nikoszr on 2015-11-28
> **zika said:**
> let us see if 1. does the job and proceed from there...

It doesn't. OK it's off topic I understand. Thanks anyway! :)

---

### Post by Doug S on 2015-11-28
> **nikoszr said:**
> It doesn't. OK it's off topic I understand. Thanks anyway! :)zika's suggestion should have worked for you, so that is odd. However note that autoremove does not purge the config files, so the kernel image still would appear as "rc". This is why I never use autoremove, as I prefer to keep my dpkg list clean via purging the kernel image rather than just removing it.

As mentioned earlier in this thread, people having issues with kernel 4.4-rc2 should try again later in the cycle. -rc2 is still early in the cycle and it is still relatively unstable. The improvement just to -rc3 should be significant. I found [a very minor issue]("http://www.spinics.net/lists/kernel/msg2130459.html"), that will be fixed in, the guy thought, -rc3.

---

### Post by zika on 2015-11-28
> **Doug S said:**
> zika's suggestion should have worked for you, so that is odd.That reveals some possible issues that could be addressed in a separate thread. First I (again) advise to look into threads that already dealt with kernel removal(s). We are way off-teh-topic here since we are talking about 14.04.1 etc.
> **Doug S said:**
>  However note that autoremove does not purge the config files, so the kernel image still would appear as "rc". This is why I never use autoremove, as I prefer to keep my dpkg list clean via purging the kernel image rather than just removing it.I was just looking for simplest solution that is shortest to explain. Afte that a cleancruft one-liner that I gave above could remove all residues as I pointed out above. Be carefull, it will remove more and it will not ask You for permission. Writing that I think about {gtk,deb}orphan package that could be better choice for novice(s).
> **Doug S said:**
> As mentioned earlier in this thread, people having issues with kernel 4.4-rc2 should try again later in the cycle. -rc2 is still early in the cycle and it is still relatively unstable. The improvement just to -rc3 should be significant. I found [a very minor issue]("http://www.spinics.net/lists/kernel/msg2130459.html"), that will be fixed in, the guy thought, -rc3.4.4 that we helped our friend to install (from mainline, not 4.4 in source) is still in a crippled state (just in area that he is most interested in) due to several round a robin dependencies of drivers... That is why it did not fullfill his expectations as it did not follow its code to the last dot. Hence *cod* and *keep* nicknames... ;)

---

### Post by nikoszr on 2015-11-28
> **Doug S said:**
> The improvement just to -rc3 should be significant. 
Is there any estimation as to approximately when the -rc3 should be expected?

---

### Post by nikoszr on 2015-11-28
> **zika said:**
>  Writing that I think about {gtk,deb}orphan package that could be better choice for novice(s).

 Even then I wouldn't be sure as to what to remove or not, so I think I wont take such risks that may ruin things in my system... But thanks a lot for your advice and support. Very much appreciated. ;)

---

### Post by Doug S on 2015-11-28
> **nikoszr said:**
> Is there any estimation as to approximately when the -rc3 should be expected?Typically there is an rc once per week, and typically it is released about midnight Sunday night UTC, but it can vary +- a day. After rc7, typically the final release is done, but there have been rc8's. There is always a 2 week gap between the final release and rc1 of the next cycle.

Due to the compile issues with this 4.4 rc series, there has been a delay of a day or more before the ubuntu PPA has a usable build, and actually rc1 never did have a usable build. This is odd because the issue was known and a patch submitted before rc1 even came out, so one would have expected by rc2 for things to be fine. Lets see what happens tomorrow night.

---

### Post by zika on 2015-11-28
> **nikoszr said:**
> Even then I wouldn't be sure as to what to remove or not, so I think I wont take such risks that may ruin things in my system... But thanks a lot for your advice and support. Very much appreciated. ;)Apps that I suggested are not known to remove vital parts etc. But, yes, I do appreciate Your reluctance.

---

### Post by nikoszr on 2015-11-28
> **Doug S said:**
> Typically there is an rc once per week, and typically it is released about midnight Sunday night UTC, but it can vary +- a day. After rc7, typically the final release is done, but there have been rc8's. There is always a 2 week gap between the final release and rc1 of the next cycle.

Due to the compile issues with this 4.4 rc series, there has been a delay of a day or more before the ubuntu PPA has a usable build, and actually rc1 never did have a usable build. This is odd because the issue was known and a patch submitted before rc1 even came out, so one would have expected by rc2 for things to be fine. Lets see what happens tomorrow night.
Oh I see! Thank you so much for the information! I would love to try the -rc3 version, it may be luckier on my system. ;)

---

### Post by nikoszr on 2015-11-28
> **zika said:**
> Apps that I suggested are not known to remove vital parts etc. But, yes, I do appreciate Your reluctance.
Perhaps I'll give it a try and just give up in case I don't understand what's going on there... ;)
(Why is always "You" and "Yours" in capital "Y"?)

---

### Post by tokyobadger on 2015-11-28
[quote="nikoszr"][I  did. I think the whole thing has to do with graphic cards incompetence  with  4.4. I tried to update the nvidia drivers but didn't succed.](http://ubuntuforums.org/showthread.php?t=2303120&p=13398119#post13398119)[/quote]
I'm not pointing at the graphics card or drivers (nvidia GTX680 + nvidia-358.16) because the GUI came up fine, I could login, I could call up the dash, I could select applications and use the terminal; but I could not use my mouse. The KB/mouse combo works fine under 4.2.0-19.

Looking in my Downloads folder I see various versions of 4.0, 4.1, and 4.2 (missed 4.3); as I recall there were some issues with nvidia drivers under 4.1.x, but other than that, every time the GUI has come up the mouse has worked fine. 

This is what dmesg reports when it works eg under 4.2.0-19

```
[    1.851009] usb 5-2: New USB device found, idVendor=046d, idProduct=c517
[    1.851013] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.851015] usb 5-2: Product: USB Receiver
[    1.851017] usb 5-2: Manufacturer: Logitech
[    1.857370] hidraw: raw HID events driver (C) Jiri Kosina
[    1.901082] usbcore: registered new interface driver usbhid
[    1.901084] usbhid: USB HID core driver
[    1.903983] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/0003:046D:C517.0001/input/input5
[    1.958281] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.2-2/input0
[    1.958291] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    1.958675] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/0003:046D:C517.0002/input/input6
[    2.014541] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-2/input1
```

Under 4.4-rc2 I don't have
```
[    1.958675] input: Logitech USB Receiver as  /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/0003:046D:C517.0002/input/input6
[    2.014541] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB  HID v1.10 Mouse [Logitech USB Receiver] on  usb-0000:00:1a.2-2/input1
```
Seems something is amiss with USBHID

---

### Post by mrfelker on 2015-11-28
Kernel 4.3 works fine (and is fast) on Ubuntu 16.04.  Kernel 4.4 rc2 panics.  Can anybody confirm?

---

### Post by tokyobadger on 2015-11-29
[4.4.x thread is here](http://ubuntuforums.org/showthread.php?t=2303120)
Works for some not for others including me. I'm not getting a kernel panic - something wrong with USBHID in 4.4-rc2 I think

---

### Post by Smask on 2015-11-29
> **tokyobadger said:**
> something wrong with USBHID in 4.4-rc2 I think

Mouse input is stuck on the last item you clicked on until you restart your mouse and then it's good for a couple of clicks? That's what I'm seeing on 4.2.0-19 with proposed enabled. Since it sticks to the last item I clicked on, I would say that it's in xinput or something.

---

### Post by zika on 2015-11-30
Mainline is up to speed.
Update&#8321;: Sadly, 999 panics...
Update&#8322;: It seems that I've found a way to {pre,circum}vent panic(s)...

---

### Post by nikoszr on 2015-11-30
> **zika said:**
> 
Update&#8321;: Sadly, 999 panics...
What does this mean?

---

### Post by Doug S on 2015-11-30
> **nikoszr said:**
> What does [999] mean?It it just a reference to the daily build, which is always called 999. See [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/").

---

### Post by nikoszr on 2015-11-30
> **Doug S said:**
> It it just a reference to the daily build, which is always called 999. See [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/").
But I still don't see what's a "daily build" and a "panic" ;)
By the way what about the -rc3? Is it released? Can I install?

---

### Post by Doug S on 2015-11-30
So now that that the [Ubuntu PPA for rc3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/") is O.K., I am attempting to use the Ubuntu kernel config file for my own compile, but it isn't working. It seems I need a newer version of the compiler (I compile on a 14.04.3 server), as my system is complaining about the STACKPROTECTOR stuff. In the end for my compile to complete, the differences are:
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]diff .config-4.4.0-040400rc3-generic .config[/COLOR]
3c3
< # Linux/x86_64 4.4.0-040400rc3-generic Kernel Configuration
---
> # Linux/x86 4.4.0-rc3 Kernel Configuration
285,286c285,286
< CONFIG_CC_STACKPROTECTOR=y
< # CONFIG_CC_STACKPROTECTOR_NONE is not set
---
> # CONFIG_CC_STACKPROTECTOR is not set
> CONFIG_CC_STACKPROTECTOR_NONE=y
288c288
< CONFIG_CC_STACKPROTECTOR_STRONG=y
---
> # CONFIG_CC_STACKPROTECTOR_STRONG is not set
7841,7845c7841
< CONFIG_DEBUG_INFO=y
< # CONFIG_DEBUG_INFO_REDUCED is not set
< # CONFIG_DEBUG_INFO_SPLIT is not set
< CONFIG_DEBUG_INFO_DWARF4=y
< CONFIG_GDB_SCRIPTS=y
---
> # CONFIG_DEBUG_INFO is not set

```The other item to note, is that while the original circular dependency issue is finally fixed, it was not fixed via that patch I referred to and used to get rc1 to compile. It was fixed just by disabling the LUSTRE stuff, which is the same as I did to get rc2 to compile (as mentioned by some other posters). i.e. ```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]diff .config .config-4.4-rc1 | grep LUSTRE[/COLOR]
< # CONFIG_LUSTRE_FS is not set
> CONFIG_LUSTRE_FS=m
> CONFIG_LUSTRE_OBD_MAX_IOCTL_BUFFER=8192
> # CONFIG_LUSTRE_DEBUG_EXPENSIVE_CHECK is not set
> CONFIG_LUSTRE_LLITE_LLOOP=m

```

---

### Post by Doug S on 2015-11-30
> **nikoszr said:**
> But I still don't see what's a "daily build" and a "panic"
By the way what about the -rc3? Is it released? Can I install?daily build: I do not know how to describe it any better. It is the daily build directory. Just watch it yourself over the next few days.
panic: I assume it means zika gets a kernel panic when he tries to run it.
-rc3: Yes, it is [there]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/"). and yes you can try it. Next week just watch [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") for -rc4.

---

### Post by nikoszr on 2015-11-30
> **Doug S said:**
> daily build: I do not know how to describe it any better. It is the daily build directory. Just watch it yourself over the next few days.
panic: I assume it means zika gets a kernel panic when he tries to run it.
-rc3: Yes, it is [there]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/"). and yes you can try it. Next week just watch [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") for -rc4.
Oh OK, thank you! But can you please give me the commands I need to execute? I can't make sense on how to do it in the index link that you gave me! &#913;ll those are incomprehensible thnigs to me in there!

---

### Post by Doug S on 2015-11-30
> **nikoszr said:**
> But can you please give me the commands I need to execute? I can't make sense on how to do it in the index link that you gave me! &#913;ll those are incomprehensible thnigs to me in there!No.
Why not? Because, and while this may seem a little harsh, it is time for you start figuring things out for yourself. Please review all the posts in this thread that are related to you. All the commands you need have been given herein, you just need to figure out for yourself how to change them from rc2 to rc3 (O.K., without the "+cod1" part this time, that was special and unusual).

---

### Post by bapoumba on 2015-11-30
One thread merged in.

---

### Post by nikoszr on 2015-12-01
> **Doug S said:**
> No.
Why not? Because, and while this may seem a little harsh, it is time for you start figuring things out for yourself. Please review all the posts in this thread that are related to you. All the commands you need have been given herein, you just need to figure out for yourself how to change them from rc2 to rc3 (O.K., without the "+cod1" part this time, that was special and unusual).
Sorry, I didn't mean to bother you or anybody else in here. I know my ignorence might be somehow annoying, and thanks for all of your help and support so far. 
I installed the -rc3 but I still have issues concernig competence with nvidia. 
During isntallation I got at the end the following error:```
 Installing[COLOR=#3C3B37][FONT=Monaco] linux-headers-4.4.0-040400rc3-generic (4.4.0-040400rc3.201511300321) ...[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Examining /etc/kernel/header_postinst.d.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-040400rc3-generic /boot/vmlinuz-4.4.0-040400rc3-generic[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-304.0.crash'[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Error! Bad return status for module build on kernel: 4.4.0-040400rc3-generic (i686)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Consult /var/lib/dkms/nvidia-304/304.131/build/make.log for more information.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]
[/FONT][/COLOR]

``` 

So the make.log is here: 
```
[COLOR=#3C3B37][FONT=Monaco]DKMS make.log for nvidia-304-304.131 for kernel 4.4.0-040400rc3-generic (i686)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]&#916;&#949;&#965; 30 &#925;&#959;&#941; 2015 09:23:35 &#956;&#956; EET[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]NVIDIA: calling KBUILD...[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Makefile:660: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]test -e include/generated/autoconf.h -a -e include/config/auto.conf || (      \[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   echo >&2;                     \[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   echo >&2 "  ERROR: Kernel configuration is invalid.";      \[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";   \[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   echo >&2 ;                     \[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   /bin/false)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]mkdir -p /var/lib/dkms/nvidia-304/304.131/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia-304/304.131/build/.tmp_versions/*[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]make -f ./scripts/Makefile.build obj=/var/lib/dkms/nvidia-304/304.131/build[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]  cc -Wp,-MD,/var/lib/dkms/nvidia-304/304.131/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.8/include -I./arch/x86/include -Iarch/x86/include/generated/uapi -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -std=gnu89 -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -m32 -msoft-float -mregparm=3 -freg-struct-return -fno-pic -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_SSSE3=1 -DCONFIG_AS_CRC32=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -fno-delete-null-pointer-checks -O2 --param=allow-store-data-races=0 -Wframe-larger-than=1024 -fstack-protector-strong -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -DCC_HAVE_ASM_GOTO -I/var/lib/dkms/nvidia-304/304.131/build -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"304.131\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /var/lib/dkms/nvidia-304/304.131/build/.tmp_nv.o /var/lib/dkms/nvidia-304/304.131/build/nv.c[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]cc: error: unrecognized command line option ‘-fstack-protector-strong’[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]make[3]: *** [/var/lib/dkms/nvidia-304/304.131/build/nv.o] Error 1[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]make[2]: *** [_module_/var/lib/dkms/nvidia-304/304.131/build] Error 2[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]NVIDIA: left KBUILD.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]nvidia.ko failed to build![/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]make[1]: *** [module] Error 1[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]make: *** [module] Error 2[/FONT][/COLOR]
```
If someone knows what those errors mean or if and how they could be possibly fixed, please let me know.

---

### Post by Doug S on 2015-12-01
> **nikoszr said:**
> 
If someone knows what those errors mean or if and how they could be possibly fixed, please let me know.Covered in my comment #55. Both you and I are using a version of the compiler that doesn't include support for STACKPROTECTOR_STRONG. From the build logs for the Ubuntu PPA compile, I gather that wily (15.10) version of gcc has the support, but that is as far as I got. I am using a 14.04.3 Ubuntu server to compile kernel, and had to NOT use  STACKPROTECTOR_STRONG to get the rc3 kernel to compile when I used the otherwise Ubuntu kernel configuration file. I have not figured out what I am going to do moving forward: Either try to compile using my 16.04 server VM or upgrade my main test server from 14.04.3 to 16.04 now instead of later.

---

### Post by Doug S on 2015-12-02
> **Doug S said:**
> The improvement just to -rc3 should be significant. I found [a very minor issue]("http://www.spinics.net/lists/kernel/msg2130459.html"), that will be fixed in, the guy thought, -rc3.It is not fixed. I'll check again at -rc4.

---

### Post by nikoszr on 2015-12-02
> **Doug S said:**
> Covered in my comment #55. Both you and I are using a version of the compiler that doesn't include support for STACKPROTECTOR_STRONG.
But are you able to log in in the system? In my case I'm not. The system won't load.

---

### Post by Doug S on 2015-12-02
> **nikoszr said:**
> But are you able to log in in the system? In my case I'm not. The system won't load.Yes, I am able to log in, and everything seems more or less O.K. Note my system is an Ubuntu server system, and I have no GUI.

EDIT: While the "minor issue" I referenced in a previous post, is just that in my case, I can envision cases, or other manifestations, where it could be a serious issue.

---

### Post by mc4man on 2015-12-02
> **Doug S said:**
> Covered in my comment #55. Both you and I are using a version of the compiler that doesn't include support for STACKPROTECTOR_STRONG. From the build logs for the Ubuntu PPA compile, I gather that wily (15.10) version of gcc has the support, but that is as far as I got. I am using a 14.04.3 Ubuntu server to compile kernel, and had to NOT use  STACKPROTECTOR_STRONG to get the rc3 kernel to compile when I used the otherwise Ubuntu kernel configuration file. I have not figured out what I am going to do moving forward: Either try to compile using my 16.04 server VM or upgrade my main test server from 14.04.3 to 16.04 now instead of later.
Is there some reason in terms of a kernel build you can't just install & specify another gcc to use? 
( the ubuntu-toolchain-r ppa has both 4.9.3 & 5.2.1 for 14.04

---

### Post by QDR06VV9 on 2015-12-03
I had problems building this last nite, But re-downloaded today and all is good.
Nvidia also installs fine..
```
$ inxi -b
System:    Host: me-Aspire-M3300 Kernel: 4.4.0-040400rc3-lowlatency x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 2500.5GB (5.8% used)
Info:      Processes: 255 Uptime: 5 min Memory: 897.7/5966.9MB
           Client: Shell (bash) inxi: 2.2.28 



```
Regards

---

### Post by Doug S on 2015-12-03
> **mc4man said:**
> Is there some reason in terms of a kernel build you can't just install & specify another gcc to use? 
( the ubuntu-toolchain-r ppa has both 4.9.3 & 5.2.1 for 14.04Yes, that is an option. Thanks for suggesting it.

---

### Post by MikeMecanic on 2015-12-03
Loads perfectly for me:

```
xenial3@hp:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
4.4.0-040400rc2-generic

```

According to command lines in post # 13

---

### Post by Doug S on 2015-12-04
> **MikeMecanic said:**
> Loads perfectly for me:

```
xenial3@hp:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
[COLOR="#FF0000"]4.4.0-040400rc2-generic[/COLOR]

```

According to command lines in post # 13We are on rc3 now.

---

### Post by MikeMecanic on 2015-12-04
4.4 rc2 generic: loads, runs and restarts properly
4.4 rc2 Upstart: loads, runs properly but it restarts pretty slowly
Must pass by Ubuntu Advanced now to load 4.3.1 because it loads default in 4.4 rc2 now.  
.
@Doug S:  Thanks for the update

**Try to install the rc3 version (command lines shown below) but unfortunately it ends in panic mode.  Remove it using Synaptic.**

```
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-headers-4.4.0-040400rc3_4.4.0-040400rc3.201511300321_all.deb
```

```
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-headers-4.4.0-040400rc3-generic_4.4.0-040400rc3.201511300321_amd64.deb
```

```
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-image-4.4.0-040400rc3-generic_4.4.0-040400rc3.201511300321_amd64.deb
```

```
$ sudo dpkg -i linux-headers-4.4*.deb linux-image-4.4*.deb
```

```
$ sudo reboot
```

Edit: Made the correction for the third command line / **The solution is in post # 72 / Was not able to build or mount rc3 with the command lines above**

P.S.:  Dual boot with 10586.17 (Nov 6th build and first release [Pro version only]; 2.91Gb ISO File / (Uxx 1.2Gb ISO file, Dec 2nd build _alongside option_).  Its quiet and stable on both sides of my HDD.  [B]Stability starts in the installer and ends on post-installation.
[/B]
All the best,

Mike

---

### Post by Doug S on 2015-12-04
> **MikeMecanic said:**
> ```
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-image-4.4.0-040400rc3-generic_4.4.0-040400rc3.201511300321[COLOR="#FF0000"]_i386[/COLOR].deb
```I think you wanted [COLOR="#FF0000"]amd64[/COLOR] there.

---

### Post by MikeMecanic on 2015-12-04
> **Doug S said:**
> I think you wanted [COLOR=#FF0000]amd64[/COLOR] there.

Thanks ounce again!  Will give it a second try later this afternoon.

---

### Post by MikeMecanic on 2015-12-04
I did the modification related to amd 64 command line. Panic mode again

The last line is this one:
1.570702 --- [end Kernel panic] - Not syncing:  No working init found. Try passing init = option to kernel.See / in / Documentation/ init.txt for guidance.  Took a picture... Try it twice in generic mode,Upstart and recovery mode.


When I remove it in Synaptic (see screeshot), it looks like the 32 bit version: i386.  If I try to remove rc2, I don't get the i386.  Again, I modified the command line which is an URL.  What can I do?  Where is that init.txt file?  Is there another way to reach rc3?  Finally, rc3 becomes default, so I must remove it each time.

Thanks in advance,

 ```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-image-4.4.0-040400rc3-generic_4.4.0-040400rc3.201511300321_amd64.deb
```

---

### Post by MikeMecanic on 2015-12-04
Friday December 4th 2015

Here's how to upgrade to Kernel 4.4 Release Candidate 3 (AMD64)

Command lines:

1.
```
cd /tmp
```
2.
```
wget \
```
3.
```
kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-headers-4.4.0-040400rc3_4.4.0-040400rc3.201511300321_all.deb \
```
4.
```
kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-headers-4.4.0-040400rc3-generic_4.4.0-040400rc3.201511300321_amd64.deb \
```
5.
```
kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc3-wily/linux-image-4.4.0-040400rc3-generic_4.4.0-040400rc3.201511300321_amd64.deb
```
6.
```
sudo dpkg -i linux-headers-4.4*.deb linux-image-4.4*.deb
```
7.
```
sudo reboot
```

```
xenial3@hp:~$ uname -a
Linux hp 4.4.0-040400rc3-generic #201511300321 SMP Mon Nov 30 03:23:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

All the best,

[http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/](http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/)

---

### Post by nikoszr on 2015-12-05
For me it still won't work, although I made an installation of 16.04 on a separate drive on my pc and this time the kernel installed without errors, the system won't boot, it's always either dark screens or "panics" etc...
(By the way, 16.04 appears to be running very nicely with kernel 4.3 on my computer)

---

### Post by MikeMecanic on 2015-12-05
Proposed demonstrates significant activity every day (many files).  Kernel is at 4.3.0.2 with today's updates.  No bug, stable.  Run 4.4 rc3 default.  


Nautilus is not showing files properly. The root is not shown the way it should be (Computer).  Unless its the new shape of Nautilus or it comes from the option alongside in the installer(dual boot).  But I think it was modified by the Kernel 4.3 upgrade? See screenshot.


Opera 35 Developer is set Default: New shape, new settings, new logo (silver instead of red), same stability.

---

### Post by mc4man on 2015-12-06
Ot: > **MikeMecanic said:**
> 


Nautilus is not showing files properly. The root is not shown the way it should be (Computer).  Unless its the new shape of Nautilus or it comes from the option alongside in the installer(dual boot).  But I think it was modified by the Kernel 4.3 upgrade? See screenshot.
.
nautilus 3.18 has changed a bit over 3.14, some good, some bad, a lot subjective. Definitely slimed down further.
(- less options inc. for free

As far as the reduced menus more will return at some point for a user nautilus window, for root window nothing specific will be fixed/changed
(- gnome doesn't support root nautilus, ubuntu doesn't care

The overall look is hybrid, nautilus, like gedit, is using csd/GtkHeaderBar so it will look different than most other app windows. It'll change a little though I'd expect to remain rather poor for many. 

(- if desiring to alter a root nautilus's preferences then run  gsettings or dconf with sudo or use - 
```
sudo -H dconf-editor
```
The 'default' "root" nautilus window here is shown in scr.1 & 2, *some* of the  issues are - 
1. mounted volumes are shown twice
2. the network section never loads (here
3. icons at the default of 'normal' are too big, actually small is still large to me. Nautilus now has just 3 icon sizes, small, normal, large. 
 - small is a little bit larger than previous 100% setting
4 . windows os volume loaded at login, it shouldn't 

A normal 'new' nautilus in scr. 3, has several issues & an inconsistent look to itself, (ex., context windows) & the ambiance theme

---

### Post by tokyobadger on 2015-12-06
@Smask: apologies for the delayed reply. I have no issues with 4.2.0-19.

When I boot 4.4-rc2 and 4.4-rc3 the GUI comes up, I can use my keyboard to login, I can use my keyboard shortcuts to pull up the dash or launch the terminal. My mouse however is not working because the wireless receiver is not being "found" in the boot process.

Re: current Nautilus - I'm also not a fan of the changes I've seen so far, but I think the topic deserves a separate thread

---

### Post by MikeMecanic on 2015-12-06
> **mc4man said:**
> Ot: 
nautilus 3.18 has changed a bit over 3.14, some good, some bad, a lot subjective. Definitely slimed down further.
(- less options inc. for free

As far as the reduced menus more will return at some point for a user nautilus window, for root window nothing specific will be fixed/changed
(- gnome doesn't support root nautilus, ubuntu doesn't care

The overall look is hybrid, nautilus, like gedit, is using csd/GtkHeaderBar so it will look different than most other app windows. It'll change a little though I'd expect to remain rather poor for many. 

(- if desiring to alter a root nautilus's preferences then run  gsettings or dconf with sudo or use - 
```
sudo -H dconf-editor
```
The 'default' "root" nautilus window here is shown in scr.1 & 2, *some* of the  issues are - 
1. mounted volumes are shown twice
2. the network section never loads (here
3. icons at the default of 'normal' are too big, actually small is still large to me. Nautilus now has just 3 icon sizes, small, normal, large. 
 - small is a little bit larger than previous 100% setting
4 . windows os volume loaded at login, it shouldn't 

A normal 'new' nautilus in scr. 3, has several issues & an inconsistent look to itself, (ex., context windows) & the ambiance theme

**Special thanks for the reply.**  
I'm definitely having an issue with Nautilus:  Not able to import profile in GUFW, the command line of my previous installation doesn't work; not able to reach it.  Enabling the search engine in Nautilus does not shows the path?
Plus Nautilus became fully unstable this morning.  Turn OFF Proposed:  I don't need that since Kernel 4.4. rc3 runs default.   Will start working with this post in few minutes.  Got another minor issue, in lock screen mode, the monitor goes into black even if it is set the proper way.   Touching any key wake-up the monitor into lock screen mode ounce again.   

Take good note that Xenial, Kernel 4.3 and  4.4 are under constructions and some hazardous issues may come out.

Regards,

---

### Post by MikeMecanic on 2015-12-06
@mac4man
The 'default' "root" nautilus window here is shown in scr.1 & 2, *some* of the  issues are - 
1. mounted volumes are shown twice
2. the network section never loads (here
3. icons at the default of 'normal' are too big, actually small is still large to me. Nautilus now has just 3 icon sizes, small, normal, large. 
 - small is a little bit larger than previous 100% setting
4 . windows os volume loaded at login, it shouldn't 

A normal 'new' nautilus in scr. 3, has several issues & an inconsistent look to itself, (ex., context windows) & the ambiance theme
                                                                                                                      *****
1.  Not my case
2.  If I click on it, I get a weird reaction, so I don't click on it any more.  Good to know that it never loads
3.  It is small enough  +  there is is another way to reduce them in post #17   [http://ubuntuforums.org/showthread.php?t=2305058&page=2](http://ubuntuforums.org/showthread.php?t=2305058&page=2)
4.  I'm not sure I'm getting that one but I don't have that issue either
```
xenial3@hp:~$ sudo -H dconf-editor
[sudo] password for xenial3: 
sudo: dconf-editor: command not found

```

6.  Finally fixed the GUFW issue and by I don't know what reason, things are back to normal.

```
sudo chmod 600 /home/xenial3/Desktop/firewall17.profile

```
7. One big question remain, should I keep Proposed enable???  Does by any meaning, Kernel 4.4 is related to Proposed patch's.

---

### Post by ridobe on 2015-12-06
> **Doug S said:**
> Kernel 4.4 RC1 does not build for me. It seems the [Ubunutu PPA version]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc1-wily/") has the same issue. My error message:```
  DEPMOD  4.4.0-rc1-stock
depmod: WARNING: found 2 modules in dependency cycles!
depmod: WARNING: /home/doug/temp-k-git/linux/./debian/tmp/lib/modules/4.4.0-rc1-stock/kernel/drivers/staging/lustre/lnet/lnet/lnet.ko in dependency cycle!
depmod: WARNING: /home/doug/temp-k-git/linux/./debian/tmp/lib/modules/4.4.0-rc1-stock/kernel/drivers/staging/lustre/lustre/libcfs/libcfs.ko in dependency cycle!
./scripts/depmod.sh: line 57: 18619 Killed                  "$DEPMOD" "$@" "$KERNELRELEASE" $SYMBOL_PREFIX
make[3]: *** [_modinst_post] Error 137
make[2]: *** [bindeb-pkg] Error 2
make[1]: *** [bindeb-pkg] Error 2
make: *** [__build_one_by_one] Error 2
```PPA error message (copied from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc1-wily/BUILD.LOG.amd64")):```
  DEPMOD  4.4.0-040400rc1-generic
depmod: ERROR: Found 2 modules in dependency cycles!
depmod: ERROR: Cycle detected: lnet -> libcfs -> lnet
/home/kernel/COD/linux/Makefile:1139: recipe for target '_modinst_post' failed
make[2]: *** [_modinst_post] Error 1
make[2]: Leaving directory '/home/kernel/COD/linux/debian/build/build-generic'
Makefile:146: recipe for target 'sub-make' failed
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory '/home/kernel/COD/linux'
debian/rules.d/2-binary-arch.mk:93: recipe for target 'install-generic' failed
make: *** [install-generic] Error 2
```Has anyone figured out how to proceed?

EDIT 1: [https://lkml.org/lkml/2015/11/2/388](https://lkml.org/lkml/2015/11/2/388)
EDIT 2: [https://lkml.org/lkml/2015/11/6/987](https://lkml.org/lkml/2015/11/6/987)
EDIT 3: Patch applied, building now.
EDIT 4: Kernel compile completed. Running now. Some errors and warnings during boot.

It appears that this has been fixed with the original patch being committed.  See [here]("https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=d035e336287b5ea7e88dd9714e31dad5907c6aaf").  I will compile shortly to test.

edit: confirmed.  This is fixed in rc4.

---

### Post by Doug S on 2015-12-06
> **ridobe said:**
> It appears that this has been fixed with the original patch being committed.  See [here]("https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=d035e336287b5ea7e88dd9714e31dad5907c6aaf").  I will compile shortly to test.

edit: confirmed.  This is fixed in rc4.Thanks. Yes, I confirm also.
Additionally the patch for the minor issue I referred to a couple of times, that was thought would be included in -rc3 is included  in -rc4 (and I just tested to confirm).

---

### Post by QDR06VV9 on 2015-12-07
This one seem's a little more responsive..but I did have to recompile Pulseaudio.(that can happen sometimes)

```
System:    Host: me-Aspire-M3300 Kernel: 4.4.0-040400rc4-lowlatency x86_64 (64 bit)  
                             Desktop: MATE 1.12.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 1400/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 2500.5GB (5.8% used)
Info:      Processes: 219 Uptime: 5:15 Memory: 865.6/5966.9MB
           Client: Shell (bash) inxi: 2.2.28 



```

---

### Post by MikeMecanic on 2015-12-07
[LEFT]The upgrade when fine but it ends in a black screen.  In an issue like this one, I exit and recover or wake-up the monitor by simply pressing the sleep mode key (HP wireless keyboard).  The main switch turns yellow.  This time I tried CRTL+ALT+L to see if the monitor would wake-up, It didn't.  But, by pressing the sleep mode key after, it ended in lock screen.  Enter the password and it came back to normal.
[B]
Is there a way to create a shortcut key so that anyone can easily exit a black screen???[/B]  Unless I don't see it, it is not listed in the shortcut list: All Settings/Keyboard/Shortcuts

Unity minor issues remain.  Lock screen mode ends rapidly in a blackscreen (from rc3 or rc2).  Pressing any key wake-up the monitor. Office icons remain too large.  Plus, for a 7 pages document, it always open 13 pages: 6 of them are empty (since Kernel 4.3).  To ended positively, the corrector in Office works fine now.
[B]
P.S.: The sleep mode key works 10 times out of 10[/B]
All the best,

Edit:  The file is a .rtf extension

[/LEFT]
```
$ uname -a
Linux hp 4.4.0-040400rc4-generic #201512061930 SMP Mon Dec 7 00:32:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by MikeMecanic on 2015-12-07
This is the **error** I'm getting when I run Software Updater.  Switch to the main server to get today's updates.  This bug show up for the first time Sunday morning but this is the result of RC4 upgrade: [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) xenial Release.  Was ask to enable it after the upgrade:  **Failed to download repository information.  *Check you Internet connection***

:The repository 'http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu xenial Release' does not have a Release file., W:data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found, W:Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, W:Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by zika on 2015-12-07
Which PPA is that [URL]("http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu") supposed to represent?

---

### Post by Doug S on 2015-12-07
> **MikeMecanic said:**
> This is the **error** I'm getting when I run Software Updater. Mike, if I could, I'd like to offer a couple of suggestions if you are going to try these release candidate kernels:
[LIST]
[/LIST]
. I never run updates while running these leading edge kernels. To do updates, I boot to the stock kernel, then run updates. Admittedly, I have forgotten on occasion.

. Keep in mind things that can and can not be attributed to the kernel itself. Icon sizes and nautilus stuff have nothing to do with the kernel, and are not subjects for this thread.

As with zika, I do not understand the link you provided.

---

### Post by MikeMecanic on 2015-12-07
> **zika said:**
> Which PPA is that [URL]("http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu") supposed to represent?

This PPA comes from the error generated by Software Updater after updating to RC4.  See screenshot (PPA).  I'm always getting the same message that you see in the screenshot since Sunday.  The PPA was not enable and I think it comes from there.  When I enable it, I just Copy/Paste the error from the pop-up of Sofware Updater.

Edit 1:  Got the error back (I copy it in this window).  It occurs when I switch from the Main Server to my home-town Ubuntu mirror.  See screenshot Error_Pop_up
Edit 2: Have no error if I disable both launchpad PPA's URL.  See screenshot No_Error (4.3.0.2)
Edit 3: Get that error when I re-enable them:
W:The repository 'http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu xenial Release' does not have a Release file., W:data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found, W:Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, W:Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

[SIZE=4]**I'm in a no end loop with Software Updater (SU) since Sunday morning.**[/SIZE]

---

### Post by MikeMecanic on 2015-12-07
> **Doug S said:**
> Mike, if I could, I'd like to offer a couple of suggestions if you are going to try these release candidate kernels:. I never run updates while running these leading edge kernels. To do updates, I boot to the stock kernel, then run updates. Admittedly, I have forgotten on occasion.

. Keep in mind things that can and can not be attributed to the kernel itself. Icon sizes and nautilus stuff have nothing to do with the kernel, and are not subjects for this thread.

As with zika, I do not understand the link you provided.

**Your suggestions a more then welcome.**

Stock Kernel:  It is the lowest one I guess?  The lowest one I have is 4.3.0.2.  It's not that easy the load the lowest ounce the highest boots first. But now that your telling me to do so...  

Well, I'm just giving feedback of issues that I deal with.  Will try, if you prefer, to forward them in launchpad or open a new thread.

For the link, the title of the screenshot explain it (see Zika above):  It comes from an error window in Software Updater. 

Regards,

---

### Post by Doug S on 2015-12-08
> **MikeMecanic said:**
> Stock Kernel:  It is the lowest one I guess?  The lowest one I have is 4.3.0.2.  It's not that easy the load the lowest ounce the highest boots first. But now that your telling me to do so... I just meant whatever is supposed to be the current kernel for whatever release you are using (for me that is 3.16.0-55-generic).

I always have grub set to a long timeout (like 20 seconds), specifically so that I have time to go to the advanced menu and select the kernel I want, as it is very very rare that I want to  boot the one that grub would select by default.

---

### Post by zika on 2015-12-08
LeftShift is the key to not have any unwanted delay in grub... ;)

---

### Post by ch43 on 2015-12-08
Confirmed kernel compiles starting from rc4. Before rc4, I had to disable the LNET modules. I have some builds up at kernel.epsilon.space but they are using mtune=mcore2 as they are for personal use...

---

### Post by MikeMecanic on 2015-12-10
Made a fourth fresh install of Ubuntu x. The grub menu is now black, it looks better, much more clearer.  One of the surprises that developers give me when I play a little deeper in the machine.  

```
xenia4l@hp:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc4-generic           4.4.0-040400rc4.201512061930               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-19-generic            4.2.0-19.23                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-2-generic             4.3.0-2.11                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
xenia4l@hp:~$

```

Regards,

---

### Post by tokyobadger on 2015-12-10
> **tokyobadger said:**
> When I boot 4.4-rc2 and 4.4-rc3 the GUI comes up, I can use my keyboard to login, I can use my keyboard shortcuts to pull up the dash or launch the terminal. My mouse however is not working because the wireless receiver is not being "found" in the boot process.

Re: current Nautilus - I'm also not a fan of the changes I've seen so far, but I think the topic deserves a separate thread
4.4-rc4 has resolved the issue with the keyboard's wireless receiver.

I also now have a black grub screen and verbose boot process for 50% of boot before plymouth kicks in but these are no doubt related to the plymouth updates that came in today (6 or 7 packages?)

Nvidia proprietary (358.16) working fine (so far)

---

### Post by MikeMecanic on 2015-12-10
Got a successful partial updates.  Then I did it manually and was up to date.  The Grub menu is black now. 

No bug, no error..  Except maybe a video glitch on startup when Unity shows up.  Plus, it boots slowly, not fully enjoying Systemd.  It shutdown rapidly.

---

### Post by Doug S on 2015-12-13
Kernel 4.4-rc5 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc5-wily/"). It will be awhile before I can try it.

Edit: Seems O.K., but I haven't done much yet.```
Linux s15 4.4.0-rc5-stock #140 SMP Sun Dec 13 20:45:31 PST 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by sammiev on 2015-12-13
So far so good.

```
sam@sam-G-L650:~$ uname -r
4.4.0-040400rc5-generic
```

---

### Post by MikeMecanic on 2015-12-14
> **sammiev said:**
> So far so good.

Same here, this time on XUbuntu default LVM configuration.  Proposed remains enable:  No bug, no error.  Btw, history page is back in Synaptic 0.82.5

```
xu@xx:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc5-generic   4.4.0-040400rc5.201512140221             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-2-generic     4.3.0-2.11                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-4-generic     4.3.0-4.13                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
xu@xx:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for xu: 
NAME                   FSTYPE        SIZE MOUNTPOINT LABEL
sda                                698.7G            
&#9500;&#9472;sda1                 ext2          243M /boot      
&#9500;&#9472;sda2                                 1K            
&#9492;&#9472;sda5                 LVM2_member 698.4G            
  &#9500;&#9472;xubuntu--vg-root   ext4        694.5G /          
  &#9492;&#9472;xubuntu--vg-swap_1 swap          3.9G [SWAP]     
sr0                                 1024M            
xu@xx:~$ exit

```

*ii means It should be installed and it is installed *
*rc means It's removed/uninstalled but it's configuration files are still there*

[http://news.softpedia.com/news/linus-torvalds-announces-linux-kernel-4-4-rc5-final-release-coming-early-2016-497555.shtml](http://news.softpedia.com/news/linus-torvalds-announces-linux-kernel-4-4-rc5-final-release-coming-early-2016-497555.shtml)

All the best,

---

### Post by zika on 2015-12-15
To remove all the cruft either use (gtk)orphan(er) or```
dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
```with care... ;)

---

### Post by MikeMecanic on 2015-12-15
> **zika said:**
> To remove all the cruft either use (gtk)orphan(er) or```
dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
```with care... ;)

[LEFT][SIZE=3][COLOR=#666666][FONT=Consolas]I removed old Kernel's successfully using the command line above.
[/FONT][/COLOR][/SIZE][COLOR=#666666][FONT=Consolas]
[/FONT][/COLOR][/LEFT]
```
[LEFT]xu@xx:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc5-generic   4.4.0-040400rc5.201512140221             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xu@xx:~$ exit[/LEFT]

```[LEFT]
[SIZE=3][COLOR=#666666][FONT=Consolas]Was getting an error on startup that I don't get anymore.  [/FONT][/COLOR][COLOR=#666666][FONT=Consolas]Seems to boot faster now.
[/FONT][/COLOR][COLOR=#666666][FONT=Consolas]As shown in Gnome System Log (GUI)

Dec15 13:07:19 xx whoopsie[777]: [13:07:19] Parsing/var/crash/_usr_sbin_update-apt-xapian-index.0.crash.
Dec15 13:07:19 xx whoopsie[777]: [13:07:19] Uploading/var/crash/_usr_sbin_update-apt-xapian-index.0.crash.
Dec15 13:07:20 xx whoopsie[777]: [13:07:20] Sent; server replied with:No error
Dec15 13:07:20 xx whoopsie[777]: [13:07:20] Response code: 200
Dec15 13:07:20 xx whoopsie[777]: [13:07:20] Reported OOPS IDaec23424-a356-11e5-b1b5-fa163e75317b

[/FONT][/COLOR][COLOR=#666666][FONT=Consolas]With grateful thanks for the tip,

[/FONT][/COLOR][/SIZE]Edit:  sudo apt-get autoremove
```
xu@xx:~$ uname -r
4.4.0-040400rc5-generic
xu@xx:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.3.0-2 linux-headers-4.3.0-2-generic linux-headers-4.3.0-4
  linux-headers-4.3.0-4-generic linux-headers-generic thermald
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 154 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 233774 files and directories currently installed.)
Removing linux-headers-generic (4.3.0.4.5) ...
Removing linux-headers-4.3.0-2-generic (4.3.0-2.11) ...
Removing linux-headers-4.3.0-2 (4.3.0-2.11) ...
Removing linux-headers-4.3.0-4-generic (4.3.0-4.13) ...
Removing linux-headers-4.3.0-4 (4.3.0-4.13) ...
Removing thermald (1.4.3-5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu1) ...
xu@xx:~$ **sudo reboot**
xu@xx:~$ sudo apt-get autoremove
[sudo] password for xu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xu@xx:~$ exit
[SIZE=3][COLOR=#666666][FONT=Consolas]
[/FONT][/COLOR][/SIZE]
```

[/LEFT]

---

### Post by Doug S on 2015-12-20
Kernel 4.4-rc6 has been [released]("https://www.kernel.org/"). It is on the [Ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/").
I am running a self compiled one now.```
~$ uname -a
Linux s15 4.4.0-rc6-stock #141 SMP Sun Dec 20 18:23:49 PST 2015 x86_64 x86_64 x86_64 GNU/Linux
```
EDIT: Now running the Ubuntu PPA kernel:```
$ uname -a
Linux s15 4.4.0-040400rc6-generic #201512202030 SMP Mon Dec 21 01:32:09 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```and am using the Ubuntu kernel config file for my own compiles. I had not synchronized with the Ubuntu kernel config since the start of this cycle. The differences between my old config and the Ubuntu config were significant.

---

### Post by MikeMecanic on 2015-12-21
That ends a perfect week on RC 5.

```
xu@xx:~$ uname -r
4.4.0-040400rc6-generic
xu@xx:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc5-generic   4.4.0-040400rc5.201512140221               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xu@xx:~$ 

```

All the best,

Edit: Made a fresh install (LVM Default) after the upgrade with today's build.  Lost the network name and therefore the wired network on reboot (not the first time in the past 2 weeks). Edit Connection (empty)/Add/Ethernet/Create/Edit/Rename/Save/.  Recover the Internet that way.

```
ux@rc6:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc5-generic   4.4.0-040400rc5.201512140221             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-2-generic     4.3.0-2.11                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ux@rc6:~$ dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 213996 files and directories currently installed.)
Removing linux-image-extra-4.3.0-2-generic (4.3.0-2.11) ...
Purging configuration files for linux-image-extra-4.3.0-2-generic (4.3.0-2.11) ...
ux@rc6:~$   sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-generic thermald
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 591 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 213996 files and directories currently installed.)
Removing linux-headers-generic (4.3.0.2.5) ...
Removing thermald (1.4.3-5) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu1) ...
ux@rc6:~$ **sudo reboot**
ux@rc6:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc5-generic   4.4.0-040400rc5.201512140221             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ux@rc6:~$ sudo apt-get autoremove
[sudo] password for ux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ux@rc6:~$ uname -a
Linux rc6 4.4.0-040400rc6-generic #201512202030 SMP Mon Dec 21 01:32:09 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ux@rc6:~$ exit
```

EDIT 2:  Proposed Enable

```
ux@rc6:~$ sudo apt-get autoremove
[sudo] password for ux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ux@rc6:~$ dpkg --list | grep linux-image
[COLOR=#ff0000]ii [/COLOR] linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ux@rc6:~$ exit

```

---

### Post by MikeMecanic on 2015-12-27
From the installer up-to loading RC_6 after post-installation, I have no bug and no error to report.

```
rc6@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.3.0-2-generic           4.3.0-2.11                               amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.3.0-5-generic           4.3.0-5.16                               amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-2-generic     4.3.0-2.11                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-5-generic     4.3.0-5.16                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-generic                   4.3.0.5.6                                amd64        Generic Linux kernel image
rc6@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-2-generic     4.3.0-2.11                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-5-generic     4.3.0-5.16                               amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
rc6@ug:~$ dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
[sudo] password for rc6: 
...
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc6@ug:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                         FSTYPE        SIZE MOUNTPOINT LABEL
sda                                      698.7G            
&#9500;&#9472;sda1                       ext2          243M /boot      
&#9500;&#9472;sda2                                       1K            
&#9492;&#9472;sda5                       LVM2_member 698.4G            
  &#9500;&#9472;ubuntu--gnome--vg-root   ext4        694.5G /          
  &#9492;&#9472;ubuntu--gnome--vg-swap_1 swap          3.9G [SWAP]     
sr0                                       1024M            
rc6@ug:~$ 


```

All the best,

---

### Post by Irihapeti on 2015-12-27
4.4_rc6 seems to be running fine on my EeePC 900.
```
dpkg --list | grep linux-image
ii  linux-image-4.3.0-5-generic           4.3.0-5.16                                 i386         Linux kernel image for version 4.3.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030               i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.3.0-5-generic     4.3.0-5.16                                 i386         Linux kernel extra modules for version 4.3.0 on 32 bit x86 SMP
ii  linux-image-generic                   4.3.0.5.6                                  i386         Generic Linux kernel image
```

---

### Post by tokyobadger on 2015-12-28
[4.4-rc7 is up]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc7-wily/") (and installed here).

[Looks like there will be an rc8](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-rc7-Released) before the official release.

This series from rc6 has been very stable; up to rc4 only partially working, and rc5 left me ambivalent.

16.04 kernel freeze is 2016/04/07 - almost enough time for a 4.6 inclusion <-- not going to happen at release as it is an LTS, certainly enough time to ensure 4.4 is solid

---

### Post by sammiev on 2015-12-28
So far no issues.

```
uname -r
4.4.0-040400rc7-generic
```

---

### Post by Irihapeti on 2015-12-28
Seems to be working here, too.

```
uname -r
4.4.0-040400rc7-generic
```

---

### Post by sammiev on 2015-12-28
> **Irihapeti said:**
> Seems to be working here, too.

```
uname -r
4.4.0-040400rc7-generic
```

I'm so glad it worked out so well for you with all the problems you had. :)

---

### Post by Irihapeti on 2015-12-28
Actually, it was only one problem which I fixed by changing Grub settings. 

Now it's back to its boringly-stable normal state. :)


Is 4.4 still going to be the standard xenial kernel by release time?

---

### Post by MikeMecanic on 2015-12-28
Upstart is not shown anymore in the Grub menu, only generic and recovery mode.

```
rc6@ug:~$ dpkg --list | grep linux-image
ii [COLOR=#ff0000] linux-image[/COLOR]-4.4.0-040400rc6-generic   4.4.0-040400rc6.201512202030               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff0000] linux-image[/COLOR]-4.4.0-040400rc7-generic   4.4.0-040400rc7.201512272230               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP

```
Will now do a fresh install with the latest build to see if it loads properly after.

EDIT:  Fresh Install today"s build. No bug with any minor issue.

Loading sequence with Proposed

```
xx7@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.3.0-2-generic           4.3.0-2.11                                 amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.3.0-5-generic           4.3.0-5.16                                 amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc7-generic   4.4.0-040400rc7.201512272230               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-2-generic     4.3.0-2.11                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-5-generic     4.3.0-5.16                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-generic                   4.3.0.5.6                                  amd64        Generic Linux kernel image
xx7@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M  147M   77M  66% /boot
xx7@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.3.0-2-generic           4.3.0-2.11                                 amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.3.0-5-generic           4.3.0-5.16                                 amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc7-generic   4.4.0-040400rc7.201512272230               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-2-generic     4.3.0-2.11                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-5-generic     4.3.0-5.16                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-generic                   4.3.0.5.6                                  amd64        Generic Linux kernel image
xx7@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M  147M   77M  66% /boot
xx7@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.3.0-5-generic           4.3.0-5.16                                 amd64        Linux kernel image for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc7-generic   4.4.0-040400rc7.201512272230               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.3.0-5-generic     4.3.0-5.16                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
ii  linux-image-generic                   4.3.0.5.6                                  amd64        Generic Linux kernel image
xx7@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M  101M  123M  46% /boot
xx7@ug:~$
```

---

### Post by Rustan on 2015-12-28
After starting the game borderlands 2 virtual console (Ctrl + Alt + F1) no longer works. kernel 4.3 has no problems

---

### Post by Doug S on 2016-01-03
Kernel 4.4-rc8 is available at kernel.org, but not yet at the Ubuntu PPA (perhaps shortly).
I am building it now.

---

### Post by sammiev on 2016-01-03
> **Doug S said:**
> Kernel 4.4-rc8 is available at kernel.org, but not yet at the Ubuntu PPA (perhaps shortly).
I am building it now.

I wonder what the changes were, it was solid here.

Looking forward for the main release to come out. ;)

---

### Post by Doug S on 2016-01-03
> **sammiev said:**
> I wonder what the changes were, it was solid here.

Looking forward for the main release to come out. ;)For an rc8 version, I observed a surprising number of commits when I did a "git pull" to go from rc7 to rc8.
Anyway running it now, but haven't done much yet:
```
doug@s15:~$ uname -a
Linux s15 4.4.0-rc8-stock #144 SMP Sun Jan 3 20:35:42 PST 2016 x86_64 x86_64 x86_64 GNU/Linux
```

EDIT: Here is the commit list summary:
```
1683098 Linux 4.4-rc8
4294616 Merge branch 'upstream' of git://git.linux-mips.org/pub/scm/ralf/upstream-linus
4e5e384 Merge tag 'drm-intel-fixes-2016-01-02' of git://anongit.freedesktop.org/drm-intel
9c982e8 Merge tag 'pci-v4.4-fixes-3' of git://git.kernel.org/pub/scm/linux/kernel/git/helgaas/pci
7c672dd Merge git://git.kernel.org/pub/scm/linux/kernel/git/davem/sparc
8f5daf2 Merge git://git.kernel.org/pub/scm/linux/kernel/git/davem/net
42d85c5 sparc: Wire up mlock2 system call.
8b30ca7 sparc: Add all necessary direct socket system calls.
068d8bd sctp: sctp should release assoc when sctp_make_abort_user return NULL in sctp_close
a0ccc3f Merge tag 'wireless-drivers-for-davem-2015-12-28' of git://git.kernel.org/pub/scm/linux/kernel/git/kvalo/wireless-drivers
574aab1 net, socket, socket_wq: fix missing initialization of flags
c616920 Merge branch 'for-linus' of git://git.kernel.dk/linux-block
3d8acd1 drm/i915: increase the tries for HDMI hotplug live status checking
866be88 Merge branch 'akpm' (patches from Andrew)
e25bd6c Merge branch 'for-linus' of git://git.kernel.org/pub/scm/linux/kernel/git/viro/vfs
6cdb18a mm/vmstat: fix overflow in mod_zone_page_state()
cc28d6d ocfs2/dlm: clear migration_pending when migration target goes down
5f0f288 mm/memory_hotplug.c: check for missing sections in test_pages_in_a_zone()
b5a8bc3 ocfs2: fix flock panic issue
92a8ed4 m32r: add io*_rep helpers
6122192 m32r: fix build failure
facca61 arch/x86/xen/suspend.c: include xen/xen.h
6df3868 mm: memcontrol: fix possible memcg leak due to interrupted reclaim
5c9ee4c ocfs2: fix BUG when calculate new backup super
398c750 MIPS: VDSO: Fix build error with binutils 2.24 and earlier
c1e3334 drivers: net: cpsw: fix error return code
90c7afc openvswitch: Fix template leak in error cases.
76cc404 [PATCH] arm: fix handling of F_OFD_... in oabi_fcntl64()
c3293a9 lightnvm: wrong offset in bad blk lun calculation
1e60508 Merge tag 'for-linus' of git://git.kernel.org/pub/scm/linux/kernel/git/dledford/rdma
48cc661 null_blk: use async queue restart helper
2149141 block: add blk_start_queue_async()
8513342 Merge branch 'linus' of git://git.kernel.org/pub/scm/linux/kernel/git/herbert/crypto-2.6
2c7143d Merge branch 'for-linus2' of git://git.kernel.org/pub/scm/linux/kernel/git/jmorris/linux-security
f41647e RDMA/be2net: Remove open and close entry points
10a214d RDMA/ocrdma: Depend on async link events from CNA
36ac0db RDMA/ocrdma: Dispatch only port event when port state changes
c6002d5 RDMA/ocrdma: Fix vlan-id assignment in qp parameters
3538a5c sctp: label accepted/peeled off sockets
9ba0b96 sctp: use GFP_USER for user-controlled kmalloc
74bf8ef Linux 4.4-rc7

```

---

### Post by sammiev on 2016-01-04
@ Doug S,

Thanks

---

### Post by zika on 2016-01-04
Opened UF today without log-in ad looked at Your signature (disabled otherwise):
[COLOR=#000000]Smile today, cry tomorrow! [/COLOR][COLOR=#000000]( Read this everyday )[/COLOR]
My grandmother (very wise woman) had saying: Do take serious care today so You won't cry tomorrow.
Sorry for off-topic.

---

### Post by Doug S on 2016-01-04
> **Doug S said:**
> Kernel 4.4-rc8 is available at kernel.org, but not yet at the Ubuntu PPA (perhaps shortly).Hmmm, Still not in the Ubuntu PPA. I have never before seen such a large delay between [kernel.org]("https://www.kernel.org/") and the [Ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

---

### Post by zika on 2016-01-04
[https://launchpadlibrarian.net/232826520/linux_4.4.0-0.9_source.changes](https://launchpadlibrarian.net/232826520/linux_4.4.0-0.9_source.changes)
**ppa:canonical-kernel-team/unstable**

---

### Post by Doug S on 2016-01-05
> **zika said:**
> [https://launchpadlibrarian.net/232826520/linux_4.4.0-0.9_source.changes](https://launchpadlibrarian.net/232826520/linux_4.4.0-0.9_source.changes)
**ppa:canonical-kernel-team/unstable**zika: Isn't your link to the Ubuntu version of kernel 4.4 and not the mainline version?

Regardless, I asked on [IRC just now]("http://irclogs.ubuntu.com/2016/01/05/%23ubuntu-kernel.html")**, and indeed there was an issue. We can expect the kernel to be available "in due course", which I am not sure how long that means.

** Note: that the link I gave only updates every hour on the hour (actually, about 5 or 6 minutes after the hour). So it'll be another minute or two before the content is there.

EDIT: O.K. so [the directory has appeared]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc8-wily/"), but the builds all failed. The saga continues...

---

### Post by zika on 2016-01-05
> **Doug S said:**
> zika: Isn't your link to the Ubuntu version of kernel 4.4 and not the mainline version?Yeap: 4.4rc8 + several things more. I thought I've wrote where it came from. Nice by-pass replacement or complete solution for me for (quite) some time... CanonicalKernelTeam (I consider them as local team) is doing great job for quite some time.

---

### Post by Doug S on 2016-01-05
> **zika said:**
> Nice by-pass replacement or complete solution for me for (quite) some time... CanonicalKernelTeam (I consider them as local team) is doing great job for quite some time.Aghhh, I understand.

Everybody: The compiles (builds) failed due to some missing tools on the new builder computer. The builds are being re-run now.

---

### Post by MikeMecanic on 2016-01-05
Tuesday, January 5th 2016
Kernel 4.4 RC8

RC7 was the best one.  It's pretty stable thanks

```
xx8@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc7-generic   4.4.0-040400rc7.201512272230               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc8-generic   4.4.0-040400rc8.201601051225               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xx8@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M  101M  123M  45% /boot
xx8@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400rc8-generic   4.4.0-040400rc8.201601051225               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xx8@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M   55M  169M  25% /boot
xx8@ug:~$ exit

```

All the best in 2016,

---

### Post by MikeMecanic on 2016-01-10
_It doesn't load first_ and after a few restarts, it remains second in the Grub menu.  Manually, it loads correctly.

```
xx8@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400-generic      4.4.0-040400.201601101930                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc8-generic   4.4.0-040400rc8.201601051225               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xx8@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M  101M  123M  45% /boot
xx8@ug:~$ 

``````

[LEFT][FONT=Georgia]cd/tmp[/FONT][/LEFT]

```
```
[LEFT][FONT=Georgia]wget\[/FONT][/LEFT]

```
```
[LEFT][FONT=Georgia]kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-headers-4.4.0-040400_4.4.0-040400.201601101930_all.deb\[/FONT][/LEFT]

```
```
[LEFT][FONT=Georgia]kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-headers-4.4.0-040400-generic_4.4.0-040400.201601101930_amd64.deb\[/FONT][/LEFT]

```
```
[LEFT][FONT=Georgia]kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/linux-image-4.4.0-040400-generic_4.4.0-040400.201601101930_amd64.deb[/FONT][/LEFT]

```
```
[LEFT][FONT=Georgia]sudodpkg -i linux-headers-4.4*.deb linux-image-4.4*.deb[/FONT][/LEFT]

```
```
[LEFT] [FONT=Calibri][FONT=Georgia]sudo reboot
[/FONT][/FONT][/LEFT]

```

EDIT:
```
xx8@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400-generic      4.4.0-040400.201601101930                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xx8@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M   55M  169M  25% /boot
xx8@ug:~$
```

---

### Post by Irihapeti on 2016-01-10
> **MikeMecanic said:**
> _It doesn't load first_ and after a few restarts, it remains second in the Grub menu.  Manually, it loads correctly.

```
xx8@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400-generic      4.4.0-040400.201601101930                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-040400rc8-generic   4.4.0-040400rc8.201601051225               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
xx8@ug:~$ df -h | grep ^/dev/sda1
/dev/sda1       236M  101M  123M  45% /boot
xx8@ug:~$ 

```

I'm noticing the same thing here. Perhaps grub organises things in reverse sort order - which would normally be in order of recency, but in this particular case is not.

---

### Post by MikeMecanic on 2016-01-10
> **Irihapeti said:**
> I'm noticing the same thing here. Perhaps grub organises things in reverse sort order - which would normally be in order of recency, but in this particular case is not.

Perfect! Just want to make sure it was ok.  So I removed rc8.  As usual it runs A+

---

### Post by zika on 2016-01-11
Reverse alphabetical order that (in almost all cases) provide that the newest kernel is on top. Mainline kernels break that rule only in case of final and rc, as usual for some time...

---

### Post by fthx on 2016-01-11
We're close ;-)

[https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable/+build/8832818](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable/+build/8832818)

---

### Post by Doug S on 2016-01-11
I am running 4.4 now. This 4.4 cycle has been one of the more interesting/challenging/whatever cycles. See everyone in a couple of weeks for 4.5-rc1.

---

### Post by QDR06VV9 on 2016-01-11
> **Doug S said:**
> I am running 4.4 now. This 4.4 cycle has been one of the more interesting/challenging/whatever cycles. See everyone in a couple of weeks for 4.5-rc1.
LOL:D That is a Understatement for sure.
I can not remember the last time I had to use Bisect for kernels...Yee Haa!
But this is Testing at it's prime....
Kind Regards

---

### Post by MikeMecanic on 2016-01-11
An amazing cycle.  Made a fresh install every Monday and today I don't have to do it knowing that the base of Kernel 4.4 LTS is solid.  


Never seen Software Updater running that way.  There was a huge amount of updates every week (including Proposed) that did not affect by any meaning stability.  


I think will get 4.5 next week...

---

### Post by QDR06VV9 on 2016-01-12
This kernel has dropped my sound card [COLOR=#000000][FONT=Ubuntu Mono]4.4.0-040400rc8 Tried to fix but no go.
Kernel [/FONT][/COLOR]4.3.0-5-generic is just fine...
```
$ inxi -A
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Creative Labs SB Audigy driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.3.0-5-generic

```
It is this driver that wont load
>  Creative Labs SB Audigy driver: snd_emu10k1
Tried compiling but no success.
Regards

---

### Post by Doug S on 2016-01-12
> **runrickus said:**
> This kernel has dropped my sound card

Is this just an Ubuntu kernel configuration issue? (as opposed to a kernel source code issue.)
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]diff .config-4.3.0-040300-generic .config-4.4.0-040400rc8-generic | grep EMU10K1[/COLOR]
< CONFIG_SND_EMU10K1_SEQ=m
> # CONFIG_SND_EMU10K1_SEQ is not set
< CONFIG_SND_EMU10K1=m
< CONFIG_SND_EMU10K1X=m

```

If yes, I do not understand this comment:
> **runrickus said:**
> 4.4.0-040400rc8 Tried to fix but no go.


> **runrickus said:**
> Tried compiling but no success.
Are you saying you put back those three kernel configuration directives, and it still didn't work?

---

### Post by QDR06VV9 on 2016-01-12
[QUOTE=Doug S;13421889]Is this just an Ubuntu kernel configuration issue? (as opposed to a kernel source code issue.)
```
doug@s15:~/temp-k-git/linux$ [COLOR=#FF0000]diff .config-4.3.0-040300-generic .config-4.4.0-040400rc8-generic | grep EMU10K1[/COLOR]
< CONFIG_SND_EMU10K1_SEQ=m
> # CONFIG_SND_EMU10K1_SEQ is not set
< CONFIG_SND_EMU10K1=m
< CONFIG_SND_EMU10K1X=m

```

If yes, I do not understand this comment:



_**Are you saying you put back those three kernel configuration directives, and it still didn't work?[**_/QUOTE]

Yes Sir put those back and even alsamixer wont find the SB card..
It is just not there on RC_8 This is a first for me:o
Two Screenshots 1st with RC_8 second with 4.3.0-5-generic
You can see that the SB card is just not showing up.

---

### Post by Doug S on 2016-01-12
Oh, from observing some non related stuff in your screen shot, I think I need to explain something: I keep a great many kernel config files in my main git directory (~ over 40). It is my own naming convention. I wouldn't expect your computer to have the same files. Try looking in your /boot directory for similar stuff (i.e. for your own "diff" tests). 

I see you use the low latency kernel. I'll try a build of kernel 4.4, low latency, with that stuff put back, and see if the module is there.

---

### Post by QDR06VV9 on 2016-01-12
I am building the 4.4.0-040400.201601101930 low lat  from today(Wily) right now..
Will Report back.

---

### Post by Doug S on 2016-01-12
> **runrickus said:**
> I am building the 4.4.0-040400.201601101930 low lat  from today(Wily) right now..
Will Report back.O.K. I will wait until you do. I see that this just occurred between 4.4-rc7 and 4.4-rc8. I also observe some other sound related changes between those two RC's.
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]diff /boot/config-4.4.0-040400rc7-generic /boot/config-4.4.0-040400rc8-generic[/COLOR]
3c3
< # Linux/x86_64 4.4.0-040400rc7-generic Kernel Configuration
---
> # Linux/x86_64 4.4.0-040400rc8-generic Kernel Configuration
393c393
< CONFIG_ZONE_DMA=y
---
> # CONFIG_ZONE_DMA is not set
517,518c517
< CONFIG_ZONE_DMA_FLAG=1
< CONFIG_BOUNCE=y
---
> CONFIG_ZONE_DMA_FLAG=0
545a545
> CONFIG_ZONE_DEVICE=y
5449c5449
< CONFIG_SND_EMU10K1_SEQ=m
---
> # CONFIG_SND_EMU10K1_SEQ is not set
5469d5468
< CONFIG_SND_ALS300=m
5471d5469
< CONFIG_SND_ALI5451=m
5479d5476
< CONFIG_SND_AZT3328=m
5504,5505d5500
< CONFIG_SND_EMU10K1=m
< CONFIG_SND_EMU10K1X=m
5508,5511d5502
< CONFIG_SND_ES1938=m
< CONFIG_SND_ES1968=m
< CONFIG_SND_ES1968_INPUT=y
< CONFIG_SND_ES1968_RADIO=y
5516d5506
< CONFIG_SND_ICE1712=m
5523,5524d5512
< CONFIG_SND_MAESTRO3=m
< CONFIG_SND_MAESTRO3_INPUT=y
5532,5533d5519
< CONFIG_SND_SONICVIBES=m
< CONFIG_SND_TRIDENT=m
7448a7435,7436
> CONFIG_ND_PFN=m
> CONFIG_NVDIMM_PFN=y

```And the modules (Edited output from [COLOR="#FF0000"] locate emu10k1 | grep "\.ko"[/COLOR]):
```
/lib/modules/4.4.0-040400rc7-generic/kernel/drivers/input/gameport/emu10k1-gp.ko
/lib/modules/4.4.0-040400rc7-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/4.4.0-040400rc7-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/4.4.0-040400rc7-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/4.4.0-040400rc8-generic/kernel/drivers/input/gameport/emu10k1-gp.ko


```

---

### Post by QDR06VV9 on 2016-01-12
> **Doug S said:**
> O.K. I will wait until you do. I see that this just occurred between 4.4-rc7 and 4.4-rc8. I also observe some other sound related changes between those two RC's.
```
doug@s15:~/temp-k-git/linux$ [COLOR=#FF0000]diff /boot/config-4.4.0-040400rc7-generic /boot/config-4.4.0-040400rc8-generic[/COLOR]
3c3
< # Linux/x86_64 4.4.0-040400rc7-generic Kernel Configuration
---
> # Linux/x86_64 4.4.0-040400rc8-generic Kernel Configuration
393c393
< CONFIG_ZONE_DMA=y
---
> # CONFIG_ZONE_DMA is not set
517,518c517
< CONFIG_ZONE_DMA_FLAG=1
< CONFIG_BOUNCE=y
---
> CONFIG_ZONE_DMA_FLAG=0
545a545
> CONFIG_ZONE_DEVICE=y
5449c5449
< CONFIG_SND_EMU10K1_SEQ=m
---
> # CONFIG_SND_EMU10K1_SEQ is not set
5469d5468
< CONFIG_SND_ALS300=m
5471d5469
< CONFIG_SND_ALI5451=m
5479d5476
< CONFIG_SND_AZT3328=m
5504,5505d5500
< CONFIG_SND_EMU10K1=m
< CONFIG_SND_EMU10K1X=m
5508,5511d5502
< CONFIG_SND_ES1938=m
< CONFIG_SND_ES1968=m
< CONFIG_SND_ES1968_INPUT=y
< CONFIG_SND_ES1968_RADIO=y
5516d5506
< CONFIG_SND_ICE1712=m
5523,5524d5512
< CONFIG_SND_MAESTRO3=m
< CONFIG_SND_MAESTRO3_INPUT=y
5532,5533d5519
< CONFIG_SND_SONICVIBES=m
< CONFIG_SND_TRIDENT=m
7448a7435,7436
> CONFIG_ND_PFN=m
> CONFIG_NVDIMM_PFN=y

```

This one solved my issue..:D
```
inxi -Fxz
System:    Host: Ghost Kernel: 4.4.0-040400-lowlatency x86_64 (64 bit gcc: 5.2.1)
           Desktop: MATE 1.12.1 (Gtk 3.18.6-1ubuntu1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20743
           clock speeds: max: 2600 MHz 1: 800 MHz 2: 1400 MHz 3: 1400 MHz
           4: 2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] bus-ID: 01:00.0
           Display Server: X.Org 1.17.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 358.16 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Creative Labs SB Audigy port: e800 bus-ID: 04:05.0
           Sound: ALSA v: k4.4.0-040400-lowlatency
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: c800 bus-ID: 02:00.0
           IF: eno1 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too v: 0.9.28 port: e400 bus-ID: 04:06.0
           IF: enp4s6 state: down mac: <filter>
Drives:    HDD Total Size: 2500.5GB (0.9% used)
           ID-1: /dev/sda model: WDC_WD5000AADS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
Partition: ID-1: / size: 193G used: 15G (8%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 6.44GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 216 Uptime: 1 min Memory: 403.5/5967.0MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 



```
Thanks Doug for taking interest, Cheers

---

### Post by Doug S on 2016-01-12
> **runrickus said:**
> This one solved my issue..Perhaps we (I'll do it if you want) should go on IRC and ask why it was changed in the configuration file. I wonder if it might have been a mistake, as recall there was new build machine involved that resulted in other grief with -rc8.

---

### Post by QDR06VV9 on 2016-01-12
> **Doug S said:**
> Perhaps we (I'll do it if you want) should go on IRC and ask why it was changed in the configuration file. I wonder if it might have been a mistake, as recall there was new build machine involved that resulted in other grief with -rc8.
I think the problem is on my side, After another reboot(compiled Pulseaudio from git) the same happens again no SB card????(on4.4.0 kernel 4.3 still is good though)
I have this thing so tweaked right now(Early in Devel) That I am going to do a fresh install today **just to be sure**.
This partition has come from Trusty to Xenial.
I will report back.
Regards

---

### Post by QDR06VV9 on 2016-01-12
He He He!! No Difference..
I should have noticed my first output
```
Card-2 Creative Labs SB Audigy port: e800 bus-ID: 04:05.0
           Sound: ALSA v: k4.4.0-040400-lowlatency
```
But anyway still a no go for me
```
inxi -Fxz

System:    Host: GhostMan Kernel: 4.4.0-040400-lowlatency x86_64 (64 bit gcc: 5.2.1)
           Desktop: MATE 1.10.2 (Gtk 3.18.6-1ubuntu1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20743
           clock speeds: max: 2600 MHz 1: 1400 MHz 2: 1400 MHz 3: 800 MHz
           4: 1400 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] bus-ID: 01:00.0
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 11.0.7 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Creative Labs SB Audigy port: e800 bus-ID: 04:05.0
           Sound: ALSA v: k4.4.0-040400-lowlatency
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: c800 bus-ID: 02:00.0
           IF: eno1 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too v: 0.9.28 port: e400 bus-ID: 04:06.0
           IF: enp4s6 state: down mac: <filter>
Drives:    HDD Total Size: 2516.5GB (0.6% used)
           ID-1: /dev/sda model: WDC_WD5000AADS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
           ID-3: USB /dev/sdh model: U3_Cruzer_Micro size: 16.0GB
Partition: ID-1: / size: 193G used: 4.3G (3%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 6.44GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 211 Uptime: 2 min Memory: 336.1/5967.0MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.421) inxi: 2.2.28 


```
Fresh Install(formatted to be sure nothing left behind) with no updates yet, and no proprietary drivers installed yet..
I have not yet booted to the 4.3 generic yet.
Boot Info
```
#
# Automatically generated file; DO NOT EDIT.
# Linux/x86_64 4.4.0-040400-lowlatency Kernel Configuration
#
CONFIG_64BIT=y
CONFIG_X86_64=y
CONFIG_X86=y
CONFIG_INSTRUCTION_DECODER=y
CONFIG_PERF_EVENTS_INTEL_UNCORE=y
CONFIG_OUTPUT_FORMAT="elf64-x86-64"
CONFIG_ARCH_DEFCONFIG="arch/x86/configs/x86_64_defconfig"
CONFIG_LOCKDEP_SUPPORT=y
CONFIG_STACKTRACE_SUPPORT=y
CONFIG_HAVE_LATENCYTOP_SUPPORT=y
CONFIG_MMU=y
CONFIG_NEED_DMA_MAP_STATE=y
CONFIG_NEED_SG_DMA_LENGTH=y
CONFIG_GENERIC_ISA_DMA=y
CONFIG_GENERIC_BUG=y
CONFIG_GENERIC_BUG_RELATIVE_POINTERS=y
CONFIG_GENERIC_HWEIGHT=y
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
CONFIG_RWSEM_XCHGADD_ALGORITHM=y
CONFIG_GENERIC_CALIBRATE_DELAY=y
CONFIG_ARCH_HAS_CPU_RELAX=y
CONFIG_ARCH_HAS_CACHE_LINE_SIZE=y
CONFIG_HAVE_SETUP_PER_CPU_AREA=y
CONFIG_NEED_PER_CPU_EMBED_FIRST_CHUNK=y
CONFIG_NEED_PER_CPU_PAGE_FIRST_CHUNK=y
CONFIG_ARCH_HIBERNATION_POSSIBLE=y
CONFIG_ARCH_SUSPEND_POSSIBLE=y
CONFIG_ARCH_WANT_HUGE_PMD_SHARE=y
CONFIG_ARCH_WANT_GENERAL_HUGETLB=y
CONFIG_ZONE_DMA32=y
CONFIG_AUDIT_ARCH=y
CONFIG_ARCH_SUPPORTS_OPTIMIZED_INLINING=y
CONFIG_ARCH_SUPPORTS_DEBUG_PAGEALLOC=y
CONFIG_HAVE_INTEL_TXT=y
CONFIG_X86_64_SMP=y
CONFIG_ARCH_HWEIGHT_CFLAGS="-fcall-saved-rdi -fcall-saved-rsi -fcall-saved-rdx -fcall-saved-rcx -fcall-saved-r8 -fcall-saved-r9 -fcall-saved-r10 -fcall-saved-r11"
CONFIG_ARCH_SUPPORTS_UPROBES=y
CONFIG_FIX_EARLYCON_MEM=y
CONFIG_PGTABLE_LEVELS=4
CONFIG_DEFCONFIG_LIST="/lib/modules/$UNAME_RELEASE/.config"
CONFIG_IRQ_WORK=y
CONFIG_BUILDTIME_EXTABLE_SORT=y

#
# General setup
#
CONFIG_INIT_ENV_ARG_LIMIT=32
CONFIG_CROSS_COMPILE=""
# CONFIG_COMPILE_TEST is not set
CONFIG_LOCALVERSION=""
# CONFIG_LOCALVERSION_AUTO is not set
CONFIG_HAVE_KERNEL_GZIP=y
CONFIG_HAVE_KERNEL_BZIP2=y
CONFIG_HAVE_KERNEL_LZMA=y
CONFIG_HAVE_KERNEL_XZ=y
CONFIG_HAVE_KERNEL_LZO=y
CONFIG_HAVE_KERNEL_LZ4=y
CONFIG_KERNEL_GZIP=y
# CONFIG_KERNEL_BZIP2 is not set
# CONFIG_KERNEL_LZMA is not set
# CONFIG_KERNEL_XZ is not set
# CONFIG_KERNEL_LZO is not set
# CONFIG_KERNEL_LZ4 is not set
CONFIG_DEFAULT_HOSTNAME="(none)"
CONFIG_SWAP=y
CONFIG_SYSVIPC=y
CONFIG_SYSVIPC_SYSCTL=y
CONFIG_POSIX_MQUEUE=y
CONFIG_POSIX_MQUEUE_SYSCTL=y
CONFIG_CROSS_MEMORY_ATTACH=y
CONFIG_FHANDLE=y
CONFIG_USELIB=y
CONFIG_AUDIT=y
CONFIG_HAVE_ARCH_AUDITSYSCALL=y
CONFIG_AUDITSYSCALL=y
CONFIG_AUDIT_WATCH=y
CONFIG_AUDIT_TREE=y

#
# IRQ subsystem
#
CONFIG_GENERIC_IRQ_PROBE=y
CONFIG_GENERIC_IRQ_SHOW=y
CONFIG_GENERIC_PENDING_IRQ=y
CONFIG_GENERIC_IRQ_CHIP=y
CONFIG_IRQ_DOMAIN=y
CONFIG_IRQ_DOMAIN_HIERARCHY=y
CONFIG_GENERIC_MSI_IRQ=y
CONFIG_GENERIC_MSI_IRQ_DOMAIN=y
# CONFIG_IRQ_DOMAIN_DEBUG is not set
CONFIG_IRQ_FORCED_THREADING=y
CONFIG_SPARSE_IRQ=y
CONFIG_CLOCKSOURCE_WATCHDOG=y
CONFIG_ARCH_CLOCKSOURCE_DATA=y
CONFIG_CLOCKSOURCE_VALIDATE_LAST_CYCLE=y
CONFIG_GENERIC_TIME_VSYSCALL=y
CONFIG_GENERIC_CLOCKEVENTS=y
CONFIG_GENERIC_CLOCKEVENTS_BROADCAST=y
CONFIG_GENERIC_CLOCKEVENTS_MIN_ADJUST=y
CONFIG_GENERIC_CMOS_UPDATE=y

#
# Timers subsystem
#
CONFIG_TICK_ONESHOT=y
CONFIG_NO_HZ_COMMON=y
# CONFIG_HZ_PERIODIC is not set
CONFIG_NO_HZ_IDLE=y
# CONFIG_NO_HZ_FULL is not set
CONFIG_NO_HZ=y
CONFIG_HIGH_RES_TIMERS=y

#
# CPU/Task time and stats accounting
#
CONFIG_TICK_CPU_ACCOUNTING=y
# CONFIG_VIRT_CPU_ACCOUNTING_GEN is not set
# CONFIG_IRQ_TIME_ACCOUNTING is not set
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_TASKSTATS=y
CONFIG_TASK_DELAY_ACCT=y
CONFIG_TASK_XACCT=y
CONFIG_TASK_IO_ACCOUNTING=y

#
# RCU Subsystem
#
CONFIG_PREEMPT_RCU=y
# CONFIG_RCU_EXPERT is not set
CONFIG_SRCU=y
# CONFIG_TASKS_RCU is not set
CONFIG_RCU_STALL_COMMON=y
# CONFIG_TREE_RCU_TRACE is not set
# CONFIG_RCU_EXPEDITE_BOOT is not set
CONFIG_BUILD_BIN2C=y
# CONFIG_IKCONFIG is not set
CONFIG_LOG_BUF_SHIFT=18
CONFIG_LOG_CPU_MAX_BUF_SHIFT=12
CONFIG_HAVE_UNSTABLE_SCHED_CLOCK=y
CONFIG_ARCH_SUPPORTS_NUMA_BALANCING=y
CONFIG_ARCH_WANT_BATCHED_UNMAP_TLB_FLUSH=y
CONFIG_ARCH_SUPPORTS_INT128=y
CONFIG_NUMA_BALANCING=y
CONFIG_NUMA_BALANCING_DEFAULT_ENABLED=y
CONFIG_CGROUPS=y
# CONFIG_CGROUP_DEBUG is not set
CONFIG_CGROUP_FREEZER=y
CONFIG_CGROUP_PIDS=y
CONFIG_CGROUP_DEVICE=y
CONFIG_CPUSETS=y
CONFIG_PROC_PID_CPUSET=y
CONFIG_CGROUP_CPUACCT=y
CONFIG_PAGE_COUNTER=y
CONFIG_MEMCG=y
CONFIG_MEMCG_SWAP=y
# CONFIG_MEMCG_SWAP_ENABLED is not set
CONFIG_MEMCG_KMEM=y
CONFIG_CGROUP_HUGETLB=y
CONFIG_CGROUP_PERF=y
CONFIG_CGROUP_SCHED=y
CONFIG_FAIR_GROUP_SCHED=y
CONFIG_CFS_BANDWIDTH=y
# CONFIG_RT_GROUP_SCHED is not set
CONFIG_BLK_CGROUP=y
# CONFIG_DEBUG_BLK_CGROUP is not set
CONFIG_CGROUP_WRITEBACK=y
CONFIG_CHECKPOINT_RESTORE=y
CONFIG_NAMESPACES=y
CONFIG_UTS_NS=y
CONFIG_IPC_NS=y
CONFIG_USER_NS=y
CONFIG_PID_NS=y
CONFIG_NET_NS=y
CONFIG_SCHED_AUTOGROUP=y
# CONFIG_SYSFS_DEPRECATED is not set
CONFIG_RELAY=y
CONFIG_BLK_DEV_INITRD=y
CONFIG_INITRAMFS_SOURCE=""
CONFIG_RD_GZIP=y
CONFIG_RD_BZIP2=y
CONFIG_RD_LZMA=y
CONFIG_RD_XZ=y
CONFIG_RD_LZO=y
CONFIG_RD_LZ4=y
# CONFIG_CC_OPTIMIZE_FOR_SIZE is not set
CONFIG_SYSCTL=y
CONFIG_ANON_INODES=y
CONFIG_HAVE_UID16=y
CONFIG_SYSCTL_EXCEPTION_TRACE=y
CONFIG_HAVE_PCSPKR_PLATFORM=y
CONFIG_BPF=y
CONFIG_EXPERT=y
CONFIG_UID16=y
CONFIG_MULTIUSER=y
CONFIG_SGETMASK_SYSCALL=y
CONFIG_SYSFS_SYSCALL=y
CONFIG_SYSCTL_SYSCALL=y
CONFIG_KALLSYMS=y
CONFIG_KALLSYMS_ALL=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_PCSPKR_PLATFORM=y
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_EPOLL=y
CONFIG_SIGNALFD=y
CONFIG_TIMERFD=y
CONFIG_EVENTFD=y
CONFIG_BPF_SYSCALL=y
CONFIG_SHMEM=y
CONFIG_AIO=y
CONFIG_ADVISE_SYSCALLS=y
CONFIG_USERFAULTFD=y
CONFIG_PCI_QUIRKS=y
CONFIG_MEMBARRIER=y
# CONFIG_EMBEDDED is not set
CONFIG_HAVE_PERF_EVENTS=y

#
# Kernel Performance Events And Counters
#
CONFIG_PERF_EVENTS=y
# CONFIG_DEBUG_PERF_USE_VMALLOC is not set
CONFIG_VM_EVENT_COUNTERS=y
CONFIG_SLUB_DEBUG=y
# CONFIG_COMPAT_BRK is not set
# CONFIG_SLAB is not set
CONFIG_SLUB=y
# CONFIG_SLOB is not set
CONFIG_SLUB_CPU_PARTIAL=y
CONFIG_SYSTEM_DATA_VERIFICATION=y
CONFIG_PROFILING=y
CONFIG_TRACEPOINTS=y
CONFIG_KEXEC_CORE=y
CONFIG_OPROFILE=m
# CONFIG_OPROFILE_EVENT_MULTIPLEX is not set
CONFIG_HAVE_OPROFILE=y
CONFIG_OPROFILE_NMI_TIMER=y
CONFIG_KPROBES=y
CONFIG_JUMP_LABEL=y
# CONFIG_STATIC_KEYS_SELFTEST is not set
CONFIG_KPROBES_ON_FTRACE=y
CONFIG_UPROBES=y
# CONFIG_HAVE_64BIT_ALIGNED_ACCESS is not set
CONFIG_HAVE_EFFICIENT_UNALIGNED_ACCESS=y
CONFIG_ARCH_USE_BUILTIN_BSWAP=y
CONFIG_KRETPROBES=y
CONFIG_USER_RETURN_NOTIFIER=y
CONFIG_HAVE_IOREMAP_PROT=y
CONFIG_HAVE_KPROBES=y
CONFIG_HAVE_KRETPROBES=y
CONFIG_HAVE_OPTPROBES=y
CONFIG_HAVE_KPROBES_ON_FTRACE=y
CONFIG_HAVE_ARCH_TRACEHOOK=y
CONFIG_HAVE_DMA_ATTRS=y
CONFIG_HAVE_DMA_CONTIGUOUS=y
CONFIG_GENERIC_SMP_IDLE_THREAD=y
CONFIG_ARCH_WANTS_DYNAMIC_TASK_STRUCT=y
CONFIG_HAVE_REGS_AND_STACK_ACCESS_API=y
CONFIG_HAVE_CLK=y
CONFIG_HAVE_DMA_API_DEBUG=y
CONFIG_HAVE_HW_BREAKPOINT=y
CONFIG_HAVE_MIXED_BREAKPOINTS_REGS=y
CONFIG_HAVE_USER_RETURN_NOTIFIER=y
CONFIG_HAVE_PERF_EVENTS_NMI=y
CONFIG_HAVE_PERF_REGS=y
CONFIG_HAVE_PERF_USER_STACK_DUMP=y
CONFIG_HAVE_ARCH_JUMP_LABEL=y
CONFIG_ARCH_HAVE_NMI_SAFE_CMPXCHG=y
CONFIG_HAVE_ALIGNED_STRUCT_PAGE=y
CONFIG_HAVE_CMPXCHG_LOCAL=y
CONFIG_HAVE_CMPXCHG_DOUBLE=y
CONFIG_ARCH_WANT_COMPAT_IPC_PARSE_VERSION=y
CONFIG_ARCH_WANT_OLD_COMPAT_IPC=y
CONFIG_HAVE_ARCH_SECCOMP_FILTER=y
CONFIG_SECCOMP_FILTER=y
CONFIG_HAVE_CC_STACKPROTECTOR=y
CONFIG_CC_STACKPROTECTOR=y
# CONFIG_CC_STACKPROTECTOR_NONE is not set
# CONFIG_CC_STACKPROTECTOR_REGULAR is not set
CONFIG_CC_STACKPROTECTOR_STRONG=y
CONFIG_HAVE_CONTEXT_TRACKING=y
CONFIG_HAVE_VIRT_CPU_ACCOUNTING_GEN=y
CONFIG_HAVE_IRQ_TIME_ACCOUNTING=y
CONFIG_HAVE_ARCH_TRANSPARENT_HUGEPAGE=y
CONFIG_HAVE_ARCH_HUGE_VMAP=y
CONFIG_HAVE_ARCH_SOFT_DIRTY=y
CONFIG_MODULES_USE_ELF_RELA=y
CONFIG_HAVE_IRQ_EXIT_ON_IRQ_STACK=y
CONFIG_ARCH_HAS_ELF_RANDOMIZE=y
CONFIG_HAVE_COPY_THREAD_TLS=y
CONFIG_OLD_SIGSUSPEND3=y
CONFIG_COMPAT_OLD_SIGACTION=y

#
# GCOV-based kernel profiling
#
# CONFIG_GCOV_KERNEL is not set
CONFIG_ARCH_HAS_GCOV_PROFILE_ALL=y
# CONFIG_HAVE_GENERIC_DMA_COHERENT is not set
CONFIG_SLABINFO=y
CONFIG_RT_MUTEXES=y
CONFIG_BASE_SMALL=0
CONFIG_MODULES=y
# CONFIG_MODULE_FORCE_LOAD is not set
CONFIG_MODULE_UNLOAD=y
# CONFIG_MODULE_FORCE_UNLOAD is not set
CONFIG_MODVERSIONS=y
CONFIG_MODULE_SRCVERSION_ALL=y
CONFIG_MODULE_SIG=y
# CONFIG_MODULE_SIG_FORCE is not set
CONFIG_MODULE_SIG_ALL=y
# CONFIG_MODULE_SIG_SHA1 is not set
# CONFIG_MODULE_SIG_SHA224 is not set
# CONFIG_MODULE_SIG_SHA256 is not set
# CONFIG_MODULE_SIG_SHA384 is not set
CONFIG_MODULE_SIG_SHA512=y
CONFIG_MODULE_SIG_HASH="sha512"
# CONFIG_MODULE_COMPRESS is not set
CONFIG_MODULES_TREE_LOOKUP=y
CONFIG_BLOCK=y
CONFIG_BLK_DEV_BSG=y
CONFIG_BLK_DEV_BSGLIB=y
CONFIG_BLK_DEV_INTEGRITY=y
CONFIG_BLK_DEV_THROTTLING=y
CONFIG_BLK_CMDLINE_PARSER=y

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
# CONFIG_ACORN_PARTITION is not set
CONFIG_AIX_PARTITION=y
CONFIG_OSF_PARTITION=y
CONFIG_AMIGA_PARTITION=y
CONFIG_ATARI_PARTITION=y
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
CONFIG_BSD_DISKLABEL=y
CONFIG_MINIX_SUBPARTITION=y
CONFIG_SOLARIS_X86_PARTITION=y
CONFIG_UNIXWARE_DISKLABEL=y
CONFIG_LDM_PARTITION=y
# CONFIG_LDM_DEBUG is not set
CONFIG_SGI_PARTITION=y
CONFIG_ULTRIX_PARTITION=y
CONFIG_SUN_PARTITION=y
CONFIG_KARMA_PARTITION=y
CONFIG_EFI_PARTITION=y
CONFIG_SYSV68_PARTITION=y
CONFIG_CMDLINE_PARTITION=y
CONFIG_BLOCK_COMPAT=y

#
# IO Schedulers
#
CONFIG_IOSCHED_NOOP=y
CONFIG_IOSCHED_DEADLINE=y
CONFIG_IOSCHED_CFQ=y
CONFIG_CFQ_GROUP_IOSCHED=y
CONFIG_DEFAULT_DEADLINE=y
# CONFIG_DEFAULT_CFQ is not set
# CONFIG_DEFAULT_NOOP is not set
CONFIG_DEFAULT_IOSCHED="deadline"
CONFIG_PREEMPT_NOTIFIERS=y
CONFIG_PADATA=y
CONFIG_ASN1=y
CONFIG_UNINLINE_SPIN_UNLOCK=y
CONFIG_ARCH_SUPPORTS_ATOMIC_RMW=y
CONFIG_MUTEX_SPIN_ON_OWNER=y
CONFIG_RWSEM_SPIN_ON_OWNER=y
CONFIG_LOCK_SPIN_ON_OWNER=y
CONFIG_ARCH_USE_QUEUED_SPINLOCKS=y
CONFIG_QUEUED_SPINLOCKS=y
CONFIG_ARCH_USE_QUEUED_RWLOCKS=y
CONFIG_QUEUED_RWLOCKS=y
CONFIG_FREEZER=y

#
# Processor type and features
#
# CONFIG_ZONE_DMA is not set
CONFIG_SMP=y
CONFIG_X86_FEATURE_NAMES=y
CONFIG_X86_X2APIC=y
CONFIG_X86_MPPARSE=y
CONFIG_X86_EXTENDED_PLATFORM=y
CONFIG_X86_NUMACHIP=y
# CONFIG_X86_VSMP is not set
# CONFIG_X86_UV is not set
# CONFIG_X86_GOLDFISH is not set
CONFIG_X86_INTEL_LPSS=y
CONFIG_X86_AMD_PLATFORM_DEVICE=y
CONFIG_IOSF_MBI=y
CONFIG_IOSF_MBI_DEBUG=y
CONFIG_X86_SUPPORTS_MEMORY_FAILURE=y
CONFIG_SCHED_OMIT_FRAME_POINTER=y
CONFIG_HYPERVISOR_GUEST=y
CONFIG_PARAVIRT=y
# CONFIG_PARAVIRT_DEBUG is not set
CONFIG_PARAVIRT_SPINLOCKS=y
CONFIG_XEN=y
CONFIG_XEN_DOM0=y
CONFIG_XEN_PVHVM=y
CONFIG_XEN_512GB=y
CONFIG_XEN_SAVE_RESTORE=y
# CONFIG_XEN_DEBUG_FS is not set
CONFIG_XEN_PVH=y
CONFIG_KVM_GUEST=y
CONFIG_KVM_DEBUG_FS=y
# CONFIG_PARAVIRT_TIME_ACCOUNTING is not set
CONFIG_PARAVIRT_CLOCK=y
CONFIG_NO_BOOTMEM=y
# CONFIG_MK8 is not set
# CONFIG_MPSC is not set
# CONFIG_MCORE2 is not set
# CONFIG_MATOM is not set
CONFIG_GENERIC_CPU=y
CONFIG_X86_INTERNODE_CACHE_SHIFT=6
CONFIG_X86_L1_CACHE_SHIFT=6
CONFIG_X86_TSC=y
CONFIG_X86_CMPXCHG64=y
CONFIG_X86_CMOV=y
CONFIG_X86_MINIMUM_CPU_FAMILY=64
CONFIG_X86_DEBUGCTLMSR=y
CONFIG_PROCESSOR_SELECT=y
CONFIG_CPU_SUP_INTEL=y
CONFIG_CPU_SUP_AMD=y
CONFIG_CPU_SUP_CENTAUR=y
CONFIG_HPET_TIMER=y
CONFIG_HPET_EMULATE_RTC=y
CONFIG_DMI=y
CONFIG_GART_IOMMU=y
CONFIG_CALGARY_IOMMU=y
CONFIG_CALGARY_IOMMU_ENABLED_BY_DEFAULT=y
CONFIG_SWIOTLB=y
CONFIG_IOMMU_HELPER=y
# CONFIG_MAXSMP is not set
CONFIG_NR_CPUS=256
CONFIG_SCHED_SMT=y
CONFIG_SCHED_MC=y
# CONFIG_PREEMPT_NONE is not set
# CONFIG_PREEMPT_VOLUNTARY is not set
CONFIG_PREEMPT=y
CONFIG_PREEMPT_COUNT=y
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_IO_APIC=y
CONFIG_X86_REROUTE_FOR_BROKEN_BOOT_IRQS=y
CONFIG_X86_MCE=y
CONFIG_X86_MCE_INTEL=y
CONFIG_X86_MCE_AMD=y
CONFIG_X86_MCE_THRESHOLD=y
CONFIG_X86_MCE_INJECT=m
CONFIG_X86_THERMAL_VECTOR=y
# CONFIG_VM86 is not set
CONFIG_X86_16BIT=y
CONFIG_X86_ESPFIX64=y
CONFIG_X86_VSYSCALL_EMULATION=y
CONFIG_I8K=m
CONFIG_MICROCODE=y
CONFIG_MICROCODE_INTEL=y
CONFIG_MICROCODE_AMD=y
CONFIG_MICROCODE_OLD_INTERFACE=y
CONFIG_X86_MSR=m
CONFIG_X86_CPUID=m
CONFIG_ARCH_PHYS_ADDR_T_64BIT=y
CONFIG_ARCH_DMA_ADDR_T_64BIT=y
CONFIG_X86_DIRECT_GBPAGES=y
CONFIG_NUMA=y
CONFIG_AMD_NUMA=y
CONFIG_X86_64_ACPI_NUMA=y
CONFIG_NODES_SPAN_OTHER_NODES=y
# CONFIG_NUMA_EMU is not set
CONFIG_NODES_SHIFT=6
CONFIG_ARCH_SPARSEMEM_ENABLE=y
CONFIG_ARCH_SPARSEMEM_DEFAULT=y
CONFIG_ARCH_SELECT_MEMORY_MODEL=y
CONFIG_ARCH_MEMORY_PROBE=y
CONFIG_ARCH_PROC_KCORE_TEXT=y
CONFIG_ILLEGAL_POINTER_VALUE=0xdead000000000000
CONFIG_SELECT_MEMORY_MODEL=y
CONFIG_SPARSEMEM_MANUAL=y
CONFIG_SPARSEMEM=y
CONFIG_NEED_MULTIPLE_NODES=y
CONFIG_HAVE_MEMORY_PRESENT=y
CONFIG_SPARSEMEM_EXTREME=y
CONFIG_SPARSEMEM_VMEMMAP_ENABLE=y
CONFIG_SPARSEMEM_ALLOC_MEM_MAP_TOGETHER=y
CONFIG_SPARSEMEM_VMEMMAP=y
CONFIG_HAVE_MEMBLOCK=y
CONFIG_HAVE_MEMBLOCK_NODE_MAP=y
CONFIG_ARCH_DISCARD_MEMBLOCK=y
CONFIG_MEMORY_ISOLATION=y
CONFIG_MOVABLE_NODE=y
CONFIG_HAVE_BOOTMEM_INFO_NODE=y
CONFIG_MEMORY_HOTPLUG=y
CONFIG_MEMORY_HOTPLUG_SPARSE=y
CONFIG_MEMORY_HOTREMOVE=y
CONFIG_SPLIT_PTLOCK_CPUS=4
CONFIG_ARCH_ENABLE_SPLIT_PMD_PTLOCK=y
CONFIG_MEMORY_BALLOON=y
CONFIG_BALLOON_COMPACTION=y
CONFIG_COMPACTION=y
CONFIG_MIGRATION=y
CONFIG_ARCH_ENABLE_HUGEPAGE_MIGRATION=y
CONFIG_PHYS_ADDR_T_64BIT=y
CONFIG_ZONE_DMA_FLAG=0
CONFIG_VIRT_TO_BUS=y
CONFIG_MMU_NOTIFIER=y
CONFIG_KSM=y
CONFIG_DEFAULT_MMAP_MIN_ADDR=65536
CONFIG_ARCH_SUPPORTS_MEMORY_FAILURE=y
CONFIG_MEMORY_FAILURE=y
CONFIG_HWPOISON_INJECT=m
CONFIG_TRANSPARENT_HUGEPAGE=y
CONFIG_TRANSPARENT_HUGEPAGE_ALWAYS=y
# CONFIG_TRANSPARENT_HUGEPAGE_MADVISE is not set
CONFIG_CLEANCACHE=y
CONFIG_FRONTSWAP=y
CONFIG_CMA=y
# CONFIG_CMA_DEBUG is not set
# CONFIG_CMA_DEBUGFS is not set
CONFIG_CMA_AREAS=7
CONFIG_MEM_SOFT_DIRTY=y
CONFIG_ZSWAP=y
CONFIG_ZPOOL=y
CONFIG_ZBUD=y
CONFIG_ZSMALLOC=y
CONFIG_PGTABLE_MAPPING=y
# CONFIG_ZSMALLOC_STAT is not set
CONFIG_GENERIC_EARLY_IOREMAP=y
CONFIG_ARCH_SUPPORTS_DEFERRED_STRUCT_PAGE_INIT=y
# CONFIG_DEFERRED_STRUCT_PAGE_INIT is not set
CONFIG_IDLE_PAGE_TRACKING=y
CONFIG_ZONE_DEVICE=y
CONFIG_FRAME_VECTOR=y
CONFIG_X86_PMEM_LEGACY_DEVICE=y
CONFIG_X86_PMEM_LEGACY=y
CONFIG_X86_CHECK_BIOS_CORRUPTION=y
CONFIG_X86_BOOTPARAM_MEMORY_CORRUPTION_CHECK=y
CONFIG_X86_RESERVE_LOW=64
CONFIG_MTRR=y
CONFIG_MTRR_SANITIZER=y
CONFIG_MTRR_SANITIZER_ENABLE_DEFAULT=1
CONFIG_MTRR_SANITIZER_SPARE_REG_NR_DEFAULT=1
CONFIG_X86_PAT=y
CONFIG_ARCH_USES_PG_UNCACHED=y
CONFIG_ARCH_RANDOM=y
CONFIG_X86_SMAP=y
CONFIG_X86_INTEL_MPX=y
CONFIG_EFI=y
CONFIG_EFI_STUB=y
CONFIG_EFI_MIXED=y
CONFIG_SECCOMP=y
# CONFIG_HZ_100 is not set
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ_1000=y
CONFIG_HZ=1000
CONFIG_SCHED_HRTICK=y
CONFIG_KEXEC=y
CONFIG_KEXEC_FILE=y
CONFIG_KEXEC_VERIFY_SIG=y
CONFIG_KEXEC_BZIMAGE_VERIFY_SIG=y
CONFIG_CRASH_DUMP=y
CONFIG_KEXEC_JUMP=y
CONFIG_PHYSICAL_START=0x1000000
CONFIG_RELOCATABLE=y
CONFIG_RANDOMIZE_BASE=y
CONFIG_RANDOMIZE_BASE_MAX_OFFSET=0x40000000
CONFIG_X86_NEED_RELOCS=y
CONFIG_PHYSICAL_ALIGN=0x1000000
CONFIG_HOTPLUG_CPU=y
# CONFIG_BOOTPARAM_HOTPLUG_CPU0 is not set
# CONFIG_DEBUG_HOTPLUG_CPU0 is not set
# CONFIG_COMPAT_VDSO is not set
# CONFIG_LEGACY_VSYSCALL_NATIVE is not set
CONFIG_LEGACY_VSYSCALL_EMULATE=y
# CONFIG_LEGACY_VSYSCALL_NONE is not set
# CONFIG_CMDLINE_BOOL is not set
CONFIG_MODIFY_LDT_SYSCALL=y
CONFIG_HAVE_LIVEPATCH=y
CONFIG_LIVEPATCH=y
CONFIG_ARCH_ENABLE_MEMORY_HOTPLUG=y
CONFIG_ARCH_ENABLE_MEMORY_HOTREMOVE=y
CONFIG_USE_PERCPU_NUMA_NODE_ID=y

#
# Power management and ACPI options
#
CONFIG_ARCH_HIBERNATION_HEADER=y
CONFIG_SUSPEND=y
CONFIG_SUSPEND_FREEZER=y
# CONFIG_SUSPEND_SKIP_SYNC is not set
CONFIG_HIBERNATE_CALLBACKS=y
CONFIG_HIBERNATION=y
CONFIG_PM_STD_PARTITION=""
CONFIG_PM_SLEEP=y
CONFIG_PM_SLEEP_SMP=y
# CONFIG_PM_AUTOSLEEP is not set
CONFIG_PM_WAKELOCKS=y
CONFIG_PM_WAKELOCKS_LIMIT=100
CONFIG_PM_WAKELOCKS_GC=y
CONFIG_PM=y
CONFIG_PM_DEBUG=y
CONFIG_PM_ADVANCED_DEBUG=y
# CONFIG_PM_TEST_SUSPEND is not set
CONFIG_PM_SLEEP_DEBUG=y
# CONFIG_DPM_WATCHDOG is not set
CONFIG_PM_TRACE=y
CONFIG_PM_TRACE_RTC=y
CONFIG_PM_CLK=y
CONFIG_WQ_POWER_EFFICIENT_DEFAULT=y
CONFIG_ACPI=y
CONFIG_ACPI_LEGACY_TABLES_LOOKUP=y
CONFIG_ARCH_MIGHT_HAVE_ACPI_PDC=y
CONFIG_ACPI_SYSTEM_POWER_STATES_SUPPORT=y
# CONFIG_ACPI_DEBUGGER is not set
CONFIG_ACPI_SLEEP=y
# CONFIG_ACPI_PROCFS_POWER is not set
CONFIG_ACPI_REV_OVERRIDE_POSSIBLE=y
CONFIG_ACPI_EC_DEBUGFS=m
CONFIG_ACPI_AC=y
CONFIG_ACPI_BATTERY=y
CONFIG_ACPI_BUTTON=y
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_FAN=y
CONFIG_ACPI_DOCK=y
CONFIG_ACPI_CPU_FREQ_PSS=y
CONFIG_ACPI_PROCESSOR_IDLE=y
CONFIG_ACPI_PROCESSOR=y
CONFIG_ACPI_IPMI=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_PROCESSOR_AGGREGATOR=m
CONFIG_ACPI_THERMAL=y
CONFIG_ACPI_NUMA=y
CONFIG_ACPI_CUSTOM_DSDT_FILE=""
# CONFIG_ACPI_CUSTOM_DSDT is not set
# CONFIG_ACPI_INITRD_TABLE_OVERRIDE is not set
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_PCI_SLOT=y
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=y
CONFIG_ACPI_HOTPLUG_MEMORY=y
CONFIG_ACPI_HOTPLUG_IOAPIC=y
CONFIG_ACPI_SBS=m
CONFIG_ACPI_HED=y
# CONFIG_ACPI_CUSTOM_METHOD is not set
CONFIG_ACPI_BGRT=y
# CONFIG_ACPI_REDUCED_HARDWARE_ONLY is not set
CONFIG_ACPI_NFIT=m
# CONFIG_ACPI_NFIT_DEBUG is not set
CONFIG_HAVE_ACPI_APEI=y
CONFIG_HAVE_ACPI_APEI_NMI=y
CONFIG_ACPI_APEI=y
CONFIG_ACPI_APEI_GHES=y
CONFIG_ACPI_APEI_PCIEAER=y
CONFIG_ACPI_APEI_MEMORY_FAILURE=y
CONFIG_ACPI_APEI_EINJ=m
# CONFIG_ACPI_APEI_ERST_DEBUG is not set
CONFIG_ACPI_EXTLOG=m
# CONFIG_PMIC_OPREGION is not set
CONFIG_SFI=y

#
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_GOV_COMMON=y
CONFIG_CPU_FREQ_STAT=y
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=y

#
# CPU frequency scaling drivers
#
CONFIG_X86_INTEL_PSTATE=y
CONFIG_X86_PCC_CPUFREQ=y
CONFIG_X86_ACPI_CPUFREQ=y
CONFIG_X86_ACPI_CPUFREQ_CPB=y
CONFIG_X86_POWERNOW_K8=y
CONFIG_X86_AMD_FREQ_SENSITIVITY=m
CONFIG_X86_SPEEDSTEP_CENTRINO=y
CONFIG_X86_P4_CLOCKMOD=m

#
# shared options
#
CONFIG_X86_SPEEDSTEP_LIB=m

#
# CPU Idle
#
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y
# CONFIG_ARCH_NEEDS_CPU_IDLE_COUPLED is not set
CONFIG_INTEL_IDLE=y

#
# Memory power savings
#
CONFIG_I7300_IDLE_IOAT_CHANNEL=y
CONFIG_I7300_IDLE=m

#
# Bus options (PCI etc.)
#
CONFIG_PCI=y
CONFIG_PCI_DIRECT=y
CONFIG_PCI_MMCONFIG=y
CONFIG_PCI_XEN=y
CONFIG_PCI_DOMAINS=y
# CONFIG_PCI_CNB20LE_QUIRK is not set
CONFIG_PCIEPORTBUS=y
CONFIG_HOTPLUG_PCI_PCIE=y
CONFIG_PCIEAER=y
# CONFIG_PCIE_ECRC is not set
# CONFIG_PCIEAER_INJECT is not set
CONFIG_PCIEASPM=y
CONFIG_PCIEASPM_DEBUG=y
CONFIG_PCIEASPM_DEFAULT=y
# CONFIG_PCIEASPM_POWERSAVE is not set
# CONFIG_PCIEASPM_PERFORMANCE is not set
CONFIG_PCIE_PME=y
CONFIG_PCI_BUS_ADDR_T_64BIT=y
CONFIG_PCI_MSI=y
CONFIG_PCI_MSI_IRQ_DOMAIN=y
# CONFIG_PCI_DEBUG is not set
CONFIG_PCI_REALLOC_ENABLE_AUTO=y
CONFIG_PCI_STUB=m
CONFIG_XEN_PCIDEV_FRONTEND=m
CONFIG_HT_IRQ=y
CONFIG_PCI_ATS=y
CONFIG_PCI_IOV=y
CONFIG_PCI_PRI=y
CONFIG_PCI_PASID=y
CONFIG_PCI_LABEL=y

#
# PCI host controller drivers
#
CONFIG_ISA_DMA_API=y
CONFIG_AMD_NB=y
CONFIG_PCCARD=m
CONFIG_PCMCIA=m
CONFIG_PCMCIA_LOAD_CIS=y
CONFIG_CARDBUS=y

#
# PC-card bridges
#
CONFIG_YENTA=m
CONFIG_YENTA_O2=y
CONFIG_YENTA_RICOH=y
CONFIG_YENTA_TI=y
CONFIG_YENTA_ENE_TUNE=y
CONFIG_YENTA_TOSHIBA=y
CONFIG_PD6729=m
CONFIG_I82092=m
CONFIG_PCCARD_NONSTATIC=y
CONFIG_HOTPLUG_PCI=y
CONFIG_HOTPLUG_PCI_ACPI=y
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_HOTPLUG_PCI_CPCI=y
CONFIG_HOTPLUG_PCI_CPCI_ZT5550=m
CONFIG_HOTPLUG_PCI_CPCI_GENERIC=m
CONFIG_HOTPLUG_PCI_SHPC=m
CONFIG_RAPIDIO=y
CONFIG_RAPIDIO_TSI721=m
CONFIG_RAPIDIO_DISC_TIMEOUT=30
# CONFIG_RAPIDIO_ENABLE_RX_TX_PORTS is not set
CONFIG_RAPIDIO_DMA_ENGINE=y
# CONFIG_RAPIDIO_DEBUG is not set
CONFIG_RAPIDIO_ENUM_BASIC=m

#
# RapidIO Switch drivers
#
CONFIG_RAPIDIO_TSI57X=m
CONFIG_RAPIDIO_CPS_XX=m
CONFIG_RAPIDIO_TSI568=m
CONFIG_RAPIDIO_CPS_GEN2=m
# CONFIG_X86_SYSFB is not set

#
# Executable file formats / Emulations
#
CONFIG_BINFMT_ELF=y
CONFIG_COMPAT_BINFMT_ELF=y
CONFIG_CORE_DUMP_DEFAULT_ELF_HEADERS=y
CONFIG_BINFMT_SCRIPT=y
# CONFIG_HAVE_AOUT is not set
CONFIG_BINFMT_MISC=m
CONFIG_COREDUMP=y
CONFIG_IA32_EMULATION=y
# CONFIG_IA32_AOUT is not set
CONFIG_X86_X32=y
CONFIG_COMPAT=y
CONFIG_COMPAT_FOR_U64_ALIGNMENT=y
CONFIG_SYSVIPC_COMPAT=y
CONFIG_KEYS_COMPAT=y
CONFIG_X86_DEV_DMA_OPS=y
CONFIG_PMC_ATOM=y
CONFIG_NET=y
CONFIG_COMPAT_NETLINK_MESSAGES=y
CONFIG_NET_INGRESS=y

#
# Networking options
#
CONFIG_PACKET=y
CONFIG_PACKET_DIAG=m
CONFIG_UNIX=y
CONFIG_UNIX_DIAG=m
CONFIG_XFRM=y
CONFIG_XFRM_ALGO=m
CONFIG_XFRM_USER=m
# CONFIG_XFRM_SUB_POLICY is not set
# CONFIG_XFRM_MIGRATE is not set
CONFIG_XFRM_STATISTICS=y
CONFIG_XFRM_IPCOMP=m
CONFIG_NET_KEY=m
# CONFIG_NET_KEY_MIGRATE is not set
CONFIG_INET=y
CONFIG_IP_MULTICAST=y
CONFIG_IP_ADVANCED_ROUTER=y
CONFIG_IP_FIB_TRIE_STATS=y
CONFIG_IP_MULTIPLE_TABLES=y
CONFIG_IP_ROUTE_MULTIPATH=y
CONFIG_IP_ROUTE_VERBOSE=y
CONFIG_IP_ROUTE_CLASSID=y
CONFIG_IP_PNP=y
CONFIG_IP_PNP_DHCP=y
# CONFIG_IP_PNP_BOOTP is not set
# CONFIG_IP_PNP_RARP is not set
CONFIG_NET_IPIP=m
CONFIG_NET_IPGRE_DEMUX=m
CONFIG_NET_IP_TUNNEL=m
CONFIG_NET_IPGRE=m
CONFIG_NET_IPGRE_BROADCAST=y
CONFIG_IP_MROUTE=y
# CONFIG_IP_MROUTE_MULTIPLE_TABLES is not set
CONFIG_IP_PIMSM_V1=y
CONFIG_IP_PIMSM_V2=y
CONFIG_SYN_COOKIES=y
CONFIG_NET_IPVTI=m
CONFIG_NET_UDP_TUNNEL=m
CONFIG_NET_FOU=m
CONFIG_NET_FOU_IP_TUNNELS=y
CONFIG_INET_AH=m
CONFIG_INET_ESP=m
CONFIG_INET_IPCOMP=m
CONFIG_INET_XFRM_TUNNEL=m
CONFIG_INET_TUNNEL=m
CONFIG_INET_XFRM_MODE_TRANSPORT=m
CONFIG_INET_XFRM_MODE_TUNNEL=m
CONFIG_INET_XFRM_MODE_BEET=m
CONFIG_INET_LRO=y
CONFIG_INET_DIAG=m
CONFIG_INET_TCP_DIAG=m
CONFIG_INET_UDP_DIAG=m
CONFIG_TCP_CONG_ADVANCED=y
CONFIG_TCP_CONG_BIC=m
CONFIG_TCP_CONG_CUBIC=y
CONFIG_TCP_CONG_WESTWOOD=m
CONFIG_TCP_CONG_HTCP=m
CONFIG_TCP_CONG_HSTCP=m
CONFIG_TCP_CONG_HYBLA=m
CONFIG_TCP_CONG_VEGAS=m
CONFIG_TCP_CONG_SCALABLE=m
CONFIG_TCP_CONG_LP=m
CONFIG_TCP_CONG_VENO=m
CONFIG_TCP_CONG_YEAH=m
CONFIG_TCP_CONG_ILLINOIS=m
CONFIG_TCP_CONG_DCTCP=m
CONFIG_TCP_CONG_CDG=m
CONFIG_DEFAULT_CUBIC=y
# CONFIG_DEFAULT_RENO is not set
CONFIG_DEFAULT_TCP_CONG="cubic"
CONFIG_TCP_MD5SIG=y
CONFIG_IPV6=y
CONFIG_IPV6_ROUTER_PREF=y
CONFIG_IPV6_ROUTE_INFO=y
# CONFIG_IPV6_OPTIMISTIC_DAD is not set
CONFIG_INET6_AH=m
CONFIG_INET6_ESP=m
CONFIG_INET6_IPCOMP=m
CONFIG_IPV6_MIP6=m
CONFIG_IPV6_ILA=m
CONFIG_INET6_XFRM_TUNNEL=m
CONFIG_INET6_TUNNEL=m
CONFIG_INET6_XFRM_MODE_TRANSPORT=m
CONFIG_INET6_XFRM_MODE_TUNNEL=m
CONFIG_INET6_XFRM_MODE_BEET=m
CONFIG_INET6_XFRM_MODE_ROUTEOPTIMIZATION=m
CONFIG_IPV6_VTI=m
CONFIG_IPV6_SIT=m
CONFIG_IPV6_SIT_6RD=y
CONFIG_IPV6_NDISC_NODETYPE=y
CONFIG_IPV6_TUNNEL=m
CONFIG_IPV6_GRE=m
CONFIG_IPV6_MULTIPLE_TABLES=y
CONFIG_IPV6_SUBTREES=y
CONFIG_IPV6_MROUTE=y
CONFIG_IPV6_MROUTE_MULTIPLE_TABLES=y
CONFIG_IPV6_PIMSM_V2=y
CONFIG_NETLABEL=y
CONFIG_NETWORK_SECMARK=y
CONFIG_NET_PTP_CLASSIFY=y
# CONFIG_NETWORK_PHY_TIMESTAMPING is not set
CONFIG_NETFILTER=y
# CONFIG_NETFILTER_DEBUG is not set
CONFIG_NETFILTER_ADVANCED=y
CONFIG_BRIDGE_NETFILTER=m

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_INGRESS=y
CONFIG_NETFILTER_NETLINK=m
CONFIG_NETFILTER_NETLINK_ACCT=m
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NF_CONNTRACK=m
CONFIG_NF_LOG_COMMON=m
CONFIG_NF_CONNTRACK_MARK=y
CONFIG_NF_CONNTRACK_SECMARK=y
CONFIG_NF_CONNTRACK_ZONES=y
# CONFIG_NF_CONNTRACK_PROCFS is not set
CONFIG_NF_CONNTRACK_EVENTS=y
CONFIG_NF_CONNTRACK_TIMEOUT=y
CONFIG_NF_CONNTRACK_TIMESTAMP=y
CONFIG_NF_CONNTRACK_LABELS=y
CONFIG_NF_CT_PROTO_DCCP=m
CONFIG_NF_CT_PROTO_GRE=m
CONFIG_NF_CT_PROTO_SCTP=m
CONFIG_NF_CT_PROTO_UDPLITE=m
CONFIG_NF_CONNTRACK_AMANDA=m
CONFIG_NF_CONNTRACK_FTP=m
CONFIG_NF_CONNTRACK_H323=m
CONFIG_NF_CONNTRACK_IRC=m
CONFIG_NF_CONNTRACK_BROADCAST=m
CONFIG_NF_CONNTRACK_NETBIOS_NS=m
CONFIG_NF_CONNTRACK_SNMP=m
CONFIG_NF_CONNTRACK_PPTP=m
CONFIG_NF_CONNTRACK_SANE=m
CONFIG_NF_CONNTRACK_SIP=m
CONFIG_NF_CONNTRACK_TFTP=m
CONFIG_NF_CT_NETLINK=m
CONFIG_NF_CT_NETLINK_TIMEOUT=m
CONFIG_NF_CT_NETLINK_HELPER=m
CONFIG_NETFILTER_NETLINK_GLUE_CT=y
CONFIG_NF_NAT=m
CONFIG_NF_NAT_NEEDED=y
CONFIG_NF_NAT_PROTO_DCCP=m
CONFIG_NF_NAT_PROTO_UDPLITE=m
CONFIG_NF_NAT_PROTO_SCTP=m
CONFIG_NF_NAT_AMANDA=m
CONFIG_NF_NAT_FTP=m
CONFIG_NF_NAT_IRC=m
CONFIG_NF_NAT_SIP=m
CONFIG_NF_NAT_TFTP=m
CONFIG_NF_NAT_REDIRECT=m
CONFIG_NETFILTER_SYNPROXY=m
CONFIG_NF_TABLES=m
CONFIG_NF_TABLES_INET=m
CONFIG_NF_TABLES_NETDEV=m
CONFIG_NFT_EXTHDR=m
CONFIG_NFT_META=m
CONFIG_NFT_CT=m
CONFIG_NFT_RBTREE=m
CONFIG_NFT_HASH=m
CONFIG_NFT_COUNTER=m
CONFIG_NFT_LOG=m
CONFIG_NFT_LIMIT=m
CONFIG_NFT_MASQ=m
CONFIG_NFT_REDIR=m
CONFIG_NFT_NAT=m
CONFIG_NFT_QUEUE=m
CONFIG_NFT_REJECT=m
CONFIG_NFT_REJECT_INET=m
CONFIG_NFT_COMPAT=m
CONFIG_NETFILTER_XTABLES=m

#
# Xtables combined modules
#
CONFIG_NETFILTER_XT_MARK=m
CONFIG_NETFILTER_XT_CONNMARK=m
CONFIG_NETFILTER_XT_SET=m

#
# Xtables targets
#
CONFIG_NETFILTER_XT_TARGET_AUDIT=m
CONFIG_NETFILTER_XT_TARGET_CHECKSUM=m
CONFIG_NETFILTER_XT_TARGET_CLASSIFY=m
CONFIG_NETFILTER_XT_TARGET_CONNMARK=m
CONFIG_NETFILTER_XT_TARGET_CONNSECMARK=m
CONFIG_NETFILTER_XT_TARGET_CT=m
CONFIG_NETFILTER_XT_TARGET_DSCP=m
CONFIG_NETFILTER_XT_TARGET_HL=m
CONFIG_NETFILTER_XT_TARGET_HMARK=m
CONFIG_NETFILTER_XT_TARGET_IDLETIMER=m
CONFIG_NETFILTER_XT_TARGET_LED=m
CONFIG_NETFILTER_XT_TARGET_LOG=m
CONFIG_NETFILTER_XT_TARGET_MARK=m
CONFIG_NETFILTER_XT_NAT=m
CONFIG_NETFILTER_XT_TARGET_NETMAP=m
CONFIG_NETFILTER_XT_TARGET_NFLOG=m
CONFIG_NETFILTER_XT_TARGET_NFQUEUE=m
# CONFIG_NETFILTER_XT_TARGET_NOTRACK is not set
CONFIG_NETFILTER_XT_TARGET_RATEEST=m
CONFIG_NETFILTER_XT_TARGET_REDIRECT=m
CONFIG_NETFILTER_XT_TARGET_TEE=m
CONFIG_NETFILTER_XT_TARGET_TPROXY=m
CONFIG_NETFILTER_XT_TARGET_TRACE=m
CONFIG_NETFILTER_XT_TARGET_SECMARK=m
CONFIG_NETFILTER_XT_TARGET_TCPMSS=m
CONFIG_NETFILTER_XT_TARGET_TCPOPTSTRIP=m

#
# Xtables matches
#
CONFIG_NETFILTER_XT_MATCH_ADDRTYPE=m
CONFIG_NETFILTER_XT_MATCH_BPF=m
CONFIG_NETFILTER_XT_MATCH_CGROUP=m
CONFIG_NETFILTER_XT_MATCH_CLUSTER=m
CONFIG_NETFILTER_XT_MATCH_COMMENT=m
CONFIG_NETFILTER_XT_MATCH_CONNBYTES=m
CONFIG_NETFILTER_XT_MATCH_CONNLABEL=m
CONFIG_NETFILTER_XT_MATCH_CONNLIMIT=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
CONFIG_NETFILTER_XT_MATCH_CPU=m
CONFIG_NETFILTER_XT_MATCH_DCCP=m
CONFIG_NETFILTER_XT_MATCH_DEVGROUP=m
CONFIG_NETFILTER_XT_MATCH_DSCP=m
CONFIG_NETFILTER_XT_MATCH_ECN=m
CONFIG_NETFILTER_XT_MATCH_ESP=m
CONFIG_NETFILTER_XT_MATCH_HASHLIMIT=m
CONFIG_NETFILTER_XT_MATCH_HELPER=m
CONFIG_NETFILTER_XT_MATCH_HL=m
CONFIG_NETFILTER_XT_MATCH_IPCOMP=m
CONFIG_NETFILTER_XT_MATCH_IPRANGE=m
CONFIG_NETFILTER_XT_MATCH_IPVS=m
CONFIG_NETFILTER_XT_MATCH_L2TP=m
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
CONFIG_NETFILTER_XT_MATCH_MULTIPORT=m
CONFIG_NETFILTER_XT_MATCH_NFACCT=m
CONFIG_NETFILTER_XT_MATCH_OSF=m
CONFIG_NETFILTER_XT_MATCH_OWNER=m
CONFIG_NETFILTER_XT_MATCH_POLICY=m
CONFIG_NETFILTER_XT_MATCH_PHYSDEV=m
CONFIG_NETFILTER_XT_MATCH_PKTTYPE=m
CONFIG_NETFILTER_XT_MATCH_QUOTA=m
CONFIG_NETFILTER_XT_MATCH_RATEEST=m
CONFIG_NETFILTER_XT_MATCH_REALM=m
CONFIG_NETFILTER_XT_MATCH_RECENT=m
CONFIG_NETFILTER_XT_MATCH_SCTP=m
CONFIG_NETFILTER_XT_MATCH_SOCKET=m
CONFIG_NETFILTER_XT_MATCH_STATE=m
CONFIG_NETFILTER_XT_MATCH_STATISTIC=m
CONFIG_NETFILTER_XT_MATCH_STRING=m
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m
CONFIG_NETFILTER_XT_MATCH_TIME=m
CONFIG_NETFILTER_XT_MATCH_U32=m
CONFIG_IP_SET=m
CONFIG_IP_SET_MAX=256
CONFIG_IP_SET_BITMAP_IP=m
CONFIG_IP_SET_BITMAP_IPMAC=m
CONFIG_IP_SET_BITMAP_PORT=m
CONFIG_IP_SET_HASH_IP=m
CONFIG_IP_SET_HASH_IPMARK=m
CONFIG_IP_SET_HASH_IPPORT=m
CONFIG_IP_SET_HASH_IPPORTIP=m
CONFIG_IP_SET_HASH_IPPORTNET=m
CONFIG_IP_SET_HASH_MAC=m
CONFIG_IP_SET_HASH_NETPORTNET=m
CONFIG_IP_SET_HASH_NET=m
CONFIG_IP_SET_HASH_NETNET=m
CONFIG_IP_SET_HASH_NETPORT=m
CONFIG_IP_SET_HASH_NETIFACE=m
CONFIG_IP_SET_LIST_SET=m
CONFIG_IP_VS=m
CONFIG_IP_VS_IPV6=y
# CONFIG_IP_VS_DEBUG is not set
CONFIG_IP_VS_TAB_BITS=12

#
# IPVS transport protocol load balancing support
#
CONFIG_IP_VS_PROTO_TCP=y
CONFIG_IP_VS_PROTO_UDP=y
CONFIG_IP_VS_PROTO_AH_ESP=y
CONFIG_IP_VS_PROTO_ESP=y
CONFIG_IP_VS_PROTO_AH=y
CONFIG_IP_VS_PROTO_SCTP=y

#
# IPVS scheduler
#
CONFIG_IP_VS_RR=m
CONFIG_IP_VS_WRR=m
CONFIG_IP_VS_LC=m
CONFIG_IP_VS_WLC=m
CONFIG_IP_VS_FO=m
CONFIG_IP_VS_OVF=m
CONFIG_IP_VS_LBLC=m
CONFIG_IP_VS_LBLCR=m
CONFIG_IP_VS_DH=m
CONFIG_IP_VS_SH=m
CONFIG_IP_VS_SED=m
CONFIG_IP_VS_NQ=m

#
# IPVS SH scheduler
#
CONFIG_IP_VS_SH_TAB_BITS=8

#
# IPVS application helper
#
CONFIG_IP_VS_FTP=m
CONFIG_IP_VS_NFCT=y
CONFIG_IP_VS_PE_SIP=m

#
# IP: Netfilter Configuration
#
CONFIG_NF_DEFRAG_IPV4=m
CONFIG_NF_CONNTRACK_IPV4=m
CONFIG_NF_TABLES_IPV4=m
CONFIG_NFT_CHAIN_ROUTE_IPV4=m
CONFIG_NFT_REJECT_IPV4=m
CONFIG_NFT_DUP_IPV4=m
CONFIG_NF_TABLES_ARP=m
CONFIG_NF_DUP_IPV4=m
CONFIG_NF_LOG_ARP=m
CONFIG_NF_LOG_IPV4=m
CONFIG_NF_REJECT_IPV4=m
CONFIG_NF_NAT_IPV4=m
CONFIG_NFT_CHAIN_NAT_IPV4=m
CONFIG_NF_NAT_MASQUERADE_IPV4=m
CONFIG_NFT_MASQ_IPV4=m
CONFIG_NFT_REDIR_IPV4=m
CONFIG_NF_NAT_SNMP_BASIC=m
CONFIG_NF_NAT_PROTO_GRE=m
CONFIG_NF_NAT_PPTP=m
CONFIG_NF_NAT_H323=m
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_AH=m
CONFIG_IP_NF_MATCH_ECN=m
CONFIG_IP_NF_MATCH_RPFILTER=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_SYNPROXY=m
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_NETMAP=m
CONFIG_IP_NF_TARGET_REDIRECT=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_CLUSTERIP=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_SECURITY=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m

#
# IPv6: Netfilter Configuration
#
CONFIG_NF_DEFRAG_IPV6=m
CONFIG_NF_CONNTRACK_IPV6=m
CONFIG_NF_TABLES_IPV6=m
CONFIG_NFT_CHAIN_ROUTE_IPV6=m
CONFIG_NFT_REJECT_IPV6=m
CONFIG_NFT_DUP_IPV6=m
CONFIG_NF_DUP_IPV6=m
CONFIG_NF_REJECT_IPV6=m
CONFIG_NF_LOG_IPV6=m
CONFIG_NF_NAT_IPV6=m
CONFIG_NFT_CHAIN_NAT_IPV6=m
CONFIG_NF_NAT_MASQUERADE_IPV6=m
CONFIG_NFT_MASQ_IPV6=m
CONFIG_NFT_REDIR_IPV6=m
CONFIG_IP6_NF_IPTABLES=m
CONFIG_IP6_NF_MATCH_AH=m
CONFIG_IP6_NF_MATCH_EUI64=m
CONFIG_IP6_NF_MATCH_FRAG=m
CONFIG_IP6_NF_MATCH_OPTS=m
CONFIG_IP6_NF_MATCH_HL=m
CONFIG_IP6_NF_MATCH_IPV6HEADER=m
CONFIG_IP6_NF_MATCH_MH=m
CONFIG_IP6_NF_MATCH_RPFILTER=m
CONFIG_IP6_NF_MATCH_RT=m
CONFIG_IP6_NF_TARGET_HL=m
CONFIG_IP6_NF_FILTER=m
CONFIG_IP6_NF_TARGET_REJECT=m
CONFIG_IP6_NF_TARGET_SYNPROXY=m
CONFIG_IP6_NF_MANGLE=m
CONFIG_IP6_NF_RAW=m
CONFIG_IP6_NF_SECURITY=m
CONFIG_IP6_NF_NAT=m
CONFIG_IP6_NF_TARGET_MASQUERADE=m
CONFIG_IP6_NF_TARGET_NPT=m

#
# DECnet: Netfilter Configuration
#
CONFIG_DECNET_NF_GRABULATOR=m
CONFIG_NF_TABLES_BRIDGE=m
CONFIG_NFT_BRIDGE_META=m
CONFIG_NFT_BRIDGE_REJECT=m
CONFIG_NF_LOG_BRIDGE=m
CONFIG_BRIDGE_NF_EBTABLES=m
CONFIG_BRIDGE_EBT_BROUTE=m
CONFIG_BRIDGE_EBT_T_FILTER=m
CONFIG_BRIDGE_EBT_T_NAT=m
CONFIG_BRIDGE_EBT_802_3=m
CONFIG_BRIDGE_EBT_AMONG=m
CONFIG_BRIDGE_EBT_ARP=m
CONFIG_BRIDGE_EBT_IP=m
CONFIG_BRIDGE_EBT_IP6=m
CONFIG_BRIDGE_EBT_LIMIT=m
CONFIG_BRIDGE_EBT_MARK=m
CONFIG_BRIDGE_EBT_PKTTYPE=m
CONFIG_BRIDGE_EBT_STP=m
CONFIG_BRIDGE_EBT_VLAN=m
CONFIG_BRIDGE_EBT_ARPREPLY=m
CONFIG_BRIDGE_EBT_DNAT=m
CONFIG_BRIDGE_EBT_MARK_T=m
CONFIG_BRIDGE_EBT_REDIRECT=m
CONFIG_BRIDGE_EBT_SNAT=m
CONFIG_BRIDGE_EBT_LOG=m
CONFIG_BRIDGE_EBT_NFLOG=m
CONFIG_IP_DCCP=m
CONFIG_INET_DCCP_DIAG=m

#
# DCCP CCIDs Configuration
#
# CONFIG_IP_DCCP_CCID2_DEBUG is not set
# CONFIG_IP_DCCP_CCID3 is not set

#
# DCCP Kernel Hacking
#
# CONFIG_IP_DCCP_DEBUG is not set
CONFIG_NET_DCCPPROBE=m
CONFIG_IP_SCTP=m
CONFIG_NET_SCTPPROBE=m
# CONFIG_SCTP_DBG_OBJCNT is not set
# CONFIG_SCTP_DEFAULT_COOKIE_HMAC_MD5 is not set
CONFIG_SCTP_DEFAULT_COOKIE_HMAC_SHA1=y
# CONFIG_SCTP_DEFAULT_COOKIE_HMAC_NONE is not set
CONFIG_SCTP_COOKIE_HMAC_MD5=y
CONFIG_SCTP_COOKIE_HMAC_SHA1=y
CONFIG_RDS=m
CONFIG_RDS_RDMA=m
CONFIG_RDS_TCP=m
# CONFIG_RDS_DEBUG is not set
CONFIG_TIPC=m
CONFIG_TIPC_MEDIA_IB=y
CONFIG_TIPC_MEDIA_UDP=y
CONFIG_ATM=m
CONFIG_ATM_CLIP=m
# CONFIG_ATM_CLIP_NO_ICMP is not set
CONFIG_ATM_LANE=m
CONFIG_ATM_MPOA=m
CONFIG_ATM_BR2684=m
# CONFIG_ATM_BR2684_IPFILTER is not set
CONFIG_L2TP=m
CONFIG_L2TP_DEBUGFS=m
CONFIG_L2TP_V3=y
CONFIG_L2TP_IP=m
CONFIG_L2TP_ETH=m
CONFIG_STP=m
CONFIG_GARP=m
CONFIG_MRP=m
CONFIG_BRIDGE=m
CONFIG_BRIDGE_IGMP_SNOOPING=y
CONFIG_BRIDGE_VLAN_FILTERING=y
CONFIG_HAVE_NET_DSA=y
CONFIG_VLAN_8021Q=m
CONFIG_VLAN_8021Q_GVRP=y
CONFIG_VLAN_8021Q_MVRP=y
CONFIG_DECNET=m
# CONFIG_DECNET_ROUTER is not set
CONFIG_LLC=m
CONFIG_LLC2=m
CONFIG_IPX=m
# CONFIG_IPX_INTERN is not set
CONFIG_ATALK=m
CONFIG_DEV_APPLETALK=m
CONFIG_IPDDP=m
CONFIG_IPDDP_ENCAP=y
CONFIG_X25=m
CONFIG_LAPB=m
CONFIG_PHONET=m
CONFIG_6LOWPAN=m
CONFIG_6LOWPAN_NHC=m
CONFIG_6LOWPAN_NHC_DEST=m
CONFIG_6LOWPAN_NHC_FRAGMENT=m
CONFIG_6LOWPAN_NHC_HOP=m
CONFIG_6LOWPAN_NHC_IPV6=m
CONFIG_6LOWPAN_NHC_MOBILITY=m
CONFIG_6LOWPAN_NHC_ROUTING=m
CONFIG_6LOWPAN_NHC_UDP=m
CONFIG_IEEE802154=m
CONFIG_IEEE802154_NL802154_EXPERIMENTAL=y
CONFIG_IEEE802154_SOCKET=m
CONFIG_IEEE802154_6LOWPAN=m
CONFIG_MAC802154=m
CONFIG_NET_SCHED=y

#
# Queueing/Scheduling
#
CONFIG_NET_SCH_CBQ=m
CONFIG_NET_SCH_HTB=m
CONFIG_NET_SCH_HFSC=m
CONFIG_NET_SCH_ATM=m
CONFIG_NET_SCH_PRIO=m
CONFIG_NET_SCH_MULTIQ=m
CONFIG_NET_SCH_RED=m
CONFIG_NET_SCH_SFB=m
CONFIG_NET_SCH_SFQ=m
CONFIG_NET_SCH_TEQL=m
CONFIG_NET_SCH_TBF=m
CONFIG_NET_SCH_GRED=m
CONFIG_NET_SCH_DSMARK=m
CONFIG_NET_SCH_NETEM=m
CONFIG_NET_SCH_DRR=m
CONFIG_NET_SCH_MQPRIO=m
CONFIG_NET_SCH_CHOKE=m
CONFIG_NET_SCH_QFQ=m
CONFIG_NET_SCH_CODEL=m
CONFIG_NET_SCH_FQ_CODEL=m
CONFIG_NET_SCH_FQ=m
CONFIG_NET_SCH_HHF=m
CONFIG_NET_SCH_PIE=m
CONFIG_NET_SCH_INGRESS=m
CONFIG_NET_SCH_PLUG=m

#
# Classification
#
CONFIG_NET_CLS=y
CONFIG_NET_CLS_BASIC=m
CONFIG_NET_CLS_TCINDEX=m
CONFIG_NET_CLS_ROUTE4=m
CONFIG_NET_CLS_FW=m
CONFIG_NET_CLS_U32=m
# CONFIG_CLS_U32_PERF is not set
CONFIG_CLS_U32_MARK=y
CONFIG_NET_CLS_RSVP=m
CONFIG_NET_CLS_RSVP6=m
CONFIG_NET_CLS_FLOW=m
CONFIG_NET_CLS_CGROUP=m
CONFIG_NET_CLS_BPF=m
CONFIG_NET_CLS_FLOWER=m
CONFIG_NET_EMATCH=y
CONFIG_NET_EMATCH_STACK=32
CONFIG_NET_EMATCH_CMP=m
CONFIG_NET_EMATCH_NBYTE=m
CONFIG_NET_EMATCH_U32=m
CONFIG_NET_EMATCH_META=m
CONFIG_NET_EMATCH_TEXT=m
CONFIG_NET_EMATCH_CANID=m
CONFIG_NET_EMATCH_IPSET=m
CONFIG_NET_CLS_ACT=y
CONFIG_NET_ACT_POLICE=m
CONFIG_NET_ACT_GACT=m
CONFIG_GACT_PROB=y
CONFIG_NET_ACT_MIRRED=m
CONFIG_NET_ACT_IPT=m
CONFIG_NET_ACT_NAT=m
CONFIG_NET_ACT_PEDIT=m
CONFIG_NET_ACT_SIMP=m
CONFIG_NET_ACT_SKBEDIT=m
CONFIG_NET_ACT_CSUM=m
CONFIG_NET_ACT_VLAN=m
CONFIG_NET_ACT_BPF=m
CONFIG_NET_ACT_CONNMARK=m
# CONFIG_NET_CLS_IND is not set
CONFIG_NET_SCH_FIFO=y
CONFIG_DCB=y
CONFIG_DNS_RESOLVER=y
CONFIG_BATMAN_ADV=m
CONFIG_BATMAN_ADV_BLA=y
CONFIG_BATMAN_ADV_DAT=y
CONFIG_BATMAN_ADV_NC=y
CONFIG_BATMAN_ADV_MCAST=y
# CONFIG_BATMAN_ADV_DEBUG is not set
CONFIG_OPENVSWITCH=m
CONFIG_OPENVSWITCH_GRE=m
CONFIG_OPENVSWITCH_VXLAN=m
CONFIG_OPENVSWITCH_GENEVE=m
CONFIG_VSOCKETS=m
CONFIG_VMWARE_VMCI_VSOCKETS=m
CONFIG_NETLINK_MMAP=y
CONFIG_NETLINK_DIAG=m
CONFIG_MPLS=y
CONFIG_NET_MPLS_GSO=m
CONFIG_MPLS_ROUTING=m
CONFIG_MPLS_IPTUNNEL=m
CONFIG_HSR=m
# CONFIG_NET_SWITCHDEV is not set
CONFIG_NET_L3_MASTER_DEV=y
CONFIG_RPS=y
CONFIG_RFS_ACCEL=y
CONFIG_XPS=y
CONFIG_CGROUP_NET_PRIO=y
CONFIG_CGROUP_NET_CLASSID=y
CONFIG_NET_RX_BUSY_POLL=y
CONFIG_BQL=y
CONFIG_BPF_JIT=y
CONFIG_NET_FLOW_LIMIT=y

#
# Network testing
#
CONFIG_NET_PKTGEN=m
CONFIG_NET_TCPPROBE=m
# CONFIG_NET_DROP_MONITOR is not set
CONFIG_HAMRADIO=y

#
# Packet Radio protocols
#
CONFIG_AX25=m
CONFIG_AX25_DAMA_SLAVE=y
CONFIG_NETROM=m
CONFIG_ROSE=m

#
# AX.25 network device drivers
#
CONFIG_MKISS=m
CONFIG_6PACK=m
CONFIG_BPQETHER=m
CONFIG_BAYCOM_SER_FDX=m
CONFIG_BAYCOM_SER_HDX=m
CONFIG_BAYCOM_PAR=m
CONFIG_YAM=m
CONFIG_CAN=m
CONFIG_CAN_RAW=m
CONFIG_CAN_BCM=m
CONFIG_CAN_GW=m

#
# CAN Device Drivers
#
CONFIG_CAN_VCAN=m
CONFIG_CAN_SLCAN=m
CONFIG_CAN_DEV=m
CONFIG_CAN_CALC_BITTIMING=y
CONFIG_CAN_LEDS=y
CONFIG_CAN_JANZ_ICAN3=m
CONFIG_CAN_SJA1000=m
CONFIG_CAN_SJA1000_ISA=m
CONFIG_CAN_SJA1000_PLATFORM=m
CONFIG_CAN_EMS_PCMCIA=m
CONFIG_CAN_EMS_PCI=m
CONFIG_CAN_PEAK_PCMCIA=m
CONFIG_CAN_PEAK_PCI=m
CONFIG_CAN_PEAK_PCIEC=y
CONFIG_CAN_KVASER_PCI=m
CONFIG_CAN_PLX_PCI=m
CONFIG_CAN_C_CAN=m
CONFIG_CAN_C_CAN_PLATFORM=m
CONFIG_CAN_C_CAN_PCI=m
CONFIG_CAN_M_CAN=m
CONFIG_CAN_CC770=m
CONFIG_CAN_CC770_ISA=m
CONFIG_CAN_CC770_PLATFORM=m

#
# CAN SPI interfaces
#
CONFIG_CAN_MCP251X=m

#
# CAN USB interfaces
#
CONFIG_CAN_EMS_USB=m
CONFIG_CAN_ESD_USB2=m
CONFIG_CAN_GS_USB=m
CONFIG_CAN_KVASER_USB=m
CONFIG_CAN_PEAK_USB=m
CONFIG_CAN_8DEV_USB=m
CONFIG_CAN_SOFTING=m
CONFIG_CAN_SOFTING_CS=m
# CONFIG_CAN_DEBUG_DEVICES is not set
CONFIG_IRDA=m

#
# IrDA protocols
#
CONFIG_IRLAN=m
CONFIG_IRNET=m
CONFIG_IRCOMM=m
CONFIG_IRDA_ULTRA=y

#
# IrDA options
#
CONFIG_IRDA_CACHE_LAST_LSAP=y
CONFIG_IRDA_FAST_RR=y
# CONFIG_IRDA_DEBUG is not set

#
# Infrared-port device drivers
#

#
# SIR device drivers
#
CONFIG_IRTTY_SIR=m

#
# Dongle support
#
CONFIG_DONGLE=y
CONFIG_ESI_DONGLE=m
CONFIG_ACTISYS_DONGLE=m
CONFIG_TEKRAM_DONGLE=m
CONFIG_TOIM3232_DONGLE=m
CONFIG_LITELINK_DONGLE=m
CONFIG_MA600_DONGLE=m
CONFIG_GIRBIL_DONGLE=m
CONFIG_MCP2120_DONGLE=m
CONFIG_OLD_BELKIN_DONGLE=m
CONFIG_ACT200L_DONGLE=m
CONFIG_KINGSUN_DONGLE=m
CONFIG_KSDAZZLE_DONGLE=m
CONFIG_KS959_DONGLE=m

#
# FIR device drivers
#
CONFIG_USB_IRDA=m
CONFIG_SIGMATEL_FIR=m
CONFIG_NSC_FIR=m
CONFIG_WINBOND_FIR=m
CONFIG_SMC_IRCC_FIR=m
CONFIG_ALI_FIR=m
CONFIG_VLSI_FIR=m
CONFIG_VIA_FIR=m
CONFIG_MCS_FIR=m
CONFIG_BT=m
CONFIG_BT_BREDR=y
CONFIG_BT_RFCOMM=m
CONFIG_BT_RFCOMM_TTY=y
CONFIG_BT_BNEP=m
CONFIG_BT_BNEP_MC_FILTER=y
CONFIG_BT_BNEP_PROTO_FILTER=y
CONFIG_BT_CMTP=m
CONFIG_BT_HIDP=m
CONFIG_BT_HS=y
CONFIG_BT_LE=y
CONFIG_BT_6LOWPAN=m
# CONFIG_BT_SELFTEST is not set
CONFIG_BT_DEBUGFS=y

#
# Bluetooth device drivers
#
CONFIG_BT_INTEL=m
CONFIG_BT_BCM=m
CONFIG_BT_RTL=m
CONFIG_BT_QCA=m
CONFIG_BT_HCIBTUSB=m
CONFIG_BT_HCIBTUSB_BCM=y
CONFIG_BT_HCIBTUSB_RTL=y
CONFIG_BT_HCIBTSDIO=m
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIUART_ATH3K=y
CONFIG_BT_HCIUART_LL=y
CONFIG_BT_HCIUART_3WIRE=y
CONFIG_BT_HCIUART_INTEL=y
CONFIG_BT_HCIUART_BCM=y
CONFIG_BT_HCIUART_QCA=y
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIDTL1=m
CONFIG_BT_HCIBT3C=m
CONFIG_BT_HCIBLUECARD=m
CONFIG_BT_HCIBTUART=m
CONFIG_BT_HCIVHCI=m
CONFIG_BT_MRVL=m
CONFIG_BT_MRVL_SDIO=m
CONFIG_BT_ATH3K=m
CONFIG_BT_WILINK=m
CONFIG_AF_RXRPC=m
# CONFIG_AF_RXRPC_DEBUG is not set
CONFIG_RXKAD=m
CONFIG_FIB_RULES=y
CONFIG_WIRELESS=y
CONFIG_WIRELESS_EXT=y
CONFIG_WEXT_CORE=y
CONFIG_WEXT_PROC=y
CONFIG_WEXT_SPY=y
CONFIG_WEXT_PRIV=y
CONFIG_CFG80211=m
# CONFIG_NL80211_TESTMODE is not set
# CONFIG_CFG80211_DEVELOPER_WARNINGS is not set
# CONFIG_CFG80211_REG_DEBUG is not set
# CONFIG_CFG80211_CERTIFICATION_ONUS is not set
CONFIG_CFG80211_DEFAULT_PS=y
CONFIG_CFG80211_DEBUGFS=y
# CONFIG_CFG80211_INTERNAL_REGDB is not set
CONFIG_CFG80211_CRDA_SUPPORT=y
CONFIG_CFG80211_WEXT=y
CONFIG_CFG80211_WEXT_EXPORT=y
CONFIG_LIB80211=m
CONFIG_LIB80211_CRYPT_WEP=m
CONFIG_LIB80211_CRYPT_CCMP=m
CONFIG_LIB80211_CRYPT_TKIP=m
# CONFIG_LIB80211_DEBUG is not set
CONFIG_MAC80211=m
CONFIG_MAC80211_HAS_RC=y
CONFIG_MAC80211_RC_MINSTREL=y
CONFIG_MAC80211_RC_MINSTREL_HT=y
CONFIG_MAC80211_RC_MINSTREL_VHT=y
CONFIG_MAC80211_RC_DEFAULT_MINSTREL=y
CONFIG_MAC80211_RC_DEFAULT="minstrel_ht"
CONFIG_MAC80211_MESH=y
CONFIG_MAC80211_LEDS=y
CONFIG_MAC80211_DEBUGFS=y
CONFIG_MAC80211_MESSAGE_TRACING=y
# CONFIG_MAC80211_DEBUG_MENU is not set
CONFIG_MAC80211_STA_HASH_MAX_SIZE=0
CONFIG_WIMAX=m
CONFIG_WIMAX_DEBUG_LEVEL=8
CONFIG_RFKILL=y
CONFIG_RFKILL_LEDS=y
CONFIG_RFKILL_INPUT=y
CONFIG_RFKILL_REGULATOR=m
CONFIG_RFKILL_GPIO=m
CONFIG_NET_9P=m
CONFIG_NET_9P_VIRTIO=m
CONFIG_NET_9P_RDMA=m
# CONFIG_NET_9P_DEBUG is not set
CONFIG_CAIF=m
# CONFIG_CAIF_DEBUG is not set
CONFIG_CAIF_NETDEV=m
CONFIG_CAIF_USB=m
CONFIG_CEPH_LIB=m
# CONFIG_CEPH_LIB_PRETTYDEBUG is not set
CONFIG_CEPH_LIB_USE_DNS_RESOLVER=y
CONFIG_NFC=m
CONFIG_NFC_DIGITAL=m
CONFIG_NFC_NCI=m
CONFIG_NFC_NCI_SPI=m
CONFIG_NFC_NCI_UART=m
CONFIG_NFC_HCI=m
CONFIG_NFC_SHDLC=y

#
# Near Field Communication (NFC) devices
#
CONFIG_NFC_PN533=m
CONFIG_NFC_WILINK=m
CONFIG_NFC_TRF7970A=m
CONFIG_NFC_MEI_PHY=m
CONFIG_NFC_SIM=m
CONFIG_NFC_PORT100=m
CONFIG_NFC_FDP=m
CONFIG_NFC_FDP_I2C=m
CONFIG_NFC_PN544=m
CONFIG_NFC_PN544_I2C=m
CONFIG_NFC_PN544_MEI=m
CONFIG_NFC_MICROREAD=m
CONFIG_NFC_MICROREAD_I2C=m
CONFIG_NFC_MICROREAD_MEI=m
CONFIG_NFC_MRVL=m
CONFIG_NFC_MRVL_USB=m
CONFIG_NFC_MRVL_UART=m
CONFIG_NFC_MRVL_I2C=m
CONFIG_NFC_MRVL_SPI=m
CONFIG_NFC_ST21NFCA=m
CONFIG_NFC_ST21NFCA_I2C=m
CONFIG_NFC_ST_NCI=m
CONFIG_NFC_ST_NCI_I2C=m
CONFIG_NFC_ST_NCI_SPI=m
CONFIG_NFC_NXP_NCI=m
CONFIG_NFC_NXP_NCI_I2C=m
CONFIG_NFC_S3FWRN5=m
CONFIG_NFC_S3FWRN5_I2C=m
CONFIG_LWTUNNEL=y
CONFIG_HAVE_BPF_JIT=y

#
# Device Drivers
#

#
# Generic Driver Options
#
CONFIG_UEVENT_HELPER=y
CONFIG_UEVENT_HELPER_PATH=""
CONFIG_DEVTMPFS=y
CONFIG_DEVTMPFS_MOUNT=y
# CONFIG_STANDALONE is not set
CONFIG_PREVENT_FIRMWARE_BUILD=y
CONFIG_FW_LOADER=y
CONFIG_FIRMWARE_IN_KERNEL=y
CONFIG_EXTRA_FIRMWARE=""
CONFIG_FW_LOADER_USER_HELPER=y
# CONFIG_FW_LOADER_USER_HELPER_FALLBACK is not set
CONFIG_WANT_DEV_COREDUMP=y
CONFIG_ALLOW_DEV_COREDUMP=y
CONFIG_DEV_COREDUMP=y
# CONFIG_DEBUG_DRIVER is not set
# CONFIG_DEBUG_DEVRES is not set
CONFIG_SYS_HYPERVISOR=y
# CONFIG_GENERIC_CPU_DEVICES is not set
CONFIG_GENERIC_CPU_AUTOPROBE=y
CONFIG_REGMAP=y
CONFIG_REGMAP_I2C=y
CONFIG_REGMAP_SPI=y
CONFIG_REGMAP_SPMI=m
CONFIG_REGMAP_MMIO=y
CONFIG_REGMAP_IRQ=y
CONFIG_DMA_SHARED_BUFFER=y
# CONFIG_FENCE_TRACE is not set
# CONFIG_DMA_CMA is not set

#
# Bus devices
#
CONFIG_CONNECTOR=y
CONFIG_PROC_EVENTS=y
CONFIG_MTD=m
# CONFIG_MTD_TESTS is not set
CONFIG_MTD_REDBOOT_PARTS=m
CONFIG_MTD_REDBOOT_DIRECTORY_BLOCK=-1
# CONFIG_MTD_REDBOOT_PARTS_UNALLOCATED is not set
# CONFIG_MTD_REDBOOT_PARTS_READONLY is not set
CONFIG_MTD_CMDLINE_PARTS=m
CONFIG_MTD_AR7_PARTS=m

#
# User Modules And Translation Layers
#
CONFIG_MTD_BLKDEVS=m
CONFIG_MTD_BLOCK=m
CONFIG_MTD_BLOCK_RO=m
CONFIG_FTL=m
CONFIG_NFTL=m
CONFIG_NFTL_RW=y
CONFIG_INFTL=m
CONFIG_RFD_FTL=m
CONFIG_SSFDC=m
CONFIG_SM_FTL=m
CONFIG_MTD_OOPS=m
CONFIG_MTD_SWAP=m
# CONFIG_MTD_PARTITIONED_MASTER is not set

#
# RAM/ROM/Flash chip drivers
#
CONFIG_MTD_CFI=m
CONFIG_MTD_JEDECPROBE=m
CONFIG_MTD_GEN_PROBE=m
# CONFIG_MTD_CFI_ADV_OPTIONS is not set
CONFIG_MTD_MAP_BANK_WIDTH_1=y
CONFIG_MTD_MAP_BANK_WIDTH_2=y
CONFIG_MTD_MAP_BANK_WIDTH_4=y
# CONFIG_MTD_MAP_BANK_WIDTH_8 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_16 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_32 is not set
CONFIG_MTD_CFI_I1=y
CONFIG_MTD_CFI_I2=y
# CONFIG_MTD_CFI_I4 is not set
# CONFIG_MTD_CFI_I8 is not set
CONFIG_MTD_CFI_INTELEXT=m
CONFIG_MTD_CFI_AMDSTD=m
CONFIG_MTD_CFI_STAA=m
CONFIG_MTD_CFI_UTIL=m
CONFIG_MTD_RAM=m
CONFIG_MTD_ROM=m
CONFIG_MTD_ABSENT=m

#
# Mapping drivers for chip access
#
CONFIG_MTD_COMPLEX_MAPPINGS=y
CONFIG_MTD_PHYSMAP=m
# CONFIG_MTD_PHYSMAP_COMPAT is not set
CONFIG_MTD_SBC_GXX=m
CONFIG_MTD_AMD76XROM=m
CONFIG_MTD_ICHXROM=m
CONFIG_MTD_ESB2ROM=m
CONFIG_MTD_CK804XROM=m
CONFIG_MTD_SCB2_FLASH=m
CONFIG_MTD_NETtel=m
CONFIG_MTD_L440GX=m
CONFIG_MTD_PCI=m
CONFIG_MTD_PCMCIA=m
# CONFIG_MTD_PCMCIA_ANONYMOUS is not set
CONFIG_MTD_GPIO_ADDR=m
CONFIG_MTD_INTEL_VR_NOR=m
CONFIG_MTD_PLATRAM=m
CONFIG_MTD_LATCH_ADDR=m

#
# Self-contained MTD device drivers
#
CONFIG_MTD_PMC551=m
# CONFIG_MTD_PMC551_BUGFIX is not set
# CONFIG_MTD_PMC551_DEBUG is not set
CONFIG_MTD_DATAFLASH=m
# CONFIG_MTD_DATAFLASH_WRITE_VERIFY is not set
CONFIG_MTD_DATAFLASH_OTP=y
CONFIG_MTD_M25P80=m
CONFIG_MTD_SST25L=m
CONFIG_MTD_SLRAM=m
CONFIG_MTD_PHRAM=m
CONFIG_MTD_MTDRAM=m
CONFIG_MTDRAM_TOTAL_SIZE=4096
CONFIG_MTDRAM_ERASE_SIZE=128
CONFIG_MTD_BLOCK2MTD=m

#
# Disk-On-Chip Device Drivers
#
CONFIG_MTD_DOCG3=m
CONFIG_BCH_CONST_M=14
CONFIG_BCH_CONST_T=4
CONFIG_MTD_NAND_ECC=m
# CONFIG_MTD_NAND_ECC_SMC is not set
CONFIG_MTD_NAND=m
CONFIG_MTD_NAND_BCH=m
CONFIG_MTD_NAND_ECC_BCH=y
CONFIG_MTD_SM_COMMON=m
CONFIG_MTD_NAND_DENALI=m
CONFIG_MTD_NAND_DENALI_PCI=m
CONFIG_MTD_NAND_DENALI_DT=m
CONFIG_MTD_NAND_DENALI_SCRATCH_REG_ADDR=0xFF108018
CONFIG_MTD_NAND_GPIO=m
# CONFIG_MTD_NAND_OMAP_BCH_BUILD is not set
CONFIG_MTD_NAND_IDS=m
CONFIG_MTD_NAND_RICOH=m
CONFIG_MTD_NAND_DISKONCHIP=m
# CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADVANCED is not set
CONFIG_MTD_NAND_DISKONCHIP_PROBE_ADDRESS=0
# CONFIG_MTD_NAND_DISKONCHIP_BBTWRITE is not set
CONFIG_MTD_NAND_DOCG4=m
CONFIG_MTD_NAND_CAFE=m
CONFIG_MTD_NAND_NANDSIM=m
CONFIG_MTD_NAND_PLATFORM=m
CONFIG_MTD_NAND_HISI504=m
CONFIG_MTD_ONENAND=m
CONFIG_MTD_ONENAND_VERIFY_WRITE=y
CONFIG_MTD_ONENAND_GENERIC=m
# CONFIG_MTD_ONENAND_OTP is not set
CONFIG_MTD_ONENAND_2X_PROGRAM=y

#
# LPDDR & LPDDR2 PCM memory drivers
#
CONFIG_MTD_LPDDR=m
CONFIG_MTD_QINFO_PROBE=m
CONFIG_MTD_SPI_NOR=m
CONFIG_MTD_SPI_NOR_USE_4K_SECTORS=y
CONFIG_MTD_UBI=m
CONFIG_MTD_UBI_WL_THRESHOLD=4096
CONFIG_MTD_UBI_BEB_LIMIT=20
CONFIG_MTD_UBI_FASTMAP=y
CONFIG_MTD_UBI_GLUEBI=m
CONFIG_MTD_UBI_BLOCK=y
# CONFIG_OF is not set
CONFIG_ARCH_MIGHT_HAVE_PC_PARPORT=y
CONFIG_PARPORT=m
CONFIG_PARPORT_PC=m
CONFIG_PARPORT_SERIAL=m
CONFIG_PARPORT_PC_FIFO=y
# CONFIG_PARPORT_PC_SUPERIO is not set
CONFIG_PARPORT_PC_PCMCIA=m
# CONFIG_PARPORT_GSC is not set
CONFIG_PARPORT_AX88796=m
CONFIG_PARPORT_1284=y
CONFIG_PARPORT_NOT_PC=y
CONFIG_PNP=y
# CONFIG_PNP_DEBUG_MESSAGES is not set

#
# Protocols
#
CONFIG_PNPACPI=y
CONFIG_BLK_DEV=y
CONFIG_BLK_DEV_NULL_BLK=m
CONFIG_BLK_DEV_FD=m
CONFIG_PARIDE=m

#
# Parallel IDE high-level drivers
#
CONFIG_PARIDE_PD=m
CONFIG_PARIDE_PCD=m
CONFIG_PARIDE_PF=m
CONFIG_PARIDE_PT=m
CONFIG_PARIDE_PG=m

#
# Parallel IDE protocol modules
#
CONFIG_PARIDE_ATEN=m
CONFIG_PARIDE_BPCK=m
CONFIG_PARIDE_COMM=m
CONFIG_PARIDE_DSTR=m
CONFIG_PARIDE_FIT2=m
CONFIG_PARIDE_FIT3=m
CONFIG_PARIDE_EPAT=m
CONFIG_PARIDE_EPATC8=y
CONFIG_PARIDE_EPIA=m
CONFIG_PARIDE_FRIQ=m
CONFIG_PARIDE_FRPW=m
CONFIG_PARIDE_KBIC=m
CONFIG_PARIDE_KTTI=m
CONFIG_PARIDE_ON20=m
CONFIG_PARIDE_ON26=m
CONFIG_BLK_DEV_PCIESSD_MTIP32XX=m
CONFIG_ZRAM=m
CONFIG_ZRAM_LZ4_COMPRESS=y
CONFIG_BLK_CPQ_CISS_DA=m
CONFIG_CISS_SCSI_TAPE=y
CONFIG_BLK_DEV_DAC960=m
CONFIG_BLK_DEV_UMEM=m
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_LOOP=y
CONFIG_BLK_DEV_LOOP_MIN_COUNT=8
CONFIG_BLK_DEV_CRYPTOLOOP=m
CONFIG_BLK_DEV_DRBD=m
# CONFIG_DRBD_FAULT_INJECTION is not set
CONFIG_BLK_DEV_NBD=m
CONFIG_BLK_DEV_SKD=m
CONFIG_BLK_DEV_OSD=m
CONFIG_BLK_DEV_SX8=m
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=65536
CONFIG_BLK_DEV_RAM_DAX=y
CONFIG_CDROM_PKTCDVD=m
CONFIG_CDROM_PKTCDVD_BUFFERS=8
# CONFIG_CDROM_PKTCDVD_WCACHE is not set
CONFIG_ATA_OVER_ETH=m
CONFIG_XEN_BLKDEV_FRONTEND=y
CONFIG_XEN_BLKDEV_BACKEND=m
CONFIG_VIRTIO_BLK=y
# CONFIG_BLK_DEV_HD is not set
CONFIG_BLK_DEV_RBD=m
CONFIG_BLK_DEV_RSXX=m
CONFIG_BLK_DEV_NVME=m

#
# Misc devices
#
CONFIG_SENSORS_LIS3LV02D=m
CONFIG_AD525X_DPOT=m
CONFIG_AD525X_DPOT_I2C=m
CONFIG_AD525X_DPOT_SPI=m
CONFIG_DUMMY_IRQ=m
CONFIG_IBM_ASM=m
CONFIG_PHANTOM=m
CONFIG_SGI_IOC4=m
CONFIG_TIFM_CORE=m
CONFIG_TIFM_7XX1=m
CONFIG_ICS932S401=m
CONFIG_ENCLOSURE_SERVICES=m
CONFIG_HP_ILO=m
CONFIG_APDS9802ALS=m
CONFIG_ISL29003=m
CONFIG_ISL29020=m
CONFIG_SENSORS_TSL2550=m
CONFIG_SENSORS_BH1780=m
CONFIG_SENSORS_BH1770=m
CONFIG_SENSORS_APDS990X=m
CONFIG_HMC6352=m
CONFIG_DS1682=m
CONFIG_TI_DAC7512=m
CONFIG_VMWARE_BALLOON=m
CONFIG_BMP085=y
CONFIG_BMP085_I2C=m
CONFIG_BMP085_SPI=m
CONFIG_USB_SWITCH_FSA9480=m
CONFIG_LATTICE_ECP3_CONFIG=m
CONFIG_SRAM=y
CONFIG_C2PORT=m
CONFIG_C2PORT_DURAMAR_2150=m

#
# EEPROM support
#
CONFIG_EEPROM_AT24=m
CONFIG_EEPROM_AT25=m
CONFIG_EEPROM_LEGACY=m
CONFIG_EEPROM_MAX6875=m
CONFIG_EEPROM_93CX6=m
CONFIG_EEPROM_93XX46=m
CONFIG_CB710_CORE=m
# CONFIG_CB710_DEBUG is not set
CONFIG_CB710_DEBUG_ASSUMPTIONS=y

#
# Texas Instruments shared transport line discipline
#
CONFIG_TI_ST=m
CONFIG_SENSORS_LIS3_I2C=m

#
# Altera FPGA firmware download module
#
CONFIG_ALTERA_STAPL=m
CONFIG_INTEL_MEI=m
CONFIG_INTEL_MEI_ME=m
CONFIG_INTEL_MEI_TXE=m
CONFIG_VMWARE_VMCI=m

#
# Intel MIC Bus Driver
#
CONFIG_INTEL_MIC_BUS=m

#
# SCIF Bus Driver
#
CONFIG_SCIF_BUS=m

#
# Intel MIC Host Driver
#
CONFIG_INTEL_MIC_HOST=m

#
# Intel MIC Card Driver
#
CONFIG_INTEL_MIC_CARD=m

#
# SCIF Driver
#
CONFIG_SCIF=m

#
# Intel MIC Coprocessor State Management (COSM) Drivers
#
CONFIG_MIC_COSM=m
CONFIG_GENWQE=m
CONFIG_GENWQE_PLATFORM_ERROR_RECOVERY=0
CONFIG_ECHO=m
# CONFIG_CXL_BASE is not set
# CONFIG_CXL_KERNEL_API is not set
# CONFIG_CXL_EEH is not set
CONFIG_HAVE_IDE=y
# CONFIG_IDE is not set

#
# SCSI device support
#
CONFIG_SCSI_MOD=y
CONFIG_RAID_ATTRS=m
CONFIG_SCSI=y
CONFIG_SCSI_DMA=y
CONFIG_SCSI_NETLINK=y
# CONFIG_SCSI_MQ_DEFAULT is not set
CONFIG_SCSI_PROC_FS=y

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=y
CONFIG_CHR_DEV_ST=m
CONFIG_CHR_DEV_OSST=m
CONFIG_BLK_DEV_SR=y
# CONFIG_BLK_DEV_SR_VENDOR is not set
CONFIG_CHR_DEV_SG=y
CONFIG_CHR_DEV_SCH=m
CONFIG_SCSI_ENCLOSURE=m
CONFIG_SCSI_CONSTANTS=y
CONFIG_SCSI_LOGGING=y
CONFIG_SCSI_SCAN_ASYNC=y

#
# SCSI Transports
#
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_SCSI_SAS_ATTRS=m
CONFIG_SCSI_SAS_LIBSAS=m
CONFIG_SCSI_SAS_ATA=y
CONFIG_SCSI_SAS_HOST_SMP=y
CONFIG_SCSI_SRP_ATTRS=m
CONFIG_SCSI_LOWLEVEL=y
CONFIG_ISCSI_TCP=m
CONFIG_ISCSI_BOOT_SYSFS=m
CONFIG_SCSI_CXGB3_ISCSI=m
CONFIG_SCSI_CXGB4_ISCSI=m
CONFIG_SCSI_BNX2_ISCSI=m
CONFIG_SCSI_BNX2X_FCOE=m
CONFIG_BE2ISCSI=m
CONFIG_BLK_DEV_3W_XXXX_RAID=m
CONFIG_SCSI_HPSA=m
CONFIG_SCSI_3W_9XXX=m
CONFIG_SCSI_3W_SAS=m
CONFIG_SCSI_ACARD=m
CONFIG_SCSI_AACRAID=m
CONFIG_SCSI_AIC7XXX=m
CONFIG_AIC7XXX_CMDS_PER_DEVICE=8
CONFIG_AIC7XXX_RESET_DELAY_MS=5000
# CONFIG_AIC7XXX_DEBUG_ENABLE is not set
CONFIG_AIC7XXX_DEBUG_MASK=0
CONFIG_AIC7XXX_REG_PRETTY_PRINT=y
CONFIG_SCSI_AIC79XX=m
CONFIG_AIC79XX_CMDS_PER_DEVICE=32
CONFIG_AIC79XX_RESET_DELAY_MS=5000
# CONFIG_AIC79XX_DEBUG_ENABLE is not set
CONFIG_AIC79XX_DEBUG_MASK=0
CONFIG_AIC79XX_REG_PRETTY_PRINT=y
CONFIG_SCSI_AIC94XX=m
# CONFIG_AIC94XX_DEBUG is not set
CONFIG_SCSI_MVSAS=m
# CONFIG_SCSI_MVSAS_DEBUG is not set
# CONFIG_SCSI_MVSAS_TASKLET is not set
CONFIG_SCSI_MVUMI=m
CONFIG_SCSI_DPT_I2O=m
CONFIG_SCSI_ADVANSYS=m
CONFIG_SCSI_ARCMSR=m
CONFIG_SCSI_ESAS2R=m
CONFIG_MEGARAID_NEWGEN=y
CONFIG_MEGARAID_MM=m
CONFIG_MEGARAID_MAILBOX=m
CONFIG_MEGARAID_LEGACY=m
CONFIG_MEGARAID_SAS=m
CONFIG_SCSI_MPT3SAS=m
CONFIG_SCSI_MPT2SAS_MAX_SGE=128
CONFIG_SCSI_MPT3SAS_MAX_SGE=128
CONFIG_SCSI_MPT2SAS=m
CONFIG_SCSI_UFSHCD=m
CONFIG_SCSI_UFSHCD_PCI=m
CONFIG_SCSI_UFSHCD_PLATFORM=m
CONFIG_SCSI_HPTIOP=m
CONFIG_SCSI_BUSLOGIC=m
CONFIG_SCSI_FLASHPOINT=y
CONFIG_VMWARE_PVSCSI=m
CONFIG_XEN_SCSI_FRONTEND=m
CONFIG_HYPERV_STORAGE=m
CONFIG_LIBFC=m
CONFIG_LIBFCOE=m
CONFIG_FCOE=m
CONFIG_FCOE_FNIC=m
CONFIG_SCSI_SNIC=m
# CONFIG_SCSI_SNIC_DEBUG_FS is not set
CONFIG_SCSI_DMX3191D=m
CONFIG_SCSI_EATA=m
CONFIG_SCSI_EATA_TAGGED_QUEUE=y
CONFIG_SCSI_EATA_LINKED_COMMANDS=y
CONFIG_SCSI_EATA_MAX_TAGS=16
CONFIG_SCSI_FUTURE_DOMAIN=m
CONFIG_SCSI_GDTH=m
CONFIG_SCSI_ISCI=m
CONFIG_SCSI_IPS=m
CONFIG_SCSI_INITIO=m
CONFIG_SCSI_INIA100=m
CONFIG_SCSI_PPA=m
CONFIG_SCSI_IMM=m
# CONFIG_SCSI_IZIP_EPP16 is not set
# CONFIG_SCSI_IZIP_SLOW_CTR is not set
CONFIG_SCSI_STEX=m
CONFIG_SCSI_SYM53C8XX_2=m
CONFIG_SCSI_SYM53C8XX_DMA_ADDRESSING_MODE=1
CONFIG_SCSI_SYM53C8XX_DEFAULT_TAGS=16
CONFIG_SCSI_SYM53C8XX_MAX_TAGS=64
CONFIG_SCSI_SYM53C8XX_MMIO=y
CONFIG_SCSI_IPR=m
CONFIG_SCSI_IPR_TRACE=y
CONFIG_SCSI_IPR_DUMP=y
CONFIG_SCSI_QLOGIC_1280=m
CONFIG_SCSI_QLA_FC=m
CONFIG_TCM_QLA2XXX=m
CONFIG_SCSI_QLA_ISCSI=m
CONFIG_SCSI_LPFC=m
# CONFIG_SCSI_LPFC_DEBUG_FS is not set
CONFIG_SCSI_DC395x=m
CONFIG_SCSI_AM53C974=m
CONFIG_SCSI_WD719X=m
CONFIG_SCSI_DEBUG=m
CONFIG_SCSI_PMCRAID=m
CONFIG_SCSI_PM8001=m
CONFIG_SCSI_BFA_FC=m
CONFIG_SCSI_VIRTIO=m
CONFIG_SCSI_CHELSIO_FCOE=m
CONFIG_SCSI_LOWLEVEL_PCMCIA=y
CONFIG_PCMCIA_AHA152X=m
CONFIG_PCMCIA_FDOMAIN=m
CONFIG_PCMCIA_QLOGIC=m
CONFIG_PCMCIA_SYM53C500=m
CONFIG_SCSI_DH=y
CONFIG_SCSI_DH_RDAC=m
CONFIG_SCSI_DH_HP_SW=m
CONFIG_SCSI_DH_EMC=m
CONFIG_SCSI_DH_ALUA=m
CONFIG_SCSI_OSD_INITIATOR=m
CONFIG_SCSI_OSD_ULD=m
CONFIG_SCSI_OSD_DPRINT_SENSE=1
# CONFIG_SCSI_OSD_DEBUG is not set
CONFIG_ATA=y
# CONFIG_ATA_NONSTANDARD is not set
CONFIG_ATA_VERBOSE_ERROR=y
CONFIG_ATA_ACPI=y
CONFIG_SATA_ZPODD=y
CONFIG_SATA_PMP=y

#
# Controllers with non-SFF native interface
#
CONFIG_SATA_AHCI=m
CONFIG_SATA_AHCI_PLATFORM=m
CONFIG_SATA_INIC162X=m
CONFIG_SATA_ACARD_AHCI=m
CONFIG_SATA_SIL24=m
CONFIG_ATA_SFF=y

#
# SFF controllers with custom DMA interface
#
CONFIG_PDC_ADMA=m
CONFIG_SATA_QSTOR=m
CONFIG_SATA_SX4=m
CONFIG_ATA_BMDMA=y

#
# SATA SFF controllers with BMDMA
#
CONFIG_ATA_PIIX=y
CONFIG_SATA_MV=m
CONFIG_SATA_NV=m
CONFIG_SATA_PROMISE=m
CONFIG_SATA_SIL=m
CONFIG_SATA_SIS=m
CONFIG_SATA_SVW=m
CONFIG_SATA_ULI=m
CONFIG_SATA_VIA=m
CONFIG_SATA_VITESSE=m

#
# PATA SFF controllers with BMDMA
#
CONFIG_PATA_ALI=m
CONFIG_PATA_AMD=m
CONFIG_PATA_ARTOP=m
CONFIG_PATA_ATIIXP=m
CONFIG_PATA_ATP867X=m
CONFIG_PATA_CMD64X=m
CONFIG_PATA_CYPRESS=m
CONFIG_PATA_EFAR=m
CONFIG_PATA_HPT366=m
CONFIG_PATA_HPT37X=m
CONFIG_PATA_HPT3X2N=m
CONFIG_PATA_HPT3X3=m
# CONFIG_PATA_HPT3X3_DMA is not set
CONFIG_PATA_IT8213=m
CONFIG_PATA_IT821X=m
CONFIG_PATA_JMICRON=m
CONFIG_PATA_MARVELL=m
CONFIG_PATA_NETCELL=m
CONFIG_PATA_NINJA32=m
CONFIG_PATA_NS87415=m
CONFIG_PATA_OLDPIIX=m
CONFIG_PATA_OPTIDMA=m
CONFIG_PATA_PDC2027X=m
CONFIG_PATA_PDC_OLD=m
CONFIG_PATA_RADISYS=m
CONFIG_PATA_RDC=m
CONFIG_PATA_SCH=m
CONFIG_PATA_SERVERWORKS=m
CONFIG_PATA_SIL680=m
CONFIG_PATA_SIS=y
CONFIG_PATA_TOSHIBA=m
CONFIG_PATA_TRIFLEX=m
CONFIG_PATA_VIA=m
CONFIG_PATA_WINBOND=m

#
# PIO-only SFF controllers
#
CONFIG_PATA_CMD640_PCI=m
CONFIG_PATA_MPIIX=m
CONFIG_PATA_NS87410=m
CONFIG_PATA_OPTI=m
CONFIG_PATA_PCMCIA=m
CONFIG_PATA_PLATFORM=m
CONFIG_PATA_RZ1000=m

#
# Generic fallback / legacy drivers
#
CONFIG_PATA_ACPI=m
CONFIG_ATA_GENERIC=y
CONFIG_PATA_LEGACY=m
CONFIG_MD=y
CONFIG_BLK_DEV_MD=y
CONFIG_MD_AUTODETECT=y
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=m
CONFIG_MD_RAID10=m
CONFIG_MD_RAID456=m
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
CONFIG_MD_CLUSTER=m
CONFIG_BCACHE=m
# CONFIG_BCACHE_DEBUG is not set
# CONFIG_BCACHE_CLOSURES_DEBUG is not set
CONFIG_BLK_DEV_DM_BUILTIN=y
CONFIG_BLK_DEV_DM=y
# CONFIG_DM_MQ_DEFAULT is not set
# CONFIG_DM_DEBUG is not set
CONFIG_DM_BUFIO=m
CONFIG_DM_BIO_PRISON=m
CONFIG_DM_PERSISTENT_DATA=m
# CONFIG_DM_DEBUG_BLOCK_STACK_TRACING is not set
CONFIG_DM_CRYPT=m
CONFIG_DM_SNAPSHOT=m
CONFIG_DM_THIN_PROVISIONING=m
CONFIG_DM_CACHE=m
CONFIG_DM_CACHE_MQ=m
CONFIG_DM_CACHE_SMQ=m
CONFIG_DM_CACHE_CLEANER=m
CONFIG_DM_ERA=m
CONFIG_DM_MIRROR=m
CONFIG_DM_LOG_USERSPACE=m
CONFIG_DM_RAID=m
CONFIG_DM_ZERO=m
CONFIG_DM_MULTIPATH=m
CONFIG_DM_MULTIPATH_QL=m
CONFIG_DM_MULTIPATH_ST=m
CONFIG_DM_DELAY=m
CONFIG_DM_UEVENT=y
CONFIG_DM_FLAKEY=m
CONFIG_DM_VERITY=m
CONFIG_DM_SWITCH=m
CONFIG_DM_LOG_WRITES=m
CONFIG_TARGET_CORE=m
CONFIG_TCM_IBLOCK=m
CONFIG_TCM_FILEIO=m
CONFIG_TCM_PSCSI=m
CONFIG_TCM_USER2=m
CONFIG_LOOPBACK_TARGET=m
CONFIG_TCM_FC=m
CONFIG_ISCSI_TARGET=m
CONFIG_SBP_TARGET=m
CONFIG_FUSION=y
CONFIG_FUSION_SPI=m
CONFIG_FUSION_FC=m
CONFIG_FUSION_SAS=m
CONFIG_FUSION_MAX_SGE=128
CONFIG_FUSION_CTL=m
CONFIG_FUSION_LAN=m
CONFIG_FUSION_LOGGING=y

#
# IEEE 1394 (FireWire) support
#
CONFIG_FIREWIRE=m
CONFIG_FIREWIRE_OHCI=m
CONFIG_FIREWIRE_SBP2=m
CONFIG_FIREWIRE_NET=m
CONFIG_FIREWIRE_NOSY=m
CONFIG_MACINTOSH_DRIVERS=y
CONFIG_MAC_EMUMOUSEBTN=m
CONFIG_NETDEVICES=y
CONFIG_MII=m
CONFIG_NET_CORE=y
CONFIG_BONDING=m
CONFIG_DUMMY=m
CONFIG_EQUALIZER=m
CONFIG_NET_FC=y
CONFIG_IFB=m
CONFIG_NET_TEAM=m
CONFIG_NET_TEAM_MODE_BROADCAST=m
CONFIG_NET_TEAM_MODE_ROUNDROBIN=m
CONFIG_NET_TEAM_MODE_RANDOM=m
CONFIG_NET_TEAM_MODE_ACTIVEBACKUP=m
CONFIG_NET_TEAM_MODE_LOADBALANCE=m
CONFIG_MACVLAN=m
CONFIG_MACVTAP=m
CONFIG_IPVLAN=m
CONFIG_VXLAN=m
CONFIG_GENEVE=m
CONFIG_NETCONSOLE=m
CONFIG_NETCONSOLE_DYNAMIC=y
CONFIG_NETPOLL=y
CONFIG_NET_POLL_CONTROLLER=y
CONFIG_NTB_NETDEV=m
CONFIG_RIONET=m
CONFIG_RIONET_TX_SIZE=128
CONFIG_RIONET_RX_SIZE=128
CONFIG_TUN=y
# CONFIG_TUN_VNET_CROSS_LE is not set
CONFIG_VETH=m
CONFIG_VIRTIO_NET=y
CONFIG_NLMON=m
CONFIG_NET_VRF=m
CONFIG_SUNGEM_PHY=m
CONFIG_ARCNET=m
CONFIG_ARCNET_1201=m
CONFIG_ARCNET_1051=m
CONFIG_ARCNET_RAW=m
CONFIG_ARCNET_CAP=m
CONFIG_ARCNET_COM90xx=m
CONFIG_ARCNET_COM90xxIO=m
CONFIG_ARCNET_RIM_I=m
CONFIG_ARCNET_COM20020=m
CONFIG_ARCNET_COM20020_PCI=m
CONFIG_ARCNET_COM20020_CS=m
CONFIG_ATM_DRIVERS=y
CONFIG_ATM_DUMMY=m
CONFIG_ATM_TCP=m
CONFIG_ATM_LANAI=m
CONFIG_ATM_ENI=m
# CONFIG_ATM_ENI_DEBUG is not set
# CONFIG_ATM_ENI_TUNE_BURST is not set
CONFIG_ATM_FIRESTREAM=m
CONFIG_ATM_ZATM=m
# CONFIG_ATM_ZATM_DEBUG is not set
CONFIG_ATM_NICSTAR=m
# CONFIG_ATM_NICSTAR_USE_SUNI is not set
# CONFIG_ATM_NICSTAR_USE_IDT77105 is not set
CONFIG_ATM_IDT77252=m
# CONFIG_ATM_IDT77252_DEBUG is not set
# CONFIG_ATM_IDT77252_RCV_ALL is not set
CONFIG_ATM_IDT77252_USE_SUNI=y
CONFIG_ATM_AMBASSADOR=m
# CONFIG_ATM_AMBASSADOR_DEBUG is not set
CONFIG_ATM_HORIZON=m
# CONFIG_ATM_HORIZON_DEBUG is not set
CONFIG_ATM_IA=m
# CONFIG_ATM_IA_DEBUG is not set
CONFIG_ATM_FORE200E=m
# CONFIG_ATM_FORE200E_USE_TASKLET is not set
CONFIG_ATM_FORE200E_TX_RETRY=16
CONFIG_ATM_FORE200E_DEBUG=0
CONFIG_ATM_HE=m
CONFIG_ATM_HE_USE_SUNI=y
CONFIG_ATM_SOLOS=m

#
# CAIF transport drivers
#
CONFIG_CAIF_TTY=m
CONFIG_CAIF_SPI_SLAVE=m
# CONFIG_CAIF_SPI_SYNC is not set
CONFIG_CAIF_HSI=m
CONFIG_CAIF_VIRTIO=m
CONFIG_VHOST_NET=m
CONFIG_VHOST_SCSI=m
CONFIG_VHOST_RING=m
CONFIG_VHOST=m
# CONFIG_VHOST_CROSS_ENDIAN_LEGACY is not set

#
# Distributed Switch Architecture drivers
#
# CONFIG_NET_DSA_MV88E6XXX is not set
# CONFIG_NET_DSA_MV88E6XXX_NEED_PPU is not set
CONFIG_ETHERNET=y
CONFIG_MDIO=m
CONFIG_NET_VENDOR_3COM=y
CONFIG_PCMCIA_3C574=m
CONFIG_PCMCIA_3C589=m
CONFIG_VORTEX=m
CONFIG_TYPHOON=m
CONFIG_NET_VENDOR_ADAPTEC=y
CONFIG_ADAPTEC_STARFIRE=m
CONFIG_NET_VENDOR_AGERE=y
CONFIG_ET131X=m
CONFIG_NET_VENDOR_ALTEON=y
CONFIG_ACENIC=m
# CONFIG_ACENIC_OMIT_TIGON_I is not set
CONFIG_ALTERA_TSE=m
CONFIG_NET_VENDOR_AMD=y
CONFIG_AMD8111_ETH=m
CONFIG_PCNET32=m
CONFIG_PCMCIA_NMCLAN=m
CONFIG_NET_VENDOR_ARC=y
CONFIG_NET_VENDOR_ATHEROS=y
CONFIG_ATL2=m
CONFIG_ATL1=m
CONFIG_ATL1E=m
CONFIG_ATL1C=m
CONFIG_ALX=m
CONFIG_NET_VENDOR_AURORA=y
CONFIG_AURORA_NB8800=m
CONFIG_NET_CADENCE=y
CONFIG_MACB=m
CONFIG_NET_VENDOR_BROADCOM=y
CONFIG_B44=m
CONFIG_B44_PCI_AUTOSELECT=y
CONFIG_B44_PCICORE_AUTOSELECT=y
CONFIG_B44_PCI=y
CONFIG_BCMGENET=m
CONFIG_BNX2=m
CONFIG_CNIC=m
CONFIG_TIGON3=m
CONFIG_BNX2X=m
CONFIG_BNX2X_SRIOV=y
CONFIG_BNX2X_VXLAN=y
CONFIG_BNXT=m
CONFIG_BNXT_SRIOV=y
CONFIG_NET_VENDOR_BROCADE=y
CONFIG_BNA=m
CONFIG_NET_VENDOR_CAVIUM=y
CONFIG_THUNDER_NIC_PF=m
CONFIG_THUNDER_NIC_VF=m
CONFIG_THUNDER_NIC_BGX=m
CONFIG_LIQUIDIO=m
CONFIG_NET_VENDOR_CHELSIO=y
CONFIG_CHELSIO_T1=m
CONFIG_CHELSIO_T1_1G=y
CONFIG_CHELSIO_T3=m
CONFIG_CHELSIO_T4=m
CONFIG_CHELSIO_T4_DCB=y
CONFIG_CHELSIO_T4_FCOE=y
CONFIG_CHELSIO_T4VF=m
CONFIG_NET_VENDOR_CISCO=y
CONFIG_ENIC=m
CONFIG_CX_ECAT=m
CONFIG_DNET=m
CONFIG_NET_VENDOR_DEC=y
CONFIG_NET_TULIP=y
CONFIG_DE2104X=m
CONFIG_DE2104X_DSL=0
CONFIG_TULIP=m
# CONFIG_TULIP_MWI is not set
# CONFIG_TULIP_MMIO is not set
# CONFIG_TULIP_NAPI is not set
CONFIG_DE4X5=m
CONFIG_WINBOND_840=m
CONFIG_DM9102=m
CONFIG_ULI526X=m
CONFIG_PCMCIA_XIRCOM=m
CONFIG_NET_VENDOR_DLINK=y
CONFIG_DL2K=m
CONFIG_SUNDANCE=m
# CONFIG_SUNDANCE_MMIO is not set
CONFIG_NET_VENDOR_EMULEX=y
CONFIG_BE2NET=m
CONFIG_BE2NET_HWMON=y
CONFIG_BE2NET_VXLAN=y
CONFIG_NET_VENDOR_EZCHIP=y
CONFIG_NET_VENDOR_EXAR=y
CONFIG_S2IO=m
CONFIG_VXGE=m
# CONFIG_VXGE_DEBUG_TRACE_ALL is not set
CONFIG_NET_VENDOR_FUJITSU=y
CONFIG_PCMCIA_FMVJ18X=m
CONFIG_NET_VENDOR_HP=y
CONFIG_HP100=m
CONFIG_NET_VENDOR_INTEL=y
CONFIG_E100=m
CONFIG_E1000=m
CONFIG_E1000E=m
CONFIG_IGB=m
CONFIG_IGB_HWMON=y
CONFIG_IGB_DCA=y
CONFIG_IGBVF=m
CONFIG_IXGB=m
CONFIG_IXGBE=m
CONFIG_IXGBE_VXLAN=y
CONFIG_IXGBE_HWMON=y
CONFIG_IXGBE_DCA=y
CONFIG_IXGBE_DCB=y
CONFIG_IXGBEVF=m
CONFIG_I40E=m
CONFIG_I40E_VXLAN=y
CONFIG_I40E_DCB=y
CONFIG_I40E_FCOE=y
CONFIG_I40EVF=m
CONFIG_FM10K=m
CONFIG_FM10K_VXLAN=y
CONFIG_NET_VENDOR_I825XX=y
CONFIG_JME=m
CONFIG_NET_VENDOR_MARVELL=y
CONFIG_MVMDIO=m
CONFIG_SKGE=m
# CONFIG_SKGE_DEBUG is not set
CONFIG_SKGE_GENESIS=y
CONFIG_SKY2=m
# CONFIG_SKY2_DEBUG is not set
CONFIG_NET_VENDOR_MELLANOX=y
CONFIG_MLX4_EN=m
CONFIG_MLX4_EN_DCB=y
CONFIG_MLX4_EN_VXLAN=y
CONFIG_MLX4_CORE=m
CONFIG_MLX4_DEBUG=y
CONFIG_MLX5_CORE=m
CONFIG_MLX5_CORE_EN=y
CONFIG_MLXSW_CORE=m
CONFIG_MLXSW_PCI=m
CONFIG_NET_VENDOR_MICREL=y
CONFIG_KS8842=m
CONFIG_KS8851=m
CONFIG_KS8851_MLL=m
CONFIG_KSZ884X_PCI=m
CONFIG_NET_VENDOR_MICROCHIP=y
CONFIG_ENC28J60=m
# CONFIG_ENC28J60_WRITEVERIFY is not set
CONFIG_ENCX24J600=m
CONFIG_NET_VENDOR_MYRI=y
CONFIG_MYRI10GE=m
CONFIG_MYRI10GE_DCA=y
CONFIG_FEALNX=m
CONFIG_NET_VENDOR_NATSEMI=y
CONFIG_NATSEMI=m
CONFIG_NS83820=m
CONFIG_NET_VENDOR_8390=y
CONFIG_PCMCIA_AXNET=m
CONFIG_NE2K_PCI=m
CONFIG_PCMCIA_PCNET=m
CONFIG_NET_VENDOR_NVIDIA=y
CONFIG_FORCEDETH=m
CONFIG_NET_VENDOR_OKI=y
CONFIG_ETHOC=m
CONFIG_NET_PACKET_ENGINE=y
CONFIG_HAMACHI=m
CONFIG_YELLOWFIN=m
CONFIG_NET_VENDOR_QLOGIC=y
CONFIG_QLA3XXX=m
CONFIG_QLCNIC=m
CONFIG_QLCNIC_SRIOV=y
CONFIG_QLCNIC_DCB=y
CONFIG_QLCNIC_VXLAN=y
CONFIG_QLCNIC_HWMON=y
CONFIG_QLGE=m
CONFIG_NETXEN_NIC=m
CONFIG_QED=m
CONFIG_QEDE=m
CONFIG_NET_VENDOR_QUALCOMM=y
CONFIG_NET_VENDOR_REALTEK=y
CONFIG_ATP=m
CONFIG_8139CP=m
CONFIG_8139TOO=m
CONFIG_8139TOO_PIO=y
# CONFIG_8139TOO_TUNE_TWISTER is not set
CONFIG_8139TOO_8129=y
# CONFIG_8139_OLD_RX_RESET is not set
CONFIG_R8169=m
CONFIG_NET_VENDOR_RENESAS=y
CONFIG_NET_VENDOR_RDC=y
CONFIG_R6040=m
CONFIG_NET_VENDOR_ROCKER=y
CONFIG_NET_VENDOR_SAMSUNG=y
CONFIG_SXGBE_ETH=m
CONFIG_NET_VENDOR_SEEQ=y
CONFIG_NET_VENDOR_SILAN=y
CONFIG_SC92031=m
CONFIG_NET_VENDOR_SIS=y
CONFIG_SIS900=m
CONFIG_SIS190=m
CONFIG_SFC=m
CONFIG_SFC_MTD=y
CONFIG_SFC_MCDI_MON=y
CONFIG_SFC_SRIOV=y
CONFIG_SFC_MCDI_LOGGING=y
CONFIG_NET_VENDOR_SMSC=y
CONFIG_PCMCIA_SMC91C92=m
CONFIG_EPIC100=m
CONFIG_SMSC911X=m
# CONFIG_SMSC911X_ARCH_HOOKS is not set
CONFIG_SMSC9420=m
CONFIG_NET_VENDOR_STMICRO=y
CONFIG_STMMAC_ETH=m
CONFIG_STMMAC_PLATFORM=m
CONFIG_DWMAC_GENERIC=m
# CONFIG_STMMAC_PCI is not set
CONFIG_NET_VENDOR_SUN=y
CONFIG_HAPPYMEAL=m
CONFIG_SUNGEM=m
CONFIG_CASSINI=m
CONFIG_NIU=m
CONFIG_NET_VENDOR_SYNOPSYS=y
CONFIG_NET_VENDOR_TEHUTI=y
CONFIG_TEHUTI=m
CONFIG_NET_VENDOR_TI=y
CONFIG_TI_CPSW_ALE=m
CONFIG_TLAN=m
CONFIG_NET_VENDOR_VIA=y
CONFIG_VIA_RHINE=m
CONFIG_VIA_RHINE_MMIO=y
CONFIG_VIA_VELOCITY=m
CONFIG_NET_VENDOR_WIZNET=y
CONFIG_WIZNET_W5100=m
CONFIG_WIZNET_W5300=m
# CONFIG_WIZNET_BUS_DIRECT is not set
# CONFIG_WIZNET_BUS_INDIRECT is not set
CONFIG_WIZNET_BUS_ANY=y
CONFIG_NET_VENDOR_XIRCOM=y
CONFIG_PCMCIA_XIRC2PS=m
CONFIG_FDDI=y
CONFIG_DEFXX=m
# CONFIG_DEFXX_MMIO is not set
CONFIG_SKFP=m
# CONFIG_HIPPI is not set
CONFIG_NET_SB1000=m
CONFIG_PHYLIB=y

#
# MII PHY device drivers
#
CONFIG_AQUANTIA_PHY=m
CONFIG_AT803X_PHY=m
CONFIG_AMD_PHY=m
CONFIG_MARVELL_PHY=m
CONFIG_DAVICOM_PHY=m
CONFIG_QSEMI_PHY=m
CONFIG_LXT_PHY=m
CONFIG_CICADA_PHY=m
CONFIG_VITESSE_PHY=m
CONFIG_TERANETICS_PHY=m
CONFIG_SMSC_PHY=m
CONFIG_BCM_NET_PHYLIB=m
CONFIG_BROADCOM_PHY=m
CONFIG_BCM7XXX_PHY=m
CONFIG_BCM87XX_PHY=m
CONFIG_ICPLUS_PHY=m
CONFIG_REALTEK_PHY=m
CONFIG_NATIONAL_PHY=m
CONFIG_STE10XP=m
CONFIG_LSI_ET1011C_PHY=m
CONFIG_MICREL_PHY=m
CONFIG_DP83848_PHY=m
CONFIG_DP83867_PHY=m
CONFIG_MICROCHIP_PHY=m
CONFIG_FIXED_PHY=y
CONFIG_MDIO_BITBANG=m
CONFIG_MDIO_GPIO=m
CONFIG_MDIO_OCTEON=m
CONFIG_MDIO_BCM_UNIMAC=m
CONFIG_MICREL_KS8995MA=m
CONFIG_PLIP=m
CONFIG_PPP=y
CONFIG_PPP_BSDCOMP=m
CONFIG_PPP_DEFLATE=m
CONFIG_PPP_FILTER=y
CONFIG_PPP_MPPE=m
CONFIG_PPP_MULTILINK=y
CONFIG_PPPOATM=m
CONFIG_PPPOE=m
CONFIG_PPTP=m
CONFIG_PPPOL2TP=m
CONFIG_PPP_ASYNC=m
CONFIG_PPP_SYNC_TTY=m
CONFIG_SLIP=m
CONFIG_SLHC=y
CONFIG_SLIP_COMPRESSED=y
CONFIG_SLIP_SMART=y
CONFIG_SLIP_MODE_SLIP6=y
CONFIG_USB_NET_DRIVERS=m
CONFIG_USB_CATC=m
CONFIG_USB_KAWETH=m
CONFIG_USB_PEGASUS=m
CONFIG_USB_RTL8150=m
CONFIG_USB_RTL8152=m
CONFIG_USB_LAN78XX=m
CONFIG_USB_USBNET=m
CONFIG_USB_NET_AX8817X=m
CONFIG_USB_NET_AX88179_178A=m
CONFIG_USB_NET_CDCETHER=m
CONFIG_USB_NET_CDC_EEM=m
CONFIG_USB_NET_CDC_NCM=m
CONFIG_USB_NET_HUAWEI_CDC_NCM=m
CONFIG_USB_NET_CDC_MBIM=m
CONFIG_USB_NET_DM9601=m
CONFIG_USB_NET_SR9700=m
CONFIG_USB_NET_SR9800=m
CONFIG_USB_NET_SMSC75XX=m
CONFIG_USB_NET_SMSC95XX=m
CONFIG_USB_NET_GL620A=m
CONFIG_USB_NET_NET1080=m
CONFIG_USB_NET_PLUSB=m
CONFIG_USB_NET_MCS7830=m
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_CDC_SUBSET=m
CONFIG_USB_ALI_M5632=y
CONFIG_USB_AN2720=y
CONFIG_USB_BELKIN=y
CONFIG_USB_ARMLINUX=y
CONFIG_USB_EPSON2888=y
CONFIG_USB_KC2190=y
CONFIG_USB_NET_ZAURUS=m
CONFIG_USB_NET_CX82310_ETH=m
CONFIG_USB_NET_KALMIA=m
CONFIG_USB_NET_QMI_WWAN=m
CONFIG_USB_HSO=m
CONFIG_USB_NET_INT51X1=m
CONFIG_USB_CDC_PHONET=m
CONFIG_USB_IPHETH=m
CONFIG_USB_SIERRA_NET=m
CONFIG_USB_VL600=m
CONFIG_USB_NET_CH9200=m
CONFIG_WLAN=y
CONFIG_PCMCIA_RAYCS=m
CONFIG_LIBERTAS_THINFIRM=m
# CONFIG_LIBERTAS_THINFIRM_DEBUG is not set
CONFIG_LIBERTAS_THINFIRM_USB=m
CONFIG_AIRO=m
CONFIG_ATMEL=m
CONFIG_PCI_ATMEL=m
CONFIG_PCMCIA_ATMEL=m
CONFIG_AT76C50X_USB=m
CONFIG_AIRO_CS=m
CONFIG_PCMCIA_WL3501=m
# CONFIG_PRISM54 is not set
CONFIG_USB_ZD1201=m
CONFIG_USB_NET_RNDIS_WLAN=m
CONFIG_ADM8211=m
CONFIG_RTL8180=m
CONFIG_RTL8187=m
CONFIG_RTL8187_LEDS=y
CONFIG_MAC80211_HWSIM=m
CONFIG_MWL8K=m
CONFIG_ATH_COMMON=m
CONFIG_ATH_CARDS=m
# CONFIG_ATH_DEBUG is not set
CONFIG_ATH5K=m
# CONFIG_ATH5K_DEBUG is not set
# CONFIG_ATH5K_TRACER is not set
CONFIG_ATH5K_PCI=y
CONFIG_ATH9K_HW=m
CONFIG_ATH9K_COMMON=m
CONFIG_ATH9K_BTCOEX_SUPPORT=y
CONFIG_ATH9K=m
CONFIG_ATH9K_PCI=y
CONFIG_ATH9K_AHB=y
CONFIG_ATH9K_DEBUGFS=y
CONFIG_ATH9K_STATION_STATISTICS=y
# CONFIG_ATH9K_DYNACK is not set
CONFIG_ATH9K_WOW=y
CONFIG_ATH9K_RFKILL=y
CONFIG_ATH9K_CHANNEL_CONTEXT=y
CONFIG_ATH9K_PCOEM=y
CONFIG_ATH9K_HTC=m
CONFIG_ATH9K_HTC_DEBUGFS=y
CONFIG_CARL9170=m
CONFIG_CARL9170_LEDS=y
# CONFIG_CARL9170_DEBUGFS is not set
CONFIG_CARL9170_WPC=y
CONFIG_CARL9170_HWRNG=y
CONFIG_ATH6KL=m
CONFIG_ATH6KL_SDIO=m
CONFIG_ATH6KL_USB=m
# CONFIG_ATH6KL_DEBUG is not set
# CONFIG_ATH6KL_TRACING is not set
CONFIG_AR5523=m
CONFIG_WIL6210=m
CONFIG_WIL6210_ISR_COR=y
CONFIG_WIL6210_TRACING=y
CONFIG_ATH10K=m
CONFIG_ATH10K_PCI=m
# CONFIG_ATH10K_DEBUG is not set
CONFIG_ATH10K_DEBUGFS=y
CONFIG_ATH10K_TRACING=y
CONFIG_WCN36XX=m
# CONFIG_WCN36XX_DEBUGFS is not set
CONFIG_B43=m
CONFIG_B43_BCMA=y
CONFIG_B43_SSB=y
CONFIG_B43_BUSES_BCMA_AND_SSB=y
# CONFIG_B43_BUSES_BCMA is not set
# CONFIG_B43_BUSES_SSB is not set
CONFIG_B43_PCI_AUTOSELECT=y
CONFIG_B43_PCICORE_AUTOSELECT=y
# CONFIG_B43_SDIO is not set
CONFIG_B43_BCMA_PIO=y
CONFIG_B43_PIO=y
CONFIG_B43_PHY_G=y
CONFIG_B43_PHY_N=y
CONFIG_B43_PHY_LP=y
CONFIG_B43_PHY_HT=y
CONFIG_B43_LEDS=y
CONFIG_B43_HWRNG=y
# CONFIG_B43_DEBUG is not set
CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_PCICORE_AUTOSELECT=y
CONFIG_B43LEGACY_LEDS=y
CONFIG_B43LEGACY_HWRNG=y
# CONFIG_B43LEGACY_DEBUG is not set
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y
CONFIG_B43LEGACY_DMA_AND_PIO_MODE=y
# CONFIG_B43LEGACY_DMA_MODE is not set
# CONFIG_B43LEGACY_PIO_MODE is not set
CONFIG_BRCMUTIL=m
CONFIG_BRCMSMAC=m
CONFIG_BRCMFMAC=m
CONFIG_BRCMFMAC_PROTO_BCDC=y
CONFIG_BRCMFMAC_PROTO_MSGBUF=y
CONFIG_BRCMFMAC_SDIO=y
CONFIG_BRCMFMAC_USB=y
CONFIG_BRCMFMAC_PCIE=y
CONFIG_BRCM_TRACING=y
# CONFIG_BRCMDBG is not set
CONFIG_HOSTAP=m
CONFIG_HOSTAP_FIRMWARE=y
CONFIG_HOSTAP_FIRMWARE_NVRAM=y
CONFIG_HOSTAP_PLX=m
CONFIG_HOSTAP_PCI=m
CONFIG_HOSTAP_CS=m
CONFIG_IPW2100=m
CONFIG_IPW2100_MONITOR=y
# CONFIG_IPW2100_DEBUG is not set
CONFIG_IPW2200=m
CONFIG_IPW2200_MONITOR=y
CONFIG_IPW2200_RADIOTAP=y
CONFIG_IPW2200_PROMISCUOUS=y
CONFIG_IPW2200_QOS=y
# CONFIG_IPW2200_DEBUG is not set
CONFIG_LIBIPW=m
# CONFIG_LIBIPW_DEBUG is not set
CONFIG_IWLWIFI=m
CONFIG_IWLWIFI_LEDS=y
CONFIG_IWLDVM=m
CONFIG_IWLMVM=m
CONFIG_IWLWIFI_OPMODE_MODULAR=y
# CONFIG_IWLWIFI_BCAST_FILTERING is not set
# CONFIG_IWLWIFI_UAPSD is not set

#
# Debugging Options
#
# CONFIG_IWLWIFI_DEBUG is not set
CONFIG_IWLWIFI_DEBUGFS=y
CONFIG_IWLWIFI_DEVICE_TRACING=y
CONFIG_IWLEGACY=m
CONFIG_IWL4965=m
CONFIG_IWL3945=m

#
# iwl3945 / iwl4965 Debugging Options
#
# CONFIG_IWLEGACY_DEBUG is not set
CONFIG_IWLEGACY_DEBUGFS=y
CONFIG_LIBERTAS=m
CONFIG_LIBERTAS_USB=m
CONFIG_LIBERTAS_CS=m
CONFIG_LIBERTAS_SDIO=m
CONFIG_LIBERTAS_SPI=m
# CONFIG_LIBERTAS_DEBUG is not set
CONFIG_LIBERTAS_MESH=y
CONFIG_HERMES=m
# CONFIG_HERMES_PRISM is not set
CONFIG_HERMES_CACHE_FW_ON_INIT=y
CONFIG_PLX_HERMES=m
CONFIG_TMD_HERMES=m
CONFIG_NORTEL_HERMES=m
CONFIG_PCMCIA_HERMES=m
CONFIG_PCMCIA_SPECTRUM=m
CONFIG_ORINOCO_USB=m
CONFIG_P54_COMMON=m
CONFIG_P54_USB=m
CONFIG_P54_PCI=m
CONFIG_P54_SPI=m
# CONFIG_P54_SPI_DEFAULT_EEPROM is not set
CONFIG_P54_LEDS=y
CONFIG_RT2X00=m
CONFIG_RT2400PCI=m
CONFIG_RT2500PCI=m
CONFIG_RT61PCI=m
CONFIG_RT2800PCI=m
CONFIG_RT2800PCI_RT33XX=y
CONFIG_RT2800PCI_RT35XX=y
CONFIG_RT2800PCI_RT53XX=y
CONFIG_RT2800PCI_RT3290=y
CONFIG_RT2500USB=m
CONFIG_RT73USB=m
CONFIG_RT2800USB=m
CONFIG_RT2800USB_RT33XX=y
CONFIG_RT2800USB_RT35XX=y
CONFIG_RT2800USB_RT3573=y
CONFIG_RT2800USB_RT53XX=y
CONFIG_RT2800USB_RT55XX=y
CONFIG_RT2800USB_UNKNOWN=y
CONFIG_RT2800_LIB=m
CONFIG_RT2800_LIB_MMIO=m
CONFIG_RT2X00_LIB_MMIO=m
CONFIG_RT2X00_LIB_PCI=m
CONFIG_RT2X00_LIB_USB=m
CONFIG_RT2X00_LIB=m
CONFIG_RT2X00_LIB_FIRMWARE=y
CONFIG_RT2X00_LIB_CRYPTO=y
CONFIG_RT2X00_LIB_LEDS=y
# CONFIG_RT2X00_LIB_DEBUGFS is not set
# CONFIG_RT2X00_DEBUG is not set
CONFIG_WL_MEDIATEK=y
CONFIG_MT7601U=m
CONFIG_RTL_CARDS=m
CONFIG_RTL8192CE=m
CONFIG_RTL8192SE=m
CONFIG_RTL8192DE=m
CONFIG_RTL8723AE=m
CONFIG_RTL8723BE=m
CONFIG_RTL8188EE=m
CONFIG_RTL8192EE=m
CONFIG_RTL8821AE=m
CONFIG_RTL8192CU=m
CONFIG_RTLWIFI=m
CONFIG_RTLWIFI_PCI=m
CONFIG_RTLWIFI_USB=m
# CONFIG_RTLWIFI_DEBUG is not set
CONFIG_RTL8192C_COMMON=m
CONFIG_RTL8723_COMMON=m
CONFIG_RTLBTCOEXIST=m
CONFIG_RTL8XXXU=m
CONFIG_RTL8XXXU_UNTESTED=y
CONFIG_WL_TI=y
CONFIG_WL1251=m
CONFIG_WL1251_SPI=m
CONFIG_WL1251_SDIO=m
CONFIG_WL12XX=m
CONFIG_WL18XX=m
CONFIG_WLCORE=m
CONFIG_WLCORE_SPI=m
CONFIG_WLCORE_SDIO=m
CONFIG_WILINK_PLATFORM_DATA=y
CONFIG_ZD1211RW=m
# CONFIG_ZD1211RW_DEBUG is not set
CONFIG_MWIFIEX=m
CONFIG_MWIFIEX_SDIO=m
CONFIG_MWIFIEX_PCIE=m
CONFIG_MWIFIEX_USB=m
CONFIG_CW1200=m
CONFIG_CW1200_WLAN_SDIO=m
CONFIG_CW1200_WLAN_SPI=m
CONFIG_RSI_91X=m
# CONFIG_RSI_DEBUGFS is not set
CONFIG_RSI_SDIO=m
CONFIG_RSI_USB=m

#
# WiMAX Wireless Broadband devices
#
CONFIG_WIMAX_I2400M=m
CONFIG_WIMAX_I2400M_USB=m
CONFIG_WIMAX_I2400M_DEBUG_LEVEL=8
CONFIG_WAN=y
CONFIG_LANMEDIA=m
CONFIG_HDLC=m
CONFIG_HDLC_RAW=m
CONFIG_HDLC_RAW_ETH=m
CONFIG_HDLC_CISCO=m
CONFIG_HDLC_FR=m
CONFIG_HDLC_PPP=m
CONFIG_HDLC_X25=m
CONFIG_PCI200SYN=m
CONFIG_WANXL=m
CONFIG_PC300TOO=m
CONFIG_FARSYNC=m
CONFIG_DSCC4=m
CONFIG_DSCC4_PCISYNC=y
CONFIG_DSCC4_PCI_RST=y
CONFIG_DLCI=m
CONFIG_DLCI_MAX=8
CONFIG_LAPBETHER=m
CONFIG_X25_ASY=m
CONFIG_SBNI=m
# CONFIG_SBNI_MULTILINE is not set
CONFIG_IEEE802154_DRIVERS=m
CONFIG_IEEE802154_FAKELB=m
CONFIG_IEEE802154_AT86RF230=m
CONFIG_IEEE802154_AT86RF230_DEBUGFS=y
CONFIG_IEEE802154_MRF24J40=m
CONFIG_IEEE802154_CC2520=m
CONFIG_IEEE802154_ATUSB=m
CONFIG_XEN_NETDEV_FRONTEND=y
CONFIG_XEN_NETDEV_BACKEND=m
CONFIG_VMXNET3=m
CONFIG_FUJITSU_ES=m
CONFIG_HYPERV_NET=m
CONFIG_ISDN=y
CONFIG_ISDN_I4L=m
CONFIG_ISDN_PPP=y
CONFIG_ISDN_PPP_VJ=y
CONFIG_ISDN_MPP=y
CONFIG_IPPP_FILTER=y
CONFIG_ISDN_PPP_BSDCOMP=m
CONFIG_ISDN_AUDIO=y
CONFIG_ISDN_TTY_FAX=y
CONFIG_ISDN_X25=y

#
# ISDN feature submodules
#
CONFIG_ISDN_DIVERSION=m

#
# ISDN4Linux hardware drivers
#

#
# Passive cards
#
CONFIG_ISDN_DRV_HISAX=m

#
# D-channel protocol features
#
CONFIG_HISAX_EURO=y
CONFIG_DE_AOC=y
# CONFIG_HISAX_NO_SENDCOMPLETE is not set
# CONFIG_HISAX_NO_LLC is not set
# CONFIG_HISAX_NO_KEYPAD is not set
CONFIG_HISAX_1TR6=y
CONFIG_HISAX_NI1=y
CONFIG_HISAX_MAX_CARDS=8

#
# HiSax supported cards
#
CONFIG_HISAX_16_3=y
CONFIG_HISAX_TELESPCI=y
CONFIG_HISAX_S0BOX=y
CONFIG_HISAX_FRITZPCI=y
CONFIG_HISAX_AVM_A1_PCMCIA=y
CONFIG_HISAX_ELSA=y
CONFIG_HISAX_DIEHLDIVA=y
CONFIG_HISAX_SEDLBAUER=y
CONFIG_HISAX_NETJET=y
CONFIG_HISAX_NETJET_U=y
CONFIG_HISAX_NICCY=y
CONFIG_HISAX_BKM_A4T=y
CONFIG_HISAX_SCT_QUADRO=y
CONFIG_HISAX_GAZEL=y
CONFIG_HISAX_HFC_PCI=y
CONFIG_HISAX_W6692=y
CONFIG_HISAX_HFC_SX=y
CONFIG_HISAX_ENTERNOW_PCI=y
# CONFIG_HISAX_DEBUG is not set

#
# HiSax PCMCIA card service modules
#
CONFIG_HISAX_SEDLBAUER_CS=m
CONFIG_HISAX_ELSA_CS=m
CONFIG_HISAX_AVM_A1_CS=m
CONFIG_HISAX_TELES_CS=m

#
# HiSax sub driver modules
#
CONFIG_HISAX_ST5481=m
CONFIG_HISAX_HFCUSB=m
CONFIG_HISAX_HFC4S8S=m
CONFIG_HISAX_FRITZ_PCIPNP=m

#
# Active cards
#
CONFIG_ISDN_CAPI=m
CONFIG_CAPI_TRACE=y
CONFIG_ISDN_CAPI_CAPI20=m
CONFIG_ISDN_CAPI_MIDDLEWARE=y
CONFIG_ISDN_CAPI_CAPIDRV=m
# CONFIG_ISDN_CAPI_CAPIDRV_VERBOSE is not set

#
# CAPI hardware drivers
#
CONFIG_CAPI_AVM=y
CONFIG_ISDN_DRV_AVMB1_B1PCI=m
CONFIG_ISDN_DRV_AVMB1_B1PCIV4=y
CONFIG_ISDN_DRV_AVMB1_B1PCMCIA=m
CONFIG_ISDN_DRV_AVMB1_AVM_CS=m
CONFIG_ISDN_DRV_AVMB1_T1PCI=m
CONFIG_ISDN_DRV_AVMB1_C4=m
CONFIG_CAPI_EICON=y
CONFIG_ISDN_DIVAS=m
CONFIG_ISDN_DIVAS_BRIPCI=y
CONFIG_ISDN_DIVAS_PRIPCI=y
CONFIG_ISDN_DIVAS_DIVACAPI=m
CONFIG_ISDN_DIVAS_USERIDI=m
CONFIG_ISDN_DIVAS_MAINT=m
CONFIG_ISDN_DRV_GIGASET=m
# CONFIG_GIGASET_CAPI is not set
CONFIG_GIGASET_I4L=y
# CONFIG_GIGASET_DUMMYLL is not set
CONFIG_GIGASET_BASE=m
CONFIG_GIGASET_M105=m
CONFIG_GIGASET_M101=m
# CONFIG_GIGASET_DEBUG is not set
CONFIG_HYSDN=m
CONFIG_HYSDN_CAPI=y
CONFIG_MISDN=m
CONFIG_MISDN_DSP=m
CONFIG_MISDN_L1OIP=m

#
# mISDN hardware drivers
#
CONFIG_MISDN_HFCPCI=m
CONFIG_MISDN_HFCMULTI=m
CONFIG_MISDN_HFCUSB=m
CONFIG_MISDN_AVMFRITZ=m
CONFIG_MISDN_SPEEDFAX=m
CONFIG_MISDN_INFINEON=m
CONFIG_MISDN_W6692=m
CONFIG_MISDN_NETJET=m
CONFIG_MISDN_IPAC=m
CONFIG_MISDN_ISAR=m
CONFIG_ISDN_HDLC=m
CONFIG_NVM=y
# CONFIG_NVM_DEBUG is not set
CONFIG_NVM_GENNVM=m
CONFIG_NVM_RRPC=m

#
# Input device support
#
CONFIG_INPUT=y
CONFIG_INPUT_LEDS=m
CONFIG_INPUT_FF_MEMLESS=m
CONFIG_INPUT_POLLDEV=m
CONFIG_INPUT_SPARSEKMAP=m
CONFIG_INPUT_MATRIXKMAP=m

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
CONFIG_INPUT_JOYDEV=m
CONFIG_INPUT_EVDEV=y
CONFIG_INPUT_EVBUG=m

#
# Input Device Drivers
#
CONFIG_INPUT_KEYBOARD=y
CONFIG_KEYBOARD_ADP5520=m
CONFIG_KEYBOARD_ADP5588=m
CONFIG_KEYBOARD_ADP5589=m
CONFIG_KEYBOARD_ATKBD=y
CONFIG_KEYBOARD_QT1070=m
CONFIG_KEYBOARD_QT2160=m
CONFIG_KEYBOARD_LKKBD=m
CONFIG_KEYBOARD_GPIO=m
CONFIG_KEYBOARD_GPIO_POLLED=m
CONFIG_KEYBOARD_TCA6416=m
CONFIG_KEYBOARD_TCA8418=m
CONFIG_KEYBOARD_MATRIX=m
CONFIG_KEYBOARD_LM8323=m
CONFIG_KEYBOARD_LM8333=m
CONFIG_KEYBOARD_MAX7359=m
CONFIG_KEYBOARD_MCS=m
CONFIG_KEYBOARD_MPR121=m
CONFIG_KEYBOARD_NEWTON=m
CONFIG_KEYBOARD_OPENCORES=m
CONFIG_KEYBOARD_SAMSUNG=m
CONFIG_KEYBOARD_STOWAWAY=m
CONFIG_KEYBOARD_SUNKBD=m
CONFIG_KEYBOARD_TWL4030=m
CONFIG_KEYBOARD_XTKBD=m
CONFIG_KEYBOARD_CROS_EC=m
CONFIG_INPUT_MOUSE=y
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_CYPRESS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
CONFIG_MOUSE_PS2_ELANTECH=y
CONFIG_MOUSE_PS2_SENTELIC=y
CONFIG_MOUSE_PS2_TOUCHKIT=y
CONFIG_MOUSE_PS2_FOCALTECH=y
CONFIG_MOUSE_PS2_VMMOUSE=y
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_APPLETOUCH=m
CONFIG_MOUSE_BCM5974=m
CONFIG_MOUSE_CYAPA=m
CONFIG_MOUSE_ELAN_I2C=m
CONFIG_MOUSE_ELAN_I2C_I2C=y
CONFIG_MOUSE_ELAN_I2C_SMBUS=y
CONFIG_MOUSE_VSXXXAA=m
CONFIG_MOUSE_GPIO=m
CONFIG_MOUSE_SYNAPTICS_I2C=m
CONFIG_MOUSE_SYNAPTICS_USB=m
CONFIG_INPUT_JOYSTICK=y
CONFIG_JOYSTICK_ANALOG=m
CONFIG_JOYSTICK_A3D=m
CONFIG_JOYSTICK_ADI=m
CONFIG_JOYSTICK_COBRA=m
CONFIG_JOYSTICK_GF2K=m
CONFIG_JOYSTICK_GRIP=m
CONFIG_JOYSTICK_GRIP_MP=m
CONFIG_JOYSTICK_GUILLEMOT=m
CONFIG_JOYSTICK_INTERACT=m
CONFIG_JOYSTICK_SIDEWINDER=m
CONFIG_JOYSTICK_TMDC=m
CONFIG_JOYSTICK_IFORCE=m
CONFIG_JOYSTICK_IFORCE_USB=y
CONFIG_JOYSTICK_IFORCE_232=y
CONFIG_JOYSTICK_WARRIOR=m
CONFIG_JOYSTICK_MAGELLAN=m
CONFIG_JOYSTICK_SPACEORB=m
CONFIG_JOYSTICK_SPACEBALL=m
CONFIG_JOYSTICK_STINGER=m
CONFIG_JOYSTICK_TWIDJOY=m
CONFIG_JOYSTICK_ZHENHUA=m
CONFIG_JOYSTICK_DB9=m
CONFIG_JOYSTICK_GAMECON=m
CONFIG_JOYSTICK_TURBOGRAFX=m
CONFIG_JOYSTICK_AS5011=m
CONFIG_JOYSTICK_JOYDUMP=m
CONFIG_JOYSTICK_XPAD=m
CONFIG_JOYSTICK_XPAD_FF=y
CONFIG_JOYSTICK_XPAD_LEDS=y
CONFIG_JOYSTICK_WALKERA0701=m
CONFIG_INPUT_TABLET=y
CONFIG_TABLET_USB_ACECAD=m
CONFIG_TABLET_USB_AIPTEK=m
CONFIG_TABLET_USB_GTCO=m
CONFIG_TABLET_USB_HANWANG=m
CONFIG_TABLET_USB_KBTAB=m
CONFIG_TABLET_SERIAL_WACOM4=m
CONFIG_INPUT_TOUCHSCREEN=y
CONFIG_TOUCHSCREEN_PROPERTIES=y
CONFIG_TOUCHSCREEN_88PM860X=m
CONFIG_TOUCHSCREEN_ADS7846=m
CONFIG_TOUCHSCREEN_AD7877=m
CONFIG_TOUCHSCREEN_AD7879=m
CONFIG_TOUCHSCREEN_AD7879_I2C=m
CONFIG_TOUCHSCREEN_AD7879_SPI=m
CONFIG_TOUCHSCREEN_ATMEL_MXT=m
CONFIG_TOUCHSCREEN_AUO_PIXCIR=m
CONFIG_TOUCHSCREEN_BU21013=m
CONFIG_TOUCHSCREEN_CY8CTMG110=m
CONFIG_TOUCHSCREEN_CYTTSP_CORE=m
CONFIG_TOUCHSCREEN_CYTTSP_I2C=m
CONFIG_TOUCHSCREEN_CYTTSP_SPI=m
CONFIG_TOUCHSCREEN_CYTTSP4_CORE=m
CONFIG_TOUCHSCREEN_CYTTSP4_I2C=m
CONFIG_TOUCHSCREEN_CYTTSP4_SPI=m
CONFIG_TOUCHSCREEN_DA9034=m
CONFIG_TOUCHSCREEN_DA9052=m
CONFIG_TOUCHSCREEN_DYNAPRO=m
CONFIG_TOUCHSCREEN_HAMPSHIRE=m
CONFIG_TOUCHSCREEN_EETI=m
CONFIG_TOUCHSCREEN_FT6236=m
CONFIG_TOUCHSCREEN_FUJITSU=m
CONFIG_TOUCHSCREEN_GOODIX=m
CONFIG_TOUCHSCREEN_ILI210X=m
CONFIG_TOUCHSCREEN_GUNZE=m
CONFIG_TOUCHSCREEN_ELAN=m
CONFIG_TOUCHSCREEN_ELO=m
CONFIG_TOUCHSCREEN_WACOM_W8001=m
CONFIG_TOUCHSCREEN_WACOM_I2C=m
CONFIG_TOUCHSCREEN_MAX11801=m
CONFIG_TOUCHSCREEN_MCS5000=m
CONFIG_TOUCHSCREEN_MMS114=m
CONFIG_TOUCHSCREEN_MTOUCH=m
CONFIG_TOUCHSCREEN_INEXIO=m
CONFIG_TOUCHSCREEN_MK712=m
CONFIG_TOUCHSCREEN_PENMOUNT=m
CONFIG_TOUCHSCREEN_EDT_FT5X06=m
CONFIG_TOUCHSCREEN_TOUCHRIGHT=m
CONFIG_TOUCHSCREEN_TOUCHWIN=m
CONFIG_TOUCHSCREEN_TI_AM335X_TSC=m
CONFIG_TOUCHSCREEN_UCB1400=m
CONFIG_TOUCHSCREEN_PIXCIR=m
CONFIG_TOUCHSCREEN_WDT87XX_I2C=m
CONFIG_TOUCHSCREEN_WM831X=m
CONFIG_TOUCHSCREEN_WM97XX=m
CONFIG_TOUCHSCREEN_WM9705=y
CONFIG_TOUCHSCREEN_WM9712=y
CONFIG_TOUCHSCREEN_WM9713=y
CONFIG_TOUCHSCREEN_USB_COMPOSITE=m
CONFIG_TOUCHSCREEN_MC13783=m
CONFIG_TOUCHSCREEN_USB_EGALAX=y
CONFIG_TOUCHSCREEN_USB_PANJIT=y
CONFIG_TOUCHSCREEN_USB_3M=y
CONFIG_TOUCHSCREEN_USB_ITM=y
CONFIG_TOUCHSCREEN_USB_ETURBO=y
CONFIG_TOUCHSCREEN_USB_GUNZE=y
CONFIG_TOUCHSCREEN_USB_DMC_TSC10=y
CONFIG_TOUCHSCREEN_USB_IRTOUCH=y
CONFIG_TOUCHSCREEN_USB_IDEALTEK=y
CONFIG_TOUCHSCREEN_USB_GENERAL_TOUCH=y
CONFIG_TOUCHSCREEN_USB_GOTOP=y
CONFIG_TOUCHSCREEN_USB_JASTEC=y
CONFIG_TOUCHSCREEN_USB_ELO=y
CONFIG_TOUCHSCREEN_USB_E2I=y
CONFIG_TOUCHSCREEN_USB_ZYTRONIC=y
CONFIG_TOUCHSCREEN_USB_ETT_TC45USB=y
CONFIG_TOUCHSCREEN_USB_NEXIO=y
CONFIG_TOUCHSCREEN_USB_EASYTOUCH=y
CONFIG_TOUCHSCREEN_TOUCHIT213=m
CONFIG_TOUCHSCREEN_TSC_SERIO=m
CONFIG_TOUCHSCREEN_TSC200X_CORE=m
CONFIG_TOUCHSCREEN_TSC2004=m
CONFIG_TOUCHSCREEN_TSC2005=m
CONFIG_TOUCHSCREEN_TSC2007=m
CONFIG_TOUCHSCREEN_PCAP=m
CONFIG_TOUCHSCREEN_ST1232=m
CONFIG_TOUCHSCREEN_SUR40=m
CONFIG_TOUCHSCREEN_SX8654=m
CONFIG_TOUCHSCREEN_TPS6507X=m
CONFIG_TOUCHSCREEN_ZFORCE=m
CONFIG_TOUCHSCREEN_ROHM_BU21023=m
CONFIG_INPUT_MISC=y
CONFIG_INPUT_88PM860X_ONKEY=m
CONFIG_INPUT_88PM80X_ONKEY=m
CONFIG_INPUT_AD714X=m
CONFIG_INPUT_AD714X_I2C=m
CONFIG_INPUT_AD714X_SPI=m
CONFIG_INPUT_ARIZONA_HAPTICS=m
CONFIG_INPUT_BMA150=m
CONFIG_INPUT_E3X0_BUTTON=m
CONFIG_INPUT_PCSPKR=m
CONFIG_INPUT_MAX77693_HAPTIC=m
CONFIG_INPUT_MAX8925_ONKEY=m
CONFIG_INPUT_MAX8997_HAPTIC=m
CONFIG_INPUT_MC13783_PWRBUTTON=m
CONFIG_INPUT_MMA8450=m
CONFIG_INPUT_MPU3050=m
CONFIG_INPUT_APANEL=m
CONFIG_INPUT_GP2A=m
CONFIG_INPUT_GPIO_BEEPER=m
CONFIG_INPUT_GPIO_TILT_POLLED=m
CONFIG_INPUT_ATLAS_BTNS=m
CONFIG_INPUT_ATI_REMOTE2=m
CONFIG_INPUT_KEYSPAN_REMOTE=m
CONFIG_INPUT_KXTJ9=m
# CONFIG_INPUT_KXTJ9_POLLED_MODE is not set
CONFIG_INPUT_POWERMATE=m
CONFIG_INPUT_YEALINK=m
CONFIG_INPUT_CM109=m
CONFIG_INPUT_REGULATOR_HAPTIC=m
CONFIG_INPUT_RETU_PWRBUTTON=m
CONFIG_INPUT_TPS65218_PWRBUTTON=m
CONFIG_INPUT_AXP20X_PEK=m
CONFIG_INPUT_TWL4030_PWRBUTTON=m
CONFIG_INPUT_TWL4030_VIBRA=m
CONFIG_INPUT_TWL6040_VIBRA=m
CONFIG_INPUT_UINPUT=y
CONFIG_INPUT_PALMAS_PWRBUTTON=m
CONFIG_INPUT_PCF50633_PMU=m
CONFIG_INPUT_PCF8574=m
CONFIG_INPUT_PWM_BEEPER=m
CONFIG_INPUT_GPIO_ROTARY_ENCODER=m
CONFIG_INPUT_DA9052_ONKEY=m
CONFIG_INPUT_DA9055_ONKEY=m
CONFIG_INPUT_DA9063_ONKEY=m
CONFIG_INPUT_WM831X_ON=m
CONFIG_INPUT_PCAP=m
CONFIG_INPUT_ADXL34X=m
CONFIG_INPUT_ADXL34X_I2C=m
CONFIG_INPUT_ADXL34X_SPI=m
CONFIG_INPUT_IMS_PCU=m
CONFIG_INPUT_CMA3000=m
CONFIG_INPUT_CMA3000_I2C=m
CONFIG_INPUT_XEN_KBDDEV_FRONTEND=m
CONFIG_INPUT_IDEAPAD_SLIDEBAR=m
CONFIG_INPUT_SOC_BUTTON_ARRAY=m
CONFIG_INPUT_DRV260X_HAPTICS=m
CONFIG_INPUT_DRV2665_HAPTICS=m
CONFIG_INPUT_DRV2667_HAPTICS=m

#
# Hardware I/O ports
#
CONFIG_SERIO=y
CONFIG_ARCH_MIGHT_HAVE_PC_SERIO=y
CONFIG_SERIO_I8042=y
CONFIG_SERIO_SERPORT=m
CONFIG_SERIO_CT82C710=m
CONFIG_SERIO_PARKBD=m
CONFIG_SERIO_PCIPS2=m
CONFIG_SERIO_LIBPS2=y
CONFIG_SERIO_RAW=m
CONFIG_SERIO_ALTERA_PS2=m
CONFIG_SERIO_PS2MULT=m
CONFIG_SERIO_ARC_PS2=m
CONFIG_HYPERV_KEYBOARD=m
CONFIG_USERIO=m
CONFIG_GAMEPORT=m
CONFIG_GAMEPORT_NS558=m
CONFIG_GAMEPORT_L4=m
CONFIG_GAMEPORT_EMU10K1=m
CONFIG_GAMEPORT_FM801=m

#
# Character devices
#
CONFIG_TTY=y
CONFIG_VT=y
CONFIG_CONSOLE_TRANSLATIONS=y
CONFIG_VT_CONSOLE=y
CONFIG_VT_CONSOLE_SLEEP=y
CONFIG_HW_CONSOLE=y
CONFIG_VT_HW_CONSOLE_BINDING=y
CONFIG_UNIX98_PTYS=y
CONFIG_DEVPTS_MULTIPLE_INSTANCES=y
CONFIG_LEGACY_PTYS=y
CONFIG_LEGACY_PTY_COUNT=0
CONFIG_SERIAL_NONSTANDARD=y
CONFIG_ROCKETPORT=m
CONFIG_CYCLADES=m
# CONFIG_CYZ_INTR is not set
CONFIG_MOXA_INTELLIO=m
CONFIG_MOXA_SMARTIO=m
CONFIG_SYNCLINK=m
CONFIG_SYNCLINKMP=m
CONFIG_SYNCLINK_GT=m
CONFIG_NOZOMI=m
CONFIG_ISI=m
CONFIG_N_HDLC=m
CONFIG_N_GSM=m
CONFIG_TRACE_ROUTER=m
CONFIG_TRACE_SINK=m
CONFIG_DEVMEM=y
# CONFIG_DEVKMEM is not set

#
# Serial drivers
#
CONFIG_SERIAL_EARLYCON=y
CONFIG_SERIAL_8250=y
# CONFIG_SERIAL_8250_DEPRECATED_OPTIONS is not set
CONFIG_SERIAL_8250_PNP=y
CONFIG_SERIAL_8250_CONSOLE=y
CONFIG_SERIAL_8250_DMA=y
CONFIG_SERIAL_8250_PCI=y
CONFIG_SERIAL_8250_CS=m
CONFIG_SERIAL_8250_NR_UARTS=48
CONFIG_SERIAL_8250_RUNTIME_UARTS=32
CONFIG_SERIAL_8250_EXTENDED=y
CONFIG_SERIAL_8250_MANY_PORTS=y
CONFIG_SERIAL_8250_SHARE_IRQ=y
# CONFIG_SERIAL_8250_DETECT_IRQ is not set
CONFIG_SERIAL_8250_RSA=y
# CONFIG_SERIAL_8250_FSL is not set
CONFIG_SERIAL_8250_DW=m
CONFIG_SERIAL_8250_RT288X=y
CONFIG_SERIAL_8250_FINTEK=m
CONFIG_SERIAL_8250_MID=m

#
# Non-8250 serial port support
#
CONFIG_SERIAL_KGDB_NMI=y
CONFIG_SERIAL_MAX3100=m
CONFIG_SERIAL_MAX310X=y
CONFIG_SERIAL_UARTLITE=m
CONFIG_SERIAL_CORE=y
CONFIG_SERIAL_CORE_CONSOLE=y
CONFIG_CONSOLE_POLL=y
CONFIG_SERIAL_JSM=m
CONFIG_SERIAL_SCCNXP=y
CONFIG_SERIAL_SCCNXP_CONSOLE=y
CONFIG_SERIAL_SC16IS7XX_CORE=m
CONFIG_SERIAL_SC16IS7XX=m
CONFIG_SERIAL_SC16IS7XX_I2C=y
CONFIG_SERIAL_SC16IS7XX_SPI=y
CONFIG_SERIAL_ALTERA_JTAGUART=m
CONFIG_SERIAL_ALTERA_UART=m
CONFIG_SERIAL_ALTERA_UART_MAXPORTS=4
CONFIG_SERIAL_ALTERA_UART_BAUDRATE=115200
# CONFIG_SERIAL_IFX6X60 is not set
CONFIG_SERIAL_ARC=m
CONFIG_SERIAL_ARC_NR_PORTS=1
CONFIG_SERIAL_RP2=m
CONFIG_SERIAL_RP2_NR_UARTS=32
CONFIG_SERIAL_FSL_LPUART=m
CONFIG_SERIAL_MEN_Z135=m
CONFIG_TTY_PRINTK=y
CONFIG_PRINTER=m
# CONFIG_LP_CONSOLE is not set
CONFIG_PPDEV=m
CONFIG_HVC_DRIVER=y
CONFIG_HVC_IRQ=y
CONFIG_HVC_XEN=y
CONFIG_HVC_XEN_FRONTEND=y
CONFIG_VIRTIO_CONSOLE=y
CONFIG_IPMI_HANDLER=m
# CONFIG_IPMI_PANIC_EVENT is not set
CONFIG_IPMI_DEVICE_INTERFACE=m
CONFIG_IPMI_SI=m
CONFIG_IPMI_SI_PROBE_DEFAULTS=y
CONFIG_IPMI_SSIF=m
CONFIG_IPMI_WATCHDOG=m
CONFIG_IPMI_POWEROFF=m
CONFIG_HW_RANDOM=y
CONFIG_HW_RANDOM_TIMERIOMEM=m
CONFIG_HW_RANDOM_INTEL=m
CONFIG_HW_RANDOM_AMD=m
CONFIG_HW_RANDOM_VIA=m
CONFIG_HW_RANDOM_VIRTIO=m
CONFIG_HW_RANDOM_TPM=m
CONFIG_NVRAM=m
CONFIG_R3964=m
CONFIG_APPLICOM=m

#
# PCMCIA character devices
#
CONFIG_SYNCLINK_CS=m
CONFIG_CARDMAN_4000=m
CONFIG_CARDMAN_4040=m
CONFIG_IPWIRELESS=m
CONFIG_MWAVE=m
CONFIG_RAW_DRIVER=m
CONFIG_MAX_RAW_DEVS=256
CONFIG_HPET=y
CONFIG_HPET_MMAP=y
CONFIG_HPET_MMAP_DEFAULT=y
CONFIG_HANGCHECK_TIMER=m
CONFIG_TCG_TPM=y
CONFIG_TCG_TIS=y
CONFIG_TCG_TIS_I2C_ATMEL=m
CONFIG_TCG_TIS_I2C_INFINEON=m
CONFIG_TCG_TIS_I2C_NUVOTON=m
CONFIG_TCG_NSC=m
CONFIG_TCG_ATMEL=m
CONFIG_TCG_INFINEON=m
CONFIG_TCG_XEN=m
CONFIG_TCG_CRB=m
CONFIG_TCG_TIS_ST33ZP24=m
CONFIG_TCG_TIS_ST33ZP24_I2C=m
CONFIG_TCG_TIS_ST33ZP24_SPI=m
CONFIG_TELCLOCK=m
CONFIG_DEVPORT=y
CONFIG_XILLYBUS=m
CONFIG_XILLYBUS_PCIE=m

#
# I2C support
#
CONFIG_I2C=y
CONFIG_ACPI_I2C_OPREGION=y
CONFIG_I2C_BOARDINFO=y
CONFIG_I2C_COMPAT=y
CONFIG_I2C_CHARDEV=y
CONFIG_I2C_MUX=m

#
# Multiplexer I2C Chip support
#
CONFIG_I2C_MUX_GPIO=m
CONFIG_I2C_MUX_PCA9541=m
CONFIG_I2C_MUX_PCA954x=m
CONFIG_I2C_MUX_PINCTRL=m
CONFIG_I2C_MUX_REG=m
CONFIG_I2C_HELPER_AUTO=y
CONFIG_I2C_SMBUS=m
CONFIG_I2C_ALGOBIT=m
CONFIG_I2C_ALGOPCA=m

#
# I2C Hardware Bus support
#

#
# PC SMBus host controller drivers
#
CONFIG_I2C_ALI1535=m
CONFIG_I2C_ALI1563=m
CONFIG_I2C_ALI15X3=m
CONFIG_I2C_AMD756=m
CONFIG_I2C_AMD756_S4882=m
CONFIG_I2C_AMD8111=m
CONFIG_I2C_I801=m
CONFIG_I2C_ISCH=m
CONFIG_I2C_ISMT=m
CONFIG_I2C_PIIX4=m
CONFIG_I2C_NFORCE2=m
CONFIG_I2C_NFORCE2_S4985=m
CONFIG_I2C_SIS5595=m
CONFIG_I2C_SIS630=m
CONFIG_I2C_SIS96X=m
CONFIG_I2C_VIA=m
CONFIG_I2C_VIAPRO=m

#
# ACPI drivers
#
CONFIG_I2C_SCMI=m

#
# I2C system bus drivers (mostly embedded / system-on-chip)
#
CONFIG_I2C_CBUS_GPIO=m
CONFIG_I2C_DESIGNWARE_CORE=m
CONFIG_I2C_DESIGNWARE_PLATFORM=m
CONFIG_I2C_DESIGNWARE_PCI=m
CONFIG_I2C_DESIGNWARE_BAYTRAIL=y
CONFIG_I2C_EMEV2=m
CONFIG_I2C_GPIO=m
CONFIG_I2C_KEMPLD=m
CONFIG_I2C_OCORES=m
CONFIG_I2C_PCA_PLATFORM=m
# CONFIG_I2C_PXA_PCI is not set
CONFIG_I2C_SIMTEC=m
CONFIG_I2C_XILINX=m

#
# External I2C/SMBus adapter drivers
#
CONFIG_I2C_DIOLAN_U2C=m
CONFIG_I2C_DLN2=m
CONFIG_I2C_PARPORT=m
CONFIG_I2C_PARPORT_LIGHT=m
CONFIG_I2C_ROBOTFUZZ_OSIF=m
CONFIG_I2C_TAOS_EVM=m
CONFIG_I2C_TINY_USB=m
CONFIG_I2C_VIPERBOARD=m

#
# Other I2C/SMBus bus drivers
#
CONFIG_I2C_CROS_EC_TUNNEL=m
CONFIG_I2C_STUB=m
# CONFIG_I2C_SLAVE is not set
# CONFIG_I2C_DEBUG_CORE is not set
# CONFIG_I2C_DEBUG_ALGO is not set
# CONFIG_I2C_DEBUG_BUS is not set
CONFIG_SPI=y
# CONFIG_SPI_DEBUG is not set
CONFIG_SPI_MASTER=y

#
# SPI Master Controller Drivers
#
CONFIG_SPI_ALTERA=m
CONFIG_SPI_BITBANG=m
CONFIG_SPI_BUTTERFLY=m
CONFIG_SPI_CADENCE=m
CONFIG_SPI_DLN2=m
CONFIG_SPI_GPIO=m
CONFIG_SPI_LM70_LLP=m
CONFIG_SPI_OC_TINY=m
CONFIG_SPI_PXA2XX_DMA=y
CONFIG_SPI_PXA2XX=m
CONFIG_SPI_PXA2XX_PCI=m
CONFIG_SPI_SC18IS602=m
CONFIG_SPI_XCOMM=m
# CONFIG_SPI_XILINX is not set
CONFIG_SPI_ZYNQMP_GQSPI=m
CONFIG_SPI_DESIGNWARE=m
CONFIG_SPI_DW_PCI=m
CONFIG_SPI_DW_MID_DMA=y
CONFIG_SPI_DW_MMIO=m

#
# SPI Protocol Masters
#
CONFIG_SPI_SPIDEV=m
CONFIG_SPI_TLE62X0=m
CONFIG_SPMI=m
CONFIG_HSI=m
CONFIG_HSI_BOARDINFO=y

#
# HSI controllers
#

#
# HSI clients
#
CONFIG_HSI_CHAR=m

#
# PPS support
#
CONFIG_PPS=m
# CONFIG_PPS_DEBUG is not set

#
# PPS clients support
#
# CONFIG_PPS_CLIENT_KTIMER is not set
CONFIG_PPS_CLIENT_LDISC=m
CONFIG_PPS_CLIENT_PARPORT=m
CONFIG_PPS_CLIENT_GPIO=m

#
# PPS generators support
#

#
# PTP clock support
#
CONFIG_PTP_1588_CLOCK=m

#
# Enable PHYLIB and NETWORK_PHY_TIMESTAMPING to see the additional clocks.
#
CONFIG_PINCTRL=y

#
# Pin controllers
#
CONFIG_PINMUX=y
CONFIG_PINCONF=y
CONFIG_GENERIC_PINCONF=y
# CONFIG_DEBUG_PINCTRL is not set
CONFIG_PINCTRL_AMD=y
CONFIG_PINCTRL_BAYTRAIL=y
CONFIG_PINCTRL_CHERRYVIEW=m
CONFIG_PINCTRL_INTEL=m
CONFIG_PINCTRL_BROXTON=m
CONFIG_PINCTRL_SUNRISEPOINT=m
CONFIG_ARCH_WANT_OPTIONAL_GPIOLIB=y
CONFIG_GPIOLIB=y
CONFIG_GPIO_DEVRES=y
CONFIG_GPIO_ACPI=y
CONFIG_GPIOLIB_IRQCHIP=y
# CONFIG_DEBUG_GPIO is not set
CONFIG_GPIO_SYSFS=y
CONFIG_GPIO_GENERIC=m
CONFIG_GPIO_MAX730X=m

#
# Memory mapped GPIO drivers
#
CONFIG_GPIO_AMDPT=m
CONFIG_GPIO_DWAPB=m
CONFIG_GPIO_GENERIC_PLATFORM=m
CONFIG_GPIO_ICH=m
CONFIG_GPIO_LYNXPOINT=y
CONFIG_GPIO_VX855=m
CONFIG_GPIO_ZX=y

#
# Port-mapped I/O GPIO drivers
#
CONFIG_GPIO_104_IDIO_16=m
CONFIG_GPIO_F7188X=m
CONFIG_GPIO_IT87=m
CONFIG_GPIO_SCH=m
CONFIG_GPIO_SCH311X=m

#
# I2C GPIO expanders
#
CONFIG_GPIO_ADP5588=m
CONFIG_GPIO_MAX7300=m
CONFIG_GPIO_MAX732X=m
CONFIG_GPIO_PCA953X=m
CONFIG_GPIO_PCF857X=m
CONFIG_GPIO_SX150X=y

#
# MFD GPIO expanders
#
CONFIG_GPIO_ADP5520=m
CONFIG_GPIO_ARIZONA=m
CONFIG_GPIO_CRYSTAL_COVE=m
CONFIG_GPIO_DA9052=m
CONFIG_GPIO_DA9055=m
CONFIG_GPIO_DLN2=m
CONFIG_GPIO_JANZ_TTL=m
CONFIG_GPIO_KEMPLD=m
CONFIG_GPIO_LP3943=m
CONFIG_GPIO_PALMAS=y
CONFIG_GPIO_RC5T583=y
CONFIG_GPIO_TPS6586X=y
CONFIG_GPIO_TPS65910=y
CONFIG_GPIO_TPS65912=m
CONFIG_GPIO_TWL4030=m
CONFIG_GPIO_TWL6040=m
CONFIG_GPIO_UCB1400=m
CONFIG_GPIO_WM831X=m
CONFIG_GPIO_WM8350=m
CONFIG_GPIO_WM8994=m

#
# PCI GPIO expanders
#
CONFIG_GPIO_AMD8111=m
CONFIG_GPIO_INTEL_MID=y
CONFIG_GPIO_ML_IOH=m
CONFIG_GPIO_RDC321X=m

#
# SPI GPIO expanders
#
CONFIG_GPIO_MAX7301=m
CONFIG_GPIO_MC33880=m

#
# SPI or I2C GPIO expanders
#
CONFIG_GPIO_MCP23S08=m

#
# USB GPIO expanders
#
CONFIG_GPIO_VIPERBOARD=m
CONFIG_W1=m
CONFIG_W1_CON=y

#
# 1-wire Bus Masters
#
CONFIG_W1_MASTER_MATROX=m
CONFIG_W1_MASTER_DS2490=m
CONFIG_W1_MASTER_DS2482=m
CONFIG_W1_MASTER_DS1WM=m
CONFIG_W1_MASTER_GPIO=m

#
# 1-wire Slaves
#
CONFIG_W1_SLAVE_THERM=m
CONFIG_W1_SLAVE_SMEM=m
CONFIG_W1_SLAVE_DS2408=m
CONFIG_W1_SLAVE_DS2408_READBACK=y
CONFIG_W1_SLAVE_DS2413=m
CONFIG_W1_SLAVE_DS2406=m
CONFIG_W1_SLAVE_DS2423=m
CONFIG_W1_SLAVE_DS2431=m
CONFIG_W1_SLAVE_DS2433=m
# CONFIG_W1_SLAVE_DS2433_CRC is not set
CONFIG_W1_SLAVE_DS2760=m
CONFIG_W1_SLAVE_DS2780=m
CONFIG_W1_SLAVE_DS2781=m
CONFIG_W1_SLAVE_DS28E04=m
CONFIG_W1_SLAVE_BQ27000=m
CONFIG_POWER_SUPPLY=y
# CONFIG_POWER_SUPPLY_DEBUG is not set
CONFIG_PDA_POWER=m
CONFIG_GENERIC_ADC_BATTERY=m
CONFIG_MAX8925_POWER=m
CONFIG_WM831X_BACKUP=m
CONFIG_WM831X_POWER=m
CONFIG_WM8350_POWER=m
CONFIG_TEST_POWER=m
CONFIG_BATTERY_88PM860X=m
CONFIG_BATTERY_DS2760=m
CONFIG_BATTERY_DS2780=m
CONFIG_BATTERY_DS2781=m
CONFIG_BATTERY_DS2782=m
CONFIG_BATTERY_SBS=m
CONFIG_BATTERY_BQ27XXX=m
CONFIG_BATTERY_BQ27XXX_I2C=y
CONFIG_BATTERY_BQ27XXX_PLATFORM=y
CONFIG_BATTERY_DA9030=m
CONFIG_BATTERY_DA9052=m
CONFIG_CHARGER_DA9150=m
CONFIG_BATTERY_DA9150=m
CONFIG_AXP288_CHARGER=m
CONFIG_AXP288_FUEL_GAUGE=m
CONFIG_BATTERY_MAX17040=m
CONFIG_BATTERY_MAX17042=m
CONFIG_BATTERY_TWL4030_MADC=m
CONFIG_CHARGER_88PM860X=m
CONFIG_CHARGER_PCF50633=m
CONFIG_BATTERY_RX51=m
CONFIG_CHARGER_ISP1704=m
CONFIG_CHARGER_MAX8903=m
CONFIG_CHARGER_TWL4030=m
CONFIG_CHARGER_LP8727=m
CONFIG_CHARGER_LP8788=m
CONFIG_CHARGER_GPIO=m
CONFIG_CHARGER_MANAGER=y
CONFIG_CHARGER_MAX14577=m
CONFIG_CHARGER_MAX77693=m
CONFIG_CHARGER_MAX8997=m
CONFIG_CHARGER_MAX8998=m
CONFIG_CHARGER_BQ2415X=m
CONFIG_CHARGER_BQ24190=m
CONFIG_CHARGER_BQ24257=m
CONFIG_CHARGER_BQ24735=m
CONFIG_CHARGER_BQ25890=m
CONFIG_CHARGER_SMB347=m
CONFIG_CHARGER_TPS65090=m
CONFIG_CHARGER_TPS65217=m
CONFIG_BATTERY_GAUGE_LTC2941=m
CONFIG_BATTERY_RT5033=m
CONFIG_CHARGER_RT9455=m
CONFIG_AXP20X_POWER=m
CONFIG_POWER_RESET=y
CONFIG_POWER_RESET_RESTART=y
CONFIG_POWER_AVS=y
CONFIG_HWMON=y
CONFIG_HWMON_VID=m
# CONFIG_HWMON_DEBUG_CHIP is not set

#
# Native drivers
#
CONFIG_SENSORS_ABITUGURU=m
CONFIG_SENSORS_ABITUGURU3=m
CONFIG_SENSORS_AD7314=m
CONFIG_SENSORS_AD7414=m
CONFIG_SENSORS_AD7418=m
CONFIG_SENSORS_ADM1021=m
CONFIG_SENSORS_ADM1025=m
CONFIG_SENSORS_ADM1026=m
CONFIG_SENSORS_ADM1029=m
CONFIG_SENSORS_ADM1031=m
CONFIG_SENSORS_ADM9240=m
CONFIG_SENSORS_ADT7X10=m
CONFIG_SENSORS_ADT7310=m
CONFIG_SENSORS_ADT7410=m
CONFIG_SENSORS_ADT7411=m
CONFIG_SENSORS_ADT7462=m
CONFIG_SENSORS_ADT7470=m
CONFIG_SENSORS_ADT7475=m
CONFIG_SENSORS_ASC7621=m
CONFIG_SENSORS_K8TEMP=m
CONFIG_SENSORS_K10TEMP=m
CONFIG_SENSORS_FAM15H_POWER=m
CONFIG_SENSORS_APPLESMC=m
CONFIG_SENSORS_ASB100=m
CONFIG_SENSORS_ATXP1=m
CONFIG_SENSORS_DS620=m
CONFIG_SENSORS_DS1621=m
CONFIG_SENSORS_DELL_SMM=m
CONFIG_SENSORS_DA9052_ADC=m
CONFIG_SENSORS_DA9055=m
CONFIG_SENSORS_I5K_AMB=m
CONFIG_SENSORS_F71805F=m
CONFIG_SENSORS_F71882FG=m
CONFIG_SENSORS_F75375S=m
CONFIG_SENSORS_MC13783_ADC=m
CONFIG_SENSORS_FSCHMD=m
CONFIG_SENSORS_GL518SM=m
CONFIG_SENSORS_GL520SM=m
CONFIG_SENSORS_G760A=m
CONFIG_SENSORS_G762=m
CONFIG_SENSORS_GPIO_FAN=m
CONFIG_SENSORS_HIH6130=m
CONFIG_SENSORS_IBMAEM=m
CONFIG_SENSORS_IBMPEX=m
CONFIG_SENSORS_IIO_HWMON=m
CONFIG_SENSORS_I5500=m
CONFIG_SENSORS_CORETEMP=m
CONFIG_SENSORS_IT87=m
CONFIG_SENSORS_JC42=m
CONFIG_SENSORS_POWR1220=m
CONFIG_SENSORS_LINEAGE=m
CONFIG_SENSORS_LTC2945=m
CONFIG_SENSORS_LTC4151=m
CONFIG_SENSORS_LTC4215=m
CONFIG_SENSORS_LTC4222=m
CONFIG_SENSORS_LTC4245=m
CONFIG_SENSORS_LTC4260=m
CONFIG_SENSORS_LTC4261=m
CONFIG_SENSORS_MAX1111=m
CONFIG_SENSORS_MAX16065=m
CONFIG_SENSORS_MAX1619=m
CONFIG_SENSORS_MAX1668=m
CONFIG_SENSORS_MAX197=m
CONFIG_SENSORS_MAX6639=m
CONFIG_SENSORS_MAX6642=m
CONFIG_SENSORS_MAX6650=m
CONFIG_SENSORS_MAX6697=m
CONFIG_SENSORS_MAX31790=m
CONFIG_SENSORS_HTU21=m
CONFIG_SENSORS_MCP3021=m
CONFIG_SENSORS_MENF21BMC_HWMON=m
CONFIG_SENSORS_ADCXX=m
CONFIG_SENSORS_LM63=m
CONFIG_SENSORS_LM70=m
CONFIG_SENSORS_LM73=m
CONFIG_SENSORS_LM75=m
CONFIG_SENSORS_LM77=m
CONFIG_SENSORS_LM78=m
CONFIG_SENSORS_LM80=m
CONFIG_SENSORS_LM83=m
CONFIG_SENSORS_LM85=m
CONFIG_SENSORS_LM87=m
CONFIG_SENSORS_LM90=m
CONFIG_SENSORS_LM92=m
CONFIG_SENSORS_LM93=m
CONFIG_SENSORS_LM95234=m
CONFIG_SENSORS_LM95241=m
CONFIG_SENSORS_LM95245=m
CONFIG_SENSORS_PC87360=m
CONFIG_SENSORS_PC87427=m
CONFIG_SENSORS_NTC_THERMISTOR=m
CONFIG_SENSORS_NCT6683=m
CONFIG_SENSORS_NCT6775=m
CONFIG_SENSORS_NCT7802=m
CONFIG_SENSORS_NCT7904=m
CONFIG_SENSORS_PCF8591=m
CONFIG_PMBUS=m
CONFIG_SENSORS_PMBUS=m
CONFIG_SENSORS_ADM1275=m
CONFIG_SENSORS_LM25066=m
CONFIG_SENSORS_LTC2978=m
CONFIG_SENSORS_LTC2978_REGULATOR=y
CONFIG_SENSORS_MAX16064=m
CONFIG_SENSORS_MAX20751=m
CONFIG_SENSORS_MAX34440=m
CONFIG_SENSORS_MAX8688=m
CONFIG_SENSORS_TPS40422=m
CONFIG_SENSORS_UCD9000=m
CONFIG_SENSORS_UCD9200=m
CONFIG_SENSORS_ZL6100=m
CONFIG_SENSORS_SHT15=m
CONFIG_SENSORS_SHT21=m
CONFIG_SENSORS_SHTC1=m
CONFIG_SENSORS_SIS5595=m
CONFIG_SENSORS_DME1737=m
CONFIG_SENSORS_EMC1403=m
CONFIG_SENSORS_EMC2103=m
CONFIG_SENSORS_EMC6W201=m
CONFIG_SENSORS_SMSC47M1=m
CONFIG_SENSORS_SMSC47M192=m
CONFIG_SENSORS_SMSC47B397=m
CONFIG_SENSORS_SCH56XX_COMMON=m
CONFIG_SENSORS_SCH5627=m
CONFIG_SENSORS_SCH5636=m
CONFIG_SENSORS_SMM665=m
CONFIG_SENSORS_ADC128D818=m
CONFIG_SENSORS_ADS1015=m
CONFIG_SENSORS_ADS7828=m
CONFIG_SENSORS_ADS7871=m
CONFIG_SENSORS_AMC6821=m
CONFIG_SENSORS_INA209=m
CONFIG_SENSORS_INA2XX=m
CONFIG_SENSORS_TC74=m
CONFIG_SENSORS_THMC50=m
CONFIG_SENSORS_TMP102=m
CONFIG_SENSORS_TMP103=m
CONFIG_SENSORS_TMP401=m
CONFIG_SENSORS_TMP421=m
CONFIG_SENSORS_TWL4030_MADC=m
CONFIG_SENSORS_VIA_CPUTEMP=m
CONFIG_SENSORS_VIA686A=m
CONFIG_SENSORS_VT1211=m
CONFIG_SENSORS_VT8231=m
CONFIG_SENSORS_W83781D=m
CONFIG_SENSORS_W83791D=m
CONFIG_SENSORS_W83792D=m
CONFIG_SENSORS_W83793=m
CONFIG_SENSORS_W83795=m
# CONFIG_SENSORS_W83795_FANCTRL is not set
CONFIG_SENSORS_W83L785TS=m
CONFIG_SENSORS_W83L786NG=m
CONFIG_SENSORS_W83627HF=m
CONFIG_SENSORS_W83627EHF=m
CONFIG_SENSORS_WM831X=m
CONFIG_SENSORS_WM8350=m

#
# ACPI drivers
#
CONFIG_SENSORS_ACPI_POWER=m
CONFIG_SENSORS_ATK0110=m
CONFIG_THERMAL=y
CONFIG_THERMAL_HWMON=y
CONFIG_THERMAL_WRITABLE_TRIPS=y
CONFIG_THERMAL_DEFAULT_GOV_STEP_WISE=y
# CONFIG_THERMAL_DEFAULT_GOV_FAIR_SHARE is not set
# CONFIG_THERMAL_DEFAULT_GOV_USER_SPACE is not set
# CONFIG_THERMAL_DEFAULT_GOV_POWER_ALLOCATOR is not set
CONFIG_THERMAL_GOV_FAIR_SHARE=y
CONFIG_THERMAL_GOV_STEP_WISE=y
CONFIG_THERMAL_GOV_BANG_BANG=y
CONFIG_THERMAL_GOV_USER_SPACE=y
CONFIG_THERMAL_GOV_POWER_ALLOCATOR=y
CONFIG_THERMAL_EMULATION=y
CONFIG_INTEL_POWERCLAMP=m
CONFIG_X86_PKG_TEMP_THERMAL=m
CONFIG_INTEL_SOC_DTS_IOSF_CORE=m
CONFIG_INTEL_SOC_DTS_THERMAL=m
CONFIG_INT340X_THERMAL=m
CONFIG_ACPI_THERMAL_REL=m
CONFIG_INTEL_PCH_THERMAL=m
CONFIG_WATCHDOG=y
CONFIG_WATCHDOG_CORE=y
# CONFIG_WATCHDOG_NOWAYOUT is not set

#
# Watchdog Device Drivers
#
CONFIG_SOFT_WATCHDOG=m
CONFIG_DA9052_WATCHDOG=m
CONFIG_DA9055_WATCHDOG=m
CONFIG_DA9063_WATCHDOG=m
CONFIG_DA9062_WATCHDOG=m
CONFIG_MENF21BMC_WATCHDOG=m
CONFIG_WM831X_WATCHDOG=m
CONFIG_WM8350_WATCHDOG=m
CONFIG_XILINX_WATCHDOG=m
CONFIG_CADENCE_WATCHDOG=m
CONFIG_DW_WATCHDOG=m
CONFIG_RN5T618_WATCHDOG=m
CONFIG_TWL4030_WATCHDOG=m
CONFIG_MAX63XX_WATCHDOG=m
CONFIG_RETU_WATCHDOG=m
CONFIG_ACQUIRE_WDT=m
CONFIG_ADVANTECH_WDT=m
CONFIG_ALIM1535_WDT=m
CONFIG_ALIM7101_WDT=m
CONFIG_F71808E_WDT=m
CONFIG_SP5100_TCO=m
CONFIG_SBC_FITPC2_WATCHDOG=m
CONFIG_EUROTECH_WDT=m
CONFIG_IB700_WDT=m
CONFIG_IBMASR=m
CONFIG_WAFER_WDT=m
CONFIG_I6300ESB_WDT=m
CONFIG_IE6XX_WDT=m
CONFIG_ITCO_WDT=m
CONFIG_ITCO_VENDOR_SUPPORT=y
CONFIG_IT8712F_WDT=m
CONFIG_IT87_WDT=m
CONFIG_HP_WATCHDOG=m
CONFIG_KEMPLD_WDT=m
CONFIG_HPWDT_NMI_DECODING=y
CONFIG_SC1200_WDT=m
CONFIG_PC87413_WDT=m
CONFIG_NV_TCO=m
CONFIG_60XX_WDT=m
CONFIG_CPU5_WDT=m
CONFIG_SMSC_SCH311X_WDT=m
CONFIG_SMSC37B787_WDT=m
CONFIG_VIA_WDT=m
CONFIG_W83627HF_WDT=m
CONFIG_W83877F_WDT=m
CONFIG_W83977F_WDT=m
CONFIG_MACHZ_WDT=m
CONFIG_SBC_EPX_C3_WATCHDOG=m
CONFIG_BCM7038_WDT=m
CONFIG_MEN_A21_WDT=m
CONFIG_XEN_WDT=m

#
# PCI-based Watchdog Cards
#
CONFIG_PCIPCWATCHDOG=m
CONFIG_WDTPCI=m

#
# USB-based Watchdog Cards
#
CONFIG_USBPCWATCHDOG=m
CONFIG_SSB_POSSIBLE=y

#
# Sonics Silicon Backplane
#
CONFIG_SSB=m
CONFIG_SSB_SPROM=y
CONFIG_SSB_BLOCKIO=y
CONFIG_SSB_PCIHOST_POSSIBLE=y
CONFIG_SSB_PCIHOST=y
CONFIG_SSB_B43_PCI_BRIDGE=y
CONFIG_SSB_PCMCIAHOST_POSSIBLE=y
# CONFIG_SSB_PCMCIAHOST is not set
CONFIG_SSB_SDIOHOST_POSSIBLE=y
CONFIG_SSB_SDIOHOST=y
CONFIG_SSB_HOST_SOC=y
# CONFIG_SSB_SILENT is not set
# CONFIG_SSB_DEBUG is not set
CONFIG_SSB_DRIVER_PCICORE_POSSIBLE=y
CONFIG_SSB_DRIVER_PCICORE=y
CONFIG_SSB_DRIVER_GPIO=y
CONFIG_BCMA_POSSIBLE=y

#
# Broadcom specific AMBA
#
CONFIG_BCMA=m
CONFIG_BCMA_BLOCKIO=y
CONFIG_BCMA_HOST_PCI_POSSIBLE=y
CONFIG_BCMA_HOST_PCI=y
CONFIG_BCMA_HOST_SOC=y
CONFIG_BCMA_DRIVER_PCI=y
CONFIG_BCMA_DRIVER_GMAC_CMN=y
CONFIG_BCMA_DRIVER_GPIO=y
# CONFIG_BCMA_DEBUG is not set

#
# Multifunction device drivers
#
CONFIG_MFD_CORE=y
CONFIG_MFD_AS3711=y
CONFIG_PMIC_ADP5520=y
CONFIG_MFD_AAT2870_CORE=y
CONFIG_MFD_BCM590XX=m
CONFIG_MFD_AXP20X=y
CONFIG_MFD_CROS_EC=m
CONFIG_MFD_CROS_EC_I2C=m
CONFIG_MFD_CROS_EC_SPI=m
CONFIG_PMIC_DA903X=y
CONFIG_PMIC_DA9052=y
CONFIG_MFD_DA9052_SPI=y
CONFIG_MFD_DA9052_I2C=y
CONFIG_MFD_DA9055=y
CONFIG_MFD_DA9062=m
CONFIG_MFD_DA9063=y
CONFIG_MFD_DA9150=m
CONFIG_MFD_DLN2=m
CONFIG_MFD_MC13XXX=m
CONFIG_MFD_MC13XXX_SPI=m
CONFIG_MFD_MC13XXX_I2C=m
CONFIG_HTC_PASIC3=m
CONFIG_HTC_I2CPLD=y
CONFIG_MFD_INTEL_QUARK_I2C_GPIO=m
CONFIG_LPC_ICH=m
CONFIG_LPC_SCH=m
CONFIG_INTEL_SOC_PMIC=y
CONFIG_MFD_INTEL_LPSS=m
CONFIG_MFD_INTEL_LPSS_ACPI=m
CONFIG_MFD_INTEL_LPSS_PCI=m
CONFIG_MFD_JANZ_CMODIO=m
CONFIG_MFD_KEMPLD=m
CONFIG_MFD_88PM800=m
CONFIG_MFD_88PM805=m
CONFIG_MFD_88PM860X=y
CONFIG_MFD_MAX14577=y
CONFIG_MFD_MAX77693=y
CONFIG_MFD_MAX77843=y
CONFIG_MFD_MAX8907=m
CONFIG_MFD_MAX8925=y
CONFIG_MFD_MAX8997=y
CONFIG_MFD_MAX8998=y
CONFIG_MFD_MT6397=m
CONFIG_MFD_MENF21BMC=m
CONFIG_EZX_PCAP=y
CONFIG_MFD_VIPERBOARD=m
CONFIG_MFD_RETU=m
CONFIG_MFD_PCF50633=m
CONFIG_PCF50633_ADC=m
CONFIG_PCF50633_GPIO=m
CONFIG_UCB1400_CORE=m
CONFIG_MFD_RDC321X=m
CONFIG_MFD_RTSX_PCI=m
CONFIG_MFD_RT5033=m
CONFIG_MFD_RTSX_USB=m
CONFIG_MFD_RC5T583=y
CONFIG_MFD_RN5T618=m
CONFIG_MFD_SEC_CORE=y
CONFIG_MFD_SI476X_CORE=m
CONFIG_MFD_SM501=m
CONFIG_MFD_SM501_GPIO=y
CONFIG_MFD_SKY81452=m
CONFIG_MFD_SMSC=y
CONFIG_ABX500_CORE=y
CONFIG_AB3100_CORE=y
CONFIG_AB3100_OTP=m
CONFIG_MFD_SYSCON=y
CONFIG_MFD_TI_AM335X_TSCADC=m
CONFIG_MFD_LP3943=m
CONFIG_MFD_LP8788=y
CONFIG_MFD_PALMAS=y
CONFIG_TPS6105X=m
CONFIG_TPS65010=m
CONFIG_TPS6507X=m
CONFIG_MFD_TPS65090=y
CONFIG_MFD_TPS65217=m
CONFIG_MFD_TPS65218=m
CONFIG_MFD_TPS6586X=y
CONFIG_MFD_TPS65910=y
CONFIG_MFD_TPS65912=y
CONFIG_MFD_TPS65912_I2C=y
CONFIG_MFD_TPS65912_SPI=y
CONFIG_MFD_TPS80031=y
CONFIG_TWL4030_CORE=y
CONFIG_MFD_TWL4030_AUDIO=y
CONFIG_TWL6040_CORE=y
CONFIG_MFD_WL1273_CORE=m
CONFIG_MFD_LM3533=m
# CONFIG_MFD_TMIO is not set
CONFIG_MFD_VX855=m
CONFIG_MFD_ARIZONA=y
CONFIG_MFD_ARIZONA_I2C=m
CONFIG_MFD_ARIZONA_SPI=m
CONFIG_MFD_WM5102=y
CONFIG_MFD_WM5110=y
CONFIG_MFD_WM8997=y
CONFIG_MFD_WM8998=y
CONFIG_MFD_WM8400=y
CONFIG_MFD_WM831X=y
CONFIG_MFD_WM831X_I2C=y
CONFIG_MFD_WM831X_SPI=y
CONFIG_MFD_WM8350=y
CONFIG_MFD_WM8350_I2C=y
CONFIG_MFD_WM8994=m
CONFIG_REGULATOR=y
# CONFIG_REGULATOR_DEBUG is not set
CONFIG_REGULATOR_FIXED_VOLTAGE=m
CONFIG_REGULATOR_VIRTUAL_CONSUMER=m
CONFIG_REGULATOR_USERSPACE_CONSUMER=m
CONFIG_REGULATOR_88PM800=m
CONFIG_REGULATOR_88PM8607=m
CONFIG_REGULATOR_ACT8865=m
CONFIG_REGULATOR_AD5398=m
CONFIG_REGULATOR_ANATOP=m
CONFIG_REGULATOR_AAT2870=m
CONFIG_REGULATOR_AB3100=m
CONFIG_REGULATOR_ARIZONA=m
CONFIG_REGULATOR_AS3711=m
CONFIG_REGULATOR_AXP20X=m
CONFIG_REGULATOR_BCM590XX=m
CONFIG_REGULATOR_DA903X=m
CONFIG_REGULATOR_DA9052=m
CONFIG_REGULATOR_DA9055=m
CONFIG_REGULATOR_DA9062=m
CONFIG_REGULATOR_DA9063=m
CONFIG_REGULATOR_DA9210=m
CONFIG_REGULATOR_DA9211=m
CONFIG_REGULATOR_FAN53555=m
CONFIG_REGULATOR_GPIO=m
CONFIG_REGULATOR_ISL9305=m
CONFIG_REGULATOR_ISL6271A=m
CONFIG_REGULATOR_LP3971=m
CONFIG_REGULATOR_LP3972=m
CONFIG_REGULATOR_LP872X=m
CONFIG_REGULATOR_LP8755=m
CONFIG_REGULATOR_LP8788=m
CONFIG_REGULATOR_LTC3589=m
CONFIG_REGULATOR_MAX14577=m
CONFIG_REGULATOR_MAX1586=m
CONFIG_REGULATOR_MAX8649=m
CONFIG_REGULATOR_MAX8660=m
CONFIG_REGULATOR_MAX8907=m
CONFIG_REGULATOR_MAX8925=m
CONFIG_REGULATOR_MAX8952=m
CONFIG_REGULATOR_MAX8973=m
CONFIG_REGULATOR_MAX8997=m
CONFIG_REGULATOR_MAX8998=m
CONFIG_REGULATOR_MAX77693=m
CONFIG_REGULATOR_MC13XXX_CORE=m
CONFIG_REGULATOR_MC13783=m
CONFIG_REGULATOR_MC13892=m
CONFIG_REGULATOR_MT6311=m
CONFIG_REGULATOR_MT6397=m
CONFIG_REGULATOR_PALMAS=m
CONFIG_REGULATOR_PCAP=m
CONFIG_REGULATOR_PCF50633=m
CONFIG_REGULATOR_PFUZE100=m
CONFIG_REGULATOR_PWM=m
CONFIG_REGULATOR_QCOM_SPMI=m
CONFIG_REGULATOR_RC5T583=m
CONFIG_REGULATOR_RN5T618=m
CONFIG_REGULATOR_RT5033=m
CONFIG_REGULATOR_S2MPA01=m
CONFIG_REGULATOR_S2MPS11=m
CONFIG_REGULATOR_S5M8767=m
CONFIG_REGULATOR_SKY81452=m
CONFIG_REGULATOR_TPS51632=m
CONFIG_REGULATOR_TPS6105X=m
CONFIG_REGULATOR_TPS62360=m
CONFIG_REGULATOR_TPS65023=m
CONFIG_REGULATOR_TPS6507X=m
CONFIG_REGULATOR_TPS65090=m
CONFIG_REGULATOR_TPS65217=m
CONFIG_REGULATOR_TPS6524X=m
CONFIG_REGULATOR_TPS6586X=m
CONFIG_REGULATOR_TPS65910=m
CONFIG_REGULATOR_TPS65912=m
CONFIG_REGULATOR_TPS80031=m
CONFIG_REGULATOR_TWL4030=m
CONFIG_REGULATOR_WM831X=m
CONFIG_REGULATOR_WM8350=m
CONFIG_REGULATOR_WM8400=m
CONFIG_REGULATOR_WM8994=m
CONFIG_MEDIA_SUPPORT=m

#
# Multimedia core support
#
CONFIG_MEDIA_CAMERA_SUPPORT=y
CONFIG_MEDIA_ANALOG_TV_SUPPORT=y
CONFIG_MEDIA_DIGITAL_TV_SUPPORT=y
CONFIG_MEDIA_RADIO_SUPPORT=y
CONFIG_MEDIA_SDR_SUPPORT=y
CONFIG_MEDIA_RC_SUPPORT=y
CONFIG_MEDIA_CONTROLLER=y
CONFIG_VIDEO_DEV=m
CONFIG_VIDEO_V4L2_SUBDEV_API=y
CONFIG_VIDEO_V4L2=m
# CONFIG_VIDEO_ADV_DEBUG is not set
# CONFIG_VIDEO_FIXED_MINOR_RANGES is not set
CONFIG_VIDEO_TUNER=m
CONFIG_V4L2_MEM2MEM_DEV=m
CONFIG_V4L2_FLASH_LED_CLASS=m
CONFIG_VIDEOBUF_GEN=m
CONFIG_VIDEOBUF_DMA_SG=m
CONFIG_VIDEOBUF_VMALLOC=m
CONFIG_VIDEOBUF_DVB=m
CONFIG_VIDEOBUF2_CORE=m
CONFIG_VIDEOBUF2_MEMOPS=m
CONFIG_VIDEOBUF2_DMA_CONTIG=m
CONFIG_VIDEOBUF2_VMALLOC=m
CONFIG_VIDEOBUF2_DMA_SG=m
CONFIG_VIDEOBUF2_DVB=m
CONFIG_DVB_CORE=m
CONFIG_DVB_NET=y
CONFIG_TTPCI_EEPROM=m
CONFIG_DVB_MAX_ADAPTERS=8
CONFIG_DVB_DYNAMIC_MINORS=y

#
# Media drivers
#
CONFIG_RC_CORE=m
CONFIG_RC_MAP=m
CONFIG_RC_DECODERS=y
CONFIG_LIRC=m
CONFIG_IR_LIRC_CODEC=m
CONFIG_IR_NEC_DECODER=m
CONFIG_IR_RC5_DECODER=m
CONFIG_IR_RC6_DECODER=m
CONFIG_IR_JVC_DECODER=m
CONFIG_IR_SONY_DECODER=m
CONFIG_IR_SANYO_DECODER=m
CONFIG_IR_SHARP_DECODER=m
CONFIG_IR_MCE_KBD_DECODER=m
CONFIG_IR_XMP_DECODER=m
CONFIG_RC_DEVICES=y
CONFIG_RC_ATI_REMOTE=m
CONFIG_IR_ENE=m
CONFIG_IR_HIX5HD2=m
CONFIG_IR_IMON=m
CONFIG_IR_MCEUSB=m
CONFIG_IR_ITE_CIR=m
CONFIG_IR_FINTEK=m
CONFIG_IR_NUVOTON=m
CONFIG_IR_REDRAT3=m
CONFIG_IR_STREAMZAP=m
CONFIG_IR_WINBOND_CIR=m
CONFIG_IR_IGORPLUGUSB=m
CONFIG_IR_IGUANA=m
CONFIG_IR_TTUSBIR=m
CONFIG_RC_LOOPBACK=m
CONFIG_IR_GPIO_CIR=m
CONFIG_MEDIA_USB_SUPPORT=y

#
# Webcam devices
#
CONFIG_USB_VIDEO_CLASS=m
CONFIG_USB_VIDEO_CLASS_INPUT_EVDEV=y
CONFIG_USB_GSPCA=m
CONFIG_USB_M5602=m
CONFIG_USB_STV06XX=m
CONFIG_USB_GL860=m
CONFIG_USB_GSPCA_BENQ=m
CONFIG_USB_GSPCA_CONEX=m
CONFIG_USB_GSPCA_CPIA1=m
CONFIG_USB_GSPCA_DTCS033=m
CONFIG_USB_GSPCA_ETOMS=m
CONFIG_USB_GSPCA_FINEPIX=m
CONFIG_USB_GSPCA_JEILINJ=m
CONFIG_USB_GSPCA_JL2005BCD=m
CONFIG_USB_GSPCA_KINECT=m
CONFIG_USB_GSPCA_KONICA=m
CONFIG_USB_GSPCA_MARS=m
CONFIG_USB_GSPCA_MR97310A=m
CONFIG_USB_GSPCA_NW80X=m
CONFIG_USB_GSPCA_OV519=m
CONFIG_USB_GSPCA_OV534=m
CONFIG_USB_GSPCA_OV534_9=m
CONFIG_USB_GSPCA_PAC207=m
CONFIG_USB_GSPCA_PAC7302=m
CONFIG_USB_GSPCA_PAC7311=m
CONFIG_USB_GSPCA_SE401=m
CONFIG_USB_GSPCA_SN9C2028=m
CONFIG_USB_GSPCA_SN9C20X=m
CONFIG_USB_GSPCA_SONIXB=m
CONFIG_USB_GSPCA_SONIXJ=m
CONFIG_USB_GSPCA_SPCA500=m
CONFIG_USB_GSPCA_SPCA501=m
CONFIG_USB_GSPCA_SPCA505=m
CONFIG_USB_GSPCA_SPCA506=m
CONFIG_USB_GSPCA_SPCA508=m
CONFIG_USB_GSPCA_SPCA561=m
CONFIG_USB_GSPCA_SPCA1528=m
CONFIG_USB_GSPCA_SQ905=m
CONFIG_USB_GSPCA_SQ905C=m
CONFIG_USB_GSPCA_SQ930X=m
CONFIG_USB_GSPCA_STK014=m
CONFIG_USB_GSPCA_STK1135=m
CONFIG_USB_GSPCA_STV0680=m
CONFIG_USB_GSPCA_SUNPLUS=m
CONFIG_USB_GSPCA_T613=m
CONFIG_USB_GSPCA_TOPRO=m
CONFIG_USB_GSPCA_TOUPTEK=m
CONFIG_USB_GSPCA_TV8532=m
CONFIG_USB_GSPCA_VC032X=m
CONFIG_USB_GSPCA_VICAM=m
CONFIG_USB_GSPCA_XIRLINK_CIT=m
CONFIG_USB_GSPCA_ZC3XX=m
CONFIG_USB_PWC=m
# CONFIG_USB_PWC_DEBUG is not set
CONFIG_USB_PWC_INPUT_EVDEV=y
CONFIG_VIDEO_CPIA2=m
CONFIG_USB_ZR364XX=m
CONFIG_USB_STKWEBCAM=m
CONFIG_USB_S2255=m
CONFIG_VIDEO_USBTV=m

#
# Analog TV USB devices
#
CONFIG_VIDEO_PVRUSB2=m
CONFIG_VIDEO_PVRUSB2_SYSFS=y
CONFIG_VIDEO_PVRUSB2_DVB=y
# CONFIG_VIDEO_PVRUSB2_DEBUGIFC is not set
CONFIG_VIDEO_HDPVR=m
CONFIG_VIDEO_USBVISION=m
CONFIG_VIDEO_STK1160_COMMON=m
CONFIG_VIDEO_STK1160_AC97=y
CONFIG_VIDEO_STK1160=m
CONFIG_VIDEO_GO7007=m
CONFIG_VIDEO_GO7007_USB=m
CONFIG_VIDEO_GO7007_LOADER=m
CONFIG_VIDEO_GO7007_USB_S2250_BOARD=m

#
# Analog/digital TV USB devices
#
CONFIG_VIDEO_AU0828=m
CONFIG_VIDEO_AU0828_V4L2=y
CONFIG_VIDEO_AU0828_RC=y
CONFIG_VIDEO_CX231XX=m
CONFIG_VIDEO_CX231XX_RC=y
CONFIG_VIDEO_CX231XX_ALSA=m
CONFIG_VIDEO_CX231XX_DVB=m
CONFIG_VIDEO_TM6000=m
CONFIG_VIDEO_TM6000_ALSA=m
CONFIG_VIDEO_TM6000_DVB=m

#
# Digital TV USB devices
#
CONFIG_DVB_USB=m
# CONFIG_DVB_USB_DEBUG is not set
CONFIG_DVB_USB_A800=m
CONFIG_DVB_USB_DIBUSB_MB=m
# CONFIG_DVB_USB_DIBUSB_MB_FAULTY is not set
CONFIG_DVB_USB_DIBUSB_MC=m
CONFIG_DVB_USB_DIB0700=m
CONFIG_DVB_USB_UMT_010=m
CONFIG_DVB_USB_CXUSB=m
CONFIG_DVB_USB_M920X=m
CONFIG_DVB_USB_DIGITV=m
CONFIG_DVB_USB_VP7045=m
CONFIG_DVB_USB_VP702X=m
CONFIG_DVB_USB_GP8PSK=m
CONFIG_DVB_USB_NOVA_T_USB2=m
CONFIG_DVB_USB_TTUSB2=m
CONFIG_DVB_USB_DTT200U=m
CONFIG_DVB_USB_OPERA1=m
CONFIG_DVB_USB_AF9005=m
CONFIG_DVB_USB_AF9005_REMOTE=m
CONFIG_DVB_USB_PCTV452E=m
CONFIG_DVB_USB_DW2102=m
CONFIG_DVB_USB_CINERGY_T2=m
CONFIG_DVB_USB_DTV5100=m
CONFIG_DVB_USB_FRIIO=m
CONFIG_DVB_USB_AZ6027=m
CONFIG_DVB_USB_TECHNISAT_USB2=m
CONFIG_DVB_USB_V2=m
CONFIG_DVB_USB_AF9015=m
CONFIG_DVB_USB_AF9035=m
CONFIG_DVB_USB_ANYSEE=m
CONFIG_DVB_USB_AU6610=m
CONFIG_DVB_USB_AZ6007=m
CONFIG_DVB_USB_CE6230=m
CONFIG_DVB_USB_EC168=m
CONFIG_DVB_USB_GL861=m
CONFIG_DVB_USB_LME2510=m
CONFIG_DVB_USB_MXL111SF=m
CONFIG_DVB_USB_RTL28XXU=m
CONFIG_DVB_USB_DVBSKY=m
CONFIG_DVB_TTUSB_BUDGET=m
CONFIG_DVB_TTUSB_DEC=m
CONFIG_SMS_USB_DRV=m
CONFIG_DVB_B2C2_FLEXCOP_USB=m
# CONFIG_DVB_B2C2_FLEXCOP_USB_DEBUG is not set
CONFIG_DVB_AS102=m

#
# Webcam, TV (analog/digital) USB devices
#
CONFIG_VIDEO_EM28XX=m
CONFIG_VIDEO_EM28XX_V4L2=m
CONFIG_VIDEO_EM28XX_ALSA=m
CONFIG_VIDEO_EM28XX_DVB=m
CONFIG_VIDEO_EM28XX_RC=m

#
# Software defined radio USB devices
#
CONFIG_USB_AIRSPY=m
CONFIG_USB_HACKRF=m
CONFIG_USB_MSI2500=m
CONFIG_MEDIA_PCI_SUPPORT=y

#
# Media capture support
#
CONFIG_VIDEO_MEYE=m
CONFIG_VIDEO_SOLO6X10=m
CONFIG_VIDEO_TW68=m
CONFIG_VIDEO_ZORAN=m
CONFIG_VIDEO_ZORAN_DC30=m
CONFIG_VIDEO_ZORAN_ZR36060=m
CONFIG_VIDEO_ZORAN_BUZ=m
CONFIG_VIDEO_ZORAN_DC10=m
CONFIG_VIDEO_ZORAN_LML33=m
CONFIG_VIDEO_ZORAN_LML33R10=m
CONFIG_VIDEO_ZORAN_AVS6EYES=m

#
# Media capture/analog TV support
#
CONFIG_VIDEO_IVTV=m
CONFIG_VIDEO_IVTV_ALSA=m
CONFIG_VIDEO_FB_IVTV=m
CONFIG_VIDEO_HEXIUM_GEMINI=m
CONFIG_VIDEO_HEXIUM_ORION=m
CONFIG_VIDEO_MXB=m
CONFIG_VIDEO_DT3155=m

#
# Media capture/analog/hybrid TV support
#
CONFIG_VIDEO_CX18=m
CONFIG_VIDEO_CX18_ALSA=m
CONFIG_VIDEO_CX23885=m
CONFIG_MEDIA_ALTERA_CI=m
CONFIG_VIDEO_CX25821=m
CONFIG_VIDEO_CX25821_ALSA=m
CONFIG_VIDEO_CX88=m
CONFIG_VIDEO_CX88_ALSA=m
CONFIG_VIDEO_CX88_BLACKBIRD=m
CONFIG_VIDEO_CX88_DVB=m
CONFIG_VIDEO_CX88_ENABLE_VP3054=y
CONFIG_VIDEO_CX88_VP3054=m
CONFIG_VIDEO_CX88_MPEG=m
CONFIG_VIDEO_BT848=m
CONFIG_DVB_BT8XX=m
CONFIG_VIDEO_SAA7134=m
CONFIG_VIDEO_SAA7134_ALSA=m
CONFIG_VIDEO_SAA7134_RC=y
CONFIG_VIDEO_SAA7134_DVB=m
CONFIG_VIDEO_SAA7134_GO7007=m
CONFIG_VIDEO_SAA7164=m
CONFIG_VIDEO_COBALT=m

#
# Media digital TV PCI Adapters
#
CONFIG_DVB_AV7110_IR=y
CONFIG_DVB_AV7110=m
CONFIG_DVB_AV7110_OSD=y
CONFIG_DVB_BUDGET_CORE=m
CONFIG_DVB_BUDGET=m
CONFIG_DVB_BUDGET_CI=m
CONFIG_DVB_BUDGET_AV=m
CONFIG_DVB_BUDGET_PATCH=m
CONFIG_DVB_B2C2_FLEXCOP_PCI=m
# CONFIG_DVB_B2C2_FLEXCOP_PCI_DEBUG is not set
CONFIG_DVB_PLUTO2=m
CONFIG_DVB_DM1105=m
CONFIG_DVB_PT1=m
CONFIG_DVB_PT3=m
CONFIG_MANTIS_CORE=m
CONFIG_DVB_MANTIS=m
CONFIG_DVB_HOPPER=m
CONFIG_DVB_NGENE=m
CONFIG_DVB_DDBRIDGE=m
CONFIG_DVB_SMIPCIE=m
CONFIG_DVB_NETUP_UNIDVB=m
CONFIG_V4L_PLATFORM_DRIVERS=y
CONFIG_VIDEO_CAFE_CCIC=m
CONFIG_VIDEO_VIA_CAMERA=m
CONFIG_SOC_CAMERA=m
CONFIG_SOC_CAMERA_PLATFORM=m
CONFIG_V4L_MEM2MEM_DRIVERS=y
CONFIG_VIDEO_MEM2MEM_DEINTERLACE=m
CONFIG_VIDEO_SH_VEU=m
CONFIG_V4L_TEST_DRIVERS=y
CONFIG_VIDEO_VIVID=m
CONFIG_VIDEO_VIVID_MAX_DEVS=64
CONFIG_VIDEO_VIM2M=m
CONFIG_DVB_PLATFORM_DRIVERS=y

#
# Supported MMC/SDIO adapters
#
CONFIG_SMS_SDIO_DRV=m
CONFIG_RADIO_ADAPTERS=y
CONFIG_RADIO_TEA575X=m
CONFIG_RADIO_SI470X=y
CONFIG_USB_SI470X=m
CONFIG_I2C_SI470X=m
CONFIG_RADIO_SI4713=m
CONFIG_USB_SI4713=m
CONFIG_PLATFORM_SI4713=m
CONFIG_I2C_SI4713=m
CONFIG_RADIO_SI476X=m
CONFIG_USB_MR800=m
CONFIG_USB_DSBR=m
CONFIG_RADIO_MAXIRADIO=m
CONFIG_RADIO_SHARK=m
CONFIG_RADIO_SHARK2=m
CONFIG_USB_KEENE=m
CONFIG_USB_RAREMONO=m
CONFIG_USB_MA901=m
CONFIG_RADIO_TEA5764=m
CONFIG_RADIO_SAA7706H=m
CONFIG_RADIO_TEF6862=m
CONFIG_RADIO_WL1273=m

#
# Texas Instruments WL128x FM driver (ST based)
#
CONFIG_RADIO_WL128X=m

#
# Supported FireWire (IEEE 1394) Adapters
#
CONFIG_DVB_FIREDTV=m
CONFIG_DVB_FIREDTV_INPUT=y
CONFIG_MEDIA_COMMON_OPTIONS=y

#
# common driver options
#
CONFIG_VIDEO_CX2341X=m
CONFIG_VIDEO_TVEEPROM=m
CONFIG_CYPRESS_FIRMWARE=m
CONFIG_DVB_B2C2_FLEXCOP=m
CONFIG_VIDEO_SAA7146=m
CONFIG_VIDEO_SAA7146_VV=m
CONFIG_SMS_SIANO_MDTV=m
CONFIG_SMS_SIANO_RC=y
CONFIG_SMS_SIANO_DEBUGFS=y

#
# Media ancillary drivers (tuners, sensors, i2c, frontends)
#
CONFIG_MEDIA_SUBDRV_AUTOSELECT=y
CONFIG_MEDIA_ATTACH=y
CONFIG_VIDEO_IR_I2C=m

#
# Audio decoders, processors and mixers
#
CONFIG_VIDEO_TVAUDIO=m
CONFIG_VIDEO_TDA7432=m
CONFIG_VIDEO_TDA9840=m
CONFIG_VIDEO_TEA6415C=m
CONFIG_VIDEO_TEA6420=m
CONFIG_VIDEO_MSP3400=m
CONFIG_VIDEO_CS5345=m
CONFIG_VIDEO_CS53L32A=m
CONFIG_VIDEO_UDA1342=m
CONFIG_VIDEO_WM8775=m
CONFIG_VIDEO_WM8739=m
CONFIG_VIDEO_VP27SMPX=m
CONFIG_VIDEO_SONY_BTF_MPX=m

#
# RDS decoders
#
CONFIG_VIDEO_SAA6588=m

#
# Video decoders
#
CONFIG_VIDEO_ADV7604=m
CONFIG_VIDEO_ADV7842=m
CONFIG_VIDEO_BT819=m
CONFIG_VIDEO_BT856=m
CONFIG_VIDEO_BT866=m
CONFIG_VIDEO_KS0127=m
CONFIG_VIDEO_SAA7110=m
CONFIG_VIDEO_SAA711X=m
CONFIG_VIDEO_TVP5150=m
CONFIG_VIDEO_TW2804=m
CONFIG_VIDEO_TW9903=m
CONFIG_VIDEO_TW9906=m
CONFIG_VIDEO_VPX3220=m

#
# Video and audio decoders
#
CONFIG_VIDEO_SAA717X=m
CONFIG_VIDEO_CX25840=m

#
# Video encoders
#
CONFIG_VIDEO_SAA7127=m
CONFIG_VIDEO_SAA7185=m
CONFIG_VIDEO_ADV7170=m
CONFIG_VIDEO_ADV7175=m
CONFIG_VIDEO_ADV7511=m

#
# Camera sensor devices
#
CONFIG_VIDEO_OV7640=m
CONFIG_VIDEO_OV7670=m
CONFIG_VIDEO_MT9V011=m

#
# Flash devices
#

#
# Video improvement chips
#
CONFIG_VIDEO_UPD64031A=m
CONFIG_VIDEO_UPD64083=m

#
# Audio/Video compression chips
#
CONFIG_VIDEO_SAA6752HS=m

#
# Miscellaneous helper chips
#
CONFIG_VIDEO_M52790=m

#
# Sensors used on soc_camera driver
#

#
# soc_camera sensor drivers
#
CONFIG_SOC_CAMERA_IMX074=m
CONFIG_SOC_CAMERA_MT9M001=m
CONFIG_SOC_CAMERA_MT9M111=m
CONFIG_SOC_CAMERA_MT9T031=m
CONFIG_SOC_CAMERA_MT9T112=m
CONFIG_SOC_CAMERA_MT9V022=m
CONFIG_SOC_CAMERA_OV2640=m
CONFIG_SOC_CAMERA_OV5642=m
CONFIG_SOC_CAMERA_OV6650=m
CONFIG_SOC_CAMERA_OV772X=m
CONFIG_SOC_CAMERA_OV9640=m
CONFIG_SOC_CAMERA_OV9740=m
CONFIG_SOC_CAMERA_RJ54N1=m
CONFIG_SOC_CAMERA_TW9910=m
CONFIG_MEDIA_TUNER=m
CONFIG_MEDIA_TUNER_SIMPLE=m
CONFIG_MEDIA_TUNER_TDA8290=m
CONFIG_MEDIA_TUNER_TDA827X=m
CONFIG_MEDIA_TUNER_TDA18271=m
CONFIG_MEDIA_TUNER_TDA9887=m
CONFIG_MEDIA_TUNER_TEA5761=m
CONFIG_MEDIA_TUNER_TEA5767=m
CONFIG_MEDIA_TUNER_MSI001=m
CONFIG_MEDIA_TUNER_MT20XX=m
CONFIG_MEDIA_TUNER_MT2060=m
CONFIG_MEDIA_TUNER_MT2063=m
CONFIG_MEDIA_TUNER_MT2266=m
CONFIG_MEDIA_TUNER_MT2131=m
CONFIG_MEDIA_TUNER_QT1010=m
CONFIG_MEDIA_TUNER_XC2028=m
CONFIG_MEDIA_TUNER_XC5000=m
CONFIG_MEDIA_TUNER_XC4000=m
CONFIG_MEDIA_TUNER_MXL5005S=m
CONFIG_MEDIA_TUNER_MXL5007T=m
CONFIG_MEDIA_TUNER_MC44S803=m
CONFIG_MEDIA_TUNER_MAX2165=m
CONFIG_MEDIA_TUNER_TDA18218=m
CONFIG_MEDIA_TUNER_FC0011=m
CONFIG_MEDIA_TUNER_FC0012=m
CONFIG_MEDIA_TUNER_FC0013=m
CONFIG_MEDIA_TUNER_TDA18212=m
CONFIG_MEDIA_TUNER_E4000=m
CONFIG_MEDIA_TUNER_FC2580=m
CONFIG_MEDIA_TUNER_M88RS6000T=m
CONFIG_MEDIA_TUNER_TUA9001=m
CONFIG_MEDIA_TUNER_SI2157=m
CONFIG_MEDIA_TUNER_IT913X=m
CONFIG_MEDIA_TUNER_R820T=m
CONFIG_MEDIA_TUNER_MXL301RF=m
CONFIG_MEDIA_TUNER_QM1D1C0042=m

#
# Multistandard (satellite) frontends
#
CONFIG_DVB_STB0899=m
CONFIG_DVB_STB6100=m
CONFIG_DVB_STV090x=m
CONFIG_DVB_STV6110x=m
CONFIG_DVB_M88DS3103=m

#
# Multistandard (cable + terrestrial) frontends
#
CONFIG_DVB_DRXK=m
CONFIG_DVB_TDA18271C2DD=m
CONFIG_DVB_SI2165=m

#
# DVB-S (satellite) frontends
#
CONFIG_DVB_CX24110=m
CONFIG_DVB_CX24123=m
CONFIG_DVB_MT312=m
CONFIG_DVB_ZL10036=m
CONFIG_DVB_ZL10039=m
CONFIG_DVB_S5H1420=m
CONFIG_DVB_STV0288=m
CONFIG_DVB_STB6000=m
CONFIG_DVB_STV0299=m
CONFIG_DVB_STV6110=m
CONFIG_DVB_STV0900=m
CONFIG_DVB_TDA8083=m
CONFIG_DVB_TDA10086=m
CONFIG_DVB_TDA8261=m
CONFIG_DVB_VES1X93=m
CONFIG_DVB_TUNER_ITD1000=m
CONFIG_DVB_TUNER_CX24113=m
CONFIG_DVB_TDA826X=m
CONFIG_DVB_TUA6100=m
CONFIG_DVB_CX24116=m
CONFIG_DVB_CX24117=m
CONFIG_DVB_CX24120=m
CONFIG_DVB_SI21XX=m
CONFIG_DVB_TS2020=m
CONFIG_DVB_DS3000=m
CONFIG_DVB_MB86A16=m
CONFIG_DVB_TDA10071=m

#
# DVB-T (terrestrial) frontends
#
CONFIG_DVB_SP8870=m
CONFIG_DVB_SP887X=m
CONFIG_DVB_CX22700=m
CONFIG_DVB_CX22702=m
CONFIG_DVB_DRXD=m
CONFIG_DVB_L64781=m
CONFIG_DVB_TDA1004X=m
CONFIG_DVB_NXT6000=m
CONFIG_DVB_MT352=m
CONFIG_DVB_ZL10353=m
CONFIG_DVB_DIB3000MB=m
CONFIG_DVB_DIB3000MC=m
CONFIG_DVB_DIB7000M=m
CONFIG_DVB_DIB7000P=m
CONFIG_DVB_TDA10048=m
CONFIG_DVB_AF9013=m
CONFIG_DVB_EC100=m
CONFIG_DVB_STV0367=m
CONFIG_DVB_CXD2820R=m
CONFIG_DVB_CXD2841ER=m
CONFIG_DVB_RTL2830=m
CONFIG_DVB_RTL2832=m
CONFIG_DVB_RTL2832_SDR=m
CONFIG_DVB_SI2168=m
CONFIG_DVB_AS102_FE=m

#
# DVB-C (cable) frontends
#
CONFIG_DVB_VES1820=m
CONFIG_DVB_TDA10021=m
CONFIG_DVB_TDA10023=m
CONFIG_DVB_STV0297=m

#
# ATSC (North American/Korean Terrestrial/Cable DTV) frontends
#
CONFIG_DVB_NXT200X=m
CONFIG_DVB_OR51211=m
CONFIG_DVB_OR51132=m
CONFIG_DVB_BCM3510=m
CONFIG_DVB_LGDT330X=m
CONFIG_DVB_LGDT3305=m
CONFIG_DVB_LGDT3306A=m
CONFIG_DVB_LG2160=m
CONFIG_DVB_S5H1409=m
CONFIG_DVB_AU8522=m
CONFIG_DVB_AU8522_DTV=m
CONFIG_DVB_AU8522_V4L=m
CONFIG_DVB_S5H1411=m

#
# ISDB-T (terrestrial) frontends
#
CONFIG_DVB_S921=m
CONFIG_DVB_DIB8000=m
CONFIG_DVB_MB86A20S=m

#
# ISDB-S (satellite) & ISDB-T (terrestrial) frontends
#
CONFIG_DVB_TC90522=m

#
# Digital terrestrial only tuners/PLL
#
CONFIG_DVB_PLL=m
CONFIG_DVB_TUNER_DIB0070=m
CONFIG_DVB_TUNER_DIB0090=m

#
# SEC control devices for DVB-S
#
CONFIG_DVB_DRX39XYJ=m
CONFIG_DVB_LNBH25=m
CONFIG_DVB_LNBP21=m
CONFIG_DVB_LNBP22=m
CONFIG_DVB_ISL6405=m
CONFIG_DVB_ISL6421=m
CONFIG_DVB_ISL6423=m
CONFIG_DVB_A8293=m
CONFIG_DVB_SP2=m
CONFIG_DVB_LGS8GXX=m
CONFIG_DVB_ATBM8830=m
CONFIG_DVB_TDA665x=m
CONFIG_DVB_IX2505V=m
CONFIG_DVB_M88RS2000=m
CONFIG_DVB_AF9033=m
CONFIG_DVB_HORUS3A=m
CONFIG_DVB_ASCOT2E=m

#
# Tools to develop new frontends
#
# CONFIG_DVB_DUMMY_FE is not set

#
# Graphics support
#
CONFIG_AGP=y
CONFIG_AGP_AMD64=y
CONFIG_AGP_INTEL=y
CONFIG_AGP_SIS=m
CONFIG_AGP_VIA=y
CONFIG_INTEL_GTT=y
CONFIG_VGA_ARB=y
CONFIG_VGA_ARB_MAX_GPUS=16
CONFIG_VGA_SWITCHEROO=y
CONFIG_DRM=m
CONFIG_DRM_MIPI_DSI=y
CONFIG_DRM_KMS_HELPER=m
CONFIG_DRM_KMS_FB_HELPER=y
CONFIG_DRM_FBDEV_EMULATION=y
CONFIG_DRM_LOAD_EDID_FIRMWARE=y
CONFIG_DRM_TTM=m

#
# I2C encoder or helper chips
#
CONFIG_DRM_I2C_ADV7511=m
CONFIG_DRM_I2C_CH7006=m
CONFIG_DRM_I2C_SIL164=m
CONFIG_DRM_I2C_NXP_TDA998X=m
CONFIG_DRM_TDFX=m
CONFIG_DRM_R128=m
CONFIG_DRM_RADEON=m
# CONFIG_DRM_RADEON_USERPTR is not set
# CONFIG_DRM_RADEON_UMS is not set
CONFIG_DRM_AMDGPU=m
# CONFIG_DRM_AMDGPU_CIK is not set
CONFIG_DRM_AMDGPU_USERPTR=y
CONFIG_DRM_NOUVEAU=m
CONFIG_NOUVEAU_DEBUG=5
CONFIG_NOUVEAU_DEBUG_DEFAULT=3
CONFIG_DRM_NOUVEAU_BACKLIGHT=y
CONFIG_DRM_I915=m
# CONFIG_DRM_I915_PRELIMINARY_HW_SUPPORT is not set
CONFIG_DRM_MGA=m
CONFIG_DRM_SIS=m
CONFIG_DRM_VIA=m
CONFIG_DRM_SAVAGE=m
CONFIG_DRM_VGEM=m
CONFIG_DRM_VMWGFX=m
CONFIG_DRM_VMWGFX_FBCON=y
CONFIG_DRM_GMA500=m
CONFIG_DRM_GMA600=y
CONFIG_DRM_GMA3600=y
CONFIG_DRM_UDL=m
CONFIG_DRM_AST=m
# CONFIG_DRM_MGAG200 is not set
CONFIG_DRM_CIRRUS_QEMU=m
CONFIG_DRM_QXL=m
# CONFIG_DRM_BOCHS is not set
CONFIG_DRM_VIRTIO_GPU=m
CONFIG_DRM_PANEL=y

#
# Display Panels
#
CONFIG_DRM_BRIDGE=y

#
# Display Interface Bridges
#
CONFIG_HSA_AMD=m

#
# Frame buffer Devices
#
CONFIG_FB=y
CONFIG_FIRMWARE_EDID=y
CONFIG_FB_CMDLINE=y
CONFIG_FB_DDC=m
CONFIG_FB_BOOT_VESA_SUPPORT=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_CFB_REV_PIXELS_IN_BYTE is not set
CONFIG_FB_SYS_FILLRECT=m
CONFIG_FB_SYS_COPYAREA=m
CONFIG_FB_SYS_IMAGEBLIT=m
# CONFIG_FB_FOREIGN_ENDIAN is not set
CONFIG_FB_SYS_FOPS=m
CONFIG_FB_DEFERRED_IO=y
CONFIG_FB_HECUBA=m
CONFIG_FB_SVGALIB=m
# CONFIG_FB_MACMODES is not set
CONFIG_FB_BACKLIGHT=y
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y

#
# Frame buffer hardware drivers
#
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
CONFIG_FB_CYBER2000_DDC=y
CONFIG_FB_ARC=m
CONFIG_FB_ASILIANT=y
CONFIG_FB_IMSTT=y
CONFIG_FB_VGA16=m
CONFIG_FB_UVESA=m
CONFIG_FB_VESA=y
CONFIG_FB_EFI=y
CONFIG_FB_N411=m
CONFIG_FB_HGA=m
CONFIG_FB_OPENCORES=m
CONFIG_FB_S1D13XXX=m
CONFIG_FB_NVIDIA=m
CONFIG_FB_NVIDIA_I2C=y
# CONFIG_FB_NVIDIA_DEBUG is not set
CONFIG_FB_NVIDIA_BACKLIGHT=y
CONFIG_FB_RIVA=m
CONFIG_FB_RIVA_I2C=y
# CONFIG_FB_RIVA_DEBUG is not set
CONFIG_FB_RIVA_BACKLIGHT=y
CONFIG_FB_I740=m
CONFIG_FB_LE80578=m
CONFIG_FB_CARILLO_RANCH=m
CONFIG_FB_INTEL=m
# CONFIG_FB_INTEL_DEBUG is not set
CONFIG_FB_INTEL_I2C=y
CONFIG_FB_MATROX=m
CONFIG_FB_MATROX_MILLENIUM=y
CONFIG_FB_MATROX_MYSTIQUE=y
CONFIG_FB_MATROX_G=y
CONFIG_FB_MATROX_I2C=m
CONFIG_FB_MATROX_MAVEN=m
CONFIG_FB_RADEON=m
CONFIG_FB_RADEON_I2C=y
CONFIG_FB_RADEON_BACKLIGHT=y
# CONFIG_FB_RADEON_DEBUG is not set
CONFIG_FB_ATY128=m
CONFIG_FB_ATY128_BACKLIGHT=y
CONFIG_FB_ATY=m
CONFIG_FB_ATY_CT=y
# CONFIG_FB_ATY_GENERIC_LCD is not set
CONFIG_FB_ATY_GX=y
CONFIG_FB_ATY_BACKLIGHT=y
CONFIG_FB_S3=m
CONFIG_FB_S3_DDC=y
CONFIG_FB_SAVAGE=m
CONFIG_FB_SAVAGE_I2C=y
# CONFIG_FB_SAVAGE_ACCEL is not set
CONFIG_FB_SIS=m
CONFIG_FB_SIS_300=y
CONFIG_FB_SIS_315=y
CONFIG_FB_VIA=m
# CONFIG_FB_VIA_DIRECT_PROCFS is not set
CONFIG_FB_VIA_X_COMPATIBILITY=y
CONFIG_FB_NEOMAGIC=m
CONFIG_FB_KYRO=m
CONFIG_FB_3DFX=m
# CONFIG_FB_3DFX_ACCEL is not set
# CONFIG_FB_3DFX_I2C is not set
CONFIG_FB_VOODOO1=m
CONFIG_FB_VT8623=m
CONFIG_FB_TRIDENT=m
CONFIG_FB_ARK=m
CONFIG_FB_PM3=m
CONFIG_FB_CARMINE=m
CONFIG_FB_CARMINE_DRAM_EVAL=y
# CONFIG_CARMINE_DRAM_CUSTOM is not set
CONFIG_FB_SM501=m
CONFIG_FB_SMSCUFX=m
CONFIG_FB_UDL=m
CONFIG_FB_IBM_GXT4500=m
# CONFIG_FB_VIRTUAL is not set
CONFIG_XEN_FBDEV_FRONTEND=m
CONFIG_FB_METRONOME=m
CONFIG_FB_MB862XX=m
CONFIG_FB_MB862XX_PCI_GDC=y
CONFIG_FB_MB862XX_I2C=y
CONFIG_FB_BROADSHEET=m
CONFIG_FB_AUO_K190X=m
CONFIG_FB_AUO_K1900=m
CONFIG_FB_AUO_K1901=m
CONFIG_FB_HYPERV=m
CONFIG_FB_SIMPLE=y
CONFIG_FB_SM712=m
CONFIG_BACKLIGHT_LCD_SUPPORT=y
CONFIG_LCD_CLASS_DEVICE=m
CONFIG_LCD_L4F00242T03=m
CONFIG_LCD_LMS283GF05=m
CONFIG_LCD_LTV350QV=m
CONFIG_LCD_ILI922X=m
CONFIG_LCD_ILI9320=m
CONFIG_LCD_TDO24M=m
CONFIG_LCD_VGG2432A4=m
CONFIG_LCD_PLATFORM=m
CONFIG_LCD_S6E63M0=m
CONFIG_LCD_LD9040=m
CONFIG_LCD_AMS369FG06=m
CONFIG_LCD_LMS501KF03=m
CONFIG_LCD_HX8357=m
CONFIG_BACKLIGHT_CLASS_DEVICE=y
CONFIG_BACKLIGHT_GENERIC=m
CONFIG_BACKLIGHT_LM3533=m
CONFIG_BACKLIGHT_CARILLO_RANCH=m
CONFIG_BACKLIGHT_PWM=m
CONFIG_BACKLIGHT_DA903X=m
CONFIG_BACKLIGHT_DA9052=m
CONFIG_BACKLIGHT_MAX8925=m
CONFIG_BACKLIGHT_APPLE=m
CONFIG_BACKLIGHT_PM8941_WLED=m
CONFIG_BACKLIGHT_SAHARA=m
CONFIG_BACKLIGHT_WM831X=m
CONFIG_BACKLIGHT_ADP5520=m
CONFIG_BACKLIGHT_ADP8860=m
CONFIG_BACKLIGHT_ADP8870=m
CONFIG_BACKLIGHT_88PM860X=m
CONFIG_BACKLIGHT_PCF50633=m
CONFIG_BACKLIGHT_AAT2870=m
CONFIG_BACKLIGHT_LM3630A=m
CONFIG_BACKLIGHT_LM3639=m
CONFIG_BACKLIGHT_LP855X=m
CONFIG_BACKLIGHT_LP8788=m
CONFIG_BACKLIGHT_PANDORA=m
CONFIG_BACKLIGHT_SKY81452=m
CONFIG_BACKLIGHT_TPS65217=m
CONFIG_BACKLIGHT_AS3711=m
CONFIG_BACKLIGHT_GPIO=m
CONFIG_BACKLIGHT_LV5207LP=m
CONFIG_BACKLIGHT_BD6107=m
CONFIG_VGASTATE=m
CONFIG_HDMI=y

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
# CONFIG_VGACON_SOFT_SCROLLBACK is not set
CONFIG_DUMMY_CONSOLE=y
CONFIG_DUMMY_CONSOLE_COLUMNS=80
CONFIG_DUMMY_CONSOLE_ROWS=25
CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE_DETECT_PRIMARY=y
CONFIG_FRAMEBUFFER_CONSOLE_ROTATION=y
# CONFIG_LOGO is not set
CONFIG_SOUND=m
CONFIG_SOUND_OSS_CORE=y
# CONFIG_SOUND_OSS_CORE_PRECLAIM is not set
CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_DMAENGINE_PCM=m
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_COMPRESS_OFFLOAD=m
CONFIG_SND_JACK=y
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_PCM_OSS_PLUGINS=y
CONFIG_SND_PCM_TIMER=y
# CONFIG_SND_SEQUENCER_OSS is not set
CONFIG_SND_HRTIMER=m
CONFIG_SND_SEQ_HRTIMER_DEFAULT=y
CONFIG_SND_DYNAMIC_MINORS=y
CONFIG_SND_MAX_CARDS=32
CONFIG_SND_SUPPORT_OLD_API=y
CONFIG_SND_PROC_FS=y
CONFIG_SND_VERBOSE_PROCFS=y
# CONFIG_SND_VERBOSE_PRINTK is not set
# CONFIG_SND_DEBUG is not set
CONFIG_SND_VMASTER=y
CONFIG_SND_DMA_SGBUF=y
CONFIG_SND_RAWMIDI_SEQ=m
CONFIG_SND_OPL3_LIB_SEQ=m
# CONFIG_SND_OPL4_LIB_SEQ is not set
# CONFIG_SND_SBAWE_SEQ is not set
# CONFIG_SND_EMU10K1_SEQ is not set
CONFIG_SND_MPU401_UART=m
CONFIG_SND_OPL3_LIB=m
CONFIG_SND_VX_LIB=m
CONFIG_SND_AC97_CODEC=m
CONFIG_SND_DRIVERS=y
CONFIG_SND_PCSP=m
CONFIG_SND_DUMMY=m
CONFIG_SND_ALOOP=m
CONFIG_SND_VIRMIDI=m
CONFIG_SND_MTPAV=m
CONFIG_SND_MTS64=m
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_MPU401=m
CONFIG_SND_PORTMAN2X4=m
CONFIG_SND_AC97_POWER_SAVE=y
CONFIG_SND_AC97_POWER_SAVE_DEFAULT=0
CONFIG_SND_SB_COMMON=m
CONFIG_SND_PCI=y
CONFIG_SND_AD1889=m
CONFIG_SND_ALS4000=m
CONFIG_SND_ASIHPI=m
CONFIG_SND_ATIIXP=m
CONFIG_SND_ATIIXP_MODEM=m
CONFIG_SND_AU8810=m
CONFIG_SND_AU8820=m
CONFIG_SND_AU8830=m
CONFIG_SND_AW2=m
CONFIG_SND_BT87X=m
# CONFIG_SND_BT87X_OVERCLOCK is not set
CONFIG_SND_CA0106=m
CONFIG_SND_CMIPCI=m
CONFIG_SND_OXYGEN_LIB=m
CONFIG_SND_OXYGEN=m
CONFIG_SND_CS4281=m
CONFIG_SND_CS46XX=m
CONFIG_SND_CS46XX_NEW_DSP=y
CONFIG_SND_CTXFI=m
CONFIG_SND_DARLA20=m
CONFIG_SND_GINA20=m
CONFIG_SND_LAYLA20=m
CONFIG_SND_DARLA24=m
CONFIG_SND_GINA24=m
CONFIG_SND_LAYLA24=m
CONFIG_SND_MONA=m
CONFIG_SND_MIA=m
CONFIG_SND_ECHO3G=m
CONFIG_SND_INDIGO=m
CONFIG_SND_INDIGOIO=m
CONFIG_SND_INDIGODJ=m
CONFIG_SND_INDIGOIOX=m
CONFIG_SND_INDIGODJX=m
CONFIG_SND_ENS1370=m
CONFIG_SND_ENS1371=m
CONFIG_SND_FM801=m
CONFIG_SND_FM801_TEA575X_BOOL=y
CONFIG_SND_HDSP=m
CONFIG_SND_HDSPM=m
CONFIG_SND_ICE1724=m
CONFIG_SND_INTEL8X0=m
CONFIG_SND_INTEL8X0M=m
CONFIG_SND_KORG1212=m
CONFIG_SND_LOLA=m
CONFIG_SND_LX6464ES=m
CONFIG_SND_MIXART=m
CONFIG_SND_NM256=m
CONFIG_SND_PCXHR=m
CONFIG_SND_RIPTIDE=m
CONFIG_SND_RME32=m
CONFIG_SND_RME96=m
CONFIG_SND_RME9652=m
CONFIG_SND_VIA82XX=m
CONFIG_SND_VIA82XX_MODEM=m
CONFIG_SND_VIRTUOSO=m
CONFIG_SND_VX222=m
CONFIG_SND_YMFPCI=m

#
# HD-Audio
#
CONFIG_SND_HDA=m
CONFIG_SND_HDA_INTEL=m
CONFIG_SND_HDA_HWDEP=y
CONFIG_SND_HDA_RECONFIG=y
CONFIG_SND_HDA_INPUT_BEEP=y
CONFIG_SND_HDA_INPUT_BEEP_MODE=0
CONFIG_SND_HDA_PATCH_LOADER=y
CONFIG_SND_HDA_CODEC_REALTEK=m
CONFIG_SND_HDA_CODEC_ANALOG=m
CONFIG_SND_HDA_CODEC_SIGMATEL=m
CONFIG_SND_HDA_CODEC_VIA=m
CONFIG_SND_HDA_CODEC_HDMI=m
CONFIG_SND_HDA_CODEC_CIRRUS=m
CONFIG_SND_HDA_CODEC_CONEXANT=m
CONFIG_SND_HDA_CODEC_CA0110=m
CONFIG_SND_HDA_CODEC_CA0132=m
CONFIG_SND_HDA_CODEC_CA0132_DSP=y
CONFIG_SND_HDA_CODEC_CMEDIA=m
CONFIG_SND_HDA_CODEC_SI3054=m
CONFIG_SND_HDA_GENERIC=m
CONFIG_SND_HDA_POWER_SAVE_DEFAULT=0
CONFIG_SND_HDA_CORE=m
CONFIG_SND_HDA_DSP_LOADER=y
CONFIG_SND_HDA_I915=y
CONFIG_SND_HDA_EXT_CORE=m
CONFIG_SND_HDA_PREALLOC_SIZE=64
CONFIG_SND_SPI=y
CONFIG_SND_USB=y
CONFIG_SND_USB_AUDIO=m
CONFIG_SND_USB_UA101=m
CONFIG_SND_USB_USX2Y=m
CONFIG_SND_USB_CAIAQ=m
CONFIG_SND_USB_CAIAQ_INPUT=y
CONFIG_SND_USB_US122L=m
CONFIG_SND_USB_6FIRE=m
CONFIG_SND_USB_HIFACE=m
CONFIG_SND_BCD2000=m
CONFIG_SND_USB_LINE6=m
CONFIG_SND_USB_POD=m
CONFIG_SND_USB_PODHD=m
CONFIG_SND_USB_TONEPORT=m
CONFIG_SND_USB_VARIAX=m
CONFIG_SND_FIREWIRE=y
CONFIG_SND_FIREWIRE_LIB=m
CONFIG_SND_DICE=m
CONFIG_SND_OXFW=m
CONFIG_SND_ISIGHT=m
CONFIG_SND_SCS1X=m
CONFIG_SND_FIREWORKS=m
CONFIG_SND_BEBOB=m
CONFIG_SND_FIREWIRE_DIGI00X=m
CONFIG_SND_FIREWIRE_TASCAM=m
CONFIG_SND_PCMCIA=y
CONFIG_SND_VXPOCKET=m
CONFIG_SND_PDAUDIOCF=m
CONFIG_SND_SOC=m
CONFIG_SND_SOC_AC97_BUS=y
CONFIG_SND_SOC_GENERIC_DMAENGINE_PCM=y
CONFIG_SND_SOC_COMPRESS=y
CONFIG_SND_SOC_TOPOLOGY=y
CONFIG_SND_ATMEL_SOC=m
CONFIG_SND_DESIGNWARE_I2S=m

#
# SoC Audio for Freescale CPUs
#

#
# Common SoC Audio options for Freescale CPUs:
#
CONFIG_SND_SOC_FSL_ASRC=m
CONFIG_SND_SOC_FSL_SAI=m
CONFIG_SND_SOC_FSL_SSI=m
CONFIG_SND_SOC_FSL_SPDIF=m
CONFIG_SND_SOC_FSL_ESAI=m
CONFIG_SND_SOC_IMX_AUDMUX=m
CONFIG_SND_SST_MFLD_PLATFORM=m
CONFIG_SND_SST_IPC=m
CONFIG_SND_SST_IPC_ACPI=m
CONFIG_SND_SOC_INTEL_SST=m
CONFIG_SND_SOC_INTEL_SST_ACPI=m
CONFIG_SND_SOC_INTEL_HASWELL=m
CONFIG_SND_SOC_INTEL_BAYTRAIL=m
CONFIG_SND_SOC_INTEL_HASWELL_MACH=m
CONFIG_SND_SOC_INTEL_BYT_RT5640_MACH=m
CONFIG_SND_SOC_INTEL_BYT_MAX98090_MACH=m
CONFIG_SND_SOC_INTEL_BROADWELL_MACH=m
CONFIG_SND_SOC_INTEL_BYTCR_RT5640_MACH=m
CONFIG_SND_SOC_INTEL_CHT_BSW_RT5672_MACH=m
CONFIG_SND_SOC_INTEL_CHT_BSW_RT5645_MACH=m
CONFIG_SND_SOC_INTEL_CHT_BSW_MAX98090_TI_MACH=m
CONFIG_SND_SOC_INTEL_SKYLAKE=m
CONFIG_SND_SOC_INTEL_SKL_RT286_MACH=m

#
# Allwinner SoC Audio support
#
CONFIG_SND_SUN4I_CODEC=m
CONFIG_SND_SOC_XTFPGA_I2S=m
CONFIG_SND_SOC_I2C_AND_SPI=m

#
# CODEC drivers
#
CONFIG_SND_SOC_AC97_CODEC=m
CONFIG_SND_SOC_ADAU1701=m
CONFIG_SND_SOC_AK4104=m
CONFIG_SND_SOC_AK4554=m
CONFIG_SND_SOC_AK4613=m
CONFIG_SND_SOC_AK4642=m
CONFIG_SND_SOC_AK5386=m
CONFIG_SND_SOC_ALC5623=m
CONFIG_SND_SOC_CS35L32=m
CONFIG_SND_SOC_CS42L51=m
CONFIG_SND_SOC_CS42L51_I2C=m
CONFIG_SND_SOC_CS42L52=m
CONFIG_SND_SOC_CS42L56=m
CONFIG_SND_SOC_CS42L73=m
CONFIG_SND_SOC_CS4265=m
CONFIG_SND_SOC_CS4270=m
CONFIG_SND_SOC_CS4271=m
CONFIG_SND_SOC_CS4271_I2C=m
CONFIG_SND_SOC_CS4271_SPI=m
CONFIG_SND_SOC_CS42XX8=m
CONFIG_SND_SOC_CS42XX8_I2C=m
CONFIG_SND_SOC_CS4349=m
CONFIG_SND_SOC_DMIC=m
CONFIG_SND_SOC_ES8328=m
CONFIG_SND_SOC_GTM601=m
CONFIG_SND_SOC_MAX98090=m
CONFIG_SND_SOC_PCM1681=m
CONFIG_SND_SOC_PCM1792A=m
CONFIG_SND_SOC_PCM512x=m
CONFIG_SND_SOC_PCM512x_I2C=m
CONFIG_SND_SOC_PCM512x_SPI=m
CONFIG_SND_SOC_RL6231=m
CONFIG_SND_SOC_RL6347A=m
CONFIG_SND_SOC_RT286=m
CONFIG_SND_SOC_RT5631=m
CONFIG_SND_SOC_RT5640=m
CONFIG_SND_SOC_RT5645=m
CONFIG_SND_SOC_RT5670=m
# CONFIG_SND_SOC_RT5677_SPI is not set
CONFIG_SND_SOC_SGTL5000=m
CONFIG_SND_SOC_SI476X=m
CONFIG_SND_SOC_SIGMADSP=m
CONFIG_SND_SOC_SIGMADSP_I2C=m
CONFIG_SND_SOC_SIRF_AUDIO_CODEC=m
CONFIG_SND_SOC_SPDIF=m
CONFIG_SND_SOC_SSM2602=m
CONFIG_SND_SOC_SSM2602_SPI=m
CONFIG_SND_SOC_SSM2602_I2C=m
CONFIG_SND_SOC_SSM4567=m
CONFIG_SND_SOC_STA32X=m
CONFIG_SND_SOC_STA350=m
CONFIG_SND_SOC_STI_SAS=m
CONFIG_SND_SOC_TAS2552=m
CONFIG_SND_SOC_TAS5086=m
CONFIG_SND_SOC_TAS571X=m
CONFIG_SND_SOC_TFA9879=m
CONFIG_SND_SOC_TLV320AIC23=m
CONFIG_SND_SOC_TLV320AIC23_I2C=m
CONFIG_SND_SOC_TLV320AIC23_SPI=m
CONFIG_SND_SOC_TLV320AIC31XX=m
CONFIG_SND_SOC_TLV320AIC3X=m
CONFIG_SND_SOC_TS3A227E=m
CONFIG_SND_SOC_WM8510=m
CONFIG_SND_SOC_WM8523=m
CONFIG_SND_SOC_WM8580=m
CONFIG_SND_SOC_WM8711=m
CONFIG_SND_SOC_WM8728=m
CONFIG_SND_SOC_WM8731=m
CONFIG_SND_SOC_WM8737=m
CONFIG_SND_SOC_WM8741=m
CONFIG_SND_SOC_WM8750=m
CONFIG_SND_SOC_WM8753=m
CONFIG_SND_SOC_WM8770=m
CONFIG_SND_SOC_WM8776=m
CONFIG_SND_SOC_WM8804=m
CONFIG_SND_SOC_WM8804_I2C=m
CONFIG_SND_SOC_WM8804_SPI=m
CONFIG_SND_SOC_WM8903=m
CONFIG_SND_SOC_WM8962=m
CONFIG_SND_SOC_WM8978=m
CONFIG_SND_SOC_TPA6130A2=m
CONFIG_SND_SIMPLE_CARD=m
# CONFIG_SOUND_PRIME is not set
CONFIG_AC97_BUS=m

#
# HID support
#
CONFIG_HID=m
CONFIG_HID_BATTERY_STRENGTH=y
CONFIG_HIDRAW=y
CONFIG_UHID=m
CONFIG_HID_GENERIC=m

#
# Special HID drivers
#
CONFIG_HID_A4TECH=m
CONFIG_HID_ACRUX=m
CONFIG_HID_ACRUX_FF=y
CONFIG_HID_APPLE=m
CONFIG_HID_APPLEIR=m
CONFIG_HID_AUREAL=m
CONFIG_HID_BELKIN=m
CONFIG_HID_BETOP_FF=m
CONFIG_HID_CHERRY=m
CONFIG_HID_CHICONY=m
CONFIG_HID_CORSAIR=m
CONFIG_HID_PRODIKEYS=m
CONFIG_HID_CP2112=m
CONFIG_HID_CYPRESS=m
CONFIG_HID_DRAGONRISE=m
CONFIG_DRAGONRISE_FF=y
CONFIG_HID_EMS_FF=m
CONFIG_HID_ELECOM=m
CONFIG_HID_ELO=m
CONFIG_HID_EZKEY=m
CONFIG_HID_GEMBIRD=m
CONFIG_HID_GFRM=m
CONFIG_HID_HOLTEK=m
CONFIG_HOLTEK_FF=y
CONFIG_HID_GT683R=m
CONFIG_HID_KEYTOUCH=m
CONFIG_HID_KYE=m
CONFIG_HID_UCLOGIC=m
CONFIG_HID_WALTOP=m
CONFIG_HID_GYRATION=m
CONFIG_HID_ICADE=m
CONFIG_HID_TWINHAN=m
CONFIG_HID_KENSINGTON=m
CONFIG_HID_LCPOWER=m
CONFIG_HID_LENOVO=m
CONFIG_HID_LOGITECH=m
CONFIG_HID_LOGITECH_DJ=m
CONFIG_HID_LOGITECH_HIDPP=m
CONFIG_LOGITECH_FF=y
CONFIG_LOGIRUMBLEPAD2_FF=y
CONFIG_LOGIG940_FF=y
CONFIG_LOGIWHEELS_FF=y
CONFIG_HID_MAGICMOUSE=m
CONFIG_HID_MICROSOFT=m
CONFIG_HID_MONTEREY=m
CONFIG_HID_MULTITOUCH=m
CONFIG_HID_NTRIG=m
CONFIG_HID_ORTEK=m
CONFIG_HID_PANTHERLORD=m
CONFIG_PANTHERLORD_FF=y
CONFIG_HID_PENMOUNT=m
CONFIG_HID_PETALYNX=m
CONFIG_HID_PICOLCD=m
CONFIG_HID_PICOLCD_FB=y
CONFIG_HID_PICOLCD_BACKLIGHT=y
CONFIG_HID_PICOLCD_LCD=y
CONFIG_HID_PICOLCD_LEDS=y
CONFIG_HID_PICOLCD_CIR=y
CONFIG_HID_PLANTRONICS=m
CONFIG_HID_PRIMAX=m
CONFIG_HID_ROCCAT=m
CONFIG_HID_SAITEK=m
CONFIG_HID_SAMSUNG=m
CONFIG_HID_SONY=m
CONFIG_SONY_FF=y
CONFIG_HID_SPEEDLINK=m
CONFIG_HID_STEELSERIES=m
CONFIG_HID_SUNPLUS=m
CONFIG_HID_RMI=m
CONFIG_HID_GREENASIA=m
CONFIG_GREENASIA_FF=y
CONFIG_HID_HYPERV_MOUSE=m
CONFIG_HID_SMARTJOYPLUS=m
CONFIG_SMARTJOYPLUS_FF=y
CONFIG_HID_TIVO=m
CONFIG_HID_TOPSEED=m
CONFIG_HID_THINGM=m
CONFIG_HID_THRUSTMASTER=m
CONFIG_THRUSTMASTER_FF=y
CONFIG_HID_WACOM=m
CONFIG_HID_WIIMOTE=m
CONFIG_HID_XINMO=m
CONFIG_HID_ZEROPLUS=m
CONFIG_ZEROPLUS_FF=y
CONFIG_HID_ZYDACRON=m
CONFIG_HID_SENSOR_HUB=m
CONFIG_HID_SENSOR_CUSTOM_SENSOR=m

#
# USB HID support
#
CONFIG_USB_HID=m
CONFIG_HID_PID=y
CONFIG_USB_HIDDEV=y

#
# USB HID Boot Protocol drivers
#
CONFIG_USB_KBD=m
CONFIG_USB_MOUSE=m

#
# I2C HID support
#
CONFIG_I2C_HID=m
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_SUPPORT=y
CONFIG_USB_COMMON=y
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB=y
CONFIG_USB_ANNOUNCE_NEW_DEVICES=y

#
# Miscellaneous USB options
#
CONFIG_USB_DEFAULT_PERSIST=y
CONFIG_USB_DYNAMIC_MINORS=y
# CONFIG_USB_OTG is not set
# CONFIG_USB_OTG_WHITELIST is not set
# CONFIG_USB_OTG_BLACKLIST_HUB is not set
CONFIG_USB_ULPI_BUS=m
CONFIG_USB_MON=m
CONFIG_USB_WUSB=m
CONFIG_USB_WUSB_CBAF=m
# CONFIG_USB_WUSB_CBAF_DEBUG is not set

#
# USB Host Controller Drivers
#
CONFIG_USB_C67X00_HCD=m
CONFIG_USB_XHCI_HCD=y
CONFIG_USB_XHCI_PCI=y
CONFIG_USB_XHCI_PLATFORM=m
CONFIG_USB_EHCI_HCD=y
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_EHCI_TT_NEWSCHED=y
CONFIG_USB_EHCI_PCI=y
CONFIG_USB_EHCI_HCD_PLATFORM=y
CONFIG_USB_OXU210HP_HCD=m
CONFIG_USB_ISP116X_HCD=m
CONFIG_USB_ISP1362_HCD=m
CONFIG_USB_FOTG210_HCD=m
CONFIG_USB_MAX3421_HCD=m
CONFIG_USB_OHCI_HCD=y
CONFIG_USB_OHCI_HCD_PCI=y
CONFIG_USB_OHCI_HCD_PLATFORM=y
CONFIG_USB_UHCI_HCD=y
CONFIG_USB_U132_HCD=m
CONFIG_USB_SL811_HCD=m
CONFIG_USB_SL811_HCD_ISO=y
CONFIG_USB_SL811_CS=m
CONFIG_USB_R8A66597_HCD=m
CONFIG_USB_WHCI_HCD=m
CONFIG_USB_HWA_HCD=m
CONFIG_USB_HCD_BCMA=m
CONFIG_USB_HCD_SSB=m
# CONFIG_USB_HCD_TEST_MODE is not set

#
# USB Device Class drivers
#
CONFIG_USB_ACM=m
CONFIG_USB_PRINTER=m
CONFIG_USB_WDM=m
CONFIG_USB_TMC=m

#
# NOTE: USB_STORAGE depends on SCSI but BLK_DEV_SD may
#

#
# also be needed; see USB_STORAGE Help for more info
#
CONFIG_USB_STORAGE=m
# CONFIG_USB_STORAGE_DEBUG is not set
CONFIG_USB_STORAGE_REALTEK=m
CONFIG_REALTEK_AUTOPM=y
CONFIG_USB_STORAGE_DATAFAB=m
CONFIG_USB_STORAGE_FREECOM=m
CONFIG_USB_STORAGE_ISD200=m
CONFIG_USB_STORAGE_USBAT=m
CONFIG_USB_STORAGE_SDDR09=m
CONFIG_USB_STORAGE_SDDR55=m
CONFIG_USB_STORAGE_JUMPSHOT=m
CONFIG_USB_STORAGE_ALAUDA=m
CONFIG_USB_STORAGE_ONETOUCH=m
CONFIG_USB_STORAGE_KARMA=m
CONFIG_USB_STORAGE_CYPRESS_ATACB=m
CONFIG_USB_STORAGE_ENE_UB6250=m
CONFIG_USB_UAS=m

#
# USB Imaging devices
#
CONFIG_USB_MDC800=m
CONFIG_USB_MICROTEK=m
CONFIG_USBIP_CORE=m
CONFIG_USBIP_VHCI_HCD=m
CONFIG_USBIP_HOST=m
# CONFIG_USBIP_DEBUG is not set
CONFIG_USB_MUSB_HDRC=m
# CONFIG_USB_MUSB_HOST is not set
# CONFIG_USB_MUSB_GADGET is not set
CONFIG_USB_MUSB_DUAL_ROLE=y

#
# Platform Glue Layer
#

#
# MUSB DMA mode
#
CONFIG_MUSB_PIO_ONLY=y
CONFIG_USB_DWC3=m
CONFIG_USB_DWC3_ULPI=y
# CONFIG_USB_DWC3_HOST is not set
# CONFIG_USB_DWC3_GADGET is not set
CONFIG_USB_DWC3_DUAL_ROLE=y

#
# Platform Glue Driver Support
#
CONFIG_USB_DWC3_PCI=m
CONFIG_USB_DWC2=y
CONFIG_USB_DWC2_HOST=y

#
# Gadget/Dual-role mode requires USB Gadget support to be enabled
#
CONFIG_USB_DWC2_PCI=y
# CONFIG_USB_DWC2_DEBUG is not set
# CONFIG_USB_DWC2_TRACK_MISSED_SOFS is not set
CONFIG_USB_CHIPIDEA=m
CONFIG_USB_CHIPIDEA_PCI=m
CONFIG_USB_CHIPIDEA_UDC=y
CONFIG_USB_CHIPIDEA_HOST=y
# CONFIG_USB_CHIPIDEA_DEBUG is not set
CONFIG_USB_ISP1760=m
CONFIG_USB_ISP1760_HCD=y
CONFIG_USB_ISP1761_UDC=y
# CONFIG_USB_ISP1760_HOST_ROLE is not set
# CONFIG_USB_ISP1760_GADGET_ROLE is not set
CONFIG_USB_ISP1760_DUAL_ROLE=y

#
# USB port drivers
#
CONFIG_USB_USS720=m
CONFIG_USB_SERIAL=m
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_SIMPLE=m
CONFIG_USB_SERIAL_AIRCABLE=m
CONFIG_USB_SERIAL_ARK3116=m
CONFIG_USB_SERIAL_BELKIN=m
CONFIG_USB_SERIAL_CH341=m
CONFIG_USB_SERIAL_WHITEHEAT=m
CONFIG_USB_SERIAL_DIGI_ACCELEPORT=m
CONFIG_USB_SERIAL_CP210X=m
CONFIG_USB_SERIAL_CYPRESS_M8=m
CONFIG_USB_SERIAL_EMPEG=m
CONFIG_USB_SERIAL_FTDI_SIO=m
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_IPAQ=m
CONFIG_USB_SERIAL_IR=m
CONFIG_USB_SERIAL_EDGEPORT=m
CONFIG_USB_SERIAL_EDGEPORT_TI=m
CONFIG_USB_SERIAL_F81232=m
CONFIG_USB_SERIAL_GARMIN=m
CONFIG_USB_SERIAL_IPW=m
CONFIG_USB_SERIAL_IUU=m
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KEYSPAN=m
CONFIG_USB_SERIAL_KEYSPAN_MPR=y
CONFIG_USB_SERIAL_KEYSPAN_USA28=y
CONFIG_USB_SERIAL_KEYSPAN_USA28X=y
CONFIG_USB_SERIAL_KEYSPAN_USA28XA=y
CONFIG_USB_SERIAL_KEYSPAN_USA28XB=y
CONFIG_USB_SERIAL_KEYSPAN_USA19=y
CONFIG_USB_SERIAL_KEYSPAN_USA18X=y
CONFIG_USB_SERIAL_KEYSPAN_USA19W=y
CONFIG_USB_SERIAL_KEYSPAN_USA19QW=y
CONFIG_USB_SERIAL_KEYSPAN_USA19QI=y
CONFIG_USB_SERIAL_KEYSPAN_USA49W=y
CONFIG_USB_SERIAL_KEYSPAN_USA49WLC=y
CONFIG_USB_SERIAL_KLSI=m
CONFIG_USB_SERIAL_KOBIL_SCT=m
CONFIG_USB_SERIAL_MCT_U232=m
CONFIG_USB_SERIAL_METRO=m
CONFIG_USB_SERIAL_MOS7720=m
CONFIG_USB_SERIAL_MOS7715_PARPORT=y
CONFIG_USB_SERIAL_MOS7840=m
CONFIG_USB_SERIAL_MXUPORT=m
CONFIG_USB_SERIAL_NAVMAN=m
CONFIG_USB_SERIAL_PL2303=m
CONFIG_USB_SERIAL_OTI6858=m
CONFIG_USB_SERIAL_QCAUX=m
CONFIG_USB_SERIAL_QUALCOMM=m
CONFIG_USB_SERIAL_SPCP8X5=m
CONFIG_USB_SERIAL_SAFE=m
# CONFIG_USB_SERIAL_SAFE_PADDED is not set
CONFIG_USB_SERIAL_SIERRAWIRELESS=m
CONFIG_USB_SERIAL_SYMBOL=m
CONFIG_USB_SERIAL_TI=m
CONFIG_USB_SERIAL_CYBERJACK=m
CONFIG_USB_SERIAL_XIRCOM=m
CONFIG_USB_SERIAL_WWAN=m
CONFIG_USB_SERIAL_OPTION=m
CONFIG_USB_SERIAL_OMNINET=m
CONFIG_USB_SERIAL_OPTICON=m
CONFIG_USB_SERIAL_XSENS_MT=m
CONFIG_USB_SERIAL_WISHBONE=m
CONFIG_USB_SERIAL_SSU100=m
CONFIG_USB_SERIAL_QT2=m
CONFIG_USB_SERIAL_DEBUG=m

#
# USB Miscellaneous drivers
#
CONFIG_USB_EMI62=m
CONFIG_USB_EMI26=m
CONFIG_USB_ADUTUX=m
CONFIG_USB_SEVSEG=m
CONFIG_USB_RIO500=m
CONFIG_USB_LEGOTOWER=m
CONFIG_USB_LCD=m
CONFIG_USB_LED=m
CONFIG_USB_CYPRESS_CY7C63=m
CONFIG_USB_CYTHERM=m
CONFIG_USB_IDMOUSE=m
CONFIG_USB_FTDI_ELAN=m
CONFIG_USB_APPLEDISPLAY=m
CONFIG_USB_SISUSBVGA=m
# CONFIG_USB_SISUSBVGA_CON is not set
CONFIG_USB_LD=m
CONFIG_USB_TRANCEVIBRATOR=m
CONFIG_USB_IOWARRIOR=m
CONFIG_USB_TEST=m
CONFIG_USB_EHSET_TEST_FIXTURE=m
CONFIG_USB_ISIGHTFW=m
CONFIG_USB_YUREX=m
CONFIG_USB_EZUSB_FX2=m
CONFIG_USB_HSIC_USB3503=m
CONFIG_USB_LINK_LAYER_TEST=m
CONFIG_USB_CHAOSKEY=m
CONFIG_USB_ATM=m
CONFIG_USB_SPEEDTOUCH=m
CONFIG_USB_CXACRU=m
CONFIG_USB_UEAGLEATM=m
CONFIG_USB_XUSBATM=m

#
# USB Physical Layer drivers
#
CONFIG_USB_PHY=y
CONFIG_NOP_USB_XCEIV=y
CONFIG_USB_GPIO_VBUS=m
CONFIG_TAHVO_USB=m
CONFIG_TAHVO_USB_HOST_BY_DEFAULT=y
CONFIG_USB_ISP1301=m
CONFIG_USB_GADGET=m
# CONFIG_USB_GADGET_DEBUG is not set
# CONFIG_USB_GADGET_DEBUG_FILES is not set
# CONFIG_USB_GADGET_DEBUG_FS is not set
CONFIG_USB_GADGET_VBUS_DRAW=2
CONFIG_USB_GADGET_STORAGE_NUM_BUFFERS=2

#
# USB Peripheral Controller
#
CONFIG_USB_FOTG210_UDC=m
CONFIG_USB_GR_UDC=m
CONFIG_USB_R8A66597=m
CONFIG_USB_PXA27X=m
CONFIG_USB_MV_UDC=m
CONFIG_USB_MV_U3D=m
# CONFIG_USB_M66592 is not set
CONFIG_USB_BDC_UDC=m

#
# Platform Support
#
CONFIG_USB_BDC_PCI=m
CONFIG_USB_AMD5536UDC=m
CONFIG_USB_NET2272=m
CONFIG_USB_NET2272_DMA=y
CONFIG_USB_NET2280=m
CONFIG_USB_GOKU=m
CONFIG_USB_EG20T=m
# CONFIG_USB_DUMMY_HCD is not set
CONFIG_USB_LIBCOMPOSITE=m
CONFIG_USB_F_ACM=m
CONFIG_USB_F_SS_LB=m
CONFIG_USB_U_SERIAL=m
CONFIG_USB_U_ETHER=m
CONFIG_USB_F_SERIAL=m
CONFIG_USB_F_OBEX=m
CONFIG_USB_F_NCM=m
CONFIG_USB_F_ECM=m
CONFIG_USB_F_PHONET=m
CONFIG_USB_F_EEM=m
CONFIG_USB_F_SUBSET=m
CONFIG_USB_F_RNDIS=m
CONFIG_USB_F_MASS_STORAGE=m
CONFIG_USB_F_FS=m
CONFIG_USB_F_UAC1=m
CONFIG_USB_F_UAC2=m
CONFIG_USB_F_UVC=m
CONFIG_USB_F_MIDI=m
CONFIG_USB_F_HID=m
CONFIG_USB_F_PRINTER=m
CONFIG_USB_CONFIGFS=m
CONFIG_USB_CONFIGFS_SERIAL=y
CONFIG_USB_CONFIGFS_ACM=y
CONFIG_USB_CONFIGFS_OBEX=y
CONFIG_USB_CONFIGFS_NCM=y
CONFIG_USB_CONFIGFS_ECM=y
CONFIG_USB_CONFIGFS_ECM_SUBSET=y
CONFIG_USB_CONFIGFS_RNDIS=y
CONFIG_USB_CONFIGFS_EEM=y
CONFIG_USB_CONFIGFS_PHONET=y
CONFIG_USB_CONFIGFS_MASS_STORAGE=y
CONFIG_USB_CONFIGFS_F_LB_SS=y
CONFIG_USB_CONFIGFS_F_FS=y
CONFIG_USB_CONFIGFS_F_UAC1=y
CONFIG_USB_CONFIGFS_F_UAC2=y
CONFIG_USB_CONFIGFS_F_MIDI=y
CONFIG_USB_CONFIGFS_F_HID=y
CONFIG_USB_CONFIGFS_F_UVC=y
CONFIG_USB_CONFIGFS_F_PRINTER=y
CONFIG_USB_ZERO=m
CONFIG_USB_AUDIO=m
CONFIG_GADGET_UAC1=y
CONFIG_USB_ETH=m
CONFIG_USB_ETH_RNDIS=y
CONFIG_USB_ETH_EEM=y
CONFIG_USB_G_NCM=m
CONFIG_USB_GADGETFS=m
CONFIG_USB_FUNCTIONFS=m
CONFIG_USB_FUNCTIONFS_ETH=y
CONFIG_USB_FUNCTIONFS_RNDIS=y
CONFIG_USB_FUNCTIONFS_GENERIC=y
CONFIG_USB_MASS_STORAGE=m
CONFIG_USB_GADGET_TARGET=m
CONFIG_USB_G_SERIAL=m
CONFIG_USB_MIDI_GADGET=m
CONFIG_USB_G_PRINTER=m
CONFIG_USB_CDC_COMPOSITE=m
CONFIG_USB_G_NOKIA=m
CONFIG_USB_G_ACM_MS=m
# CONFIG_USB_G_MULTI is not set
CONFIG_USB_G_HID=m
CONFIG_USB_G_DBGP=m
# CONFIG_USB_G_DBGP_PRINTK is not set
CONFIG_USB_G_DBGP_SERIAL=y
CONFIG_USB_G_WEBCAM=m
CONFIG_USB_LED_TRIG=y
CONFIG_UWB=m
CONFIG_UWB_HWA=m
CONFIG_UWB_WHCI=m
CONFIG_UWB_I1480U=m
CONFIG_MMC=y
# CONFIG_MMC_DEBUG is not set

#
# MMC/SD/SDIO Card Drivers
#
CONFIG_MMC_BLOCK=m
CONFIG_MMC_BLOCK_MINORS=8
CONFIG_MMC_BLOCK_BOUNCE=y
CONFIG_SDIO_UART=m
# CONFIG_MMC_TEST is not set

#
# MMC/SD/SDIO Host Controller Drivers
#
CONFIG_MMC_SDHCI=m
CONFIG_MMC_SDHCI_PCI=m
CONFIG_MMC_RICOH_MMC=y
CONFIG_MMC_SDHCI_ACPI=m
CONFIG_MMC_SDHCI_PLTFM=m
CONFIG_MMC_WBSD=m
CONFIG_MMC_TIFM_SD=m
CONFIG_MMC_SPI=m
CONFIG_MMC_SDRICOH_CS=m
CONFIG_MMC_CB710=m
CONFIG_MMC_VIA_SDMMC=m
CONFIG_MMC_VUB300=m
CONFIG_MMC_USHC=m
CONFIG_MMC_USDHI6ROL0=m
CONFIG_MMC_REALTEK_PCI=m
CONFIG_MMC_REALTEK_USB=m
CONFIG_MMC_TOSHIBA_PCI=m
CONFIG_MMC_MTK=m
CONFIG_MEMSTICK=m
# CONFIG_MEMSTICK_DEBUG is not set

#
# MemoryStick drivers
#
# CONFIG_MEMSTICK_UNSAFE_RESUME is not set
CONFIG_MSPRO_BLOCK=m
CONFIG_MS_BLOCK=m

#
# MemoryStick Host Controller Drivers
#
CONFIG_MEMSTICK_TIFM_MS=m
CONFIG_MEMSTICK_JMICRON_38X=m
CONFIG_MEMSTICK_R592=m
CONFIG_MEMSTICK_REALTEK_PCI=m
CONFIG_MEMSTICK_REALTEK_USB=m
CONFIG_NEW_LEDS=y
CONFIG_LEDS_CLASS=y
CONFIG_LEDS_CLASS_FLASH=m

#
# LED drivers
#
CONFIG_LEDS_88PM860X=m
CONFIG_LEDS_LM3530=m
CONFIG_LEDS_LM3533=m
CONFIG_LEDS_LM3642=m
CONFIG_LEDS_PCA9532=m
CONFIG_LEDS_PCA9532_GPIO=y
CONFIG_LEDS_GPIO=m
CONFIG_LEDS_LP3944=m
CONFIG_LEDS_LP55XX_COMMON=m
CONFIG_LEDS_LP5521=m
CONFIG_LEDS_LP5523=m
CONFIG_LEDS_LP5562=m
CONFIG_LEDS_LP8501=m
CONFIG_LEDS_LP8788=m
CONFIG_LEDS_LP8860=m
CONFIG_LEDS_CLEVO_MAIL=m
CONFIG_LEDS_PCA955X=m
CONFIG_LEDS_PCA963X=m
CONFIG_LEDS_WM831X_STATUS=m
CONFIG_LEDS_WM8350=m
CONFIG_LEDS_DA903X=m
CONFIG_LEDS_DA9052=m
CONFIG_LEDS_DAC124S085=m
CONFIG_LEDS_PWM=m
CONFIG_LEDS_REGULATOR=m
CONFIG_LEDS_BD2802=m
CONFIG_LEDS_INTEL_SS4200=m
CONFIG_LEDS_LT3593=m
CONFIG_LEDS_ADP5520=m
CONFIG_LEDS_DELL_NETBOOKS=m
CONFIG_LEDS_MC13783=m
CONFIG_LEDS_TCA6507=m
CONFIG_LEDS_TLC591XX=m
CONFIG_LEDS_MAX8997=m
CONFIG_LEDS_LM355x=m
CONFIG_LEDS_MENF21BMC=m

#
# LED driver for blink(1) USB RGB LED is under Special HID drivers (HID_THINGM)
#
CONFIG_LEDS_BLINKM=m

#
# LED Triggers
#
CONFIG_LEDS_TRIGGERS=y
CONFIG_LEDS_TRIGGER_TIMER=m
CONFIG_LEDS_TRIGGER_ONESHOT=m
CONFIG_LEDS_TRIGGER_HEARTBEAT=m
CONFIG_LEDS_TRIGGER_BACKLIGHT=m
CONFIG_LEDS_TRIGGER_CPU=y
CONFIG_LEDS_TRIGGER_GPIO=m
CONFIG_LEDS_TRIGGER_DEFAULT_ON=m

#
# iptables trigger is under Netfilter config (LED target)
#
CONFIG_LEDS_TRIGGER_TRANSIENT=m
CONFIG_LEDS_TRIGGER_CAMERA=m
# CONFIG_ACCESSIBILITY is not set
CONFIG_INFINIBAND=m
CONFIG_INFINIBAND_USER_MAD=m
CONFIG_INFINIBAND_USER_ACCESS=m
CONFIG_INFINIBAND_USER_MEM=y
CONFIG_INFINIBAND_ON_DEMAND_PAGING=y
CONFIG_INFINIBAND_ADDR_TRANS=y
CONFIG_INFINIBAND_MTHCA=m
# CONFIG_INFINIBAND_MTHCA_DEBUG is not set
CONFIG_INFINIBAND_QIB=m
CONFIG_INFINIBAND_QIB_DCA=y
CONFIG_INFINIBAND_CXGB3=m
# CONFIG_INFINIBAND_CXGB3_DEBUG is not set
CONFIG_INFINIBAND_CXGB4=m
CONFIG_MLX4_INFINIBAND=m
CONFIG_MLX5_INFINIBAND=m
CONFIG_INFINIBAND_NES=m
# CONFIG_INFINIBAND_NES_DEBUG is not set
CONFIG_INFINIBAND_OCRDMA=m
CONFIG_INFINIBAND_USNIC=m
CONFIG_INFINIBAND_IPOIB=m
CONFIG_INFINIBAND_IPOIB_CM=y
# CONFIG_INFINIBAND_IPOIB_DEBUG is not set
CONFIG_INFINIBAND_SRP=m
CONFIG_INFINIBAND_SRPT=m
CONFIG_INFINIBAND_ISER=m
CONFIG_INFINIBAND_ISERT=m
CONFIG_EDAC_ATOMIC_SCRUB=y
CONFIG_EDAC_SUPPORT=y
CONFIG_EDAC=y
# CONFIG_EDAC_LEGACY_SYSFS is not set
# CONFIG_EDAC_DEBUG is not set
CONFIG_EDAC_DECODE_MCE=m
CONFIG_EDAC_MM_EDAC=m
CONFIG_EDAC_AMD64=m
# CONFIG_EDAC_AMD64_ERROR_INJECTION is not set
CONFIG_EDAC_E752X=m
CONFIG_EDAC_I82975X=m
CONFIG_EDAC_I3000=m
CONFIG_EDAC_I3200=m
CONFIG_EDAC_IE31200=m
CONFIG_EDAC_X38=m
CONFIG_EDAC_I5400=m
CONFIG_EDAC_I7CORE=m
CONFIG_EDAC_I5000=m
CONFIG_EDAC_I5100=m
CONFIG_EDAC_I7300=m
CONFIG_EDAC_SBRIDGE=m
CONFIG_RTC_LIB=y
CONFIG_RTC_CLASS=y
CONFIG_RTC_HCTOSYS=y
CONFIG_RTC_HCTOSYS_DEVICE="rtc0"
CONFIG_RTC_SYSTOHC=y
CONFIG_RTC_SYSTOHC_DEVICE="rtc0"
# CONFIG_RTC_DEBUG is not set

#
# RTC interfaces
#
CONFIG_RTC_INTF_SYSFS=y
CONFIG_RTC_INTF_PROC=y
CONFIG_RTC_INTF_DEV=y
# CONFIG_RTC_INTF_DEV_UIE_EMUL is not set
# CONFIG_RTC_DRV_TEST is not set

#
# I2C RTC drivers
#
CONFIG_RTC_DRV_88PM860X=m
CONFIG_RTC_DRV_88PM80X=m
CONFIG_RTC_DRV_ABB5ZES3=m
CONFIG_RTC_DRV_ABX80X=m
CONFIG_RTC_DRV_DS1307=m
CONFIG_RTC_DRV_DS1374=m
CONFIG_RTC_DRV_DS1374_WDT=y
CONFIG_RTC_DRV_DS1672=m
CONFIG_RTC_DRV_DS3232=m
CONFIG_RTC_DRV_LP8788=m
CONFIG_RTC_DRV_MAX6900=m
CONFIG_RTC_DRV_MAX8907=m
CONFIG_RTC_DRV_MAX8925=m
CONFIG_RTC_DRV_MAX8998=m
CONFIG_RTC_DRV_MAX8997=m
CONFIG_RTC_DRV_RS5C372=m
CONFIG_RTC_DRV_ISL1208=m
CONFIG_RTC_DRV_ISL12022=m
CONFIG_RTC_DRV_ISL12057=m
CONFIG_RTC_DRV_X1205=m
CONFIG_RTC_DRV_PALMAS=m
CONFIG_RTC_DRV_PCF2127=m
CONFIG_RTC_DRV_PCF8523=m
CONFIG_RTC_DRV_PCF8563=m
CONFIG_RTC_DRV_PCF85063=m
CONFIG_RTC_DRV_PCF8583=m
CONFIG_RTC_DRV_M41T80=m
CONFIG_RTC_DRV_M41T80_WDT=y
CONFIG_RTC_DRV_BQ32K=m
CONFIG_RTC_DRV_TWL4030=m
CONFIG_RTC_DRV_TPS6586X=m
CONFIG_RTC_DRV_TPS65910=m
CONFIG_RTC_DRV_TPS80031=m
CONFIG_RTC_DRV_RC5T583=m
CONFIG_RTC_DRV_S35390A=m
CONFIG_RTC_DRV_FM3130=m
CONFIG_RTC_DRV_RX8581=m
CONFIG_RTC_DRV_RX8025=m
CONFIG_RTC_DRV_EM3027=m
CONFIG_RTC_DRV_RV3029C2=m
CONFIG_RTC_DRV_RV8803=m
CONFIG_RTC_DRV_S5M=m

#
# SPI RTC drivers
#
CONFIG_RTC_DRV_M41T93=m
CONFIG_RTC_DRV_M41T94=m
CONFIG_RTC_DRV_DS1305=m
CONFIG_RTC_DRV_DS1343=m
CONFIG_RTC_DRV_DS1347=m
CONFIG_RTC_DRV_DS1390=m
CONFIG_RTC_DRV_MAX6902=m
CONFIG_RTC_DRV_R9701=m
CONFIG_RTC_DRV_RS5C348=m
CONFIG_RTC_DRV_DS3234=m
CONFIG_RTC_DRV_PCF2123=m
CONFIG_RTC_DRV_RX4581=m
CONFIG_RTC_DRV_MCP795=m

#
# Platform RTC drivers
#
CONFIG_RTC_DRV_CMOS=y
CONFIG_RTC_DRV_DS1286=m
CONFIG_RTC_DRV_DS1511=m
CONFIG_RTC_DRV_DS1553=m
CONFIG_RTC_DRV_DS1685_FAMILY=m
CONFIG_RTC_DRV_DS1685=y
# CONFIG_RTC_DRV_DS1689 is not set
# CONFIG_RTC_DRV_DS17285 is not set
# CONFIG_RTC_DRV_DS17485 is not set
# CONFIG_RTC_DRV_DS17885 is not set
# CONFIG_RTC_DS1685_PROC_REGS is not set
# CONFIG_RTC_DS1685_SYSFS_REGS is not set
CONFIG_RTC_DRV_DS1742=m
CONFIG_RTC_DRV_DS2404=m
CONFIG_RTC_DRV_DA9052=m
CONFIG_RTC_DRV_DA9055=m
CONFIG_RTC_DRV_DA9063=m
CONFIG_RTC_DRV_STK17TA8=m
CONFIG_RTC_DRV_M48T86=m
CONFIG_RTC_DRV_M48T35=m
CONFIG_RTC_DRV_M48T59=m
CONFIG_RTC_DRV_MSM6242=m
CONFIG_RTC_DRV_BQ4802=m
CONFIG_RTC_DRV_RP5C01=m
CONFIG_RTC_DRV_V3020=m
CONFIG_RTC_DRV_WM831X=m
CONFIG_RTC_DRV_WM8350=m
CONFIG_RTC_DRV_PCF50633=m
CONFIG_RTC_DRV_AB3100=m

#
# on-CPU RTC drivers
#
CONFIG_RTC_DRV_PCAP=m
CONFIG_RTC_DRV_MC13XXX=m
CONFIG_RTC_DRV_MT6397=m

#
# HID Sensor RTC drivers
#
CONFIG_RTC_DRV_HID_SENSOR_TIME=m
CONFIG_DMADEVICES=y
# CONFIG_DMADEVICES_DEBUG is not set

#
# DMA Devices
#
CONFIG_DMA_ENGINE=y
CONFIG_DMA_VIRTUAL_CHANNELS=m
CONFIG_DMA_ACPI=y
CONFIG_INTEL_IDMA64=m
CONFIG_INTEL_IOATDMA=m
CONFIG_INTEL_MIC_X100_DMA=m
CONFIG_DW_DMAC_CORE=m
CONFIG_DW_DMAC=m
CONFIG_DW_DMAC_PCI=m
CONFIG_HSU_DMA=m

#
# DMA Clients
#
CONFIG_ASYNC_TX_DMA=y
# CONFIG_DMATEST is not set
CONFIG_DMA_ENGINE_RAID=y
CONFIG_DCA=m
CONFIG_AUXDISPLAY=y
CONFIG_KS0108=m
CONFIG_KS0108_PORT=0x378
CONFIG_KS0108_DELAY=2
CONFIG_CFAG12864B=m
CONFIG_CFAG12864B_RATE=20
CONFIG_UIO=m
CONFIG_UIO_CIF=m
CONFIG_UIO_PDRV_GENIRQ=m
CONFIG_UIO_DMEM_GENIRQ=m
CONFIG_UIO_AEC=m
CONFIG_UIO_SERCOS3=m
CONFIG_UIO_PCI_GENERIC=m
CONFIG_UIO_NETX=m
CONFIG_UIO_PRUSS=m
CONFIG_UIO_MF624=m
CONFIG_VFIO_IOMMU_TYPE1=m
CONFIG_VFIO_VIRQFD=m
CONFIG_VFIO=m
CONFIG_VFIO_PCI=m
CONFIG_VFIO_PCI_VGA=y
CONFIG_VFIO_PCI_MMAP=y
CONFIG_VFIO_PCI_INTX=y
CONFIG_IRQ_BYPASS_MANAGER=m
CONFIG_VIRT_DRIVERS=y
CONFIG_VIRTIO=y

#
# Virtio drivers
#
CONFIG_VIRTIO_PCI=y
CONFIG_VIRTIO_PCI_LEGACY=y
CONFIG_VIRTIO_BALLOON=y
CONFIG_VIRTIO_INPUT=m
CONFIG_VIRTIO_MMIO=y
CONFIG_VIRTIO_MMIO_CMDLINE_DEVICES=y

#
# Microsoft Hyper-V guest support
#
CONFIG_HYPERV=m
CONFIG_HYPERV_UTILS=m
CONFIG_HYPERV_BALLOON=m

#
# Xen driver support
#
CONFIG_XEN_BALLOON=y
CONFIG_XEN_SELFBALLOONING=y
CONFIG_XEN_BALLOON_MEMORY_HOTPLUG=y
CONFIG_XEN_BALLOON_MEMORY_HOTPLUG_LIMIT=512
CONFIG_XEN_SCRUB_PAGES=y
CONFIG_XEN_DEV_EVTCHN=m
CONFIG_XEN_BACKEND=y
CONFIG_XENFS=m
CONFIG_XEN_COMPAT_XENFS=y
CONFIG_XEN_SYS_HYPERVISOR=y
CONFIG_XEN_XENBUS_FRONTEND=y
CONFIG_XEN_GNTDEV=m
CONFIG_XEN_GRANT_DEV_ALLOC=m
CONFIG_SWIOTLB_XEN=y
CONFIG_XEN_TMEM=m
CONFIG_XEN_PCIDEV_BACKEND=m
CONFIG_XEN_SCSI_BACKEND=m
CONFIG_XEN_PRIVCMD=m
CONFIG_XEN_ACPI_PROCESSOR=y
CONFIG_XEN_MCE_LOG=y
CONFIG_XEN_HAVE_PVMMU=y
CONFIG_XEN_EFI=y
CONFIG_XEN_AUTO_XLATE=y
CONFIG_XEN_ACPI=y
CONFIG_XEN_SYMS=y
CONFIG_XEN_HAVE_VPMU=y
CONFIG_STAGING=y
CONFIG_SLICOSS=m
CONFIG_PRISM2_USB=m
CONFIG_COMEDI=m
# CONFIG_COMEDI_DEBUG is not set
CONFIG_COMEDI_DEFAULT_BUF_SIZE_KB=2048
CONFIG_COMEDI_DEFAULT_BUF_MAXSIZE_KB=20480
CONFIG_COMEDI_MISC_DRIVERS=y
CONFIG_COMEDI_BOND=m
CONFIG_COMEDI_TEST=m
CONFIG_COMEDI_PARPORT=m
CONFIG_COMEDI_SERIAL2002=m
CONFIG_COMEDI_ISA_DRIVERS=y
CONFIG_COMEDI_PCL711=m
CONFIG_COMEDI_PCL724=m
CONFIG_COMEDI_PCL726=m
CONFIG_COMEDI_PCL730=m
CONFIG_COMEDI_PCL812=m
CONFIG_COMEDI_PCL816=m
CONFIG_COMEDI_PCL818=m
CONFIG_COMEDI_PCM3724=m
CONFIG_COMEDI_AMPLC_DIO200_ISA=m
CONFIG_COMEDI_AMPLC_PC236_ISA=m
CONFIG_COMEDI_AMPLC_PC263_ISA=m
CONFIG_COMEDI_RTI800=m
CONFIG_COMEDI_RTI802=m
CONFIG_COMEDI_DAC02=m
CONFIG_COMEDI_DAS16M1=m
CONFIG_COMEDI_DAS08_ISA=m
CONFIG_COMEDI_DAS16=m
CONFIG_COMEDI_DAS800=m
CONFIG_COMEDI_DAS1800=m
CONFIG_COMEDI_DAS6402=m
CONFIG_COMEDI_DT2801=m
CONFIG_COMEDI_DT2811=m
CONFIG_COMEDI_DT2814=m
CONFIG_COMEDI_DT2815=m
CONFIG_COMEDI_DT2817=m
CONFIG_COMEDI_DT282X=m
CONFIG_COMEDI_DMM32AT=m
CONFIG_COMEDI_FL512=m
CONFIG_COMEDI_AIO_AIO12_8=m
CONFIG_COMEDI_AIO_IIRO_16=m
CONFIG_COMEDI_II_PCI20KC=m
CONFIG_COMEDI_C6XDIGIO=m
CONFIG_COMEDI_MPC624=m
CONFIG_COMEDI_ADQ12B=m
CONFIG_COMEDI_NI_AT_A2150=m
CONFIG_COMEDI_NI_AT_AO=m
CONFIG_COMEDI_NI_ATMIO=m
CONFIG_COMEDI_NI_ATMIO16D=m
CONFIG_COMEDI_NI_LABPC_ISA=m
CONFIG_COMEDI_PCMAD=m
CONFIG_COMEDI_PCMDA12=m
CONFIG_COMEDI_PCMMIO=m
CONFIG_COMEDI_PCMUIO=m
CONFIG_COMEDI_MULTIQ3=m
CONFIG_COMEDI_S526=m
CONFIG_COMEDI_PCI_DRIVERS=m
CONFIG_COMEDI_8255_PCI=m
CONFIG_COMEDI_ADDI_WATCHDOG=m
CONFIG_COMEDI_ADDI_APCI_1032=m
CONFIG_COMEDI_ADDI_APCI_1500=m
CONFIG_COMEDI_ADDI_APCI_1516=m
CONFIG_COMEDI_ADDI_APCI_1564=m
CONFIG_COMEDI_ADDI_APCI_16XX=m
CONFIG_COMEDI_ADDI_APCI_2032=m
CONFIG_COMEDI_ADDI_APCI_2200=m
CONFIG_COMEDI_ADDI_APCI_3120=m
CONFIG_COMEDI_ADDI_APCI_3501=m
CONFIG_COMEDI_ADDI_APCI_3XXX=m
CONFIG_COMEDI_ADL_PCI6208=m
CONFIG_COMEDI_ADL_PCI7X3X=m
CONFIG_COMEDI_ADL_PCI8164=m
CONFIG_COMEDI_ADL_PCI9111=m
CONFIG_COMEDI_ADL_PCI9118=m
CONFIG_COMEDI_ADV_PCI1710=m
CONFIG_COMEDI_ADV_PCI1723=m
CONFIG_COMEDI_ADV_PCI1724=m
CONFIG_COMEDI_ADV_PCI_DIO=m
CONFIG_COMEDI_AMPLC_DIO200_PCI=m
CONFIG_COMEDI_AMPLC_PC236_PCI=m
CONFIG_COMEDI_AMPLC_PC263_PCI=m
CONFIG_COMEDI_AMPLC_PCI224=m
CONFIG_COMEDI_AMPLC_PCI230=m
CONFIG_COMEDI_CONTEC_PCI_DIO=m
CONFIG_COMEDI_DAS08_PCI=m
CONFIG_COMEDI_DT3000=m
CONFIG_COMEDI_DYNA_PCI10XX=m
CONFIG_COMEDI_GSC_HPDI=m
CONFIG_COMEDI_MF6X4=m
CONFIG_COMEDI_ICP_MULTI=m
CONFIG_COMEDI_DAQBOARD2000=m
CONFIG_COMEDI_JR3_PCI=m
CONFIG_COMEDI_KE_COUNTER=m
CONFIG_COMEDI_CB_PCIDAS64=m
CONFIG_COMEDI_CB_PCIDAS=m
CONFIG_COMEDI_CB_PCIDDA=m
CONFIG_COMEDI_CB_PCIMDAS=m
CONFIG_COMEDI_CB_PCIMDDA=m
CONFIG_COMEDI_ME4000=m
CONFIG_COMEDI_ME_DAQ=m
CONFIG_COMEDI_NI_6527=m
CONFIG_COMEDI_NI_65XX=m
CONFIG_COMEDI_NI_660X=m
CONFIG_COMEDI_NI_670X=m
CONFIG_COMEDI_NI_LABPC_PCI=m
CONFIG_COMEDI_NI_PCIDIO=m
CONFIG_COMEDI_NI_PCIMIO=m
CONFIG_COMEDI_RTD520=m
CONFIG_COMEDI_S626=m
CONFIG_COMEDI_MITE=m
CONFIG_COMEDI_NI_TIOCMD=m
CONFIG_COMEDI_PCMCIA_DRIVERS=m
CONFIG_COMEDI_CB_DAS16_CS=m
CONFIG_COMEDI_DAS08_CS=m
CONFIG_COMEDI_NI_DAQ_700_CS=m
CONFIG_COMEDI_NI_DAQ_DIO24_CS=m
CONFIG_COMEDI_NI_LABPC_CS=m
CONFIG_COMEDI_NI_MIO_CS=m
CONFIG_COMEDI_QUATECH_DAQP_CS=m
CONFIG_COMEDI_USB_DRIVERS=m
CONFIG_COMEDI_DT9812=m
CONFIG_COMEDI_NI_USB6501=m
CONFIG_COMEDI_USBDUX=m
CONFIG_COMEDI_USBDUXFAST=m
CONFIG_COMEDI_USBDUXSIGMA=m
CONFIG_COMEDI_VMK80XX=m
CONFIG_COMEDI_8254=m
CONFIG_COMEDI_8255=m
CONFIG_COMEDI_8255_SA=m
CONFIG_COMEDI_KCOMEDILIB=m
CONFIG_COMEDI_AMPLC_DIO200=m
CONFIG_COMEDI_AMPLC_PC236=m
CONFIG_COMEDI_DAS08=m
CONFIG_COMEDI_ISADMA=m
CONFIG_COMEDI_NI_LABPC=m
CONFIG_COMEDI_NI_LABPC_ISADMA=m
CONFIG_COMEDI_NI_TIO=m
CONFIG_PANEL=m
CONFIG_PANEL_PARPORT=0
CONFIG_PANEL_PROFILE=5
# CONFIG_PANEL_CHANGE_MESSAGE is not set
CONFIG_RTL8192U=m
CONFIG_RTLLIB=m
CONFIG_RTLLIB_CRYPTO_CCMP=m
CONFIG_RTLLIB_CRYPTO_TKIP=m
CONFIG_RTLLIB_CRYPTO_WEP=m
CONFIG_RTL8192E=m
CONFIG_R8712U=m
CONFIG_R8188EU=m
CONFIG_88EU_AP_MODE=y
CONFIG_R8723AU=m
CONFIG_8723AU_AP_MODE=y
CONFIG_8723AU_BT_COEXIST=y
CONFIG_RTS5208=m
CONFIG_VT6655=m
CONFIG_VT6656=m

#
# IIO staging drivers
#

#
# Accelerometers
#
CONFIG_ADIS16201=m
CONFIG_ADIS16203=m
CONFIG_ADIS16204=m
CONFIG_ADIS16209=m
CONFIG_ADIS16220=m
CONFIG_ADIS16240=m
CONFIG_LIS3L02DQ=m
CONFIG_SCA3000=m

#
# Analog to digital converters
#
CONFIG_AD7606=m
CONFIG_AD7606_IFACE_PARALLEL=m
CONFIG_AD7606_IFACE_SPI=m
CONFIG_AD7780=m
CONFIG_AD7816=m
CONFIG_AD7192=m
CONFIG_AD7280=m

#
# Analog digital bi-direction converters
#
CONFIG_ADT7316=m
CONFIG_ADT7316_SPI=m
CONFIG_ADT7316_I2C=m

#
# Capacitance to digital converters
#
CONFIG_AD7150=m
CONFIG_AD7152=m
CONFIG_AD7746=m

#
# Direct Digital Synthesis
#
CONFIG_AD9832=m
CONFIG_AD9834=m

#
# Digital gyroscope sensors
#
CONFIG_ADIS16060=m

#
# Network Analyzer, Impedance Converters
#
CONFIG_AD5933=m

#
# Light sensors
#
CONFIG_SENSORS_ISL29018=m
CONFIG_SENSORS_ISL29028=m
CONFIG_TSL2583=m
CONFIG_TSL2x7x=m

#
# Magnetometer sensors
#
CONFIG_SENSORS_HMC5843=m
CONFIG_SENSORS_HMC5843_I2C=m
CONFIG_SENSORS_HMC5843_SPI=m

#
# Active energy metering IC
#
CONFIG_ADE7753=m
CONFIG_ADE7754=m
CONFIG_ADE7758=m
CONFIG_ADE7759=m
CONFIG_ADE7854=m
CONFIG_ADE7854_I2C=m
CONFIG_ADE7854_SPI=m

#
# Resolver to digital converters
#
CONFIG_AD2S90=m
CONFIG_AD2S1200=m
CONFIG_AD2S1210=m

#
# Triggers - standalone
#
CONFIG_IIO_PERIODIC_RTC_TRIGGER=m
CONFIG_IIO_SIMPLE_DUMMY=m
# CONFIG_IIO_SIMPLE_DUMMY_EVENTS is not set
# CONFIG_IIO_SIMPLE_DUMMY_BUFFER is not set
CONFIG_FB_SM750=m
CONFIG_FB_XGI=m

#
# Speakup console speech
#
CONFIG_SPEAKUP=m
CONFIG_SPEAKUP_SYNTH_ACNTSA=m
CONFIG_SPEAKUP_SYNTH_APOLLO=m
CONFIG_SPEAKUP_SYNTH_AUDPTR=m
CONFIG_SPEAKUP_SYNTH_BNS=m
CONFIG_SPEAKUP_SYNTH_DECTLK=m
CONFIG_SPEAKUP_SYNTH_DECEXT=m
CONFIG_SPEAKUP_SYNTH_LTLK=m
CONFIG_SPEAKUP_SYNTH_SOFT=m
CONFIG_SPEAKUP_SYNTH_SPKOUT=m
CONFIG_SPEAKUP_SYNTH_TXPRT=m
CONFIG_SPEAKUP_SYNTH_DUMMY=m
CONFIG_TOUCHSCREEN_SYNAPTICS_I2C_RMI4=m
CONFIG_STAGING_MEDIA=y
CONFIG_I2C_BCM2048=m
CONFIG_DVB_CXD2099=m
CONFIG_DVB_MN88472=m
CONFIG_DVB_MN88473=m
CONFIG_LIRC_STAGING=y
CONFIG_LIRC_BT829=m
CONFIG_LIRC_IMON=m
CONFIG_LIRC_PARALLEL=m
CONFIG_LIRC_SASEM=m
CONFIG_LIRC_SERIAL=m
CONFIG_LIRC_SERIAL_TRANSMITTER=y
CONFIG_LIRC_SIR=m
CONFIG_LIRC_ZILOG=m
CONFIG_STAGING_RDMA=m
CONFIG_INFINIBAND_AMSO1100=m
# CONFIG_INFINIBAND_AMSO1100_DEBUG is not set
CONFIG_INFINIBAND_HFI1=m
# CONFIG_HFI1_DEBUG_SDMA_ORDER is not set
CONFIG_HFI1_VERBS_31BIT_PSN=y
# CONFIG_SDMA_VERBOSITY is not set
# CONFIG_PRESCAN_RXQ is not set
CONFIG_INFINIBAND_IPATH=m

#
# Android
#
CONFIG_WIMAX_GDM72XX=m
CONFIG_WIMAX_GDM72XX_QOS=y
CONFIG_WIMAX_GDM72XX_K_MODE=y
CONFIG_WIMAX_GDM72XX_WIMAX2=y
CONFIG_WIMAX_GDM72XX_USB=y
# CONFIG_WIMAX_GDM72XX_SDIO is not set
CONFIG_WIMAX_GDM72XX_USB_PM=y
CONFIG_LTE_GDM724X=m
CONFIG_FIREWIRE_SERIAL=m
CONFIG_FWTTY_MAX_TOTAL_PORTS=64
CONFIG_FWTTY_MAX_CARD_PORTS=32
CONFIG_MTD_SPINAND_MT29F=m
CONFIG_MTD_SPINAND_ONDIEECC=y
# CONFIG_LUSTRE_FS is not set
CONFIG_DGNC=m
CONFIG_DGAP=m
CONFIG_GS_FPGABOOT=m
CONFIG_CRYPTO_SKEIN=y
CONFIG_UNISYSSPAR=y
CONFIG_UNISYS_VISORBUS=m
CONFIG_UNISYS_VISORNIC=m
CONFIG_UNISYS_VISORINPUT=m
CONFIG_UNISYS_VISORHBA=m
CONFIG_FB_TFT=m
CONFIG_FB_TFT_AGM1264K_FL=m
CONFIG_FB_TFT_BD663474=m
CONFIG_FB_TFT_HX8340BN=m
CONFIG_FB_TFT_HX8347D=m
CONFIG_FB_TFT_HX8353D=m
CONFIG_FB_TFT_HX8357D=m
CONFIG_FB_TFT_ILI9163=m
CONFIG_FB_TFT_ILI9320=m
CONFIG_FB_TFT_ILI9325=m
CONFIG_FB_TFT_ILI9340=m
CONFIG_FB_TFT_ILI9341=m
CONFIG_FB_TFT_ILI9481=m
CONFIG_FB_TFT_ILI9486=m
CONFIG_FB_TFT_PCD8544=m
CONFIG_FB_TFT_RA8875=m
CONFIG_FB_TFT_S6D02A1=m
CONFIG_FB_TFT_S6D1121=m
CONFIG_FB_TFT_SSD1289=m
CONFIG_FB_TFT_SSD1306=m
CONFIG_FB_TFT_SSD1331=m
CONFIG_FB_TFT_SSD1351=m
CONFIG_FB_TFT_ST7735R=m
CONFIG_FB_TFT_ST7789V=m
CONFIG_FB_TFT_TINYLCD=m
CONFIG_FB_TFT_TLS8204=m
CONFIG_FB_TFT_UC1611=m
CONFIG_FB_TFT_UC1701=m
CONFIG_FB_TFT_UPD161704=m
CONFIG_FB_TFT_WATTEROTT=m
CONFIG_FB_FLEX=m
CONFIG_FB_TFT_FBTFT_DEVICE=m
# CONFIG_WILC1000_DRIVER is not set
CONFIG_MOST=m
CONFIG_MOSTCORE=m
CONFIG_AIM_CDEV=m
CONFIG_AIM_NETWORK=m
CONFIG_AIM_SOUND=m
CONFIG_AIM_V4L2=m
CONFIG_HDM_DIM2=m
CONFIG_HDM_I2C=m
CONFIG_HDM_USB=m
CONFIG_X86_PLATFORM_DEVICES=y
CONFIG_ACER_WMI=m
CONFIG_ACERHDF=m
CONFIG_ALIENWARE_WMI=m
CONFIG_ASUS_LAPTOP=m
CONFIG_DELL_LAPTOP=m
CONFIG_DELL_WMI=m
CONFIG_DELL_WMI_AIO=m
CONFIG_DELL_SMO8800=m
CONFIG_DELL_RBTN=m
CONFIG_FUJITSU_LAPTOP=m
# CONFIG_FUJITSU_LAPTOP_DEBUG is not set
CONFIG_FUJITSU_TABLET=m
CONFIG_AMILO_RFKILL=m
CONFIG_HP_ACCEL=m
CONFIG_HP_WIRELESS=m
CONFIG_HP_WMI=m
CONFIG_MSI_LAPTOP=m
CONFIG_PANASONIC_LAPTOP=m
CONFIG_COMPAL_LAPTOP=m
CONFIG_SONY_LAPTOP=m
CONFIG_SONYPI_COMPAT=y
CONFIG_IDEAPAD_LAPTOP=m
CONFIG_THINKPAD_ACPI=m
CONFIG_THINKPAD_ACPI_ALSA_SUPPORT=y
CONFIG_THINKPAD_ACPI_DEBUGFACILITIES=y
# CONFIG_THINKPAD_ACPI_DEBUG is not set
# CONFIG_THINKPAD_ACPI_UNSAFE_LEDS is not set
CONFIG_THINKPAD_ACPI_VIDEO=y
CONFIG_THINKPAD_ACPI_HOTKEY_POLL=y
CONFIG_SENSORS_HDAPS=m
CONFIG_INTEL_MENLOW=m
CONFIG_EEEPC_LAPTOP=m
CONFIG_ASUS_WMI=m
CONFIG_ASUS_NB_WMI=m
CONFIG_EEEPC_WMI=m
CONFIG_ACPI_WMI=m
CONFIG_MSI_WMI=m
CONFIG_TOPSTAR_LAPTOP=m
CONFIG_ACPI_TOSHIBA=m
CONFIG_TOSHIBA_BT_RFKILL=m
CONFIG_TOSHIBA_HAPS=m
CONFIG_TOSHIBA_WMI=m
CONFIG_ACPI_CMPC=m
CONFIG_INTEL_IPS=m
CONFIG_IBM_RTL=m
CONFIG_SAMSUNG_LAPTOP=m
CONFIG_MXM_WMI=m
CONFIG_INTEL_OAKTRAIL=m
CONFIG_SAMSUNG_Q10=m
CONFIG_APPLE_GMUX=m
CONFIG_INTEL_RST=m
CONFIG_INTEL_SMARTCONNECT=m
CONFIG_PVPANIC=m
CONFIG_INTEL_PMC_IPC=m
CONFIG_SURFACE_PRO3_BUTTON=m
CONFIG_CHROME_PLATFORMS=y
CONFIG_CHROMEOS_LAPTOP=m
CONFIG_CHROMEOS_PSTORE=m
CONFIG_CROS_EC_CHARDEV=m
CONFIG_CROS_EC_LPC=m
CONFIG_CROS_EC_PROTO=y
CONFIG_CLKDEV_LOOKUP=y
CONFIG_HAVE_CLK_PREPARE=y
CONFIG_COMMON_CLK=y

#
# Common Clock Framework
#
CONFIG_COMMON_CLK_WM831X=m
CONFIG_COMMON_CLK_SI5351=m
CONFIG_COMMON_CLK_S2MPS11=m
CONFIG_CLK_TWL6040=m
CONFIG_COMMON_CLK_PALMAS=m
CONFIG_COMMON_CLK_PWM=m
# CONFIG_COMMON_CLK_PXA is not set
CONFIG_COMMON_CLK_CDCE706=m

#
# Hardware Spinlock drivers
#

#
# Clock Source drivers
#
CONFIG_CLKEVT_I8253=y
CONFIG_I8253_LOCK=y
CONFIG_CLKBLD_I8253=y
# CONFIG_ATMEL_PIT is not set
# CONFIG_SH_TIMER_CMT is not set
# CONFIG_SH_TIMER_MTU2 is not set
# CONFIG_SH_TIMER_TMU is not set
# CONFIG_EM_TIMER_STI is not set
CONFIG_MAILBOX=y
CONFIG_PCC=y
CONFIG_ALTERA_MBOX=m
CONFIG_IOMMU_API=y
CONFIG_IOMMU_SUPPORT=y

#
# Generic IOMMU Pagetable Support
#
CONFIG_IOMMU_IOVA=y
CONFIG_AMD_IOMMU=y
CONFIG_AMD_IOMMU_STATS=y
CONFIG_AMD_IOMMU_V2=m
CONFIG_DMAR_TABLE=y
CONFIG_INTEL_IOMMU=y
CONFIG_INTEL_IOMMU_SVM=y
# CONFIG_INTEL_IOMMU_DEFAULT_ON is not set
CONFIG_INTEL_IOMMU_FLOPPY_WA=y
CONFIG_IRQ_REMAP=y

#
# Remoteproc drivers
#
CONFIG_REMOTEPROC=m
CONFIG_STE_MODEM_RPROC=m

#
# Rpmsg drivers
#

#
# SOC (System On Chip) specific Drivers
#
# CONFIG_SUNXI_SRAM is not set
CONFIG_SOC_TI=y
CONFIG_PM_DEVFREQ=y

#
# DEVFREQ Governors
#
CONFIG_DEVFREQ_GOV_SIMPLE_ONDEMAND=y
CONFIG_DEVFREQ_GOV_PERFORMANCE=y
CONFIG_DEVFREQ_GOV_POWERSAVE=y
CONFIG_DEVFREQ_GOV_USERSPACE=y

#
# DEVFREQ Drivers
#
CONFIG_PM_DEVFREQ_EVENT=y
CONFIG_EXTCON=y

#
# Extcon Device Drivers
#
CONFIG_EXTCON_ADC_JACK=m
CONFIG_EXTCON_ARIZONA=m
CONFIG_EXTCON_AXP288=m
CONFIG_EXTCON_GPIO=m
CONFIG_EXTCON_MAX14577=m
CONFIG_EXTCON_MAX77693=m
CONFIG_EXTCON_MAX77843=m
CONFIG_EXTCON_MAX8997=m
CONFIG_EXTCON_PALMAS=m
CONFIG_EXTCON_RT8973A=m
CONFIG_EXTCON_SM5502=m
CONFIG_EXTCON_USB_GPIO=m
CONFIG_MEMORY=y
CONFIG_IIO=m
CONFIG_IIO_BUFFER=y
CONFIG_IIO_BUFFER_CB=m
CONFIG_IIO_KFIFO_BUF=m
CONFIG_IIO_TRIGGERED_BUFFER=m
CONFIG_IIO_TRIGGER=y
CONFIG_IIO_CONSUMERS_PER_TRIGGER=2
CONFIG_IIO_TRIGGERED_EVENT=m

#
# Accelerometers
#
CONFIG_BMA180=m
CONFIG_BMC150_ACCEL=m
CONFIG_BMC150_ACCEL_I2C=m
CONFIG_BMC150_ACCEL_SPI=m
CONFIG_HID_SENSOR_ACCEL_3D=m
CONFIG_IIO_ST_ACCEL_3AXIS=m
CONFIG_IIO_ST_ACCEL_I2C_3AXIS=m
CONFIG_IIO_ST_ACCEL_SPI_3AXIS=m
CONFIG_KXSD9=m
CONFIG_KXCJK1013=m
CONFIG_MMA8452=m
CONFIG_MMA9551_CORE=m
CONFIG_MMA9551=m
CONFIG_MMA9553=m
CONFIG_MXC4005=m
CONFIG_STK8312=m
CONFIG_STK8BA50=m

#
# Analog to digital converters
#
CONFIG_AD_SIGMA_DELTA=m
CONFIG_AD7266=m
CONFIG_AD7291=m
CONFIG_AD7298=m
CONFIG_AD7476=m
CONFIG_AD7791=m
CONFIG_AD7793=m
CONFIG_AD7887=m
CONFIG_AD7923=m
CONFIG_AD799X=m
CONFIG_AXP288_ADC=m
CONFIG_CC10001_ADC=m
CONFIG_DA9150_GPADC=m
CONFIG_HI8435=m
CONFIG_LP8788_ADC=m
CONFIG_MAX1027=m
CONFIG_MAX1363=m
CONFIG_MCP320X=m
CONFIG_MCP3422=m
CONFIG_MEN_Z188_ADC=m
CONFIG_NAU7802=m
CONFIG_QCOM_SPMI_IADC=m
CONFIG_QCOM_SPMI_VADC=m
CONFIG_TI_ADC081C=m
CONFIG_TI_ADC128S052=m
CONFIG_TI_AM335X_ADC=m
CONFIG_TWL4030_MADC=m
CONFIG_TWL6030_GPADC=m
CONFIG_VIPERBOARD_ADC=m

#
# Amplifiers
#
CONFIG_AD8366=m

#
# Chemical Sensors
#
CONFIG_VZ89X=m

#
# Hid Sensor IIO Common
#
CONFIG_HID_SENSOR_IIO_COMMON=m
CONFIG_HID_SENSOR_IIO_TRIGGER=m
CONFIG_IIO_MS_SENSORS_I2C=m

#
# SSP Sensor Common
#
CONFIG_IIO_SSP_SENSORS_COMMONS=m
CONFIG_IIO_SSP_SENSORHUB=m
CONFIG_IIO_ST_SENSORS_I2C=m
CONFIG_IIO_ST_SENSORS_SPI=m
CONFIG_IIO_ST_SENSORS_CORE=m

#
# Digital to analog converters
#
CONFIG_AD5064=m
CONFIG_AD5360=m
CONFIG_AD5380=m
CONFIG_AD5421=m
CONFIG_AD5446=m
CONFIG_AD5449=m
CONFIG_AD5504=m
CONFIG_AD5624R_SPI=m
CONFIG_AD5686=m
CONFIG_AD5755=m
CONFIG_AD5764=m
CONFIG_AD5791=m
CONFIG_AD7303=m
CONFIG_M62332=m
CONFIG_MAX517=m
CONFIG_MCP4725=m
CONFIG_MCP4922=m

#
# Frequency Synthesizers DDS/PLL
#

#
# Clock Generator/Distribution
#
CONFIG_AD9523=m

#
# Phase-Locked Loop (PLL) frequency synthesizers
#
CONFIG_ADF4350=m

#
# Digital gyroscope sensors
#
CONFIG_ADIS16080=m
CONFIG_ADIS16130=m
CONFIG_ADIS16136=m
CONFIG_ADIS16260=m
CONFIG_ADXRS450=m
CONFIG_BMG160=m
CONFIG_BMG160_I2C=m
CONFIG_BMG160_SPI=m
CONFIG_HID_SENSOR_GYRO_3D=m
CONFIG_IIO_ST_GYRO_3AXIS=m
CONFIG_IIO_ST_GYRO_I2C_3AXIS=m
CONFIG_IIO_ST_GYRO_SPI_3AXIS=m
CONFIG_ITG3200=m

#
# Humidity sensors
#
CONFIG_DHT11=m
CONFIG_HDC100X=m
CONFIG_HTU21=m
CONFIG_SI7005=m
CONFIG_SI7020=m

#
# Inertial measurement units
#
CONFIG_ADIS16400=m
CONFIG_ADIS16480=m
CONFIG_KMX61=m
CONFIG_INV_MPU6050_IIO=m
CONFIG_IIO_ADIS_LIB=m
CONFIG_IIO_ADIS_LIB_BUFFER=y

#
# Light sensors
#
CONFIG_ACPI_ALS=m
CONFIG_ADJD_S311=m
CONFIG_AL3320A=m
CONFIG_APDS9300=m
CONFIG_APDS9960=m
CONFIG_BH1750=m
CONFIG_CM32181=m
CONFIG_CM3232=m
CONFIG_CM3323=m
CONFIG_CM36651=m
CONFIG_GP2AP020A00F=m
CONFIG_ISL29125=m
CONFIG_HID_SENSOR_ALS=m
CONFIG_HID_SENSOR_PROX=m
CONFIG_JSA1212=m
CONFIG_RPR0521=m
CONFIG_SENSORS_LM3533=m
CONFIG_LTR501=m
CONFIG_OPT3001=m
CONFIG_PA12203001=m
CONFIG_STK3310=m
CONFIG_TCS3414=m
CONFIG_TCS3472=m
CONFIG_SENSORS_TSL2563=m
CONFIG_TSL4531=m
CONFIG_US5182D=m
CONFIG_VCNL4000=m

#
# Magnetometer sensors
#
CONFIG_AK8975=m
CONFIG_AK09911=m
CONFIG_BMC150_MAGN=m
CONFIG_MAG3110=m
CONFIG_HID_SENSOR_MAGNETOMETER_3D=m
CONFIG_MMC35240=m
CONFIG_IIO_ST_MAGN_3AXIS=m
CONFIG_IIO_ST_MAGN_I2C_3AXIS=m
CONFIG_IIO_ST_MAGN_SPI_3AXIS=m

#
# Inclinometer sensors
#
CONFIG_HID_SENSOR_INCLINOMETER_3D=m
CONFIG_HID_SENSOR_DEVICE_ROTATION=m

#
# Triggers - standalone
#
CONFIG_IIO_INTERRUPT_TRIGGER=m
CONFIG_IIO_SYSFS_TRIGGER=m

#
# Digital potentiometers
#
CONFIG_MCP4531=m

#
# Pressure sensors
#
CONFIG_BMP280=m
CONFIG_HID_SENSOR_PRESS=m
CONFIG_MPL115=m
CONFIG_MPL3115=m
CONFIG_MS5611=m
CONFIG_MS5611_I2C=m
CONFIG_MS5611_SPI=m
CONFIG_MS5637=m
CONFIG_IIO_ST_PRESS=m
CONFIG_IIO_ST_PRESS_I2C=m
CONFIG_IIO_ST_PRESS_SPI=m
CONFIG_T5403=m

#
# Lightning sensors
#
CONFIG_AS3935=m

#
# Proximity sensors
#
CONFIG_LIDAR_LITE_V2=m
CONFIG_SX9500=m

#
# Temperature sensors
#
CONFIG_MLX90614=m
CONFIG_TMP006=m
CONFIG_TSYS01=m
CONFIG_TSYS02D=m
CONFIG_NTB=m
CONFIG_NTB_INTEL=m
CONFIG_NTB_PINGPONG=m
CONFIG_NTB_TOOL=m
CONFIG_NTB_TRANSPORT=m
CONFIG_VME_BUS=y

#
# VME Bridge Drivers
#
CONFIG_VME_CA91CX42=m
CONFIG_VME_TSI148=m

#
# VME Board Drivers
#
CONFIG_VMIVME_7805=m

#
# VME Device Drivers
#
CONFIG_VME_USER=m
CONFIG_VME_PIO2=m
CONFIG_PWM=y
CONFIG_PWM_SYSFS=y
CONFIG_PWM_CRC=y
CONFIG_PWM_LP3943=m
CONFIG_PWM_LPSS=m
CONFIG_PWM_LPSS_PCI=m
CONFIG_PWM_LPSS_PLATFORM=m
CONFIG_PWM_PCA9685=m
CONFIG_PWM_TWL=m
CONFIG_PWM_TWL_LED=m
CONFIG_IPACK_BUS=m
CONFIG_BOARD_TPCI200=m
CONFIG_SERIAL_IPOCTAL=m
CONFIG_RESET_CONTROLLER=y
CONFIG_FMC=m
CONFIG_FMC_FAKEDEV=m
CONFIG_FMC_TRIVIAL=m
CONFIG_FMC_WRITE_EEPROM=m
CONFIG_FMC_CHARDEV=m

#
# PHY Subsystem
#
CONFIG_GENERIC_PHY=y
CONFIG_PHY_PXA_28NM_HSIC=m
CONFIG_PHY_PXA_28NM_USB2=m
CONFIG_BCM_KONA_USB2_PHY=m
CONFIG_PHY_SAMSUNG_USB2=m
# CONFIG_PHY_EXYNOS4210_USB2 is not set
# CONFIG_PHY_EXYNOS4X12_USB2 is not set
# CONFIG_PHY_EXYNOS5250_USB2 is not set
CONFIG_PHY_TUSB1210=m
CONFIG_POWERCAP=y
CONFIG_INTEL_RAPL=m
CONFIG_MCB=m
CONFIG_MCB_PCI=m

#
# Performance monitor support
#
CONFIG_RAS=y
CONFIG_AMD_MCE_INJ=m
CONFIG_THUNDERBOLT=m

#
# Android
#
# CONFIG_ANDROID is not set
CONFIG_LIBNVDIMM=y
CONFIG_BLK_DEV_PMEM=m
CONFIG_ND_BLK=m
CONFIG_ND_CLAIM=y
CONFIG_ND_BTT=m
CONFIG_BTT=y
CONFIG_ND_PFN=m
CONFIG_NVDIMM_PFN=y
CONFIG_NVMEM=m
CONFIG_STM=m
CONFIG_STM_DUMMY=m
CONFIG_STM_SOURCE_CONSOLE=m
CONFIG_INTEL_TH=m
CONFIG_INTEL_TH_PCI=m
CONFIG_INTEL_TH_GTH=m
CONFIG_INTEL_TH_STH=m
CONFIG_INTEL_TH_MSU=m
CONFIG_INTEL_TH_PTI=m
# CONFIG_INTEL_TH_DEBUG is not set

#
# FPGA Configuration Support
#
CONFIG_FPGA=m
CONFIG_FPGA_MGR_ZYNQ_FPGA=m

#
# Firmware Drivers
#
CONFIG_EDD=y
CONFIG_EDD_OFF=y
CONFIG_FIRMWARE_MEMMAP=y
CONFIG_DELL_RBU=m
CONFIG_DCDBAS=m
CONFIG_DMIID=y
CONFIG_DMI_SYSFS=m
CONFIG_DMI_SCAN_MACHINE_NON_EFI_FALLBACK=y
CONFIG_ISCSI_IBFT_FIND=y
CONFIG_ISCSI_IBFT=m
# CONFIG_GOOGLE_FIRMWARE is not set

#
# EFI (Extensible Firmware Interface) Support
#
CONFIG_EFI_VARS=y
CONFIG_EFI_ESRT=y
CONFIG_EFI_VARS_PSTORE=m
# CONFIG_EFI_VARS_PSTORE_DEFAULT_DISABLE is not set
CONFIG_EFI_RUNTIME_MAP=y
# CONFIG_EFI_FAKE_MEMMAP is not set
CONFIG_EFI_RUNTIME_WRAPPERS=y
CONFIG_UEFI_CPER=y

#
# File systems
#
CONFIG_DCACHE_WORD_ACCESS=y
# CONFIG_EXT2_FS is not set
# CONFIG_EXT3_FS is not set
CONFIG_EXT4_FS=y
CONFIG_EXT4_USE_FOR_EXT2=y
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
CONFIG_EXT4_ENCRYPTION=m
CONFIG_EXT4_FS_ENCRYPTION=y
# CONFIG_EXT4_DEBUG is not set
CONFIG_JBD2=y
# CONFIG_JBD2_DEBUG is not set
CONFIG_FS_MBCACHE=y
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
CONFIG_JFS_STATISTICS=y
CONFIG_XFS_FS=m
CONFIG_XFS_QUOTA=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_RT=y
# CONFIG_XFS_WARN is not set
# CONFIG_XFS_DEBUG is not set
CONFIG_GFS2_FS=m
CONFIG_GFS2_FS_LOCKING_DLM=y
CONFIG_OCFS2_FS=m
CONFIG_OCFS2_FS_O2CB=m
CONFIG_OCFS2_FS_USERSPACE_CLUSTER=m
CONFIG_OCFS2_FS_STATS=y
CONFIG_OCFS2_DEBUG_MASKLOG=y
# CONFIG_OCFS2_DEBUG_FS is not set
CONFIG_BTRFS_FS=m
CONFIG_BTRFS_FS_POSIX_ACL=y
# CONFIG_BTRFS_FS_CHECK_INTEGRITY is not set
# CONFIG_BTRFS_FS_RUN_SANITY_TESTS is not set
# CONFIG_BTRFS_DEBUG is not set
# CONFIG_BTRFS_ASSERT is not set
CONFIG_NILFS2_FS=m
CONFIG_F2FS_FS=m
CONFIG_F2FS_STAT_FS=y
CONFIG_F2FS_FS_XATTR=y
CONFIG_F2FS_FS_POSIX_ACL=y
CONFIG_F2FS_FS_SECURITY=y
# CONFIG_F2FS_CHECK_FS is not set
CONFIG_F2FS_FS_ENCRYPTION=y
# CONFIG_F2FS_IO_TRACE is not set
CONFIG_FS_DAX=y
CONFIG_FS_POSIX_ACL=y
CONFIG_EXPORTFS=y
CONFIG_FILE_LOCKING=y
CONFIG_FSNOTIFY=y
CONFIG_DNOTIFY=y
CONFIG_INOTIFY_USER=y
CONFIG_FANOTIFY=y
CONFIG_FANOTIFY_ACCESS_PERMISSIONS=y
CONFIG_QUOTA=y
CONFIG_QUOTA_NETLINK_INTERFACE=y
# CONFIG_PRINT_QUOTA_WARNING is not set
# CONFIG_QUOTA_DEBUG is not set
CONFIG_QUOTA_TREE=m
CONFIG_QFMT_V1=m
CONFIG_QFMT_V2=m
CONFIG_QUOTACTL=y
CONFIG_QUOTACTL_COMPAT=y
CONFIG_AUTOFS4_FS=m
CONFIG_FUSE_FS=y
CONFIG_CUSE=m
CONFIG_OVERLAY_FS=m

#
# Caches
#
CONFIG_FSCACHE=m
CONFIG_FSCACHE_STATS=y
# CONFIG_FSCACHE_HISTOGRAM is not set
# CONFIG_FSCACHE_DEBUG is not set
# CONFIG_FSCACHE_OBJECT_LIST is not set
CONFIG_CACHEFILES=m
# CONFIG_CACHEFILES_DEBUG is not set
# CONFIG_CACHEFILES_HISTOGRAM is not set

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=m
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=m
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=y
CONFIG_MSDOS_FS=m
CONFIG_VFAT_FS=y
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
# CONFIG_NTFS_RW is not set

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_VMCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_PROC_PAGE_MONITOR=y
CONFIG_PROC_CHILDREN=y
CONFIG_KERNFS=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_TMPFS_POSIX_ACL=y
CONFIG_TMPFS_XATTR=y
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
CONFIG_CONFIGFS_FS=m
CONFIG_EFIVAR_FS=y
CONFIG_MISC_FILESYSTEMS=y
CONFIG_ADFS_FS=m
# CONFIG_ADFS_FS_RW is not set
CONFIG_AFFS_FS=m
CONFIG_ECRYPT_FS=y
CONFIG_ECRYPT_FS_MESSAGING=y
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_HFSPLUS_FS_POSIX_ACL=y
CONFIG_BEFS_FS=m
# CONFIG_BEFS_DEBUG is not set
CONFIG_BFS_FS=m
CONFIG_EFS_FS=m
CONFIG_JFFS2_FS=m
CONFIG_JFFS2_FS_DEBUG=0
CONFIG_JFFS2_FS_WRITEBUFFER=y
# CONFIG_JFFS2_FS_WBUF_VERIFY is not set
# CONFIG_JFFS2_SUMMARY is not set
CONFIG_JFFS2_FS_XATTR=y
CONFIG_JFFS2_FS_POSIX_ACL=y
CONFIG_JFFS2_FS_SECURITY=y
CONFIG_JFFS2_COMPRESSION_OPTIONS=y
CONFIG_JFFS2_ZLIB=y
CONFIG_JFFS2_LZO=y
CONFIG_JFFS2_RTIME=y
# CONFIG_JFFS2_RUBIN is not set
# CONFIG_JFFS2_CMODE_NONE is not set
# CONFIG_JFFS2_CMODE_PRIORITY is not set
# CONFIG_JFFS2_CMODE_SIZE is not set
CONFIG_JFFS2_CMODE_FAVOURLZO=y
CONFIG_UBIFS_FS=m
# CONFIG_UBIFS_FS_ADVANCED_COMPR is not set
CONFIG_UBIFS_FS_LZO=y
CONFIG_UBIFS_FS_ZLIB=y
CONFIG_UBIFS_ATIME_SUPPORT=y
# CONFIG_LOGFS is not set
CONFIG_CRAMFS=m
CONFIG_SQUASHFS=m
# CONFIG_SQUASHFS_FILE_CACHE is not set
CONFIG_SQUASHFS_FILE_DIRECT=y
# CONFIG_SQUASHFS_DECOMP_SINGLE is not set
# CONFIG_SQUASHFS_DECOMP_MULTI is not set
CONFIG_SQUASHFS_DECOMP_MULTI_PERCPU=y
CONFIG_SQUASHFS_XATTR=y
CONFIG_SQUASHFS_ZLIB=y
CONFIG_SQUASHFS_LZ4=y
CONFIG_SQUASHFS_LZO=y
CONFIG_SQUASHFS_XZ=y
# CONFIG_SQUASHFS_4K_DEVBLK_SIZE is not set
# CONFIG_SQUASHFS_EMBEDDED is not set
CONFIG_SQUASHFS_FRAGMENT_CACHE_SIZE=3
CONFIG_VXFS_FS=m
CONFIG_MINIX_FS=m
CONFIG_OMFS_FS=m
CONFIG_HPFS_FS=m
CONFIG_QNX4FS_FS=m
CONFIG_QNX6FS_FS=m
# CONFIG_QNX6FS_DEBUG is not set
CONFIG_ROMFS_FS=m
CONFIG_ROMFS_BACKED_BY_BLOCK=y
# CONFIG_ROMFS_BACKED_BY_MTD is not set
# CONFIG_ROMFS_BACKED_BY_BOTH is not set
CONFIG_ROMFS_ON_BLOCK=y
CONFIG_PSTORE=y
# CONFIG_PSTORE_CONSOLE is not set
# CONFIG_PSTORE_PMSG is not set
# CONFIG_PSTORE_FTRACE is not set
CONFIG_PSTORE_RAM=m
CONFIG_SYSV_FS=m
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
# CONFIG_UFS_DEBUG is not set
CONFIG_EXOFS_FS=m
# CONFIG_EXOFS_DEBUG is not set
CONFIG_ORE=m
CONFIG_NETWORK_FILESYSTEMS=y
CONFIG_NFS_FS=m
CONFIG_NFS_V2=m
CONFIG_NFS_V3=m
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=m
CONFIG_NFS_SWAP=y
CONFIG_NFS_V4_1=y
CONFIG_NFS_V4_2=y
CONFIG_PNFS_FILE_LAYOUT=m
CONFIG_PNFS_BLOCK=m
CONFIG_PNFS_OBJLAYOUT=m
CONFIG_PNFS_FLEXFILE_LAYOUT=m
CONFIG_NFS_V4_1_IMPLEMENTATION_ID_DOMAIN="kernel.org"
CONFIG_NFS_V4_1_MIGRATION=y
CONFIG_NFS_V4_SECURITY_LABEL=y
CONFIG_NFS_FSCACHE=y
# CONFIG_NFS_USE_LEGACY_DNS is not set
CONFIG_NFS_USE_KERNEL_DNS=y
CONFIG_NFS_DEBUG=y
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
CONFIG_NFSD_PNFS=y
CONFIG_NFSD_V4_SECURITY_LABEL=y
# CONFIG_NFSD_FAULT_INJECTION is not set
CONFIG_GRACE_PERIOD=m
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_SUNRPC_BACKCHANNEL=y
CONFIG_SUNRPC_SWAP=y
CONFIG_RPCSEC_GSS_KRB5=m
CONFIG_SUNRPC_DEBUG=y
CONFIG_SUNRPC_XPRT_RDMA=m
CONFIG_CEPH_FS=m
CONFIG_CEPH_FSCACHE=y
CONFIG_CEPH_FS_POSIX_ACL=y
CONFIG_CIFS=m
CONFIG_CIFS_STATS=y
# CONFIG_CIFS_STATS2 is not set
CONFIG_CIFS_WEAK_PW_HASH=y
CONFIG_CIFS_UPCALL=y
CONFIG_CIFS_XATTR=y
CONFIG_CIFS_POSIX=y
CONFIG_CIFS_ACL=y
CONFIG_CIFS_DEBUG=y
# CONFIG_CIFS_DEBUG2 is not set
CONFIG_CIFS_DFS_UPCALL=y
CONFIG_CIFS_SMB2=y
CONFIG_CIFS_SMB311=y
CONFIG_CIFS_FSCACHE=y
CONFIG_NCP_FS=m
CONFIG_NCPFS_PACKET_SIGNING=y
CONFIG_NCPFS_IOCTL_LOCKING=y
CONFIG_NCPFS_STRONG=y
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
CONFIG_AFS_FS=m
# CONFIG_AFS_DEBUG is not set
CONFIG_AFS_FSCACHE=y
CONFIG_9P_FS=m
CONFIG_9P_FSCACHE=y
CONFIG_9P_FS_POSIX_ACL=y
CONFIG_9P_FS_SECURITY=y
CONFIG_NLS=y
CONFIG_NLS_DEFAULT="utf8"
CONFIG_NLS_CODEPAGE_437=y
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=m
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=m
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
CONFIG_NLS_MAC_ROMAN=m
CONFIG_NLS_MAC_CELTIC=m
CONFIG_NLS_MAC_CENTEURO=m
CONFIG_NLS_MAC_CROATIAN=m
CONFIG_NLS_MAC_CYRILLIC=m
CONFIG_NLS_MAC_GAELIC=m
CONFIG_NLS_MAC_GREEK=m
CONFIG_NLS_MAC_ICELAND=m
CONFIG_NLS_MAC_INUIT=m
CONFIG_NLS_MAC_ROMANIAN=m
CONFIG_NLS_MAC_TURKISH=m
CONFIG_NLS_UTF8=m
CONFIG_DLM=m
# CONFIG_DLM_DEBUG is not set

#
# Kernel hacking
#
CONFIG_TRACE_IRQFLAGS_SUPPORT=y

#
# printk and dmesg options
#
CONFIG_PRINTK_TIME=y
CONFIG_MESSAGE_LOGLEVEL_DEFAULT=4
CONFIG_BOOT_PRINTK_DELAY=y
CONFIG_DYNAMIC_DEBUG=y

#
# Compile-time checks and compiler options
#
CONFIG_DEBUG_INFO=y
# CONFIG_DEBUG_INFO_REDUCED is not set
# CONFIG_DEBUG_INFO_SPLIT is not set
CONFIG_DEBUG_INFO_DWARF4=y
CONFIG_GDB_SCRIPTS=y
# CONFIG_ENABLE_WARN_DEPRECATED is not set
# CONFIG_ENABLE_MUST_CHECK is not set
CONFIG_FRAME_WARN=1024
# CONFIG_STRIP_ASM_SYMS is not set
# CONFIG_READABLE_ASM is not set
CONFIG_UNUSED_SYMBOLS=y
# CONFIG_PAGE_OWNER is not set
CONFIG_DEBUG_FS=y
# CONFIG_HEADERS_CHECK is not set
# CONFIG_DEBUG_SECTION_MISMATCH is not set
CONFIG_SECTION_MISMATCH_WARN_ONLY=y
CONFIG_ARCH_WANT_FRAME_POINTERS=y
CONFIG_FRAME_POINTER=y
# CONFIG_DEBUG_FORCE_WEAK_PER_CPU is not set
CONFIG_MAGIC_SYSRQ=y
CONFIG_MAGIC_SYSRQ_DEFAULT_ENABLE=0x1
CONFIG_DEBUG_KERNEL=y

#
# Memory Debugging
#
# CONFIG_PAGE_EXTENSION is not set
# CONFIG_DEBUG_PAGEALLOC is not set
# CONFIG_DEBUG_OBJECTS is not set
# CONFIG_SLUB_DEBUG_ON is not set
# CONFIG_SLUB_STATS is not set
CONFIG_HAVE_DEBUG_KMEMLEAK=y
# CONFIG_DEBUG_KMEMLEAK is not set
# CONFIG_DEBUG_STACK_USAGE is not set
# CONFIG_DEBUG_VM is not set
# CONFIG_DEBUG_VIRTUAL is not set
# CONFIG_DEBUG_MEMORY_INIT is not set
CONFIG_MEMORY_NOTIFIER_ERROR_INJECT=m
# CONFIG_DEBUG_PER_CPU_MAPS is not set
CONFIG_HAVE_DEBUG_STACKOVERFLOW=y
# CONFIG_DEBUG_STACKOVERFLOW is not set
CONFIG_HAVE_ARCH_KMEMCHECK=y
CONFIG_HAVE_ARCH_KASAN=y
# CONFIG_KASAN is not set
# CONFIG_DEBUG_SHIRQ is not set

#
# Debug Lockups and Hangs
#
CONFIG_LOCKUP_DETECTOR=y
CONFIG_HARDLOCKUP_DETECTOR=y
# CONFIG_BOOTPARAM_HARDLOCKUP_PANIC is not set
CONFIG_BOOTPARAM_HARDLOCKUP_PANIC_VALUE=0
# CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC is not set
CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC_VALUE=0
CONFIG_DETECT_HUNG_TASK=y
CONFIG_DEFAULT_HUNG_TASK_TIMEOUT=120
# CONFIG_BOOTPARAM_HUNG_TASK_PANIC is not set
CONFIG_BOOTPARAM_HUNG_TASK_PANIC_VALUE=0
# CONFIG_PANIC_ON_OOPS is not set
CONFIG_PANIC_ON_OOPS_VALUE=0
CONFIG_PANIC_TIMEOUT=0
CONFIG_SCHED_DEBUG=y
CONFIG_SCHED_INFO=y
CONFIG_SCHEDSTATS=y
CONFIG_SCHED_STACK_END_CHECK=y
# CONFIG_DEBUG_TIMEKEEPING is not set
CONFIG_TIMER_STATS=y
# CONFIG_DEBUG_PREEMPT is not set

#
# Lock Debugging (spinlocks, mutexes, etc...)
#
# CONFIG_DEBUG_RT_MUTEXES is not set
# CONFIG_DEBUG_SPINLOCK is not set
# CONFIG_DEBUG_MUTEXES is not set
# CONFIG_DEBUG_WW_MUTEX_SLOWPATH is not set
# CONFIG_DEBUG_LOCK_ALLOC is not set
# CONFIG_PROVE_LOCKING is not set
# CONFIG_LOCK_STAT is not set
# CONFIG_DEBUG_ATOMIC_SLEEP is not set
# CONFIG_DEBUG_LOCKING_API_SELFTESTS is not set
CONFIG_LOCK_TORTURE_TEST=m
CONFIG_STACKTRACE=y
# CONFIG_DEBUG_KOBJECT is not set
CONFIG_DEBUG_BUGVERBOSE=y
# CONFIG_DEBUG_LIST is not set
# CONFIG_DEBUG_PI_LIST is not set
# CONFIG_DEBUG_SG is not set
# CONFIG_DEBUG_NOTIFIERS is not set
# CONFIG_DEBUG_CREDENTIALS is not set

#
# RCU Debugging
#
# CONFIG_PROVE_RCU is not set
# CONFIG_SPARSE_RCU_POINTER is not set
CONFIG_TORTURE_TEST=m
# CONFIG_RCU_TORTURE_TEST is not set
CONFIG_RCU_CPU_STALL_TIMEOUT=60
# CONFIG_RCU_TRACE is not set
# CONFIG_RCU_EQS_DEBUG is not set
# CONFIG_DEBUG_BLOCK_EXT_DEVT is not set
CONFIG_NOTIFIER_ERROR_INJECTION=m
CONFIG_CPU_NOTIFIER_ERROR_INJECT=m
CONFIG_PM_NOTIFIER_ERROR_INJECT=m
# CONFIG_FAULT_INJECTION is not set
# CONFIG_LATENCYTOP is not set
CONFIG_ARCH_HAS_DEBUG_STRICT_USER_COPY_CHECKS=y
# CONFIG_DEBUG_STRICT_USER_COPY_CHECKS is not set
CONFIG_USER_STACKTRACE_SUPPORT=y
CONFIG_NOP_TRACER=y
CONFIG_HAVE_FUNCTION_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_FP_TEST=y
CONFIG_HAVE_DYNAMIC_FTRACE=y
CONFIG_HAVE_DYNAMIC_FTRACE_WITH_REGS=y
CONFIG_HAVE_FTRACE_MCOUNT_RECORD=y
CONFIG_HAVE_SYSCALL_TRACEPOINTS=y
CONFIG_HAVE_FENTRY=y
CONFIG_HAVE_C_RECORDMCOUNT=y
CONFIG_TRACER_MAX_TRACE=y
CONFIG_TRACE_CLOCK=y
CONFIG_RING_BUFFER=y
CONFIG_EVENT_TRACING=y
CONFIG_CONTEXT_SWITCH_TRACER=y
CONFIG_RING_BUFFER_ALLOW_SWAP=y
CONFIG_TRACING=y
CONFIG_GENERIC_TRACER=y
CONFIG_TRACING_SUPPORT=y
CONFIG_FTRACE=y
CONFIG_FUNCTION_TRACER=y
CONFIG_FUNCTION_GRAPH_TRACER=y
# CONFIG_IRQSOFF_TRACER is not set
# CONFIG_PREEMPT_TRACER is not set
CONFIG_SCHED_TRACER=y
CONFIG_FTRACE_SYSCALLS=y
CONFIG_TRACER_SNAPSHOT=y
# CONFIG_TRACER_SNAPSHOT_PER_CPU_SWAP is not set
CONFIG_BRANCH_PROFILE_NONE=y
# CONFIG_PROFILE_ANNOTATED_BRANCHES is not set
# CONFIG_PROFILE_ALL_BRANCHES is not set
CONFIG_STACK_TRACER=y
CONFIG_BLK_DEV_IO_TRACE=y
CONFIG_KPROBE_EVENT=y
CONFIG_UPROBE_EVENT=y
CONFIG_BPF_EVENTS=y
CONFIG_PROBE_EVENTS=y
CONFIG_DYNAMIC_FTRACE=y
CONFIG_DYNAMIC_FTRACE_WITH_REGS=y
CONFIG_FUNCTION_PROFILER=y
CONFIG_FTRACE_MCOUNT_RECORD=y
# CONFIG_FTRACE_STARTUP_TEST is not set
CONFIG_MMIOTRACE=y
# CONFIG_MMIOTRACE_TEST is not set
# CONFIG_TRACEPOINT_BENCHMARK is not set
# CONFIG_RING_BUFFER_BENCHMARK is not set
# CONFIG_RING_BUFFER_STARTUP_TEST is not set
# CONFIG_TRACE_ENUM_MAP_FILE is not set
CONFIG_TRACING_EVENTS_GPIO=y

#
# Runtime Testing
#
# CONFIG_LKDTM is not set
# CONFIG_TEST_LIST_SORT is not set
# CONFIG_KPROBES_SANITY_TEST is not set
# CONFIG_BACKTRACE_SELF_TEST is not set
CONFIG_RBTREE_TEST=m
CONFIG_INTERVAL_TREE_TEST=m
CONFIG_PERCPU_TEST=m
# CONFIG_ATOMIC64_SELFTEST is not set
CONFIG_ASYNC_RAID6_TEST=m
CONFIG_TEST_HEXDUMP=m
CONFIG_TEST_STRING_HELPERS=m
CONFIG_TEST_KSTRTOX=m
CONFIG_TEST_PRINTF=m
# CONFIG_TEST_RHASHTABLE is not set
# CONFIG_PROVIDE_OHCI1394_DMA_INIT is not set
# CONFIG_DMA_API_DEBUG is not set
CONFIG_TEST_LKM=m
CONFIG_TEST_USER_COPY=m
CONFIG_TEST_BPF=m
CONFIG_TEST_FIRMWARE=m
CONFIG_TEST_UDELAY=m
CONFIG_MEMTEST=y
CONFIG_TEST_STATIC_KEYS=m
# CONFIG_SAMPLES is not set
CONFIG_HAVE_ARCH_KGDB=y
CONFIG_KGDB=y
CONFIG_KGDB_SERIAL_CONSOLE=y
# CONFIG_KGDB_TESTS is not set
CONFIG_KGDB_LOW_LEVEL_TRAP=y
CONFIG_KGDB_KDB=y
CONFIG_KDB_DEFAULT_ENABLE=0x1
CONFIG_KDB_KEYBOARD=y
CONFIG_KDB_CONTINUE_CATASTROPHIC=0
CONFIG_STRICT_DEVMEM=y
# CONFIG_X86_VERBOSE_BOOTUP is not set
CONFIG_EARLY_PRINTK=y
CONFIG_EARLY_PRINTK_DBGP=y
CONFIG_EARLY_PRINTK_EFI=y
# CONFIG_X86_PTDUMP_CORE is not set
# CONFIG_X86_PTDUMP is not set
# CONFIG_EFI_PGT_DUMP is not set
CONFIG_DEBUG_RODATA=y
# CONFIG_DEBUG_RODATA_TEST is not set
# CONFIG_DEBUG_WX is not set
CONFIG_DEBUG_SET_MODULE_RONX=y
# CONFIG_DEBUG_NX_TEST is not set
CONFIG_DOUBLEFAULT=y
# CONFIG_DEBUG_TLBFLUSH is not set
# CONFIG_IOMMU_DEBUG is not set
# CONFIG_IOMMU_STRESS is not set
CONFIG_HAVE_MMIOTRACE_SUPPORT=y
# CONFIG_X86_DECODER_SELFTEST is not set
CONFIG_IO_DELAY_TYPE_0X80=0
CONFIG_IO_DELAY_TYPE_0XED=1
CONFIG_IO_DELAY_TYPE_UDELAY=2
CONFIG_IO_DELAY_TYPE_NONE=3
# CONFIG_IO_DELAY_0X80 is not set
CONFIG_IO_DELAY_0XED=y
# CONFIG_IO_DELAY_UDELAY is not set
# CONFIG_IO_DELAY_NONE is not set
CONFIG_DEFAULT_IO_DELAY_TYPE=1
# CONFIG_DEBUG_BOOT_PARAMS is not set
# CONFIG_CPA_DEBUG is not set
CONFIG_OPTIMIZE_INLINING=y
# CONFIG_DEBUG_ENTRY is not set
# CONFIG_DEBUG_NMI_SELFTEST is not set
# CONFIG_X86_DEBUG_STATIC_CPU_HAS is not set
CONFIG_X86_DEBUG_FPU=y
CONFIG_PUNIT_ATOM_DEBUG=m

#
# Security options
#
CONFIG_KEYS=y
CONFIG_PERSISTENT_KEYRINGS=y
CONFIG_BIG_KEYS=y
CONFIG_TRUSTED_KEYS=y
CONFIG_ENCRYPTED_KEYS=y
# CONFIG_SECURITY_DMESG_RESTRICT is not set
CONFIG_SECURITY=y
CONFIG_SECURITYFS=y
CONFIG_SECURITY_NETWORK=y
CONFIG_SECURITY_NETWORK_XFRM=y
CONFIG_SECURITY_PATH=y
CONFIG_INTEL_TXT=y
CONFIG_LSM_MMAP_MIN_ADDR=0
CONFIG_SECURITY_SELINUX=y
CONFIG_SECURITY_SELINUX_BOOTPARAM=y
CONFIG_SECURITY_SELINUX_BOOTPARAM_VALUE=0
CONFIG_SECURITY_SELINUX_DISABLE=y
CONFIG_SECURITY_SELINUX_DEVELOP=y
CONFIG_SECURITY_SELINUX_AVC_STATS=y
CONFIG_SECURITY_SELINUX_CHECKREQPROT_VALUE=1
# CONFIG_SECURITY_SELINUX_POLICYDB_VERSION_MAX is not set
CONFIG_SECURITY_SMACK=y
# CONFIG_SECURITY_SMACK_BRINGUP is not set
CONFIG_SECURITY_SMACK_NETFILTER=y
CONFIG_SECURITY_TOMOYO=y
CONFIG_SECURITY_TOMOYO_MAX_ACCEPT_ENTRY=2048
CONFIG_SECURITY_TOMOYO_MAX_AUDIT_LOG=1024
# CONFIG_SECURITY_TOMOYO_OMIT_USERSPACE_LOADER is not set
CONFIG_SECURITY_TOMOYO_POLICY_LOADER="/sbin/tomoyo-init"
CONFIG_SECURITY_TOMOYO_ACTIVATION_TRIGGER="/sbin/init"
CONFIG_SECURITY_APPARMOR=y
CONFIG_SECURITY_APPARMOR_BOOTPARAM_VALUE=1
CONFIG_SECURITY_APPARMOR_HASH=y
CONFIG_SECURITY_YAMA=y
CONFIG_INTEGRITY=y
CONFIG_INTEGRITY_SIGNATURE=y
CONFIG_INTEGRITY_ASYMMETRIC_KEYS=y
CONFIG_INTEGRITY_AUDIT=y
CONFIG_IMA=y
CONFIG_IMA_MEASURE_PCR_IDX=10
CONFIG_IMA_LSM_RULES=y
# CONFIG_IMA_TEMPLATE is not set
CONFIG_IMA_NG_TEMPLATE=y
# CONFIG_IMA_SIG_TEMPLATE is not set
CONFIG_IMA_DEFAULT_TEMPLATE="ima-ng"
CONFIG_IMA_DEFAULT_HASH_SHA1=y
# CONFIG_IMA_DEFAULT_HASH_SHA256 is not set
# CONFIG_IMA_DEFAULT_HASH_SHA512 is not set
# CONFIG_IMA_DEFAULT_HASH_WP512 is not set
CONFIG_IMA_DEFAULT_HASH="sha1"
CONFIG_IMA_APPRAISE=y
CONFIG_IMA_TRUSTED_KEYRING=y
# CONFIG_IMA_LOAD_X509 is not set
CONFIG_EVM=y
CONFIG_EVM_ATTR_FSUUID=y
CONFIG_EVM_EXTRA_SMACK_XATTRS=y
# CONFIG_DEFAULT_SECURITY_SELINUX is not set
# CONFIG_DEFAULT_SECURITY_SMACK is not set
# CONFIG_DEFAULT_SECURITY_TOMOYO is not set
CONFIG_DEFAULT_SECURITY_APPARMOR=y
# CONFIG_DEFAULT_SECURITY_DAC is not set
CONFIG_DEFAULT_SECURITY="apparmor"
CONFIG_XOR_BLOCKS=m
CONFIG_ASYNC_CORE=m
CONFIG_ASYNC_MEMCPY=m
CONFIG_ASYNC_XOR=m
CONFIG_ASYNC_PQ=m
CONFIG_ASYNC_RAID6_RECOV=m
CONFIG_CRYPTO=y

#
# Crypto core or helper
#
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_ALGAPI2=y
CONFIG_CRYPTO_AEAD=m
CONFIG_CRYPTO_AEAD2=y
CONFIG_CRYPTO_BLKCIPHER=y
CONFIG_CRYPTO_BLKCIPHER2=y
CONFIG_CRYPTO_HASH=y
CONFIG_CRYPTO_HASH2=y
CONFIG_CRYPTO_RNG=y
CONFIG_CRYPTO_RNG2=y
CONFIG_CRYPTO_RNG_DEFAULT=m
CONFIG_CRYPTO_PCOMP=m
CONFIG_CRYPTO_PCOMP2=y
CONFIG_CRYPTO_AKCIPHER2=y
CONFIG_CRYPTO_AKCIPHER=m
CONFIG_CRYPTO_RSA=m
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_MANAGER2=y
CONFIG_CRYPTO_USER=m
CONFIG_CRYPTO_MANAGER_DISABLE_TESTS=y
CONFIG_CRYPTO_GF128MUL=m
CONFIG_CRYPTO_NULL=m
CONFIG_CRYPTO_NULL2=y
CONFIG_CRYPTO_PCRYPT=m
CONFIG_CRYPTO_WORKQUEUE=y
CONFIG_CRYPTO_CRYPTD=m
CONFIG_CRYPTO_MCRYPTD=m
CONFIG_CRYPTO_AUTHENC=m
CONFIG_CRYPTO_TEST=m
CONFIG_CRYPTO_ABLK_HELPER=m
CONFIG_CRYPTO_GLUE_HELPER_X86=m

#
# Authenticated Encryption with Associated Data
#
CONFIG_CRYPTO_CCM=m
CONFIG_CRYPTO_GCM=m
CONFIG_CRYPTO_CHACHA20POLY1305=m
CONFIG_CRYPTO_SEQIV=m
CONFIG_CRYPTO_ECHAINIV=m

#
# Block modes
#
CONFIG_CRYPTO_CBC=y
CONFIG_CRYPTO_CTR=m
CONFIG_CRYPTO_CTS=m
CONFIG_CRYPTO_ECB=y
CONFIG_CRYPTO_LRW=m
CONFIG_CRYPTO_PCBC=m
CONFIG_CRYPTO_XTS=m
CONFIG_CRYPTO_KEYWRAP=m

#
# Hash modes
#
CONFIG_CRYPTO_CMAC=m
CONFIG_CRYPTO_HMAC=y
CONFIG_CRYPTO_XCBC=m
CONFIG_CRYPTO_VMAC=m

#
# Digest
#
CONFIG_CRYPTO_CRC32C=y
CONFIG_CRYPTO_CRC32C_INTEL=y
CONFIG_CRYPTO_CRC32=m
CONFIG_CRYPTO_CRC32_PCLMUL=m
CONFIG_CRYPTO_CRCT10DIF=y
CONFIG_CRYPTO_CRCT10DIF_PCLMUL=m
CONFIG_CRYPTO_GHASH=m
CONFIG_CRYPTO_POLY1305=m
CONFIG_CRYPTO_POLY1305_X86_64=m
CONFIG_CRYPTO_MD4=m
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_CRYPTO_RMD128=m
CONFIG_CRYPTO_RMD160=m
CONFIG_CRYPTO_RMD256=m
CONFIG_CRYPTO_RMD320=m
CONFIG_CRYPTO_SHA1=y
CONFIG_CRYPTO_SHA1_SSSE3=m
CONFIG_CRYPTO_SHA256_SSSE3=m
CONFIG_CRYPTO_SHA512_SSSE3=m
CONFIG_CRYPTO_SHA1_MB=m
CONFIG_CRYPTO_SHA256=y
CONFIG_CRYPTO_SHA512=y
CONFIG_CRYPTO_TGR192=m
CONFIG_CRYPTO_WP512=m
CONFIG_CRYPTO_GHASH_CLMUL_NI_INTEL=m

#
# Ciphers
#
CONFIG_CRYPTO_AES=y
CONFIG_CRYPTO_AES_X86_64=m
CONFIG_CRYPTO_AES_NI_INTEL=m
CONFIG_CRYPTO_ANUBIS=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_BLOWFISH=m
CONFIG_CRYPTO_BLOWFISH_COMMON=m
CONFIG_CRYPTO_BLOWFISH_X86_64=m
CONFIG_CRYPTO_CAMELLIA=m
CONFIG_CRYPTO_CAMELLIA_X86_64=m
CONFIG_CRYPTO_CAMELLIA_AESNI_AVX_X86_64=m
CONFIG_CRYPTO_CAMELLIA_AESNI_AVX2_X86_64=m
CONFIG_CRYPTO_CAST_COMMON=m
CONFIG_CRYPTO_CAST5=m
CONFIG_CRYPTO_CAST5_AVX_X86_64=m
CONFIG_CRYPTO_CAST6=m
CONFIG_CRYPTO_CAST6_AVX_X86_64=m
CONFIG_CRYPTO_DES=m
CONFIG_CRYPTO_DES3_EDE_X86_64=m
CONFIG_CRYPTO_FCRYPT=m
CONFIG_CRYPTO_KHAZAD=m
CONFIG_CRYPTO_SALSA20=m
CONFIG_CRYPTO_SALSA20_X86_64=m
CONFIG_CRYPTO_CHACHA20=m
CONFIG_CRYPTO_CHACHA20_X86_64=m
CONFIG_CRYPTO_SEED=m
CONFIG_CRYPTO_SERPENT=m
CONFIG_CRYPTO_SERPENT_SSE2_X86_64=m
CONFIG_CRYPTO_SERPENT_AVX_X86_64=m
CONFIG_CRYPTO_SERPENT_AVX2_X86_64=m
CONFIG_CRYPTO_TEA=m
CONFIG_CRYPTO_TWOFISH=m
CONFIG_CRYPTO_TWOFISH_COMMON=m
CONFIG_CRYPTO_TWOFISH_X86_64=m
CONFIG_CRYPTO_TWOFISH_X86_64_3WAY=m
CONFIG_CRYPTO_TWOFISH_AVX_X86_64=m

#
# Compression
#
CONFIG_CRYPTO_DEFLATE=m
CONFIG_CRYPTO_ZLIB=m
CONFIG_CRYPTO_LZO=y
CONFIG_CRYPTO_842=m
CONFIG_CRYPTO_LZ4=m
CONFIG_CRYPTO_LZ4HC=m

#
# Random Number Generation
#
CONFIG_CRYPTO_ANSI_CPRNG=m
CONFIG_CRYPTO_DRBG_MENU=m
CONFIG_CRYPTO_DRBG_HMAC=y
CONFIG_CRYPTO_DRBG_HASH=y
CONFIG_CRYPTO_DRBG_CTR=y
CONFIG_CRYPTO_DRBG=m
CONFIG_CRYPTO_JITTERENTROPY=m
CONFIG_CRYPTO_USER_API=m
CONFIG_CRYPTO_USER_API_HASH=m
CONFIG_CRYPTO_USER_API_SKCIPHER=m
CONFIG_CRYPTO_USER_API_RNG=m
CONFIG_CRYPTO_USER_API_AEAD=m
CONFIG_CRYPTO_HASH_INFO=y
CONFIG_CRYPTO_HW=y
CONFIG_CRYPTO_DEV_PADLOCK=y
CONFIG_CRYPTO_DEV_PADLOCK_AES=m
CONFIG_CRYPTO_DEV_PADLOCK_SHA=m
CONFIG_CRYPTO_DEV_CCP=y
CONFIG_CRYPTO_DEV_CCP_DD=m
CONFIG_CRYPTO_DEV_CCP_CRYPTO=m
CONFIG_CRYPTO_DEV_QAT=m
CONFIG_CRYPTO_DEV_QAT_DH895xCC=m
CONFIG_CRYPTO_DEV_QAT_DH895xCCVF=m
CONFIG_ASYMMETRIC_KEY_TYPE=y
CONFIG_ASYMMETRIC_PUBLIC_KEY_SUBTYPE=y
CONFIG_PUBLIC_KEY_ALGO_RSA=y
CONFIG_X509_CERTIFICATE_PARSER=y
CONFIG_PKCS7_MESSAGE_PARSER=y
CONFIG_PKCS7_TEST_KEY=m
CONFIG_SIGNED_PE_FILE_VERIFICATION=y

#
# Certificates for signature checking
#
CONFIG_MODULE_SIG_KEY="certs/signing_key.pem"
CONFIG_SYSTEM_TRUSTED_KEYRING=y
CONFIG_SYSTEM_TRUSTED_KEYS=""
CONFIG_HAVE_KVM=y
CONFIG_HAVE_KVM_IRQCHIP=y
CONFIG_HAVE_KVM_IRQFD=y
CONFIG_HAVE_KVM_IRQ_ROUTING=y
CONFIG_HAVE_KVM_EVENTFD=y
CONFIG_KVM_APIC_ARCHITECTURE=y
CONFIG_KVM_MMIO=y
CONFIG_KVM_ASYNC_PF=y
CONFIG_HAVE_KVM_MSI=y
CONFIG_HAVE_KVM_CPU_RELAX_INTERCEPT=y
CONFIG_KVM_VFIO=y
CONFIG_KVM_GENERIC_DIRTYLOG_READ_PROTECT=y
CONFIG_KVM_COMPAT=y
CONFIG_HAVE_KVM_IRQ_BYPASS=y
CONFIG_VIRTUALIZATION=y
CONFIG_KVM=m
CONFIG_KVM_INTEL=m
CONFIG_KVM_AMD=m
# CONFIG_KVM_MMU_AUDIT is not set
CONFIG_KVM_DEVICE_ASSIGNMENT=y
CONFIG_BINARY_PRINTF=y

#
# Library routines
#
CONFIG_RAID6_PQ=m
CONFIG_BITREVERSE=y
# CONFIG_HAVE_ARCH_BITREVERSE is not set
CONFIG_RATIONAL=y
CONFIG_GENERIC_STRNCPY_FROM_USER=y
CONFIG_GENERIC_STRNLEN_USER=y
CONFIG_GENERIC_NET_UTILS=y
CONFIG_GENERIC_FIND_FIRST_BIT=y
CONFIG_GENERIC_PCI_IOMAP=y
CONFIG_GENERIC_IOMAP=y
CONFIG_GENERIC_IO=y
CONFIG_ARCH_USE_CMPXCHG_LOCKREF=y
CONFIG_ARCH_HAS_FAST_MULTIPLIER=y
CONFIG_CRC_CCITT=m
CONFIG_CRC16=y
CONFIG_CRC_T10DIF=y
CONFIG_CRC_ITU_T=m
CONFIG_CRC32=y
# CONFIG_CRC32_SELFTEST is not set
CONFIG_CRC32_SLICEBY8=y
# CONFIG_CRC32_SLICEBY4 is not set
# CONFIG_CRC32_SARWATE is not set
# CONFIG_CRC32_BIT is not set
CONFIG_CRC7=m
CONFIG_LIBCRC32C=m
CONFIG_CRC8=m
# CONFIG_AUDIT_ARCH_COMPAT_GENERIC is not set
# CONFIG_RANDOM32_SELFTEST is not set
CONFIG_842_COMPRESS=m
CONFIG_842_DECOMPRESS=m
CONFIG_ZLIB_INFLATE=y
CONFIG_ZLIB_DEFLATE=y
CONFIG_LZO_COMPRESS=y
CONFIG_LZO_DECOMPRESS=y
CONFIG_LZ4_COMPRESS=m
CONFIG_LZ4HC_COMPRESS=m
CONFIG_LZ4_DECOMPRESS=y
CONFIG_XZ_DEC=y
CONFIG_XZ_DEC_X86=y
CONFIG_XZ_DEC_POWERPC=y
CONFIG_XZ_DEC_IA64=y
CONFIG_XZ_DEC_ARM=y
CONFIG_XZ_DEC_ARMTHUMB=y
CONFIG_XZ_DEC_SPARC=y
CONFIG_XZ_DEC_BCJ=y
CONFIG_XZ_DEC_TEST=m
CONFIG_DECOMPRESS_GZIP=y
CONFIG_DECOMPRESS_BZIP2=y
CONFIG_DECOMPRESS_LZMA=y
CONFIG_DECOMPRESS_XZ=y
CONFIG_DECOMPRESS_LZO=y
CONFIG_DECOMPRESS_LZ4=y
CONFIG_GENERIC_ALLOCATOR=y
CONFIG_REED_SOLOMON=m
CONFIG_REED_SOLOMON_ENC8=y
CONFIG_REED_SOLOMON_DEC8=y
CONFIG_REED_SOLOMON_DEC16=y
CONFIG_BCH=m
CONFIG_BCH_CONST_PARAMS=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m
CONFIG_BTREE=y
CONFIG_INTERVAL_TREE=y
CONFIG_ASSOCIATIVE_ARRAY=y
CONFIG_HAS_IOMEM=y
CONFIG_HAS_IOPORT_MAP=y
CONFIG_HAS_DMA=y
CONFIG_CHECK_SIGNATURE=y
CONFIG_CPU_RMAP=y
CONFIG_DQL=y
CONFIG_GLOB=y
# CONFIG_GLOB_SELFTEST is not set
CONFIG_NLATTR=y
CONFIG_ARCH_HAS_ATOMIC64_DEC_IF_POSITIVE=y
CONFIG_LRU_CACHE=m
CONFIG_CLZ_TAB=y
CONFIG_CORDIC=m
CONFIG_DDR=y
CONFIG_MPILIB=y
CONFIG_SIGNATURE=y
CONFIG_OID_REGISTRY=y
CONFIG_UCS2_STRING=y
CONFIG_FONT_SUPPORT=y
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
# CONFIG_SG_SPLIT is not set
CONFIG_ARCH_HAS_SG_CHAIN=y
CONFIG_ARCH_HAS_PMEM_API=y
CONFIG_ARCH_HAS_MMIO_FLUSH=y
```
Well kernel 4.4 just may be the straw that breaks me..If not Fixed.
```
 inxi -b
System:    Host: GhostMan Kernel: 4.3.0-2-generic x86_64 (64 bit)
           Desktop: MATE 1.10.2  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
inxi -A
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Creative Labs SB Audigy _**driver: snd_emu10k1**_
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic


```
Everything on 4.3 is just fine the driver gets loaded.

---

### Post by Doug S on 2016-01-12
Oh, I see. Even if one sets those three kernel configuration directives back to "m", they get turned back off during the kernel compile. Hmmm...

In the below, I saved a copy of the .config as .config-4.4-runrickus before starting the compile.

```
doug@s15:~/temp-k-git/linux$ diff .config .config-4.4-runrickus
5444c5444
< # CONFIG_SND_EMU10K1_SEQ is not set
---
> CONFIG_SND_EMU10K1_SEQ=m
5495a5496,5497
> CONFIG_SND_EMU10K1=m
> CONFIG_SND_EMU10K1X=m

```EDIT 1: It seems to be a dependent change, meaning another change mandates that these be disabled. How do I know? I copied the -rc7 config file and it seems to be working.
EDIT 2: I'm going to let the compile finish, check that the modules are actually there, and then ask for help/insight on IRC.

---

### Post by QDR06VV9 on 2016-01-12
You will appreciate this Doug:D
Just had to check it out on Arch
```
inxi -FxzSystem:    Host: ARCH Kernel: 4.4.0-1-MANJARO x86_64 (64 bit gcc: 5.3.0)
           Desktop: MATE 1.12.1 (Gtk 3.18.6)
           Distro: ManjaroLinux 15.12 Capella
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 20750
           clock speeds: max: 2600 MHz 1: 2600 MHz 2: 1400 MHz 3: 1400 MHz
           4: 1400 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520] bus-ID: 01:00.0
           Display Server: X.Org 1.17.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.63 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Creative Labs SB Audigy
           driver: _**snd_emu10k1 port: e800 bus-ID: 04:05.0**_
           Sound: Advanced Linux Sound Architecture v: k4.4.0-1-MANJARO
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: c800 bus-ID: 02:00.0
           IF: eno1 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too v: 0.9.28 port: e400 bus-ID: 04:06.0
           IF: enp4s6 state: down mac: <filter>
Drives:    HDD Total Size: 2500.5GB (4.8% used)
           ID-1: /dev/sda model: WDC_WD5000AAKS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
Partition: ID-1: / size: 450G used: 105G (25%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 9.45GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
Sensors:   System Temperatures: cpu: 48.0C mobo: 46.5C gpu: 0.0:48C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 189 Uptime: 2 min Memory: 739.3/5971.9MB
           Init: systemd Gcc sys: 5.3.0
           Client: Shell (bash 4.3.421) inxi: 2.2.32 



```
> [COLOR=#000000]EDIT 1: It seems to be a dependent change, meaning another change mandates that these be disabled. How do I know? I copied the -rc7 config file and it seems to be working.[/COLOR]
[COLOR=#000000]EDIT 2: I'm going to let the compile finish, check that the modules are actually there, and then ask for help/insight on IRC.[/COLOR]
Thank You Doug
waiting to see how your compile went..

---

### Post by Doug S on 2016-01-12
> **runrickus said:**
> waiting to see how your compile went..Oh, I forgot to report back. The compile was fine and the modules are there.
I have asked on [IRC]("http://irclogs.ubuntu.com/2016/01/12/%23ubuntu-kernel.html#t23:27"), but in my experience most help seems to come from way way way East, and it is probably too late for them now.

---

### Post by QDR06VV9 on 2016-01-12
> **Doug S said:**
> Oh, I forgot to report back. The compile was fine and the modules are there.
I have asked on [IRC]("http://irclogs.ubuntu.com/2016/01/12/%23ubuntu-kernel.html#t23:27"), but in my experience most help seems to come from way way way East, and it is probably too late for them now.
Sounds Good!:D
I would not worry about it though, as it will surely get fixed before release anyway!!
But I sure do appreciate the attention you have given here to this..(or me)
It also could have been the iso that I used for the install also, So in couple of days I will DL a new image to burn and install.;) 
A Big THANKS.

---

### Post by QDR06VV9 on 2016-01-13
I took the daily iso dated 1-12-2016 and installed it today, But the problem persists.
Tried a few other kernels(4.3 &&4.4 RC7's) and they were fine for my sound-card.
The only way I can Load 4.4([wily]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/")) is the method Doug S used..
So far I have not seen any one else with this problem.
Thanks for the link to irc Doug S let me know if you need me to add to it.
Regards

---

### Post by Doug S on 2016-01-13
> **runrickus said:**
> I would not worry about it though, as it will surely get fixed before release anyway!!I think it is worth worrying about. There have been a few occasions when I have gone to IRC for help and found that they were not aware of the issue. 

> **runrickus said:**
> I took the daily iso dated 1-12-2016 and installed it today, But the problem persists.I should have mentioned, I tried the daily yesterday.
> **runrickus said:**
> So far I have not seen any one else with this problem.I assume that is because not many are using kernel 4.4 yet.
> **runrickus said:**
> Thanks for the link to irc Doug S let me know if you need me to add to it.I assume you know that the logs are day-by-day (UTC), and the conversation has spilled over to [today]("http://irclogs.ubuntu.com/2016/01/13/%23ubuntu-kernel.html"). You will have to filter out all the other traffic (perhaps search by "smythies").

At this point, I will attempt to build a low latency kernel with a specific kernel configuration and a modified /linux/mm/Kconfig file. If the build is successful, would you be willing to test it? It is taking me awhile because I have other stuff to do.

---

### Post by QDR06VV9 on 2016-01-13
> [COLOR=#000000]I assume you know that the logs are day-by-day (UTC), and the conversation has spilled over to [/COLOR][today]("http://irclogs.ubuntu.com/2016/01/13/%23ubuntu-kernel.html")[COLOR=#000000]. You will have to filter out all the other traffic (perhaps search by "smythies").[/COLOR]
Yep already did that..
> [COLOR=#000000][INDENT]At this point, I will attempt to build a low latency kernel with a specific kernel configuration and a modified /linux/mm/Kconfig file. If the build is successful, would you be willing to test it? It is taking me awhile because I have other stuff to do.
[/INDENT]
[/COLOR]

Yes of course!!;) I will just keep checking back..
> [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG][COLOR=#000000] Originally Posted by [/COLOR]**runrickus**[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13422511#post13422511")[COLOR=#000000][I]So far I have not seen any one else with this problem.

[/I]
[/COLOR]
[COLOR=#000000]I assume that is because not many are using kernel 4.4 yet.[/COLOR]
Sometimes I am not the sharpest tool in the shed..:o I also thought about that last nite. LOL
> apw: I do not actually have the sound card (Creative Labs SB Audigy) and came here on behalf of someone else, after helping them isolate the issue(at least to the point where I needed help here). Yes, his AlsaMxer program isn't working,as the card isn't being detected. I also wonder if some 
of those other sound card differences in the kernel configuration file are for the same reason (ref: [http://paste.ubuntu.com/14481736/](http://paste.ubuntu.com/14481736/) )	15:00


apw
dsmythies, oddness, the delta i was shown was just the one card
I probably should have waited or at least saved a few more logs to send him..Oh Well..

---

### Post by Doug S on 2016-01-13
> **runrickus said:**
> I probably should have waited or at least saved a few more logs to send him..Oh Well..It is O.K. as it is understood what the issue is. (at least by Andy (apw) and rtg. I do not completely understand the chained dependency mechanism as to why the various sounds cards get disabled).

Anyway, the build failed, as Andrew predicted it would. And because of the calculation for ZONE_SHIFT, which cascades into other calculations.

---

### Post by QDR06VV9 on 2016-01-13
> **Doug S said:**
> It is O.K. as it is understood what the issue is. (at least by Andy (apw) and rtg. I do not completely understand the chained dependency mechanism as to why the various sounds cards get disabled).

Anyway, the build failed, as Andrew predicted it would. **And because of the calculation for ZONE_SHIFT, which cascades into other calculations**.
yes I was watching the thread.. But yes it makes it > [COLOR=#818144][FONT=Times New Roman]as that will likely oom us in the middle[/FONT][/COLOR]
I also spent about 4 hours on this last night, Also with no success.
But at least they know now..
Doug I can't thank you enough for taking the time out of your busy Day to add this to your work flow..
Kudos

---

### Post by MikeMecanic on 2016-01-14
A NVIDIA novel has already been written on this web site only.  On an Intel environment there ain't no such miscalculation.  Remains quiet and stable.  


```
mik@ug:~$ inxi -A
Audio:     Card-1 Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Logitech HD Webcam C525 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.4.0-040400-generic
mik@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400-generic      4.4.0-040400.201601101930                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
mik@ug:~$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free
mik@ug:~$ ubuntu-drivers list
intel-microcode
mik@ug:~$ exit
```

---

### Post by Doug S on 2016-01-14
> **Doug S said:**
>  see that this just occurred between 4.4-rc7 and 4.4-rc8. I also observe some other sound related changes between those two RC's.
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]diff /boot/config-4.4.0-040400rc7-generic /boot/config-4.4.0-040400rc8-generic[/COLOR]
3c3
< # Linux/x86_64 4.4.0-040400rc7-generic Kernel Configuration
---
> # Linux/x86_64 4.4.0-040400rc8-generic Kernel Configuration
393c393
< CONFIG_ZONE_DMA=y
---
> # CONFIG_ZONE_DMA is not set
517,518c517
< CONFIG_ZONE_DMA_FLAG=1
< CONFIG_BOUNCE=y
---
> CONFIG_ZONE_DMA_FLAG=0
545a545
> CONFIG_ZONE_DEVICE=y
5449c5449
< CONFIG_SND_EMU10K1_SEQ=m
---
> # CONFIG_SND_EMU10K1_SEQ is not set
5469d5468
< CONFIG_SND_ALS300=m
5471d5469
< CONFIG_SND_ALI5451=m
5479d5476
< CONFIG_SND_AZT3328=m
5504,5505d5500
< CONFIG_SND_EMU10K1=m
< CONFIG_SND_EMU10K1X=m
5508,5511d5502
< CONFIG_SND_ES1938=m
< CONFIG_SND_ES1968=m
< CONFIG_SND_ES1968_INPUT=y
< CONFIG_SND_ES1968_RADIO=y
5516d5506
< CONFIG_SND_ICE1712=m
5523,5524d5512
< CONFIG_SND_MAESTRO3=m
< CONFIG_SND_MAESTRO3_INPUT=y
5532,5533d5519
< CONFIG_SND_SONICVIBES=m
< CONFIG_SND_TRIDENT=m
7448a7435,7436
> CONFIG_ND_PFN=m
> CONFIG_NVDIMM_PFN=y

```All of the sound card differences seem to be a side effect of the change of the CONFIG_ZONE_DMA in the kernel configuration. The relevant file is, in the kernel source tree, linux/sound/pci/Kconfig and the relevant directive is "depends on ZONE_DMA". The only sound card that has that directive but does not appear in the above difference list is the "SiS 7019 Audio Accelerator" (SND_SIS7019), but that is because it is also a 32 bit only card (depends on X86_32).

So, if this doesn't get fixed we can expect complaints from users of these sound cards:

Avance Logic ALS300/ALS300+
ALi M5451 PCI Audio Controller
Aztech AZF3328 / PCI168
Emu10k1 (SB Live!, Audigy, E-mu APS)
Emu10k1X (Dell OEM Version)
ESS ES1938/1946/1969 (Solo-1)
ESS ES1968/1978 (Maestro-1/2/2E)
ICEnsemble ICE1712 (Envy24)
ESS Allegro/Maestro3
S3 SonicVibes
Trident 4D-Wave DX/NX; SiS 7018

EDIT: To keep track of this issue, a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534647") has been entered.

---

### Post by QDR06VV9 on 2016-01-15
Thanks for keeping us(me) in the loop Doug S

> [COLOR=#000000]So, if this doesn't get fixed we can expect complaints from users of these sound cards:[/COLOR]


I won't complain,(Futile here) I will just move along..;)
```

4.4.0-1-MANJAROLSB Version:	n/a
Distributor ID:	ManjaroLinux
Description:	Manjaro Linux
Release:	15.12
Codename:	Capella

```
The sound works flawlessly here^^^^

---

### Post by MikeMecanic on 2016-01-17
Bugs that I encounter early in the cycle under Ubuntu are all gone in Kylin.  Didn't have any problem loading Kernel 4.4.  The Num Lock keyboard is dead on startup even if it's enable in the BIOS.

```
xx@uk:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400-generic              4.4.0-040400.201601101930                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-5-generic             4.3.0-5.16                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
rc  linux-image-extra-4.3.0-6-generic             4.3.0-6.17                                 amd64        Linux kernel extra modules for version 4.3.0 on 64 bit x86 SMP
...
xx@uk:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-040400-generic              4.4.0-040400.201601101930                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP

xx@uk:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                         FSTYPE        SIZE MOUNTPOINT LABEL
sda                                      698.7G            
&#9500;&#9472;sda1                       ext2          243M /boot      
&#9500;&#9472;sda2                                       1K            
&#9492;&#9472;sda5                       LVM2_member 698.4G            
  &#9500;&#9472;ubuntu--kylin--vg-root   ext4        694.5G /          
  &#9492;&#9472;ubuntu--kylin--vg-swap_1 swap          3.9G [SWAP]     
sr0        
xx@uk:~$ exit

```

**EDIT:  Lost network name this morning on the Non-Sudoer account (wired).  Rename it to recover Internet.**

All the best,

---

### Post by Smask on 2016-01-22
I updated the DD-WRT firmware on my wifi router and the kernel version went from 3.2 to 4.4. The old FW was about a week old.

The newer router models come with enough flash memory storage available (thanks to SSD:s cratering the flash memory market) to make this possible.

[edit]

And there it is! 4.4 just dropped into proposed.

---

### Post by MikeMecanic on 2016-01-25
> **Smask said:**
> 
And there it is! 4.4 just dropped into proposed.

In deed 4.4 is in Proposed now. 

```
xx45@ug:~$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-1-generic           4.4.0-1.15                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-1-generic     4.4.0-1.15                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
xx45@ug:~$ 

```

---

### Post by syntaxerror74 on 2016-01-25
4.4.0 is a fantastic piece of work, and I hope it it will make it to *main* soon.
All of 4.3.x were nothing to write home about, but 4.4.0 comes with lots of overdue fixes (see also changelog).

---

### Post by MikeMecanic on 2016-02-01
> **syntaxerror74 said:**
> 4.4.0 is a fantastic piece of work, and I hope it it will make it to *main* soon.
All of 4.3.x were nothing to write home about, but 4.4.0 comes with lots of overdue fixes (see also changelog).

It's in today's build:  Ubuntu Kylin Feb.1st.  

```
xx@uk:~$ dpkg --list | grep linux-imageii  linux-image-4.4.0-2-generic                   4.4.0-2.16                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-2-generic             4.4.0-2.16                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.2.1                                  amd64        Generic Linux kernel image
xx@uk:~$ exit
```

---

### Post by fjgaude on 2016-02-02
Yes, 4.4 is working nicely on my new Skylake box, audio, video, all! I'm getting to be a happy camper.

---

### Post by sammiev on 2016-02-02
Been testing 4.4.1-040401-generic for a few days now.

Think I will keep this one for a bit.

---

### Post by QDR06VV9 on 2016-02-05
Well this is still a frustration for me..Today's Iso Xenial Mate
 ```
~$ inxi -A
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-2-generic

```
Still No SB Audigy Sound Card
```
$ inxi -b
System:    Host: ubuntu-mate Kernel: 4.4.0-2-generic x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.1.1
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 2508.6GB (0.4% used)
Info:      Processes: 209 Uptime: 13 min Memory: 659.3/5967.0MB
           Client: Shell (bash) inxi: 2.2.28 

```

The Pride seems to be absent in coding these days..:frown:
I since have been testing other distros with the 4.4 series kernel all of them have spot on support for all my hardware.
```
$ inxi -b
System:    Host: oldboy Kernel: 4.4.1-2-ARCH x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: Antergos Linux
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.18.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 361.18
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Creative Labs SB Audigy driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.4.1-2-ARCH
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 2508.6GB (1.0% used)
Info:      Processes: 180 Uptime: 3 min Memory: 654.1/5971.9MB
           Client: Shell (bash) inxi: 2.2.32 

```
So I guess I am done with testing Ubuntu..The good though is that it brought me back to Arch where i will Stay..
I am glad to hear that others are happy with it.
Forgot to mention the same happens on kernel 4.5RCs also.
Kind Regards

---

### Post by Doug S on 2016-02-05
> **runrickus said:**
> Well this is still a joke for me..Today's Iso Xenial Mate
... 
The Pride seems to be absent in coding these days..:frown:
I since have been testing other distros with the 4.4 series kernel all of them have spot on support for all my hardware.
...
So I guess I am done with testing Ubuntu..The good though is that it brought me back to Arch where i will Stay..
I am glad to hear that others are happy with it.
Forgot to mention the same happens on kernel 4.5RCs also.
Kind Regardsrunnrickas: Please bear with Ubuntu, and be aware that your issue is being worked on. Please also to consider to not get upset with Ubuntu for bringing an issue to the foreground that will eventually have to be dealt with for all distributions. There has been an upstream kernel patch proposed, although I am not current on the status.

I believe that if you try the low-latency kernel you will find it is O.K. with your sound card (and actually please do try it).
You can follow developments on[ the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534647") (and see the links in the last couple of comments). While it has been set to fix released, myself I do not like the current solution, for the exact reason you discovered, the generic kernel remains broken.

---

### Post by QDR06VV9 on 2016-02-05
> **Doug S said:**
> runnrickas: Please bear with Ubuntu, and be aware that your issue is being worked on. Please also to consider to not get upset with Ubuntu for bringing an issue to the foreground that will eventually have to be dealt with for all distributions. There has been an upstream kernel patch proposed, although I am not current on the status.

I believe that if you try the low-latency kernel you will find it is O.K. with your sound card (and actually please do try it).
You can follow developments on[ the bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534647") (and see the links in the last couple of comments). While it has been set to fix released, myself I do not like the current solution, for the exact reason you discovered, the generic kernel remains broken.
I do not get upset..But rather matter of fact.
As seen in the output in my last post the kernel runs fine, no problems with other non-debian distro's
But I have a love for Ubuntu so i will do my best to support it weather I use it or not!
There are other issues that i will not junk this thread with ATM.
But yes Doug I will test the low-lat kernels. 
Also I have been following the bug report.
Kind Regards
EDIT: @Doug_S I hope I do not sound callus here I very much appreciate your attention on this Thank You!:D

---

### Post by QDR06VV9 on 2016-02-06
Well after some hours of fooling around with some of the 4.4 kernels(lowlatency)
I determined that the only kernel that will now work with the Creative SB is the one in synaptic "4.4.0-2-lowlatency"
But that took some forcing to install..
The "4.4.1-040401-lowlatency" From mainline will not work at all
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ inxi -A
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel
           Sound: ALSA v: k4.4.1-040401-lowlatency
me@me-Aspire-M3300:~$ uname -r
4.4.1-040401-lowlatency
```
Found a bunch of info in the logs that helped me hammer the driver in only for the "4.4.0-2-lowlatency" kernel though;)
```
$ /sbin/lsmod | grep snd
snd_hda_codec_hdmi     53248  1
snd_hda_intel          36864  4
snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           65536  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
me@me-Aspire-M3300:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
    Subsystem: Acer Incorporated [ALI] RS780 Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fd000000-fe8fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000fbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    DeviceName: Onboard ATI SATA
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 28
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=8]
    I/O ports at 7000 [size=4]
    I/O ports at 6000 [size=16]
    Memory at fcfffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fcffe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0 USB OHCI1 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fcffd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fcfff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fcffc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0 USB OHCI1 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fcff7000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at fcfff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
    Subsystem: Acer Incorporated [ALI] SBx00 SMBus Controller
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco

00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (prog-if 8a [Master SecP PriP])
    DeviceName: Onboard ATI PATA
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4
    I/O ports at 0170 [size=8]
    I/O ports at 0374
    I/O ports at ff00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fcff6000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Device 196e:0915
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at fa000000 (64-bit, prefetchable) [size=32M]
    I/O ports at b800 [size=128]
    Expansion ROM at fe880000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
    Subsystem: Device 196e:0915
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe87c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
    DeviceName: Onboard Marvell Lan
    Subsystem: Acer Incorporated [ALI] 88E8071 PCI-E Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at c800 [size=256]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] VT6315 Series Firewire Controller
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at feaff800 (64-bit, non-prefetchable) [size=2K]
    I/O ports at d800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

04:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
    Subsystem: Creative Labs SB0350 Audigy 2
    Flags: bus master, medium devsel, latency 64
    I/O ports at e800 [size=64]
    Capabilities: <access denied>

04:05.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
    Subsystem: Creative Labs SB Audigy FireWire Port
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at e400 [size=256]
    Memory at febff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139cp, 8139too


```

But Long story short I have one kernel that works for the sound card.
```
$ inxi -A
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller driver: snd_hda_intel
           Card-2 Creative Labs SB Audigy driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-2-lowlatency


```
Regards

---

### Post by Doug S on 2016-02-10
Did you observe on the[ bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534647"), that there is an upstream fix (which we knew about, actually) "that now allows both ZONE_DMA and
ZONE_DEVICE to be set"? This had to be ultimately be the solution, I did not like the interim fix. I guess it still has to percolate down to Ubuntu.

---

### Post by QDR06VV9 on 2016-02-10
> **Doug S said:**
> Did you observe on the[ bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534647"), that there is an upstream fix (which we knew about, actually) "that now allows both ZONE_DMA and
ZONE_DEVICE to be set"? This had to be ultimately be the solution, I did not like the interim fix. I guess it still has to percolate down to Ubuntu.
Thanks Doug_S!:D
The way i read it was "Fixed"
> [COLOR=#333333][FONT=Ubuntu]55 minutes ago[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][TABLE="class: bug-activity"]
[TR]
[TD="colspan: 2"]Changed in linux (Ubuntu Xenial):[/TD]
[/TR]
[TR]
[TD="align: right"]**status**:[/TD]
[TD]In Progress &#8594; Fix Committed[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

I have been on another OS for a couple of days so I will fire Xenial up and check it out.
Thanks again Doug and sorry about the rant from before, you don't need my frustrations, and i feel bad about the other day.
But your reply back was very professional so say the least.
Kind Regards

---

### Post by Doug S on 2016-02-10
> **runrickus said:**
> 
The way i read it was "Fixed""fix committed" does not mean "fix released", and sometimes they even set "fixed released" a bit early. Wait for "fix released" and a subsequent updated kernel with regular updates on Xenial before testing.

---

### Post by QDR06VV9 on 2016-02-10
;) Thanks.

---

### Post by Doug S on 2016-02-18
@runrickus: Todays xenial updates include kernel 4.4.0-6.21, which should include the fix for your sound card issues.

---

### Post by QDR06VV9 on 2016-02-19
> **Doug S said:**
> @runrickus: Todays xenial updates include kernel 4.4.0-6.21, which should include the fix for your sound card issues.

Thank You Sir..:D
Been a little under the weather lately, so i will at my first chance get current..
Regards

---

