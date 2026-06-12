---
title: "GPU passthrough with qemu"
date: 2016-04-13
forum: Virtualisation
---

### Post by DanHorniblow on 2016-04-13
Hi

Im trying to setup GPU passthrough from my 16.04 box to a Windows VM, which "technically" is working. I have used a combination of guides to do this, primarily [this one]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/").

Currently the Windows VM is outputting video via the passed through GPU (ATI R9 290XO) my problem is within Windows, when I try to install the AMD drivers for the card, the VM will crash and reboot. Im assuming Windows blue screens but I can't actually see because at the time of the crash the screen goes black (im assuming this is to do with Windows removing its default drivers of the card at the time of the crash).

I know there isn't any issue with the drivers as I used to use them without issue when I was running Windows natively. I have also tried reinstalling different versions of Windows within the VM just incase Windows is being "spazzy". This makes me think that the problem is actually the method I am using to pass my GPU through. 

Bellow is a copy of my script im using to start the VM:
 
```
#!/bin/bash

configfile=/etc/gaming-vm-pci.cfg

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

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 6114 -cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/seabios/bios.bin \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-usb -usbdevice host:1b1c:1b09 \
-usb -usbdevice host:04d9:a067 \
-usb -usbdevice host:1e7d:3750 \
-drive file=/var/lib/libvirt/images/Gaming-os.img,id=disk-os,format=raw,if=none,cache=none -device ide-hd,bus=ide.0,drive=disk-os \
-drive file=/data/virt/Gaming-data.img,id=disk-data,format=raw,if=none,cache=none -device ide-hd,bus=ide.1,drive=disk-data \
-device e1000,netdev=tunnel -netdev tap,id=tunnel,ifname=vnet0 \
-vga none

exit 0

```

I have read about NVIDIA actually using VM detection within there drivers and causing code 43 errors within Windows is the GPU is present in a VM, however I haven't been able to find much info about this problem on AMD cards.

I have also tried modifying my start script to this:

```
#!/bin/bash

configfile=/etc/gaming-vm-pci.cfg

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

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 6114 -cpu host,kvm=off \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/seabios/bios.bin \
-device vfio-pci,host=01:00.0,x-vga=on \
-device vfio-pci,host=01:00.1 \
-usb -usbdevice host:1b1c:1b09 \
-usb -usbdevice host:04d9:a067 \
-usb -usbdevice host:1e7d:3750 \
-drive file=/var/lib/libvirt/images/Gaming-os.img,id=disk-os,format=raw,if=none,cache=none -device ide-hd,bus=ide.0,drive=disk-os \
-drive file=/data/virt/Gaming-data.img,id=disk-data,format=raw,if=none,cache=none -device ide-hd,bus=ide.1,drive=disk-data \
-device e1000,netdev=tunnel -netdev tap,id=tunnel,ifname=vnet0 \
-vga none

exit 0

```

This time when I attempt to install the AMD drivers Windows doesn't crash but I do however loose all output from the card / Windows and am just presented with a black screen.

Can anyone see something I'm not?

Also what does the "kvm=off" option I added actually do?


Thanks 
Dan

---

### Post by MAFoElffen on 2016-04-13
Info on the "kvm=off" option:
> 
The off state is meant to hide kvm from standard detection routines.  This allows us to disable paravirtualization detection in the guest and can be used to bypass hypervisor checks in certain guest drivers.

In relation to hardware passthrough:
```

-cpu host, kvm=off

```
In the commandline option "-cpu host" is telling the hypervisor to emulate the host's exact CPU. The option "kvm=off" is mostly used with NVidia cards to stop the VM guest from automatically detecting a hypervisor and therefore exiting with an error. That is a common error if trying to do hardware passthrough with an NVidia card.

Down in your script, the device lines say to  turn on this device on the host, found at this PCI bus address, and ttake ownership of it. This assumes that you have this device blacklisted from the host, so it is not used nor owned as a host asset.

From what I see in your script, do an lspci or lshw, filtered on video, and ensure that your card's PCI address matches what is in your script, then ensure that your script can take owner ship, to powerup that card solely on that VM. 

I don't do video hardware passthrough regularly. I did it to see what it was about and how it worked, but didn't like the lag, and moved on. So if someone see's something I don't, please chime in.

---

### Post by DanHorniblow on 2016-04-13
Hi MAFoElffen

I have blacklisted my GPU card by doing the following:

Output of ```
lspci -nn | grep -i amd
```
```

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon R9 290X] [1002:67b0]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio [1002:aac8]

```

I then took the IDs ```
[1002:67b0]
``` and ```
[1002:aac8]
``` added them to my /etc/initramfs-tools/modules file to make it look like this:

