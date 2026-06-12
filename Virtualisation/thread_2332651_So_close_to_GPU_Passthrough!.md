---
title: "So close to GPU Passthrough!"
date: 2016-08-02
forum: Virtualisation
---

### Post by supermechacow on 2016-08-02
Hey guys! I was hoping someone could help me through this last little bit of this project I was working on. I've been trying to dedicate a pair of GTX 960's to a Windows virtual machine for the occasional gaming. I've moved to Ubuntu full time, and I very much enjoy linux. I don't want to maintain an entire windows installation and dual boot just to play a particular game every once and awhile.

I've been going at it script-kiddie style and following the [well-known puget guide]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/"). Here's the exact steps I took to set this up:

> -> /etc/modules
```
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel 

```

-> /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"

```

-> ```
sudo update-grub

```

-> ```
lspci -nn | grep NVIDIA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1)
02:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)

```

-> /etc/initramfs-tools/modules
```
pci_stub ids=10de:1401,10de:0fba

```

-> ```
sudo update-initramfs -u

```

-> reboot


-> dmesg | grep pci-stub
```
[    2.069389] pci-stub: add 10DE:1401 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.069396] pci-stub 0000:01:00.0: claimed by stub
[    2.069400] pci-stub 0000:02:00.0: claimed by stub
[    2.069401] pci-stub: add 10DE:0FBA sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.069404] pci-stub 0000:01:00.1: claimed by stub
[    2.069406] pci-stub 0000:02:00.1: claimed by stub

```

-> /etc/vfio-pci1.cfg
```
0000:01:00.0
0000:01:00.1

```

-> /etc/vfio-pci2.cfg
```
0000:02:00.0
0000:02:00.1

```

- > ```
dd if=/dev/zero of=windows1.img bs=1M seek=160000 count=0
```

-> /usr/vm1


```
#!/bin/bash


configfile=/etc/vfio-pci1.cfg


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


sudo qemu-system-x86_64 -enable-kvm -M q35 -m 8192 -cpu host \
-smp 2,sockets=1,cores=2,threads=1 \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-drive file=/home/mechacow/windows1.img,id=disk,format=raw,if=none -device ide-hd,bus=ide.1,drive=disk \
-drive file=/home/mechacow/win10.iso,id=isocd,format=raw,if=none -device ide-cd,bus=ide.0,drive=isocd \
-boot menu=on


exit 0

```

-> ```
sudo chmod 755 /usr/vm1

```

The status is that adding/removing "-vga none" from bios line either I can get the VM to run on my linux desktop enough to install Windows (but no GPUs are detected in Windows), or the qemu screen comes up as if it is working, but there is no output from my graphics cards at all. I can't find anything that can tell me if it's at least trying to work or not and just throwing and error.

This has to be the last step before gettting a working VM with GPU passthrough and it's been frustrating.

Does anybody have advice on how to finish this?

---

### Post by KillerKelvUK on 2016-08-04
Hi, so I don't know the guide you're using specifically but it's a little outdated as its using pci-stub. Prior to kernel 4.1 (I think), pci-stub was the way but since the kernel update you can now map devices directly to the vfio-pci driver at boot. This removes all the hassle of scripting the driver/module changes prior to starting your VM.

Also scripting maybe your thing but just in case you are not aware there are a couple of other routes/alternatives that simplify the process and remove potential of user error (no offence intended). If you have a desktop on your host then I'd recommend using virt-manager with libvirt, no desktop then I'd recommend using virsh with libvirt.

Regards a more up-to-date guide from a reputable source aka a Red Hat dev working on KVM and vfio then I'd point you here... [http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html?m=1](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html?m=1)

If all of the above was already known to you and your current method is specifically what you want to achieve then please post back the output of ```
sudo lspci -vvvs 01:
```

Also do you know if your gfx cards are UEFI capable? I'm guessing that if the lspci output shows everything as its needed and your script isn't bad then the reason for your current problems is because you aren't using a UEFI bios (OVFM) so the GFX cards can't initialise.

---

### Post by heiko_s on 2016-08-04
I've prepared a how-to for Linux Mint, a distribution based on Ubuntu. It should work the same or very similar with Ubuntu. See [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692").

I agree with the others that either the graphics card doesn't have an UEFI BIOS, or that you are not using OVFM.

If you are using two identical graphics cards - one for Linux and one for Windows - then pci-stub is not going to work. In this case use vfio-pci. Depending on your kernel version (I run 3.19) you may need to load it as described in the tutorial above (or in one of the comments - there should be a reference).

---

### Post by supermechacow on 2016-08-05
> [COLOR=#000000]Also do you know if your gfx cards are UEFI capable? I'm guessing that if the lspci output shows everything as its needed and your script isn't bad then the reason for your current problems is because you aren't using a UEFI bios (OVFM) so the GFX cards can't initialise.[/COLOR]

I'm using a UEFI motherboard and the two GTX 960's support UEFI. When you say I'm not using a UEFI bios, do you mean that bios image for my QEMU does not support UEFI?

> [COLOR=#000000]If you are using two identical graphics cards - one for Linux and one for Windows - then pci-stub is not going to work. In this case use vfio-pci. Depending on your kernel version (I run 3.19) you may need to load it as described in the tutorial above (or in one of the comments - there should be a reference).[/COLOR]

I am passing two identical cards to the Windows VM. I am using onboard Intel graphics for the Ubuntu host. Does having two identical cards on the guest make a difference?

---

### Post by KillerKelvUK on 2016-08-05
> **supermechacow said:**
> I'm using a UEFI motherboard and the two GTX 960's support UEFI. When you say I'm not using a UEFI bios, do you mean that bios image for my QEMU does not support UEFI?

Yes the virtual machine bios should be OVMF instead of the default/legacy qemu seabios.  For a long time the ovmf package from the main ppa was too old to work with passthrough so I'd usually direct people to a 3rd party source however the its recently been updated so you should be able to install it using apt-get.  My installed version is as shown below, just validate against this before installing yours as if your not on the latest distro I'm not sure what the package version will be.

```

