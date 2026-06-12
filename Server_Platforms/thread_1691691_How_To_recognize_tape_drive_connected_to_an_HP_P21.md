---
title: "How To recognize tape drive connected to an HP P212 controller on Ubuntu 10.10"
date: 2011-02-20
forum: Server Platforms
---

### Post by wmeng15 on 2011-02-20
Hi All,
 
I am having a problem with a HP DAT160 SAS tape drive being recognized by ubuntu.
 
I have P212/P411 RAID controller and HP DAT160, they are working fine under Windows System, but the tape drive can not be recognized by Ubuntu OS, the controller is found and it sees a device, but doesn't connected to the tape drive.
 
I have tried LSI RAID controlled with the tape drive on ubuntu system, they are working smoothly for data backup, but we would like to use the P212/P411 controller rather than get a different controller. any suggestion on it?
 
I'm currently have two machines, one has installed P212 and another has installed P411, the HP DAT 160 SAS tape drive can be detected on Windows platform, but I can only see the cciss RAID controller in the ubuntu system, can not see the tape drive...
 
I used Google and followed several instructions but still does not work... can somebody help me? much appreciated. :)
 
I can not see the tape related information after system started, the below are some actions i have taken before but no impact... :(
 
  **root# modprobe st**
[B]  root# lsmod|grep st
[/B]           st                     33874  0
  [B]root# dmesg|grep tape
[/B]            [  433.884290] st 4:0:0:0: Attached scsi tape st0
            [  433.919733] cciss0: resetting tape drive or medium changer.
[B]  root# dmesg|grep st0
[/B]            [  433.884290] st 4:0:0:0: Attached scsi tape st0
            [  433.884303] st 4:0:0:0: st0: try direct i/o: yes (alignment 4 B)
[B]  root# lsscsi
[/B]            [1:0:0:0]    disk    ATA      Flash Module     Ver3  /dev/sda
            [4:0:0:0]    tape    HP       DAT160           WS92  /dev/st0
 [B]  root# lspci
[/B]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 RAID bus controller: Hewlett-Packard Company Smart Array G6 controllers (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

[B]root# cat /proc/driver/cciss/cciss0
[/B]cciss0: HP Smart Array P411 Controller
Board ID: 0x3247103c
Firmware Version: 3.66
IRQ: 45
Logical drives: 0
Current Q depth: 0
Current # commands on controller: 0
Max Q depth since init: 1
Max # commands on controller since init: 1
Max SG entries since init: 1
Sequential access devices: 1

[B]root# cat /proc/scsi/cciss/4
[/B]cciss0: SCSI host: 4
c4b0t0l0 01 0x0000000000000001

**[COLOR=sienna]seems everything is OK, but when I run "mt -f /dev/st0(nst0) status", the system prompted below:[/COLOR]**
 
[B]root# mt -f /dev/st0 status
/dev/st0: No such device or address
[/B]
  
i also tried below command, but still does not work...
 
**root# echo "engage scsi" > /proc/driver/cciss/cciss0      **
 
Please help, thanks

---

