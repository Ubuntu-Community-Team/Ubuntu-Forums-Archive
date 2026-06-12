---
title: "HP Smart Array P212 cciss driver"
date: 2010-06-07
forum: Server Platforms
---

### Post by beckzar on 2010-06-07
Hi,

I need to make a "HP Smart Array P212" HBA-controller work on Ubuntu 10.04 i.e.
have the appropriate "cciss" driver so that my tape unit (a HP StorageWorks 1840 SAS)
can be detected by the "/proc/scsi" subsystem.

Does anyone know how I can make this controller work with Ubuntu? I prefer not to use Red Hat or SUSE which is the only Linux distrbutions supported by HP.

Regards & thanks,
Beckz

---

### Post by beckzar on 2010-09-14
> **beckzar said:**
> Hi,

I need to make a "HP Smart Array P212" HBA-controller work on Ubuntu 10.04 i.e.
have the appropriate "cciss" driver so that my tape unit (a HP StorageWorks 1840 SAS)
can be detected by the "/proc/scsi" subsystem.

Does anyone know how I can make this controller work with Ubuntu? I prefer not to use Red Hat or SUSE which is the only Linux distrbutions supported by HP.

Regards & thanks,
Beckz

Solution:

Add the following to /etc/rc.local

```
echo "engage scsi" > /proc/driver/cciss/cciss0 
echo "rescan" > /proc/scsi/cciss/0
```

---

### Post by abouch on 2011-01-21
Thanks for this - rescued me - as I was having the same problem with a P212 and HP Ultrium 3000 LTO-5 tape drive.

---

### Post by wmeng15 on 2011-02-20
Hi All,
 
I have same problem, and still can not be solved :(
 
I have two machines, one has installed P212 and another has installed P411, I have a HP DAT 160 SAS tape drive, it can be detected if I installed the Windows OS on the two machines, but i can not see the tape drive if I install Unbutu to the machines...
 
I followed several instruction but still does not work... can somebody help me? much appreciated. :)
 
I can not see any tape related information after system start, so I did below actions but no good result :(
 
  modprobe st
  root# lsmod|grep st
           st                     33874  0
  root# dmesg|grep tape
            [  433.884290] st 4:0:0:0: Attached scsi tape st0
            [  433.919733] cciss0: resetting tape drive or medium changer.
  root# dmesg|grep st0
            [  433.884290] st 4:0:0:0: Attached scsi tape st0
            [  433.884303] st 4:0:0:0: st0: try direct i/o: yes (alignment 4 B)
  root# lsscsi
            [1:0:0:0]    disk    ATA      Flash Module     Ver3  /dev/sda
            [4:0:0:0]    tape    HP       DAT160           WS92  /dev/st0
 
  root# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
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

root# cat /proc/driver/cciss/cciss0
cciss0: HP Smart Array P411 Controller
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

root# cat /proc/scsi/cciss/4
cciss0: SCSI host: 4
c4b0t0l0 01 0x0000000000000001

**seems everything is OK, but when I run "mt -f /dev/st0(nst0) status", the system prompted below:**
 
[B]mt -f /dev/st0 status
/dev/st0: No such device or address
[/B]
  
i also tried below command, but still does not work...
 
echo "engage scsi" > /proc/driver/cciss/cciss0      
 
Please help, thanks

---

### Post by cepal on 2011-06-17
Maybe the hardware is dead. That is what happened to me. Symptoms: booting the HP SmartStart (downloadable from HP site) CD, I could see in System Event Log (in Diagnostic Tools) that there wasa Bus Incorrectable Error and when I booted from Ubuntu 10.04 server install CD, it could not find any controller and DMESG clearly showed the RAID controller was DISABLED (by itself). Also the PWR LED was flashing LED but only on next boot... Problem is, it is not the controller what died, but the motherboard (probably North Bridge).

Cheers...

---

