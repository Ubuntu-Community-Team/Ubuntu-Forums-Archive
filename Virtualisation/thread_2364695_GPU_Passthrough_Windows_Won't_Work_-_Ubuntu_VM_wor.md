---
title: "GPU Passthrough Windows Won't Work - Ubuntu VM works! (nvidia-smi) - stuck"
date: 2017-06-26
forum: Virtualisation
---

### Post by boredofthis on 2017-06-26
So as much as I feel I have tried everything I obviously have not but I am at a complete brick wall now. Especially considering one works but windows does not.

*Please Ubuntu gods give me some pointers.*

Ubuntu running in a VM works, Nvidia-smi and external screen turns on with display manager - PERFECT :)
Windows 10 (or 7 also tried) continue to get error 43 whatever I do - NOT GOOD :(

I am a little confused as to why my Ubuntu running in a VM can operate perfectly with official NVidia windows drivers but I fail to get anywhere with windows.

I will go into in detail below (in the hope it can help others in the future as well as thought checking myself).

**H/W Configuration:**
[LIST]
[*]Ubuntu server 17.04
[*]i7700k
[*]Geforce 1080
[*]32GB RAM
[*]Intel IGP
[/LIST]

**S/W Configuration:**

_GRUB default command line ( probably overkill )_
```

pcie_acs_override=downstream nofb nomodeset vga=normal video=vesafb:off i915.enable_hd_vgaarb=1 i915.modeset=0 intel_iommu=on iommu=pt rd.driver.pre=vfio-pci
```

_/etc/modprobe.d/local.conf_```
options kvm allow_unsafe_assigned_interrupts=1
options vfio-pci ids=10de:1b80,10de:10f0
options vfio-pci disable_vga=1
```

_/etc/initramfs-tools/modules.conf_```
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```


_/etc/modprobe.d/blacklist.conf_```
blacklist nouveau
blacklist lbm-nouveau
```


If I check the passthrough, lspci -nnk I see they are indeed using the right driver.

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104 [GeForce GTX 1080] [10de:1b80] (rev a1)
        Subsystem: Dell GP104 [GeForce GTX 1080] [1028:3366]
        Kernel driver in use: vfio-pci
        Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GP104 High Definition Audio Controller [10de:10f0] (rev a1)
        Subsystem: Dell GP104 High Definition Audio Controller [1028:3366]
        Kernel driver in use: vfio-pci
        Kernel modules: snd_hda_intel
```


Checking the kernel log, dmesg|grep -i vfio
```
[    3.136766] VFIO - User Level meta-driver version: 0.3
[    3.140229] vfio-pci 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[    3.157852] vfio_pci: add [10de:1b80[ffff:ffff]] class 0x000000/00000000
[    3.177847] vfio_pci: add [10de:10f0[ffff:ffff]] class 0x000000/00000000
```

I would say that looks ideal.
[B]
VM Configuration
[/B]
Hiding the VM from nvidia, all configurations have the following:
```
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
      <vendor_id state='on' value='yesplease'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-passthrough'/>
```

The PCIE passthrough part:
```
   <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x05' slot='0x00' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x06' slot='0x00' function='0x0'/>
    </hostdev>

```
For Ubuntu VM I am running UEFI and the GPU is passed through, confirmed with NVidia-smi.
If I want to do it via Qemu command line with novga then I run the following:
```
qemu-system-x86_64 -machine pc-i440fx-zesty,accel=kvm -cpu Skylake-Client,kvm=off -smp 1,sockets=1,cores=1,threads=1 -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/ub_VARS.fd,if=pflash,format=raw,unit=1 -m 1024 -drive file=/var/lib/libvirt/images/ub.qcow2,format=qcow2,if=none,id=drive-ide0-0-0 -device ide-hd,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0,bootindex=1 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x8 -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x9 -vga none
```



Onto Windows, I cannot for the life of me get windows to not give an error 43.
I have tried 
[LIST]
[*]various Bios and UEFI configurations of both Q35 and I440FX
[*]the hiding configuration above
[*]various NVidia drivers (if anyone has a tip for one that works please let me know)
[*]Enabling MSI for the devices in windows via the registry (only the HD audio device gets a negative IRQ the card stays yellow)
[/LIST]

Here is my full windows config:
```
<domain type='kvm'>
  <name>win10q35</name>
  <uuid>0a706dcb-9b07-4d72-8c05-6ca16d25835b</uuid>
  <memory unit='KiB'>12582912</memory>
  <currentMemory unit='KiB'>12582912</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-2.8'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10q35_VARS.fd</nvram>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
      <vendor_id state='on' value='yesplease'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-passthrough'/>
  <clock offset='localtime'>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>destroy</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/en_windows_10_enterprise_n_version_1703_updated_march_2017_x64_dvd_10189280.iso'/>
      <target dev='sdb' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/win10q35.qcow2'/>
      <target dev='sdc' bus='sata'/>
      <address type='drive' controller='0' bus='0' target='0' unit='2'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x7'/>
</controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1d' function='0x2'/>
    </controller>
    <controller type='sata' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'/>
    <controller type='pci' index='1' model='dmi-to-pci-bridge'>
      <model name='i82801b11-bridge'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1e' function='0x0'/>
    </controller>
    <controller type='pci' index='2' model='pci-bridge'>
      <model name='pci-bridge'/>
      <target chassisNr='2'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </controller>
    <controller type='pci' index='3' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='3' port='0x10'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </controller>
    <controller type='pci' index='4' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='4' port='0x18'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </controller>
    <controller type='pci' index='5' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='5' port='0x20'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </controller>
    <controller type='pci' index='6' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='6' port='0x28'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:1a:37:56'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x02' function='0x0'/>
    </interface>
<input type='tablet' bus='usb'>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
    </graphics>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x05' slot='0x00' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x06' slot='0x00' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x04' slot='0x00' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```


I really appreciate any help with this. thanks :)

