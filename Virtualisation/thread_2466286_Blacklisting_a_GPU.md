---
title: "Blacklisting a GPU"
date: 2021-08-24
forum: Virtualisation
---

### Post by demonenero84 on 2021-08-24
Hello, I took a look at this guide [https://www.youtube.com/watch?v=ID3dlVHDl0c](https://www.youtube.com/watch?v=ID3dlVHDl0c).
To cut a long story short it tells you to make sure to have virtualization extensions enabled ( I enabled vt-d and vt-x ), and after updating your system run a script ( [https://github.com/pavolelsig/passthrough_helper_ubuntu_20](https://github.com/pavolelsig/passthrough_helper_ubuntu_20)), reboot and your second gpu should be bound to [FONT=monospace][COLOR=#000000]vfio-pci.
[/COLOR]After doing that if I run lspci -k I get this one


[/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000]01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050] (rev a1) [/COLOR]
        Subsystem: NVIDIA Corporation GP107 [GeForce GTX 1050] 
        Kernel driver in use: nouveau 
        Kernel modules: nvidiafb, nouveau 
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1) 
        Subsystem: NVIDIA Corporation GP107GL High Definition Audio Controller 
        Kernel driver in use: vfio-pci 
        Kernel modules: snd_hda_intel

Only the audio part is bound to vfio-pci.
[/FONT][/FONT]Any suggestions?
Many thanks in advance, perhaps a noob like me shouldn't start learning ubuntu with these intimidating programs :)

---

### Post by T.J. on 2021-08-24
Hi! *friendly hug* Don't beat yourself up.  

All "newbies" need to be given time to learn, and what works for one GNU/Linux distribution does not always work for another, especially in regards to boot processes.  This is **not** an easy topic!  Even the best of us get confused.  You need to create or edit three files on an Ubuntu install if you want to bind your GPU to the VFIO driver.

/etc/modprobe.d/nvidia.conf  (to prevent the proprietary and opensource Nvidia drivers from being used).

```
blacklist nvidia
blacklist nouveau
blacklist nvidiafb
blacklist nouveaufb
```


/etc/modprobe.d/vfio.conf  (to bind the devices to VFIO) Be sure to include the PCI addresses of both the video card and the onboard audio.  You must have both.  You can obtain them with 

***```
lspci -vnn***
```.

```

options vfio-pci ids=<addresses>

# ex. options vfio-pci ids=10de:1401,10de:0fba


```

You should also add the vfio-pci driver to the init image. 

/etc/initramfs-tools/modules  (to add the vFIO driver to the boot image)

```

 List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
vfio-pci

```

Then run*** ```
sudo update-initramfs -k all -u
``` ***to update your system.  Reboot, and viola, you should be good to go.

Without digressing too much, you may also be required to modify your boot parameters.  A lot depends on your version of GNU/Linux and your firmware.  Please let me know if there is anything else I can do.

---

### Post by MAFoElffen on 2021-08-24
Please go back to your first post and edit it to wrap your output within [noparse]```
 Put_output_and_commands_here 
```[/noparse] tags... One, it makes it easier to read. It then doesn't accidentally screw with the forums software. And keeps you in good grace with the Moderators who have to remind people to do that... Looking after/for you.
(Your link does not work in my locale, but that is not important...)

Wait please...

Where is the information for your *other* Video device? What is the VM Host that you are hosting from? And what will be your Guest VM?

Because some of that is old news and you don't need to do depending on the VM Host you are using. For some systems, it's really isn't that hard anymore. And just bllindly blacklisting resources, with some VM guests is going to make that a problem in some cases now. Especially if the other video resource, is similar enough...)

So lets start from square one. Please provide at least enough information that we may steer you in the right direction...

You know you need two video devices to do a pass through right? Unless it is a headless server... Just saying. Where is the info for that?

---

### Post by T.J. on 2021-08-24
> **MAFoElffen said:**
> Please go back to your first post and edit it to wrap your output within [noparse]```
 Put_output_and_commands_here 
```[/noparse] tags... One, it makes it easier to read. It then doesn't accidentally screw with the forums software. And keeps you in good grace with the Moderators who have to remind people to do that... Looking after/for you.


Thanks for the advice.  I realize you weren't necessarily referring to me, but it does help to outline the commands.

---

### Post by MAFoElffen on 2021-08-24
> **T.J. said:**
> Thanks for the advice.  I realize you weren't necessarily referring to me, but it does help to outline the commands.
Welcome to the Virtualization Section! I wasn't referring to anyone. Just general information. What he is trying to do, he needs to provide some information for others to be able to help him... (In fact, some of us are presently working on a project to help users to be able to easily provide that...)

I am assuming his Host is Ubuntu. That is what it sounds like from what he described. If he is using KVM as his VM Host, he can add a pass-through through  directly from Virt-Manager, by going to his VM Guest's configuration panel, if he checks "Change Configuration before Installation" or from the Guest Details window while it is powered off: 

Add Virtual Hardware > Add Host PCI Device...Then it will display all the host's PCI devices, which when selected, will reserve that specific device for exclusive use by that VM Guest... (it also has a menu for host USB devices)

If he is using VMware, similar. Windowed, GUI driven. No typing or searching to do manually.

He needs to realize that it will be "Exclusive" to just that one VM Guest. He will no longer be able to use it for his host, until it is removed from that VM Guest configurations. The VM Host takes care of the blacklisting.

Depending on what he wants to do, and the guests he wants to run, there are also other options now... Some of us are working with and testing VirGL... Which so far doesn't want to play well yet with NVidia... Other GPU's, better. But, LOL. We'll see how far we can stretch it.

Please do not be a stranger here. User's need help here also.

---

### Post by MAFoElffen on 2021-08-25
A bit preemptive, but to see what kernel VFIO "drivers" are built into your kernel:
```
# cat /lib/modules/$(uname -r)/modules.builtin | grep vfio
kernel/drivers/vfio/vfio.ko
kernel/drivers/vfio/vfio_virqfd.ko
kernel/drivers/vfio/vfio_iommu_type1.ko
kernel/drivers/vfio/pci/vfio-pci.korem
```
They will not list them will lsmod...

---

### Post by T.J. on 2021-08-25
> **MAFoElffen said:**
> Welcome to the Virtualization Section! 

Why thank you so much!

It's been my experience that practicing hardware binding that it is just something that should be encouraged as a way to pass on knowledge.  You are quite welcome to disagree of course.  Using libvirt is not always practical.  In rare cases, it actually causes software issues with Windows installations and certain firmware.  RedHat, the primary developer of virt-manager, has plans to abandon it in favor of "cockpit" last I read; so helping others gain experience is even more important.

> **MAFoElffen said:**
> Depending on what he wants to do, and the guests he wants to run, there are also other options now... Some of us are working with and testing VirGL... Which so far doesn't want to play well yet with NVidia... Other GPU's, better. But, LOL. We'll see how far we can stretch it. 

I sincerely hope your research turns out well. 

> **MAFoElffen said:**
> Please do not be a stranger here. User's need help here also.

I hope I can.

---

### Post by demonenero84 on 2021-08-25
Thanks a lot for the replies:)
So here is my system
> 
Operating System: Kubuntu 21.04
KDE Plasma Version: 5.21.4
KDE Frameworks Version: 5.80.0
Qt Version: 5.15.2
Kernel Version: 5.11.0-31-generic
OS Type: 64-bit
Graphics Platform: X11
Processors: 4 × Intel® Core&#8482; i5-7400 CPU @ 3.00GHz
Memory: 7,6 GiB of RAM
Graphics Processor: Mesa Intel® HD Graphics 630

