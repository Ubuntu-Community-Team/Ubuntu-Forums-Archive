---
title: "Qemu+GPU Passthrough Qemu freezes"
date: 2016-12-26
forum: Virtualisation
---

### Post by growlith1223 on 2016-12-26
so, I'm a bit new to the aspect of virtualization on Linux, and noticed that i could pass a gpu to the VM, i went ahead and decided to try to accomplish this!

it worked...in a sense, i could start the vm with a script, but once it loaded, it just froze. i can't do anything with it, there's no console, i've even done a vnc setup and it just stays at connecting.

I had it somewhat working before but that was with PCI-Stub instead of what i am doing now, which is vfio-pci.

with PCI-Stub, it froze the qemu console but vnc would connect but it just showed a constant "Starting windows..." screen(trying to install Windows 7)

Specs:
CPU: intel core i5-4690k - linux using HD Graphics from cpu
GPU: ZOTAC AMP! Edition GTX 760 - this is the gpu being passed on

my script to launch is:

```
#!/bin/bashsudo qemu-system-x86_64 -enable-kvm -M pc -m 1024 -cpu host,kvm=off \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/seabios/bios.bin -vga none \
-device vfio-pci,host=0000:01:00.0,x-vga=on,multifunction=on -device vfio-pci,host=01:00.1 \
-device qxl \
-vga none \
-vnc :0
exit 0
```

the gpu is being bound correctly at startup(at least i think it is):
```
[   28.443019] vfio_pci: add [10de:1187[ffff:ffff]] class 0x000000/00000000[   28.443023] vfio_pci: add [10de:0e0a[ffff:ffff]] class 0x000000/00000000
[  131.972538] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x900

```

im not sure if i have missed something or what? i have a monitor connected to said gpu being passed too.

I don't know if this helps solving this but my linux boot is using my IGPU on an intel 4690k. and yes, Intel_IOMMU is on

If there is any other information you need, just lemme know!

EDIT: forgot to mention, im on Ubuntu 16.04 LTS

---

### Post by vanbynight on 2016-12-26
Hi I had a lot of problems installing windows on virtual machines in the past but had some success setting up GPU passthrough using 16.04 and 16.10.

If you're just setting up a one off desktop vm virt-manager is a nice tool that you can use on a remote pc. All you need to use it is the libvirt-bin package installed and copy ssh keys for a sudo user to your kvm host. 

You should really check out the GPU passthrough via ovmf article on the arch wiki. It has tons of good info for setting up a working vm and is very up to date. 

16.04 will require adding Jacob Zimmerman's virtualisation (dat typo :/ ) ppa if you use virsh. 16.10 has a newer version of libvirt and qemu and doesn't require any special ppa.

If you would like a more thorough explanation of what needs to be done I guess I could write up a basic how to if duck hook approves :)

---

### Post by KillerKelvUK on 2016-12-27
Hi so there are a few things that aren't quiet right with your script which might be causing you some issues...

(Your origin script with my red highlights)
```

#!/bin/bashsudo qemu-system-x86_64 -enable-kvm -M pc [COLOR=#ff0000]-m 1024[/COLOR] -cpu host,kvm=off \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/seabios/bios.bin [COLOR=#ff0000]-vga none[/COLOR] \
-device vfio-pci,host=0000:01:00.0,[COLOR=#ff0000]x-vga=on,multifunction=on[/COLOR] -device vfio-pci,host=01:00.1 \
[COLOR=#ff0000]-device qxl \
-vga none \[/COLOR]
[COLOR=#ff0000]-vnc :0[/COLOR]
exit 0

```

I'd recommend you increase the memory allocation to the guest, running Windows with 1GB RAM is not going to workout IMO.  Also you have more than 1 "-vga none" device reference which isn't optimal (I believe when more than one device parameter is found qemu will always use the last one and ignore those prior).  Then you are trying to add a virtual QXL graphics device after the vfio-pci lines adding in your passed thru 760, is this intentional i.e. are you trying to get a multi-head vm using both passed thru and virtual GFX devices?  The x-vga=on would only be required if you're attempting to passthrough your primary gfx card (in your case the Intel iGD) so you don't need it.  The multifunction=on is an odd one as I can't locate any references to it in regards to the vfio-pci driver, did you add it here purposefully or were you just copy/pasting from a guide?  (My GTX 970 passes through without it for reference.)  Lastly the vnc device you're attempting to use is bound to the virtual QXL device that I don't believe will ever work in this configuration.

I 2nd vanbynight's recommendation to try something like virt-manager as a tool to help you get up and running with passthrough as well as looking into OVMF as this may become a requirement...it was for my 760 when I got that working...a while back now.

---

### Post by csc2 on 2016-12-27
If you want to use Nvidia's most recent proprietary drivers you're going to need to use the KVM off flags along with spoofing a hyperv vendor id. I'm not sure if the qemu command line offers these but I do know that the later versions of libvirt support it.

---

