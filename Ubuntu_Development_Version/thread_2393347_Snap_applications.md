---
title: "Snap applications"
date: 2018-06-02
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-06-02
With communitheme the snap applications Terminal, Calculator and System Monitor used transparency.
They are now working on my Cosmic Cuttlefish installation. The transparency is gone. There are however some error messages.
```
Jun  2 07:59:58 pi-MS-7A34 gnome-calculato[14759]: Theme parsing error: gtk.css:2662:72: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Jun  2 08:01:08 pi-MS-7A34 gnome-terminal-[14909]: Theme parsing error: gtk.css:2662:72: The :insensitive pseudo-class is deprecated. Use :disabled instead.
Jun  2 08:01:33 pi-MS-7A34 gnome-system-mo[14932]: Theme parsing error: gtk.css:2662:72: The :insensitive pseudo-class is deprecated. Use :disabled instead.

```
It's not working on Ubuntu 18.04

---

### Post by PaulW2U on 2018-06-07
I think I'm seeing something different here. 

To clarify, the regular **deb** versions of the Calculator and System Monitor using Communitheme are working correctly in 18.10. But the **snap** versions are broken in that they are totally transparent and therefore unusable. I'm seeing this issue with Communitheme from both the stable and edge channels.

Is there a snap version of gnome-terminal? I can't seem to find one.
```
paul@paul-VirtualBox:~$ snap install gnome-terminal
error: snap "gnome-terminal" not found

```
"snap search" doesn't find gnome-terminal either.

Where are those errors being logged?

---

### Post by #&amp;thj^% on 2018-06-07
> **PaulW2U said:**
> I think I'm seeing something different here. 

To clarify, the regular **deb** versions of the Calculator and System Monitor using Communitheme are working correctly in 18.10. But the **snap** versions are broken in that they are totally transparent and therefore unusable. I'm seeing this issue with Communitheme from both the stable and edge channels.

Is there a snap version of gnome-terminal? I can't seem to find one.
```
paul@paul-VirtualBox:~$ snap install gnome-terminal
error: snap "gnome-terminal" not found

```
"snap search" doesn't find gnome-terminal either.

Where are those errors being logged?
+1
I wonder if OP ran 
```
env
``` 
when first logged in would show anything helpful.
I know if a wayland session is used then it dose not load  Communitheme fast enough but a second login loads Communitheme fine.
xorg session is fine though on my end.

---

### Post by PaulW2U on 2018-06-07
Thanks 1fallen, you prompted me to log into a Wayland session. Both the Calculator and System Monitor display correctly using Communitheme. It's Xorg that breaks those applications. I must remember to think Wayland more often.  :)

There's probably a lot on the [Community Hub]("https://community.ubuntu.com/") that I should be reading but the relevant threads are getting very long and I don't find the technical stuff re themes that interesting.

---

### Post by #&amp;thj^% on 2018-06-07
> **PaulW2U said:**
>  It's Xorg that breaks those applications. I must remember to think Wayland more often.  :)


PaulW2U did you then try to login to xorg from wayland, and was it any different?

---

### Post by PaulW2U on 2018-06-07
> **1fallen said:**
> PaulW2U did you then try to login to xorg from wayland, and was it any different?
In an Xorg session, both applications are again transparent.  :(

---

### Post by #&amp;thj^% on 2018-06-07
Sounds like bug reporting time again. :)
Thanks for checking PaulW2U.

---

