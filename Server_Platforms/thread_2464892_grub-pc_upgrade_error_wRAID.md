---
title: "grub-pc upgrade error w/RAID"
date: 2021-07-15
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2021-07-15
I have a computer which has two puzzling small problems on a computer running 18.04 LTS

First I am getting the following error whenever I update or```
 run apt install -f
```

```
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried forcing a reinstall that didn't resolve this issue. I didn't purge grub-pc and reinstall, I'm chicken.

It appears that grub works fine I get a grub menu and the boot stars normally.
However at a point in the boot the process stops and I get this message 

```
Press enter for maintenance (or type control-d to continue)

```

Typing <control-d> causes the boot to continue normally and everything completes normally.

I've searched the logs but no joy. I'm thinking of doing a release upgrade to 20.04 to see if that solves it.

---

### Post by oldfred on 2021-07-15
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2021-07-15
You are being told that you have packages that are broken because of having unmet dependencies. The printout from apt has given you a command that will fix those broken packages. What packages are they? The printout from apt usually tells us what packages are broken. Is it Grub? Or, are they two different problems?

Did you run?

```
sudo apt install -f
```

What happened? 

Regards

---

### Post by rsteinmetz70112 on 2021-07-15
> **oldfred said:**
> Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:]
What are you asking me to run from which ppa?
> Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rsteinmetz70112 on 2021-07-15
> **grahammechanical said:**
> You are being told that you have packages that are broken because of having unmet dependencies. The printout from apt has given you a command that will fix those broken packages. What packages are they? The printout from apt usually tells us what packages are broken. Is it Grub? Or, are they two different problems?

I'm not completely sure iof it's one or two problems.  grub-pc is the package that generates and error  

> Did you run?

```
sudo apt install -f
```

What happened? 

Regards

Yes I ran it and got the same error exactly

```
# dpkg --configure -a
Setting up grub-pc (2.02-2ubuntu8.23) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
# apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-pc (2.02-2ubuntu8.23) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've been thinking of purging grub -pc and reinstalling it.

```
# apt purge grub-pc --simulate
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  grub-pc-bin grub2-common
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Purg grub-pc [2.02-2ubuntu8.23] [grub-gfxpayload-lists:amd64 ]
Purg grub-gfxpayload-lists [0.7]
```

---

### Post by Impavidus on 2021-07-15
> **rsteinmetz70112 said:**
> 
```
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```The first error message should be above that. Best just to show the whole output of apt install -f.

> I'm thinking of doing a release upgrade to 20.04 to see if that solves it.

Release upgrades don't solve problems (other than "this release is no longer supported", but that's not your problem). On the contrary, you have to fix this problem before you can even attempt a release upgrade.

Edit: OK, you showed the full output. Not much interesting there on first sight. That's weird.

---

### Post by oldfred on 2021-07-15
If you click on the link to Boot-Repair you should see this:

> [h=2]2nd option : install Boot-Repair in Ubuntu[/h] - either from an Ubuntu live-session ([boot your computer on a Ubuntu live-CD or live-USB]("https://help.ubuntu.com/community/BootFromCD") then choose "Try Ubuntu") or from your installed Ubuntu session (if you can access it) 
- connect to the Internet 
- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type the following commands (press Enter after each line): 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

---

### Post by rsteinmetz70112 on 2021-07-15
OK this is wierd I'm trying to post a response and get a Forbidden error message. I think the code I'm posting may be too long.

---

### Post by rsteinmetz70112 on 2021-07-15
boot repair was installed on my computer but I ran the commands you suggested.
I tried to post the output of the install but I keep getting a forbidden error.
It doesn't seem like it was too long to me.

---

### Post by yancek on 2021-07-15
Run boot repair and click the option to Create BootInfo Summary.  When it finishes, you should get a link which you can post here.

---

