---
title: "[Ubuntu 24.04][Infrared]Failing to load ite-cir"
date: 2024-04-09
forum: Ubuntu Development Version
---

### Post by Swiftjay on 2024-04-09
Hey everyone, I'll pre-face this with saying that I haven't tested any newer OSes besides 24.04, but I do plan on doing so soon on the hardware once I finish some other tests, but I thought I'd try and see if anyone with some experience may be able to provide some help ahead of time.

I have some hardware that uses Ubuntu server 20.04, and we're due to upgrade to a new OS, 24.04, the hardware comes with ITE8708 CIR transceiver that allows us to send and receive IR signals.  This works flawlessly on 20.04, loads up, no issues whatsoever.

This doesn't seem to be the case for 24.04, on boot the driver ite-cir fails to load the kernel module to perform ir operations.

From the journalctl logs The following happens

The kernel attempts to see the transmitter
```

Apr 08 15:26:19 host kernel: rc rc0: lirc_dev: driver ite-cir registered at minor = 0, raw IR receiver, raw IR transmitter
Apr 08 15:26:19 host kernel: proc_thermal 0000:00:04.0: enabling device (0000 -> 0002)
Apr 08 15:26:19 hostkernel: input: ITE8708 CIR transceiver as /devices/pnp0/00:03/rc/rc0/input3

```

Then the kernel doesn't load the transmitter
```

kernel: ite-cir: probe of 00:03 failed with error -16

```

The message was extremely vague, but I looked up what -16 means from kernel error logs, and it seems to say that a -16 means the device is already in use ?  Again not, entirely helpful.

From some searching around there doesn't seem to be much info about people having issues with ite-cir in the past few years.  


If anyone has any experience with this driver and can shed some  light I'd appreciate it.


