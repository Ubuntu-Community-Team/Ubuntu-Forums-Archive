---
title: "Ubuntu 14.04 KVM VGA Passthrough Nvidia GTX &quot;How To&quot;"
date: 2015-01-24
forum: Virtualisation
---

### Post by pepsifx357 on 2015-01-24
I spent a frustrating week trying to get this to work so I hope this thread will help other people out.  I kept getting stuck at "code 43" in windows after installing the nvidia driver.  Turns out I had the wrong version of qemu and didn't use the kvm=off feature, which is the key to passing this card through correctly.

Here are my machine's specs

ASUS Sabertooth 990fx rev2
AMD FX8350
ATI Radeon HD 6450 (Host's Card)
EVGA Nvidia GTX 560 Ti (Windows 7 guest Card)

I used qemu-system-x86_64 version 2.1.2.  It allows you to use kvm=off.  You can get it by using the Jacob Virtualization repo here:
```
sudo add-apt-repository ppa:jacob/virtualisation
```

I had some problems getting the seabios to work right after I upgraded qemu, due to a symlink missing, so do this:
```
sudo ln -s /usr/share/seabios/bios.bin /usr/share/qemu/
```

You're going to need kvm installed using this tutorial:
[https://help.ubuntu.com/community/KVM/Installation]("https://help.ubuntu.com/community/KVM/Installation")

You're also going to need to download the 3.18.0 kernel from here:
[https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.18.tar.xz]("https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.18.tar.xz")

You're going to need the ACS and i915 patches from here:
[https://docs.google.com/file/d/0Bxp_MsrVrNnEQzBGSmE5NE9mOUk/edit]("https://docs.google.com/file/d/0Bxp_MsrVrNnEQzBGSmE5NE9mOUk/edit")
Just click the download button at the top of the page.

Extract the linux-3.18.tar.gz file, I used archive manager to do this. Then move the files from the linux-mainline folder, containing the patches, into the linux-3.18 folder you just extracted.  I'm no compiling expert, but this is what I did:
```
make mrproper
```
```
patch -p1 < override_for_missing_acs_capabilities.patch
```
```
patch -p1 < i915_317.patch
```

After that just make menuconfig or however you want to configure your kernel and then compile.  Don't forget to enable all of the KVM, VFIO, and virtualization things.  If you don't know how to do this, there are hundreds of tutorials on the webs.

Reboot into the new kernel.

Here is the rest of the info you need.  Remember this is for an AMD processor.  If you have an intel processor, you'll have to change the relevant items.  Important stuff in bold.

/etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1"
```

lspci -nn | grep NVIDIA
```
**07:00.0** VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] [**10de:1200**] (rev a1)
**07:00.1** Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [**10de:0e0c**] (rev a1)
```

/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_amd

```

/etc/initramfs-tools/modules
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
pci_stub ids=**10de:1200,10de:0e0c**

```

/etc/vfio-pci1.cfg
```
[B]0000:07:00.0
0000:07:00.1[/B]

```

reboot your computer

Check to make sure the card got stubbed at boot by using
```
dmesg | grep pci-stub
```

You should see your cards ID followed by "claimed by stub" I stubbed both the graphics and the sound on the card.

Now for the Guest's startup script.  I had to patch mine together using like 4 different startup scripts I saw on different forums, youtube, ect.

I have an extra keyboard, mouse, and usb audio device hooked up to my computer just for this and here's my lsusb output, just so you can see how I got the ID's for passing the usb to the guest.

```
lsusb
```
```
Bus 009 Device 002: ID 059b:0579 Iomega Corp. eGo Portable Hard Drive
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 013 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 012 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 007 Device 008: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box**
**Bus 007 Device 007: ID 06a3:8021 Saitek PLC Eclipse II Keyboard**
Bus 007 Device 006: ID 046d:c326 Logitech, Inc. 
Bus 007 Device 005: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 007 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
**Bus 007 Device 003: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller**
Bus 007 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

/usr/Windows

```
#!/bin/bash

configfile=**/etc/vfio-pci1.cfg**

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

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host,**kvm=off **\
-smp 4,sockets=1,cores=1,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=**07:00.0**,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile=/home/ben/Downloads/GF114.rom \
-device vfio-pci,host=**07:00.1**,bus=root.1,addr=00.1 \
-drive file=**/home/ben/KVM-Images/Windows.img**,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=**/home/ben/Downloads/windows.iso**,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
**-usb -usbdevice host:06a3:8021 -usbdevice host:0461:4d03 -usbdevice host:0d8c:013c \**
-boot menu=on

exit 0
```

To make this script executable run

```
sudo chmod +x /usr/Windows
```

Make sure you have a monitor attached to your nvidia card and startup with:
```
sudo /usr/Windows
```

Good luck, I hope this helps people where I got stuck.  The kvm=off feature only works in qemu 2.1.2.

---

### Post by lifehacksback on 2015-02-19
Hello!

Great Tutorial! May I ask if this is applicable to: 1) 14.10 2) 2 nvidia gtx 980m? I just ordered a bonobo extreme with 2 of these suckers and I want to virtualize windows and make it into a gaming machine, so passing through the second nvidia gpu is essential :D Thank You!

---

### Post by pepsifx357 on 2015-02-25
Should work.  I used ATI graphics for the host, but Nvidia should work as well.  Just make sure you don't blacklist the nvidia driver.

---

### Post by jbaldwin9182 on 2015-03-31
The PPA you provided does not seem to have qemu 2.1.2 for Trusty, only 2.0.

