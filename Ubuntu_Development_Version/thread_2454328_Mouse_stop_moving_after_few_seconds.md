---
title: "Mouse stop moving after few seconds"
date: 2020-11-27
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-11-27
Mouse stop moving after few seconds if not used. Restart moving on click but stops again in few seconds.
problem appears after last updates
```
The following NEW packages will be installed:
  libdebuginfod1
The following packages will be upgraded:
  apport apport-gtk gdb gdbserver gir1.2-rsvg-2.0 libasound2 libasound2-data libatopology2 libdjvulibre-text libdjvulibre21 libegl-mesa0 libfprint-2-2
  libgbm1 libgl1-mesa-dri libglapi-mesa libglx-mesa0 libqpdf28 librsvg2-2 librsvg2-common libxatracker2 linux-firmware mesa-vulkan-drivers python3-apport
  python3-problem-report
24 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
```
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1905946](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1905946)

---

### Post by dino99 on 2020-11-27
Also get that issue since a couple days; not very harmful. A bigger problem is page scrolling on GS xorg session (chromium browser): jump back and forth :mad:

---

### Post by corradoventu on 2020-11-27
If You have the same problem please subscribe my bug: click on 'yes it affect me'.

---

### Post by P-I H on 2020-11-27
Added me to the bug

---

### Post by dino99 on 2020-11-27
Just got a hard mouse lock:
- have waited a couple minutes, but to not avail
- then exit the session, but the mouse was still locked
- finally reboot and checked the journal; get:

> systemd-logind[439]: Removed session 2.
 systemd[2183]: tracker-extract.service: Succeeded.
 kernel: INFO: task kworker/3:0:1944 blocked for more than 241 seconds.
 kernel:       Not tainted 5.8.0-31-generic #33+21.04.1-Ubuntu
 kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
 kernel: kworker/3:0     D    0  1944      2 0x00004000
 kernel: Workqueue: events_long rtl_hw_phy_work_func_t [r8152]
 kernel: Call Trace:
 kernel:  __schedule+0x212/0x5d0
 kernel:  schedule+0x55/0xc0
 kernel:  rpm_resume+0x177/0x810
 kernel:  ? wait_woken+0x80/0x80
 kernel:  rpm_resume+0x320/0x810
 kernel:  ? newidle_balance+0x290/0x350
 kernel:  __pm_runtime_resume+0x52/0x80
 kernel:  usb_autopm_get_interface+0x1d/0x50
 kernel:  rtl_hw_phy_work_func_t+0x2f/0x150 [r8152]
 kernel:  ? __schedule+0x21a/0x5d0
 kernel:  process_one_work+0x1e8/0x3b0
 kernel:  worker_thread+0x50/0x370
 kernel:  kthread+0x12f/0x150
 kernel:  ? process_one_work+0x3b0/0x3b0
 kernel:  ? __kthread_bind_mask+0x70/0x70
 kernel:  ret_from_fork+0x22/0x30


This is with 5.8.0-31 kernel on G-S on xorg session. Do you have such log too when the mouse freeze on your system ?

---

