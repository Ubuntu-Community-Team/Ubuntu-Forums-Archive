---
title: "GPU passthrough fails after kernel 6.5 -&gt; 6.8"
date: 2024-08-16
forum: Virtualisation
---

### Post by libertyspike138 on 2024-08-16
Hello I'm running 22.04.4, I use Intel HD graphics for my host and have nVidia that I have blacklisted to use as passthrough in QEMU / KVM guests. This has worked perfectly up until kernel 6.5 but after upgrading to kernel 6.8 after reboot my login screen was present on the monitor connected to my nVidia instead. I tried to boot up a VM and it completely froze my system to where I had to do a hard reset. Here are my GRUB boot parameters. "nosgx drm.edid_firmware=edid/DELLP2719H.bin intel_iommu=on iommu=pt video=efifb:off kvm.ignore_msrs=1 vfio-pci.ids=10de:1184,10de:0e0a isolcpus=2,3,4,5,8,9,10,11 splash" 
Has the way you assign VFIO drivers to a GPU changed between kernels? How do I get my GPU to use VFIO instead of Nouveau while booting with kernel 6.8? Thanks!

---

### Post by libertyspike138 on 2024-08-17
So I think I may have resolved this on my own. Probably about a year or so ago I ended up remarking to disable the blacklists I made of nouveau &  snd_hda_intel in my /etc/modprobe.d/vfio.conf because it was disabling those drivers for all devices in the system that use those drivers and everything was working fine through various kernel updates until 6.8. So now I went back in removed the remark to once again blacklist only the nouveau driver because blacklisting the snd_hda_intel also kills my main soundcard out. After this I updated initramfs and rebooted to see my login on the proper monitor output of the Intel HD instead of nVidia. I'm not sure if it is going to cause an issue with the nVidia display running VFIO but the nVidia sound using snd_hda_intel instead of VFIO or not but I don't know how else to approach assigning VFIO to the nVidia sound without blacklisting it altogether and killing my main soundcard as well.

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 770] [10de:1184] (rev a1)
	Subsystem: eVga.com. Corp. GK104 [GeForce GTX 770] [3842:3776]
	Kernel driver in use: vfio-pci
	Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
	Subsystem: eVga.com. Corp. GK104 HDMI Audio Controller [3842:3776]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1f.3 Audio device [0403]: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller [8086:a170] (rev 31)
	Subsystem: Gigabyte Technology Co., Ltd 100 Series/C230 Series Chipset Family HD Audio Controller [1458:a182]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_avs

---

