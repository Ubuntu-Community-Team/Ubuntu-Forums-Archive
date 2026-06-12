---
title: "Switchable Graphic Passthrough with KVM"
date: 2016-09-09
forum: Virtualisation
---

### Post by ndoob on 2016-09-09
Greetings!

Howdy to you all from this new member of the forum, and a new convert to Linux! :).. 

After researching for a while, I am very much interested in KVM, especially since it allows to pass through hardware to client OSs (also one of the reason why I convert..)  Anyways, as the title suggests, I am trying to pass a GPU to Windows 10 client but unfortunately with no success.

I have a Lenovo G510 laptop with the following configuration:
[LIST]
[*]CPU Intel i7 4800MQ (upgraded from i7 4700MQ to support VT-d)
[*]Switchable graphics with:
[LIST]
[*]Integrated Graphics - Intel HD Graphics 4600
[*]Dedicated Graphics - AMD Radeon HD 8750M
[/LIST]

[*]Xubuntu 16.04
[/LIST]

My /etc/modules looks like:
```

pci_stubvfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
kvm
kvm_intel
...

```

My GRUB setting looks like:
```
quiet splash radeon.modeset=1 i915.modeset=1 radeon.runpm=0 intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1
```

My /etc/modprobe.d/vfio.conf looks like:
```
options vfio-pci ids=1002:6600
```

I added ```
blacklist radeon
``` to my /etc/modprobe.d/blacklist.conf.

Not to forget the following steps:
```
echo '0000:01:00.0' | sudo tee /sys/bus/pci/devices/0000:01:00.0/driver/unbind    sudo modprobe vfio
    sudo modprobe vfio_pci
    echo 1002 6600 | sudo tee /sys/bus/pci/drivers/vfio-pci/new_id

```

And, after running sudo update-initramfs -u, dmesg | grep vfio looks like 
```

...
[    5.344080] vfio_pci: add [1002:6600[ffff:ffff]] class 0x000000/00000000
...

```

And sudo lspci -vv shows
```

...
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M]
...
Kernel driver in use: vfio-pci
Kernel modules: radeon

...

```

The following is my QEMU script to my Windows 10 client #1:
```
sudo qemu-system-x86_64 -enable-kvm -M q35 -m 8192 -cpu host,kvm=off -smp 4,sockets=1,cores=4,threads=1 -vga std -soundhw pcspk -usb -usbdevice tablet -device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=off,rombar=0 -drive file=/home/lolla/boxes/iobox.img,id=disk,format=raw,if=virtio -drive file=/home/lolla/Download/Win10_1511_1_EnglishInternational_x64.iso,id=isocd,format=raw,if=none -device ide-cd,bus=ide.1,drive=isocd -cdrom /home/lolla/Download/virtio-win-0.1.102.iso -boot menu=on;
```

The following is my XML configuration for my WIndows 10 client #2:
```

<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit iobox
or other application using the libvirt API.
-->


<domain type='kvm'>
  <name>iobox</name>
  <uuid>2251c26e-0a29-4652-91e9-1657c04e3ec3</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-2.5'>hvm</type>
    <bootmenu enable='yes'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Haswell-noTSX</model>
    <topology sockets='4' cores='1' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw' io='native'/>
      <target dev='sda' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw' io='native'/>
      <target dev='sdb' bus='sata'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' io='native'/>
      <source file='/var/lib/libvirt/images/iobox.img'/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x04' function='0x0'/>
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
      <address type='pci' domain='0x0000' bus='0x01' slot='0x01' function='0x0'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x03' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='51:53:00:1c:14:0b'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x01' function='0x0'/>
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
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <image compression='off'/>
    </graphics>
    <sound model='ich9'>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x02' function='0x0'/>
    </sound>
    <video>
      <model type='vga' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <rom bar='off'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x05' function='0x0'/>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'> 
      <address type='pci' domain='0x0000' bus='0x02' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

Both of these VMs recognize the AMD Radeon, as Graphic Device, but only with Error Code 43.

I tried these and those, I even use a customized kernel, just to enable DMA remapping option, which in default kernel was disabled. Am I missing something? Do my hardware support passthrough? Is there someway I can do to check (both in host or in clients) if everything is OK? Does it have any connection to vgaswitcheroo because of the switchable graphics? If so, using my modified kernel, I get the following error:

```
sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access '/sys/kernel/debug/vgaswitcheroo/switch': No such file or directory

