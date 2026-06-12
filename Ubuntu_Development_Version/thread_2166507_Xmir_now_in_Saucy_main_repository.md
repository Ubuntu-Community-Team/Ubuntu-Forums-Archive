---
title: "Xmir now in Saucy main repository"
date: 2013-08-09
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2013-08-09
I found this link on Ubuntu Discourse

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-August/037572.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-August/037572.html)


I tried the 20130809 ISO image but the live session does not run on Xmir like the Xubuntu-Xmir ISO does. I will try again with the daily image for tomorrow, 20130810. Now, that Xmir is in the main repository it should soon be part of the ISO image.

That link also gives an update on progress.

Regards.

---

### Post by mc4man on 2013-08-09
"- Fallback to stand alone X (for proprietary drivers)" 
That is now working ok here so if not liking the combo of nouveau, xmir & u-s-c then installing the prop nvidia drivers will make 13.10 useful 
Whether fallback & 3d support work with both available nvidia drivers don't know, 3.19 seems ok

(whether they create a hard dep on u-s-c in 13.10 I also don't know but atm it can be removed or disabled if not suitable

---

### Post by Mateusz Stachowski on 2013-08-10
> **grahammechanical said:**
> 

 ... I will try again with the daily image for tomorrow, 20130810. Now, that Xmir is in the main repository it should soon be part of the ISO image.



unity-system-compositor won't be part of the main installation until they develop two major features to support XMir, multimonitor & bypass composition support. You can be sure that XMir won't be enabled in 20130810 image and other that will follow in next week. I think that it will land just before the Feature freeze on August 22.

---

### Post by grahammechanical on 2013-08-10
Thank you.

So, not long then?

Regards.

---

### Post by mc4man on 2013-08-10
u-s-c is in the main repo now so no need for ppa, just install u-s-c & restart to try.

The input delay bug is pretty much fixed though at least here with MY nvidia hardware vsync in nouveau continues to be nonexistent
Restarts show vram instead of plymouth, not that big of a deal

---

### Post by OrangeCrate on 2013-08-10
After thoroughly wrecking my current install, I just grabbed the latest Xubuntu 64-bit daily from unetbootin (it doesn't tell you the specific date) and reinstalled.

Checking synaptic, I see this package:

```
xserver-xorg-xmir
```

Description:

> Xorg - the X.Org X server (module for running nested in Mir) 
 
xserver-xorg-xmir provides an extension module to support running an
Xorg as a client of an existing Mir compositor.

Edit:

Oops, accidently posted before I had finished. See next post...

---

### Post by OrangeCrate on 2013-08-10
Adding...

I went ahead and installed that package plus it's dependencies, and nothing happened. Looked around in synaptic and found the unity-system-compositor package and installed that with it's dependencies too. Rebooted, and here we are:

steve@laptop:~$ ps -ef | grep unity
root      1016   937  0 19:13 ?        00:00:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --from-dm-fd 10 --to-dm-fd 13 --vt 7
root      1023  1016  1 19:13 tty7     00:00:02 /usr/sbin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
steve     1726  1676  0 19:16 pts/0    00:00:00 grep --color=auto unity
steve@laptop:~$ grep -i xmir /var/log/Xorg.0.log
[    17.888] (II) LoadModule: "xmir"
[    17.888] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    17.909] (II) Module xmir: vendor="X.Org Foundation"
[    18.071] (II) intel(0): Output XMIR-1 has no monitor section
[    18.071] (II) intel(0): Printing probed modes for output XMIR-1
[    18.071] (II) intel(0): Modeline "XMIR mode of death"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz eP)
[    18.071] (II) intel(0): Output XMIR-1 connected
[    18.071] (II) intel(0): Output XMIR-1 using initial mode XMIR mode of death
steve@laptop:~$ 

