---
title: "[Ubuntu Desktop] Xen Hypervisor + Bumblebee = Cannot access secondary GPU | Need help"
date: 2015-10-20
forum: Virtualisation
---

### Post by GhettoGirl on 2015-10-20
Hello dear forum members. I don't know were I should start, but short story: I want to play Windows games which ABSOLUTELY DOESN'T RUN in wine (*100%* Garbage *cough* DX10~12 *cough*) :frown:
Since I have a fully **Hardware Visualization** compatible Laptop (Intel VT-d/GPU passtrough), I decided to give the Xen Hypervisor a try to install a copy of Windows. [COLOR=#ff0000]**NOTE:**[/COLOR] Dual Boot is **NOT** an option, since I'm a strict Linux-only user!!! And I hate the idea to reboot every single time I wanna play these games.

[SIZE=4]First some hardware specs:[/SIZE]
```
TUXEDO Book XC1705
# > lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 980M] (rev ff)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
03:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)

# > lsusb
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 079: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 007: ID 5986:066d Acer, Inc 
Bus 001 Device 002: ID 1e7d:2d5a ROCCAT 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

# > uname -a
Linux GhettoGirl-Ubuntu 4.1.0-040100rc8-generic #201506150335 SMP Mon Jun 15 02:37:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Ubuntu "Vivid Vervet" 15.04

RAM: (DDR3 SO-DIMM): 32 GB (4x 8192MB) 1866MHz Crucial Ballistix Sport
CPU: Intel Core i7-5700HQ (Quad-Core, 4x 2,70 - 3,50GHz)
```

I successfully installed the Xen Hypervisor, no errors while installation. The problem I'm encounting is, that **bumblebee** doesn't work while the Xen Kernel is active.
```
Cannot access secondary GPU | (EE) ... i forgot to note the exact error message. sorry
```

So basically, when the stock kernel is active, bumblebee works 100%, but with the xen kernel, I get this error message when trying to run **optirun glxinfo** or **primusrun glxinfo**.
When I run these command as root = infinite loop (no output, nothing happens), need to invoke Ctrl+C :confused:
Currently I'm running the stock kernel again...

At the moment I didn't go any further (create a vm, etc.), since I won't lose the ability to use the nvidia card in linux.

My question now is: Does the xen kernel breaks **bbswitch** and **gpu access**, or does the kernel takes complete ownership of the gpu???
The Laptop has a status LED which light up, while the NVIDIA card is active. With stock kernel everything is normal, but with xen the LED lights up ALL the time!

When someone can clarify some things out for me, that would be great :D
I really wanna play these games with full 3D/GPU acceleration and NO lags.

Thanks in advance



SIDE NOTE: VMware Workstation doesn't have direct access to the GPU, therefore the games lags like *** and are ultra slow. This is the reason why I wanna setup Xen.

---

### Post by GhettoGirl on 2015-10-22
Ok, I gave up **XEN** and switched to **KVM**
It's much easier to configure (:

I finally have a Windows Guest with full GPU access and working NVidia Drivers

In case you guys are curious.

This is the script I run before booting up the KVM
```
# configfile
configfile=/etc/vfio-pci1.cfg

# bind hardware defined in $configfile to the kvm pci_stub
vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
}

echo -e "\033[1;31m[KVM-SCRIPT] Bind hardware to the kvm pci_stub...\033[0m"
cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done
```
Should be obious what is does. After running this script I cannot use optirun/primusrun. *Cannot access secondary GPU*

And this is the script, to get the hardware back.
```
# configfile
configfile=/etc/vfio-pci1.cfg

# unbind hardware defined in $configfile from the kvm pci_stub
vfiounbind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
}

echo -e "\033[1;31m[KVM-SCRIPT] Unbind hardware from the kvm pci_stub...\033[0m"
cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiounbind $line
done

# turn off the nvidia card after unbinding it from the kvm pci_stub to safe power/battery (laptop)
echo -e "\033[1;31m[KVM-SCRIPT] NVIDIA discrete card: bbswitch <<< OFF\033[0m"
tee /proc/acpi/bbswitch <<<OFF 2>&1 > /dev/null
```
After this command I can use optirun/primusrun again, and I have back the nvidia card for Linux (:

---

