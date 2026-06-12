---
title: "Video card missing from IOMMU?"
date: 2018-12-04
forum: Virtualisation
---

### Post by zaurian on 2018-12-04
So I'm getting ready to check out VGA passthrough and I've already hit a roadblock!  The video card I want to pass through from 18.04 to Windows 10 does not seem to show up when I list IOMMU mappings??

My system: ASUS Zenith Extreme X399 / Threadripper 1950X / 128G

AMD-Vi / IOMMU / SVM is supported:

```
 steve@Threadripper:~$ dmesg | grep AMD-Vi
[    0.000000] AMD-Vi: Using IVHD type 0x11
[    0.000000] AMD-Vi: device: 00:00.2 cap: 0040 seg: 0 flags: b0 info 0000
[    0.000000] AMD-Vi:        mmio-addr: 00000000efd00000
[    0.000000] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:01.0 flags: 00
[    0.000000] AMD-Vi:   DEV_RANGE_END         devid: 3f:1f.6
[    0.000000] AMD-Vi:   DEV_ALIAS_RANGE         devid: ff:00.0 flags: 00 devid_to: 00:14.4
[    0.000000] AMD-Vi:   DEV_RANGE_END         devid: ff:1f.7
[    0.000000] AMD-Vi:   DEV_SPECIAL(HPET[0])        devid: 00:14.0
[    0.000000] AMD-Vi:   DEV_SPECIAL(IOAPIC[128])        devid: 00:14.0
[    0.000000] AMD-Vi:   DEV_SPECIAL(IOAPIC[129])        devid: 00:00.1
[    0.963212] AMD-Vi: IOMMU performance counters supported
[    0.976701] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    0.976703] AMD-Vi: Extended features (0xf77ef22294ada):
[    0.976707] AMD-Vi: Interrupt remapping enabled
[    0.976708] AMD-Vi: virtual APIC enabled
[    0.977001] AMD-Vi: Lazy IO/TLB flushing enabled

steve@Threadripper:~$ dmesg | grep -E "IOMMU"
[    0.963212] AMD-Vi: IOMMU performance counters supported
[    0.976701] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    0.978961] perf/amd_iommu: Detected AMD IOMMU #0 (2 banks, 4 counters/bank).
```

 As you can see here, I have two NVIDIA cards installed:

```
steve@Threadripper:~$ lspci | grep VGA
0a:00.0 VGA compatible controller: NVIDIA Corporation GP104 [GeForce GTX 1070] (rev a1)
43:00.0 VGA compatible controller: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] (rev a1)
```

It's the 1080 Ti that I want to pass through, so Bus Number 43:00.0 and PCI IDs 10de:1b06 for the video. 

```
steve@Threadripper:~$ lspci -nn | grep 43:00.
43:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] [10de:1b06] (rev a1)
43:00.1 Audio device [0403]: NVIDIA Corporation GP102 HDMI Audio Controller [10de:10ef] (rev a1)
```

 So - I want to figure out what IOMMU group this card is in, looking for the group with 43:00 in it, but it doesn't show up!?  What am I missing?

