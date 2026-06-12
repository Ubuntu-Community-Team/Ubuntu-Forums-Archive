---
title: "After today's upgrade, the default Ubuntu 18.04 shows interesting login choices"
date: 2017-10-28
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-10-28
After today's upgrade, the default Ubuntu 18.04 login screen shows something interesting. (This 18.04 dev install uses lightdm instead of gdm.)

---

### Post by jbicha on 2017-10-28
Please file a bug against gnome-session. That regression might have been introduced by gnome-session [3.26.1-0ubuntu6]("https://launchpad.net/ubuntu/+source/gnome-session/3.26.1-0ubuntu6").

---

### Post by Chanath on 2017-11-01
> **jbicha said:**
> Please file a bug against gnome-session. That regression might have been introduced by gnome-session [3.26.1-0ubuntu6]("https://launchpad.net/ubuntu/+source/gnome-session/3.26.1-0ubuntu6").

I reported this the same day as a bug, which never appeared, so posted again today, [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1729249](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1729249) 

I asked this as a question the same day then as the bug report couldn't be seen, which got replied by Manfred Hampl. > [COLOR=#333333][FONT=Ubuntu]Ubuntu 18.04 is work in progress and you cannot expect a smooth experience whilst the developers are working on it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]If you deem this so severe that it has to be changed immediately, please file a bug report.[/FONT][/COLOR]

Do I find it severe? Not 100% sure, as I can use the Xorg without much worry. Couldn't find the earlier bug report anywhere. Do the devs find it severe? No idea.
Even after today's upgrade, the default shows X11.

---

### Post by vasa1 on 2017-11-01
> **Chanath said:**
> After today's upgrade, the default Ubuntu 18.04 login screen shows something interesting. (This 18.04 dev install uses lightdm instead of gdm.)
But is it still default if you use lightdm instead of gdm?

---

### Post by Chanath on 2017-11-01
> **vasa1 said:**
> But is it still default if you use lightdm instead of gdm?

I am using lightdm, and it is the default. 

I can move to gdm any time (dpkg-reconfigure gdm3), but still the same result. Ubuntu default would go on a loop, never starting. Only Ubuntu on Xorg would. Someone also has the same problem, [http://ubuntuforums.org/showthread.php?t=2373467&page=2](http://ubuntuforums.org/showthread.php?t=2373467&page=2)

---

### Post by dino99 on 2017-11-01
> **Chanath said:**
> I reported this the same day as a bug, which never appeared, so posted again today, [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1729249](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1729249) 

if you open a report, do it with 'ubuntu-bug <packagename>' , or later use: apport-collect <bug number>

---

### Post by ventrical on 2017-11-01
Not here on my Intel Dry Gnome3 gdm3 box.

Regards..

---

### Post by dino99 on 2017-11-01
> **ventrical said:**
> Not here on my Intel Dry Gnome3 gdm3 box.

Regards..

is it a dist-upgraded install or a fresh one ?
Mine is a Artful netboot fresh install upgraded to Bionic (intel igp). First, no way to login (gdm3 loop); so lightdm has been installed and used, but still get the problem reported above (no wayland session at all)

---

### Post by rrnbtter on 2017-11-01
Greetings,
On a new install from the Artful ISO I default to xorg. Then install gnome-shell and gdm3. I can then boot to Gnome/Wayland. I have yet to get a default Gnome Wayland install. I think that will come with the 18.04 ISO's, yet to arrive.

---

### Post by dino99 on 2017-11-01
ubuntu or gnome login (supposed to be a wayland session), but:

echo $XDG_SESSION_TYPE
x11

---

### Post by ventrical on 2017-11-01
> **dino99 said:**
> is it a dist-upgraded install or a fresh one ?
Mine is a Artful netboot fresh install upgraded to Bionic (intel igp). First, no way to login (gdm3 loop); so lightdm has been installed and used, but still get the problem reported above (no wayland session at all)

*This* install I am speaking of was 17.10 release! > dist-upgrade to 18.04 through correct means. Works beautifully. Currently in wayland. I only installed synaptic for xorg and I dare not install any other xapps packages, even in xorg becasue wayland/gdm3 is too touchy rightnow and I don't want to break this particular Dry Gnome3 install because i want to monitor progression.
Proposed in ON.


I'll get back on my other boxes with lightdm installed but it looks like you guys confirmed it.
```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.25-0ubuntu1)
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0 serial: N/A
           UEFI: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) 
           arch: Haswell rev.3 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12399
           clock speeds: max: 3100 MHz 1: 3099 MHz 2: 3099 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 200.0GB (3.9% used)
           ID-1: /dev/sda model: MAXTOR_STM320082 size: 200.0GB
Partition: ID-1: / size: 182G used: 7.3G (5%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 205 Uptime: 58 min Memory: 1152.3/3808.9MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37 
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by dino99 on 2017-11-01
hm, mine is quite similar as yours, maybe some more additional packages: dconf, dkms, gtkorphan, bleachbit

---

### Post by ventrical on 2017-11-01
> **dino99 said:**
> hm, mine is quite similar as yours, maybe some more additional packages: dconf, dkms, gtkorphan, bleachbit

Thanks dino,
Honestly I do not want to be told to turn my proposed off or anything.  I will   experiment with it and report bugs. so far .. no bugs.. I am using it right now.  I really like how it is going and I want it to succeed. As I say I'll get back  with detials about my other boxes that have lightdm.

---

### Post by Chanath on 2017-11-01
I installed the default Ubuntu 17.10 while it was in the late development stage, and kept on updating and upgrading and then moved it to 18.04. Wayland was there for sometime, and then one day after an upgrade, Wayland had gone, that is, ubuntu.desktop is there in the xsessions, and it says, ```
[Desktop Entry]Name=Ubuntu on Xorg
Comment=This session logs you into Ubuntu
Exec=env GNOME_SHELL_SESSION_MODE=ubuntu  gnome-session --session=ubuntu
TryExec=gnome-shell
Icon=
Type=Application
DesktopNames=ubuntu:GNOME
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```

Done by the upgrade system, coming automatically or otherwise. Or is it intentional?

---