### Post by P-I H on 2018-06-07
There is a bug report and discussion about the transparency
[https://github.com/ubuntu/gtk-communitheme/issues](https://github.com/ubuntu/gtk-communitheme/issues)

However on my installation of Cosmic with the 14.17 kernel the snap versions are working as intended.
I am not able to check this further as my system crashed this morning.

---

### Post by PaulW2U on 2018-06-07
> **P-I H said:**
> There is a bug report and discussion about the transparency
[https://github.com/ubuntu/gtk-communitheme/issues](https://github.com/ubuntu/gtk-communitheme/issues)
I'll take a look, thanks.
> **1fallen said:**
> Sounds like bug reporting time again. :)
Thanks for checking PaulW2U.
I'm not sure I've reported back to you correctly now 1fallen. It's confusing having two supposedly identical calculators installed but from different sources and then having to work out which is which.

So in a Wayland session I uninstalled both calculators. I installed the deb version and it was correctly themed with Communitheme. I uninstalled that and installed the snap version. No Communitheme but Ambiance. So it looks like Communitheme doesn't work at all with Wayland but makes the calculator totally transparent with Xorg. System Monitor also shows the same results but I can't start both versions at the same time.

The attached screenshot shows my desktop when both calculators were installed.

Perhaps someone who knows a little more than I do can confirm my revised findings?

---

### Post by #&amp;thj^% on 2018-06-07
> **PaulW2U said:**
> 
So in a Wayland session I uninstalled both calculators. I installed the deb version and it was correctly themed with Communitheme. I uninstalled that and installed the snap version. No Communitheme but Ambiance. So it looks like Communitheme doesn't work at all with Wayland but makes the calculator totally transparent with Xorg. System Monitor also shows the same results but I can't start both versions at the same time.

The attached screenshot shows my desktop when both calculators were installed.

Perhaps someone who knows a little more than I do can confirm my revised findings?
Yup that's my findings also on "wayland" but for me at least xorg session works fine I have Nvidia Drivers installed? I wonder if P-I H has Nvidia, I know he reports that kernel 4.17 is working for him.
Hard to triage with this kind of information being reported. Maybe wait and see if Jbicha has anything to say.

---

### Post by P-I H on 2018-06-07
This is my present configuration after a new installation
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-22-generic x86_64 bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.H0 date: 05/02/2018
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3000 MHz 1: 1377 MHz 2: 1374 MHz 3: 1376 MHz
           4: 1372 MHz 5: 1402 MHz 6: 1546 MHz 7: 1376 MHz 8: 1376 MHz
           9: 1377 MHz 10: 1377 MHz 11: 1377 MHz 12: 1377 MHz 13: 1375 MHz
           14: 1376 MHz 15: 1377 MHz 16: 1377 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480]
           Display Server: x11 (X.Org 1.19.6 ) driver: amdgpu
           Resolution: 2560x1440@119.99hz
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-22-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-3 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-4 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-22-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 490.1GB (1.6% used)
           ID-1: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-2: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 7.5G (4%) fs: ext4 dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 32.0C mobo: 36.0C gpu: 29.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 219 fan-2: 338 fan-3: 998 fan-4: 0 fan-5: 747
Info:      Processes: 372 Uptime: 13 min Memory: 1972.1/16052.5MB
           Client: Shell (bash) inxi: 2.3.56 
p-i@pi-MS-7A34:~$ 

```

---

### Post by P-I H on 2018-06-07
This is the recommended way to install communitheme
[https://github.com/ubuntu/communitheme-snap-helpers/blob/master/README.md](https://github.com/ubuntu/communitheme-snap-helpers/blob/master/README.md)
When you are using the snap version you will get an updated version every monday
Useful commands are
snap info communitheme
snap refresh communitheme --stable

---

### Post by PaulW2U on 2018-06-22
I'm now seeing [communitheme]("https://community.ubuntu.com/t/call-for-participation-an-ubuntu-default-theme-lead-by-the-community/1545") correctly applied to the snap versions of the Calculator and System Monitor when running in both Xorg and Wayland sessions. The Ambiance theme is now looking rather dated after being the default theme for what must be six or more years now.

communitheme, or whatever it is going to be renamed to, will give Ubuntu a much needed facelift that, in my opinion, completes the switch from Unity to GNOME Shell.

---

### Post by corradoventu on 2018-06-23
On cosmic installed from recent ISO the installation of snap applications does not complete: [https://forum.snapcraft.io/t/gnome-calculator-failed-to-create-symbolic-link/5742](https://forum.snapcraft.io/t/gnome-calculator-failed-to-create-symbolic-link/5742)

---

### Post by mc4man on 2018-06-23
> **corradoventu said:**
> On cosmic installed from recent ISO the installation of snap applications does not complete: [https://forum.snapcraft.io/t/gnome-calculator-failed-to-create-symbolic-link/5742](https://forum.snapcraft.io/t/gnome-calculator-failed-to-create-symbolic-link/5742)

At times Canonicals snap thing is a mess & errors can be misleading. Your snap list is missing gtk-common-themes
At this point you'd need to  - 
```

