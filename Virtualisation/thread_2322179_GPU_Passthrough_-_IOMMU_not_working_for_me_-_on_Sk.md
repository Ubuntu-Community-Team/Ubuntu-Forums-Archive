---
title: "GPU Passthrough - IOMMU not working for me - on SkyLake 16.04 AsRock"
date: 2016-04-26
forum: Virtualisation
---

### Post by gavi2 on 2016-04-26
> Trying to do GPU passthrough on 16.04 qemu  SkyLake NVIDIA ITX.
IOMMU is "enabled" but not functional as groups can't be found.


I read this thread on GPU Passthrough working on Ubuntu 16.04:
[URL="http://ubuntuforums.org/showthread.php?t=2320369"]http://ubuntuforums.org/showthread.php?t=2320369
[/URL]
And I read the most relevant articles,
 including those from
 vfio.blogspot.co.uk        and
 [www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/]("http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/")


*** **OS**:

(K)Ubuntu 16.04.0 booting from UEFI
 

*****HARDWARE**:
 
i7 6700-k (which supports VT-D)
motherboard AsRock ( Fatal1ty Z170 Gaming ITX ac latest Uefi Version 2.0) which has got both VT-D and Intel Virtualization "enabled".
GTX 970 destined to GPU passthrough  with qemu and KVM
intel integrated graphics destinate to the host. (bios primary display setting = "integrated", shared memory="1024MB" )


*****PROBLEM**:
```
dmesg | grep -e DMAR -e IOMMU
```

results in:

```
[    0.000000] DMAR: IOMMU enabled
```

however typing:

```
**find /sys/kernel/iommu_groups/ -type l**
```

results in:
 ** no output at all**



*** **SETTINGS**:

I tried with each of these:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi=off    intel_iommu=on "
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi=off    intel_iommu=on intel_iommu=igfx_off"
```

```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi=off    intel_iommu=on intel_iommu=igfx_off  pcie_acs_override=downstream"
```

always followed by  
```
sudo update-grub
```  and reboot, of course.

I need acpi=off in my system, otherwise dmesg shows a ton of warnings that keep growing.
Those warning are not likely to be related to the problem with IOMMU

I also have got the following settings:

```
 sudo kate /etc/modules
```

```
  pci_stub
  vfio
  vfio_iommu_type1
  vfio_pci
  kvm
  kvm_intel
```

On a separate but related topic, I tried to blacklist the GTX 970. I tried to assign vfio-pci directly (as it should have worked since Kernel 4.1), but it did not work. So I used pci-stub. I tried to blacklist the nvidia drivers explicitly, but I still get "Kernel modules: nvidiafb, nouveau":

```
sudo lspci -s 01: -v
```
gives:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: NVIDIA Corporation GM204 [GeForce GTX 970]
        Flags: fast devsel, IRQ 16
        Memory at de000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at d0000000 (64-bit, prefetchable) [disabled] [size=32M]
        I/O ports at e000 [disabled] [size=128]
        Expansion ROM at df000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Legacy Endpoint, MSI 00
        Kernel driver in use: pci-stub
        **Kernel modules: nvidiafb, nouveau**

01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
        Subsystem: NVIDIA Corporation GM204 High Definition Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at df080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Kernel driver in use: pci-stub
        Kernel modules: snd_hda_intel

```

---

### Post by MAFoElffen on 2016-04-27
Note: Please go back and edit your post #1 to encapsulate the commands and output within code tags... I started that for you as an example. It's a forum policy... It keeps the forum's software from translating something by mistake, and organizes things to make a post more readable..

Is your BIOS at current version 2.00? There were earlier versions 1.00, 1.10, 1.20, 1.30, 1.40, 1.50, 1.60, 1.80.

Try this:
```

for iommu_group in $(find /sys/kernel/iommu_groups/ -maxdepth 1 -mindepth 1 -type d); \
do echo "IOMMU group $(basename "$iommu_group")"; \
for device in $(ls -1 "$iommu_group"/devices/); \
do echo -n $'\t'; lspci -nns "$device"; done; done

```

---

### Post by gavi2 on 2016-04-27
Thank you for your reply.
I corrected the first post with the code tags. I added there also the Uefi version (which was and is  the latest "P2.0") and a few more details on the settings. 

The code you suggested:
```
echo "Trying to show IOMMU";
for iommu_group in $(find /sys/kernel/iommu_groups/ -maxdepth 1 -mindepth 1 -type d); 
do echo "IOMMU group $(basename "$iommu_group")"; 
for device in $(ls -1 "$iommu_group"/devices/); 
do echo -n $'\t'; lspci -nns "$device"; done; done
echo "Finished trying to show IOMMU";
```
gives nothing:
```
Trying to show IOMMU
Finished trying to show IOMMU
```


Would it be better, for solving this thread, if I reinstall Linux and go with a more popular GUI such as Unity or Gnome, to get more people interested in helping?
If all goes well, I plan to write a summary of all the steps for my hardware / distro, as the instructions to achieve GPU pass-through seem to evolve quite quickly, and each case has got its own hardware specific issues.