*update*
While typing this I found a commit that was made to the kernel about my exact driver in 2021 which was shipped to 5.13 but is also now going to 6.9 rc-3 :[https://github.com/torvalds/linux/commit/49e851de7e573529885fd1df4365e2459c6030ee](https://github.com/torvalds/linux/commit/49e851de7e573529885fd1df4365e2459c6030ee) about a failing to probe the module.  My motherboard isn't the same, but perhaps this is related.  I'm going to see if it's possible to use this RC on my device and check if it fixes the issue.

---

### Post by Swiftjay on 2024-04-11
So further update to this is that the kernel patch is back ported to 6.8 (perhaps canonical did this) which means it *should* be working but it isn't.  Upon checking, there's a new module that's associated that's not on our devices with 20.04 `cec`.  I'll, it is "possible" it might be trying to use ite-cir driver but unsure without trying to understand what is using the device driver right now.

```

user@host:~$ lsmod |grep ite
ite_cir                32768  0
rc_core                77824  4 ite_cir,ir_rc6_decoder,rc_rc6_mce,cec

```

I'm going to do some testing with 23.04 and 23.10 in the next few days and see if the IR driver works on either of those versions so maybe it's something that's changed in 24.04 or not.

---

### Post by Swiftjay on 2024-04-12
I've tested 23.04 and 23.10 and it looks like there might be regression/change from the kernel versions that were released

23.04 used kernel 6.2, ite-cir loads just fine
23.10 uses kernel 6.5 ite-cir fails to load due to same issue of 6.8

Something has changed in the ite-cir since 6.2 - 6.5 and will try and investigate more

---

### Post by Swiftjay on 2024-04-15
Further update on this now.

It's not the kernel version, I've downloaded the ite-cir driver for both 23.04 and 24.04 and there is no difference in the code between the two

```

curl https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/noble/plain/drivers/media/rc/ite-cir.c?h=Ubuntu-6.8.0-22.22 -o ite-cir.c.noble
curl https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/lunar/plain/drivers/media/rc/ite-cir.c?h=Ubuntu-6.2.0-39.40 -o ite-cir.c.lunar
diff ite-cir.c.lunar ite-cir.noble

```

Me and my colleague potentially suspected it might be the introduction to a new driver in the rc_core group that potentially might use the device which is causing the resource in use but I black listed cec and the drivers that depended on it and ite-cir still failed.

So this has got me a bit stumped but it has narrowed things down

* The kernel is not the issue
* This looks to be a change from 23.10 onwards before up to 23.04 ite-cir was working as expected

Some next steps for me are to try and compare some changes between 23.04 and 23.10 onward that might of caused this, perhaps there's other drivers that might be using the hardware or something else but if I can find out, hopefully I can file a bug report for Canonical to fix this.

---

### Post by MAFoElffen on 2024-04-16
If it says it "is in use..." You need to check to see what it is being used by. If not by ite-cir, then balcklist what is stealling it and try to insert module itr-cir with verbose turned on, to try to get clues why it fails.

From the ouput you posted, it's on the PVIe bus right? (not USB, right)

How I would approach that (if PCIe)
```

ls pci

```
Look at the output, which will be one line each. Get something from the 'name' of the device in column 2, to use in a grep filter like this
```

lspci -knnn | grep -A3 -E 'Unique_Match_Text'

```
For example, if I use that on a display or NIC:
```

lspci -knnn | grep -A3 -E 'Display|VGA|3D|Ethernet'
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Lenovo 2nd Generation Core Processor Family Integrated Graphics Controller [17aa:21d1]
    Kernel driver in use: i915
    Kernel modules: i915
--
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
    Subsystem: Lenovo ThinkPad T520 [17aa:21ce]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [Quadro NVS 4200M] [10de:1057] (rev a1)
    Subsystem: Lenovo GF119M [Quadro NVS 4200M] [17aa:21d1]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```
As you can see, that algorithm will display what driver and module(s) is/are claiming the device...

---

### Post by Swiftjay on 2024-04-17
Hi MAFoElffen,
Thanks for replying, so the device is a pnp device, I was confused by this a bit as it wasn't showing up on lspci until I did lshw and then I found the device listed there



```

user@host:~$ sudo lshw -class generic
  *-generic:0 UNCLAIMED     
       description: Signal processing controller
       product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm cap_list
       configuration: latency=0
       resources: memory:a1530000-a1537fff
  *-generic:1
       description: Signal processing controller
       product: Cannon Point-LP Thermal Controller
       vendor: Intel Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: driver=intel_pch_thermal latency=0
       resources: irq:16 memory:a1548000-a1548fff
  *-device
       description: SD/MMC Device
       product: DA4064
       vendor: Unknown (69)
       physical id: 1
       bus info: mmc@0:0001
       date: 05/2022
       serial: 
       capabilities: mmc
     *-interface:0
          physical id: 1
          logical name: /dev/mmcblk0rpmb
     *-interface:1
          physical id: 2
          logical name: /dev/mmcblk0
          size: 
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: guid=79af8447-14ec-4512-9e2c-a69e3ccdaa0c logicalsectorsize=512 sectorsize=512
  *-pnp00:03
       product: PnP device ITE8708
       vendor: Integrated Tech Express Inc
       physical id: 3
       capabilities: pnp
  *-pnp00:05
       product: PnP device INT3f0d
       vendor: Interphase Corporation
       physical id: 5
       capabilities: pnp
       configuration: driver=system

```

The device is listed but it doesn't have a configuration because it's not loaded. Further investigations about this device was when we checked the devices folder and found it has a waiting_for_supplier file with the value of 0

```

user@host:~$ ll /sys/devices/pnp0/00:03/
total 0
drwxr-xr-x  3 root root    0 Apr 16 16:01 ./
drwxr-xr-x 13 root root    0 Apr 16 14:01 ../
lrwxrwxrwx  1 root root    0 Apr 16 14:01 firmware_node -> ../../LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:19/ITE8708:00/
-r--r--r--  1 root root 4096 Apr 16 14:01 id
-r--r--r--  1 root root 4096 Apr 16 14:01 options
drwxr-xr-x  2 root root    0 Apr 16 14:01 power/
-rw-r--r--  1 root root 4096 Apr 16 14:01 resources
lrwxrwxrwx  1 root root    0 Apr 15 10:24 subsystem -> ../../../bus/pnp/
-rw-r--r--  1 root root 4096 Apr 16 14:01 uevent
-r--r--r--  1 root root 4096 Apr 16 14:01 waiting_for_supplier

```

I read up that this is due to it waiting to be probed, which doesn't seem to happen due to the device apparently being in use. I haven't found a driver that apparently seems to be using it but I am reviewing the source code of the ite-cir and rc source code with my colleague to try and find out what it's doing when it's initialising a device to hopefully track down what's going on. I'm not familiar with C personally but I'm able to read it slightly with some help and maybe we can see if there's something the kernel thinks is wrong which is causing the issue.

---

### Post by Swiftjay on 2024-04-18
So we investigated the kernel a bit further, and we added some extra logs to the ite-cir module to try and get some details from it

```

Apr 18 15:55:08 host kernel: ite-cir 00:03: pnp_port_len: 8, io_region_size: 8
Apr 18 15:55:08 host kernel: Registered IR keymap rc-rc6-mce
Apr 18 15:55:08 host kernel: rc rc0: ITE8708 CIR transceiver as /devices/pnp0/00:03/rc/rc0
Apr 18 15:55:08 host kernel: rc rc0: lirc_dev: driver ite-cir registered at minor = 0, raw IR receiver, raw IR transmitter
Apr 18 15:55:08 host kernel: input: ITE8708 CIR transceiver as /devices/pnp0/00:03/rc/rc0/input29
Apr 18 15:55:08 host kernel: ite-cir 00:03: >>>>>>>> about to request_region
Apr 18 15:55:08 host kernel: ite-cir 00:03: >>>>>>>> 000000002aec6c49, 8, ite-cir
Apr 18 15:55:08 host kernel: ite-cir 00:03: >>>>>>>> go to exit_unregister

```

The ite-cir sets the device to busy and then checks if everything is ok, if it fails the checks then it will unregister the device.  The last function that it goes to before failing is request_region, this attempts to assign the device into a space in memory on the machine (the 000 number) but it fails to do so.

My senior colleague found that registered port regions can be viewed from /proc/ioports

So on a working OS with ite-cir (20.04) we get this 

```

[LEFT][FONT=Monaco]sudo cat /proc/ioports 0000-0cf7 : PCI Bus 0000:00   
0000-001f : dma1   0020-0021 : pic1   0040-0043 : timer0   0050-0053 : timer1   0060-0060 : keyboard   
0064-0064 : keyboard   0068-0068 : PNP0C09:01     0068-0068 : EC data   006c-006c : PNP0C09:01     
006c-006c : EC cmd   0070-0071 : rtc_cmos     0070-0071 : rtc0   0080-008f : dma page reg   00a0-00a1 : pic2   
00c0-00df : dma2   00f0-00ff : fpu   02f8-02ff : ite-cir   03f8-03ff : serial   0400-041f : iTCO_wdt   0680-069f : pnp 00:04 
[/FONT][/LEFT]

```[LEFT][COLOR=#D1D2D3][FONT=Monaco]

[/FONT][/COLOR][FONT=Monaco]On 24.04 we get

[/FONT]```
[FONT=Monaco]
sudo cat /proc/ioports 
0000-0cf7 : PCI Bus 0000:00   0000-001f : dma1   0020-0021 : pic1   0040-0043 : timer0   0050-0053 : timer1   
0060-0060 : keyboard   0064-0064 : keyboard   0068-0068 : PNP0C09:01     
0068-0068 : EC data   006c-006c : PNP0C09:01  006c-006c : EC cmd   0070-0071 : rtc_cmos     
0070-0071 : rtc0   0080-008f : dma page reg   00a0-00a1 : pic2   00c0-00df : dma2   
00f0-00ff : fpu   02f8-02ff : serial   03f8-03ff : serial   
0400-041f : iTCO_wdt   0680-069f : pnp 00:04
[/FONT]
```[FONT=Monaco]

So it looks like serial devices are now consuming the memory allocation where ite-cir is supposed to be which is why the device is stating its busy or in use.  I'm hoping to try and get a resolution on this in the near future to where we can either resolve this (I'll make sure I post my resolution here for others who may suffer in the future) or we can file a bug report with either Canonical or ite-cir driver maintainer.[/FONT]
[/LEFT]

---

### Post by Swiftjay on 2024-04-19
Good news!  We have solved the issue, so it looked like the serial driver had a kernel change from 6.5 that allowed it to use more than 1 serial port, we believe it was either one of these two CR commits that did it:

* [https://github.com/torvalds/linux/commit/9d86719f8769244dc99b8cb6091c41eae3fd684f](https://github.com/torvalds/linux/commit/9d86719f8769244dc99b8cb6091c41eae3fd684f)
* [https://github.com/torvalds/linux/commit/84a9582fd203063cd4d301204971ff2cd8327f1a](https://github.com/torvalds/linux/commit/84a9582fd203063cd4d301204971ff2cd8327f1a)

```

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 8250, Port: 0x02f8, IRQ: 3

```
This is the same place in memory that the ite-cir should have for this port

So we used setserial to remove the port from being used, modprobed ite-cir...and viola the driver loaded as expected and it's up and running.  The problem is that setserial isn't permanent and we'd then have to do some custom script on boot that would:
* setserial to remove the port 
* remove the ite-cir driver (because it does get loaded even though it doesn't work) then mod probe it back again to fix the issue

We saw there was an option in grub config that set the number uart ports that the serial driver can claim, you need to use 8250.nr_uarts (which isn't documented unless you go to the kernel github code) as nr_uarts will not do this.

So we edited /etc/default/grub and set this to 1 

```

GRUB_CMDLINE_LINUX_DEFAULT="8250.nr_uarts=1"

```

Did a sudo update-grub, rebooted and now there's only one device being claimed and ite-cir driver is working

```

sudo setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

sudo ir-keytable 
Found /sys/class/rc/rc0/ with:
    Name: ITE8708 CIR transceiver
    Driver: ite-cir
    Default keymap: rc-rc6-mce
    Input device: /dev/input/event7
    LIRC device: /dev/lirc0
    Attached BPF protocols: Operation not supported
    Supported kernel protocols: lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp imon rc-mm 
    Enabled kernel protocols: lirc rc-6 
    bus: 25, vendor/product: 1283:0000, version: 0x0000
    Repeat delay: 500 ms, repeat period: 125 ms


```
Before ir-keytable wouldn't even show a device being there, I'm going to do some thorough testing to confirm this is operational but I'm considering the matter, resolved.  Some next steps come into mind before I mark this thread as solved

@[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547") or anyone else at canonical, should we file this bug up stream to the kernel directly or should we send this to your team?

---

### Post by MAFoElffen on 2024-04-22
Just a volunteer, like everyone else. Glad you found out what was wrong.

For your setserial and such, "I" would create a startup script to set those... Pick a timing where it would have to be loaded (after certain things, before others.) Could be triggered by a unit file. It you search me user name, I have a few examples of those posted.

I would file a bug report against Linux. Both the links you posted were from the Kernel GitHub.

---