### Post by rsteinmetz70112 on 2021-07-16
Hopefully today I'll get to run boot-repair I had to make an new 18.04 live media. 
I also noticed this thread this morning.
[https://ubuntuforums.org/showthread.php?t=2461875](https://ubuntuforums.org/showthread.php?t=2461875)

---

### Post by rsteinmetz70112 on 2021-07-16
I ran boot-repair here is the pastbin 
[http://paste.ubuntu.com/p/qbWmkGnhGM/](http://paste.ubuntu.com/p/qbWmkGnhGM/)
when I ran boot repair it wanted to remove dmraid, however since my compter uses mdadm and LVM2 I said no. It then installed mdadm.

---

### Post by oldfred on 2021-07-16
Do not know RAID nor LVM.
Moving to server sub-forum where users that do know those details may be able to help.

I do have this in my notes.
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.
[dmraid] packages may interfere with MDraid. 

You need to resolve these errors.
```
mount -r /dev/sdd3 : Error code 12
Error code 32
mount -r /dev/dm-5 /mnt/boot-sav/dm-5

```

---

### Post by rsteinmetz70112 on 2021-07-16
The problem with resolving these errors is that I ran boot-repair from a live session and I don't know which actual drives it refers to.
When booted normally

sda is 2Gb has 1 partition ext4 filesystem external USB
sdb is 1GB has 3 partitions
sdc is 1GB has 1 partition 
sdd is 1Gb has 3 partitions
sde is 1GB has 1 partition

md 126 contains sde1 and sc1 it contains LVM volumes
md0 contains sdb1 and sdd1  it contains LVM volumes
md1 contains contains sdb2 and sdd2  it contains LVM volumes

That leaves sdb3 and sdd3 as unaccounted for. 
sdb3 is an unmounted ext4 filesystem
sdd3 is an unformatted Linux partition
On both sdb and sdd there is additional unformatted space after the 3rd partition.

Neither of those partitions are mounted in fstab so I'm not sure where those errors come from, especially the one referring  /mnt/boot-sav since I don't seem a mount point a /mnt/boot-sav
Normally dm-5 is a link to /dev/mapper/system-root which mounts on / or a link 2 /dev/system/root.

Also when booting normally the boot process stops with this message(I hope I transcribed it correctly):

```
[   0.000000] do_IRQ: 0.55 No irq handler for vector
[   3.380438] xhci_hcd 0000:004:00.0 ERROR Transfer event for unknown stream ring slot 2 cp.2
[   3.380438] xhci_hcd 000:04:00.0: @00000000 41082460 00000000 00000000 1b000000 02038001
You are in emergency mode: After logging type "journalctl -xb" to view system logs, "systemctl reboot" to reboot, "systemctl default" or "exit to boot into default mode.
Give root password for maintenance (or press Control-D to continue)
```

Pressing Control-D allows the computer to complete booting successfully.

---

### Post by MAFoElffen on 2021-07-16
> **rsteinmetz70112 said:**
> OK this is wierd I'm trying to post a response and get a Forbidden error message. I think the code I'm posting may be too long.
*** No, not that weird... This is tied to a new known problem with the Forums Software. *** (Am being told they are working on it.)

I reported this to the Admin's just after the last Forum's Maintenance. It's erroring on posting some commands, even if they are contained in code or quote tags... To post something that I needed to for a user, to get around that posting problem, I had to break the one command into several "pieces" across several codes tag, just so the forum filter would not not see if as some malicious/forbidden filtered out string. It's happening in PM's also.

---

### Post by MAFoElffen on 2021-07-16
I have some background questions...

Don't get nervous about it mentioning dmraid. mdadm and dmraid are different animals, and do different things. YannBuntu has asked me to consult him on some minor things in his boot-repair app. He has done an amazing job on that. All credit to him. We have talked about the scripting and shared ideas for a project I was working on, for a GUI as a wrapper for mdadm...

"mdadm" is "the accepted" Linux Software Raid. "dmraid", is a Linux utility that discovers, activates, deactivates and displays properties of software RAID sets. He is using that in his scripting to use the Linux device-mapper to find RAID devices with their respective mappings. Not sure why "reinstalling" (try that first, rather than first removing) Grub would remove dmraid(?) 

Is this system still running? Meaning that  you haven't tried to reboot since you started this and the raid is still actively assembled? Then you can use mdadm to query it's health, members and layout. 
 you can read the filesystems on the assembled raid objects? Is would be useful to first see:
```
cat /etc/mdadm/mdadm.conf
cat /proc/mdstat
```
I am hoping that this is still running and not interrupted. That would be a lot easier. Because you can use mdadm to query the individual members of the sets, to see which sets they belong to and what order they are in those sets.

If it is not running and you are using a LiveCD system, can you mount the installed filesystem and successfully mount the assembled RAID Sets?

 That may be too much detail for what you really need. But is still useful, if needed. Because what you really need is for Grub to work...

*** AS I understand this, it is just having trouble with the grub package right? But grub has to see how it is laid out... with mdadm "and" LVM before it can do it... then create the intramfs image after that, for it to be able to boot from it correctly. That is now how grub reads raid sets and is able to boot from it. (without having to have a separate normal boot partition). Grub and the intramfs images are in  (lvmid/fkP78I-v54Y-syYD-X9VA-wgBP-62Lu-78Iwz7/Vosyl7-KwOv-EoIc-NBc2-o1dn-9a    3c-R9MYlE)/boot/, which is in LVM, which in in one of the three mdadm RAID device sets... So more info is needed to see what partitions are tied to what sets, what those sets are in personality, and how LVM is related to those sets.

Next question: Was this always 18.04 or originally installed as an earlier version?

EDIT: I see (now) that it still boots, but with errors...

---

### Post by rsteinmetz70112 on 2021-07-16
> **MAFoElffen said:**
> I have some background questions...

To oldfred, don't get nervous about it mentioning dmraid. mdadm and dmraid are different animals, and do different things. YannBuntu has asked me to consult him on some minor things in his boot-repair app. He has done an amazing job on that. All credit to him. We have talked about the scripting and shared ideas for a project I was working on, for a GUI as a wrapper for mdadm...

"mdadm" is "the accepted" Linux Software Raid. "dmraid", is a Linux utility that discovers, activates, deactivates and displays properties of software RAID sets. He is using that in his scripting to use the Linux device-mapper to find RAID devices with their respective mappings. Not sure why "reinstalling" (try that first, rather than first removing) Grub would remove dmraid(?) 

Is this system still running? Meaning that  you haven't tried to reboot since you started this and the raid is still actively assembled? Then you can use mdadm to query it's health, members and layout. 
I believe mdadm was installed because boot-repair detected md devices and I was running in a live environment which does not usually include mdadm.

I'm not sure exactly what you mean here. I booted the system using a live DVD and ran the boot-repair commands to generate the pastebin I posted earlier.
I then rebooted the computer into its original state and it is still running. This computer is my companies mail server and I'm reluctant to leave it down for long. I can boot into a live session or reboot if necessary I don't mind doing that.
When booted normally the raid and LVM are assembled and activated normally.

>  you can read the filesystems on the assembled raid objects? Is would be useful to first see:
```
cat /etc/mdadm/mdadm.conf
cat /proc/mdstat
```
I am hoping that this is till running and not interrupted. That would be a lot easier.

If it is not running and you are using a LiveCD system, can you mount the installed filesystem and successfully mount the assembled RAID Sets? 
It is running not not from a live system.
```
# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=a1c15a2b:6ba03c3e:448de4d4:07e4e535
ARRAY /dev/md/2  UUID=50ce1068:0f35d145:f046d243:b301d3af
ARRAY /dev/md1 UUID=a5865e80:27a899df:bfaac05b:eff3fc62
ARRAY /dev/md/126  UUID=07950f05:69cb75e8:1e0efbd2:0d73f6b2
```

```
# cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md126 : active raid1 sde1[0] sdc1[1]
      976629760 blocks super 1.2 [2/2] [UU]
      bitmap: 3/8 pages [12KB], 65536KB chunk

md2 : active raid1 sdd2[1] sdb2[0]
      459959296 blocks super 1.2 [2/2] [UU]
      bitmap: 1/4 pages [4KB], 65536KB chunk

md0 : active raid1 sdd1[0] sdb1[1]
      78148096 blocks [2/2] [UU]

unused devices: <none>

```

I hadn't noticed the reference to md1 but I think it's obsolete since I changed out some of the drives a while ago. In any event it doesn't matter it it's not there.


> *** AS I understand this, it is just having trouble with the grub package right? But grub has to see how it is laid out... with mdadm "and" LVM before it can do it... then create the intramfs image after that, for it to be able to boot from it correctly. That is now how grub reads raid sets and is able to boot from it. (without having to have a separate normal boot partition. Grub and the intramfs images are in  (lvmid/fkP78I-v54Y-syYD-X9VA-wgBP-62Lu-78Iwz7/Vosyl7-KwOv-EoIc-NBc2-o1dn-9a    3c-R9MYlE)/boot/, which is in LVM, which in in one of the two mdadm RAID device sets... So more info is needed to see what partitions are tied to what sets, what those sets are in personality, and how LVM is related to those sets.

Next question: Was this always 18.04 or originally installed as an earlier version?
Whenever I run an upgrade I get the error message shown above above about grub-pc. Similar messages show up when ever dpkg is run or when initramfs is rebuilt. It hasn't seemed to really cause any problems, but I don't think it's good.
 
There is another possibly unrelated problem where the boot process stops in the middle and drops into "emergency mode". That is interfering with remote administration since I cannot reboot remotely.

The computer was upgraded from 16.04 LTS and earlier versions but ran 18.04 for a long time before this problem appeared. I have other very similar installs that haven't shown this problem. I have upgraded most of them to 20.04 but am holding back on this one until I can resolve this.

---

### Post by MAFoElffen on 2021-07-16
I'm looking at your boot errors...

Are any of your drives attached via USB? And if so:
- Is the port(s) USB3.x or USB2.x?
- Is the port(s) an internal to your motherboard, or through a PCIe expansion card?
If multiple drives are... are they attached to ports of differing USB Types? (2 and 3?)
```
uname -r
sudo lspci | grep -i "USB"
sudo lsusb
dmesg | grep -i -a5 "[COLOR=#333333][FONT=sans-serif]xhci"[/FONT][/COLOR] 
```
And what motherboard is the system?

EDIT: The reason I'm asking those is that usually that error is related to a firmware problem, related to USB3.x... (Which then sometimes causes Kernel Panic.) I'm looking if your two problems are related the each other or separate problems.  But I think this problem is actually your immediate, most important priority.

---

### Post by rsteinmetz70112 on 2021-07-16
> **MAFoElffen said:**
> I'm looking at your boot errors...

Are any of your drives attached via USB? And if so:
- Is the port(s) USB3.x or USB2.x?
- Is the port(s) an internal to your motherboard, or through a PCIe expansion card?
If multiple drives are... are they attached to ports of differing USB Types? (2 and 3?)
```
uname -r
sudo lspci | grep -i "USB"
sudo lsusb
dmesg | grep -i -a5 "[COLOR=#333333][FONT=sans-serif]xhci"[/FONT][/COLOR] 
```
And what motherboard is the system?

EDIT: The reason I'm asking those is that usually that error is related to a firmware problem, related to USB3.x... (Which then sometimes causes Kernel Panic.)

There is one USB drive it is connected to a USB 3.x PCIe card. The other 4 drive are SATA connected to SATA ports.
The Mother board is a  ASRock  N68C-GS4 FX. As far as I can tell from the website I have the latest firmware.

```
$ uname -r
4.15.0-47-generic
```


```
# sudo lspci | grep -i "USB"
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
04:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
```

```
# sudo lsusb
Bus 004 Device 002: ID 0bc2:aa14 Seagate RSS LLC
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
$ dmesg | grep -i -a5 "xhci"
[    1.194118] usb usb2: SerialNumber: 0000:00:02.0
[    1.194247] hub 2-0:1.0: USB hub found
[    1.194254] hub 2-0:1.0: 10 ports detected
[    1.194468] ohci-platform: OHCI generic platform driver
[    1.194476] uhci_hcd: USB Universal Host Controller Interface driver
[    1.194525] xhci_hcd 0000:04:00.0: Resetting
[    2.076138] tsc: Refined TSC clocksource calibration: 3214.619 MHz
[    2.076195] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2e563bf53da, max_idle_ns: 440795214095 ns
[    2.236295] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    2.236300] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    2.241576] xhci_hcd 0000:04:00.0: hcc params 0x014050cf hci version 0x100 quirks 0x0000000000000090
[    2.241849] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.241851] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.241852] usb usb3: Product: xHCI Host Controller
[    2.241854] usb usb3: Manufacturer: Linux 4.15.0-47-generic xhci-hcd
[    2.241855] usb usb3: SerialNumber: 0000:04:00.0
[    2.242026] hub 3-0:1.0: USB hub found
[    2.242034] hub 3-0:1.0: 2 ports detected
[    2.242129] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    2.242132] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    2.242135] xhci_hcd 0000:04:00.0: Host supports USB 3.0  SuperSpeed
[    2.245098] usb usb4: We don't know the algorithms for LPM for this host, disabling LPM.
[    2.245122] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.245124] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.245125] usb usb4: Product: xHCI Host Controller
[    2.245126] usb usb4: Manufacturer: Linux 4.15.0-47-generic xhci-hcd
[    2.245127] usb usb4: SerialNumber: 0000:04:00.0
[    2.245287] hub 4-0:1.0: USB hub found
[    2.245297] hub 4-0:1.0: 2 ports detected
[    2.245460] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.248158] serio: i8042 KBD port at 0x60,0x64 irq 1
--
[    3.181311] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.181591] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.181680] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.181760] ata2: port disabled--ignoring
[    3.184101] [drm] Initialized nouveau 1.3.1 20120801 for 0000:00:0d.0 on minor 0
[    3.340554] usb 4-2: new SuperSpeed USB device number 2 using xhci_hcd
[    3.366254] usb 4-2: New USB device found, idVendor=0bc2, idProduct=aa14
[    3.366256] usb 4-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    3.366257] usb 4-2: Product: Basic
[    3.366258] usb 4-2: Manufacturer: Seagate
[    3.366260] usb 4-2: SerialNumber: 00000000NABC59D0
--
[    3.379755] sd 6:0:0:0: [sda] 3907029167 512-byte logical blocks: (2.00 TB/1.82 TiB)
[    3.379757] sd 6:0:0:0: [sda] 4096-byte physical blocks
[    3.379834] sd 6:0:0:0: [sda] Write Protect is off
[    3.379835] sd 6:0:0:0: [sda] Mode Sense: 4f 00 00 00
[    3.379995] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.380438] xhci_hcd 0000:04:00.0: ERROR Transfer event for unknown stream ring slot 2 ep 2
[    3.380478] xhci_hcd 0000:04:00.0: @0000000411082460 00000000 00000000 1b000000 02038001
[    3.384043] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.386489] ata3.00: ATA-8: TOSHIBA HDWD110, MS2OA8J0, max UDMA/133
[    3.386491] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.391165] ata3.00: configured for UDMA/133
[    3.391353] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA HDWD110  A8J0 PQ: 0 ANSI: 5

```

---

### Post by rsteinmetz70112 on 2021-07-16
Is the USB 3.0 problem related to Linux, the motherboard or the PCIe Card or some interaction between them. 

I can easily get a different PCIe card if that would solve it.

I did some googling on the errors and saw some old references to USB controllers and kernel bugs but that was several years ago on 3.x kernels. I figured it was fixed by now.

---

### Post by MAFoElffen on 2021-07-16
I dove into it. The problem is not related to the firmware on the motherboard.

The problem is related to the "Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)" card and Linux Kernels 4.12 through 4.8. There seems to be reports on that card with three different problems.
 1. uPD720202 controllers without a ROM, so the correct driver or the kernel module is buggy.
 2. uPD720202 controllers with a ROM, but old firmware.
 3. uPD720202 controllers not working or not working right when IOMMU is enabled.

The easiest to deal with would be to add a "amd_iommu=off" as a kernel boot option in grub, and see if that helps that.

The others vary, and are related to if your specific card has an onboard ROM or not. If it does have a ROM, then it can be easily updated via Windows. You could do it from Linux, but it is an ugly affair. The bug reports I see for this card and Kernels 4.12 though 4.8 are still open and still active.

---

### Post by MAFoElffen on 2021-07-16
> **rsteinmetz70112 said:**
> Is the USB 3.0 problem related to Linux, the motherboard or the PCIe Card or some interaction between them.Yes. I can see that the error is on Bus 4, which that when that card initializes it creates as Bus 4. The error points back to BUS 4, and an xhci error, which then... has problems with that USB attached drive. Which then causes a problem because a member of the RAID dropped out. Thus the "emergency mode."

> **rsteinmetz70112 said:**
> I can easily get a different PCIe card if that would solve it. If turning off IOMMU does not fix it, then yes, that would be easiest, especially if you need IOMMU for other things like SR-IOV...

> **rsteinmetz70112 said:**
> I did some googling on the errors and saw some old references to USB controllers and kernel bugs but that was several years ago on 3.x kernels. I figured it was fixed by now.May have on those old reports... But it started having problems again after Kernel Versions 4.12 through 4.8, which are now. Those reports are open and active as now.

---

### Post by rsteinmetz70112 on 2021-07-16
Would upgrading to the HWE kernel solve the issue? Its currently 5.3.
.
Would upgrading to 20.04 solve the issue? Its kernel is 5.4.

---

### Post by MAFoElffen on 2021-07-16
It "may"... I don't see anything on it Kernel versions after 4.8. A quick and easy test for that would be to boot the machine off a 20.04.2 LiveCD image, which has Kernel Version 5.8, and check dmesg for xhci_hcd. At least that way, you can see if it corrects it without having to go through a whole release upgrade and failing in the process. (Because of the, now, known problem.)

*** My number one recommendation is that before you do anything, make sure you have a good backup. You already know you have intermittent problems writing and reading from disk, because of that controller. A release upgrade is a heavy taxing load.

Also the best practice recommended would be to "Migrate to", instead of upgrade in place, so you don't carry extraneous problems forward. or recreate orphaned objects, such as that MD member that went away, isn't used anymore, but still shows up in some of your configs...

---

### Post by rsteinmetz70112 on 2021-07-16
I'll have to create another live media but testing it seems like a good idea, although when I tested the 18.04 media I didn't see the problem either. 
I'll have to check and see what kernel version the 18.04 media is.
Oh well maybe I'll get this solved.

I have complete backups of everything, in multiple locations. 

BTW I have live computers that have been migrated from as far back as 6.04 that still work every day without serious problems. 
Since most of my Linux computers are servers of one kind or another migrating configurations is not as easy as desktops where pretty much everything is in the /home directory that can be easily isolated.

---

### Post by MAFoElffen on 2021-07-16
By the way... on your Grub issue, have you tried to do:
```
sudo apt --only-upgrade install grub-common
```
And see what happens after that with apt on an upgrade(?) There seems to be some issues with a recent grub package were starting out that way seems to resolve the issue. Some kind of chicken before the egg affair... 

I understand. I have done the same. There are more things involved than a desktop, as you have configs in /etc/,  /var/, /usr/, network shares, and such... which, again, can be migrated. You know the layout of those, or if not, should document them. You have many services, applications, and idiosyncrasies. I just had to put that disclaimer out there. Why? Because you are not just going to try to do a release upgrade on a production system... but you are doing it on a system that already had problems... which you hope, an upgrade will fix... In the meanwhile, it is not (but intermittent). That process is a high IO process. And  one of the disks is located on a controller that currently is having intermittent problems. I had to say that as a disclaimer.

I wish you luck with that and will have my fingers crossed.

---

### Post by rsteinmetz70112 on 2021-07-17
When I do these things I always cross my fingers, but so far I've always been able to recover, even if it sometimes gets ugly.

Tomorrow I'm going to my local Micro Center to pick up a few parts for this and some other projects.

---

### Post by MAFoElffen on 2021-07-17
Wait... Where is the "original snippet" from the APT log, where it got the oriiginal error? I went back through the thread this morning a didn't see that. Are you sure it was an error on grub-pc, grub-common, or another dependent grub package? Because you haven't tried to reinstall that specific package yet, right?

For example:
```

sudo apt install grub-common
sudo update-grub

# And because you have LVM on RAID...
sudo update-intramfs -u

```
Just want to ensure thaose steps were tried.

---

### Post by rsteinmetz70112 on 2021-07-18
OK some success.  

I swapped out the USB 3 card and replaced it with a different one. The computer now boots without stopping. At least I can now effectively administer it remotely.
I also just realized I can confirm the issue is solved in later releases of Ubuntu or the kernel. I have a computer similar the one I'm working on. It has the same USB 3 PCIe card as the problem machine except it is running 20.04 and has never shown the USB problem.
I have delayed upgrading this one because of the grub-pc problem, which predated the adding the USB3 card and therefore the USB problem.

On the grub-pc error. It only occurs when dpkg runs.

```
# dpkg --configure -a
Setting up grub-pc (2.02-2ubuntu8.23) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
```

```
# apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up grub-pc (2.02-2ubuntu8.23) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
# apt install grub-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
grub-common is already the newest version (2.02-2ubuntu8.23).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up grub-pc (2.02-2ubuntu8.23) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Doesn't seem to be much point in running the other commands since nothing apparently changed and there may be some risk in overwriting a configuration that works.

What do you think of running:

```
# apt purge grub-pc
# apt install gurb-pc

```

or
```
#apt install grub-pc --reinstall
```
How much damage could that do?

---

### Post by MAFoElffen on 2021-07-18
I'll defer to oldfred's thoughts on that.

I'm thinking the install script is still not picking up the EFI variables, that, that script is using to configure on it's own. oldfred picked that up also, when he was asking about changes in the fstab file, where he noted that invalid entries there might trigger that. My preference if it where my machine, I think it would be safer to reinstall, that way if it fails, it roles back to what is there... 

But oldfred might have some more wisdom on that. He's better on EFI grub issues than I, and I respect his thoughts on that. I think he has a better idea of what happens behind the curtains,when it is trying to do it on it's own during an update or install, rather than just from the command line.

EDIT: I have been doing some reading on how that process works. I found this, which seems to try to  explain how Grub gets the EFI Vars, and what goes wrong with them...
 - [https://askubuntu.com/questions/906574/what-does-update-grub-and-modprobe-efivars-programs-do-in-this-case](https://askubuntu.com/questions/906574/what-does-update-grub-and-modprobe-efivars-programs-do-in-this-case)

Seems that he mentioned that the specific system's own EFI BIOS, Grub's efimanager,and the NVRRM have a lot to do with Grub's background processes and the EFI variables.  That when you use the --nonvram option, that overrides the EFI vars.

---

### Post by oldfred on 2021-07-18
Grub-pc is the BIOS boot version of grub. Not sure if it even knows about UEFI.
But it often has errors if you try to install to a gpt partitioned drive without a bios_grub partition. 

I first had that error in 2010 on my BIOS only system and got help from Rod Smith, the author of gdisk who was encouraging the use of gpt.
Grub used to give various errors about trying to install to gpt's protective MBR without bios_grub or directly to a partition's PBR. It would say not recommended an it would have to use blocklists or hard coded addresses. Now it more often than not seems to just fail if install MBR & bios_grub (if gpt) are not correct.

If you have newer UEFI system in CSM mode, it is just BIOS.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
And because UEFI and BIOS write data for operating system differently onto hard drive, you cannot dual boot from grub. You have to reboot which rEFInd seems to be able to do to switch from UEFI and reboot in CSM mode.

---

### Post by rsteinmetz70112 on 2021-07-18
This is not an EFI system. It is pure BIOS. 
As far as I can tell remotely parted tells me every partition table is msdos not gpt. The partitions are  LVM2  PVs with LVs on them.

---

### Post by oldfred on 2021-07-18
LVM - Logical Volumes
They normally are inside a partition which can be either a MBR partitioned drive or a gpt partitioned drive.

---

### Post by MAFoElffen on 2021-07-19
You, oldfred and I were are right. That deserves an explanation.

I discussed the upgrade process with oldfred. He gave me some snippets of logs that pointed me in the right direction. Then I traced through the grub postint scripts... Where the error occurs is when it gathers information on the mdadm devices and LVM device mapper. It doesn't set the code there, but carries the info about the error across.

I researched what would cause an "Exit Code 20". When an MD or LVM device cannot come up during a read status. Most often occurs when it is an MD Device. It is a byproduct, that just occurs when dpkg --configure grub-pc is running and reading the status of the RAID members. Seems to come up more often dealing with a problem of the sync of RAID1. So that specific code is related to a device object, that has multi-volume members, and has a problem with one of the members...

So oldfred asking about the ftsab, which reads the UUID of the MD devices... You asking me if it was related to the PCIe USB3 card error which is intermittently dropping out that RAID Member... Yes, it all does seem to be connected to RAID, and possibly caused by that USB3 extension card.

Here is a few checks on the MD Members that might recreate that from another perspective... Or all least show their health.:
```
sudo mdadm --verify /dev/md{0, 2, 126}
sudo mdadm -D /dev/md{0, 2, 126}

```

---

### Post by rsteinmetz70112 on 2021-07-19
There seems to be something wrong with those commands.

```
# mdadm --verify /dev/md{0, 2, 126}
mdadm: unrecognized option '--verify'
Usage: mdadm --help
  for help
```

Checking the man page there doesn't seem to be a --verify option.


```
# mdadm -D /dev/md{0, 2, 126}
mdadm: cannot open /dev/md{0,: No such file or directory
mdadm: cannot open 2,: No such file or directory
mdadm: cannot open 126}: No such file or directory
```

Running them individually.  You can also run it by listing the devices

```
#  mdadm -D /dev/md0 /dev/md2 /dev/md126
```


```
# mdadm -D /dev/md0
/dev/md0:
           Version : 0.90
     Creation Time : Sun Mar 11 19:05:49 2007
        Raid Level : raid1
        Array Size : 78148096 (74.53 GiB 80.02 GB)
     Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
      Raid Devices : 2
     Total Devices : 2
   Preferred Minor : 0
       Persistence : Superblock is persistent

       Update Time : Sun Jul 18 11:59:33 2021
             State : clean
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

              UUID : a1c15a2b:6ba03c3e:448de4d4:07e4e535
            Events : 0.28526134
```

```
# mdadm -D /dev/md2
/dev/md2:
           Version : 1.2
     Creation Time : Tue Oct 10 09:40:12 2017
        Raid Level : raid1
        Array Size : 459959296 (438.65 GiB 471.00 GB)
     Used Dev Size : 459959296 (438.65 GiB 471.00 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Mon Jul 19 09:45:43 2021
             State : clean
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : bitmap

              Name : thelma:2  (local to host thelma)
              UUID : 50ce1068:0f35d145:f046d243:b301d3af
            Events : 603566

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       50        1      active sync   /dev/sdd2
```



```
# mdadm -D /dev/md126
/dev/md126:
           Version : 1.2
     Creation Time : Sun Mar 11 14:36:58 2018
        Raid Level : raid1
        Array Size : 976629760 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976629760 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Mon Jul 19 09:44:01 2021
             State : clean
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : bitmap

              Name : thelma:126  (local to host thelma)
              UUID : 07950f05:69cb75e8:1e0efbd2:0d73f6b2
            Events : 51408

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
```

You mentioned the /etc/fstab file;

```
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system>       <mount>              <type>      <options>  <dump>  <pass>
proc                    /proc                 proc        defaults       0    0
/dev/mapper/system-root /                     ext4        defaults       0    1
/dev/mapper/system-tmp  /tmp                  ext4        defaults       0    2
/dev/mapper/system-var  /var                  ext4        defaults       0    2
/dev/mapper/system-www  /var/www              ext4        defaults       0    2
#/dev/mapper/system-home /home                ext4        defaults       0    2
/dev/md/2                /home                reiserfs    defaults       0    2
dev/mapper/system-swap   none                 swap        sw             0    0
/dev/mapper/system-xtra /var/mail             ext4        defaults       0    2
/dev/mapper/thelma-root /files/thelma         reiserfs    defaults       0    2
/dev/mapper/thelma-var  /files/thelma/var     reiserfs    defaults       0    2
/dev/mapper/thelma-tmp  /files/thelma/tmp     reiserfs    defaults       0    2
/dev/mapper/thelma-www  /files/thelma/var/www reiserfs    defaults       0    2
/dev/thelma/swap none                  swap        sw             0    0
#/dev/sda3              /boot                 ext4        defaults       0    2
#/dev/md127             /home                 reiserfs    defaults       0    2
/dev/hdc        /media/cdrom0                 udf,iso9660 user,noauto    0    0
/dev/fd0        /media/floppy0                auto        rw,user,noauto 0    0
UUID="701ea8dd-fc4b-426e-b41c-f40ea8dbaa37" /backup ext4 defaults 0 1
```

---

### Post by MAFoElffen on 2021-07-19
I went back and looked at the results of when I asked you this:
```
cat /etc/mdadm/mdadm.conf
cat /proc/mdstat
```
Most of the utilities use mdsat to look at the RAID devices, some use the mdadm.conf ... _They don't match._

You said that the /dev/md1 device that is listed in the mdamd.conf file was from the past and doesn't exist anymore. Maybe it's getting a false negative / failure because the device md1 doesn't exist anymore and cannot open(?) Everything you just posted looks good... But like I said, an Exit Code 20, is a device open error. ...and the part of the script where it is exiting from, is where it is looking at the MD and LVM devices.

Please try to rebuild/update the mdadm.conf file and try again.

*** Please excuse if I have typos or strangeness this morning. My own system is having typing speed issues at the moment. I don't think it's had it's caffeine yet. LOL

---

### Post by rsteinmetz70112 on 2021-07-19
I commented out /dev/md1 in the  mdadm.com file.  That did not solve the problem which only shows up when dpkg is run.

> You asking me if it was related to the PCIe USB3 card error which is intermittently dropping out that RAID Member

Just to be clear the USB3 drive is a single drive used to copy the current filesystem. It is not a RAID member nor does it use mdadm or LVM.

I created an new mdadm.conf using /share/mdadm/mkconf

```
# cat ./mdadm.conf
# mdadm.conf
#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=a1c15a2b:6ba03c3e:448de4d4:07e4e535
ARRAY /dev/md/2  metadata=1.2 UUID=50ce1068:0f35d145:f046d243:b301d3af name=thelma:2
ARRAY /dev/md/126  metadata=1.2 UUID=07950f05:69cb75e8:1e0efbd2:0d73f6b2 name=thelma:126

# This configuration was auto-generated on Mon, 19 Jul 2021 13:50:11 -0400 by mkconf
```

No change. I haven't been able to reboot yet.

```

# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-4.15.0-47-generic
mdadm: /dev/md1 not identified in config file.
```

Not quire sure where that is coming from since there is no /dev/md1 and it's not shown in /proc/mdstat

---

### Post by MAFoElffen on 2021-07-19
See, it is still trying to bring up /dev/md1... So rebuild it from live the md devices...

Just in case...
```
sudo rm /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```
[COLOR=#ff0000]EDITED: I found a quark.  Please post your new maddm.conf file before you try the next step...[/COLOR]
```
sudo update-initramfs -u
```
Then maybe reboot and try that update process again... (But only if it does that without errors.)

*** If I type too fast, my keyboard speed is skipping characters, please check for typos from my end. I'm trying to be careful.

---

### Post by rsteinmetz70112 on 2021-07-19
> **MAFoElffen said:**
> See, it is still trying to bring up /dev/md1... So rebuild it from live the md devices...
already did that.

> Just in case...
```
sudo rm /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```
[COLOR=#ff0000]EDITED: I found a quark.  Please post your new maddm.conf file before you try the next step...[/COLOR]

I rebuilt it with```
 /share/mdadm/mkconf
```
It doesn't contain the /dev/md1

[QUOTE}```
sudo update-initramfs -u
```
Then maybe reboot and try that update process again... (But only if it does that without errors.)

*** If I type too fast, my keyboard speed is skipping characters, please check for typos from my end. I'm trying to be careful.
[/QUOTE]
I tried that and it didn't work see my earlier post. I can't reboot just now. I'll do it as soon as I can.

---

### Post by MAFoElffen on 2021-07-19
So the output of 
```
sudo mdadm --detail --scan 
```
Matches what you copied over?

And now updating your intramfs works without errors? Or not? Because doing that is going to check your system devices and filesystems during that process to make sure everything matches... Just saying. if so, edit your msadm.conf file in the section that is currenly
```
# definitions of existing MD arrays 
ARRAY /dev/md0 UUID=a1c15a2b:6ba03c3e:448de4d4:07e4e535
ARRAY /dev/md/2  metadata=1.2 UUID=50ce1068:0f35d145:f046d243:b301d3af name=thelma:2
ARRAY /dev/md/126  metadata=1.2 UUID=07950f05:69cb75e8:1e0efbd2:0d73f6b2 name=thelma:126

```
So that it reads as:
```
# definitions of existing MD arrays
ARRAY /dev/md0 UUID=a1c15a2b:6ba03c3e:448de4d4:07e4e535
ARRAY /dev/md2 UUID=50ce1068:0f35d145:f046d243:b301d3af
ARRAY /dev/md126 UUID=07950f05:69cb75e8:1e0efbd2:0d73f6b2

```
And verify that 
```
sudo ls /dev/md* 
```
That the output matched those...

Then try to update intramfs again. Tell me if it then has any errors...

---

### Post by MAFoElffen on 2021-07-19
Somehow mt posts got messed up... Wait one...

I edited the above... going on from there...

The edit, I checked with your original post of what you had for your mdadm.conf file, that would convert it to the original form, with the /dev/md1 line out...

---

### Post by rsteinmetz70112 on 2021-07-19
Updating initramfs, I've broken grub. It won't boot except to the grub menu.

---

### Post by rsteinmetz70112 on 2021-07-20
I've now purged and reinstalled grub and that eliminated the grub-pc error. It seems to have been something with the install.

I'm going to make this solved.

Thanks for those who helped.

---

### Post by LHammonds on 2021-07-21
> **rsteinmetz70112 said:**
> Since most of my Linux computers are servers of one kind or another migrating configurations is not as easy as desktops where pretty much everything is in the /home directory that can be easily isolated.
Here is a potential way of getting around the problem of needing to do an upgrade-from-fresh-install but needing to re-use the same hardware.  It is not fun "trying" an upgrade or "trying" a fresh install when the original is replaced and the only recourse is to restore if things go sideways...especially when a restore can take a long time.

Use a virtual machine on a PC or another unused server to install the new version (e.g. server 20.04) and then install the software (e.g. MariaDB, Apache, etc) and configure it to match the original server.  During this time, you can also document how to get a fresh server to the state that it matches the current old version.  If you have the space, you can also perform a data migration to see if it all works correctly.  In some cases, you might even want to point the production IP addresses to the temporary VM as the live server while you perform a re-install on the hardware and then migrate the configuration / data to the newly installed hardware system and move the IP addresses back to make it the production server again.  Downtime can be reduced to just a few minutes and very little risk of "oh no! It did not work, let's restore"

LHammonds

---

### Post by rsteinmetz70112 on 2021-07-22
Thanks I'll consider that for my next adventure.

 I have a very challenging upgrade ahead of me. For reasons that I can't remember I installed my oldest server in 32bit mode, even though it was 64 bit capable and Ubuntu had AMD 64 bit isos (6.06 LTS) this server has been upgraded from one LTS version to the next and is currently 18.04 LTS. All of the hardware has been changed over time most recently 2 years ago. But I need to convert this to 64 bit and upgrade the Samba PDC to  an AD DC. I've know I need to do this for years but I'm chickin.

---

### Post by MAFoElffen on 2021-07-22
Yes, you need to plan for a migration to it being 64bit on Server 20.04 LTS... The 32bit libraries dead-end at 18.04 for LTS versions.

LHammands has suggested a very good strategy for that...

---