The GPU that I want to use in my virtual machine is a Nvidia [FONT=monospace][FONT=monospace][COLOR=#000000]GeForce GTX 1050[/COLOR][/FONT][/FONT].
I am using Virtual Machine Manager 3.2.0 "Powered by libvirt" the hypervisor is QEMU/KVM.
I made a Windows XP vm as a quick test and it works fine ( I know that my nvidia card does not support Winxp so I will make my gpu passthrough test with Win10)
> 
I am assuming his Host is Ubuntu. That is what it sounds like from what  he described. If he is using KVM as his VM Host, he can add a  pass-through through  directly from Virt-Manager, by going to his VM  Guest's configuration panel, if he checks "Change Configuration before  Installation" or from the Guest Details window while it is powered off: 

Add Virtual Hardware > Add Host PCI Device...Then it will display all  the host's PCI devices, which when selected, will reserve that specific  device for exclusive use by that VM Guest... (it also has a menu for  host USB devices)

So is it possible to do everything using Virt-Manager even the blacklisting part?
Thanks a lot

---

### Post by T.J. on 2021-08-25
> **demonenero84 said:**
> 
So is it possible to do everything using Virt-Manager even the blacklisting part?
Thanks a lot

Honestly, I have never tried, but I do not believe so.  Every time I have tried to passthrough without binding the card first, virt-manager fails miserably.

It is true you can manually unbind and rebind a driver without rebooting, but in my *opinion* that is overly complicated and rather unreliable.  I find that the best way is to simply bind the hardware to the VFIO driver at boot time, assuming that you have a second video card.  You can always release it later.

I'd be happy to help you through the process of solving this problem.  Any questions, just ask.

---

### Post by demonenero84 on 2021-08-25
Thanks a lot, 
Can you tell me how to get permission to create and edit "nvidia.conf" and "vfio.conf" in /etc/modprobe.d/ directory?
I can edit /etc/initramfs-tools/modules so I guess I just have to add what you told me
> 
assuming that you have a second video card

Yes, I am using an integrated GPU ( Mesa Intel® HD Graphics 630 			 		)
Thanks in advance

---

### Post by T.J. on 2021-08-25
> **demonenero84 said:**
> Thanks a lot, 
Can you tell me how to get permission to create and edit "nvidia.conf" and "vfio.conf" in /etc/modprobe.d/ directory?
I can edit /etc/initramfs-tools/modules so I guess I just have to add what you told me


You need to prefix admin commands with *sudo*.  Ex.

```
sudo nano /etc/modprobe.d/nvidia.conf
```

My apologies if I was not clear; and you're very welcome!  Please be extra careful whenever you use *sudo*.  It gives you the ability to overwrite just about everything.

---

### Post by MAFoElffen on 2021-08-25
(Taking a break while I wait for some answers from someone testing some code...)

Just a note: Good to make a backup of those files (and any others you edit) before you make those changes... That way you have a way to roll back those changes if necessary.

---

### Post by T.J. on 2021-08-26
> **MAFoElffen said:**
> (Taking a break while I wait for some answers from someone testing some code...)

Just a note: Good to make a backup of those files (and any others you edit) before you make those changes... That way you have a way to roll back those changes if necessary.

Thank you so much!  That is great advice that I should have mentioned! &#55358;&#56618;

---

### Post by demonenero84 on 2021-08-26
Thanks;),
So these are my addresses 
> 
[FONT=monospace][COLOR=#000000]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:1c81] (rev a1) (prog-if [/COLOR]
00 [VGA controller]) 
        Subsystem: NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:11c0] 
        Flags: bus master, fast devsel, latency 0, IRQ 129 
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M] 
        Memory at e0000000 (64-bit, prefetchable) [size=256M] 
        Memory at f0000000 (64-bit, prefetchable) [size=32M] 
        I/O ports at e000 [size=128] 
        Expansion ROM at f7000000 [disabled] [size=512K] 
        Capabilities: <access denied> 
        Kernel driver in use: nouveau 
        Kernel modules: nvidiafb, nouveau 