```

I appreciate all help and guidance. Any further online resources will also be a great help. Many thanks!

Cheers!

---

### Post by KillerKelvUK on 2016-09-10
Hey ndoob, welcome to the forum...glad to see you've made the leap to linux :-)

Please can you elaborate a little more on your expectations around "Switchable..."?

Regards the script you've noted you use...

 ```
 
echo '0000:01:00.0' | sudo tee /sys/bus/pci/devices/0000:01:00.0/driver/unbind    sudo modprobe vfio
    sudo modprobe vfio_pci
    echo 1002 6600 | sudo tee /sys/bus/pci/drivers/vfio-pci/new_id
```

I'm not seeing the reason for this as you are capturing your devices on the vfio-pci driver via the changes to your initramfs.  If you remove this step in your process and then lspci -vv the passthrough devices they should show the kernel driver in use is vfio-pci...if they don't we might need to circle back up to your earlier steps.

Regards your guest config...client 1 using the qemu commandline includes "-vga std" and client 2 using libvirt xml includes ```
 <video>      <model type='vga' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/>
    </video>
```

These configs put a virtual graphics device in the guest, this can cause problems with passthrough.  I'd recommend re-configuring both client's to ensure that the only graphics device present in the guest in the pass-through PCI card.

---

### Post by ndoob on 2016-09-11
Hello [COLOR=#000000]KillerKelvUK!

Thanks a bunch! Glad to be here! Anyways, regarding the term "Switchable", at first, my understanding was that there would be 2 graphic cards in my laptop, the same way we would have in PC: one integrated in motherboard (in this case, my Intel 4600), one attached in PCI (in this case, my AMD radeon), or so. But after some online reading, I have the impression, that the secondary GPU, or the discrete GPU, will only be active on a certain condition, e.g., when the graphic operations need more performance, etc. Therefore I'm not sure anymore if the discrete GPU could act like a dedicated GPU. In a sense that I could perform a passthrough to a VM. But please correct my understanding here, since I am pretty sure there's some mistakes in it. :)..

And about the following steps (and all the steps I provided in this post):
[/COLOR]```
[COLOR=#000000][FONT=&amp]echo '0000:01:00.0' | sudo tee /sys/bus/pci/devices/0000:01:00.0/driver/unbind 
sudo modprobe vfio
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo modprobe vfio_pci
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]echo 1002 6600 | sudo tee /sys/bus/pci/drivers/vfio-pci/new_id[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
```[COLOR=#000000]
are parts of the online resources that I've found. For example [this]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/") and [this]("https://wiki.debian.org/VGAPassthrough").

I tried to remove the 
[/COLOR]```
[COLOR=#000000]-vga std[/COLOR]
```[COLOR=#000000]
and the
[/COLOR]```
[COLOR=#000000][FONT=&amp]<video> 
     <model type='vga' vram='16384' heads='1'/>
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]     <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0'/> [/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]</video>
[/FONT][/COLOR]
```[COLOR=#000000]
but then it shows nothing, although I am quite sure that the client VMs run. This is also part of the question: since I am using a laptop, if this were to succeed, what behavior would I expect? Would the client VM overtake my laptop's display?

The second question would be, how should I reconfigure my settings? Any suggestions? 

Btw, I tried the following: 
[/COLOR]```
sudo qemu-system-x86_64 -enable-kvm -M q35 -m 8192 -cpu host,kvm=off -smp 4,sockets=1,cores=4,threads=1 -vga none -soundhw pcspk -usb -usbdevice tablet -device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=off,rombar=0 -drive file=/home/noot/Runnables/boxes/iobox.img,id=disk,format=raw,if=virtio -drive file=/home/noot/Repo/raw/Win10_1511_1_EnglishInternational_x64.iso,id=isocd,format=raw,if=none -device ide-cd,bus=ide.1,drive=isocd -cdrom /home/noot/Repo/raw/virtio-win-0.1.102.iso -boot menu=on;

```[COLOR=#000000]
Replacing the -vga std with -vga none, and it shows only a blank QEMU window, but the console shows the following:
[/COLOR]```
e1000: Writing to register at offset: 0x00002410. It is not fully implemented.e1000: Writing to register at offset: 0x00002418. It is not fully implemented.
e1000: Writing to register at offset: 0x00002420. It is not fully implemented.
e1000: Writing to register at offset: 0x00002428. It is not fully implemented.
e1000: Writing to register at offset: 0x00002430. It is not fully implemented.
e1000: Writing to register at offset: 0x00003410. It is not fully implemented.
e1000: Writing to register at offset: 0x00003418. It is not fully implemented.
e1000: Writing to register at offset: 0x00010000. It is not fully implemented.
e1000: Writing to register at offset: 0x00003420. It is not fully implemented.
e1000: Writing to register at offset: 0x00003428. It is not fully implemented.
e1000: Writing to register at offset: 0x00003430. It is not fully implemented.
e1000: TDH wraparound @67b2, TDT b220, TDLEN 22000

```[COLOR=#000000]
And dmesg shows the following:
[/COLOR]```
[ 1626.790816] vfio-pci 0000:01:00.0: disabling bus mastering[ 1626.790823] vfio-pci 0000:01:00.0: enabling device (0002 -> 0003)
[ 1626.790866] ACPI Error: [AR02] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[ 1626.790870] ACPI Error: Method parse/execution failed [\_SB.PCI0.PEG0._PRT] (Node ffff88045dce4910), AE_NOT_FOUND (20150930/psparse-542)
[ 1626.822816] vfio-pci 0000:01:00.0: restoring config space at offset 0x4 (was 0x100400, writing 0x100003)
[ 1626.822907] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x270
[ 1627.874592] vfio-pci 0000:01:00.0: restoring config space at offset 0x3c (was 0x1ff, writing 0x107)
[ 1627.874598] vfio-pci 0000:01:00.0: restoring config space at offset 0x30 (was 0x0, writing 0xfffe0000)
[ 1627.874601] vfio-pci 0000:01:00.0: restoring config space at offset 0x2c (was 0x0, writing 0x380117aa)
[ 1627.874606] vfio-pci 0000:01:00.0: restoring config space at offset 0x20 (was 0x1, writing 0x4001)
[ 1627.874610] vfio-pci 0000:01:00.0: restoring config space at offset 0x18 (was 0x4, writing 0xb8000004)
[ 1627.874615] vfio-pci 0000:01:00.0: restoring config space at offset 0x10 (was 0xc, writing 0xb000000c)
[ 1627.874618] vfio-pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0x10)
[ 1631.130199] kvm: zapping shadow pages for mmio generation wraparound
[ 1631.131776] kvm: zapping shadow pages for mmio generation wraparound
[ 1634.032535] kvm [5008]: vcpu0 unhandled rdmsr: 0x641
[ 1681.171518] ACPI Error: [AR02] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[ 1681.171524] ACPI Error: Method parse/execution failed [\_SB.PCI0.PEG0._PRT] (Node ffff88045dce4910), AE_NOT_FOUND (20150930/psparse-542)

```

[COLOR=#000000]Does the error message mean something? I also attach the whole dmesg just in case.[/COLOR][ATTACH]271080[/ATTACH][COLOR=#000000]
[/COLOR]

---

### Post by KillerKelvUK on 2016-09-12
> **ndoob said:**
> [COLOR=#000000]Thanks a bunch! Glad to be here! Anyways, regarding the term "Switchable", at first, my understanding was that there would be 2 graphic cards in my laptop, the same way we would have in PC: one integrated in motherboard (in this case, my Intel 4600), one attached in PCI (in this case, my AMD radeon), or so. But after some online reading, I have the impression, that the secondary GPU, or the discrete GPU, will only be active on a certain condition, e.g., when the graphic operations need more performance, etc. Therefore I'm not sure anymore if the discrete GPU could act like a dedicated GPU. In a sense that I could perform a passthrough to a VM. But please correct my understanding here, since I am pretty sure there's some mistakes in it. :)..
[/COLOR]

Hey, so I'm still not sure what you mean by "Switchable" but your logic above I'd agree with i.e. integrated gfx (iGD) vs discrete gfx, the challenge for you, as you have called out is how this would apply to your laptop as its not guaranteed to be the same vs a workstation or server etc.  If you haven't already I'd recommend you research your specific laptop for users who have attempted gfx passthrough to a virtual machine to garner some expectations for how it should and should not function.  

> but then it shows nothing, although I am quite sure that the client VMs run. This is also part of the question: since I am using a laptop, if this were to succeed, what behavior would I expect? Would the client VM overtake my laptop's display?

So your expectations here should be that the display output port (HDMI, DisplayPort, VGA) associated with the gfx card you've passed through to the guest should start pumping out the display you'd normally expect with a booting computer e.g. bios/uefi, os loading etc.  In your example it would not be the built-in laptop display as this is in use with the host...are you able (via the UEFI for example) to associate the AMD graphics to a specific display output i.e. the HDMI port?  Have you connected a monitor up this way already or were you expecting/wanting it to use the built-in laptop display?

Regards the rest of your reply, I'd recommend the following...

[LIST]
[*]For now stick with one way of creating and configuring a guest.  If you have limited experience here then I'd recommend against using qemu on the command line directly and urge you to focus on using libvirt xml and if possible virt-manager (GUI needed), this is just to limit the potential of user error (no offence intended).  I'm not advocating you stick with virt-manager for life but it will help in getting you started.
[*]Remove any unnecessary configurations e.g. network adaptors, VNC/Spice displays, sound cards, usb redirection channels.  These can all be added back in later but for now I'd recommend you limit what can complain so as to help draw out any issues preventing gfx passthrough.
[*]If your laptop and gfx passthrough are UEFI capable and if you are already booting the xbuntu host as UEFI then you need to configure your guest to use the same, this comes in the form of OVMF and is a standard package now in ubuntu 16.04 so just install this.  NOTE:  Using virt-manager there are two configuration items that can only be set  when you first define/create the guest, these are the machine type (i440fx vs Q35) and the bios loader (seabios vs OVMF).  Hence I'd recommend you create a new guest to select these options unless you know what you're doing in hacking around the xml.
[*]Lastly, I'd recommend a more recent guide by the VFIO maintainer ([http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html))
[/LIST]

---

### Post by ndoob on 2016-09-12
Hi!

I really appreciate all your suggestions. I think I will start by plugging in a secondary monitor and trying to assign the gfx card to either HDMI or display port (All this time I just use my laptop's display. Haha.). I will keep posting any results (good or bad) or as soon as I stumble on something interesting.. :D.. although that will take a while.. :D..

> [COLOR=#000000]If your laptop and gfx passthrough are UEFI capable and if you are already booting the xbuntu host as UEFI then you need to configure your guest to use the same, this comes in the form of OVMF and is a standard package now in ubuntu 16.04 so just install this.[/COLOR]
Anyways, so far I have no UEFI installed. Are you saying that having UEFI will increase the chance of success?

---

### Post by KillerKelvUK on 2016-09-14
> **ndoob said:**
> Anyways, so far I have no UEFI installed. Are you saying that having UEFI will increase the chance of success?

So passthrough is possible without using OVMF (the UEFI implementation for virtual machines) however depending on your host hardware you may encounter vga arbitration issues that result in poor/unusual host gfx.  Thus using OVMF instead of legacy seabios in the guest worked around this problem meaning you don't have to patch your host kernel (i915 arbitration).

I'm not sure however if you need to have a full UEFI chain i.e. the host should boot using UEFI and thus when the guest boots and uses OVMF it arbitrates the vga space of the passthrough card away from the host...you should probably have a read through about this, I think its covered in the guide I linked.

---

### Post by heiko_s on 2016-09-26
For what it's worth, you may try the how-to I posted in the Linux Mint forum: [HOW-TO make dual-boot obsolete using kvm VGA passthrough]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692"). The how-to should work likewise in Ubuntu 16.04 (users have reported success).

In your case, check if the graphics card supports UEFI (see how-to). You can boot Ubuntu whichever way you like - that is legacy or UEFI - but it will be easier to install and run Windows 10 (or Windows 8) using UEFI with OVMF (this only refers to the Windows VM, not to Ubuntu).

You need to make sure that VT-d (IOMMU) is turned on in your BIOS settings. Most manufacturers disable it by default. You'll find ways to check this in my how-to.

Good luck!

---

### Post by heiko_s on 2016-09-26
I checked the dmesg file you attached to one of the posts and it shows that IOMMU is working, which is good news. As to the VM configuration: stick with one method and don't confuse qemu command line with libvirt / virsh / virt-manager. I use the qemu command in a script, which is easy to read and to modify.

Since you are using the IDG (Intel graphics) for your host, you should use OVMF (UEFI boot of the Windows VM). OVMF does not require the VGA arbitration which is broken for Intel graphics (see [01x09b-VFIOandYou-small.pdf]("http://www.linux-kvm.org/images/b/b3/01x09b-VFIOandYou-small.pdf")). My how-to describes how to test your graphics card for UEFI support - make sure you check it!

The output of the rom-parser utility should look like:
```
$ ./rom-parser image.rom
Valid ROM signature found @0h, PCIR offset 1a0h
	PCIR: type 0 (x86 PC-AT), vendor: 10de, device: 13c2, class: 030000
	PCIR: revision 0, vendor revision: 1
Valid ROM signature found @f400h, PCIR offset 1ch
	PCIR: type 3 (EFI), vendor: 10de, device: 13c2, class: 030000
	PCIR: revision 3, vendor revision: 0
		EFI: Signature Valid, Subsystem: Boot, Machine: X64
	Last image
```


If your graphics card does not support UEFI, you have two choices:

1. Use legacy boot and patch the kernel with the i915 arbiter patch - have a look at this: [http://vfio.blogspot.co.il/2015/05/vfio-gpu-how-to-series-part-5-vga-mode.html]("http://vfio.blogspot.co.il/2015/05/vfio-gpu-how-to-series-part-5-vga-mode.html").
2. Get a UEFI BIOS for your graphics card (I haven't found a BIOS for your card, but haven't given it much time).

Hope it helps.

---

### Post by ndoob on 2016-10-09
Greetings!

First of all, thanks a bunch @KillerKevUK and @heiko_s for all tips. The reason it took quite some time to write again in this topic is that I just freshly install my xubuntu. XD.. I played around quite some time with the kernel config (I tried to compile directly from the source just to play around..) just to see if it will make any difference, and in some point, I forgot what I did, and my lappy wont boot. So now I have to start again from the beginning. But that was fun :)

@heiko_s, I think I will try your suggestion  at first. This will take some time. 

I just wanna keep in touch, make sure that this topic will keep alive. Will write back again soon.

Cheers!

---