---

### Post by KillerKelvUK on 2017-06-27
Hey, I think your problem might be the hypervclock you've enabled for the windows guest, try removing the following line from your xml...

```

 <timer name='hypervclock' present='yes'/>

```

---

### Post by boredofthis on 2017-06-27
I just tried that and removing the clock tags completely but no difference I am afraid. 
I just cannot see why windows will not work but Ubuntu does. That is surely a sign that my passthrough settings are correct and my VM settings are not?

I do see this in my kernel logs but I don't think that is anything to worry about:


```
[29603.330989] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x900
[29604.849909] vfio-pci 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
[29604.850003] vfio-pci 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
```

---

### Post by KillerKelvUK on 2017-06-27
Well as a comparator here's my kern output grep'd for vfio (at the point I start my Win10 vm)...

```

[Tue Jun 27 13:21:40 2017] vfio-pci 0000:00:1a.0: enabling device (0000 -> 0002)
[Tue Jun 27 13:21:41 2017] vfio_cap_init: 0000:00:1a.0 hiding cap 0xa
[Tue Jun 27 13:21:41 2017] vfio-pci 0000:00:1d.0: enabling device (0000 -> 0002)
[Tue Jun 27 13:21:41 2017] vfio_cap_init: 0000:00:1d.0 hiding cap 0xa
[Tue Jun 27 13:21:41 2017] vfio-pci 0000:09:00.0: enabling device (0400 -> 0402)

```

Have you dumped the vbios on the card already, if not maybe time to try that map that into your xml as a file?

When you say you got this working in an Ubuntu vm, how do you verify it was nvidia and not nouveau?

---

### Post by boredofthis on 2017-06-27
Sorry for the delay, work always gets in the way!

Do you use Virsh or qemu directly? Is it possible to see your full set of config/options?

I did dump the rom, echo one to make it readable, cat it out and then 0 back.
that resulted in a 60k file, I am not sure if that is the right size or not but if I look inside I see NVidia strings.
I tried that rom with windows but it made no difference, for Ubuntu I have not been using the rom at all.



So on the Ubuntu vm it is definitely Nvidia:

Host dmesg when running ub(not ubuntu vm):
```
[40260.128146] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x900
[40261.731635] virbr0: port 2(vnet0) entered learning state
[40261.896538] vfio-pci 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
[40261.896633] vfio-pci 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
```

All the rest on now run on the Ubuntu vm:
NVidia-smi:
```
Tue Jun 27 11:56:06 2017       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 375.66                 Driver Version: 375.66                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1080    Off  | 0000:00:08.0     Off |                  N/A |
|  0%   50C    P0    36W / 180W |      0MiB /  8114MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```


dmesg | grep -i NVidia

```
[    1.246546] nvidia: loading out-of-tree module taints kernel.
[    1.246943] nvidia: module license 'NVIDIA' taints kernel.
[    1.250396] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    1.309401] nvidia 0000:00:08.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[    1.309594] nvidia-nvlink: Nvlink Core is being initialized, major device number 245
[    1.309680] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  375.66  Mon May  1 15:29:16 PDT 2017 (using threaded interrupts)
[    1.310714] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  375.66  Mon May  1 14:33:30 PDT 2017
[    1.311299] [drm] [nvidia-drm] [GPU ID 0x00000008] Loading driver
[    3.397498] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 244
[    4.892536] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:09.0/sound/card1/input4
[    4.892577] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:09.0/sound/card1/input5
[    4.892610] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:09.0/sound/card1/input6
[    4.892645] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:09.0/sound/card1/input7
```

Hashcat, quick check of opencl:
```
root@ub:~# hashcat -b
hashcat (v3.30) starting in benchmark mode...
OpenCL Platform #1: NVIDIA Corporation
======================================
* Device #1: GeForce GTX 1080, 2028/8114 MB allocatable, 20MCU
Hashtype: MD4


Speed.Dev.#1.....: 45517.6 MH/s (58.94ms)


```

---

### Post by KillerKelvUK on 2017-06-27
No need to apologise its all time for free here...

I use virsh, will post back my xml in a mo, just need to reconfigure the windows guest as I split my GTX's between Windows for gaming/VR and Ubuntu for eth mining.