01:00.1 Audio device [0403]: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:0fb9] (rev a1) 
        Subsystem: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:11c0] 
        Flags: bus master, fast devsel, latency 0, IRQ 17 
        Memory at f7080000 (32-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: snd_hda_intel 
        Kernel modules: snd_hda_intel

[/FONT]

How should my vfio.conf look like?
> 
He needs to realize that it will be "Exclusive" to just that one VM  Guest. He will no longer be able to use it for his host, until it is  removed from that VM Guest configurations. The VM Host takes care of the  blacklisting.

So I cannot pass the same GPU to multiple VM 
Let's say I need a Win7 vm and a Win10 vm, Would I need two GPUs even if I want to run only one vm in a given time?
Thanks a lot

---

### Post by T.J. on 2021-08-26
> **demonenero84 said:**
> Thanks;),
So these are my addresses 

How should my vfio.conf look like?


> 
[FONT=monospace][COLOR=#000000]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:1c81] (rev a1) (prog-if [/COLOR]
00 [VGA controller]) 

01:00.1 Audio device [0403]: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:0fb9] (rev a1) [/FONT]


You want the main PCI bus IDs, so:

```

options vfio-pci ids=10de:1c81,10de:0fb9

```

> So I cannot pass the same GPU to multiple VM 
Let's say I need a Win7 vm and a Win10 vm, 