snap remove gnome-3-26-1604
snap remove  gnome-calculator
```

Then this, ignore any error message if any about gtk-common-themes but let process complete, i.e return to prompt.

```
snap install gnome-calculator
```

This should lead to a snap list of 
```
$ snap list
Name               Version  Rev   Tracking  Developer  Notes
core               16-2.33  4830  stable    canonical  core
gnome-3-26-1604    3.26.0   64    stable    canonical  -
gnome-calculator   3.28.1   178   stable    canonical  -
gtk-common-themes  0.1      319   stable    canonical  -
```

And it should open when running
```
snap run gnome-calculator
```

---

### Post by P-I H on 2018-06-24
Installed the latest cosmic iso, that's from 11/6. Tried to install updates, but this didn't finish because of the "snap seed problem". Added me to the bug.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844)

---

### Post by PaulW2U on 2018-06-24
> **P-I H said:**
> Installed the latest cosmic iso, that's from 11/6. Tried to install updates, but this didn't finish because of the "snap seed problem". Added me to the bug.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844)
Thanks for posting the link to that bug report. For some strange reason I couldn't find it last night when I too created a new cosmic installation. I've also marked the bug as affecting me and subscribed to notifications.

Fortunately, I was already aware of how to apply the fix by re-ordering seeds.yaml and aborting the relevant item in the "snap changes" list which was stuck on a status of "Doing".
```

paul@N1642u~> snap list
Name                  Version  Rev   Tracking  Developer  Notes
communitheme          0.1      465   stable    didrocks   -
core                  16-2.33  4830  stable    canonical  core
gnome-3-26-1604       3.26.0   64    stable    canonical  -
gnome-calculator      3.28.1   178   stable    canonical  -
gnome-characters      3.28.2   101   stable    canonical  -
gnome-logs            3.28.2   37    stable    canonical  -
gnome-system-monitor  3.26.0   45    stable    canonical  -
gtk-common-themes     0.1      319   stable    canonical  -

```
Apart from communitheme, which was added later, the above list of snaps is the current default after all snaps have been refreshed.

---

### Post by P-I H on 2018-06-24
Managed to get it to work after some tries. Didn't work to edit /var/lib/snapd/seed/seed.yaml and reboot or reinstall. I had to abort the "doing" "Initialize system state" as PaulW2U wrote.
I run the command
```
snap changes
snap abort 1
snap changes
snap tasks 3
```
1 is the number of the change with status "doing"  and 3 is the number of the new "Initialize system state" created by some service.
After aborting the change in "doing" and installation of Communitheme I got
```
p-i@pi-GA-990FXA-UD3:~$ snap changes
ID   Status  Spawn                Ready                Summary
3    Done    today at 15:11 CEST  today at 15:12 CEST  Initialize system state
4    Done    today at 15:19 CEST  today at 15:19 CEST  Install "communitheme" snap
1    Undone  today at 16:28 CEST  today at 15:11 CEST  Initialize system state
2    Done    today at 16:28 CEST  today at 16:28 CEST  Initialize device

p-i@pi-GA-990FXA-UD3:~$ snap list
Name                  Version  Rev   Tracking  Developer  Notes
communitheme          0.1      465   stable    didrocks   -
core                  16-2.33  4830  stable    canonical  core
gnome-3-26-1604       3.26.0   64    stable/…  canonical  -
gnome-calculator      3.28.1   178   stable/…  canonical  -
gnome-characters      3.28.2   101   stable/…  canonical  -
gnome-logs            3.28.2   37    stable/…  canonical  -
gnome-system-monitor  3.26.0   45    stable/…  canonical  -
gtk-common-themes     0.1      319   stable/…  canonical  -