Have a look [https://www.techpowerup.com/vgabios/](https://www.techpowerup.com/vgabios/) for your vbios, usually a comprehensive collection that you can just download as dumping them can be an issue.

Your ubuntu passthrough as you say looks good, nvidia-smi would complain if you were getting the code 43 equivalent.  How does the kern output differ between the ubuntu vm and windows, do you get the same rom header signature issues?  A quick google would suggest the error is harmless and unrelated.

---

### Post by KillerKelvUK on 2017-06-27
So my guest xml...

```

<domain type='kvm' id='10'>
  <name>blackwindowspro</name>
  <uuid>xxx-clipped-xxx</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>6</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-q35-2.8'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/blackwindowspro_VARS.fd</nvram>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='4096'/>
      <vendor_id state='on' value='blackKVM'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='host-passthrough'>
    <topology sockets='1' cores='3' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/mnt/virt/vms/blackwindowspro.qcow2'/>
      <backingStore/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x04' slot='0x00' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/mnt/virt/vms/blackwindowspro_games.qcow2'/>
      <backingStore/>
      <target dev='vdb' bus='virtio'/>
      <alias name='virtio-disk1'/>
      <address type='pci' domain='0x0000' bus='0x09' slot='0x00' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <boot order='2'/>
      <alias name='sata0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='sata' index='0'>
      <alias name='ide'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1f' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pcie-root'>
      <alias name='pcie.0'/>
    </controller>
    <controller type='pci' index='1' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='1' port='0x10'/>
      <alias name='pci.1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </controller>
    <controller type='pci' index='2' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='2' port='0x18'/>
      <alias name='pci.2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </controller>
    <controller type='pci' index='3' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='3' port='0x20'/>
      <alias name='pci.3'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </controller>
    <controller type='pci' index='4' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='4' port='0x28'/>
      <alias name='pci.4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='pci' index='5' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='5' port='0x30'/>
      <alias name='pci.5'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <controller type='pci' index='6' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='6' port='0x38'/>
      <alias name='pci.6'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </controller>
    <controller type='pci' index='7' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='7' port='0x8'/>
      <alias name='pci.7'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </controller>
    <controller type='pci' index='8' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='8' port='0x40'/>
      <alias name='pci.8'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </controller>
    <controller type='pci' index='9' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='9' port='0x48'/>
      <alias name='pci.9'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </controller>
    <controller type='pci' index='10' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='10' port='0x50'/>
      <alias name='pci.10'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </controller>
    <controller type='pci' index='11' model='dmi-to-pci-bridge'>
      <model name='i82801b11-bridge'/>
      <alias name='pci.11'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x1e' function='0x0'/>
    </controller>
    <controller type='pci' index='12' model='pci-bridge'>
      <model name='pci-bridge'/>
      <target chassisNr='12'/>
      <alias name='pci.12'/>
      <address type='pci' domain='0x0000' bus='0x0b' slot='0x00' function='0x0'/>
    </controller>
    <controller type='pci' index='13' model='pcie-root-port'>
      <model name='ioh3420'/>
      <target chassis='13' port='0x58'/>
      <alias name='pci.13'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <alias name='virtio-serial0'/>
      <address type='pci' domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
    </controller>
    <controller type='usb' index='0' model='nec-xhci'>
      <alias name='usb'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='xxx-clipped-xxx'/>
      <source bridge='br0'/>
      <target dev='vnet1'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/1'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/1'>
      <source path='/dev/pts/1'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0' state='connected'/>
      <alias name='channel0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'>
      <alias name='input0'/>
    </input>
    <input type='keyboard' bus='ps2'>
      <alias name='input1'/>
    </input>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x00' slot='0x14' function='0x0'/>
      </source>
      <alias name='hostdev0'/>
      <address type='pci' domain='0x0000' bus='0x0c' slot='0x01' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x00' slot='0x1a' function='0x0'/>
      </source>
      <alias name='hostdev1'/>
      <address type='pci' domain='0x0000' bus='0x0c' slot='0x02' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x00' slot='0x1d' function='0x0'/>
      </source>
      <alias name='hostdev2'/>
      <address type='pci' domain='0x0000' bus='0x0c' slot='0x03' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x09' slot='0x00' function='0x0'/>
      </source>
      <alias name='hostdev3'/>
      <address type='pci' domain='0x0000' bus='0x06' slot='0x00' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <driver name='vfio'/>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <alias name='hostdev4'/>
      <address type='pci' domain='0x0000' bus='0x07' slot='0x00' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <stats period='5'/>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x05' slot='0x00' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='none' model='none'/>
  <seclabel type='dynamic' model='dac' relabel='yes'>
    <label>xxx-clipped-xxx</label>
    <imagelabel>xxx-clipped-xxx</imagelabel>
  </seclabel>
</domain>

```


[ATTACH=CONFIG]275789[/ATTACH]

---

### Post by boredofthis on 2017-06-27
thanks!
I see you do not use a gpu rom either.
Out of interest what Nvidia graphics driver are you running in windows?

A quick look on vgabios tells me 60K is not big enough for my GPU rom. I do find it weird though that it works without it in Ubuntu VM so I thought the same should be true in windows. Problem is my card looks to have a dell specific subsystem code and as such is relatively uncommon i.e not in the database. I will have a bit more of a play with dumping it now I know how big it should be, also it appears to just be a PNY GTX 1080 8GB founders edition rebranded... So I could try loading(not flashing) a PNY rom which is in the DB.

In terms of the header signature yes Ubuntu does the same.

I just had a thought... Haven't tested it yet. I am using the 'sata' or 'ide' io driver for my virtual HDD (uefi/bios) and not the VIRTIO driver. I wonder if Nvidia is detecting that...

Also does it matter how the host OS is booted, UEFI vs BIOS? I notice my host is bios booted, i.e. no [FONT=Consolas]/sys/firmware/efi[/FONT]

How is the eth mining going? Took quite the hit this week!

---

### Post by KillerKelvUK on 2017-06-27
I've got both a 970 4GB and 1070 8GB both Asus Strix.

Can't see how the nvidia drivers would be balking at using sata for disk, switching to virtio however will give you better performance so I'd say switch is regardless.

Regards your host boot and legacy vs UEFI, its been a while since I've been interested in this to research it. I can tell you my host is 17.04 which is UEFI booted and my bios has CSM active and all my guests for passthrough us OVMF. So this could be a gfx handoff issue between host bios -> OVMF - > windows bootloader which is obviously different in the ubuntu alternative...I'm reaching here tbh I'd suggest you research further and maybe some of the other members here will pick up on this point for you.

One last thing is that I've seen windows installations complain about code 43 for no other reason than they've had lots of driver install attempts and different driver versions tried. If you have the time/patience to do a clean install with a good looking set of xml I'd recommend it but as a minimum, you should look to use a driver cleanup tool to ensure your guest os is as virgin as possible (albeit from the QXL virt gfx).

p.s. don't wind me up about eth this week:lolflag:...not!  Glad I'm only new to it so I don't have a lot of bank in it, looks like coinbase will refund those who lost out of the fire sales but wow did it drop!

---

### Post by KillerKelvUK on 2017-06-27
Thought, have you tried without the hyperv in your xml.  17.04 stock has the right libvirt and qemu versions to use the latest hacks but you might as well try it before anything more intrusive.

---

### Post by boredofthis on 2017-06-27
I have tried without hyperv in my xml. removing the whole thing, hiding it, only removing the line from the clock etc. I feel I've tried every combo but obviously I haven't.

In terms of clean windows, I have a few windows 10 VMs now in my host depending on bios / uefi config etc. All of them have a snapshot before any driver installs so I keep rolling back and taking it from there.

Interesting to hear about the uefi boot of your Ubuntu. I will try and modify my host to boot uefi. I let it go with legacy as I couldn't for the life of me get grub to install on my nvme with the Ubuntu installer. So I added a USB stick and boot off that for the moment. But....once again it works in Ubuntu vm!

Things I will try:
[LIST]
[*]Host boot as UEFI
[*]Virtio for my disks
[*]Butcher your config
[/LIST]


Yeh I am pretty new to eth also, I see NVidia announced a line of cryto cards today. Dedicated ASICs are the way to go. I have friends that bought in at $8, how silly I feel!

---

### Post by KillerKelvUK on 2017-06-27
Dude I just realised your xml still has the virtual gfx adapter included (QXL), that causes the nvidia drivers to 43 if I remember.  Have you tried without that?  You also need to remove and rescan for new devices in windows to set back up again...just in case ;-)