The way that the GPUs are designed, they can only be bound to one operating system at a time. So a single GPU cannot be shared using passthrough.  You can, of course, setup multiple VMs using a GPU, but only one VM can use the GPU at a time.  For another to use it, it has to be released.  There are other means besides passthrough that allow GPUs to be shared through software, but you won't get quite as good performance with them.


> Would I need two GPUs even if I want to run only one vm in a given time?
Thanks a lot

For the sake of convenience, you need one GPU for the host OS (Linux), and one for the guest OS, so you can switch between them easily.  Generally, it is assumed that if you are attempting passthrough that you have at least two GPUs, even if one is just an onboard chip. There are ways to use only one GPU, but it can be significantly more difficult to set up, and you would have to use a remote terminal to access the host.  For example, binding your single GPU to the Windows guest, and then using a terminal program in Windows to access Linux - because Linux would no longer have access to the GPU as long as the Windows guest is active.

---

### Post by demonenero84 on 2021-08-26
Thanks
> 
So a single GPU cannot be shared using passthrough.  You can, of course,  setup multiple VMs using a GPU, but only one VM can use the GPU at a  time.  For another to use it, it has to be released

Is the process of releasing done automatically by "Virtual Machine Manager" when a vm is shut down?
> 
There are other means besides passthrough that allow GPUs to be shared  through software, but you won't get quite as good performance with them

Just for my curiosity what are those means?
Thanks for your help :)

Edit:

So I made a test and I get this error
> 
Error starting domain: unsupported configuration: host doesn't support passthrough of host PCI devices

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 65, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 101, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/object/libvirtobject.py", line 57, in newfn
    ret = fn(self, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/object/domain.py", line 1329, in startup
    self._backend.create()
  File "/usr/lib/python3/dist-packages/libvirt.py", line 1353, in create
    raise libvirtError('virDomainCreate() failed')
libvirt.libvirtError: unsupported configuration: host doesn't support passthrough of host PCI devices


Any suggestions?
Thanks in advance for your help ( and your patience )

---

### Post by T.J. on 2021-08-27
> **demonenero84 said:**
> 

Any suggestions?
Thanks in advance for your help ( and your patience )

No problem, but let's go over things one step at a time.  Did you know if your system supports IOMMU and did you verify the bindings with ```
lspci -vnn 
```

---

### Post by demonenero84 on 2021-08-28
Thanks
> 
let's go over things one step at a time

Yes, of course so in my bios settings I enabled an option called " Intel Virtualization Technology" and another one called "VT-d"
This is what I get with " lspci -vnn "
```

[FONT=monospace][COLOR=#000000]00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:591f] (re[/COLOR]
v 05) 
        Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [1043:8694] 
        Flags: bus master, fast devsel, latency 0 
        Capabilities: <access denied> 
        Kernel driver in use: skl_uncore 

00:01.0 PCI bridge [0604]: Intel Corporation 6th-10th Gen Core Processor PCIe Controller (x16) [8086:1901] (rev 05) (prog-if 00
 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0, IRQ 122 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
        I/O behind bridge: 0000e000-0000efff [size=4K] 
        Memory behind bridge: f6000000-f70fffff [size=17M] 
        Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff [size=288M] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 630 [8086:5912] (rev 04) (prog-if 00 [VGA controller]) 
        DeviceName:  Onboard IGD 
        Subsystem: ASUSTeK Computer Inc. HD Graphics 630 [1043:8694] 
        Flags: bus master, fast devsel, latency 0, IRQ 129 
        Memory at 2ffe000000 (64-bit, non-prefetchable) [size=16M] 
        Memory at 2fe0000000 (64-bit, prefetchable) [size=256M] 
        I/O ports at f000 [size=64] 
        Expansion ROM at 000c0000 [virtual] [disabled] [size=128K] 
        Capabilities: <access denied> 
        Kernel driver in use: i915 
        Kernel modules: i915 

00:14.0 USB controller [0c03]: Intel Corporation 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller [8086:a2af] (prog-if 30
 [XHCI]) 
        Subsystem: ASUSTeK Computer Inc. 200 Series/Z370 Chipset Family USB 3.0 xHCI Controller [1043:8694] 
        Flags: bus master, medium devsel, latency 0, IRQ 126 
        Memory at 2fff010000 (64-bit, non-prefetchable) [size=64K] 
        Capabilities: <access denied> 
        Kernel driver in use: xhci_hcd 
        Kernel modules: xhci_pci 

00:16.0 Communication controller [0780]: Intel Corporation 200 Series PCH CSME HECI #1 [8086:a2ba] 
        Subsystem: ASUSTeK Computer Inc. 200 Series PCH CSME HECI [1043:8694] 
        Flags: bus master, fast devsel, latency 0, IRQ 130 
        Memory at 2fff025000 (64-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: mei_me 
        Kernel modules: mei_me 

00:17.0 SATA controller [0106]: Intel Corporation 200 Series PCH SATA controller [AHCI mode] [8086:a282] (prog-if 01 [AHCI 1.0]
) 
        Subsystem: ASUSTeK Computer Inc. 200 Series PCH SATA controller [AHCI mode] [1043:8694] 
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 127 
        Memory at f7204000 (32-bit, non-prefetchable) [size=8K] 
        Memory at f7207000 (32-bit, non-prefetchable) [size=256] 
        I/O ports at f090 [size=8] 
        I/O ports at f080 [size=4] 
        I/O ports at f060 [size=32] 
        Memory at f7206000 (32-bit, non-prefetchable) [size=2K] 
        Capabilities: <access denied> 
        Kernel driver in use: ahci 
        Kernel modules: ahci 

00:1c.0 PCI bridge [0604]: Intel Corporation 200 Series PCH PCI Express Root Port #5 [8086:a294] (rev f0) (prog-if 00 [Normal d
ecode]) 
        Flags: bus master, fast devsel, latency 0, IRQ 123 
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
        I/O behind bridge: 00002000-00002fff [size=4K] 
        Memory behind bridge: b8000000-b81fffff [size=2M] 
        Prefetchable memory behind bridge: 0000002000000000-00000020001fffff [size=2M] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

00:1c.7 PCI bridge [0604]: Intel Corporation 200 Series PCH PCI Express Root Port #8 [8086:a297] (rev f0) (prog-if 00 [Normal d
ecode]) 
        Flags: bus master, fast devsel, latency 0, IRQ 124 
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0 
        I/O behind bridge: 0000d000-0000dfff [size=4K] 
        Memory behind bridge: f7100000-f71fffff [size=1M] 
        Prefetchable memory behind bridge: [disabled] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

