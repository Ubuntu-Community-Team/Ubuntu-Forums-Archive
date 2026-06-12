---
title: "Ubuntu and W10 in a triple boot system"
date: 2020-03-16
forum: Ubuntu, Linux and OS Chat
---

### Post by P-I H on 2020-03-16
I bought a W10 pro license to use on my main computer in a triple boot with Ubuntu 19.10, Ubuntu 20.04 and W10.
When I started the computer had Ubuntu 19.10 installed on a 500 GB NVme disk, Ubuntu 20.04 installed on a 250 GB NVme and an unformatted 250 GB ssd.
The plan was to keep the Ubuntu versions on NVme and install W10 on the ssd.
However this didn't work. My conclusion is that it's impossible to install W10 on a ssd, with other OS:s on NVme.
In the end I had to sacrifice the Ubuntu 20.04 installation on the 250GB Nvme, install W10 on this disk and install Ubuntu 20.04 on the ssd.


Tried a lot of methods to install W10 on the SSD
- created an installation USB with the Media Creation Tool
- created an installation USB with Rufus
- created a partion with installation files on the ssd
- used the ssd unformatted
- formatted the ssd with Gparted
- formatted the ssd with DiskPart and learnt to start the PowerShell terminal with SHIFT+F10 during the installation
Got a lot of error messages
- Driver not found
- Windows could not prepare the computer to boot into the next phase of installation
- We couldn't create a new partition or locate an existing one. For mor information see the Setup log files
- W10 error code 0xC0000005
- Windows installer encountered an unexpected error
- Verify that the installation sources are accessible and restart the installation
The most strange was the error message about "Driver not found", when I tried to install from the ssd. To fix this I had to have an USB stick installed in a USB 2.0 port even though it wasn't used.

---

### Post by oldfred on 2020-03-16
Did you try turning off the NVMe drives in UEFI drive settings?
Windows installs normally to the drive set as default in UEFI/BIOS, not sure how that is seen or set with UEFI. With BIOS we have seen users have Windows boot partition on one drive and c: drive on another drive.

Not sure if installer works directly with AHCI or not. Most installs now use Intel RST, and we have to have users change to AHCI, but have to add AHCI drivers first.

---

### Post by P-I H on 2020-03-16
Yes I tried to turn off the NVme drives as I expected this to be the problem. However I didn't find any setting in my Asus BIOS. Last time I removed a NVme drive I lost the screw.
One other problem might have been that I'm using lvm on Ubuntu 19.10 installed on the 500 GB Nvme disk
The installation of W10 on the 250GB NVme disk went OK, but I saw a message from the W10 installer about a repaired disk. All boot files, Ubuntu 19.10, Ubuntu 20.04 and W10, are stored the 500 GB NVme disk. The grub menu was built OK during the installation of Ubuntu 20.04 and boot to the three systems works as expected. 
```
p-i@pi-Asus-B450-F:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                FSTYPE        SIZE MOUNTPOINT                   LABEL
loop0               squashfs     91,4M /snap/core/8689              
loop1               squashfs     54,7M /snap/core18/1668            
loop2               squashfs     47,7M /snap/snap-store/295         
loop3               squashfs     44,9M /snap/gtk-common-themes/1440 
loop4               squashfs    163,7M /snap/spotify/41             
loop5               squashfs    221,4M /snap/gnome-3-34-1804/18     
sda                             232,9G                              
&#9500;&#9472;sda1              vfat          512M                              
&#9492;&#9472;sda2              ext4        232,4G /                            
sr0                              1024M                              
nvme0n1                         447,1G                              
&#9500;&#9472;nvme0n1p1         vfat          512M /boot/efi                    
&#9492;&#9472;nvme0n1p2         LVM2_member 446,6G                              
  &#9500;&#9472;vgubuntu-root   ext4        445,7G                              
  &#9492;&#9472;vgubuntu-swap_1 swap          980M                              
nvme1n1                         232,9G                              
&#9500;&#9472;nvme1n1p1                        16M                              
&#9492;&#9472;nvme1n1p2         ntfs        232,9G                              
p-i@pi-Asus-B450-F:~$ 

```

---

### Post by oldfred on 2020-03-16
See this:
[https://ubuntuforums.org/showthread.php?t=2438669&p=13939259#post13939259](https://ubuntuforums.org/showthread.php?t=2438669&p=13939259#post13939259)

From Above.
See this example from my Asus Z97
Screenshot # 3. Advanced mode, Storage configuration, can set to disabled
[https://ubuntuforums.org/showthread.php?t=2258575&p=13196664#post13196664](https://ubuntuforums.org/showthread.php?t=2258575&p=13196664#post13196664)

I know my Gigabyte Z170 also has similar disabled setting per manual, but do not have a screenshot.
[https://ubuntuforums.org/showthread.php?t=2258575&page=2](https://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by P-I H on 2020-03-16
Thanks for the information, but these settings are not available on my motherboard. According to the manual it should be, but it isn't.
The Samsung 960 EVO disk is also missing in the lists of SSD:s. There is a more recent BIOS Version 3003, that might fix these problems. However everything is working and I will not risk a BIOS upgrade.
```
p-i@pi-Asus-B450-F:~$ inxi -Fz
System:    Kernel: 5.4.0-14-generic x86_64 bits: 64 Desktop: Gnome 3.35.91 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> 
           UEFI: American Megatrends v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1375 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1375 2: 1375 3: 1375 4: 1375 5: 1368 6: 1451 
           7: 1362 8: 1369 9: 1375 10: 1375 11: 1362 12: 1650 13: 1359 14: 1360 15: 1375 16: 1374 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] 
           driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.7 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD NAVI10 (DRM 3.35.0 5.4.0-14-generic LLVM 9.0.1) v: 4.6 Mesa 20.0.0 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-14-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 680.02 GiB used: 8.58 GiB (1.3%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 227.74 GiB used: 8.54 GiB (3.8%) fs: ext4 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 33.4 C mobo: 35.0 C gpu: amdgpu temp: 46 C 
           Fan Speeds (RPM): cpu: 536 case-1: 906 case-2: 830 case-3: 478 gpu: amdgpu fan: 0 
Info:      Processes: 346 Uptime: 21m Memory: 15.56 GiB used: 1.46 GiB (9.3%) Shell: bash inxi: 3.0.38 
p-i@pi-Asus-B450-F:~$
```

---

### Post by oldfred on 2020-03-16
I was able to download a Samsung ISO to update firmware.
It just had a minimal screen more like old DOS and download was just for my model.
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

sudo nvme list

Also they announced that it should be directly updateable.
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start)
[https://www.phoronix.com/scan.php?page=news_item&px=Google-Require-Chromebook-Fwupd](https://www.phoronix.com/scan.php?page=news_item&px=Google-Require-Chromebook-Fwupd)

---