```

# List of modules that you want to include in your initramfs.
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

# Gaming VM Config
# Blacklisting the R9 290X & USB card
pci_stub ids=1002:67b0,1002:aac8
radeon

```

As you can see I also blacklisted the radeon driver from loading on the host.

I then took the PCI slot IDs ```
01:00.0
``` and ```
01:00.1
```

Added them to /etc/gaming-vm-pci.cfg (which is called by my launch script) like so..
```

0000:01:00.0
0000:01:00.1

```


When I initially boot my host lspci -k looks like this:
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon R9 290X]
	Subsystem: XFX Pine Group Inc. Double Dissipation R9 290X
	Kernel driver in use: pci-stub
	Kernel modules: radeon
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio
	Subsystem: XFX Pine Group Inc. Hawaii HDMI Audio
	Kernel driver in use: pci-stub
	Kernel modules: snd_hda_intel

```

However once I have booted the VM it then looks like this:
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon R9 290X]
	Subsystem: XFX Pine Group Inc. Double Dissipation R9 290X
	Kernel driver in use: vfio-pci
	Kernel modules: radeon
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio
	Subsystem: XFX Pine Group Inc. Hawaii HDMI Audio
	Kernel driver in use: vfio-pci
	Kernel modules: snd_hda_intel

```

The device is being passed through to the VM, and Windows is able to output video from it, the problem occurs when I install the AMD video drivers for the card. Am I doing anything wrong with my passthrough?


Thanks Dan

---

### Post by DanHorniblow on 2016-04-13
Also

Does anybody know the difference between the two different methods I tried to pass the PCI card through, more specifically the effects they have on the guest?
```

-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \

```

vs

```

-device vfio-pci,host=01:00.0,x-vga=on \
-device vfio-pci,host=01:00.1 \

```

Thanks again

---

### Post by KillerKelvUK on 2016-04-14
So the differences are the first is creating a specific root PCI controller and mapping the passthrough specifically, the other you're letting qemu/kvm handle this automatically.  Also unless you're attempting Primary VGA assignment the x-vga=on isn't required.