---

### Post by boredofthis on 2017-06-27
I cannot seem to remove that with virsh or virt-manager it keeps coming back? how do you mean remove it?
I have also tried using only qemu at the console with -vga none which I think is the same thing?

```
qemu-system-x86_64 -machine pc-q35-2.8,accel=kvm -cpu host,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff,hv_vendor_id=yesplease,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win10q35_VARS.fd,if=pflash,format=raw,unit=1 -m 12288 -drive file=/var/lib/libvirt/images/win10q35.qcow2,format=qcow2,if=none,id=drive-sata0-0-2 -device ide-hd,bus=ide.2,drive=drive-sata0-0-2,id=sata0-0-2,bootindex=1 -device vfio-pci,host=01:00.0,multifunction=on -device vfio-pci,host=01:00.1 -vga none
```

---

### Post by KillerKelvUK on 2017-06-27
Virt-manager will always keep a virtual graphics adapter present if you have a display adapter also in the config i.e spice or vnc. So to remove it you need to first remove the display adapter and then the graphics adapter. If you still can't remove it then you have a problem/dependency elsewhere causing this.

As for trying this directly with qemu you are right but if you tried this on an install that had previously had the qxl present and didn't force windows to reload the driver then this could still cause a 43.

I always set my windows guests up clean using qxl and spice to start with and get them to the point where I'm ready to start passing through the Nvidia card. I then shutdown pullout spice and qxl and anything else I don't need and from that point forward nothing changes until nvidia is in and working.