```
steve@Threadripper:~$ for a in /sys/kernel/iommu_groups/*; do find $a -type l; done | sort --version-sort
/sys/kernel/iommu_groups/0/devices/0000:00:01.0
/sys/kernel/iommu_groups/1/devices/0000:00:01.1
/sys/kernel/iommu_groups/2/devices/0000:00:01.3
/sys/kernel/iommu_groups/3/devices/0000:00:02.0
/sys/kernel/iommu_groups/4/devices/0000:00:03.0
/sys/kernel/iommu_groups/5/devices/0000:00:03.1
/sys/kernel/iommu_groups/6/devices/0000:00:04.0
/sys/kernel/iommu_groups/7/devices/0000:00:07.0
/sys/kernel/iommu_groups/8/devices/0000:00:07.1
/sys/kernel/iommu_groups/9/devices/0000:00:08.0
/sys/kernel/iommu_groups/10/devices/0000:00:08.1
/sys/kernel/iommu_groups/11/devices/0000:00:14.0
/sys/kernel/iommu_groups/11/devices/0000:00:14.3
/sys/kernel/iommu_groups/12/devices/0000:00:18.0
/sys/kernel/iommu_groups/12/devices/0000:00:18.1
/sys/kernel/iommu_groups/12/devices/0000:00:18.2
/sys/kernel/iommu_groups/12/devices/0000:00:18.3
/sys/kernel/iommu_groups/12/devices/0000:00:18.4
/sys/kernel/iommu_groups/12/devices/0000:00:18.5
/sys/kernel/iommu_groups/12/devices/0000:00:18.6
/sys/kernel/iommu_groups/12/devices/0000:00:18.7
/sys/kernel/iommu_groups/13/devices/0000:00:19.0
/sys/kernel/iommu_groups/13/devices/0000:00:19.1
/sys/kernel/iommu_groups/13/devices/0000:00:19.2
/sys/kernel/iommu_groups/13/devices/0000:00:19.3
/sys/kernel/iommu_groups/13/devices/0000:00:19.4
/sys/kernel/iommu_groups/13/devices/0000:00:19.5
/sys/kernel/iommu_groups/13/devices/0000:00:19.6
/sys/kernel/iommu_groups/13/devices/0000:00:19.7
/sys/kernel/iommu_groups/14/devices/0000:01:00.0
/sys/kernel/iommu_groups/14/devices/0000:01:00.1
/sys/kernel/iommu_groups/14/devices/0000:01:00.2
/sys/kernel/iommu_groups/14/devices/0000:02:00.0
/sys/kernel/iommu_groups/14/devices/0000:02:01.0
/sys/kernel/iommu_groups/14/devices/0000:02:02.0
/sys/kernel/iommu_groups/14/devices/0000:02:03.0
/sys/kernel/iommu_groups/14/devices/0000:02:04.0
/sys/kernel/iommu_groups/14/devices/0000:02:09.0
/sys/kernel/iommu_groups/14/devices/0000:03:00.0
/sys/kernel/iommu_groups/14/devices/0000:04:00.0
/sys/kernel/iommu_groups/14/devices/0000:05:00.0
/sys/kernel/iommu_groups/14/devices/0000:08:00.0
/sys/kernel/iommu_groups/15/devices/0000:09:00.0
/sys/kernel/iommu_groups/16/devices/0000:0a:00.0
/sys/kernel/iommu_groups/16/devices/0000:0a:00.1
/sys/kernel/iommu_groups/17/devices/0000:0b:00.0
/sys/kernel/iommu_groups/18/devices/0000:0b:00.2
/sys/kernel/iommu_groups/19/devices/0000:0b:00.3
/sys/kernel/iommu_groups/20/devices/0000:0c:00.0
/sys/kernel/iommu_groups/21/devices/0000:0c:00.2
/sys/kernel/iommu_groups/22/devices/0000:0c:00.3
```
What am I missing?  There are 22 IOMMU groups, none of which appear to have the bus 43:00

Anyone have any ideas?  One thing I plan to try next is swapping the 1070 and 1080Ti PCI slots to see if then the 1080Ti is assigned an IOMMU group.   Both slots are 16x, but for some reason slot 1 is mentioned as preferred if there is only one video card; not sure why ...

Thanks!
Steve

---

### Post by wildmanne39 on 2018-12-04
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by zaurian on 2018-12-05
Got it, wildmanne39.  My first post here - I was actually trying to figure out how people were doing that. Now hopefully someone in the know will stumble across this - I can't figure it out for the life of me.

edit: I actually solved the problem by switching the cards around, swapping PCI slots.  I'd still like to know why the card in the first 16x PCI slot doesn't show as one of the 22 IOMMU groups - strange.

---

### Post by springshades on 2018-12-10
This script floats around inside a few of the guides. You could try it if you haven't already. It does a better job of listing the IOMMU groups.

```
#!/bin/bash
for d in /sys/kernel/iommu_groups/*/devices/*; do
  n=${d#*/iommu_groups/*}; n=${n%%/*}
  printf 'IOMMU Group %s ' "$n"
  lspci -nns "${d##*/}"
done
```

I had a similar issue, and there is a guide on level1techs for Ubuntu 17.04 which mentions that they had similar issues getting the vfio to pick up the card before the nvidia driver. Note that our use case isn't super common (two Nvidia cards) since most people are using one card and an iGPU instead. Many of the guides don't cover it.

[HTML]https://forum.level1techs.com/t/ubuntu-17-04-vfio-pcie-passthrough-kernel-update-4-14-rc1/119639[/HTML]

Anyway, it seems like one of their extra steps fixed my issue. My guess is it's the modification to /etc/initramfs-tools/modules that does the trick since it explicitly loads up all of the modules in order earlier in the boot process.

Your issue may have been the same, or I guess it could have been the shared IOMMU group issue since swapping slots fixed it. The arch guide spends some time on that.

EDIT: Sorry, I didn't realize that you had started two threads. This post is partially in response to some of the information in your other thread.

---