steve@laptop:~$ grep -i LoadModule /var/log/Xorg.0.log
[    17.992] (II) LoadModule: "glx"
[    18.008] (II) LoadModule: "xmir"
[    18.184] (II) LoadModule: "intel"
[    18.184] (II) LoadModule: "vesa"
[    18.185] (II) LoadModule: "modesetting"
[    18.185] (II) LoadModule: "fbdev"
[    18.186] (II) UnloadModule: "vesa"
[    18.186] (II) UnloadModule: "modesetting"
[    18.186] (II) UnloadModule: "fbdev"
[    18.188] (II) LoadModule: "dri2"
[    18.214] (II) LoadModule: "evdev"
[    18.237] (II) LoadModule: "synaptics"
steve@laptop:~$ 


As I mentioned in another thread, this mir/xmir thingee is new to me. I assume I've got everything installed properly, if not, please let me know...

There is "flashing" on the login screen on startup, but once in, things, at least for now, appear to be working fine.

Tested on a Lenovo ThinkPad T400, with an embedded Intel chipset.

---

### Post by Chanath on 2013-08-10
I installed xmir from the repos, but how do I get into xmir?

---

### Post by Elfy on 2013-08-11
Installed them with a clean install of Xubuntu daily - other than a flashing login screen it appears to be 'ok'

---

### Post by P-I H on 2013-08-11
I have installed on an Asus 1000HE  and on a desktop with Radeon HD6670 graphics. It is working on the Asus with Intel graphics. The validation
```
p-i@pi-1000HE:~$ ps aux | grep unity-system-compositor
root       932  0.0  0.0   2268   552 ?        S    09:02   0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --from-dm-fd 10 --to-dm-fd 13 --vt 7
root       938  0.1  1.9 237396 19528 tty7     Ssl+ 09:02   0:26 /usr/sbin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
p-i       5544  0.0  0.0   5672   852 pts/0    S+   12:56   0:00 grep --color=auto unity-system-compositor
p-i@pi-1000HE:~$ grep -i xmir /var/log/Xorg.0.log
[    42.064] (II) LoadModule: "xmir"
[    42.065] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    42.110] (II) Module xmir: vendor="X.Org Foundation"
[    42.318] (II) intel(0): Output XMIR-1 has no monitor section
[    42.318] (II) intel(0): Printing probed modes for output XMIR-1
[    42.318] (II) intel(0): Modeline "XMIR mode of death"x59.7   43.75  1024 1072 1104 1184  600 603 613 619 +hsync -vsync (37.0 kHz eP)
[    42.319] (II) intel(0): Output XMIR-1 connected
[    42.319] (II) intel(0): Output XMIR-1 using initial mode XMIR mode of death
p-i@pi-1000HE:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 62 aug 11 09:02 /var/log/lightdm/unity-system-compositor.log
p-i@pi-1000HE:~$
```
It isn't working on the desktop. The validation
```
p-i@pi-GA-MA770-UD3-ubuntutest:~$ ps aux | grep unity-system-compositor
p-i       3913  0.0  0.0  14860   948 pts/0    S+   14:29   0:00 grep --color=auto unity-system-compositor
p-i@pi-GA-MA770-UD3-ubuntutest:~$ grep -i xmir /var/log/Xorg.0.log
p-i@pi-GA-MA770-UD3-ubuntutest:~$ ls -l /var/log/lightdm/unity-system-compositor.log
-rw------- 1 root root 143 aug 11 12:41 /var/log/lightdm/unity-system-compositor.log
p-i@pi-GA-MA770-UD3-ubuntutest:~$
```
The unity-system-compositor.log contains
```
/usr/sbin/unity-system-compositor: symbol lookup error: /usr/lib/x86_64-linux-gnu/libEGL.so.1: undefined symbol: mir_egl_mesa_display_is_valid

```

---

### Post by grahammechanical on 2013-08-11
> **Chanath said:**
> I installed xmir from the repos, but how do I get into xmir?

