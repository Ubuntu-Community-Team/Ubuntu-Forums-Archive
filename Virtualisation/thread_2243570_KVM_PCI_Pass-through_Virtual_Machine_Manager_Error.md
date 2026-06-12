---
title: "KVM PCI Pass-through Virtual Machine Manager Error starting domain"
date: 2014-09-09
forum: Virtualisation
---

### Post by rewt2 on 2014-09-09
Ubuntu 14.04 with KVM set-up, attempting PCI Pass-through of an AMD Radeon card to a Windows 7 VM. The VM was created using Virtual Machine Manager (VMM) and runs. But once I add the PCI Host Device (Radeon card) in VMM and run the VM again, the following error is displayed:

Also note that xorg driver for my PCI AMD Radeon card is installed on the host. Not sure if that would cause problems.

Error:
```

Error starting domain: internal error: Process exited prior to exec: libvirt:  error : cannot limit locked memory to 18253611008: Operation not permitted


Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 96, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 117, in tmpcb
    callback(*args, **kwargs)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1162, in startup
    self._backend.create()
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 866, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: internal error: Process exited prior to exec: libvirt:  error : cannot limit locked memory to 18253611008: Operation not permitted



```

---

### Post by TheFu on 2014-09-10
It is unclear concerning your setup.

You do have 2 separate video cards and monitors, correct?  For passthru, the 2nd GPU must be 100% dedicated to the specific VM.

---

### Post by rewt2 on 2014-09-10
> **TheFu said:**
> It is unclear concerning your setup.

You do have 2 separate video cards and monitors, correct?  For passthru, the 2nd GPU must be 100% dedicated to the specific VM.

Yes. On-board Intel HD 4600 and a PCI AMD Radeon R9 280. 4600 is connected with HDMI to monitor1 and DVI to monitor2, the 280 is connected via HDMI to monitor1.

 Oddly enough, I removed the PCI device (Radeon card) from the VM hardware, started Windows a few times, re-added the PCI device and now VMM returns a different error "Error starting domain: internal  error: Device 0000:01:00.0 is already in use".

Device ID 0000:01:00.0 is  for the PCI card which I've blacklisted (pci-stub) the host OS from using, yet it  seems to be in use. Any suggestions?

---

### Post by heiko_s on 2014-09-12
I'm not a KVM expert and use Xen on a day by day basis, but you should make sure your AMD graphics card is not attached to any driver. Try this to check:
```
lspci -v | grep -A 12 -i vga
```
and check which driver is attached. In my case it's pciback.

The best source of info on KVM passthrough I know is here: [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")

Perhaps my Xen how-to can explain how to prevent the AMD driver from loading (using pciback): [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013")

Success with VGA passthrough also depends on the hardware. Can you list your m/b and graphics card details?

---

### Post by rewt2 on 2014-09-12
> **heiko_s said:**
> I'm not a KVM expert and use Xen on a day by day basis, but you should make sure your AMD graphics card is not attached to any driver. Try this to check:
```
lspci -v | grep -A 12 -i vga
```
and check which driver is attached. In my case it's pciback.

The best source of info on KVM passthrough I know is here: [https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)

Perhaps my Xen how-to can explain how to prevent the AMD driver from loading (using pciback): [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013](http://forums.linuxmint.com/viewtopic.php?f=42&t=112013)

Success with VGA passthrough also depends on the hardware. Can you list your m/b and graphics card details?




Motherboard is an ASUS Z87 with Intel HD 4600 on-board graphics and PCI Radeon R9 280.

 I've noticed the host OS is loading X.Org X server display driver wrapper, but couldn't disable it. The guide linked in my private message suggests blacklisting the card. Running **lspci -v | grep -A 12 -i vga** displays:

```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at ef800000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8534
    Flags: bus master, fast devsel, latency 0, IRQ 50
--
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Device 3003
    Flags: fast devsel, IRQ 11
    Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at efe00000 (64-bit, non-prefetchable) [disabled] [size=256K]
    I/O ports at e000 [disabled] [size=256]
    Expansion ROM at efe40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: pci-stub

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
    Subsystem: XFX Pine Group Inc. Device aaa0
    Flags: bus master, fast devsel, latency 0, IRQ 10

```

---

### Post by rewt2 on 2014-09-12
I've stopped using VMM and switched to running the Windows VM with QEMU. Perhaps I should start a new thread with all the steps I've done?

Here is the script I run:

```

#!/bin/bash

configfile=/etc/vfio-pci.cfg

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
-bios /usr/share/qemu/bios.bin -vga cirrus \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-drive file=/home/rewt/windows7a.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/rewt/ISO/windows7.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on

exit 0

```

I have two monitors. On-board Intel HD 4600 is connected  with HDMI to  Monitor1 and also DVI to Monitor2, then an AMD Radeon R9 280 is  connected via HDMI  to Monitor1. 

When I run my script with **-vga cirrus** the Windows VM is displayed in a QEMU window. Mouse/keyboard capture stay within the QEMU window, no freeze happens, switching to physical 2nd souce displays nothing, this would indicate the PCI card isn't in use. **Issue:** No PCI pass-though

When I run my script with **-vga none** a black QEMU command window starts on Monitor1, I then manually change source to HDMI2 for  viewing the Windows VM but cannot interact with the keyboard or mouse. Monitor2  flickers to an 8-bit rainbow of colors (see image below). **Issue:** No mouse/keyboard, rainbow on 2nd monitor.




[IMG]http://i.imgur.com/UqABxkp.jpg[/IMG]

---

### Post by heiko_s on 2014-09-15
It seems that primary passthrough doesn't work, so secondary passthrough may be the way to go (-vga cirrus). When you get the qemu Windows display, log in and install Windows as usual. Then after a complete install download the AMD driver and install WITHOUT the AMD control center ( this can cause problems). Install the graphics driver for your card, then reboot the guest. See if that works.

---

### Post by rewt2 on 2014-09-15
> **heiko_s said:**
> It seems that primary passthrough doesn't work, so secondary passthrough may be the way to go (-vga cirrus). When you get the qemu Windows display, log in and install Windows as usual. Then after a complete install download the AMD driver and install WITHOUT the AMD control center ( this can cause problems). Install the graphics driver for your card, then reboot the guest. See if that works.

Yeah, I had to take a totally differnet route, including the use of cirrus. Seems to be working so far, thank you for your time.

---

### Post by froyomuffin on 2014-09-23
Hello, would you mind sharing how you resolved this? I'm having similar issues :)

---