Have you checked dmesg for any outputs like unsafe interrupts, a guest reset can be caused my the KVM module mis-handling interrumpt requests which can you work around, see here [https://wiki.debian.org/VGAPassthrough#Unsafe_interrupts_remapping](https://wiki.debian.org/VGAPassthrough#Unsafe_interrupts_remapping)

You could also try changing the guest cpu type to core2duo, from a Win10/qemu compatibility perspective this represents a safe harbour position and is generally required when Win10 is applying a major update needing reboots etc.

Also, the use of the pci-stub driver is now dated, since kernel 4.1 I think you can directly map a device to the vfio-pci driver on boot, this removes the need for the device to have a different module loaded against it as the guest starts i.e. host os boot and your devices are loaded using the pci-stub driver, you start your guest and the devices need to switch pci-stub out for the vfio-pci driver...this process can create instabilities so mapping them directly to vfio-pci at boot is preferential.

EDIT:  Also from your outputs earlier in the thread your pci-stub isn't grabbing the card early enough, you see this when you do 'sudo lspci -s 01: -v' and the kernel modules are radeon and snd_hda_intel...this should be pci-stub only...I'd suggest as a test you blacklist the snd_hda_intel module also and move your stubbing into the /etc/default/grub location so pci-stub module is loaded as early as possible in the process.  If after a host reboot your card's 2 devices (video and audio) are both loaded using the pci-stub module your good...you should see this change only to vfio-pci once you start the Win10 guest...anything else your config is bad.  If your host needs the snd_hda_intel module also then you can recover this by 'sudo modprobe snd_hda_intel', as pci-stub should have already grabbed your passthrough card this shouldn't change.

If you are going to switch to vfio-pci instead of stub then even better but the above logic still applies, your passthrough card needs to be grabbed by the vfio-pci driver at host boot to secure it for your guest assignment.

---

### Post by DanHorniblow on 2016-04-14
Hi KillerKelvUK

I have just done as you suggested, mapping to the vfio-pci driver on boot and its worked, see output of sudo lspci -s 01: -v :
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon R9 290X] (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Double Dissipation R9 290X
	Flags: fast devsel, IRQ 16
	Memory at e0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [disabled] [size=8M]
	I/O ports at e000 [disabled] [size=256]
	Memory at f7d00000 (32-bit, non-prefetchable) [disabled] [size=256K]
	Expansion ROM at f7d40000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Capabilities: [270] #19
	Capabilities: [2b0] Address Translation Service (ATS)
	Capabilities: [2c0] #13
	Capabilities: [2d0] #1b
	Kernel driver in use: vfio-pci
	Kernel modules: radeon

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio
	Subsystem: XFX Pine Group Inc. Hawaii HDMI Audio
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7d60000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: vfio-pci
	Kernel modules: snd_hda_intel


```

A key point that you pointed out, the snd_hda_intel and radeon modules are still being loaded as you can see. I am currently doing my blacklisting in "/etc/modprobe.d/blacklist.conf" with the following lines:
```

blacklist radeon
blacklist snd_hda_intel

```

For some reason this seems to be getting ignored.

If I was to map my GPU to vfio-pci earlier in the boot process with grub like you suggested, would I even need to blacklist those two modules?

Also does anybody know the syntax I would need in my "/etc/deafult/grub" file to do this? Im assuming I would put it in here:
```

GRUB_CMDLINE_LINUX_DEFAULT=

```


Before anyone points out I have been running sudo update-initramfs -u and sudo update-grub after each relevant config change.

Thanks Dan

---

### Post by DanHorniblow on 2016-04-14
Incase anyone can see anything wrong with my current settings in /etc/default/grub they are:
```

GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"

```

---

### Post by KillerKelvUK on 2016-04-14
Regards the blacklisting and module loading they way I set this up was as follows...

Blacklist the radeon driver as you are doing but leave the snd_hda_intel out i.e. let that load normally
Create /etc/modprobe.d/local.conf and added the following obviously customising for your setup...

```

# File location is /etc/modprobe.d/


#e159:0001: OpenVox FXO/FXS Card
#1ade:3038: DVBSky Card
#10de:11c8: nVIDIA GTX 650 (video) card
#10de:0e0b: nVIDIA GTX 650 (audio) card
#10de:13c2: nVIDIA GTX 970 (video) card
#10de:0fbb: nVIDIA GTX 970 (audio) card


options kvm_intel nested=1
options kvm ignore_msrs=1
options vfio_iommu_type1 allow_unsafe_interrupts=1
options vfio-pci ids=10de:11c8,10de:0e0b,1ade:3038,e159:0001,10de:13c2,10de:0fbb

```

Then 'update-initramfs -u' next as you have been doing...

Finally slim your grub line down to remove the vfio_iommu_type1.allow_unsafe_interrupts=1.

The above lets vfio-pci grab my passthrough cards first and host audio still works.

EDIT:

For guides check out this blog...dude rocks the passthrough world as in he dev's the kvm code for redhat i believe...[http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html)

---

### Post by DanHorniblow on 2016-04-14
Sadly that hasn't worked, Im still unable to install the drivers for my GPU within windows either via the AMD catalyst software or the device manager.

Im beginning to think that AMD do some sort of VM detection within their drivers... Although I'm not sure.

After some more google sessions ive found people with similar issues as myself. 

[https://www.redhat.com/archives/vfio-users/2015-October/msg00120.html]("https://www.redhat.com/archives/vfio-users/2015-October/msg00120.html")
[URL="https://lists.fedoraproject.org/pipermail/virt/2013-December/003911.html"]
https://lists.fedoraproject.org/pipermail/virt/2013-December/003911.html[/URL]
[URL="https://bbs.archlinux.org/viewtopic.php?id=162768&p=33"]
https://bbs.archlinux.org/viewtopic.php?id=162768&p=33[/URL]

---

### Post by DanHorniblow on 2016-04-14
IT WORKS!!

So after revisiting one of the links I posted above I noticed this:
> AMD platform worked basically out of the box, because nbhs has very similar setup (chipset is the same).  Intel, however, was a bit tougher to get working because of Catalyst 13.9 atikmpag.sys' code 116 BSOD which was finally solved thanks to recent posts from aw and gentoo-nut by simply ommiting the HDMI Audio completely (or adding it to pcie.0 bus works as well).

Firstly I tried unbinding the HDMI audi device from vfio-pci by removing 1002:aac8 from my /etc/modprobe.d/local.conf file I created earlier in the post, this caused qemu to fail to passthrough 1002:67b0 (my GPU). I don't understand why.

So I re added 1002:aac8 to my /etc/modprobe.d/local.conf file so it would bind to vifo-pci at boot again and simply just removed this line from my VM start script:
```

-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \

```

The AMD catalyst software then didn't attempt to install the HDMI audi driver and didn't crash Windows, causing me to believe that the issue is with the HDMI audio driver and not that of the GPU one.

Hope this helps others!!

---

### Post by kvm-kim on 2016-07-30
> **DanHorniblow said:**
> IT WORKS!!

So after revisiting one of the links I posted above I noticed this:


Firstly I tried unbinding the HDMI audi device from vfio-pci by removing 1002:aac8 from my /etc/modprobe.d/local.conf file I created earlier in the post, this caused qemu to fail to passthrough 1002:67b0 (my GPU). I don't understand why.

So I re added 1002:aac8 to my /etc/modprobe.d/local.conf file so it would bind to vifo-pci at boot again and simply just removed this line from my VM start script:
```

-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \

```

The AMD catalyst software then didn't attempt to install the HDMI audi driver and didn't crash Windows, causing me to believe that the issue is with the HDMI audio driver and not that of the GPU one.

Hope this helps others!!

It would be wonderful if you wrote a nice clean updated HowTo for Ubuntu 16.04, outline the process step by step just as the original pudget article did. Can you do that for us please?  :)

---

### Post by yanman on 2016-07-30
> **kvm-kim said:**
> It would be wonderful if you wrote a nice clean updated HowTo for Ubuntu 16.04, outline the process step by step just as the original pudget article did. Can you do that for us please?  :)

I'm trying to do the same, and given I'm prob more of a newb I might provide a bit of newb-perspective :)

So far I've come across a lot of issues not covered in that original guide.

My progress so far:
- Install 16.04 Desktop from USB with UEFI (caused me a few issues cos the D30 board refused to boot without "Windows Boot Manager" label)

- Step 1 of earlier guide:

kvm and kvm_intel were already present in /proc/modules so I only added the remaining ones
after editing the grub file to add the line i got this error:
```
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
```
So I changed the GRUB_TIMEOUT to 0
IOMMU didn't give the exact output but I did at least get the "IOMMU enabled":
```
[    0.000000] DMAR: IOMMU enabled
[    1.883832] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.883835] AMD IOMMUv2 functionality not available on this system
```

- Step 2:

I have an HD6970 at the moment but am planning on going nVidia next. I'm also going headless on the host so I figured I may as well remove the GPU from the host
Might be handy to point out that I'm not sure whether the UEFI BIOS mod for this card actually worked. When checking the output of some EFI-checking scripts it still doesn't appear right
```
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman XT [Radeon HD 6970] [1002:6718]
03:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series] [1002:aa80]
```
I tried the steps to get it claimed by the stub but the radeon module was grabbing it first.
```
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cayman XT [Radeon HD 6970]
        Subsystem: Hightech Information System Ltd. Cayman XT [Radeon HD 6970]
        Kernel driver in use: radeon
        Kernel modules: radeon
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
        Subsystem: Hightech Information System Ltd. Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
        Kernel driver in use: pci-stub
        Kernel modules: snd_hda_intel
