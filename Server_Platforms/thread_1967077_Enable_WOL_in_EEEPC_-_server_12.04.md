---
title: "Enable WOL in EEEPC - server 12.04"
date: 2012-04-27
forum: Server Platforms
---

### Post by colchaodemola on 2012-04-27
I have installed ubuntu server 12.04 in  an EEEPC 900 but till now i am not able to make it wake on lan.
I edited /etc/network/interfaces and add the line ethernet-wol g.

# The primary network interface
auto eth0
iface eth0 inet dhcp
	ethernet-wol g

after that i can see with ethtool eth0
        Supports Wake-on: g
	Wake-on: g


but after a power off , and send the magic packet, the machine does not power up.

I also tried to add the following lines in rc.local


# Allow eth0 to wake up machine
echo enabled > /sys/class/net/eth0/device/power/wakeup

# Configure ACPI
grep `lspci -tv | grep -i ethernet | cut -d- -f2` \
    /proc/acpi/wakeup | cut -d' ' -f1 > /proc/acpi/wakeup



a new power off , and again machine does not power up after a magic packet.

I am out of ideas.

---

### Post by papibe on 2012-04-27
Hi colchaodemola.

I usually start by checking the BIOS. I've seen that the WOL option (not always called that on the BIOS) it can be set on and off there.

Just a thought.
Regards.

---

### Post by colchaodemola on 2012-04-27
There is no option for wol in bios.
But since it worked in windows xp i think it should work in linux too.

---

### Post by elico on 2012-04-28
> **colchaodemola said:**
> There is no option for wol in bios.
But since it worked in windows xp i think it should work in linux too.

because EEEPC is not supporting WOL..

---

### Post by sourchier on 2012-04-29
What nic is this? Would you please  give us the output of lspci.

---

### Post by schmidtbag on 2012-05-11
Did you ever solve this?  I'm getting the same problem on my eee PC 900.  WOL is known to be supported on these netbooks and ethtool confirms that WOL is on, but no matter what I do, the ethernet port powers off (the router's light for it turns off, where other WOL computers aren't doing that) so it just simply can't receive the signal.

Maybe you're getting the same issue?

---

### Post by egpetrich on 2012-05-12
Have you reviewed these threads?

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=1855551](http://ubuntuforums.org/showthread.php?t=1855551)
[http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

I had to tweak the settings on some intermediate devices in order to get wake-on-LAN working on my system.

---

### Post by schmidtbag on 2012-05-12
> **egpetrich said:**
> Have you reviewed these threads?

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=1855551](http://ubuntuforums.org/showthread.php?t=1855551)
[http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

I had to tweak the settings on some intermediate devices in order to get wake-on-LAN working on my system.

Yes, I have.  They didn't answer my question.  I'm just wondering if there's a way to force power to run through ethernet while the computer is off.

---

### Post by egpetrich on 2012-05-14
I haven't looked at the back of my server when it's suspended, so I don't know if the activity lights are running. There's another thread that may give some info:

[http://ubuntuforums.org/showpost.php?p=8863310](http://ubuntuforums.org/showpost.php?p=8863310)

In addition to having wake-on-LAN enabled for your LAN controller, the bus devices above it have to be enabled. I get the impression that this means they'll still have power even when you're in S3.

First, try these two commands:

```
lspci -tv
cat /proc/acpi/wakeup
```

The "lspci" dump will show you the PCI device tree. You need to find the devices sitting above your LAN controller. The proc file "/proc/acpi/wakeup" will show you which devices are enabled during suspend and shutdown. Post the output of those commands here, and maybe I or someone will see something amiss.

---

### Post by schmidtbag on 2012-05-14
```
-[0000:00]-+-00.0  Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
           +-02.0  Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
           +-02.1  Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
           +-1b.0  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
           +-1c.0-[04]--
           +-1c.1-[03]----00.0  Atheros Communications Inc. L2 Fast Ethernet
           +-1c.2-[01-02]--
           +-1d.0  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
           +-1d.1  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
           +-1d.2  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
           +-1d.3  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
           +-1d.7  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
           +-1e.0-[05]--
           +-1f.0  Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801FBM (ICH6M) SATA Controller
           \-1f.3  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
```

```
Device  S-state   Status   Sysfs node
P0P3      S4    *disabled  pci:0000:00:1e.0
P0P4      S4    *disabled  pci:0000:00:1c.0
P0P5      S4    *disabled  pci:0000:00:1c.1
P0P6      S4    *disabled  pci:0000:00:1c.2
P0P7      S4    *disabled  
MC97      S4    *disabled  
USB1      S3    *enabled   pci:0000:00:1d.0
USB2      S3    *enabled   pci:0000:00:1d.1
USB3      S3    *enabled   pci:0000:00:1d.2
USB4      S3    *enabled   pci:0000:00:1d.3
EUSB      S3    *enabled   pci:0000:00:1d.7
```

MC97 is onboard audio which I think I currently have disabled, so I'm pretty sure that can be ignored.

---

### Post by egpetrich on 2012-05-14
Based on your reports, it looks like the LAN controller is device "POP5" (that's papa-oscar-papa-five), and it's listed as "disabled". Given that information, I would enter the following command:

```
cat /sys/devices/pci0000\:00/1c.1/power/wakeup
```

I would expect this to return "disabled". If so, I would then enter these commands:

```
sudo sh -c 'echo enabled > /sys/devices/pci0000\:00/1c.1/power/wakeup'
sudo sh -c 'echo P0P5 > /proc/acpi/wakeup'
```

The pseudo-file under /sys/devices is an informed guess, based on your output from "lspci". If the pseudo-file doesn't exist when you try to "cat" it, you may need to look around further to find it.

When all is said and done, you should see "enabled" for POP5 when you display /proc/acpi/wakeup. Then you can check to see if your LAN hardware is active when you're suspended.

---

### Post by schmidtbag on 2012-05-15
All I had to do was:
echo enabled > /sys/devices/pci0000:00/0000:00:1c.1/power/wakeup

Which did change the POP5 state to enabled automatically.  However, that didn't fix the problem - I can't WOL from suspend or off, and the ethernet port still has no lights when the computer is in those states.

I'm beginning to think this isn't possible on this device.  Know of any cheap USB adapters where this might work?

---

