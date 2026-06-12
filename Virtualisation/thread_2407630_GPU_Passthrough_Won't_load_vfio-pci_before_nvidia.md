---
title: "GPU Passthrough: Won't load vfio-pci before nvidia"
date: 2018-12-06
forum: Virtualisation
---

### Post by zaurian on 2018-12-06
I've followed numerous tutorials and I think I'm getting close, but I can't get vfio-pci to take control of the GPU I want to pass through.

I have two NVIDIA cards:

```
steve@Threadripper:~$ lspci -nn -d 10de:
09:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] [10de:1b06] (rev a1)
09:00.1 Audio device [0403]: NVIDIA Corporation GP102 HDMI Audio Controller [10de:10ef] (rev a1)
43:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104 [GeForce GTX 1070] [10de:1b81] (rev a1)
43:00.1 Audio device [0403]: NVIDIA Corporation GP104 High Definition Audio Controller [10de:10f0] (rev a1)

```

It's the 1080 Ti at 09:00.0 10de:1b06 that I'd like to pass through, along with the Audio Controller at 09:00.1 10de:10ef

However, once I'm all booted up and I look to see what drivers are loaded, the NVIDIA drivers are attaching both video cards.  Of course I want the vfio-pci driver to pick up the 1080Ti before NVIDIA drivers load. I can't blacklist nvidia because I need it for my host card.  I know that vfio-pci is loading because it _does_ take hold of the audio controller on the 1080Ti; I also know that it's paying attention to the PCI ID's because it _does not_ take control of either video or audio on the 1070 card that I want to use for the host.

For the 1080 card it loads the nvidia driver as seen here (but notice vfio-pci caught the audio):```
steve@Threadripper:~$ lspci -kn | grep -A 2 09:00
09:00.0 0300: 10de:1b06 (rev a1)
    Subsystem: 1462:3602
    Kernel driver in use: nvidia
--
09:00.1 0403: 10de:10ef (rev a1)
    Subsystem: 1462:3602
    Kernel driver in use: vfio-pci
```

For the 1070 card, it is expected to load the nvidia video driver and the intel audio driver as seen: ```
steve@Threadripper:~$ lspci -kn | grep -A 2 43:00
43:00.0 0300: 10de:1b81 (rev a1)
    Subsystem: 1043:8598
    Kernel driver in use: nvidia
--
43:00.1 0403: 10de:10f0 (rev a1)
    Subsystem: 1043:8598
    Kernel driver in use: snd_hda_intel
```
/etc/modprobe.d/local.conf```
options kvm_intel nested=1 #I have Ryzen Threadripper 1950X but don't see an AMD version of this
options vfio_iommu_type1 allow_unsafe_interrupts=1
options vfio-pci ids=10de:1b06,10de:10ef disable_vga=1options kvm ignore_msrs=1 allow_unsafe_assigned_interrupts=1
install vfio-pci /sbin/vfio-pci-override-vga.sh
softdep nvidia pre: vfio-pci #saw this somewhere, supposed to force vfio-pci before nvidia loads

```

This script is supposed to override loading drivers, but after boot the files contain '(null)' rather than 'vfio-pci'
cat /sbin/vfio-pci-override-vga.sh 
```
#!/bin/sh

DEVS="0000:09:00.0 0000:09:00.1"

for DEV in $DEVS; do
    echo "vfio-pci" > /sys/bus/pci/devices/$DEV/driver_override
done

modprobe -i vfio-pci
```

I read that dmesg | grep -i vfio will tell me what is currently bound to vfio_pci. It does show the video card (1b06) here, so I'm confused.

```
steve@Threadripper:/etc/modprobe.d$ dmesg | grep -i vfio
[    2.342670] VFIO - User Level meta-driver version: 0.3
[    6.404134] vfio_pci: add [10de:1b06[ffff:ffff]] class 0x000000/00000000
[    6.404139] vfio_pci: add [10de:10ef[ffff:ffff]] class 0x000000/00000000
```

This is my /boot/grub/grub.cfg```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2

GRUB_CMDLINE_LINUX_DEFAULT="modprobe.blacklist=noveau nomodeset amd_iommu=on iommu=pt kvm_amd.npt=1 amd_iommu_dump=1 kvm.ignore_msrs=1 ivrs_ioapic[130]=00:00.2 hugepages=8192"
GRUB_CMDLINE_LINUX=""
```

So my question is basically, why isn't vfio-pci taking the video card before nvidia drivers load? It seems like I have multiple mechanisms to force vfio to load first?

Also, I'm confused - these seem to conflict - the first command tells me nvida is bound to the video card, the second tells me vfio-pci is bound to the video card. Am I reading this wrong?
```
lspci -kn | grep -A 2 09:00
dmesg | grep -i vfio

```

Anyone have any ideas of things I might try in order to get vfio-pci to bind to the video card before nvidia loads on it?

Thanks!

---

### Post by KillerKelvUK on 2018-12-09
No an expert here so pls ignore any crap...

In /etc/modprobe.d/local.conf...
> 
options kvm_intel nested=1 #I have Ryzen Threadripper 1950X but don't see an AMD version of this

There are lots of articles talking about "kvm_amd" ([https://docs.fedoraproject.org/en-US/quick-docs/using-nested-virtualization-in-kvm/](https://docs.fedoraproject.org/en-US/quick-docs/using-nested-virtualization-in-kvm/)) and ([https://wiki.archlinux.org/index.php/Talk:KVM](https://wiki.archlinux.org/index.php/Talk:KVM)).  However it would be atypical in my experience to want to bother with nested virtulisation if your intentions are for gaming.  Appreciate there are other uses for vga passthrough you might be wanting to explore, note the use of systool to explore kernel module parameters, something like "systool -avm kvm_amd" would show you the current system.

> 
install vfio-pci /sbin/vfio-pci-override-vga.sh

So the shell script is trying to redo what the prior line in this file should be doing via the modprobe process, seems a little odd and difficult to debug i.e. you are trying to hack around the problem rather than fix the problem.  My recommendation would be to remove this for now.

In your /boot/grub/grub.cfg...
> 
GRUB_CMDLINE_LINUX_DEFAULT="modprobe.blacklist=noveau nomodeset amd_iommu=on iommu=pt kvm_amd.npt=1 amd_iommu_dump=1 kvm.ignore_msrs=1 ivrs_ioapic[130]=00:00.2 hugepages=8192"

Okay so lots going on here, my recommendations are to...
[LIST]
[*] clean up the blacklist into /etc/modprobe.d/blacklist.conf
[*]Why nomodeset?
[*]kvm.ignore_msrs=1 is also being set in /etc/modprobe.d/local.conf, I'd recommend you remove this from grub
[/LIST]

> 
Also, I'm confused - these seem to conflict - the first command tells me nvida is bound to the video card, the second tells me vfio-pci is bound to the video card. Am I reading this wrong?
```

lspci -kn | grep -A 2 09:00
dmesg | grep -i vfio

```

So the 1st command tells you what is the config in real-time the 2nd tell you what was the config at that point in history.  I think its possible that your shell script (vfio-pci-override-vga.sh) is undoing some of vfio as I noted above.

Lastly it might be worthwhile if you are still having issues to confirm which device the VGA arbitration process is acquiring on boot, to see this you might need to do a clean boot and then run "dmesg | grep vgaarb" which will give you something like...
```

[    0.189157] pci 0000:00:02.0: vgaarb: setting as boot VGA device

```

---

### Post by zandor22 on 2019-03-24
Hi, just curious if you were ever able to solve this -- I'm having the exact same issue -- can't block nvidia from attached to the card.

---