ii  ovmf                                            0~20160408.ffea0a2c-2                                       all          UEFI firmware for virtual machines

```

> **supermechacow said:**
> I am passing two identical cards to the Windows VM. I am using onboard Intel graphics for the Ubuntu host. Does having two identical cards on the guest make a difference?

No, only if you were splitting them between host and guest due to vfio-pci mapping however I understand this has a functional solution also but you should be good to go.

---

### Post by supermechacow on 2016-08-06
KillerKelvUK I tried your guide straight through. The only thing I didn't touch was the hugepages and I took that line out of the script. When I run the script the prompt just sits still and becomes nonresponsive. No new processes seem to be running. The only thing that didn't match your guide exactly was

```
dmesg | grep pci-stub
```

didn't show anything.

I have to use my onboard gpu right now, because it's not using my two graphics cards.

---

### Post by KillerKelvUK on 2016-08-07
> **supermechacow said:**
> KillerKelvUK I tried your guide straight through. The only thing I didn't touch was the hugepages and I took that line out of the script. When I run the script the prompt just sits still and becomes nonresponsive. No new processes seem to be running. The only thing that didn't match your guide exactly was

```
dmesg | grep pci-stub
```

didn't show anything.

I have to use my onboard gpu right now, because it's not using my two graphics cards.

Hey, so the guide actually says to use vfio-pci instead of pci-stub if you are using kernel 4.1 or greater?

Regardless if you want to get pci-stub working then I'd suggest your issue is because you aren't loading the pci-stub module on boot. Have you modified /etc/modules or created a new module.d file and added the pci-stub line item? Remember you need to update your initramfs for these changes to take affect?

---

### Post by heiko_s on 2016-08-07
Which guide? Alex Williamsons guide? It's for Fedora but can be adapted to Ubuntu. I personally had bad experiences with virt-manager, but perhaps recent versions have improved. I find the GUI much more cumbersome than qemu command line options.

Both pci-stub or vfio-pci can be used to bind the graphics cards, though the latter is better in my opinion.

---

### Post by supermechacow on 2016-08-07
Woops, I said your name but meant heiko_s

---

### Post by KillerKelvUK on 2016-08-07
> **heiko_s said:**
> Which guide? Alex Williamsons guide? It's for Fedora but can be adapted to Ubuntu. I personally had bad experiences with virt-manager, but perhaps recent versions have improved. I find the GUI much more cumbersome than qemu command line options.

Both pci-stub or vfio-pci can be used to bind the graphics cards, though the latter is better in my opinion.

Yeah AW's guide, pretty comprehensive I think and yeah I see from read around a that virt-manager is like marmite :)

Definitely had better and more stable experiences using vfio-pci.

---

### Post by heiko_s on 2016-08-08
OK. If you used the pci-stub method and don't get anything with dmesg | grep "pci-stub" then the pci-stub driver doesn't bind to your graphics card. Check which driver binds to the card using
```
lspci -v
```

You may need to blacklist the driver that shows up there. But before you do anything, read this post: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032").

It describes how to use vfio-pci instead of pci-stub to bind the graphics card (I need to update the tutorial - vfio-pci is the better method).

If you have already used vfio-pci you need to run:
```
dmesg | grep "vfio-pci"
```
The result should be similar to the one below:
```
dmesg | grep "vfio-pci"
[    3.908324] vfio-pci 0000:02:00.0: enabling device (0000 -> 0003)
```

---

