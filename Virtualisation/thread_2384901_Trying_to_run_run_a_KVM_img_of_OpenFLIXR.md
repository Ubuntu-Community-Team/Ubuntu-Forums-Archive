---
title: "Trying to run run a KVM img of OpenFLIXR"
date: 2018-02-13
forum: Virtualisation
---

### Post by sinykk on 2018-02-13
I need help trying to setup openflixr on ubuntu server, if someone could lend me a hand.

OpenFLIXR has multiple file formats available: vhd, ova, img, and pvm.

I was able to get the .vhd file working on windows. But I'd prefer to run the img file for kvm that the creator has provided, on ubuntu server (for obvious reasons like OS ram/processor usage)
I've never run a VM in ubuntu before and following the many guides online for installing a kvm, I mess up at the creating a bridge part. I always lose internet when i get to setting up the bridge.

Please excuse any of my mistakes as I'm also new to Ubuntu (I installed it on my daily use computer as my primary OS), so I'm learning.

My computer's specs are as follows:
> Processor: i7 875K
Ram: 16gb
Graphics: nVidia GTX 1070
Storage: 
[LIST]
[*]120gb SSD
[*]2TB HDD
[/LIST]
Connected to the internet through ethernet, though the computer does have a pci-e wifi card.

This is my ifconfig


```
enp0s25: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.58  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::21c:c0ff:fefb:348f  prefixlen 64  scopeid 0x20<link>
        ether 00:1c:c0:fb:34:8f  txqueuelen 1000  (Ethernet)
        RX packets 2323532  bytes 3468997003 (3.4 GB)
        RX errors 0  dropped 429  overruns 0  frame 0
        TX packets 1109417  bytes 83978298 (83.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf3400000-f3420000  

lo:     flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3590  bytes 330136 (330.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3590  bytes 330136 (330.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:1d:bc:bf  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether c4:e9:84:13:e0:c6  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


This is my interface file:

```
auto lo
iface lo inet loopback

iface br0 inet staticaddress 192.168.2.58
        network 192.168.2.0
        netmask 255.255.255.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        dns-nameservers 192.168.2.1
        dns-search openflixr
        bridge_ports enp0s25
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

The instructions from openflixr say:

> 3. Setup a vm using the ubuntu template but make sure to choose seabios as bios type *

4. Choose the vm machine type to be Q35 2.x  (failure to do so will cause issues with your network adaptor on vm)**

5. Attach the vm image to the primary vdisk location


This is what I'm typing for virt-install:

```
virt-install \--name=OpenFLIXR \
    --vcpus=2 \
    --memory=8192 \ [COLOR="#FF0000"](half of my processors and ram. any way to use them all?)[/COLOR]
    --disk path=/var/lib/libvirt/images/OpenFLIXR_2.0_KVM_unRAID.img.zip,size=100 \
    --cdrom=/var/lib/libvirt/images/OpenFLIXR_2.0_KVM_unRAID.img.zip \ [COLOR="#FF0000"](what's the difference between diskpath and cd rom? is diskpath where the storage is and cdrom where the install file is?)[/COLOR]
    --network bridge=br0 \
    --os-type=linux \
    --os-variant=ubuntu16.04 \
--machine=pc-q35-2.7
    --graphics=vnc \

```
I'm not sure where to define the bios.

Edit: I've pieced all of this from reading multiple guides online, and this is basically Frankenstien's baby. Any guidance would be appreciated.
Edit 2: Formatting :)

---

### Post by DuckHook on 2018-02-13
Please refrain from unusual fonts, styles and formatting. This makes your post very hard to read. The use of formatting in code boxes is especially bad because it changes the readout.

Although I can't help you with this one (I've never heard of OpenFLIXR), I would note that your *ifconfig* output is not standard, which leads me to question its accuracy. Your prior formatting may have scrambled it, and it may be worth your while to post another&#8212;this time&#8212;pristine readout so that any helper will be working from data of assured accuracy.

---

### Post by sinykk on 2018-02-14
Thanks for the input. I will post again when I'm home. Hopefully with proper formatting.

---

### Post by KillerKelvUK on 2018-02-18
So I've not been able to grab to a copy of OpenFLIXR as their download server seems borked but looking at your virt-install command I think you have a couple of problems...

>  --disk path=/var/lib/libvirt/images/OpenFLIXR_2.0_KVM_unRAID.img.zip,size=100 \

Firstly, you are pointing to the .zip file, instead you need to point to the .img file so you need to extract that from the .zip file and correct the file pointer in the above.
Secondly, you've included the "size" argument, the manual (man virt-install) advises this is only needed if creating a new disk image, as OpenFLIXR is using a pre-created image this isn't necessary so just remove it.

Lastly regards your query about "disk" vs. "cdrom" you are correct with your assumption...disk is the storage location for the virtual machines hard disk and cdrom is a pointer to any removal storage you want your virtual machine to have access to i.e. installation media...for OpenFLIXR this isn't required.

---