I tried unsuccessfully to build the qemu 2.2 packages from Vivid beta, even after installing several unspecified build dependencies.

Don't think this is going to be possible on Trusty without pulling in half a non-LTS release, tried avoiding patching the kernel by using UEFI (which doesn't need the VGA arbiter/acs patches which break KMS) but never got that to work either.

Guess I'll wait for 16.04...

---

### Post by KillerKelvUK on 2015-04-01
> **jbaldwin9182 said:**
> The PPA you provided does not seem to have qemu 2.1.2 for Trusty, only 2.0.

I tried unsuccessfully to build the qemu 2.2 packages from Vivid beta, even after installing several unspecified build dependencies.

Don't think this is going to be possible on Trusty without pulling in half a non-LTS release, tried avoiding patching the kernel by using UEFI (which doesn't need the VGA arbiter/acs patches which break KMS) but never got that to work either.

Guess I'll wait for 16.04...

Using OVMF only removes the need for the VGA arbiter patches... but the passthrough card needs to support EFI ([http://vfio.blogspot.co.uk/2014/08/does-my-graphics-card-rom-support-efi.html](http://vfio.blogspot.co.uk/2014/08/does-my-graphics-card-rom-support-efi.html))

ACS patching is needed if your IOMMU groupings result with the passthrough card within a group that has multiple PCI devices within it, this isn't related to VGA arbitration and is a separate *challenge* ([http://vfio.blogspot.co.uk/2014/08/iommu-groups-inside-and-out.html](http://vfio.blogspot.co.uk/2014/08/iommu-groups-inside-and-out.html))

Its a shame you can't move beyond the LTS release, 14.10 works for me without any modifications for passing through my GTX 650...however I had to apply ACS patches when I wanted to pass through my DVB card as well.

What were your problems with building qemu on 14.04...this should be a viable build candidate.

---

### Post by pepsifx357 on 2015-04-02
Not to fret.  I had the same problem when I reinstalled my system.  The ppa to use now is ppa:jacob/virtualisation.  I've changed my first post to reflect this.  Thanks for the reply!

---

### Post by vincedj on 2015-04-11
Hello,
great tutorial pepsi, I have problem to compile the kernel, I've extracted all the archives the kernel3.18 and the patch. When I finished to apply the patch, If i try to "make menuconfig" the error:

[COLOR=#DD4814]root@ub1404:/home/user/Downloads/linux-3.18# make menuconfig
  HOSTCC  scripts/kconfig/mconf.o
In file included from scripts/kconfig/mconf.c:23:0:
scripts/kconfig/lxdialog/dialog.h:38:20: fatal error: curses.h: No such file or directory
 #include CURSES_LOC
                    ^
compilation terminated.
make[1]: *** [scripts/kconfig/mconf.o] Error 1
make: *** [menuconfig] Error 2
[/COLOR]

---

### Post by KillerKelvUK on 2015-04-11
> **vincedj said:**
> Hello,
great tutorial pepsi, I have problem to compile the kernel, I've extracted all the archives the kernel3.18 and the patch. When I finished to apply the patch, If i try to "make menuconfig" the error:

[COLOR=#DD4814]root@ub1404:/home/user/Downloads/linux-3.18# make menuconfig
  HOSTCC  scripts/kconfig/mconf.o
In file included from scripts/kconfig/mconf.c:23:0:
scripts/kconfig/lxdialog/dialog.h:38:20: fatal error: curses.h: No such file or directory
 #include CURSES_LOC
                    ^
compilation terminated.
make[1]: *** [scripts/kconfig/mconf.o] Error 1
make: *** [menuconfig] Error 2
[/COLOR]

You're missing some required packages. The error message indicates which, install libncurses5-dev...possible you will still have other errors due to missing packages so just google the error msg to find out which package is needed.

---

### Post by mateomiguel on 2015-04-22
> **lifehacksback said:**
> Hello!

Great Tutorial! May I ask if this is applicable to: 1) 14.10 2) 2 nvidia gtx 980m? I just ordered a bonobo extreme with 2 of these suckers and I want to virtualize windows and make it into a gaming machine, so passing through the second nvidia gpu is essential :D Thank You!

I had this same idea. Did it work out for you?

---

### Post by crashtua2 on 2015-05-16
Hello everyone. And what about performance? Same config with GTX980 performs twice slower in dota2 than on native windows.

---

### Post by timbuntu2 on 2015-07-02
> **jbaldwin9182 said:**
> The PPA you provided does not seem to have qemu 2.1.2 for Trusty, only 2.0.

For me, I have to remove the original qemu-system-x86 package 

```
$ sudo apt-get purge qemu-system-x86
```

and reinstall again.:p

---

### Post by ipeek90 on 2015-07-12
Wondering if maybe someone can give some insight to my problem.

I've got it "working" but I can not get the VM to install Windows. The error I get is 

```
qemu-system-x86_64: vfio_bar_write(,0xd2ef, 0x0, 1) failed: Device or resource busy
```

This is when I try and boot from any of the options listed when I press f12 for boot options. 

Here is my startup script

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
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-usb -usbdevice host:046e:6000 \
-usb -device usb-host,hostbus=7,hostaddr=17 \
-drive file=/home/sezotove/win-game.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/sezotove/Downloads/win7.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on

exit 0
```

---

### Post by fredwntr1 on 2015-10-13
Is the i915 patch necessary if you use an FX 8350?

---