00:1d.0 PCI bridge [0604]: Intel Corporation 200 Series PCH PCI Express Root Port #9 [8086:a298] (rev f0) (prog-if 00 [Normal d
ecode]) 
        Flags: bus master, fast devsel, latency 0, IRQ 125 
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
        I/O behind bridge: 00003000-00003fff [size=4K] 
        Memory behind bridge: b8200000-b83fffff [size=2M] 
        Prefetchable memory behind bridge: 0000002000200000-00000020003fffff [size=2M] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

00:1f.0 ISA bridge [0601]: Intel Corporation 200 Series PCH LPC Controller (B250) [8086:a2c8] 
        Subsystem: ASUSTeK Computer Inc. 200 Series PCH LPC Controller (B250) [1043:8694] 
        Flags: bus master, medium devsel, latency 0 

00:1f.2 Memory controller [0580]: Intel Corporation 200 Series/Z370 Chipset Family Power Management Controller [8086:a2a1] 
        Subsystem: ASUSTeK Computer Inc. 200 Series/Z370 Chipset Family Power Management Controller [1043:8694] 
        Flags: fast devsel 
        Memory at f7200000 (32-bit, non-prefetchable) [disabled] [size=16K] 

00:1f.3 Audio device [0403]: Intel Corporation 200 Series PCH HD Audio [8086:a2f0] 
        Subsystem: ASUSTeK Computer Inc. 200 Series PCH HD Audio [1043:86c7] 
        Flags: bus master, fast devsel, latency 32, IRQ 131 
        Memory at 2fff020000 (64-bit, non-prefetchable) [size=16K] 
        Memory at 2fff000000 (64-bit, non-prefetchable) [size=64K] 
        Capabilities: <access denied> 
        Kernel driver in use: snd_hda_intel 
        Kernel modules: snd_hda_intel 

00:1f.4 SMBus [0c05]: Intel Corporation 200 Series/Z370 Chipset Family SMBus Controller [8086:a2a3] 
        Subsystem: ASUSTeK Computer Inc. 200 Series/Z370 Chipset Family SMBus Controller [1043:8694] 
        Flags: medium devsel, IRQ 16 
        Memory at 2fff024000 (64-bit, non-prefetchable) [size=256] 
        I/O ports at f040 [size=32] 
        Kernel driver in use: i801_smbus 
        Kernel modules: i2c_i801 

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:1c81] (rev a1) (prog-if 00 [VGA con
troller]) 
        Subsystem: NVIDIA Corporation GP107 [GeForce GTX 1050] [10de:11c0] 
        Flags: fast devsel, IRQ 11 
        Memory at f6000000 (32-bit, non-prefetchable) [disabled] [size=16M] 
        Memory at e0000000 (64-bit, prefetchable) [disabled] [size=256M] 
        Memory at f0000000 (64-bit, prefetchable) [disabled] [size=32M] 
        I/O ports at e000 [disabled] [size=128] 
        Expansion ROM at f7000000 [disabled] [size=512K] 
        Capabilities: <access denied> 
        Kernel modules: nvidiafb, nouveau 

