---
title: "New ISO allows Full and Minimal install"
date: 2023-09-15
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-09-15
I installed from today ISO and it WORKS!

---

### Post by Rubi1200 on 2023-09-18
Hi,

Will test it and let you know my results.

Thanks.

---

### Post by #&amp;thj^% on 2023-09-18
Rubi1200 I'm using this one now:20230918/
Link: [https://cdimage.ubuntu.com/daily-live/](https://cdimage.ubuntu.com/daily-live/)
Never Mind saw your recent edit.

---

### Post by Rubi1200 on 2023-09-18
I tried the daily build for Xubuntu and here are some observations:

1. I had to start in safe graphics mode (admittedly this is a rather old netbook)

2. during initial startup the logo shows 23.04 but at installation, choosing where to install, it says 23.10

3. there was no screen to choose between a full or minimal install

I will try the build from the link provided by 1fallen tomorrow and report back.

Hope this helps.

---

### Post by #&amp;thj^% on 2023-09-18
For Xubuntu minimal :[https://cdimage.ubuntu.com/xubuntu/daily-minimal/current/](https://cdimage.ubuntu.com/xubuntu/daily-minimal/current/)
His link was for Gnome,  corradoventu is a Gnome user. :)
Here ya go:
```
inxi -SFzz
System:
  Kernel: 6.5.0-5-generic arch: x86_64 bits: 64 Desktop: Xfce v: 4.18.1
    Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Kvm System: QEMU product: Standard PC (Q35 + ICH9, 2009) v: pc-q35-8.1
    serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A UEFI: EDK II v: N/A date: 2/2/2022
CPU:
  Info: 4x 1-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: SMP cache: L2: 4x 512 KiB (2 MiB)
  Speed (MHz): avg: 2994 min/max: N/A cores: 1: 2994 2: 2994 3: 2994 4: 2994
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa dri: swrast gpu: qxl
    resolution: 1024x768~60Hz
  API: OpenGL v: 4.5 Mesa 23.1.7-1ubuntu1 renderer: llvmpipe (LLVM 15.0.7
    256 bits)
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  API: ALSA v: k6.5.0-5-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active
Network:
  Device-1: Red Hat Virtio 1.0 network driver: virtio-pci
  Device-2: Red Hat Virtio 1.0 network driver: virtio-pci
  IF-ID-1: enp1s0 state: up speed: -1 duplex: unknown mac: <filter>
  IF-ID-2: enp7s0 state: up speed: -1 duplex: unknown mac: <filter>
RAID:
  Device-1: bpool type: zfs status: ONLINE level: linear raw: size: 1.62 GiB
    free: 1.51 GiB zfs-fs: size: 1.5 GiB free: 1.38 GiB
  Components: Online: 1: vda3
  Device-2: rpool type: zfs status: ONLINE level: linear raw: size: 25.5 GiB
    free: 23.2 GiB zfs-fs: size: 24.7 GiB free: 22.39 GiB
  Components: Online: 1: vda4
Drives:
  Local Storage: total: raw: 30 GiB usable: 28.7 GiB used: 2.45 GiB (8.5%)
  ID-1: /dev/vda model: N/A size: 30 GiB
Partition:
  ID-1: / size: 24.59 GiB used: 2.2 GiB (9.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_mjksxr
  ID-2: /boot size: 1.5 GiB used: 122 MiB (7.9%) fs: zfs
    logical: bpool/BOOT/ubuntu_mjksxr
  ID-3: /boot/efi size: 511 MiB used: 14.4 MiB (2.8%) fs: vfat
    dev: /dev/vda1
  ID-4: /var/log size: 22.39 GiB used: 3.6 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_mjksxr/var/log
Swap:
  ID-1: swap-1 type: partition size: 2 GiB used: 0 KiB (0.0%) dev: /dev/vda2
Sensors:
  Src: lm-sensors+/sys Message: No sensor data found using /sys/class/hwmon
    or lm-sensors.
Info:
  Processes: 331 Uptime: 2m Memory: total: 6 GiB available: 5.71 GiB
  used: 1.28 GiB (22.3%) Shell: Bash inxi: 3.3.29

```
I have to stay ahead for my semi-rolling production machine on zfs-root
Mike check the kernel.

---

### Post by MAFoElffen on 2023-09-18
@1fallen -- See it now. Downloading to install and test.

EDIT:
First crash... Was hopeful. See attachment. Bug Report: [https://bugs.launchpad.net/subiquity/+bug/2036482](https://bugs.launchpad.net/subiquity/+bug/2036482)

Entered into the QA Tracker...

Install as normal went fine, but even choosing to download updates during install, immediately after first boot, there was an update(?)

Excited so far...

---

### Post by Rubi1200 on 2023-09-19
> **1fallen said:**
> For Xubuntu minimal :[https://cdimage.ubuntu.com/xubuntu/daily-minimal/current/](https://cdimage.ubuntu.com/xubuntu/daily-minimal/current/)
His link was for Gnome,  corradoventu is a Gnome user.

Sadly, neither the link for Gnome or Xubuntu minimal worked for me. Probably has something to do with the old netbook I was using.

If I have time (and energy) there is another test laptop I can dust off which has better graphics and RAM.

Sorry I couldn't be of more help.

---

### Post by guiverc on 2023-09-19
> **Rubi1200 said:**
> I tried the daily build for Xubuntu and here are some observations:

2. during initial startup the logo shows 23.04 but at installation, choosing where to install, it says 23.10

Hope this helps.

Thanks for reporting that...  I followed up, and was just told

> 
-SwissBot/#xubuntu-devel- ::xubuntu-artwork:: Bump plymouth-text version number for mantic @ [https://github.com/Xubuntu/xubuntu-artwork/commit/b899e32a65e29cdc3337a283e442cdc989a3781f](https://github.com/Xubuntu/xubuntu-artwork/commit/b899e32a65e29cdc3337a283e442cdc989a3781f) (by bluesabre)

<bluesabre> guiverc: Whoops, that &#8593; will take care of the 23.04 text, on next upload.


(IRClog is wanted should appear here - [https://irclogs.ubuntu.com/2023/09/19/%23xubuntu-devel.html](https://irclogs.ubuntu.com/2023/09/19/%23xubuntu-devel.html))

---

### Post by #&amp;thj^% on 2023-09-19
Thanks guiverc !, I did notice the same.

---

### Post by Rubi1200 on 2023-09-19
> **guiverc said:**
> Thanks for reporting that...  I followed up

And thanks to you for reporting it, much appreciated.

Glad I was able to help in some small way.

---

### Post by pqwoerituytrueiwoq on 2023-09-19
installed kubuntu just now and i did not get/notice a minimal option, the install icon and installer do show 23.10

[https://cdimage.ubuntu.com/kubuntu/daily-live/current/](https://cdimage.ubuntu.com/kubuntu/daily-live/current/)

---

### Post by #&amp;thj^% on 2023-09-19
Bit the bullet full upgrade for zfs-root
```
inxi -S
System:
  Host: buntu-zfs Kernel: 6.5.0-5-generic arch: x86_64 bits: 64 Desktop: Xfce
    v: 4.18.1 Distro: Ubuntu 23.10 (Mantic Minotaur)

```
This was a bit touch and go:
```
 inxi -p
Partition:
  ID-1: / size: 224.7 GiB used: 3.88 GiB (1.7%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16
  ID-2: /boot size: 1.75 GiB used: 124.8 MiB (7.0%) fs: zfs
    logical: bpool/BOOT/ubuntu_oxrf16
  ID-3: /boot/efi size: 511 MiB used: 15 MiB (2.9%) fs: vfat
    dev: /dev/nvme1n1p1
  ID-4: /home/me size: 220.82 GiB used: 768 KiB (0.0%) fs: zfs
    logical: rpool/USERDATA/me_1jb4y8
  ID-5: /root size: 220.82 GiB used: 512 KiB (0.0%) fs: zfs
    logical: rpool/USERDATA/root_1jb4y8
  ID-6: /srv size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/srv
  ID-7: /usr/local size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/usr/local
  ID-8: /var/games size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/games
  ID-9: /var/lib size: 220.83 GiB used: 6.5 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/lib
  ID-10: /var/lib/AccountsService size: 220.82 GiB used: 128 KiB (0.0%)
    fs: zfs logical: rpool/ROOT/ubuntu_oxrf16/var/lib/AccountsService
  ID-11: /var/lib/NetworkManager size: 220.82 GiB used: 256 KiB (0.0%)
    fs: zfs logical: rpool/ROOT/ubuntu_oxrf16/var/lib/NetworkManager
  ID-12: /var/lib/apt size: 220.89 GiB used: 74.2 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/lib/apt
  ID-13: /var/lib/dpkg size: 220.85 GiB used: 28.9 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/lib/dpkg
  ID-14: /var/log size: 220.82 GiB used: 2.5 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/log
  ID-15: /var/mail size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/mail
  ID-16: /var/snap size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/snap
  ID-17: /var/spool size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/spool
  ID-18: /var/www size: 220.82 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_oxrf16/var/www
  ID-19: swap-1 size: 2 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/nvme1n1p2

```
I can't recommend a upgrade just yet though.
Still a bit rough.

---

### Post by Rubi1200 on 2023-09-20
Good news and some observations:

Used a laptop with better specs. and successfully installed the Ubuntu minimal version!

This was the daily build from September 19.

1. First time I tried to start the installer said a new version was available, so I let it download and install

2. However, when I got to the screen for Full or Minimal it would not go beyond that point

3. I rebooted choosing not to update the installer and this time everything just worked, including using the Manual partitioning option

4. Installation was smooth and fast and I do, indeed, have a very minimal install :-)

5. Two small(ish) annoyances to report: I had to write the image to the USB using dd. No other method worked because I kept on getting out of range errors
The other minor issue (for me at least) is that the GRUB menu does not show and, therefore, I was unable to select any other operating system. It just booted straight into 13.10

I hope some of this information is useful.

I have to say, I really like the new installer though there is one small thing that I believe needs to be changed. Namely, when it offers to install alongside it says them rather than specifying whether it is Windows or another Linux distribution. This could be confusing for some people.

UPDATE: GRUB not displaying was resolved by editing the file at /etc/default/grub so no worries.

But...the laptop is not shutting down correctly on 13.10 and I need to hold down the power key to force a shutdown. Does not happen with the other operating systems installed on the same laptop. Any ideas?

---

### Post by #&amp;thj^% on 2023-09-20
> **Rubi1200 said:**
> 
UPDATE: GRUB not displaying was resolved by editing the file at /etc/default/grub so no worries.

But...the laptop is not shutting down correctly on 13.10 and I need to hold down the power key to force a shutdown. Does not happen with the other operating systems installed on the same laptop. Any ideas?

What dose grub look like now Rubi1200?
and this might help looking in:
```
sudo journalctl -b -1 -xe
```
Until i changed some things like update-initramfs, I would get caught in a reboot to Bios every time. (Now all is proper)
```
sudo journalctl -b -1 -xe
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 576.
Sep 20 05:57:58 buntu-zfs systemd[1]: modprobe@efi_pstore.service: Deactivated >
&#9617;&#9617; Subject: Unit succeeded
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit modprobe@efi_pstore.service has successfully entered the 'dead' sta>
Sep 20 05:57:58 buntu-zfs systemd[1]: Finished modprobe@efi_pstore.service - Lo>
&#9617;&#9617; Subject: A start job for unit modprobe@efi_pstore.service has finished succe>
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit modprobe@efi_pstore.service has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 610.
Sep 20 05:57:58 buntu-zfs systemd[1]: modprobe@loop.service: Deactivated succes>
&#9617;&#9617; Subject: Unit succeeded
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit modprobe@loop.service has successfully entered the 'dead' state.
Sep 20 05:57:58 buntu-zfs systemd-journald[794]: Time spent on flushing to /va
```

---

### Post by Rubi1200 on 2023-09-20
@1fallen

I changed the following:

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE="menu" [COLOR=#ff0000]was set to hidden[/COLOR]
GRUB_TIMEOUT=10 [COLOR=#ff0000]was set to 0[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Here is the output of the command:

```
Sep 20 15:44:27 rubi-home systemd[1]: Reached target poweroff.target - System P>
&#9617;&#9617; Subject: A start job for unit poweroff.target has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit poweroff.target has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2170.
Sep 20 15:44:27 rubi-home systemd[1]: Shutting down.
Sep 20 15:44:27 rubi-home systemd-shutdown[1]: Syncing filesystems and block de>
Sep 20 15:44:28 rubi-home systemd-shutdown[1]: Sending SIGTERM to remaining pro>
Sep 20 15:44:28 rubi-home systemd-journald[232]: Received SIGTERM from PID 1 (s>
Sep 20 15:44:28 rubi-home systemd-journald[232]: Journal stopped

```

---

### Post by #&amp;thj^% on 2023-09-20
> **Rubi1200 said:**
> 
Here is the output of the command:

```
Sep 20 15:44:27 rubi-home systemd[1]: Reached target poweroff.target - System P>
&#9617;&#9617; Subject: A start job for unit poweroff.target has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit poweroff.target has finished successfully.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2170.
Sep 20 15:44:27 rubi-home systemd[1]: Shutting down.
Sep 20 15:44:27 rubi-home systemd-shutdown[1]: Syncing filesystems and block de>
Sep 20 15:44:28 rubi-home systemd-shutdown[1]: Sending SIGTERM to remaining pro>
Sep 20 15:44:28 rubi-home systemd-journald[232]: Received SIGTERM from PID 1 (s>
Sep 20 15:44:28 rubi-home systemd-journald[232]: Journal stopped

```
It looks like it just hangs on shutdown: (Journal stopped)
```
systemctl status poweroff.target
&#9675; poweroff.target - System Power Off
     Loaded: loaded (/lib/systemd/system/poweroff.target; disabled; preset: dis>
     Active: inactive (dead)
       Docs: man:systemd.special(7)
lines 1-4/4 (END)

```
I would be interested if this helps on your machine>>GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq"

---

### Post by Rubi1200 on 2023-09-20
> I would be interested if this helps on your machine>>GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq"

Unfortunately not. Also **acpi=force** did not help.

This is a fairly old laptop that still has legacy BIOS, if that makes a difference?

EDIT: ran apt update and apt upgrade, all good but no change with the shutdown issue.

Everything is running smoothly except for this one problem.

Should I remove that line from the GRUB file?

Is there anything else I can try?

---

### Post by #&amp;thj^% on 2023-09-20
> **Rubi1200 said:**
> Unfortunately not. Also **acpi=force** did not help.

Should I remove that line from the GRUB file?

Is there anything else I can try?

Yes I would, if not producing the desired result.
MAFoElffen filed a bug against 23.04 maybe add yourself to it or start another Bug Report.
I'll try and find the one MAFoElffen filed and include the link. (give me a minute)
I can't seem to find the link, I'll ask Mike to add it.
But for now will this shutdown your machine:
```
systemctl start poweroff.target
```

---

### Post by Dennis N on 2023-09-20
> But...the laptop is not shutting down correctly on 13.10 and I need to hold down the power key to force a shutdown
Did you wait the requisite 90 seconds before using the power key? It may then shut down itself.

---

### Post by Rubi1200 on 2023-09-20
> **Dennis N said:**
> Did you wait the requisite 90 seconds before using the power key? It may then shut down itself.

I waited more than 5 minutes before using the power key.

As mentioned in an earlier post, the problem seems to be only with 13.10. Both Windows and AntiX shut down normally without any need to intervene.

---

### Post by Rubi1200 on 2023-09-21
> **1fallen said:**
> But for now will this shutdown your machine:
```
systemctl start poweroff.target
```

Nope. Just hangs at the Ubuntu logo. I waited 5 minutes and then had to power off manually.

I looked at the journalctl command you suggested above but there was no useful information, just stuff about mtp-probe.

EDIT: I tried playing around with power management settings from within Ubuntu but no joy. Added apm=power_off to GRUB but that also had no effect.

---

### Post by Claus7 on 2023-09-21
Hello,

I suppose that the command: sudo shutdown -h, produces the same results? Actually I would try to press Ctrl+Alt+F1 or F2 e.t.c.. Doing so, I would abandon the graphical interface and move to virtual console. Then I would try the above commands and see if I get any error.

Just some ideas,
Regards!

---

### Post by Rubi1200 on 2023-09-21
> **Claus7 said:**
> Hello,

I suppose that the command: sudo shutdown -h, produces the same results? Actually I would try to press Ctrl+Alt+F1 or F2 e.t.c.. Doing so, I would abandon the graphical interface and move to virtual console. Then I would try the above commands and see if I get any error.

Just some ideas,
Regards!

Tried this both on Wayland and Xorg but no luck and no error messages visible.

Laptop starts what seems to be the shutdown process but instead of turning off there is nothing, not even any signs of disk activity.

After 3-5 minutes I need to manually power down.

Very curious, since everything else works really smoothly.

---

### Post by Claus7 on 2023-09-21
Hello,

I saw from previous post of yours that you have tried other OS and you are able to shutdown normally. Unfortunately I cannot add more help other than to add to the previous command the option now:
sudo shutdown -h now

I haven't tested it before, yet checking the help option of shutdown command I can see the following options:
-k 
--show

don't know if they are relevant, yet you could try and see if you will get any error.

Regards!

---

### Post by #&amp;thj^% on 2023-09-21
> **Rubi1200 said:**
> Nope. Just hangs at the Ubuntu logo. I waited 5 minutes and then had to power off manually.

I looked at the journalctl command you suggested above but there was no useful information, just stuff about mtp-probe.

EDIT: I tried playing around with power management settings from within Ubuntu but no joy. Added apm=power_off to GRUB but that also had no effect.

Rubi1200, this needs a bug report filed soon or it won't get a look at release time. :)

---

### Post by Rubi1200 on 2023-09-21
> **1fallen said:**
> Rubi1200, this needs a bug report filed soon or it won't get a look at release time. :)

Done (at least I hope this was correct, first time reporting a bug on Launchpad).

For reference:
[https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)

---

### Post by #&amp;thj^% on 2023-09-21
> **Rubi1200 said:**
> Done (at least I hope this was correct, first time reporting a bug on Launchpad).

For reference:
[https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)

Good Job, Very Helpful.
They will ask for more input from you, but at least it is reported now.

---

### Post by MAFoElffen on 2023-09-22
> **1fallen said:**
> Yes I would, if not producing the desired result.
MAFoElffen filed a bug against 23.04 maybe add yourself to it or start another Bug Report.
I'll try and find the one MAFoElffen filed and include the link. (give me a minute)
I can't seem to find the link, I'll ask Mike to add it.
But for now will this shutdown your machine:
```
systemctl start poweroff.target
```
Bug Report was: [https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136)
Started with Kernel 6.2.0-26 and has continued with kernels after that. Affects 22.04 with the HWE, and newer releases with those kernels and newer (on just some hardware).

Hey... I have had to search my emails to look for my past Bugs. If I go to launchpad and look at my bugs, many are missing from the list beyond 25 of them. Has this happened to any of you?

---

### Post by Rubi1200 on 2023-09-22
@MAFoElffen

This is the bug report I filed [https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)

I am thinking this might be something specific to 23.10?

I tried 22.04.3 and no issues with powering off. I want to try 23.04 later to see what happens and will report back here and also on Launchpad.

But...meantime, do you have anything I can try/test on 23.10 to discover what is preventing a full shutdown?

---

### Post by MAFoElffen on 2023-09-22
@Rubi1200

In the past (12.04, 18.04) this has happened and was about either ACPI, kernel or graphics drivers... 

[s]Does yours have an NVidia GPU?[/s] Is this a laptop or notebook? (Different power and ACPI options) [SIZE=1]*<<yes, looked at Bug Report>>*[/SIZE]
```

sudo lshw -C video -businfo
sudo lshw -C video | grep -e 'product\|driver'
acpi -V -i
sudo journalctl -b2 -g 'shutdown'

```
EDIT: If you logout of the GUI, and Select <Cntrl><Alt><F4> to get to VTTY4,... Log in to the console and do
```

sudo systemctl poweroff

```
That way, we see what happens with the graphics driver & desktop, not loaded to try to isolate that, and go directly to poweroff.target... Does it shutdown gracefully?

I see you tried 'acpi=off' and 'acpi=force' kernel parameters. Have you tried 'acpi=on'?

Maybe we should start a new thread, so we don't muddy up this one, and have it just concentrate on this issue.

EDIT: Read and subscribed to the Bug Report Notifications, and made a comment there.

Tip: When I file Bugs at lauchpad or upstream, if there is information contained in a threads somewhere, I add those thread links to cross-link the information. (On the bug report also...) I also ask people who have questions posted at AskUbuntu and on the Forum, to link between them. That way everyone is on the same page, and the left hand knows what the right hand is doing. That way someone doesn't ask you to try 'the same things over again', multiple times... That seems to help keep everyone on the same page.

---

### Post by Rubi1200 on 2023-09-22
Integrated Intel graphics.

Important update: see also bug report but I have installed and tested 22.4.03 and 23.04 and both shutdown and power off the laptop normally.

Therefore, at this point I can only conclude that there is something with 23.10 that is preventing normal shutdown?

---

### Post by Rubi1200 on 2023-09-22
@MAFoElffen

I just saw your edits in post #30.

Let me test and get back to you on those points.

---

### Post by Rubi1200 on 2023-09-22
@MAFoElffen
> sudo systemctl poweroff
That way, we see what happens with the graphics driver & desktop, not loaded to try to isolate that, and go directly to poweroff.target... Does it shutdown gracefully?


I see you tried 'acpi=off' and 'acpi=force' kernel parameters. Have you tried 'acpi=on'?


Neither option worked.

I updated the bug report with this information and also linked to this thread.

---

### Post by #&amp;thj^% on 2023-09-22
This iis what I've found so far, my reboot to bios was fixed from first upgrade (Not Live installer) to boot with:
```
 sudo update-initramfs -c -u
update-initramfs: Generating /boot/initrd.img-6.5.0-5-generic
I: The initramfs will attempt to resume from /dev/nvme1n1p2
I: (UUID=37368987-6d99-4295-92bf-5829ed87b6f1)
I: Set the RESUME variable to override this.

```
So those flags discription, 
[list]
[*]-c  This mode creates a new initramfs
[*]-u  This mode updates an existing initramfs.[/list]
I was lucky enough not to create the initramfs for a specific kernel, some have had to.
I got very curious about why that worked for me, long story short:
```
 /etc/initramfs-tools/hooks
amd64_microcode  cryptroot-unlock    intel_microcode  thermal
console_setup    dhcpcd              kbd              thin-provisioning-tools
cryptgnupg       dmsetup             klibc-utils      udev
cryptgnupg-sc    fixrtc              kmod             zdev
cryptkeyctl      framebuffer         lvm2             zfs
cryptopensc      framebuffer-nvidia  ntfs_3g          zfsunlock
cryptpassdev     fsck                plymouth         zz-busybox-initramfs
cryptroot        fuse                resume

```
My Unit is a AMD Ryzen 5 4600H, but I was lacking amd64_microcode, after the the generation from initramfs it now shows. (I would have filed a bug but I can't. (Please don't ask why it pisses me off to no end) :P
Still curious so i looked in:
```
#!/bin/sh
# intel-microcode initramfs-tools hook script version 3
# Copyright (C) 2012-2016 Henrique de Moraes Holschuh <hmh@debian.org>
# Released under the GNU GPL v2 or later license
#
# Generates a copy of the Intel microcode (by default tailored to the
# running system), and installs it in the early initramfs.
#
# iucode_tool v1.0 or later is required.
#

PREREQ=""
IUCODE_CONFIG=/etc/default/intel-microcode

prereqs()
{
   echo "$PREREQ"
}

case $1 in
prereqs)
   prereqs
   exit 0
   ;;
esac

. /usr/share/initramfs-tools/hook-functions

verbose()
{
	if [ "${verbose}" = "y" ] ; then
		echo "intel-microcode: $*"
	fi
	:
}

if [ "${verbose}" = "y" ] ; then
	IUCODE_TOOL_OPTIONS="-l"
else
	IUCODE_TOOL_OPTIONS="-q"
fi

IUCODE_TOOL=$(command -v iucode_tool)
if [ -z "${IUCODE_TOOL}" ] && [ -x /usr/sbin/iucode_tool ] ; then
	IUCODE_TOOL=/usr/sbin/iucode_tool
fi

IUCODE_FW_DIR=/lib/firmware/intel-ucode
if [ "$MODULES" = "most" ]; then
	IUCODE_TOOL_INITRAMFS=early
	IUCODE_TOOL_SCANCPUS=no
else
	IUCODE_TOOL_INITRAMFS=auto
	IUCODE_TOOL_SCANCPUS=yes
fi
IUCODE_TOOL_EXTRA_OPTIONS=

[ -r ${IUCODE_CONFIG} ] && . ${IUCODE_CONFIG}

[ -z "${IUCODE_TOOL_INITRAMFS}" ] && IUCODE_TOOL_INITRAMFS=no

case "${IUCODE_TOOL_INITRAMFS}" in
    no|0)
	verbose "intel-microcode: disabled by ${IUCODE_CONFIG}"
	exit 0
	;;
    auto|early)
	;;
    yes|1)
	IUCODE_TOOL_INITRAMFS=early
	echo "W: intel-microcode: initramfs mode not supported, using early initramfs mode" >&2
	;;
    *)
	echo "E: intel-microcode: invalid IUCODE_TOOL_INITRAMFS, using automatic mode" >&2
	IUCODE_TOOL_INITRAMFS=auto
esac

# don't do anything unless there's an Intel processor in the system in auto mode
if [ "${IUCODE_TOOL_INITRAMFS}" = "auto" ] ; then
	grep -q "^vendor_id[[:blank:]]*:[[:blank:]]*.*GenuineIntel" /proc/cpuinfo || {
		verbose "no Intel processors detected, nothing to do"
		exit 0
	}
fi

# we require iucode_tool, but something is broken
if [ ! -x "${IUCODE_TOOL}" ] ; then
	echo "E: intel-microcode: cannot run iucode_tool!" >&2
	exit 0
fi

# Blacklist all kernel versions before v3.10, as they don't support early
# initramfs mode.
#
# This doesn't blacklist early 3.10 kernels in the LTS branches, we don't have
# enough information at the initramfs-tools layer, due to the way Debian and
# Ubuntu version kernel packages.
if dpkg --compare-versions "${version}" lt 3.10 ; then
       echo "E: intel-microcode: unsupported kernel version!" >&2
       exit 0
fi

if [ "${IUCODE_TOOL_SCANCPUS}" != "yes" ] ; then
	verbose "adding microcode for either all or selected Intel processor models"
else
	verbose "adding microcode for currently online and selected Intel processors"
	grep -q cpu/cpuid /proc/devices || modprobe -q cpuid
	IUCODE_TOOL_OPTIONS="${IUCODE_TOOL_OPTIONS} --scan-system"
fi

# paranoia
[ -z "${DESTDIR}" ] && {
	echo "E: intel-microcode: DESTDIR empty!" >&2
	exit 1
}
[ -z "${IUCODE_FW_DIR}" ] && {
	echo "E: intel-microcode: IUCODE_FW_DIR empty!" >&2
	exit 1
}

# include the microcode module in the initramfs for logging purposes, but
# ensure it will have no microcode data files to load.  This is also a safety
# net: we don't want it to be acidentally loaded outside the initramfs.
#
# This shouldn't be expensive, as the in-kernel firmware loader is quite
# fast at detecting missing data files and doesn't wait for them.
#
# note: force_load will load a blacklisted module. We depend on that behavior.
#
# For 4.4 and later kernels, the microcode driver cannot be a module and will
# be built-in.
dpkg --compare-versions "${version}" lt 4.4 && {
    [ -d "${DESTDIR}${IUCODE_FW_DIR}" ] && rm -fr "${DESTDIR}${IUCODE_FW_DIR}"

    manual_add_modules microcode && {
        # force_load has broken semanthics when the .ko file is missing
        find "${DESTDIR}/${MODULESDIR}" -type f -print | grep -qc '/microcode\.ko$' && {
            verbose "modular microcode driver detected"
            force_load microcode
        }
    }
}

# generate early initramfs image and prepend
verbose "using early initramfs microcode update mode..."
EFW=$(mktemp "${TMPDIR:-/var/tmp}/mkinitramfs-EFW_XXXXXXXXXX") || {
	echo "E: intel-microcode: cannot create temporary file" >&2
	exit 1
    }
( find /usr/share/misc -maxdepth 1 -type f -name 'intel-microcode*' -print0 ;
  find "${IUCODE_FW_DIR}" -maxdepth 0 -type d -print0 ) 2>/dev/null \
| xargs -0 -r -x ${IUCODE_TOOL} ${IUCODE_TOOL_OPTIONS} \
		--write-earlyfw="${EFW}" --overwrite \
		${IUCODE_TOOL_EXTRA_OPTIONS} \
&& prepend_earlyinitramfs "${EFW}" && {
	rm "${EFW}"
	exit 0
}

# usually we get here when initramfs-tools is missing prepend_earlyinitramfs()
# or when iucode_tool does not support --write-earlyfw, i.e. when old versions
# of these tools are installed.

rm "${EFW}" || true

echo "E: intel-microcode: failed to create or prepend the early initramfs to the initramfs" >&2

:

```
This is interesting:
```
# usually we get here when initramfs-tools is missing prepend_earlyinitramfs()
# or when iucode_tool does not support --write-earlyfw, i.e. when old versions
# of these tools are installed.

rm "${EFW}" || true

```
This is from amd64_microcode:
```
#!/bin/sh
# amd64-microcode initramfs-tools hook script
# Copyright (C) 2012-2016 Henrique de Moraes Holschuh <hmh@debian.org>
# Released under the GPL v2 or later license
#
# Generates a copy of the minimal microcode for all AMD processors
# and installs it to the early initramfs
```
Which makes sense to me why *mine* booted to Bios and not the system.

---

### Post by MAFoElffen on 2023-09-22
@1fallen --
I'll take a look & play with the code of that when I get back home from Salmon fishing tonight. (LOL)

If I find something, I'll post a patch on the Bug Reports and give you credit for the hints. That might P@#$ someone off, but keep you in the lime-light in a good (valued) perspective. Maybe they will rethink your ban there. LOL

---

### Post by #&amp;thj^% on 2023-09-22
> **MAFoElffen said:**
>  Maybe they will rethink your ban there. LOL
Good then i can start my torment on popey again....:lolflag:
Alan you know i'm just tugging your leg

---

### Post by Rubi1200 on 2023-09-23
Ran apt update and apt upgrade today but no improvement.

Does the attached log output offer any clues?

---

### Post by Paddy Landau on 2023-09-23
> **Rubi1200 said:**
> … I need to hold down the power key to force a shutdown.
For future note, you probably want to use REISUB (restart) or REISUO (power down) to force a clean shut-down, rather than holding down the power key.

Canonical has disabled all functions bar SUB, so REI are disabled, but you can re-enable them.

[LIST]
[*]Edit [FONT=courier new]/etc/sysctl.d/10-magic-sysrq.conf[/FONT] and change the value of [FONT=courier new]kernel.sysrq[/FONT] to 244.
[*]Register the change:
```
sudo sysctl --load /etc/sysctl.d/10-magic-sysrq.conf
```
[*]Unfortunately, you have to reboot before the new setting takes effect.
[/LIST]

---

### Post by MAFoElffen on 2023-09-23
I looked at the syslog extract. Didn't see any magic there. But I think it may have been a problem with the filter you used for the extract. The problem with looking at syslog, is that it stops writing at a certain point in the shutdown process, whereas journelctl, writes longer in that process... That is what I use to diagnose shutdown problems.

Please try:
```

journalctl --boot=2 --grep='systemd' | tail -n 200 | sort --reverse

```

---

### Post by Rubi1200 on 2023-09-23
Output of the command is in the attached zip file.

I hope there is something there of use.

Appreciate the efforts :-)

---

### Post by #&amp;thj^% on 2023-09-23
> **Rubi1200 said:**
> Output of the command is in the attached zip file.

I hope there is something there of use.

Appreciate the efforts :-)

That's ugly, this is a mess:
```
Sep 20 14:44:36 rubi-home systemd[1]: systemd-machine-id-commit.service - Commit a transient machine-id on disk was skipped because of an unmet condition check (ConditionPathIsMountPoint=/etc/machine-id).
Sep 20 14:44:36 rubi-home systemd[1]: Starting systemd-binfmt.service - Set Up Additional Binary Formats...
```
This:
```
Sep 20 14:55:00 rubi-home systemd[1]: Closed systemd-oomd.socket - Userspace Out-Of-Memory (OOM) Killer Socket.
```
There is a lot of cycles that looks like it keep re spawning.
I'm on Arch right now so I won't show  mine until I'm finished with my session here.
I wouldn't mind seeing this:
```
journalctl --boot=2 --grep='systemd' | tail -n 200 | sort --reverse | grep successfully
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-zram-setup@zram0.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-update-utmp.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-update-done.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-tmpfiles-setup.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-tmpfiles-setup-dev.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-tmpfiles-setup-dev-early.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-sysusers.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-remount-fs.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-reboot.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-modules-load.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-journal-catalog-update.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-backlight@leds:platform::kbd_backlight.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-backlight@backlight:nvidia_0.service: Deactivated successfully.
Sep 18 10:08:59 crystal-arch systemd[1]: systemd-backlight@backlight:amdgpu_bl1.service: Deactivated successfully.
Sep 18 10:08:58 crystal-arch systemd[1]: systemd-user-sessions.service: Deactivated successfully.
Sep 18 10:08:58 crystal-arch systemd[1]: systemd-sysctl.service: Deactivated successfully.
Sep 18 10:08:58 crystal-arch systemd[1]: systemd-coredump.socket: Deactivated successfully.
Sep 18 10:08:58 crystal-arch systemd[1]: systemd-ask-password-wall.path: Deactivated successfully.
Sep 18 10:08:58 crystal-arch systemd[1]: systemd-ask-password-console.path: Deactivated successfully.
Sep 18 10:08:57 crystal-arch systemd[1]: systemd-random-seed.service: Deactivated successfully.
Sep 18 10:08:57 crystal-arch systemd[1]: systemd-logind.service: Deactivated successfully.
Sep 18 10:08:56 crystal-arch systemd[1]: systemd-tmpfiles-clean.timer: Deactivated successfully.
Sep 18 10:08:56 crystal-arch systemd[1]: systemd-rfkill.socket: Deactivated successfully.
Sep 18 10:02:50 crystal-arch polkitd[585]: Operator of unix-session:2 successfully authenticated as unix-user:me to gain TEMPORARY authorization for action org.freedesktop.systemd1.manage-units for system-bus-name::1.85 [systemctl start firewalld] (owned by unix-user:me)
Sep 18 10:02:29 crystal-arch polkitd[585]: Operator of unix-session:2 successfully authenticated as unix-user:me to gain TEMPORARY authorization for action org.freedesktop.systemd1.manage-unit-files for system-bus-name::1.81 [systemctl enable firewalld] (owned by unix-user:me)
Sep 18 09:59:41 crystal-arch polkitd[585]: Operator of unix-session:2 successfully authenticated as unix-user:me to gain TEMPORARY authorization for action org.freedesktop.systemd1.manage-unit-files for system-bus-name::1.76 [systemctl enable apparmor] (owned by unix-user:me)
Sep 18 09:58:45 crystal-arch systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 18 09:52:24 crystal-arch systemd[1]: systemd-tmpfiles-clean.service: Deactivated successfully.
Sep 18 09:37:54 crystal-arch systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 18 09:37:29 crystal-arch systemd[1]: systemd-rfkill.service: Deactivated successfully.

```

---

### Post by MAFoElffen on 2023-09-23
Hmmm. All through that I kept seeing dbus messages for freedesktop where they were labeled as unconfined... ad a few warnings about failures after this (remebr this is in reverse order):
```

Sep 20 14:45:24 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:16 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activating service name='org.freedesktop.systemd1' requested by ':1.2' (uid=124 pid=1005 comm="/usr/libexec/gnome-session-binary --autostart /usr" label="unconfined")
Sep 20 14:45:16 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:16 rubi-home gnome-session[1005]: gnome-session-binary[1005]: WARNING: Could not check if unit gnome-session-wayland@gnome-login.target is active: Error calling StartServiceByName for org.freedesktop.systemd1: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:13 rubi-home gnome-session-binary[1005]: WARNING: Could not check if unit gnome-session-wayland@gnome-login.target is active: Error calling StartServiceByName for org.freedesktop.systemd1: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:08 rubi-home dbus-daemon[990]: [session uid=124 pid=990] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-permission-store.service' requested by ':1.9' (uid=124 pid=1008 comm="/usr/libexec/xdg-document-portal" label="unconfined")
Sep 20 14:45:07 rubi-home dbus-daemon[990]: [session uid=124 pid=990] Successfully activated service 'org.freedesktop.systemd1'
Sep 20 14:45:07 rubi-home dbus-daemon[990]: [session uid=124 pid=990] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.2' (uid=124 pid=972 comm="/usr/bin/snap run snapd-desktop-integration" label="unconfined")
Sep 20 14:45:07 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.26' (uid=124 pid=971 comm="/usr/bin/pipewire -c filter-chain.conf" label="unconfined")

```
It is running Wayland. Could you try that again on Xorg?

DEDIT:
Hmmm. We could always look at the obvious:
```

journalctl -p 4 -x --boot=2 -r --no-pager > ~/journal_errors-00.log

```
Which just sorts out the priority"notice" and higher (notice, warning, error, critical, alert and emergency), in 2 boots back, reverse order, adding any known explanations... and output it to a file. That way we don't miss anything there. If it is too big to upload, then add "--lines=200" to the end.

---

### Post by Rubi1200 on 2023-09-23
@1fallen

Here is the output of your command:

```
sudo journalctl --boot=2 --grep='systemd' | tail -n 200 | sort --reverse | grep successfully
Sep 20 14:55:00 rubi-home systemd[1]: systemd-update-utmp.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-tmpfiles-setup.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-tmpfiles-setup-dev.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-timesyncd.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-sysusers.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-sysctl.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-resolved.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-remount-fs.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-reboot.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-oomd.socket: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-modules-load.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-binfmt.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-backlight@backlight:acpi_video0.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-ask-password-wall.path: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-ask-password-plymouth.path: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dtmpfiles\x2dsetup\x2ddev.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dsysusers.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dsysctl.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dresolved.service.mount: Deactivated successfully.
Sep 20 14:54:59 rubi-home systemd[1]: systemd-user-sessions.service: Deactivated successfully.
Sep 20 14:54:59 rubi-home systemd[1]: systemd-oomd.service: Deactivated successfully.
Sep 20 14:54:58 rubi-home systemd[1]: systemd-random-seed.service: Deactivated successfully.
Sep 20 14:54:58 rubi-home systemd[1]: systemd-logind.service: Deactivated successfully.
Sep 20 14:54:57 rubi-home systemd[1]: systemd-tmpfiles-clean.timer: Deactivated successfully.
Sep 20 14:54:57 rubi-home systemd[1]: systemd-rfkill.socket: Deactivated successfully.
Sep 20 14:52:46 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:50:33 rubi-home systemd[1]: systemd-timedated.service: Deactivated successfully.
Sep 20 14:48:12 rubi-home systemd[1]: systemd-localed.service: Deactivated successfully.
Sep 20 14:48:12 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:46:08 rubi-home systemd[1]: systemd-localed.service: Deactivated successfully.
Sep 20 14:46:08 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:45:34 rubi-home systemd[1]: systemd-update-utmp-runlevel.service: Deactivated successfully.
Sep 20 14:45:33 rubi-home systemd[1]: systemd-timedated.service: Deactivated successfully.
Sep 20 14:45:25 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
```

---

### Post by Rubi1200 on 2023-09-23
> **MAFoElffen said:**
> Hmmm. All through that I kept seeing dbus messages for freedesktop where they were labeled as unconfined... ad a few warnings about failures after this (remebr this is in reverse order):
[
It is running Wayland. Could you try that again on Xorg?

Just to clarify, do you mean the same command as before but on Xorg?

I am currently in a Wayland session.

---

### Post by Rubi1200 on 2023-09-23
Okay, this is the output  when logged in to a Xorg session:

```
Sep 20 14:55:01 rubi-home systemd-journald[230]: Received SIGTERM from PID 1 (systemd-shutdow).
Sep 20 14:55:00 rubi-home umount[4297]: umount: /run/credentials/systemd-tmpfiles-setup.service: no mount point specified.
Sep 20 14:55:00 rubi-home systemd[1]: Unmounting run-credentials-systemd\x2dtmpfiles\x2dsetup\x2ddev.service.mount - /run/credentials/systemd-tmpfiles-setup-dev.service...
Sep 20 14:55:00 rubi-home systemd[1]: Unmounting run-credentials-systemd\x2dtmpfiles\x2dsetup.service.mount - /run/credentials/systemd-tmpfiles-setup.service...
Sep 20 14:55:00 rubi-home systemd[1]: Unmounting run-credentials-systemd\x2dsysusers.service.mount - /run/credentials/systemd-sysusers.service...
Sep 20 14:55:00 rubi-home systemd[1]: Unmounted run-credentials-systemd\x2dtmpfiles\x2dsetup\x2ddev.service.mount - /run/credentials/systemd-tmpfiles-setup-dev.service.
Sep 20 14:55:00 rubi-home systemd[1]: Unmounted run-credentials-systemd\x2dtmpfiles\x2dsetup.service.mount - /run/credentials/systemd-tmpfiles-setup.service.
Sep 20 14:55:00 rubi-home systemd[1]: Unmounted run-credentials-systemd\x2dsysusers.service.mount - /run/credentials/systemd-sysusers.service.
Sep 20 14:55:00 rubi-home systemd[1]: Unmounted run-credentials-systemd\x2dsysctl.service.mount - /run/credentials/systemd-sysctl.service.
Sep 20 14:55:00 rubi-home systemd[1]: Unmounted run-credentials-systemd\x2dresolved.service.mount - /run/credentials/systemd-resolved.service.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-update-utmp.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-tmpfiles-setup.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-tmpfiles-setup-dev.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-timesyncd.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-sysusers.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-sysctl.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-resolved.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-remount-fs.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-reboot.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-oomd.socket: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-modules-load.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-binfmt.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-backlight@backlight:acpi_video0.service: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-ask-password-wall.path: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: systemd-ask-password-plymouth.path: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: Stopping systemd-update-utmp.service - Record System Boot/Shutdown in UTMP...
Sep 20 14:55:00 rubi-home systemd[1]: Stopping systemd-timesyncd.service - Network Time Synchronization...
Sep 20 14:55:00 rubi-home systemd[1]: Stopping systemd-resolved.service - Network Name Resolution...
Sep 20 14:55:00 rubi-home systemd[1]: Stopping systemd-binfmt.service - Set Up Additional Binary Formats...
Sep 20 14:55:00 rubi-home systemd[1]: Stopping systemd-backlight@backlight:acpi_video0.service - Load/Save Screen Backlight Brightness of backlight:acpi_video0...
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-update-utmp.service - Record System Boot/Shutdown in UTMP.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-tmpfiles-setup.service - Create Volatile Files and Directories.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-tmpfiles-setup-dev.service - Create Static Device Nodes in /dev.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-timesyncd.service - Network Time Synchronization.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-sysusers.service - Create System Users.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-sysctl.service - Apply Kernel Variables.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-resolved.service - Network Name Resolution.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-remount-fs.service - Remount Root and Kernel File Systems.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-modules-load.service - Load Kernel Modules.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-binfmt.service - Set Up Additional Binary Formats.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-backlight@backlight:acpi_video0.service - Load/Save Screen Backlight Brightness of backlight:acpi_video0.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-ask-password-wall.path - Forward Password Requests to Wall Directory Watch.
Sep 20 14:55:00 rubi-home systemd[1]: Stopped systemd-ask-password-plymouth.path - Forward Password Requests to Plymouth Directory Watch.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dtmpfiles\x2dsetup\x2ddev.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dtmpfiles\x2dsetup.service.mount: Mount process exited, code=exited, status=32/n/a
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dtmpfiles\x2dsetup.service.mount: Failed with result 'exit-code'.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dsysusers.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dsysctl.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: run-credentials-systemd\x2dresolved.service.mount: Deactivated successfully.
Sep 20 14:55:00 rubi-home systemd[1]: Removed slice system-systemd\x2dbacklight.slice - Slice /system/systemd-backlight.
Sep 20 14:55:00 rubi-home systemd[1]: Finished systemd-reboot.service - System Reboot.
Sep 20 14:55:00 rubi-home systemd[1]: Closed systemd-oomd.socket - Userspace Out-Of-Memory (OOM) Killer Socket.
Sep 20 14:54:59 rubi-home systemd[1]: systemd-user-sessions.service: Deactivated successfully.
Sep 20 14:54:59 rubi-home systemd[1]: systemd-oomd.service: Deactivated successfully.
Sep 20 14:54:59 rubi-home systemd[1]: systemd-oomd.service: Consumed 1.586s CPU time.
Sep 20 14:54:59 rubi-home systemd[1]: Stopping systemd-user-sessions.service - Permit User Sessions...
Sep 20 14:54:59 rubi-home systemd[1]: Stopping systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer...
Sep 20 14:54:59 rubi-home systemd[1]: Stopped systemd-user-sessions.service - Permit User Sessions.
Sep 20 14:54:59 rubi-home systemd[1]: Stopped systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer.
Sep 20 14:54:59 rubi-home systemd[1519]: Finished systemd-exit.service - Exit the Session.
Sep 20 14:54:59 rubi-home dbus-daemon[604]: [system] Activation via systemd failed for unit 'dbus-org.freedesktop.nm-dispatcher.service': Transaction for NetworkManager-dispatcher.service/start is destructive (swap.img.swap has 'stop' job queued, but 'start' is included in transaction).
Sep 20 14:54:59 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.14' (uid=0 pid=770 comm="/usr/sbin/NetworkManager --no-daemon" label="unconfined")
Sep 20 14:54:58 rubi-home systemd[1]: systemd-random-seed.service: Deactivated successfully.
Sep 20 14:54:58 rubi-home systemd[1]: systemd-logind.service: Deactivated successfully.
Sep 20 14:54:58 rubi-home systemd[1]: Stopped systemd-random-seed.service - Load/Save OS Random Seed.
Sep 20 14:54:58 rubi-home systemd[1]: Stopped systemd-logind.service - User Login Management.
Sep 20 14:54:58 rubi-home dbus-daemon[604]: [system] Activation via systemd failed for unit 'colord.service': Transaction for colord.service/start is destructive (shutdown.target has 'start' job queued, but 'stop' is included in transaction).
Sep 20 14:54:58 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.22' (uid=0 pid=915 comm="/usr/sbin/cupsd -l" label="/usr/sbin/cupsd (enforce)")
Sep 20 14:54:57 rubi-home systemd[1]: systemd-tmpfiles-clean.timer: Deactivated successfully.
Sep 20 14:54:57 rubi-home systemd[1]: systemd-rfkill.socket: Deactivated successfully.
Sep 20 14:54:57 rubi-home systemd[1]: Stopping systemd-random-seed.service - Load/Save OS Random Seed...
Sep 20 14:54:57 rubi-home systemd[1]: Stopping systemd-logind.service - User Login Management...
Sep 20 14:54:57 rubi-home systemd[1]: Stopped systemd-tmpfiles-clean.timer - Daily Cleanup of Temporary Directories.
Sep 20 14:54:57 rubi-home systemd[1]: Closed systemd-rfkill.socket - Load/Save RF Kill Switch Status /dev/rfkill Watch.
Sep 20 14:54:13 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.125' (uid=1000 pid=3272 comm="/usr/bin/gnome-terminal.real" label="unconfined")
Sep 20 14:52:46 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:51:42 rubi-home systemd[1]: Starting systemd-hostnamed.service - Hostname Service...
Sep 20 14:51:42 rubi-home systemd[1]: Started systemd-hostnamed.service - Hostname Service.
Sep 20 14:51:42 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.115' (uid=1000 pid=2991 comm="/usr/bin/nautilus --gapplication-service" label="unconfined")
Sep 20 14:50:33 rubi-home systemd[1]: systemd-timedated.service: Deactivated successfully.
Sep 20 14:50:13 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.90' (uid=1000 pid=2332 comm="/usr/libexec/tracker-miner-fs-3" label="unconfined")
Sep 20 14:50:03 rubi-home systemd[1]: Starting systemd-timedated.service - Time & Date Service...
Sep 20 14:50:03 rubi-home systemd[1]: Started systemd-timedated.service - Time & Date Service.
Sep 20 14:50:03 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.17' (uid=0 pid=748 comm="/usr/lib/snapd/snapd" label="unconfined")
Sep 20 14:48:43 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.105' (uid=1000 pid=2590 comm="/usr/bin/gnome-terminal.real" label="unconfined")
Sep 20 14:48:12 rubi-home systemd[1]: systemd-localed.service: Deactivated successfully.
Sep 20 14:48:12 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:47:54 rubi-home systemd[963]: Finished systemd-exit.service - Exit the Session.
Sep 20 14:47:49 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.90' (uid=1000 pid=2332 comm="/usr/libexec/tracker-miner-fs-3" label="unconfined")
Sep 20 14:47:45 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.89' (uid=1000 pid=2405 comm="gjs /usr/share/gnome-shell/extensions/ding@rasters" label="unconfined")
Sep 20 14:47:45 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Files' unit='tracker-miner-fs-3.service' requested by ':1.82' (uid=1000 pid=2309 comm="/usr/bin/nautilus --gapplication-service" label="unconfined")
Sep 20 14:47:44 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gtk' unit='xdg-desktop-portal-gtk.service' requested by ':1.67' (uid=1000 pid=2187 comm="/usr/libexec/xdg-desktop-portal" label="unconfined")
Sep 20 14:47:43 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activating service name='org.freedesktop.systemd1' requested by ':1.14' (uid=124 pid=1183 comm="/usr/libexec/gsd-sharing" label="unconfined")
Sep 20 14:47:42 rubi-home systemd[1]: Starting systemd-localed.service - Locale Service...
Sep 20 14:47:42 rubi-home systemd[1]: Started systemd-localed.service - Locale Service.
Sep 20 14:47:42 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' requested by ':1.99' (uid=1000 pid=1906 comm="/usr/libexec/gsd-keyboard" label="unconfined")
Sep 20 14:47:41 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook10' unit='evolution-addressbook-factory.service' requested by ':1.74' (uid=1000 pid=2248 comm="/usr/libexec/evolution-calendar-factory" label="unconfined")
Sep 20 14:47:40 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.80' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:40 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.34' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:40 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar8' unit='evolution-calendar-factory.service' requested by ':1.53' (uid=1000 pid=1876 comm="/usr/libexec/gnome-shell-calendar-server" label="unconfined")
Sep 20 14:47:40 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='ca.desrt.dconf' unit='dconf.service' requested by ':1.34' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:39 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.34' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:39 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gnome' unit='xdg-desktop-portal-gnome.service' requested by ':1.67' (uid=1000 pid=2187 comm="/usr/libexec/xdg-desktop-portal" label="unconfined")
Sep 20 14:47:38 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.34' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:38 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.portal.Desktop' unit='xdg-desktop-portal.service' requested by ':1.65' (uid=1000 pid=2183 comm="/snap/snapd-desktop-integration/83/usr/bin/snapd-d" label="snap.snapd-desktop-integration.snapd-desktop-integration (enforce)")
Sep 20 14:47:37 rubi-home systemd[1]: Starting systemd-hostnamed.service - Hostname Service...
Sep 20 14:47:37 rubi-home systemd[1]: Started systemd-hostnamed.service - Hostname Service.
Sep 20 14:47:37 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.34' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:37 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.34' (uid=1000 pid=1778 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:47:37 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gnome.evolution.dataserver.Sources5' unit='evolution-source-registry.service' requested by ':1.53' (uid=1000 pid=1876 comm="/usr/libexec/gnome-shell-calendar-server" label="unconfined")
Sep 20 14:47:36 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.82' (uid=1000 pid=1914 comm="/usr/libexec/gsd-rfkill" label="unconfined")
Sep 20 14:47:33 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.18' (uid=1000 pid=1721 comm="/usr/libexec/xdg-desktop-portal-rewrite-launchers" label="unconfined")
Sep 20 14:47:31 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-permission-store.service' requested by ':1.8' (uid=1000 pid=1567 comm="/usr/libexec/xdg-document-portal" label="unconfined")
Sep 20 14:47:30 rubi-home (systemd)[1519]: pam_unix(systemd-user:session): session opened for user rubi(uid=1000) by (uid=0)
Sep 20 14:47:30 rubi-home dbus-daemon[1551]: [session uid=1000 pid=1551] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.4' (uid=1000 pid=1534 comm="/usr/bin/snap run snapd-desktop-integration" label="unconfined")
Sep 20 14:47:22 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:46:08 rubi-home systemd[1]: systemd-localed.service: Deactivated successfully.
Sep 20 14:46:08 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:45:34 rubi-home systemd[1]: systemd-update-utmp-runlevel.service: Deactivated successfully.
Sep 20 14:45:34 rubi-home systemd[1]: Starting systemd-update-utmp-runlevel.service - Record Runlevel Change in UTMP...
Sep 20 14:45:34 rubi-home systemd[1]: Finished systemd-update-utmp-runlevel.service - Record Runlevel Change in UTMP.
Sep 20 14:45:33 rubi-home systemd[1]: systemd-timedated.service: Deactivated successfully.
Sep 20 14:45:33 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:32 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:28 rubi-home systemd[1]: Started systemd-hostnamed.service - Hostname Service.
Sep 20 14:45:27 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activating service name='org.freedesktop.systemd1' requested by ':1.14' (uid=124 pid=1183 comm="/usr/libexec/gsd-sharing" label="unconfined")
Sep 20 14:45:27 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:27 rubi-home systemd[1]: Starting systemd-hostnamed.service - Hostname Service...
Sep 20 14:45:27 rubi-home gsd-sharing[1183]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:27 rubi-home gsd-sharing[1183]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:27 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:27 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:27 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.42' (uid=124 pid=1190 comm="/usr/libexec/gsd-rfkill" label="unconfined")
Sep 20 14:45:26 rubi-home systemd[1]: Starting systemd-localed.service - Locale Service...
Sep 20 14:45:26 rubi-home systemd[1]: Started systemd-localed.service - Locale Service.
Sep 20 14:45:26 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:25 rubi-home systemd[1]: systemd-hostnamed.service: Deactivated successfully.
Sep 20 14:45:24 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.36' (uid=124 pid=1080 comm="/usr/bin/gnome-shell" label="unconfined")
Sep 20 14:45:16 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activating service name='org.freedesktop.systemd1' requested by ':1.2' (uid=124 pid=1005 comm="/usr/libexec/gnome-session-binary --autostart /usr" label="unconfined")
Sep 20 14:45:16 rubi-home /usr/libexec/gdm-wayland-session[1004]: dbus-daemon[1004]: [session uid=124 pid=1004] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:16 rubi-home gnome-session[1005]: gnome-session-binary[1005]: WARNING: Could not check if unit gnome-session-wayland@gnome-login.target is active: Error calling StartServiceByName for org.freedesktop.systemd1: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:13 rubi-home gnome-session-binary[1005]: WARNING: Could not check if unit gnome-session-wayland@gnome-login.target is active: Error calling StartServiceByName for org.freedesktop.systemd1: Process org.freedesktop.systemd1 exited with status 1
Sep 20 14:45:08 rubi-home dbus-daemon[990]: [session uid=124 pid=990] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-permission-store.service' requested by ':1.9' (uid=124 pid=1008 comm="/usr/libexec/xdg-document-portal" label="unconfined")
Sep 20 14:45:07 rubi-home dbus-daemon[990]: [session uid=124 pid=990] Successfully activated service 'org.freedesktop.systemd1'
Sep 20 14:45:07 rubi-home dbus-daemon[990]: [session uid=124 pid=990] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.2' (uid=124 pid=972 comm="/usr/bin/snap run snapd-desktop-integration" label="unconfined")
Sep 20 14:45:07 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.26' (uid=124 pid=971 comm="/usr/bin/pipewire -c filter-chain.conf" label="unconfined")
Sep 20 14:45:06 rubi-home (systemd)[963]: pam_unix(systemd-user:session): session opened for user gdm(uid=124) by (uid=0)
Sep 20 14:45:02 rubi-home systemd[1]: Starting systemd-user-sessions.service - Permit User Sessions...
Sep 20 14:45:02 rubi-home systemd[1]: Started systemd-timedated.service - Time & Date Service.
Sep 20 14:45:02 rubi-home systemd[1]: Finished systemd-user-sessions.service - Permit User Sessions.
Sep 20 14:45:01 rubi-home systemd[1]: Starting systemd-timedated.service - Time & Date Service...
Sep 20 14:45:01 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.17' (uid=0 pid=748 comm="/usr/lib/snapd/snapd" label="unconfined")
Sep 20 14:44:57 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.14' (uid=0 pid=770 comm="/usr/sbin/NetworkManager --no-daemon" label="unconfined")
Sep 20 14:44:56 rubi-home systemd[1]: Starting systemd-hostnamed.service - Hostname Service...
Sep 20 14:44:56 rubi-home systemd[1]: Started systemd-hostnamed.service - Hostname Service.
Sep 20 14:44:56 rubi-home NetworkManager[770]: <info>  [1695210296.5072] dns-mgr: init: dns=systemd-resolved rc-manager=unmanaged (auto), plugin=systemd-resolved
Sep 20 14:44:56 rubi-home dbus-daemon[604]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.14' (uid=0 pid=770 comm="/usr/sbin/NetworkManager --no-daemon" label="unconfined")
Sep 20 14:44:52 rubi-home rsyslogd[768]: imuxsock: Acquired UNIX socket '/run/systemd/journal/syslog' (fd 3) from systemd.  [v8.2306.0]
Sep 20 14:44:51 rubi-home systemd[1]: Started systemd-logind.service - User Login Management.
Sep 20 14:44:51 rubi-home systemd[1]: Finished systemd-backlight@backlight:acpi_video0.service - Load/Save Screen Backlight Brightness of backlight:acpi_video0.
Sep 20 14:44:50 rubi-home systemd[1]: systemd-pcrphase.service - TPM2 PCR Barrier (User) was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/StubPcrKernelImage-4a67b082-0a4c-41cf-b6c7-440b29bb8c4f).
Sep 20 14:44:50 rubi-home systemd[1]: Starting systemd-logind.service - User Login Management...
Sep 20 14:44:50 rubi-home systemd[1]: Starting systemd-backlight@backlight:acpi_video0.service - Load/Save Screen Backlight Brightness of backlight:acpi_video0...
Sep 20 14:44:50 rubi-home systemd[1]: Created slice system-systemd\x2dbacklight.slice - Slice /system/systemd-backlight.
Sep 20 14:44:50 rubi-home dbus-daemon[604]: [system] Successfully activated service 'org.freedesktop.systemd1'
Sep 20 14:44:49 rubi-home systemd[1]: networkd-dispatcher.service - Dispatcher daemon for systemd-networkd was skipped because no trigger condition checks were met.
Sep 20 14:44:49 rubi-home dbus-daemon[604]: [system] Activating systemd to hand-off: service name='org.freedesktop.PolicyKit1' unit='polkit.service' requested by ':1.3' (uid=0 pid=742 comm="/usr/libexec/power-profiles-daemon" label="unconfined")
Sep 20 14:44:43 rubi-home systemd[1]: systemd-pcrphase-sysinit.service - TPM2 PCR Barrier (Initialization) was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/StubPcrKernelImage-4a67b082-0a4c-41cf-b6c7-440b29bb8c4f).
Sep 20 14:44:43 rubi-home systemd[1]: Started systemd-tmpfiles-clean.timer - Daily Cleanup of Temporary Directories.
Sep 20 14:44:43 rubi-home systemd[1]: Started systemd-resolved.service - Network Name Resolution.
Sep 20 14:44:40 rubi-home systemd[1]: Listening on systemd-rfkill.socket - Load/Save RF Kill Switch Status /dev/rfkill Watch.
Sep 20 14:44:38 rubi-home systemd[1]: systemd-ask-password-console.path - Dispatch Password Requests to Console Directory Watch was skipped because of an unmet condition check (ConditionPathExists=!/run/plymouth/pid).
Sep 20 14:44:38 rubi-home systemd[1]: Starting systemd-update-utmp.service - Record System Boot/Shutdown in UTMP...
Sep 20 14:44:38 rubi-home systemd[1]: Starting systemd-timesyncd.service - Network Time Synchronization...
Sep 20 14:44:38 rubi-home systemd[1]: Starting systemd-resolved.service - Network Name Resolution...
Sep 20 14:44:38 rubi-home systemd[1]: Starting systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer...
Sep 20 14:44:38 rubi-home systemd[1]: Started systemd-timesyncd.service - Network Time Synchronization.
Sep 20 14:44:38 rubi-home systemd[1]: Started systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer.
Sep 20 14:44:38 rubi-home systemd[1]: Started systemd-ask-password-plymouth.path - Forward Password Requests to Plymouth Directory Watch.
Sep 20 14:44:38 rubi-home systemd[1]: Finished systemd-update-utmp.service - Record System Boot/Shutdown in UTMP.
Sep 20 14:44:37 rubi-home systemd[1]: Starting systemd-tmpfiles-setup.service - Create Volatile Files and Directories...
Sep 20 14:44:37 rubi-home systemd[1]: Started systemd-udevd.service - Rule-based Manager for Device Events and Files.
Sep 20 14:44:37 rubi-home systemd[1]: Finished systemd-tmpfiles-setup.service - Create Volatile Files and Directories.
Sep 20 14:44:37 rubi-home systemd[1]: Finished systemd-journal-flush.service - Flush Journal to Persistent Storage.
Sep 20 14:44:37 rubi-home systemd[1]: Finished systemd-binfmt.service - Set Up Additional Binary Formats.
Sep 20 14:44:36 rubi-home systemd[1]: systemd-machine-id-commit.service - Commit a transient machine-id on disk was skipped because of an unmet condition check (ConditionPathIsMountPoint=/etc/machine-id).
Sep 20 14:44:36 rubi-home systemd[1]: Starting systemd-binfmt.service - Set Up Additional Binary Formats...
Sep 20 14:44:36 rubi-home systemd[1]: proc-sys-fs-binfmt_misc.automount: Got automount request for /proc/sys/fs/binfmt_misc, triggered by 286 (systemd-binfmt)
Sep 20 14:44:35 rubi-home systemd[1]: Starting systemd-udevd.service - Rule-based Manager for Device Events and Files...
Sep 20 14:44:35 rubi-home systemd[1]: Starting systemd-tmpfiles-setup-dev.service - Create Static Device Nodes in /dev...
Sep 20 14:44:35 rubi-home systemd[1]: Finished systemd-tmpfiles-setup-dev.service - Create Static Device Nodes in /dev.
Sep 20 14:44:35 rubi-home systemd[1]: Finished systemd-sysusers.service - Create System Users.
Sep 20 14:44:35 rubi-home systemd[1]: Finished systemd-sysctl.service - Apply Kernel Variables.
Sep 20 14:44:34 rubi-home systemd[1]: Starting systemd-sysusers.service - Create System Users...
Sep 20 14:44:34 rubi-home systemd[1]: Starting systemd-sysctl.service - Apply Kernel Variables...
Sep 20 14:44:34 rubi-home systemd[1]: Starting systemd-journal-flush.service - Flush Journal to Persistent Storage...
Sep 20 14:44:34 rubi-home systemd[1]: Started systemd-journald.service - Journal Service.
Sep 20 14:44:34 rubi-home systemd[1]: Finished systemd-udev-trigger.service - Coldplug All udev Devices.
Sep 20 14:44:34 rubi-home systemd[1]: Finished systemd-random-seed.service - Load/Save OS Random Seed.
Sep 20 14:44:34 rubi-home systemd[1]: Finished systemd-modules-load.service - Load Kernel Modules.
```

---

### Post by #&amp;thj^% on 2023-09-23
MAFoElffen do you ever see this "systemd-oomd.service" cause i sure don't:
```
journalctl --boot=2 --grep='systemd' | tail -n 200 | sort --reverse | grep systemd-oomd.service

```
No return.

---

### Post by Rubi1200 on 2023-09-23
I am getting an _unknown output format_ error when I try to run this:
```
journalctl -p 4 -x --boot=2 -r --output=~/journal_errors-00.log
```

---

### Post by MAFoElffen on 2023-09-23
> **1fallen said:**
> MAFoElffen do you ever see this "systemd-oomd.service" cause i sure don't:
```
journalctl --boot=2 --grep='systemd' | tail -n 200 | sort --reverse | grep systemd-oomd.service

```
No return.
LOL.

Rewritten and ran on my daily test case from yesterday:
```

mafoelffen@minatuar-23-09-18:~$ journalctl --boot=2 --grep='systemd' --lines=200 -r --unit=systemd-oomd.service --no-pager > /home/mafoelffen/journal_errors-00.log
mafoelffen@minatuar-23-09-18:~$ grep . journal_errors-00.log
Sep 18 19:43:02 minatuar-23-09-18 systemd[1]: Stopped systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer.
Sep 18 19:43:02 minatuar-23-09-18 systemd[1]: systemd-oomd.service: Deactivated successfully.
Sep 18 19:43:02 minatuar-23-09-18 systemd[1]: Stopping systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer...
Sep 18 19:40:52 minatuar-23-09-18 systemd[1]: Started systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer.
Sep 18 19:40:51 minatuar-23-09-18 systemd[1]: Starting systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer...

```
It shows up for me...

---

### Post by #&amp;thj^% on 2023-09-23
Rubi1200 are you trying to create a text log?
```
journalctl -p 4 -x --boot=2 -r >boot.txt
```

---

### Post by Rubi1200 on 2023-09-23
@MAFoElffen
I hope this is the correct format for you to analyze.

---

### Post by #&amp;thj^% on 2023-09-23
> **MAFoElffen said:**
> LOL.

Rewritten and ran on my daily test case from yesterday:
```

mafoelffen@minatuar-23-09-18:~$ journalctl --boot=2 --grep='systemd' --lines=200 -r --unit=systemd-oomd.service --no-pager > /home/mafoelffen/journal_errors-00.log
mafoelffen@minatuar-23-09-18:~$ grep . journal_errors-00.log
Sep 18 19:43:02 minatuar-23-09-18 systemd[1]: Stopped systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer.
Sep 18 19:43:02 minatuar-23-09-18 systemd[1]: systemd-oomd.service: Deactivated successfully.
Sep 18 19:43:02 minatuar-23-09-18 systemd[1]: Stopping systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer...
Sep 18 19:40:52 minatuar-23-09-18 systemd[1]: Started systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer.
Sep 18 19:40:51 minatuar-23-09-18 systemd[1]: Starting systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer...

```
It shows up for me...
It must be a Gnome thing:
2nd```
grep . journal_errors-00.log
-- No entries --

```
1st```
 journalctl --boot=2 --grep='systemd' --lines=200 -r --unit=systemd-oomd.service --no-pager > /home/me/journal_errors-00.log

```

---

### Post by MAFoElffen on 2023-09-23
IDK -- I didn't see anything that reached out and grabbed me, to tell me (clearly): "This is a problem that would cause that!"

Although: 
There were hints that say that the ACPi driver is incorrect and either the BIOS needs to be updated and/or the correct ACPI driver needs to be configured. ACPI can cause not shutting off. But there was nothing that said there was some kind of fatal error.

Then this with it's CPU:
```

Sep 20 14:44:34 rubi-home kernel: MDS CPU bug present and SMT on, data leak possible. See https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html for more details.

```
That is a CPU vulnerability that have these related CVE's:
```

CVE-2018-12126    MSBDS    Microarchitectural Store Buffer Data Sampling
CVE-2018-12130    MFBDS    Microarchitectural Fill Buffer Data Sampling
CVE-2018-12127    MLPDS    Microarchitectural Load Port Data Sampling
CVE-2019-11091    MDSUM    Microarchitectural Data Sampling Uncacheable Memory

```
Which means, for whatever version of Linux kernel you run, you should boot it with this kernel parameter: mds=full,nosmt in your GRUB_CMDLINE_LINUX_DEFAULT line.

Mine is similar, in that it reboots straight to a BIOS Boot Loop. Though when it does this, right before displaying the BIOS Boot menu, it flashes a n error containg "device error" in it. I've been trying to let it error while I video the error, so I can forward though it, frame, by frame, to see what it sames. So far, I keep missing it or it somehow is working, then errors again. It's been a "challenge."

---

### Post by MAFoElffen on 2023-09-23
> **Rubi1200 said:**
> I am getting an _unknown output format_ error when I try to run this:
```
journalctl -p 4 -x --boot=2 -r --output=~/journal_errors-00.log
```

I had a typo. Sorry. Corrected in the original post... to something like this. But you must have seen that before I edited that.
```
journalctl -p 4 -x --boot=2 -r --no-pager > ~/journal_errors-00.log
```

---

### Post by Rubi1200 on 2023-09-23
Really appreciate the efforts and analysis.

It's an odd one for me especially since both test installs of 22.04.3 and 23.04 shut down gracefully with none of these "issues."

I am going away for a couple of days but will take a closer look at the ACPI and MDS points you mentioned when I can.

Will report back with any findings or updates.

By the way, I see the bug report I filed remains unassigned. I assume this means either they did not get to it yet or consider it not important enough?

I will update the report with the relevant log files and information from this thread as soon as I can.

---

