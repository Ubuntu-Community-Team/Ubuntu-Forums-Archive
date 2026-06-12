---
title: "AMD CPU passthrough virtualization KVM/QEMU"
date: 2016-12-05
forum: Virtualisation
---

### Post by zmoky2 on 2016-12-05
I have issues with my PT Virtualization steup on a Asrock AM1B-ITX mainboard and AMD Athlon(tm) 5350 CPU.

I am posting here the details, hoping that somebody there knows what this is about.

First of all, the CPU and also the MB supports virtualization and it is also enabled in the BIOS.
 - CPU: [http://www.cpu-world.com/CPUs/Jaguar/AMD-Athlon%205350%20-%20AD5350JAH44HM.html](http://www.cpu-world.com/CPUs/Jaguar/AMD-Athlon%205350%20-%20AD5350JAH44HM.html)

Kernel:

```

# uname -a
Linux szomoru-desktop 4.4.0-51-generic #72-Ubuntu SMP Thu Nov 24 18:29:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

CPU svm flag for AMD virtualization

```

# cat /proc/cpuinfo | grep svm
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb bpext perfctr_l2 hw_pstate proc_feedback vmmcall bmi1 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshol

```

Loaded modules

```

# cat /etc/modules
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd
#kmv_intel

```

```

# cat /etc/initramfs-tools/modules
pci_stub ids=1002:9830,1002:9840,1022:780d
radeon

```
I updated every time with update-initramfs -u

I get no IOMMU or AMD-Vt messages, but I get something related to IOMMUv2 for not being supported

```

# dmesg | grep AMD
[    0.000000]   AMD AuthenticAMD
[    0.000000] RAMDISK: [mem 0x33806000-0x35bfafff]
[    0.000000] ACPI: SSDT 0x000000009CEFCB48 000E58 (v01 AMD    AGESA    00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 0x000000009CEFD9A0 0046B7 (v02 AMD    AGESA    00000002 MSFT 04000000)
[    0.000000] ACPI: CRAT 0x000000009CF02058 0003F8 (v01 AMD    AGESA    00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 0x000000009CF02450 0006CA (v01 AMD    CPMADPS4 00000001 INTL 20051117)
[    0.000000] ACPI: SSDT 0x000000009CF02B20 001120 (v01 AMD    CPMCMN   00000001 INTL 20051117)
[    0.203420] smpboot: CPU0: AMD Athlon(tm) 5350 APU with Radeon(tm) R3 (family: 0x16, model: 0x0, stepping: 0x1)
[    0.203462] Performance Events: AMD PMU driver.
[    1.445858] perf: AMD NB counters detected
[    1.445865] perf: AMD L2I counters detected
[    1.445988] perf: AMD IBS detected (0x000000ff)
[    1.503912] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.517511] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.156550] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    2.158760] AMD IOMMUv2 functionality not available on this system
[    2.216726] ATOM BIOS: AMD
[   18.470521] AMD64 EDAC driver v3.4.0

```


I tried here amd_iommu=on, iommu=1, iommu=soft, iommu=1, etc, everything ( [https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt) ) 

```
 
# cat /etc/default/grub
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on"
GRUB_CMDLINE_LINUX=""

```
I updated every time with update-grub

```

# cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.4.0-51-generic root=UUID=9ace4a7f-7e0c-48f9-98de-edbbe0f0009c ro amd_iommu=on

```


And of course the famous script for starting the vm:

```

# cat gamebox.sh
#!/bin/bash


configfile=/etc/gamebox-vm.cfg


vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id


}


modprobe vfio-pci


cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done


# -cpu host,kvm=off


sudo qemu-system-x86_64 -enable-kvm -M q35 -m 6144 -cpu host,kvm=off \
-smp 2,sockets=1,cores=2,threads=1 \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=00:01.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=00:01.1,bus=root.1,addr=00.1 \
-device vfio-pci,host=00:10.0,bus=pcie.0 \
-device vfio-pci,host=00:12.0,bus=pcie.0 \
-device vfio-pci,host=00:12.2,bus=pcie.0 \
-device vfio-pci,host=00:13.0,bus=pcie.0 \
-device vfio-pci,host=00:13.2,bus=pcie.0 \
-drive file=/data/vm/gamebox.img,id=disk-os,format=raw,if=none,cache=none -device ide-hd,bus=ide.0,drive=disk-os \
-drive file=/data/vm/win10.iso,id=isocd, -device ide-cd,bus=ide.1,drive=isocd \
-device e1000,netdev=tunnel -netdev tap,id=tunnel,ifname=vnet0 \
-boot menu=on \


# -device vfio-pci,host=00:13.2,bus=pcie.0 \

```

Everything seems to fail due to the fact that /sys/kernel/iommu_groups/ is empty so no iommu with pt was loaded.

I found that there are some bugs related to this for the 4.4.0 kernel.

Thank you

---

### Post by KillerKelvUK on 2016-12-06
Have you tried the amd_iommu=force_isolation and iommu=pt kernel parameters?

Regards the UEFI settings, mine (granted intel ASRock mobo) had 2 separate settings enabling/disabling both virtualisation and IOMMU, one under CPU and one under Chipset?

---

### Post by zmoky2 on 2016-12-06
I tried what you suggested. I have no option for Virtualization under the Chipset menu. I only have the  SVM option to Enable/Disable and in the description it says that is for AMD HW PT virtualization .
Here is the manual ( [http://asrock.pc.cdn.bitgravity.com/Manual/AM1B-ITX.pdf](http://asrock.pc.cdn.bitgravity.com/Manual/AM1B-ITX.pdf) ) . At page 42 of the pdf you can see the SVM enabling option.

I added also the flags for the kernel booting option but nothing happend.

When I run the gamebox.sh script it get the following output:

```

# ./gamebox.sh
W: /etc/qemu-ifup: no bridge for guest interface found
WARNING: Image format was not specified for '/data/vm/win10.iso' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 0]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 1]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 2]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 3]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 4]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 5]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 6]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 7]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 8]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 9]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 12]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 13]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 14]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 15]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 16]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 17]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 23]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 24]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 0]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 1]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 2]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 3]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 4]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 5]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 6]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 7]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 8]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 9]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 12]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 13]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 14]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 15]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 16]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 17]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 23]
warning: host doesn't support requested feature: CPUID.80000001H:EDX [bit 24]
qemu-system-x86_64: -device vfio-pci,host=00:01.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: error no iommu_group for device
qemu-system-x86_64: -device vfio-pci,host=00:01.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device initialization failed

```

---

### Post by KillerKelvUK on 2016-12-07
Looking at your mobo I'd say it doesn't support AMD-Vi which is the directed I/O virtualisation that Intel calls VT-d...basically you need this for IOMMU separation of your PCI devices which is why you are getting the error message saying "vfio: error no iommu_group for device".

NOTE:  AMD-V is not the same as AMD-Vi, see here [http://www.virtualizationadmin.com/blogs/lowe/news/difference-between-amd-vintel-vt-x-and-amd-viintel-vt-d-188.html](http://www.virtualizationadmin.com/blogs/lowe/news/difference-between-amd-vintel-vt-x-and-amd-viintel-vt-d-188.html)

---

### Post by zmoky2 on 2016-12-07
Yes, you right. The manual states clearly that it supports the AMD-V, nothing about AMD-Vi.

Thank you

---

