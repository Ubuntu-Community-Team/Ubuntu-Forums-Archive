---
title: "Ubuntu 14.04 KVM VGA Passthrough.....SO CLOSE!   Need help."
date: 2015-01-23
forum: Virtualisation
---

### Post by pepsifx357 on 2015-01-23
Hi everyone,  

I'm doing this.  I've been at it for a week now.  I started off with CentOS7 and got zero response on their forums, so I switched over to Ubuntu and got miles closer to passing this card.  This is my first post here about my setup.  

Windows 7 starts up on the monitor attached to the Nvidia card.  I've installed the nvidia driver and I get poor resolution and a code 43.  I also have to restart the host if Windows restarts because the monitor won't come back on.  I used "GPU-Z" to dump the rom file and have included it in my startup script, but I still have to restart the host.  

I've messaged a few people on youtube about their setups.  They said I needed the ACS and i915 patches.  The only place I could find those patches are at [https://lkml.org/lkml/2013/5/30/513]("https://lkml.org/lkml/2013/5/30/513") and [https://lkml.org/lkml/2014/5/9/517]("https://lkml.org/lkml/2014/5/9/517").  I downloaded them, but they are text files.  In short....I have no clue how to use these patches.  I've compiled kernels before with something like the Realtime kernel patch, which was a .gz file.  So I need to know the proper procedure for patching a kernel with the patches from those links.

Hardware Stuffs:

ASUS Sabertooth 990FX rev2
AMD FX8350
ATI Radeon HD 6450 (Host's Card)
EVGA 560 Ti (Windows 7 guest's card)

Software Stuffs:
Ubuntu 14.04 (3.16.0-29-generic-lts-utopic) no patches applied.  Standard 14.04 repo KVM installed and all that good stuff.

Grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1"
```

lspci:
```
ben@KVM-Host:~$ lspci | grep NVIDIA
07:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
07:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
```

Stubs:
```
ben@KVM-Host:~$ dmesg | grep pci-stub
[    1.878000] pci-stub: add 10DE:1200 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    1.878015] pci-stub 0000:07:00.0: claimed by stub
[    1.878020] pci-stub: add 10DE:0E0C sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    1.878027] pci-stub 0000:07:00.1: claimed by stub
```

vfio-pci1.cfg
```
0000:07:00.0
0000:07:00.1

```


Guest's startup script:
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

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile=/home/ben/Downloads/GF114.rom \
-device vfio-pci,host=07:00.1,bus=root.1,addr=00.1 \
-drive file=/home/ben/KVM-Images/Windows.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
#-drive file=/home/ben/Downloads/windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-usb -usbdevice host:06a3:8021 -usbdevice host:0461:4d03 \
-boot menu=on

exit 0
```


Please, if anyone knows how to patch the kernel with these patches, or can see an error in my script please OH PLEASE help me out.

Thanks.

---

### Post by TheFu on 2015-01-23
CentOS is mainly used by server administrators - it isn't surprising to me that nobody replied about GUI stuff over there.

---

### Post by pepsifx357 on 2015-01-23
My thought process about using CentOS was that it's basically Redhat and Redhat actively develops KVM, so I assumed it would be the best bet to get this to work.  Needless to say, I was wrong.

---

### Post by pepsifx357 on 2015-01-23
Ok, so now I've compiled a 3.18.0 kernel with the acs override patch and the i915 patch, which can be found at this link: [https://drive.google.com/open?id=0Bxp_MsrVrNnEQzBGSmE5NE9mOUk&authuser=0]("https://drive.google.com/open?id=0Bxp_MsrVrNnEQzBGSmE5NE9mOUk&authuser=0").  I see no difference at all.  Driver still works the same, still can't restart the guest without having to restart the host.  I'm starting to run out of options here.

I GOT IT TO WORK!.....

I'm going to play around with it for a while before I get too excited.  Afterwards I'm going to post EVERYTHING I had to do to get this to work, because There are a lot of things that just weren't discussed in most of the forums...like qemu version seabios version ect.

The only thing I still haven't gotten to work is being able to restart the guest without having to restart the host and right now I can only pass 1 core of the processor to the guest, which kinda sucks.

I have proven to myself, however, that you can pass an NVIDIA GTX card.  You don't need a Nvidia professional card.


Here's my new thread on how I fixed my problem:
[http://ubuntuforums.org/showthread.php?t=2262280]("http://ubuntuforums.org/showthread.php?t=2262280")

---

