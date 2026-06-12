---
title: "Proper way to Add VBox in 22.04"
date: 2024-05-01
forum: Virtualisation
---

### Post by Rick St. George on 2024-05-01
What is the proper way to install VirtualBox in Ubuntu 22.04 ???

Previously, after Fresh install of 22.04 on new SSD, after all updates, installed Synaptic and found VirtualBox selecting install.
After next boot screen filled up with continous Error messages. Managed to write down the Error, screen fills up with ...

"UBSAN: array index out of bounds in /var/lib/dkms/virtualbox 6.1.50/build/vboxdrv/SUPDrvGip"

Had to Re-install the OS. Now need to Add VirtualBox back in because I use it for my Trading Software which runs on Windows ONLY.

Any Help would be appreciated. Thanks!

---

### Post by ajgreeny on 2024-05-01
I would suggest that you download and install Virtualbox directly from the downloads available at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) then enable their repos using the info shown in the section on  **Debian-based Linux distributions**.
That will make sure that your Virtualbox version is kept updated automatically along with all other packages in Ubuntu.

I no longer use Virtualbox having moved over to KVM/QEMU a long time ago which in my opinion is much better if using a Linux host OS.
I would therefore recommend that you try it yourself, easily done by installing the virt-manager package which will automatically pull in everything else needed to use KVM/QEMU

See [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) and [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) for more details.

---

### Post by Rick St. George on 2024-05-01
Is Ubuntu / UbuntuStudio v22.04 considered a mixed installation being made on an AMD64 kernel with 32 bit packages? 
If so, the VirtualBox page above says ii is not supported, and would need to setup a 64-bit chroot environment (whatever that means).

My Vbox data is extensive, with Trading Software etc. 60 GB on separate Drive. Can not Install all over again, and don't have time to learn new Software (KVM/QEMU). I can't make another mistake.