```
Calculator and System Monitor is now working.

---

### Post by corradoventu on 2018-06-25
corrado@corrado-HP-p4-cc-0620:~$ snap remove gnome-3-26-1604
error: cannot remove "gnome-3-26-1604": snap "gnome-3-26-1604" has "seed"
       change in progress
corrado@corrado-HP-p4-cc-0620:~$ snap remove  gnome-calculator
error: cannot remove "gnome-calculator": snap "gnome-calculator" has "seed"
       change in progress
corrado@corrado-HP-p4-cc-0620:~$ snap install  gnome-calculator
snap "gnome-calculator" is already installed, see 'snap help refresh'
corrado@corrado-HP-p4-cc-0620:~$

---

### Post by PaulW2U on 2018-06-25
Hi corrado, to fix that you need to re-order the entries in seed.yaml so that the entry for gtk-common-themes is before the entries for the applications. Then you have to abort the initialisation shown in the snap changes list. This is what P-I H and I were documenting in the above two posts. I think snaps are being initialised in the wrong order to until the issue is fixed seed.yaml needs to be edited to reflect the revised order.

Once the initialisation has been stopped in should restart automatically and read your updated seed.yaml file. You don't need to remove and re-add the calculator.

characters, logs and the system monitor should automatically appear in the snap list once you have applied the fix and the system has reinitialised.

---

### Post by corradoventu on 2018-06-26
in /var/lib/snapd/seed/seed.yaml i see:
```
snaps:
  -
    name: core
    channel: stable
    file: core_4830.snap
  -
    name: gnome-3-26-1604
    channel: stable/ubuntu-18.10
    file: gnome-3-26-1604_64.snap
  -
    name: gnome-calculator
    channel: stable/ubuntu-18.10
    file: gnome-calculator_178.snap
  -
    name: gnome-characters
    channel: stable/ubuntu-18.10
    file: gnome-characters_101.snap
  -
    name: gnome-logs
    channel: stable/ubuntu-18.10
    file: gnome-logs_37.snap
  -
    name: gnome-system-monitor
    channel: stable/ubuntu-18.10
    file: gnome-system-monitor_45.snap
  -
    name: gtk-common-themes
    channel: stable/ubuntu-18.10
    file: gtk-common-themes_319.snap
```

```
corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready  Summary
1    Doing   4 days ago, at 09:33 CEST  -      Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ snap abort 1
corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready  Summary
1    Undo    4 days ago, at 09:33 CEST  -      Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready                Summary
1    Undone  4 days ago, at 09:33 CEST  today at 07:14 CEST  Initialize system state
3    Doing   today at 07:14 CEST        -                    Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready                Summary
1    Undone  4 days ago, at 09:33 CEST  today at 07:14 CEST  Initialize system state
3    Doing   today at 07:14 CEST        -                    Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready                Summary
1    Undone  4 days ago, at 09:33 CEST  today at 07:14 CEST  Initialize system state
3    Doing   today at 07:14 CEST        -                    Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ 

```

---

### Post by PaulW2U on 2018-06-26
Did you change the order of the entries in seed.yaml? The block
```
    name: gtk-common-themes
    channel: stable/ubuntu-18.10
    file: gtk-common-themes_319.snap

```
needs to be moved before the calculator entry. Take care  to preserve the spacing in the file Then you can continue with "snap abort **3**".

---

### Post by corradoventu on 2018-06-26
changed seed.yaml, now it works, thanks a lot,```
corrado@corrado-HP-p4-cc-0620:~$ snap abort 3
corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready                Summary
1    Undone  4 days ago, at 09:33 CEST  today at 07:14 CEST  Initialize system state
3    Undone  today at 07:14 CEST        today at 16:22 CEST  Initialize system state
4    Doing   today at 16:22 CEST        -                    Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ snap changes
ID   Status  Spawn                      Ready                Summary
1    Undone  4 days ago, at 09:33 CEST  today at 07:14 CEST  Initialize system state
3    Undone  today at 07:14 CEST        today at 16:22 CEST  Initialize system state
4    Done    today at 16:22 CEST        today at 16:23 CEST  Initialize system state

corrado@corrado-HP-p4-cc-0620:~$ snap list
Name                  Version  Rev   Tracking  Developer  Notes
core                  16-2.33  4830  stable    canonical  core
gnome-3-26-1604       3.26.0   64    stable/…  canonical  -
gnome-calculator      3.28.1   178   stable/…  canonical  -
gnome-characters      3.28.2   101   stable/…  canonical  -
gnome-logs            3.28.2   37    stable/…  canonical  -
gnome-system-monitor  3.26.0   45    stable/…  canonical  -
gtk-common-themes     0.1      319   stable/…  canonical  -
corrado@corrado-HP-p4-cc-0620:~$ 

```

---