We don't. Provided we are not running on proprietary video drivers it should all take place during the OS loading process and we should not notice any difference between running on Xserver or Xmir. Apart from the usual issues that come up with the development branch, that is. Apart from a few noticable bugs, which seem to be now fixed, we tell we are running on Xmir by running some commands. I use

```
grep -i xmir /var/log/Xorg.0.log
```
```
 grep -i LoadModule /var/log/Xorg.0.log
```

Look for some thing that says Xmir loaded. And carrying on using the system to see if you can identify any instability or poor user experience that is down to Xmir.

For example, on Friday I installed Xmir. On Saturday I run the update and then I had 4 system freezes. But I do not put it down to the update or Xmir. Chromium was the only application running. I did not get a freeze when using Libreoffice. I am now using Firefox to see if the same things happens. It is not due to maxing out the CPU or memory either.

Regards

---

### Post by sanderj on 2013-08-11
FWIW: I just activated XMir on my 13.10

```
sudo apt-get install unity-system-compositor
sudo restart lightdm
```

and after the fresh login I have a functional desktop (not anymore the annoying second mouse pointer) and:

```


sander@HPtje:~$ grep -i xmir /var/log/Xorg.0.log 
[  1552.710] (II) LoadModule: "xmir"
[  1552.711] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[  1552.716] (II) Module xmir: vendor="X.Org Foundation"
[  1552.726] (II) intel(0): Output XMIR-1 has no monitor section
[  1552.726] (II) intel(0): Printing probed modes for output XMIR-1
[  1552.726] (II) intel(0): Modeline "XMIR mode of death"x60.0   72.00  1366 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz eP)
[  1552.726] (II) intel(0): Output XMIR-1 connected
[  1552.727] (II) intel(0): Output XMIR-1 using initial mode XMIR mode of death
sander@HPtje:~$ 

sander@HPtje:~$ grep -i loadmodule /var/log/Xorg.0.log 
[  1552.710] (II) LoadModule: "glx"
[  1552.710] (II) LoadModule: "xmir"
[  1552.719] (II) LoadModule: "intel"
[  1552.719] (II) LoadModule: "vesa"
[  1552.720] (II) LoadModule: "modesetting"
[  1552.720] (II) LoadModule: "fbdev"
[  1552.723] (II) UnloadModule: "vesa"
[  1552.723] (II) UnloadModule: "modesetting"
[  1552.723] (II) UnloadModule: "fbdev"
[  1552.727] (II) LoadModule: "dri2"
[  1552.760] (II) LoadModule: "evdev"
[  1552.768] (II) LoadModule: "synaptics"
sander@HPtje:~$

sander@HPtje:~$ ps afx | grep unity-system-compositor
12258 ?        S      0:00  \_ /bin/sh /usr/sbin/unity-system-compositor.sleep --from-dm-fd 11 --to-dm-fd 14 --vt 7
12261 tty7     Ssl+   0:11  |   \_ /usr/sbin/unity-system-compositor --from-dm-fd 11 --to-dm-fd 14 --vt 7
14394 pts/8    S+     0:00          |   |   \_ grep --color=auto unity-system-compositor
sander@HPtje:~$ 



```

That means XMir is correctly running, doesn't it?

FWIW: Intel CPU & GPU.

---

### Post by ventrical on 2013-08-11
Yes it does.

