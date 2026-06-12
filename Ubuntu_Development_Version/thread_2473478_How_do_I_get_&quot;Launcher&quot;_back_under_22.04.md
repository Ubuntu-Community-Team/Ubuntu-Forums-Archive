---
title: "How do I get &quot;Launcher&quot; back under 22.04"
date: 2022-04-05
forum: Ubuntu Development Version
---

### Post by cigtoxdoc on 2022-04-05
I have lightdm and unity desktop installed, but I still have the “horrible” display of programs and disk drives that was there just after I upgraded.  How do I get the "launcher" back and have same desktop I had on 21.10?

Thank you,

John

---

### Post by yancek on 2022-04-06
Could you be more specific on what "horrible display" means?  The final release of 22.04 is on April 22nd so you have upgraded to a beta (test) version so you caa expect problems.  Post more details and someone may be able to help.

---

### Post by cigtoxdoc on 2022-04-06
Thank you for your reply.  Two pictures show what screen looks like in 22.04.  I wanted to add a third picture of 21.10 desktop, but I apparently don't know how to do that.

John

---

### Post by cigtoxdoc on 2022-04-06
Apparently, I don't know what I am doing with uploads on this forum.  I had to convert the jpg of the 21.10 desktop with lightdm display to a PDF file and reduce the size of that to show viewers the desktop I want in 22.04.

Thank you,

John

---

### Post by slickymaster on 2022-04-06
*Thread moved to **Ubuntu Development Version**.*

---

### Post by deadflowr on 2022-04-06
Your images show the gnome desktop.
Did you want unity instead?

You should be able to switch it at the login screen.
It does not matter if the login screen is lightdm or gdm3.

In the gdm3 login screen there should be a cog-like icon in the bottom right corner area.
(The cog may or may not show up until you select the user, but before you enter a password)
You can select the desktop session from the cog-like icon's dropdown menu listing.

In lightdm's login screen there should be an icon within the login username box,
you can click on that to select whichever desktop session you'd like to login to.

---

### Post by cigtoxdoc on 2022-04-06
Thank you.  I had already tried your suggestion.  A "sad computer icon comes up.  Underneath the first line of text reads, "Oh no! Something has gone wrong." The second line of text reads, "A problem has occurred and the system can't recover.  All extensions have been disabled as a precaution." Underneath that is a box marked, "Log out"

John

---

### Post by #&amp;thj^% on 2022-04-06
> **cigtoxdoc said:**
>  "Oh no! Something has gone wrong." The second line of text reads, "A problem has occurred and the system can't recover.  All extensions have been disabled as a precaution.
John

You might try:
Minimal Installation:
```

sudo apt install ubuntu-unity-desktop --no-install-recommends
```

The minimum installation is suitable for testing, and having the bare minimum, older hardware would benefit from this version. Overall, the size is 76MB to download, and 280MB additional space is required afterward.
Standard Installation:
```

sudo apt install ubuntu-unity-desktop
```

The standard Unity installation is the most recommended for the average desktop user that wants a balance system. Overall, the size is 250MB to download, and 820MB additional space is required afterward.
Full Installation:
```

sudo apt install ubuntu-unity-desktop --install-suggests
```

This comes with everything naturally being a complete installation, but it will add bloat, affecting older systems without enough resources.

---

### Post by cigtoxdoc on 2022-04-06
Thank you.  I had already tried your suggestion.  A "sad computer icon comes up.  Underneath the first line of text reads, "Oh no! Something has gone wrong." The second line of text reads, "A problem has occurred and the system can't recover.  All extensions have been disabled as a precaution." Underneath that is a box marked, "Log out"

John

---

