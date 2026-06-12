---
title: "Daily ISO"
date: 2018-11-25
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-11-25
I installed a daily ISO, as the third system, on my main computer. The installation went OK. However the installation of Grub is always a problem. I most often disconnect all disks except the installation disk, but that is a little bit complicated with a NVMe M.2 disk installed below the GPU. On my system Grub as default is installed on this disk. Should be nice with a feature to select the Grub installation disk. This is also a problem when you install on an USB stick.
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.18.0-11-generic x86_64 bits: 64 Desktop: Gnome 3.30.1 Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <root required> 
           UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1377 MHz min/max: 1550/3000 MHz Core speeds (MHz): 1: 1376 2: 1378 3: 1377 4: 1375 5: 1376 6: 1377 7: 1374 
           8: 1376 9: 1377 10: 1377 11: 1503 12: 1404 13: 1391 14: 1375 15: 1375 16: 1377 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X] driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.3 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.26.0 4.18.0-11-generic LLVM 7.0.0) v: 4.5 Mesa 18.2.2 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580] driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k4.18.0-11-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full 
Drives:    Local Storage: total: 689.34 GiB used: 6.92 GiB (1.0%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition: ID-1: / size: 218.57 GiB used: 6.91 GiB (3.2%) fs: ext4 dev: /dev/sdb2 
Sensors:   System Temperatures: cpu: 32.1 C mobo: N/A gpu: amdgpu temp: 40 C 
           Fan Speeds (RPM): N/A gpu: amdgpu fan: 1161 
Info:      Processes: 358 Uptime: 3m Memory: 15.68 GiB used: 1.23 GiB (7.8%) Shell: bash inxi: 3.0.27 
p-i@pi-MS-7A34:~$ 

```

---

### Post by cariboo on 2018-11-25
If you use the Something else option, you can choose where to install grub.

---

### Post by oldfred on 2018-11-25
I have yet to get Ubuntu's grub to install anywhere other than sda. It is smart enough to use first NVMe drive, but otherwise always installs to sda.
With my 19.04 install, I used combo box to change to sdb, I clicked on sda's ESP and said do not use, I clicked on sdb's ESP and said to mount as ESP. And it overwrote my /EFI/Ubuntu folder in the ESP on sda.

Bug from 2014, I just added new comment
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Several years ago I installed Fedora just to see difference in grub. It installed to sdb. But it embedded the drive info into its .efi file, nothing like the /EFI/ubuntu/grub.cfg that you can relatively easily edit back to install you want as default.

I quickly learned to backup ESP.
But now I normally just go back into /EFI/ubuntu/grub.cfg and edit to UUID & drive, partition of my main working install.

      ```
 fred@Bionic-Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid c29fc361-ea05-420b-b919-850aeef65dd4 root hd0,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 


```

---

### Post by mc4man on 2018-12-01
grub installs fine here to sdb when told to..

---

### Post by oldfred on 2018-12-01
@mc4man
Is that using UEFI or BIOS/CSM?
Never had an issue with BIOS, but UEFI has not worked on two of my systems, only installs to sda's ESP.

---

### Post by mc4man on 2018-12-02
> **oldfred said:**
> @mc4man
Is that using UEFI or BIOS/CSM?
Never had an issue with BIOS, but UEFI has not worked on two of my systems, only installs to sda's ESP.

UEFI, see screen, the _dropdown_ (- the highlighted orange would not be where I would of installed Ubuntu, just happened to be highlighted...
Ot - what a pain & semi-useless Ubuntu has now made live sessions. The ubuntu user can't access other volumes, removable media, nothing. Made copying  that screenshot more difficult than it should of been.

Edit: maybe comparing oranges to apples as I have the EFI partion created on sdb.. screen 2

---

### Post by oldfred on 2018-12-02
Yours seems to be one of the many systems (including mine ) that promote the USB flash drive to first or sda). Then install is installing to sdb.
Have seen some users where grub installed to flash drive, overwriting flash drive and then they had issues booting live installer again.
Not sure how grub really works, but just seen a lot of installs and results from those.

I have flash drive as sda, SSD as sdb & then HDD as sdc in some installs. And then I want grub installed to sdc.
I do not install from flash drives, usually. I allocate a partition on every drive for ISOs and boot them from grub to install to other drive.

---

### Post by mc4man on 2018-12-02
> **oldfred said:**
> Yours seems to be one of the many systems (including mine ) that promote the USB flash drive to first or sda). Then install is installing to sdb.
Have seen some users where grub installed to flash drive, overwriting flash drive and then they had issues booting live installer again.
Not sure how grub really works, but just seen a lot of installs and results from those.

I have flash drive as sda, SSD as sdb & then HDD as sdc in some installs. And then I want grub installed to sdc.
I do not install from flash drives, usually. I allocate a partition on every drive for ISOs and boot them from grub to install to other drive.

Actually sda is one of those internal ssd's that lenovo included on their laptops for Windows caching (this machine has a 24GB, my other a 32GB ssd.
By default the installer wants to install the bootloader there (sda), I always have to change that.
(atm they are just unallocated space drives, guess I could find some use for them but never bothered..

---

