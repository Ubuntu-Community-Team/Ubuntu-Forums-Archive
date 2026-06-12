---
title: "Boot problem"
date: 2018-06-07
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-06-07
Grub was updated yesterday evening. Today the computer will not boot. The motherboard indicates "no boot device" after a CMOS reset. There is no signal to the monitor and it's not possible to access the BIOS menu. This might be similar to the Lenovo boot failure.
[https://forums.lenovo.com/t5/Linux-Discussion/Ubuntu-17-10-corrupts-Lenovo-BIOS-USB-not-recognized-not-saving/td-p/3887679](https://forums.lenovo.com/t5/Linux-Discussion/Ubuntu-17-10-corrupts-Lenovo-BIOS-USB-not-recognized-not-saving/td-p/3887679)
Below is an older inxi, today's installation have the release version of kernel 4.17.
Has anybody else got this problem?
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-20-generic x86_64 bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3743 MHz 1: 3004 MHz 2: 3007 MHz 3: 3004 MHz
           4: 3027 MHz 5: 3027 MHz 6: 3036 MHz 7: 3019 MHz 8: 3006 MHz
           9: 3287 MHz 10: 3005 MHz 11: 3018 MHz 12: 3006 MHz 13: 2996 MHz
           14: 2999 MHz 15: 3581 MHz 16: 3743 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580]
           Display Server: x11 (X.Org 1.19.6 ) driver: amdgpu
           Resolution: 2560x1440@143.99hz
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-20-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-2 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 740.2GB (14.9% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 103G (48%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.0C mobo: 35.0C gpu: 36.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 555 fan-2: 486 fan-3: 1011 fan-4: 0 fan-5: 742
Info:      Processes: 497 Uptime: 50 min Memory: 2431.0/16053.6MB
           Client: Shell (bash) inxi: 2.3.56 
p-i@pi-MS-7A34:~$

```

I have disconnected all disks and change monitor cable from DP to DVI and I'm now able to access BIOS and boot to Ubuntu 18.04 from an USB device.
Have to think about the best way forward.

---

### Post by oldfred on 2018-06-07
CMOS reset reverts everything back to defaults.
I have a multiple item list that I have to go thru to reset after every UEFI update. 
With my newer UEFI system, it lists changes so it was easy to document. It also allows saving screenshots.
With my old BIOS system I had to use camera to take photos to see all the details.

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

---

### Post by P-I H on 2018-06-07
This computer had three disks a NVme, a SanDisk Ultra and a Samsung 850 EVO.
I was able to make a new 18.04 installation on the Samsung 850 EVO after removing the NVme disk  and change of the connection to the monitor from DP to HDMI.
The UEFI that's on the Ubuntu download iso for 18.04 works OK on my Tomahawk B350.
After sudo update-grub the system on the SanDisk Ultra is shown in Grub, but it will not boot. I think it's searching for the EFI System on the NVme disk.
I'm not sure, but I think these problems are related to an update of Grub last evening.

---

### Post by oldfred on 2018-06-07
Post this:
       lsblk  -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT 

Partlabel is GUID and is used by UEFI to know which partition to boot from.
Post this.
sudo efibootmgr -v

---

### Post by P-I H on 2018-06-08
When I boot the not working installation on sda, I get the doots and after some time an information and I'm also able to run
```
journalctl -p -err -b
```
Which gives the error message
```
Timed out waiting for device dev-disk-by\x2duuid-695E\x2d1EE9.device

```
This is from the running system, which now is 18.04.

```
p-i@pi-MS-7A34:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT 
NAME LABEL PARTLABEL        SIZE UUID                                 MOUNTPOINT
loop0
                            8,6M                                      /snap/comm
loop1
                            140M                                      /snap/gnom
loop2
                            3,3M                                      /snap/gnom
loop3
                           12,2M                                      /snap/gnom
loop4
                           86,6M                                      /snap/core
loop5
                             21M                                      /snap/gnom
loop6
                            1,6M                                      /snap/gnom
sda                       223,6G                                      
&#9500;&#9472;sda1
&#9474;          EFI System Partition
&#9474;                           512M DF06-B9B9                            
&#9492;&#9472;sda2
                          223,1G 527726c6-7d7b-4747-a720-5516b68ae81a 
sdb                       232,9G                                      
&#9500;&#9472;sdb1
&#9474;          EFI System Partition
&#9474;                           512M FD3B-74FA                            /boot/efi
&#9492;&#9472;sdb2
                          232,4G cb2d147a-f33f-47b3-9346-09b53e812c43 /
p-i@pi-MS-7A34:~$
```

```
p-i@pi-MS-7A34:~$ sudo efibootmgr -v
[sudo] password for p-i: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0005
Boot0000* ubuntu    HD(1,GPT,ef489757-04e8-4450-8fdf-32fa62688d3f,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0005* Hard Drive    BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0200)..GO..NO..........S.a.m.s.u.n.g. .S.S.D. .8.5.0. .E.V.O. .2.5.0.G.B...................\.,.@.r.d.=.X..........A.................................>..Gd-.;.A..MQ..L.2.S.6.R.B.N.H.0.2.C.0.9.3.7. .M. . . . ........BO..NO..........S.a.n.D.i.s.k. .U.l.t.r.a. .I.I. .2.4.0.G.B...................\.,.@.r.d.=.X..........A.................................>..Gd-.;.A..MQ..L.5.1.9.3.9.7.1.4.6.1.6.8. . . . . . . . ........BO
p-i@pi-MS-7A34:~$
```

These are the disks

---

### Post by oldfred on 2018-06-08
Sorry, not partlabel, but this:
       lsblk -o parttype,PARTUUID 
    
You must not label partitions, I prefer to label partitions.

Your UEFI entry is trying to boot from this partuuid:
ef489757-04e8-4450-8fdf-32fa62688d3f

Also then if able to get to command line:
cat /etc/fstab

It may be an entry in fstab is not valid and that is issue.

---

### Post by P-I H on 2018-06-08
Thanks, that is the case.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=527726c6-7d7b-4747-a720-5516b68ae81a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=659E-1EE9  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

```

I suppose I only have to remove that entry in fstab or do I have to enter a reference to the boot file on the Sandisk?

I changed the fstab and used the DF06-B9B9 UUID, which worked.

When I dual boot I normally I remove all disks except the one I use for the install. In this case I get the boot file on the right device and is able to change boot disk in bios. With a NVme disk you can't do that and the boot file will always be on the NVme disk. It should be better if it's possible to specify the boot disk during the installation.

---

### Post by oldfred on 2018-06-08
Since UUID for ESP  at /boot/efi is wrong, I think it is better to totally re-install grub.

Use Boot-Repair from Ubuntu live installer booted in UEFI mode and in Boot-Repair's advanced mode and choose your install & drive (not partition) for grub total install. Not just a grub update which just updates grub menu.

If that does not work, post new link to summary report from Boot-Repair.

---

### Post by P-I H on 2018-06-08
I will keep it as is for now. I will check out the proposed method on another system.

---