### Post by #&amp;thj^% on 2022-04-06
Yep all that was clear enough, but you never said you tried again, with: "install --reinstall"
EDIT: as a last resort you may have to rid the corrupt install:
```
sudo apt autoremove '^unity' --purge
```
there will be no doubt left over stuff to contend with,** so use at your own peril. **;)
Then again try reinstall "Unity"
BTW you may be a little early for Unity on 22.04 >>supported here: [https://discourse.ubuntu.com/t/testing-unity-session-on-ubuntu-21-10/23250](https://discourse.ubuntu.com/t/testing-unity-session-on-ubuntu-21-10/23250)
I had to see.
I can't reproduce your problem, fresh install xfce4-22.04 not updated yet, I went straight to install:
 ```
 sudo apt install ubuntu-unity-desktop
```
Restarted and:
```
 inxi -Fz
System:
  Kernel: 5.15.0-25-generic x86_64 bits: 64 Desktop: Unity 7.5.1
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Kvm System: QEMU product: Standard PC (Q35 + ICH9, 2009)
    v: pc-q35-6.2 serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: ArchLinux 1.16.0-1
    date: 04/01/2014
CPU:
  Info: 4x 1-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: SMP cache: L2: 4x 512 KiB (2 MiB)
  Speed (MHz): avg: 2994 min/max: N/A cores: 1: 2994 2: 2994 3: 2994
    4: 2994
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel
  Display: x11 server: X.Org v: 1.20.14 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa gpu: qxl note:  X driver n/a
    resolution: 1024x768~60Hz
  OpenGL: renderer: llvmpipe (LLVM 13.0.1 256 bits) v: 4.5 Mesa 22.0.0
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Red Hat Virtio network driver: virtio-pci
  IF-ID-1: enp1s0 state: up speed: -1 duplex: unknown mac: <filter>
RAID:
  Device-1: bpool type: zfs status: ONLINE level: linear raw: size: 1.12 GiB
    free: 803 MiB zfs-fs: size: 1023.9 MiB free: 675.3 MiB
  Components: Online: N/A
  Device-2: rpool type: zfs status: ONLINE level: linear raw: size: 22 GiB
    free: 15.6 GiB zfs-fs: size: 21.31 GiB free: 14.98 GiB
  Components: Online: N/A
Drives:
  Local Storage: total: raw: 25 GiB usable: 47.31 GiB used: 5.95 GiB (12.6%)
  ID-1: /dev/vda model: N/A size: 25 GiB
Partition:
  ID-1: / size: 19.37 GiB used: 4.39 GiB (22.7%) fs: zfs
    logical: rpool/ROOT/ubuntu_d2r0c4
  ID-2: /boot size: 915.9 MiB used: 240.6 MiB (26.3%) fs: zfs
    logical: bpool/BOOT/ubuntu_d2r0c4
  ID-3: /boot/efi size: 512 MiB used: 15.9 MiB (3.1%) fs: vfat
    dev: /dev/vda2
  ID-4: /var/log size: 14.98 GiB used: 2.8 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_d2r0c4/var/log
Swap:
  ID-1: swap-1 type: partition size: 1.13 GiB used: 0 KiB (0.0%)
    dev: /dev/vda3
Sensors:
  Message: No sensor data found. Is lm-sensors configured?
Info:
  Processes: 325 Uptime: 1m Memory: 3.83 GiB used: 2.04 GiB (53.3%)
  Shell: Bash inxi: 3.3.13

```

---

### Post by cigtoxdoc on 2022-04-06
Thank you for your help and advice.  It appears that ubuntu-unity-desktop is not ready for 22.04.  Is there place where I can give my feedback?

John

---

### Post by #&amp;thj^% on 2022-04-06
It worked for me, >> see my last post for support and suggestions.(the link provided)

---

### Post by cigtoxdoc on 2022-04-06
Thank you for your help.

Shown below is the output of inxi -Fz for PC I am working on.  I still get the same "sad face" screen when I try to login as Unity.  I thought about removing Gnome 42.  However, synaptic wants to take evolution down with it.  Evoultion is mission critical.  I have it running on other PC's so that would not be fatal, and all accounts are IMAP.  I have followed your instructions as listed above. Perhaps I am not daring enough.  If all else fails, I reboot into Win 10.  Data files are on a partition that works for both ubuntu and win 10 and outlook does the email, and it get a working bluetooth speaker that does work with ubuntu.

```
System:
  Kernel: 5.15.0-25-generic x86_64 bits: 64 Desktop: GNOME 42.0
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Desktop System: MSI product: MS-7846 v: 1.0
    serial: <superuser required>
  Mobo: MSI model: CSM-B85M-P32 (MS-7846) v: 1.0
    serial: <superuser required> BIOS: American Megatrends v: 2.6
    date: 07/19/2014
CPU:
  Info: quad core model: Intel Core i7-4770K bits: 64 type: MT MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 2701 min/max: 800/3900 cores: 1: 2701 2: 2701 3: 2701
    4: 2700 5: 2701 6: 2702 7: 2704 8: 2703
Graphics:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics
    driver: i915 v: kernel
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1200~60Hz
  OpenGL: renderer: Mesa Intel HD Graphics 4600 (HSW GT2)
    v: 4.6 Mesa 22.0.1
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    driver: snd_hda_intel
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    driver: snd_hda_intel
  Device-3: Jieli UACDemoV1.0 type: USB
    driver: hid-generic,snd-usb-audio,usbhid
  Sound Server-1: ALSA v: k5.15.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Bluetooth:
  Device-1: Cambridge Silicon Radio Bluetooth Dongle (HCI mode) type: USB
    driver: btusb
  Report: hciconfig ID: hci0 state: up address: <filter> bt-v: 2.1
Drives:
  Local Storage: total: 447.13 GiB used: 15.34 GiB (3.4%)
  ID-1: /dev/sda vendor: Intel model: SSDSC2BP480G4 size: 447.13 GiB
Partition:
  ID-1: / size: 47.04 GiB used: 15.34 GiB (32.6%) fs: ext4 dev: /dev/sda10
  ID-2: /boot/efi size: 512 MiB used: 5.3 MiB (1.0%) fs: vfat
    dev: /dev/sda11
Swap:
  ID-1: swap-1 type: partition size: 9.79 GiB used: 0 KiB (0.0%)
    dev: /dev/sda8
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 258 Uptime: 14m Memory: 15.47 GiB used: 1.32 GiB (8.5%)
  Shell: Bash inxi: 3.3.13
john@john-MS-7846:~$
```

---

### Post by deadflowr on 2022-04-07
I'm assuming you use the lightdm display manager to login with.
If you switch to gdm3 does it do the same stuff?
> Thank you. I had already tried your suggestion.
Not helpful when I gave multiple suggestions.
It's hard to know which.



Edit: Forgot to mention I too ran an upgrade from 21.10 to 22.04 running unity
and all works as expected.
I even switched display managers as a check on that and unity runs fine with both.

Also...
Thinking it over a little have you tried creating test user to see if that user can log into unity?
Sometimes issues are on the user side and not on the software side.
But maybe you mentioned you tried that and I simply missed it.

---

### Post by cigtoxdoc on 2022-04-07
Thank you for your suggestion.

I tried setting up another user (as an administrator). Still, choice of unity on login resulted in another "sad face".  Tried removing gnome 42. Had to get that back using the terminal.  Everything I tried didn't give me unity.  One blessing.  What ever happened when I reload gnome, made my Bluetooth speaker work.  Perhaps by the time final release of 22.04 is avialable, the "unity problem" will be solved.  When I changed lightdm to gdm3, I did not get a choice of gmome, ubuntu, or unity,

---

### Post by grahammechanical on 2022-04-07
I know this thread is about using Unity 7 with Ubuntu 22.04 but the OP has a dislike of Gnome shell putting icons for partitions (drives) in the Dock (Launcher). These icons can be removed.

System Settings>Appearance>Configure Dock Behaviour. There are two sliders = Show Volumes and Devices as well as Show Trash. There are two check boxes = Include Unmounted Devices as well as Include Network Volumes.

Regards

---

### Post by cigtoxdoc on 2022-04-08
Thank you for your suggestion.  It was excellent and solved the immediate problem.  John

---