```
I tried adding "radeon" to /etc/initramfs-tools/modules, but still no luck.
Then I came across this bit of advice:
> This is happening because the radeon module is taking control of the device before pci-stub, so you need to reverse the load order.

Blacklist the radeon module (as root):

$ echo blacklist radeon >> /etc/modprobe.d/blacklist.conf
And add the module to initrams (as root):

$ echo radeon >> /etc/initramfs-tools/modules
$ update-initramfs -u
After, reboot. Problem solved!

.. and it fixed it:
```
[    2.398945] pci-stub: add 1002:6718 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.398958] pci-stub 0000:03:00.0: claimed by stub
[    2.398980] pci-stub: add 1002:AA80 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.398985] pci-stub 0000:03:00.1: claimed by stub
```

Next was KVM.. the problem being that the guide skipped this. I have no experience setting up KVM and there were several different methods I found in various VM-passthrough guides so here's what I've done so far:
```
apt install qemu-kvm libvirt-bin hugepages ubuntu-vm-builder bridge-utils
```
one guide mentioned spice and spice-client but my apt search didn't return the exact same names :/ not sure if that's needed?

- Step 3 - no issues here, I just followed

- Step 4 - I wanted to use a NVMe SSD so I had to also install nvme-client and follow a few other guides for nvme prep before I could create the .img here

- Step 5 - I followed this, but seeing my results in #6 I wonder whether I am missing vfiobind? There's no such command on my install so far

- Step 6 - didn't boot.. wasn't super surprised though given the early days

```
frank@lensvr:~$ sudo /usr/vm1
[sudo] password for frank:
cat: /sys/bus/pci/devices//vendor: No such file or directory
cat: /sys/bus/pci/devices//device: No such file or directory
/usr/vm1: line 12: echo: write error: Invalid argument
qemu: could not load PC BIOS '/usr/share/qemu/bios.bin'
/usr/vm1: line 31: -boot: command not found
```

---

### Post by ODTech on 2017-01-19
[http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3](http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3) 

Maybe try this driver. It's the Realtek HDMI HD driver used by AMD cards.

---

### Post by yanman on 2017-02-28
> **ODTech said:**
> [http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3](http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3) 

Maybe try this driver. It's the Realtek HDMI HD driver used by AMD cards.
It's okay I got past that point now :p Just working on some lock-up issues and getting some great help here:
[https://ubuntuforums.org/showthread.php?t=2266916&goto=newpost](https://ubuntuforums.org/showthread.php?t=2266916&goto=newpost)

---