```

ventrical@ventrical-asus-aiproactive-extreme:~$ ps aux | grep unity-system-compositor
root       970  0.0  0.0   2268   548 ?        S    15:36   0:00 /bin/sh /usr/sbin/unity-system-compositor.sleep --from-dm-fd 7 --to-dm-fd 13 --vt 7
root      1009  1.3  2.6 199832 26968 tty7     Ssl+ 15:36   0:04 /usr/sbin/unity-system-compositor --from-dm-fd 7 --to-dm-fd 13 --vt 7
1000      2235  0.0  0.0   5668   804 pts/1    S+   15:42   0:00 grep --color=auto unity-system-compositor
ventrical@ventrical-asus-aiproactive-extreme:~$ grep -i xmir /var/log/Xorg.0.log
[    20.792] (II) LoadModule: "xmir"
[    20.793] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    20.813] (II) Module xmir: vendor="X.Org Foundation"
[    20.914] (II) NOUVEAU(0): Output XMIR-1 has no monitor section
[    20.914] (II) NOUVEAU(0): Printing probed modes for output XMIR-1
[    20.914] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz eP)
[    20.914] (II) NOUVEAU(0): Output XMIR-1 connected
[    20.914] (II) NOUVEAU(0): Output XMIR-1 using initial mode XMIR mode of death
[    20.914] (**) NOUVEAU(0):  Driver mode "XMIR mode of death": 88.8 MHz (scaled from 0.0 MHz), 55.5 kHz, 59.9 Hz
[    20.914] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz eP)
ventrical@ventrical-asus-aiproactive-extreme:~$ 

```

---

### Post by ventrical on 2013-08-11
> **mc4man said:**
> u-s-c is in the main repo now so no need for ppa, just install u-s-c & restart to try.

The input delay bug is pretty much fixed though at least here with MY nvidia hardware vsync in nouveau continues to be nonexistent
Restarts show vram instead of plymouth, not that big of a deal

That pretty well streamlines  the installation process. It's not rolling to llvmpipe like is was. I'll have to test those other machines.

---

### Post by ventrical on 2013-08-11
> **sanderj said:**
> FWIW: I just activated XMir on my 13.10

```
sudo apt-get install unity-system-compositor
sudo restart lightdm
```

and after the fresh login I have a functional desktop (not anymore the annoying second mouse pointer) and:

```


sander@HPtje:~$ grep -i xmir /var/log/Xorg.0.log 
[  1552.710] (II) LoadModule: "xmir"
[  1552.711] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[  1552.716] (II) Module xmir: vendor="X.Org Foundation"
[  1552.726] (II) intel(0): Output XMIR-1 has no monitor section
[  1552.726] (II) intel(0): Printing probed modes for output XMIR-1
[  1552.726] (II) intel(0): Modeline "XMIR mode of death"x60.0   72.00  1366 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz eP)
[  1552.726] (II) intel(0): Output XMIR-1 connected
[  1552.727] (II) intel(0): Output XMIR-1 using initial mode XMIR mode of death
sander@HPtje:~$ 

sander@HPtje:~$ grep -i loadmodule /var/log/Xorg.0.log 
[  1552.710] (II) LoadModule: "glx"
[  1552.710] (II) LoadModule: "xmir"
[  1552.719] (II) LoadModule: "intel"
[  1552.719] (II) LoadModule: "vesa"
[  1552.720] (II) LoadModule: "modesetting"
[  1552.720] (II) LoadModule: "fbdev"
[  1552.723] (II) UnloadModule: "vesa"
[  1552.723] (II) UnloadModule: "modesetting"
[  1552.723] (II) UnloadModule: "fbdev"
[  1552.727] (II) LoadModule: "dri2"
[  1552.760] (II) LoadModule: "evdev"
[  1552.768] (II) LoadModule: "synaptics"
sander@HPtje:~$

sander@HPtje:~$ ps afx | grep unity-system-compositor
12258 ?        S      0:00  \_ /bin/sh /usr/sbin/unity-system-compositor.sleep --from-dm-fd 11 --to-dm-fd 14 --vt 7
12261 tty7     Ssl+   0:11  |   \_ /usr/sbin/unity-system-compositor --from-dm-fd 11 --to-dm-fd 14 --vt 7
14394 pts/8    S+     0:00          |   |   \_ grep --color=auto unity-system-compositor
sander@HPtje:~$ 



```

That means XMir is correctly running, doesn't it?

FWIW: Intel CPU & GPU.


Another way to validate that mir is working:

Open a terminal with ctrl+alt+t

THEN

type in   'top' at the command prompt. You should see u-s-c in  rack.