Followed your advice to download the DEB file from VirtualBox website, but had to follow these instructions [https://gcore.com/learning/how-to-install-virtualbox-on-ubuntu/]("https://gcore.com/learning/how-to-install-virtualbox-on-ubuntu/") to add ppa and keys. Now up and running in no time, after adding my appliance (via its own folder). 

Thanks!

---

### Post by Rick St. George on 2024-05-19
> **ajgreeny said:**
> 
I would therefore recommend that you try it yourself, easily done by installing the virt-manager package which will automatically pull in everything else needed to use KVM/QEMU


Question: Since my Data is extensive within my VM Appliance, is there a way to transfer or export it into KVM?

I may try it since I believe I need to Delete/Remove Vbox as my computer is having trouble booting (black screen)  [See Here]("https://ubuntuforums.org/showthread.php?t=2497470").

Thanks!

---

### Post by Claus7 on 2024-05-19
Hello,

I do not know about the transfer you are asking about, yet the errors you are facing during boot have to do with kernel-virtualbox issues, that I have come across as well and which haven't affected my booting experience, except seeing the error messages for a little while. I think that you might have to look elsewhere for your booting problem.

Regards!

---

### Post by Rick St. George on 2024-05-19
Found the following via AI.

kernel-virtualbox issues in Ubuntu v22.04

The kernel-virtualbox issue in Ubuntu v22.04 seems to be related to the VirtualBox kernel driver not being installed or set up correctly. 
Here are some possible solutions:

1. Run the following command as root to set up the VirtualBox kernel driver again.

```

sudo /sbin/vboxconfig

```

2. If your system has EFI Secure Boot enabled, you may need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before loading them. You can do this by following your Linux system&#8217;s documentation for more information.

To troubleshoot the issue, you can try the following steps:

1. Check if the VirtualBox kernel driver is installed by running the command 
```

lsmod | grep vbox

```

If the driver is not installed, you can install it by running the command 
```

sudo apt-get install virtualbox

```

2. Check if the kernel modules are signed by running the command 
```

lsmod | grep vbox | xargs modinfo

```

If the modules are not signed, you can sign them by running the command 
```

sudo sign-kernel-module vboxdrv vboxnetflt vboxnetadp vboxpci

```

Note: this would not work for me (sign-kernel-module: command not found)

3. Try to load the VirtualBox kernel driver by running the command 

```

sudo modprobe vboxdrv

```

I have tried these, and will Shutdown and ReStart to see what happens, and report back.

---

### Post by currentshaft on 2024-05-20
no

---

### Post by Rick St. George on 2024-05-20
VirtualBox running now, but had to also install "Guest Additions".

Will Research alternative to VirtualBox and hope I can Clone / Transfer / Export Appliance or whatever its called, to be able to IMPORT it into the next Virtual program!  Any idea what that would be called?

---

### Post by MAFoElffen on 2024-05-20
> **Rick St. George said:**
> Question: Since my Data is extensive within my VM Appliance, is there a way to transfer or export it into KVM?

I may try it since I believe I need to Delete/Remove Vbox as my computer is having trouble booting (black screen)  [See Here]("https://ubuntuforums.org/showthread.php?t=2497470").

Thanks!
Lots of times, vendors will give out vDisks, of their OS. or others with applications. Some of them (like Windows VM's are time-bombed. I convert vDisk formats often. Many Vagrant formatted disks out there... 

A virtual disk (vDisk), is just a file. Files can be copied very easily... You say you don't want to lose what you had ---> have you made a copy of that yet for the just-in-cases? You know that convert usually creates a new file, not overwriting the old, right?

So you saying you have complicated data and don't want to lose it... Doesn't really hold water. Because you don't have to lose anything at all. You can just work on the copy of what you had. It can stay there (safe) in it's original form. 

Although VBox supports many vDisk formats, the default format for a VirtualBox vDisk is .vdi...  Two of the most popular vDisk formats for KVM is qcow2 & raw... Everyone seems to use vmdk files for demo's...

Say if you wanted to covert that from within VBox:
```

vboxmanage clonemedium noble-desktop-24.04.vdi noble-desktop-24.04.img --format raw

```
If you further wanted to convert to qcow2
```

qemu-img convert -f raw noble-desktop-24.04.img -O qcow2 noble-desktop-24.04.qcow2

```
That is what the VBox world will tell you to do... What they do not understand, that these also work without VBox. Not documented, but works if you think of it in the qemu-img man page, under convert > formats, as "other"
```

qemu-img convert noble-desktop-24.04.vdi -O raw noble-desktop-24.04.img  
qemu-img convert noble-desktop-24.04.vdi -O qcow2 noble-desktop-24.04.qcow2

```   
In KVM Virtual Machine manager > New > Import Existing Image >> Create the machine, using the vDisk file as the storage file.

Easy Peasy.

Not saying you must try this. Nor that this is what you 'should do'. Just saying you have more options than you seem to think you have. Nothing said as a cut or anything. Just making you aware... I want to help you with  that. Even if you do not try KVM, and  stay with VBox. Make a copy of what you don't want to lose. That just makes sense.

---

### Post by Rick St. George on 2024-05-21
> **MAFoElffen said:**
> 

That is what the VBox world will tell you to do... What they do not understand, that these also work without VBox. Not documented, but works if you think of it in the qemu-img man page, under convert > formats, as "other"
```

qemu-img convert noble-desktop-24.04.vdi -O raw noble-desktop-24.04.img  
qemu-img convert noble-desktop-24.04.vdi -O qcow2 noble-desktop-24.04.qcow2

```   

In KVM Virtual Machine manager > New > Import Existing Image >> Create the machine, using the vDisk file as the storage file.


If I understand you correctly ... "noble-desktop-24.04.vdi" is the  Virtual Disk name from VirtualBox, and using the code above will convert to QEMU Format - Yes?  But I get this ;

```

ms7640:/media/VirtualBox VMs$ qemu-img convert VirtualDisk-TradeSoft.vdi -o qcow2 VirtualDisk-Tradesoft.qcow2
qemu-img: Invalid parameter 'qcow2'

ms7640:/media/VirtualBox VMs$ qemu-img convert VirtualDisk-TradeSoft.vdi -o raw VirtualDisk-Tradesoft.img
qemu-img: Invalid parameter 'raw'

ms7640:/media/VirtualBox VMs$ qemu-img convert VirtualDisk-TradeSoft.vdi -o VirtualDisk-Tradesoft.img
qemu-img: Must specify image file name


```

When attempting use the ".vdi" file, I get this;

```

Unable to complete install: 'internal error: process exited while connecting to monitor: 2024-05-21T20:45:06.205521Z qemu-system-x86_64: -blockdev bla bla bla

ms7640:/media/VirtualBox VMs$ qemu-img convert VirtualDisk-TradeSoft.vdi -o qcow2 VirtualDisk-Tradesoft.qcow2
qemu-img: Invalid parameter 'qcow2'
qemu-img: Invalid parameter 'qcow2'
Command 'qemu-img:' not found, did you mean:
  command 'qemu-img' from deb qemu-utils (1:6.2+dfsg-2ubuntu6.15)
Try: sudo apt install <deb name>

ms7640:/media/VirtualBox VMs$ sudo apt install qemu-utils
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
qemu-utils is already the newest version (1:6.2+dfsg-2ubuntu6.19).
qemu-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


What am I doing wrong ? ? ?
Thanks!

---

### Post by bobunderwood99 on 2024-05-21
Use upper-case "O" rather than lower-case "o".

```
 ms7640:/media/VirtualBox VMs$ qemu-img convert VirtualDisk-TradeSoft.vdi -[COLOR=#ff0000]O[/COLOR] qcow2 VirtualDisk-Tradesoft.qcow2
```

---

### Post by Rick St. George on 2024-05-21
> **bobunderwood99 said:**
> Use upper-case "O" rather than lower-case "o".

```
 ms7640:/media/VirtualBox VMs$ qemu-img convert VirtualDisk-TradeSoft.vdi -[COLOR=#ff0000]O[/COLOR] qcow2 VirtualDisk-Tradesoft.qcow2
```

Thanks Bo, that seemed to work. But still can't create/pull in the ---.qcow2. Get this Error;

> 
Unable to complete install: Cannot access storage file '/media/VBox/VirtualBox-VMs/VirtualDisk-TradeSoft.qcow2'
(as UID: 64055, gid:109): Permission Denied


Followed the [Steps Here]("https://help.ubuntu.com/community/KVM/Installation") I'm almost there! 

FYI:
```

~$ inxi -Fzx
System:
  Kernel: 6.5.0-35-lowlatency x86_64 bits: 64 compiler: N/A
    Desktop: KDE Plasma 5.24.7 Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: MSI model: 990FXA-GD65 (MS-7640) v: 3.0
    serial: <superuser required> UEFI: American Megatrends v: 20.3
    date: 09/26/2013
CPU:
  Info: 8-core model: AMD FX-8320 bits: 64 type: MT MCP arch: Piledriver
    rev: 0 cache: L1: 384 KiB L2: 8 MiB L3: 8 MiB
  Speed (MHz): avg: 1984 high: 3500 min/max: 1400/3500 boost: enabled
    cores: 1: 1400 2: 1400 3: 3500 4: 1400 5: 1400 6: 1400 7: 2300 8: 3076
    bogomips: 56007
  Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: NVIDIA GF119 [GeForce GT 610] vendor: ASUSTeK driver: N/A
    bus-ID: 03:00.0
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: nouveau,vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 1024x768~76Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
Audio:
  Device-1: AMD SBx00 Azalia vendor: Micro-Star MSI driver: snd_hda_intel
    v: kernel bus-ID: 00:14.2
  Device-2: NVIDIA GF119 HDMI Audio vendor: ASUSTeK driver: snd_hda_intel
    v: kernel bus-ID: 03:00.1
  Sound Server-1: ALSA v: k6.5.0-35-lowlatency running: yes
  Sound Server-2: JACK v: 1.9.20 running: no
  Sound Server-3: PulseAudio v: 15.99.1 running: yes
  Sound Server-4: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Micro-Star MSI driver: r8169 v: kernel port: e000 bus-ID: 01:00.0
  IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: virbr0 state: down mac: <filter>
Drives:
  Local Storage: total: 931.51 GiB used: 406.78 GiB (43.7%)
  ID-1: /dev/sda vendor: Western Digital model: WD Blue SA510 2.5 1000GB
    size: 931.51 GiB
Partition:
  ID-1: / size: 287.31 GiB used: 153.76 GiB (53.5%) fs: ext4 dev: /dev/sda1
  ID-2: /boot/efi size: 499 MiB used: 7.6 MiB (1.5%) fs: vfat
    dev: /dev/sda3
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 32.6 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 263 Uptime: 3h 51m Memory: 15.5 GiB used: 1.43 GiB (9.2%)
  Init: systemd runlevel: 5 Compilers: gcc: 12.3.0 Packages: 3078
  Shell: Bash v: 5.1.16 inxi: 3.3.13

```

Sooo - What am I missing Now???  Thanks!

---

### Post by bobunderwood99 on 2024-05-22
The instructions from that site are obsolete. If you install virt-manager it will pull in the required dependencies.

---

### Post by Rick St. George on 2024-05-23
> **bobunderwood99 said:**
> The instructions from that site are obsolete. If you install virt-manager it will pull in the required dependencies.

 I did install Virtual Machine Manager. Perhaps I'm not pulling it in right? Why does it ask (required to proceed) what OS the VDI/qcow2 file is?
Here are my Steps (with Virtual Machine Manager);

1. Click the + to add New Virtual Machine
2. Select "Import Existing Disk Image"
3. Provide Storage Path and Operating System of VM
4. Receive Warning: "Emulator may not have search permission to for that path", check box: Do you want to correct this?  YES
5. Errors were encountered changing permissions. Very likely VM will fail to start.
6. VM Fails to Start. 

I have a 2nd HDD with Vbox Appliance thereon. That's where I did the conversion to qcow2 format. When opening up Dolphin, and attempting to mount that partition, I see -> "An error occurred while accessing 'Home', the system responded: The requested operation has failed: Error mounting /dev/sdb1 at /media/stephen/VBox: Unknown error when mounting /dev/sdb1".

That's why I previously moved the created file to another partition on my SSD where UbuntuStudio v22.04 is running (in another partition). 
So its no wonder the Error Msg responds with UID warning. I have 2 partitions on that No. 2 HDD and only the partition labelled VBOX will not mount. Strange. So I'm stumped !?!

---

### Post by bobunderwood99 on 2024-05-23
Copy the qcow file to your home directory in UbuntuStudio and try again.

---

### Post by Rick St. George on 2024-05-24
> **bobunderwood99 said:**
> Copy the qcow file to your home directory in UbuntuStudio and try again.

Looks like it was attempting to Start, then Windows Blue Screen of Death.
Closed Virt-Mgr, Reopened, Clicked Power On ... its shows running but no Window to the Virtual Machine. Red Stop button won't shut down.
Had Click File / Close and whole Virt-Mgr window closes. Unbelievable! I'm having so much trouble. A new day, computer stills shows my #2 Drive with Partition for VMs not able to mount. 2nd partition with storage - no problem. 

Note: I have not yet Removed VirtualBox. Upon Boot-up, I see messages scrolling about the VirtualBox directory, but around 5.--- after Plymouth Boot Screen Terminated, the Login Screen shows, I have to immediately hit the Num Locks key - or Black Screen.  When I shut down, those  scrolling lines are still showing and running up into the 1000's. I can't wait to Uninstall  VirtualBox - but not without Virt-Mgr working and pulling in the qcow2 appliance.

This is the 2nd Clean Install of UbuntuStudio v22.04. I have a newer GPU coming AMD Radeon 580 today. Will be able to Remove Nvidia 390 drivers for an older GPU that is causing problems, only 1 out of 2 monitors showing, and only at 1024X768, but is capable of 1920x1080.

Any more ideas about this qcow2 file and Virt-Mgr?

---

### Post by bobunderwood99 on 2024-05-24
Open Virtual Machine Manager
Select the desired VM
Click the Open button (opens the VMM console window)
Click the Play button in the console window - tooltip: "Power on the virtual machine"

What version of Windows is in the VM?

---

### Post by Rick St. George on 2024-05-25
I received my new GPU, after hardware install ... did a Fresh Install of UbuntuStudio v22.04. Both Monitors now working.
Installed virt-manager via MUON Pkg Mgr, virt-manager will not Run. Have to open terminal and do;
```

sudo virt-manager

```

Selected the qcow2 file, and Blue Screen shows when WinXP attempts to start with Stop: 0x000007B. Even Safe Mode won't work.
Maybe it got corrupted and should try the conversion process again? So did so ... same thing!
I realize this now has nothing to do with the Heading of this Thread.  Should I start another one? Or continue ???

---

### Post by bobunderwood99 on 2024-05-25
Yes, start a new thread.

---

### Post by Rick St. George on 2024-05-25
> **bobunderwood99 said:**
> Yes, start a new thread.

ENDING this Thread as Solved, Due to ... giving up on VirtualBox by Oracle as it messed up my UbuntuStudio v22.04 install.

Thanks to all who helped! 
YOU  Rock ! ! ! 
:guitar:

---

### Post by MAFoElffen on 2024-05-27
This morning I had installed Oracle VBox in a KVM virt nested Ubuntu 22.04 VM...

Because the current kernel is 6.5 in the 22.04 HWE stack, the VBox kernel modules will fail to build unless you install gcc-12 & g++-12. Then the modules will build fine.

To build the vbox drivers, the version of the gcc compiler needs to be the same version as what the Kernel was compiled with, just liek nVidia drivers.

---