---

### Post by boredofthis on 2017-06-27
how do you install the NVidia driver once you pull out qxl and spice, i.e. no virtual screen to see what you are doing?

---

### Post by KillerKelvUK on 2017-06-27
So the screen connected to your nvidia card should output OVMF, windows will boot with a basic graphics adapter at a low resolution to get you to a desktop so you need just keyboard and mouse so either usb attach them to the guest or use synergy to share your hosts keyboard & mouse.  Synergy requires prior setup so if this is new to you Id recommend you start with usb attaching your host keyboard and mouse to get you started.

---

### Post by boredofthis on 2017-06-27
Now that is interesting. This is what I thought but my setup doesn't do that. I do not get any output when doing that. However I do with Ubuntu and -vga only

---

### Post by KillerKelvUK on 2017-06-28
Okay so take your ubuntu guest, make the CDROM boot priority and attach your windows iso...does that get you to a installer on the hdmi out the nvidia card?

---

### Post by boredofthis on 2017-06-28
Sorry what I mean is vga none only works in Ubuntu when the nvidia driver or nouveau driver is installed. 
And only when loading xorg, no frame buffer or Vesa output I guess

I found this online which is supposed to test out if the screen turns on, mine does not. 
```

#!/bin/bash

cp /usr/share/ovmf/OVMF.fd /tmp/my_vars.fd
qemu-system-x86_64 \
  -enable-kvm \
  -m 2048 \
  -cpu host,kvm=off \
  -vga none \
  -device vfio-pci,host=01:00.0,multifunction=on,x-vga=on \
  -device vfio-pci,host=01:00.1 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/ovmf/OVMF.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd


 .  
```

---

### Post by KillerKelvUK on 2017-06-28
So your script didn't work for me either, had to ditch x-vga=on to get it to work.

x-vga is only need for primary gfx assignment.  If you get ovmf output without it then you're good to go I'd say.

---

### Post by boredofthis on 2017-06-28
yeh I tried without the x-vga also and still nothing. 
It is really odd, like it is only operating in certain modes

---

### Post by KillerKelvUK on 2017-06-28
Post back your working xml & qemu cmd for ubuntu will you?

---

### Post by boredofthis on 2017-06-28
sure.
So with virsh this XML brings up a virtual screen and the NVidia card is addressable at the command line (no screen turns on)