```

%Cpu(s):  4.5 us,  2.3 sy,  0.0 ni, 93.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   1025960 total,   763148 used,   262812 free,    29872 buffers
KiB Swap:  1301500 total,        0 used,  1301500 free,   394424 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 2136 ventrica  20   0  111m  30m 6816 S   6.3  3.0   0:00.19 evolution-calen   
 1127 root      20   0 99.4m  25m  13m S   2.7  2.5   0:05.72 Xorg              
 1009 root      20   0  195m  26m 9376 S   1.0  2.6   0:02.68 unity-system-co   

```

---

### Post by sanderj on 2013-08-11
> **ventrical said:**
> Another way to valiate that mir is working:

Open a terminal with ctrl+alt+t

THEN

type in   'top' at the command prompt. You should see u-s-c in  rack.

```

%Cpu(s):  4.5 us,  2.3 sy,  0.0 ni, 93.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   1025960 total,   763148 used,   262812 free,    29872 buffers
KiB Swap:  1301500 total,        0 used,  1301500 free,   394424 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 2136 ventrica  20   0  111m  30m 6816 S   6.3  3.0   0:00.19 evolution-calen   
 1127 root      20   0 99.4m  25m  13m S   2.7  2.5   0:05.72 Xorg              
 1009 root      20   0  195m  26m 9376 S   1.0  2.6   0:02.68 unity-system-co   

```

If using top, I find

```
top -bn1 | grep unity-system-compositor

```
easier

---

### Post by sacridex on 2013-08-11
Tested it and it works, but everything is really slow...
I have massive tearing(i.e. when moving windows), when I type text into a terminal, it takes seconds till it reacts on it and the text is shown...

Using a geforce 9600 with open source drivers.

---

### Post by OrangeCrate on 2013-08-11
> **ventrical said:**
> Another way to valiate that mir is working:

Open a terminal with ctrl+alt+t

THEN

type in   'top' at the command prompt. You should see u-s-c in  rack.


That's easy, now why didn't I think of that?

:)

---

### Post by Mateusz Stachowski on 2013-08-11
> **sacridex said:**
> Tested it and it works, but everything is really slow...
I have massive tearing(i.e. when moving windows), when I type text into a terminal, it takes seconds till it reacts on it and the text is shown...

Using a geforce 9600 with open source drivers.

I also have GeForce 9600 GT and I didn't have problems with performance or tearing, typing is flaky especially for terminal. I tested Unity and [Xubuntu]("http://vanir.unit193.tk/mir/") using grml-rescueboot which creates bootable entries in grub for iso images. 

I could watch 720p or 1080p webm music videos downloaded from YouTube without problems. The 720p worked even with 2x speed in Firefox. No problems with other effects of Unity like scale, workspaces or minimize animation.

---

### Post by terry_gardener on 2013-08-12
> **sacridex said:**
> Tested it and it works, but everything is really slow...
I have massive tearing(i.e. when moving windows), when I type text into a terminal, it takes seconds till it reacts on it and the text is shown...

Using a geforce 9600 with open source drivers.

i have the gtx460 and it is slow also.

---