01:00.1 Audio device [0403]: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:0fb9] (rev a1) 
        Subsystem: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:11c0] 
        Flags: bus master, fast devsel, latency 0, IRQ 17 
        Memory at f7080000 (32-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: snd_hda_intel 
        Kernel modules: snd_hda_intel 

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [
10ec:8168] (rev 15) 
        Subsystem: ASUSTeK Computer Inc. PRIME B450M-A Motherboard [1043:8677] 
        Flags: bus master, fast devsel, latency 0, IRQ 19 
        I/O ports at d000 [size=256] 
        Memory at f7104000 (64-bit, non-prefetchable) [size=4K] 
        Memory at f7100000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: r8169 
        Kernel modules: r8169
[/FONT]
```
Thanks:P

---

### Post by T.J. on 2021-08-28
So from the readout I can see that your nvidia card is not bound by the vfio driver.  When you edited your files, afterward did you run

sudo update-grub

sudo update-initramfs -k all -u

---

### Post by demonenero84 on 2021-08-29
> 
sudo update-grub

sudo update-initramfs -k all -u                                                                                                                                

Done, I still get the same readout if I run " lspci -vnn "
Thanks

---

### Post by T.J. on 2021-09-04
Sorry, been away a bit.   Do you still need assistance?

---

### Post by demonenero84 on 2021-09-05
No problem.
I decided to take a break, right now I am using my dedicated GPU so no more tests for a while, however virtualization with GPU passthrough is really an interesting option when I will have more free time I try again.
Thanks for your help :cool:

---

### Post by T.J. on 2021-09-05
> **demonenero84 said:**
> No problem.
I decided to take a break, right now I am using my dedicated GPU so no more tests for a while, however virtualization with GPU passthrough is really an interesting option when I will have more free time I try again.
Thanks for your help :cool:

When that comes, I hope you might consider contacting me again.  If the thread is closed, please mark it as so.

---

### Post by demonenero84 on 2021-09-06
> 
I hope you might consider contacting me again

Sure thanks T.J. :)
> 
If the thread is closed, please mark it as so

If that is not a problem I would like to keep this thread open, since it contains some useful information about my hardware and the software that I use. 
When ready to make another attempt I will simply add all useful information here

---

### Post by demonenero84 on 2022-08-07
So now that I have a bit of time I tried again :)
So basically it seem that my GPU is bound to the vfio-pci, if I run lspci -k I get this output
> 
[FONT=monospace][COLOR=#000000]01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050] (rev a1) [/COLOR]
        Subsystem: NVIDIA Corporation GP107 [GeForce GTX 1050] 
        Kernel driver in use: vfio-pci 
        Kernel modules: nvidiafb, nouveau 
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1) 
        Subsystem: NVIDIA Corporation GP107GL High Definition Audio Controller 
        Kernel driver in use: vfio-pci 
        Kernel modules: snd_hda_intel
[/FONT]
With virt-manager I can add those two pci devices, but my vm does not recognize those devices, my GPU does not output anything and win10 device manager does not list them
Any suggestions?
thanks a lot in advance

---

### Post by demonenero84 on 2022-08-12
So I made a rather childish mistake ](*,)I set my firmware settings to "BIOS" instead of "UEFI".
Now I get this error when adding my GPU
> 
 Error starting domain: Requested operation is not valid: domain is already running

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 72, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 108, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/object/libvirtobject.py", line 57, in newfn
    ret = fn(self, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/object/domain.py", line 1384, in startup
    self._backend.create()
  File "/usr/lib/python3/dist-packages/libvirt.py", line 1353, in create
    raise libvirtError('virDomainCreate() failed')
libvirt.libvirtError: Requested operation is not valid: domain is already running
And when my vm is running I get this output from my GPU
[IMG]https://i.ibb.co/GFNR2zX/Whats-App-Image-2022-08-12-at-14-48-59.jpg[/IMG]
Any suggestions? 
thank a lot in advance

---

### Post by TheFu on 2022-08-12
Kubuntu 21.04?
Support for that release ended 8 months ago.  Move to 22.04 or back to 20.04, if you like.

Trying to fix issues on unsupported releases isn't worth anyone's time.

I'm just lurking ... to learn.

---

### Post by demonenero84 on 2022-08-12
thanks for the reply
I am using Kubuntu 22.04 I forgot to update my pc specs O:)

Operating System: Kubuntu 22.04
Processors: 4 × Intel® Core&#8482; i5-7400 CPU @ 3.00GHz
Memory: 7,7 GiB of RAM
Graphics Processor: Mesa Intel® HD Graphics 630
Graphics Processor: Nvidia [FONT=monospace][FONT=monospace][COLOR=#000000]GeForce GTX 1050[/COLOR][/FONT][/FONT]

Done :)

---