Thanks in advance.

---

### Post by QIII on 2016-04-27
Hello!

Re-installing with a different DE would really make no difference at all.  Yours is not a DE problem.

We support all official flavors of Ubuntu here.  Don't change what you use.

---

### Post by gavi2 on 2016-04-27
Reinstalling Linux, this time Ubuntu 16.04, solved both the IOMMU problem as well as the kernel ring flooded by messages (the problem that did force me to run the Grub command line with acpi=off)

```
**find /sys/kernel/iommu_groups/ -type l**
```[B]

```
/sys/kernel/iommu_groups/0/devices/0000:00:00.0
/sys/kernel/iommu_groups/1/devices/0000:00:01.0
/sys/kernel/iommu_groups/1/devices/0000:01:00.0
/sys/kernel/iommu_groups/1/devices/0000:01:00.1
/sys/kernel/iommu_groups/2/devices/0000:00:14.0
/sys/kernel/iommu_groups/2/devices/0000:00:14.2
/sys/kernel/iommu_groups/3/devices/0000:00:16.0
/sys/kernel/iommu_groups/4/devices/0000:00:17.0
/sys/kernel/iommu_groups/5/devices/0000:00:1c.0
/sys/kernel/iommu_groups/5/devices/0000:00:1c.4
/sys/kernel/iommu_groups/5/devices/0000:00:1c.6
/sys/kernel/iommu_groups/5/devices/0000:03:00.0
/sys/kernel/iommu_groups/5/devices/0000:04:00.0
/sys/kernel/iommu_groups/6/devices/0000:00:1d.0
/sys/kernel/iommu_groups/6/devices/0000:05:00.0
/sys/kernel/iommu_groups/7/devices/0000:00:1f.0
/sys/kernel/iommu_groups/7/devices/0000:00:1f.2
/sys/kernel/iommu_groups/7/devices/0000:00:1f.3
/sys/kernel/iommu_groups/7/devices/0000:00:1f.4
/sys/kernel/iommu_groups/8/devices/0000:00:1f.6
```


[/B]I think that the cause of the problem was the following:

16.04.0 (both Kubuntu and Ubuntu) crashed my system systematically when the monitor was attached to my NVIDIA via DVI-D cable.

After I realized that to avoid that crash at boot, I simply had to connect the monitor to the Intel integrated gpu, I had not more crashes.
But I think that my attempts to fix that issue might have introduced an IOMMU problem in the Kubuntu installation.

---

### Post by MAFoElffen on 2016-04-30
LOL. I needed a laugh and you cheered up my day. Sorry for that, but don't feel embarrassed, I've been there also.

Yes, you need to connect a monitor to the GPU that will be active on boot -and- to the monitor that will be used in the pass-through.

idk about the later problem you say you might have caused in the install... go back over and recheck the files you edited for the pass-thorugh... I forget what the default editor in kubuntu is. In gedit, if you look in the dierectory of where those files were, there will be a backup file of what that file was before the last saved edit ... with an "~" (tild) character appended to the filename...

---

### Post by nejc.gasper on 2016-09-16
Sorry to necro, but this is the only post I could find in 4 hours that is even remotely similar to my problem. Also using Kubuntu 16.04 (upgraded 15.04 -> 15.10 -> 16.04).

**find /sys/kernel/iommu_groups/ -type l**Also yields no results at all. Problem is all guides assume this part is working and here clearly something is not. Could be kernel compiled differently for kubuntu compared to ubuntu?

HW: 6850K, Rampage V Extreme (both should support VT-d).

Basically at this point I am either having some kubuntu specific bug OR mobo has buggy bios. Hope it is the former. Any ideas on what to try?

---

### Post by redger on 2016-09-17
please verify that you have 
[LIST=1]
[*]A vt-d enabled CPU (not the k series)
[*]A vt-d enabled motherboard
[*]Enabled the vt-d facilities via the motherboard's bios
[*]Set intel_iommu=on in the grub command line (edit /etc/default/grub and then "sudo update-grub" after saving the changes)
[*]Rebooted after the above
[/LIST]

---

### Post by nejc.gasper on 2016-09-17
Still not there, but it was 4), have done what is necessary ([FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX=[/COLOR][COLOR=#FF54FF]**"intel_iommu=on")**[/COLOR][/FONT] ... well because of your checklist I also checked at boot time and the param was no there! Added it manually and now I at least get IOMMU enabled dmesg message. Thanks! Spent hours on this :/

---

### Post by redger on 2016-09-17
ok, now you need to assign the elements of the group the video card lies in to vfio-pci. Plenty of instructions on how to do that

then the easiest step from there is to use virt-manager to create your vm. Be sure to select "modify definition before install" and then on the overview screen select UEFI bios BEFORE you proceed to installing the OS. You also probably want to create an lvm partition has host storage for performance and manageability. From there it's all pretty easy .. plenty of instructions around

---