### Post by jerrylamos on 2013-08-12
> **philinux said:**
> [http://iloveubuntu.net/xmir-landed-ubuntu-1310s-universe](http://iloveubuntu.net/xmir-landed-ubuntu-1310s-universe)

Well, it installed on 3.11 but bug [https://bugs.launchpad.net/bugs/1102760](https://bugs.launchpad.net/bugs/1102760) on multimonitor support is even worse now.  Not only is the external monitor 1980x1020 limited to a 1024x600 quadrant, the screen flashes like mad, cursor hardly moves, keyboard deadly slow. Unusable. Previous two cursor versions of mir would do a limited amount, not this one.  I'll wait for the bug to clear.

---

### Post by mc4man on 2013-08-12
> **sacridex said:**
> Tested it and it works, but everything is really slow...
I have massive tearing(i.e. when moving windows), when I type text into a terminal, it takes seconds till it reacts on it and the text is shown...

Using a geforce 9600 with open source drivers.
Some of the input delay was fixed in  - better here in terminal, ect.
> mir (0.0.8+13.10.20130810-0ubuntu1) saucy; urgency=low

  [ Robert Ancell ]
  * Remove documentation on the system-compositor-testing PPA now
    everything is in main/universe in saucy.

  [ Kevin DuBois ]
  * Add an object for sending display config change messages to all
    connected clients (globally).

  [ Daniel van Vugt ]
  * Fix the compositor side of lag observed between input events and the
    screen. This is half the fix for LP: #1199450. The other half of the
    fix is to resolve client buffers arriving out of order, which has
    not been fully diagnosed but is known to be resolved by the "switch"
    branch. . (LP: #1199450)


Regression of no vsync with nouveau is tracked here, nothing of note yet as far as resolving
[https://bugs.launchpad.net/mir/+bug/1195811](https://bugs.launchpad.net/mir/+bug/1195811)

Also to consider is the 10%+ performance hit, this may become a factor on older hardware until fixed.

To note -  whether all nvidia hardware is affected with no vsync don't know, can only comment on hardware here where it's a total regression from none to everywhere. As far as videos & some saying they are ok, not all videos are susceptible to tearing, the test vid I previously linked does a decent job of exposing

---

### Post by QkpW4xf on 2013-08-13
[COLOR=#000000]*it works ok ! but very slow... ( *[/COLOR]will be faster in the future )
I'm[COLOR=#000000]* Using a amd 5770 with open source drivers.*[/COLOR]

---

### Post by ventrical on 2013-08-13
> **QkpW4xf said:**
> [COLOR=#000000]*it works ok ! but very slow... ( *[/COLOR]will be faster in the future )
I'm[COLOR=#000000]* Using a amd 5770 with open source drivers.*[/COLOR]

 On AMD Athlon 5000+ ccsm is working really well  (Unity Also) OverClocked x 500MHz. I don't see the tearing .. but it is a little jumpy on my (nVidia GeForce210/218) overclocked @4.1GHz on an Intel chip.

```



ventrical@ventrical-asus-aiproactive-extreme:~$ sudo dmidecode -t processor | grep "Speed"
    Max Speed: 3800 MHz
    Current Speed: 3263 MHz
ventrical@ventrical-asus-aiproactive-extreme:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +75.0°C)

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.57 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.28 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +4.95 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.03 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     3199 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +29.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +25.0°C  (high = +45.0°C, crit = +90.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +32.0°C  
Core0 Temp:   +40.0°C  
Core1 Temp:   +33.0°C  
Core1 Temp:   +40.0°C  

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-asus-aiproactive-extreme:~$ 

```

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

```

---

### Post by P-I H on 2013-08-14
I installed yesterday's daily and unity-system-composer works now
```
p-i@pi-GA-MA770-UD3-test:~$ grep -i xmir /var/log/Xorg.0.log
[    16.089] (II) LoadModule: "xmir"
[    16.089] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    16.109] (II) Module xmir: vendor="X.Org Foundation"
[    16.265] (II) [XMir] Using Radeon device from Mir.
[    16.272] (II) RADEON(0): Output XMIR-1 has no monitor section
[    16.272] (II) RADEON(0): Printing probed modes for output XMIR-1
[    16.272] (II) RADEON(0): Modeline "XMIR mode of death"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[    16.272] (II) RADEON(0): Output XMIR-1 connected
[    16.272] (II) RADEON(0): Output XMIR-1 using initial mode XMIR mode of death
p-i@pi-GA-MA770-UD3-test:~$
``` 
On the old installation libegl1-mesa wasn't upgraded and 9.2~git20130628.g6b676e6-0ubuntu0+mir1-jenkins83saucy0 was still used. On the new install libegl1-mesa is version 9.1.6-2ubuntu2.

---

