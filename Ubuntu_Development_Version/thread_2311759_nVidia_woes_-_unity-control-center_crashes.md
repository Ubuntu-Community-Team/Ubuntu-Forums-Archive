---
title: "nVidia woes - unity-control-center crashes"
date: 2016-01-29
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2016-01-29
I've actually fought problems with nvidia-304 ever since we went from the Wily kernel (4.2 series) to the first Xenial kernel (4.3 series) and a while back I installed the first of the 4.4 series kernels, then today pulled 4.4.0-2 from xenial-proposed and it's the first of the Xenial kernels where the additional drivers UI successfully installed the proprietary nvidia driver. Hooray I thought - time to party!!!!!!!!!!!!!

But as with all Xenial kernels up to this point the max resolution with the proprietary driver was 1024x768 rather than 1368x768. The nouveau driver properly boots to 1368x768 by default but the actual screen size is very slightly off (like 1/32" too large, pushing the right side of the DE off screen). It's been that way for a long time with any driver that uses llvmpipe - at least as far back as 13.10 but I never cared enough to file a bug report. With different hardware I found that selecting 1280x1024 fits the screen perfectly in those corner cases where llvmpipe is in use.

Anyway, after that long story, the new short story is that with 4.4.0-2 from xenial-proposed and nvidia-304 installed System Settings fails to open and apport automagically helps report this bug:

[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1539597](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1539597)

But it only happens with the nvidia driver installed/activated. With the nouveau driver System Settings opens OK. So this is just a heads up.

---

### Post by VMC on 2016-01-29
Does your syslog show the nvidia driver actually installed. Mine doesn't.

---

### Post by kansasnoob on 2016-02-01
> **VMC said:**
> Does your syslog show the nvidia driver actually installed. Mine doesn't.

It appears not. Also from JournalErrors in that bug report:

> Jan 29 07:26:56 username-AMD-desktop kernel: nvidia: module license 'NVIDIA' taints kernel.
Jan 29 07:26:56 username-AMD-desktop kernel: Disabling lock debugging due to kernel taint
Jan 29 07:26:56 username-AMD-desktop kernel: nvidia: Unknown symbol mtrr_del (err 0)
Jan 29 07:26:56 username-AMD-desktop kernel: nvidia: Unknown symbol mtrr_add (err 0)

As far as I can tell this dates back to some time during late Wily kernel dev, so sometime during kernel series 4.2.

If I google "ubuntu nvidia-304 fails to build with 4.2 series kernel" I get a gazillion hits, just for example:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1498146](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1498146)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340-updates/+bug/1477593](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340-updates/+bug/1477593)

I realize those are for nvidia-340 but if you check duplicates it includes other series of nvidia drivers.

So currently Wily, Xenial, and the Trusty dailies (with Wily kernel) are borked :(

---

### Post by kansasnoob on 2016-02-06
Suspecting that 14.04.4 with the Wily HWE stack will likely be released Thursday the 11th I decided to give things another look expecting to file a new duplicate bug report, and I probably still will but for the most part it's working:

```
lance@lance-AMD-desktop:~$ lspci -v -s `lspci | awk '/VGA/{print $1}'`
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Biostar Microtech Int'l Corp Device 1405
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	**Kernel driver in use: nvidia**

lance@lance-AMD-desktop:~$ uname -a
Linux lance-AMD-desktop 4.2.0-28-generic #33~14.04.1-Ubuntu SMP Thu Feb 4 12:26:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

Initially installing the driver using the UI fails as you can see here (check the clock at the top and you'll see that the process just never progresses:

[ATTACH=CONFIG]267155[/ATTACH]

[ATTACH=CONFIG]267156[/ATTACH]

So I just used synaptic to install nvidia-304 and surprisingly it's working :D

Now I need to pick my brain a bit :-k

---

### Post by kansasnoob on 2016-02-22
Working great today:

```
lance@lance-AMD-desktop:~$ uname -a
Linux lance-AMD-desktop 4.4.0-6-generic #21-Ubuntu SMP Tue Feb 16 20:32:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
lance@lance-AMD-desktop:~$ lspci -v -s `lspci | awk '/VGA/{print $1}'`
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Biostar Microtech Int'l Corp C61 [GeForce 7025 / nForce 630a]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_304

```

---

### Post by $yl9pAR%t on 2016-02-22
Could you tell me, is it working great on Unity and/or Gnome, too? I know this driver is installable since about a week, but is unusable after login on Unity and Gnome on Geforce 6150. I am not too suprised when it comes to Unity, but I expect working Gnome at least.

---

### Post by kansasnoob on 2016-02-22
> **mefisto888 said:**
> Could you tell me, is it working great on Unity and/or Gnome, too? I know this driver is installable since about a week, but is unusable after login on Unity and Gnome on Geforce 6150. I am not too suprised when it comes to Unity, but I expect working Gnome at least.

I tried it on flashback w/metacity this AM. Xenial Beta 1 (for flavors) is this week so I'll find out what happens with Unity and GNOME Shell soon.

---

### Post by kansasnoob on 2016-02-22
I just tried and Unity seems to run OK(ish) ................. I add (ish) because Unity notoriously gobbles up about 3/4 of the 2GB RAM on that box, whereas Flashback w/Metacity uses a negligible amount (about 25%).

---

### Post by andyczerwonka on 2016-07-05
This happens to me under Xenial and Quadro M1000M. As soon as I plug in an external monitor, unity crashes. I have to run Intel Mode to attache a second monitor to my mini display port.

---