### Post by Yahoé on 2020-11-27
+1 under Unity, Logitech touch pad (not a laptop) and keyboard are mostly unusable because they lag/stop working.
Reported in [bug # 1905946]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1905946")

---

### Post by dino99 on 2020-11-27
Feedback:
- after reboot , select again the latest kernel (31) and shortly reproduced that issue, with the same strace.
- then select the main kernel (25) and does not get mouse freeze/lock since  ~ 30 min

Note that kernel (30) was getting some rare soft freezes; but (31) hardly fails
Get this logged:   kernel: usb 1-4.3: reset low-speed USB device number 7 using xhci_hcd


note2: after ~45 min with kernel (25) , no problem with the mouse, but had a hard network failure, locking the whole system.

---

### Post by Yahoé on 2020-11-27
Thank you @dino99. Could please update [bug # 1905946]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1905946") with you latest findings?

---

### Post by zika on 2020-11-28
I do use i3 and similar and mouse freeze is present so I suspect that the reason for that is somewhere else. Due to very different kernels used, it is not in a kernel either. Got used to that... ;)
Some (small, truly) sort of lessening of freeze is achieved with loading usbmouse driver....

---

### Post by tokyobadger on 2020-11-28
Also affected. Updated 7 hrs ago - not at the box now but checking the apt history the packages listed by corradoventu were not identical.

Mouse freezes. Keyboard more or less unusable. Resorted to onscreen keyboard.

Also sure that it is not kernel related. Daily updates have me with 5.8.0-26 and 5.8.0-25. Booting into both with the same behaviour. Recovery mode on both kernels also has the keyboard unresponsive so I don&#8217;t think the bug is WM/DE related. Haven&#8217;t tried booting to console yet. But considering the recovery experience probably not going to make a difference.

libinput, libusb, or related seem most likely culprits.

FWIW this is a desktop put together last year, Groovy and eOS are both fine, as was Hirsute before the reboot after update
**Edit**
These are the packages updated after which the issue above started
```
Start-Date: 2020-11-28  10:05:38
Commandline: apt-get upgrade
Requested-By: tokyobadger (1000)
Upgrade: libdjvulibre-text:amd64 (3.5.27.1-15, 3.5.28-1), gnome-control-center-data:amd64 (1:3.38.1-1ubuntu1, 1:3.38.2-1ubuntu1),
 gnome-control-center:amd64 (1:3.38.1-1ubuntu1, 1:3.38.2-1ubuntu1), libpulsedsp:amd64 (1:13.99.3-1ubuntu1, 1:14.0-1ubuntu1), 
pulseaudio:amd64 (1:13.99.3-1ubuntu1, 1:14.0-1ubuntu1), cheese:amd64 (3.38.0-2, 3.38.0-3), libpulse0:amd64 (1:13.99.3-1ubuntu1, 
1:14.0-1ubuntu1), libpulse-mainloop-glib0:amd64 (1:13.99.3-1ubuntu1, 1:14.0-1ubuntu1), libhttp-cookies-perl:amd64 (6.08-1, 6.09-1), 
rubygems-integration:amd64 (1.17.2, 1.17.3), libcheese-gtk25:amd64 (3.38.0-2, 3.38.0-3), cheese-common:amd64 (3.38.0-2, 3.38.0-3), 
gnome-control-center-faces:amd64 (1:3.38.1-1ubuntu1, 1:3.38.2-1ubuntu1), libdjvulibre21:amd64 (3.5.27.1-15, 3.5.28-1), 
pulseaudio-module-bluetooth:amd64 (1:13.99.3-1ubuntu1, 1:14.0-1ubuntu1), libcheese8:amd64 (3.38.0-2, 3.38.0-3), 
libetonyek-0.1-1:amd64 (0.1.9-3, 0.1.9-4), pulseaudio-utils:amd64 (1:13.99.3-1ubuntu1, 1:14.0-1ubuntu1), 
libcdr-0.1-1:amd64 (0.1.6-1build3, 0.1.6-2), libe-book-0.1-1:amd64 (0.1.3-1build4, 0.1.3-2), libdouble-conversion3:amd64 (3.1.5-6ubuntu1, 3.1.5-6.1)
```

overlap with corradoventu seems to be
```

libdjvulibre-text libdjvulibre21
```
but that doesn't make any sense

I also updated yesterday and don't recall rebooting
```
Start-Date: 2020-11-27  07:07:23
Commandline: apt-get upgrade
Requested-By: tokyobadger (1000)
Upgrade: libfprint-2-2:amd64 (1:1.90.3+tod1-0ubuntu1, 1:1.90.3+tod1-0ubuntu2), libasound2-data:amd64 (1.2.3.2-1ubuntu4, 1.2.3.2-1ubuntu5), 
libnet-dns-perl:amd64 (1.28-1, 1.29-1), apport:amd64 (2.20.11-0ubuntu51, 2.20.11-0ubuntu53), python3-apport:amd64 (2.20.11-0ubuntu51, 
2.20.11-0ubuntu53), libasound2:amd64 (1.2.3.2-1ubuntu4, 1.2.3.2-1ubuntu5), apport-gtk:amd64 (2.20.11-0ubuntu51, 2.20.11-0ubuntu53), 
gdbserver:amd64 (9.2-0ubuntu2, 10.1-0ubuntu2), linux-firmware:amd64 (1.191, 1.192), 
python3-problem-report:amd64 (2.20.11-0ubuntu51, 2.20.11-0ubuntu53), libjson-maybexs-perl:amd64 (1.004002-1, 1.004003-1), 
libatopology2:amd64 (1.2.3.2-1ubuntu4, 1.2.3.2-1ubuntu5)
End-Date: 2020-11-27  07:08:10

Start-Date: 2020-11-27  07:08:17
Commandline: apt-get dist-upgrade
Requested-By: tokyobadger (1000)
Install: libdebuginfod1:amd64 (0.182-1, automatic)
Upgrade: gdb:amd64 (9.2-0ubuntu2, 10.1-0ubuntu2)
End-Date: 2020-11-27  07:08:19

Start-Date: 2020-11-27  18:23:41
Commandline: apt-get upgrade
Requested-By: tokyobadger (1000)
Upgrade: libqpdf28:amd64 (10.0.3-1, 10.0.4-1), librsvg2-common:amd64 (2.50.1+dfsg-1, 2.50.2+dfsg-1), 
librsvg2-2:amd64 (2.50.1+dfsg-1, 2.50.2+dfsg-1), ibus-pinyin:amd64 (1.5.0-6.1, 1.5.0-6.1build1), liblua5.4-0:amd64 (5.4.0-2, 5.4.1-1), 
qpdf:amd64 (10.0.3-1, 10.0.4-1), gir1.2-rsvg-2.0:amd64 (2.50.1+dfsg-1, 2.50.2+dfsg-1)
```
So now I think it's the linux-firmware package with apport-related packages second in the likely suspects line-up

---

### Post by Yahoé on 2020-11-28
@zika, @tokyobadger could please indicate in [bug # 1905946]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1905946") that it also affects you.

---

### Post by zika on 2020-11-29
> **Yahoé said:**
> @zika, @tokyobadger could please indicate in [bug # 1905946]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1905946") that it also affects you.Done, eventhough I'm, still, not sure about culprit.

---

### Post by corradoventu on 2020-11-29
Reinstalled from Ubuntu 21.04 "Hirsute Hippo" - Alpha amd64 (20201125) with NO download updates.
mouse works fine
held linux-firmware package: sudo apt-mark hold linux-firmware
done update+upgrade
problem reappear
... so linux-firmware is not guilty

---

### Post by ajgreeny on 2020-11-29
I updated my system last night, Sat, 28 Nov. at about 19:00hrs GMT and rebooted but did not notice anything odd.
I am running Xubuntu but as a VM in KVM/QEMU, so my situation may not be of any consequence but I thought it worth reporting.
I will run it longer today and report back the results.

---

### Post by corradoventu on 2020-11-29
Xubuntu is not Ubuntu, also Lubuntu seems immune.
On Ubuntu 21.04 I installed last kernel from mainline ppa and the problem does not disappear.
```
corrado@corrado-x5-hippo-1125:~$ uname -a
Linux corrado-x5-hippo-1125 5.10.0-051000rc5-generic #202011221956 SMP Mon Nov 23 01:02:11 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-x5-hippo-1125:~$ 
```

---

### Post by dino99 on 2020-11-30
Looks like a missing mouse driver:

config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse2)
 No input driver specified, ignoring this device
 kernel: usb 1-4.3: reset low-speed USB device number 47 using xhci_hcd

---

### Post by corradoventu on 2020-11-30
if the mouse driver was missing the mouse would not work at all while it works for a few seconds and restarts by clicking and then stops again.
More: the mouse works fine on a new install from Ubuntu 21.04 "Hirsute Hippo" - Alpha amd64 (20201125) but stop working after updates.
problem happens wit 3 different mice

---

### Post by dino99 on 2020-11-30
After googling around that issue, i've found a user blaming a legacy usb bios parameter possibly conflicting (when usb3 hub exist) with default internal kernel settings when it is activated. So i switch it to 'auto' to run a new test now :p  In case it still freeze, then i will set it to 'off'

---

### Post by corradoventu on 2020-11-30
Please give me the link of the problem You found about legacy bios parameter. Legacy? I have UEFI bios on both my PC. 
As stated in my bug I have the same problem on 2 different PC (desktop and laptop) on the desktop I have an internal USB3 hub connected to a PCIe port but on the laptop I don't have an USB3 hub. 
They are also 7 other people with my same problem... all with same USB bios parameter on different motherboard?
And why all my mice works fine on same hardware with Ubuntu 16.04, 18.04, 19.10, 20.04, 20.10 and Lubuntu 21.04 but not on 21.04?

---

### Post by dino99 on 2020-11-30
I've read many threads/posts/reports/gits to find that possible conflict: can't point you to a link but a user was blaming Asus to set their uefi default usb to 'legacy' even on recent hardware with usb3; and it seems that recent (which? ) kernel/libinput/firmware does not like the usb2/usb3 mixed hub . And he suggest to set it to either 'auto' or 'false'.

By now on a recent asus laptop (with uefi) i've switched 'usb legacy' to 'false' . Looks like the usb2/usb3 mix disturb the kernel about the requested power. (this might explain the journal message 'reset low speed usb' previously reported.

With usb set 'auto' on this laptop, i now get:
- lower temp/ cpu used
- browser react smoother too.

Will see if these good news will persist :P

---

### Post by corradoventu on 2020-11-30
On my desktop I changed USB legacy to 'false' but the problem remain.
```
corrado@corrado-x2-hh-1104:~$ inxi -SMCx
System:
  Host: corrado-x2-hh-1104 Kernel: 5.8.0-25-generic x86_64 bits: 64 
  compiler: gcc v: 10.2.0 Desktop: GNOME 3.38.1 
  Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop Mobo: ASRock model: H110M-G/M.2 
  serial: <superuser/root required> UEFI: American Megatrends v: P1.10 
  date: 05/11/2017 
CPU:
  Info: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 31199 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 801 4: 800 
corrado@corrado-x2-hh-1104:~$ 

```

---

### Post by dino99 on 2020-11-30
Problem persist here too, but:
-less often
- now i need to detect which action/app/browser news stream (chromium) make high cpu usage. Might use firefox instead to know if its chromium dependant.
- the mouse/keyboard is no more locked (at least, not yet seen)

---

### Post by corradoventu on 2020-11-30
I don't have chromium, using just firefox. for me the mouse continue stop moving after about 5 seconds of non-use and restart with a click to stop again after 5 seconds of non-use.
My bug is now 'confirmed' by other 7 users and developers are looking at it... I will wait and use Gorilla instead Hippo in the meantime.

---

### Post by P-I H on 2020-11-30
Installed all the updates in proposed from main, which fixed the problem. libfpint [1:1.90.3+tod1-0ubuntu3]("https://launchpad.net/ubuntu/+source/libfprint/1:1.90.3+tod1-0ubuntu3") was installed

---

### Post by zika on 2020-12-01
> **P-I H said:**
> Installed all the updates in proposed from main, which fixed the problem. libfpint [1:1.90.3+tod1-0ubuntu3]("https://launchpad.net/ubuntu/+source/libfprint/1:1.90.3+tod1-0ubuntu3") was installedI'd say: You're right... It seems so. Great.

---

### Post by tokyobadger on 2020-12-01
Same libfprint update fixed it for me too.

---

### Post by jabulon1 on 2021-09-07
I seem to suffer the same symptoms on 20.04.3
My version of libfprint is:
```
sudo apt list|grep libfprint

libfprint-2-2/focal-updates,now 1:1.90.2+tod1-0ubuntu1~20.04.4 amd64 [installed,automatic]
libfprint-2-dev/focal-updates 1:1.90.2+tod1-0ubuntu1~20.04.4 amd64
libfprint-2-doc/focal-updates,focal-updates 1:1.90.2+tod1-0ubuntu1~20.04.4 all
libfprint-2-tod-dev/focal-updates 1:1.90.2+tod1-0ubuntu1~20.04.4 amd64
libfprint-2-tod1/focal-updates,now 1:1.90.2+tod1-0ubuntu1~20.04.4 amd64 [installed]

```

Should I update it? If so, can you please direct me to the source or terms I need to research to understand how to do it?

---