```
<domain type='kvm'>
  <name>ub</name>
  <uuid>1459f57e-68f0-43ff-9d74-eeeccbb9e0e7</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-zesty'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/ub_VARS.fd</nvram>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Skylake-Client</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/ub.qcow2'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:a5:21:a2'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='1'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

and here is the QEMU that will bring up the screen but only for Xorg, I do not see anything boot (FB):

```
qemu-system-x86_64 -machine pc-i440fx-zesty,accel=kvm -cpu Skylake-Client,kvm=off -smp 1,sockets=1,cores=1,threads=1 -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/ub_VARS.fd,if=pflash,format=raw,unit=1 -m 1024 -drive file=/var/lib/libvirt/images/ub.qcow2,format=qcow2,if=none,id=drive-ide0-0-0 -device ide-hd,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0,bootindex=1 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x8 -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x9 -vga none
```

---

### Post by KillerKelvUK on 2017-06-28
Sorry I'm not following you regards what happens with the qemu cmdline, please can you elaborate?

---

### Post by boredofthis on 2017-06-28
yes I guess that wasn't too clear! Sorry.
So I installed Ubuntu using a virtual screen. When I use that Qemu command line the first thing I see is the display manager screen asking me to log into my desktop, Xorg. While Ubuntu is booting I do not see the uefi screen, kernel booting logs display nothing until Xorg starts.

---

### Post by KillerKelvUK on 2017-06-28
So the nvidia drivers have an issue with the efi framebuffer which for me means I don't get boot text...well actually that's not correct, I get OVMF, Grub, then blank screen until lightdm kicks in with a login prompt, this can be remided by switching out grub for the efi stub loader but if you aren't fussed about it then you don't need the extra hassle.  What version of ubuntu have you installed, is it possible your missing grub because you've installed the desktop version which I think usually hides grub?  Is it also possible you're just missing ovmf because its completing before you switch inputs or your monitor is detecting the new input?

Things to try to prove this, shove a load a ram into the guest as this should cause ovmf to lag around a little longer, if you have keyboard and mouse input you should also be able to keystroke (del or F2 maybe) into the ovmf menu. Similarly with grub either reconfigure it to be visible or use 'shift' i think at boot time to reveal it.

I'll be honest bud at first I though you had a bad setup all through but with getting it working via qemu that would simply suggest your libvirt setups & installs are busted.  Are you running all stock binaries from ubuntu or do you have other ppa's or builds in their?

---

### Post by boredofthis on 2017-06-28
Damn, thanks for helping with this BTW. I do really appreciate your help and your knowledge!
In the VM I have the same version as the host (had the iso sitting around), 17.04 server.

No custom PPAs, this is a stock Server 17.04 install. I am beginning to think this is just not something that will work with this hardware setup. My real host bios does not have a lot of options for configuration either which sucks.

---

### Post by KillerKelvUK on 2017-06-28
So I'm gunna have to bail for the rest of this evening as its my bday and I got a bottle of single malt to smash but I hate being beaten so I'm not one for giving up on this if you aint.

If you definitely don't think you're getting ovmf and grub output then I rek next is to get your host uefi booting, shouldn't be much of a hassel to reverse in.  As for your host uefi as long as you have vt-x and vt-d enabled and have set its primary boot gfx to be the intel igd then you should be good!  Do you have any other pci devices to prove passthrough with like a sound, dvb, usb pcie card?

---

### Post by boredofthis on 2017-06-28
Happy Birthday man! Ohh I do love a single malt! Still really love aberlour abundah these days. Enjoy! 
I am not giving up, I refuse :) I am just going to try and get the host to boot with uefi tonight. I am starting to think there might be something in that. Great minds ;)

I could indeed try passing through a usb pcie card but I think the pass through is proven to a part. I can mine eth in Ubuntu in a vm.
I also just picked up a couple of display port adapters from work in case it is trying to output but using the wrong connector ( I know it shouldn't but worth trying everything ).

I will keep you posted.

---

### Post by KillerKelvUK on 2017-06-28
Abundah's a nice tipple! got the Ardbeg out now :-)

Eth recovering slowly but surely haha

i should avoid offering help when I've had a drink but I do recall getting dragged onto a support call at 2am after a rather heavy night and stu-muttering "hosts file" to the 8 strong team of engineers who all tutted simultaneously and then who all cheered when it was a borked hosts file, their 5 hours to my 5 minutes lol and who says booze is bad for you &#128556;

---

### Post by boredofthis on 2017-06-28
hah those are the best calls :) Ardberg is a good choice

---

### Post by boredofthis on 2017-06-30
Hope the hang over wasn't too bad and you had a great night. So i have tried quite a few more things but none with any success.


I decided to start a fresh install of ubuntu server 17.04 onto an external harddrive this time and boot it UEFI, that way i can keep a windows install on my nvme and still have a functional PC.

Using windows I booted it and used 'gpuz' to dump the bios of my GPU ROM, ~256KB, looks much better. I used the tool (cannot remember it's name) to check it was valid and supported EFI. It is and does.

Now i tried the previous installs, new install, script to check video card output without an os image etc etc with and without the ROM and no output.
I can get windows to see the Nvidia card but always 43, there is never any 'boot' VESA output though.

Swearing that I was going insane i downloaded 'unRaid' to see if that made any difference and if so 'snoop' on their stock 'windows 10' config file. Nothing different and i was doing the right thing. I have to be honest they have put quite a nice customisation together. No real need for me as i have a synology nas though. Either way windows 10 booted up with unraid but i still couldn't get anything to VESA output on the screen. I managed to pass through the intel IGP and have it seem functional in terms of drivers, no errors in device managed and VNC showed two screens. But i still could not get any output to my physical screen. Nvidia 1080 was still error 43.

Things I noticed / extra details
[LIST]
[*]Machine is a dell XPS 8920 which does not allow me to select the primary GPU in the bios ( i assume it has a mux)
[*]IGP has a single HDMI, GTX 1080 has 3 display ports, 1 HDMI and 1 DVI-D
[*]Booting windows natively on this PC and only having the IGP connected will not show the bios or the boot screen on the display. Only once windows has loaded (IGP driver loaded?) does the screen turn on. Doing the same thing but into the GTX 1080 HDMI shows everything including bios POST.
[*]Booting Ubuntu without first kicking off a VM with passthrough but with the devices assigned to vfio_pci the Screen (HDMI) stays on but black, no output. Starting a VM makes this change and then the screen turns off due to no signal.
[/LIST]

---

### Post by KillerKelvUK on 2017-07-01
Hey, hangover cleared eventually :-)

Lot of work you've done!

So this reads like your XPS boots and auto selects the Nvidia card as the primary which from what I understand makes it part of the VGA arbitration process which is why you can't get any VESA output and probably why then it code 43.  You see I would have expected the IGP to be extremely difficult assign as this typically falls under the category of Primary GFX Assignment.  For me my UEFI allows me to select the primary GFX either internal or PCI but if yours is auto selecting then your options are going to be limited.  So the guys over at Arch have done quite a bit on primary graphics assignment, it effectively requires your to decouple as much of the host as possible from the primary card so certainly no GUI, ditch the frame buffer and a few other things.  From this the primary card can then be extricated from the host and assigned to a guest...if you could get this working you could then have a tri-os configuration i.e. a very simple light host os running nothing but virt, then a guest using intel IGP passthrough for your linux desktop and another windows guest using your nvidia.

Alternatives???  Hack your UEFI, see if someone out there has had the same issue with the XPS and has a custom hack for you...its been known.  Take out the nvidia card to prove your Intel IGP does become primary for all boot output, would prove the UEFI is auto-selecting.  You could then see if the auto-select is affected by which PCI slot the nvidia card is in maybe.

A quick google finds others in your space, maybe they have some info you've not had to hand previous?

[https://bbs.archlinux.org/viewtopic.php?id=208065](https://bbs.archlinux.org/viewtopic.php?id=208065)
[http://us.informatiweb.net/tutorials/it/9-bios/230--force-the-use-of-the-internal-graphics-card-onboard-vga.html](http://us.informatiweb.net/tutorials/it/9-bios/230--force-the-use-of-the-internal-graphics-card-onboard-vga.html)

---

### Post by boredofthis on 2017-07-01
yeh this is what I was afraid of but I am not giving up just yet.
Thing is,  I still go back to my GTX 1080 being able to output to my monitor when I start Ubuntu in a vm! That part I still don't understand. 

I did the same thing as the guy in the first link already, that is manage to get IGP output for the kernel boot but not the bios on the IGP monitor using fbcon=map:1**. **That doesn't really help my problem though, same issue whether it is assigned or not.
I will try taking the NVidia out to prove that. I am intrigued to know if adding another GPU would force that as primary but I doubt it. I think the 16x slot if filled normally becomes primary

---

### Post by KillerKelvUK on 2017-07-04
Any luck with this?

---

### Post by boredofthis on 2017-07-04
I have a stack of new things to try out but haven't got around to it yet.  I'll post back when I do for sure. 
Today is actually my birthday this time! Brit living in America with July the 4th birthday! Ironic.

---

### Post by KillerKelvUK on 2017-07-04
Oh my, way to go!  Well have a great day and enjoy a dram or three :-)

---

### Post by boredofthis on 2017-08-09
Just wanted to kick this thread to keep it alive. Still haven't got around to looking into this more but I intend to this week.
I have been away from home for the last month but back now.

---

### Post by KillerKelvUK on 2017-08-10
Ah-ha once more into the fray!

---

### Post by heiko_s on 2017-08-27
Allow me to add my 2C worth of confusion. I was reading through the thread and, at first sight, your configuration looks OK (man I hate xml).

I've written a how-to on getting VGA passthrough work with Linux Mint, which should work likewise with Ubuntu. The original how-to is hosted [here]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692"), but I'm hosting my latest version on my own website [https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/]("https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/")

Here my suggestions:

1. Check that your Nvidia graphics card is using the vfio-pci driver:
```
dmesg | grep vfio
```
You should get a similar output to this:
[ 3.294520] vfio-pci 0000:02:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=none
[ 3.311690] vfio_pci: add [10de:13c2[ffff:ffff]] class 0x000000/00000000
[ 3.331711] vfio_pci: add [10de:0fbb[ffff:ffff]] class 0x000000/00000000
[ 9.206363] vfio-pci 0000:02:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=none

In the above output the Nvidia graphics card was added to vfio_pci.

2. Check your IOMMU groups:
```
for a in /sys/kernel/iommu_groups/*; do find $a -type l; done
```
You should get something like this:
…
/sys/kernel/iommu_groups/18/devices/0000:00:1f.3
/sys/kernel/iommu_groups/18/devices/0000:00:1f.2
/sys/kernel/iommu_groups/18/devices/0000:00:1f.0
[B]/sys/kernel/iommu_groups/19/devices/0000:01:00.1
/sys/kernel/iommu_groups/19/devices/0000:01:00.0
[/B]/sys/kernel/iommu_groups/2/devices/0000:00:02.0
/sys/kernel/iommu_groups/20/devices/0000:02:00.1
/sys/kernel/iommu_groups/20/devices/0000:02:00.0
/sys/kernel/iommu_groups/21/devices/0000:05:00.0
/sys/kernel/iommu_groups/21/devices/0000:06:04.0
…

Note: I got 2 discrete graphics cards. In your case 01:00.0 and 01:00.1 should be within their own IOMMU group.

3. Can you post your /etc/default/grub file content, only the part with:
GRUB_CMDLINE_LINUX_DEFAULT=”modprobe.blacklist=nouveau quiet intel_iommu=on”

I saw you used the ACS patch entry in grub, but for that to work you would need a patched kernel.

The ACS override patch is only needed if your IOMMU groups are no good and you get other non-root devices listed together with your graphics card (usually 2 lines - graphics and sound). If that is not the case, you should remove the ACS entry in grub and
```
sudo update-grub
```

4. Note: I'm booting my host via BIOS and my Windows VM using UEFI and I haven't had any problems with that. In the past I also booted the host using UEFI, and the guest either UEFI or SeaBIOS, it all worked. But your situation might be different.

5. I strongly suggest doing UEFI boot for the guest using the OVMF image and variables. Your Nvidia card seems to support UEFI, so there is no reason not to use it.

6. I never had much success using virt-manager, though many people had better luck. I find reading and editing a simple bash script with a qemu command a lot easier and less trouble-prone. My how-to doesn't use virt-manager.

7. I'm using q35 instead of the standard PC (fx440) for a much improved VM performance. If you change that, you would need to reinstall Windows.

8. **error 43**: Usually this error points to the Nvidia driver detecting that Windows runs in a VM. Nvidia drivers have a "bug" in that they won't work within a VM unless your Nvidia graphics card is one of the professional (Quadro etc.) cards. Luckily the kvm team has found a simple workaround. When using the qemu command, use the following:
```
qemu-system-x86_64 \
-machine type=q35,accel=kvm \
-cpu host,kvm=off \

```
The -machine ... accel=kvm option tells qemu to use KVM
The -cpu ... kvm=off option tells qemu to hide kvm from the guest.

If you want to use virsh or virt-manager, the kvm=off option must be there.

9. If the above doesn't help, you may need to reinstall Windows. Just make sure the above conditions are met before starting with the installation.

The how-to I wrote is quite detailed, but unfortunately I don't make any use of virsh. It's up to you to give it a try. The above points are valid no matter which way you take.

Good luck!

---

### Post by boredofthis on 2017-09-03
Wooo I really appreciate this reply. I keep saying I will go back to this and retry and I in all serious will but really haven't had the time.

See the only thing that I think I might have forgotten is making sure the IOMMU groups are correct but in all fairness it has been so much time I just cannot remember.
I still think the issue is down to the GPU mux on my silly Dell XPS 8920, i.e IGP vs PCI slot 0.

All this being said, the place I left this at was that I was able to run an Ubuntu VM in the host Ubuntu system that was able to pass through my GeForce 1080 and use CUDA to perform operations. I.e. success. However if I tried the same thing with windows 10 as the VM then no matter what I did I would end up with the dreaded error in windows and it couldn't utilize the GPU.

Now having said that and a fresh head I really should go back and carefully follow through my working and your post and try again.

Once again I really appreciate the post and will (soon-ish) get back to trying again and posting my results back.

---

### Post by heiko_s on 2017-09-10
The big question is: Is your Dell XPS a laptop or a regular PC. Laptops with Nvidia cards often use Optimus technology that won't let you do VGA passthrough. Your laptop or PC would need to have separate outputs for the internal IGP and the GPU. If that is not the case then it's try and pray.

---

### Post by boredofthis on 2017-09-10
Sure the computer is a desktop. VGA passthrough must be working as I was able to use CUDA in an Ubuntu VM running on top of Ubuntu with pass through all enabled etc. The issue I was having was with windows as the VM.
Yeh it really seems that windows always has the error 43 issue and as such I do not think I can manage passthrough with the current bios I have and windows which is a bit odd (still not giving up just yet though).

Here is the output to my screen that makes me question this. Stock Dell XPS setup running windows 10 natively (i.e no Ubuntu no pass through etc, just running windows normally on the PC).

If I plug the hdmi/dp cable into the **Nvidia GPU** and boot I see the bios screen, POST and all the windows boot up until I am at the windows login screen
If I plug the hdmi cable into the **Intel IGP** and boot I see nothing until the windows login, this to me tells me that the intel GPU driver has sorted this out and by default I would not get any vga output on the intel IGP until the driver load.

---

### Post by heiko_s on 2017-09-24
> **boredofthis said:**
> Sure the computer is a desktop. VGA passthrough must be working as I was able to use CUDA in an Ubuntu VM running on top of Ubuntu with pass through all enabled etc. The issue I was having was with windows as the VM.
Yeh it really seems that windows always has the error 43 issue and as such I do not think I can manage passthrough with the current bios I have and windows which is a bit odd (still not giving up just yet though).

Here is the output to my screen that makes me question this. Stock Dell XPS setup running windows 10 natively (i.e no Ubuntu no pass through etc, just running windows normally on the PC).

If I plug the hdmi/dp cable into the **Nvidia GPU** and boot I see the bios screen, POST and all the windows boot up until I am at the windows login screen
If I plug the hdmi cable into the **Intel IGP** and boot I see nothing until the windows login, this to me tells me that the intel GPU driver has sorted this out and by default I would not get any vga output on the intel IGP until the driver load.

With that out of the way, I believe the problem is a misconfiguration in virt-manager / virsh. My guess is that the Nvidia driver detects kvm and quits with an error 43. If I remember correctly, you may need to manually edit the xml file to add the kvm=off option I described in one of my earlier posts.

An easier way is to not use virt-manager but a little script. See the link to my tutorial in my earlier post.

---

### Post by kevin160 on 2017-10-02
I'm just about to do this again from scratch and was doing over my notes.  So, in case you don't have this fixed yet, problems I had before:

Apparmor:  Check those logs for file access being blocked.

Video BIOS:  This may not affect you, but I had to download an alternative ROM file from TechPowerUP, trim it with a hex editor, and provide it in the vm's xml with <rom file='/home/VM/ROM/660ti_efi_trimmed.rom'/>

Error 43:  Nvidia's windows driver hates people not buying pro cards.  Added 

<features>
    <hyperv>
      <vendor_id state='on' value='1234567890ab'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>


to the <domain type='kvm'>  section.  

Wish me luck getting this going again.

---

