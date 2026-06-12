---
title: "Minimal Installation in VM"
date: 2013-11-23
forum: Virtualisation
---

### Post by JKyleOKC on 2013-11-23
I spent much of yesterday attempting to create a minimal installation of Ubuntu in a virtualbox VM, for some testing purposes. I didn't anticipate any problem, having installed a dozen or more VMs with Win2K and WinXP systems, plus a few more with Debian and Xubuntu. I downloaded the minimal ISO file, created my empty VM with the default RAM size, 5 GB of disk storage, and the ISO file as the CD, set maximum CPU usage to 80%, and clicked "Start" to run it.

The CD loaded properly and gave me a menu with only a few choices; I selected "Install" and answered a few questions as it ran, until I got to the part where it told me it was downloading the installer. Then nothing more happened.

The host system (Xubuntu 12.04.3) includes the CPU Graph and Net Monitor panel applets, which allow me to keep an eye on activity at such times. CPU usage showed virtualbox taking 80%, but the net monitor showed only very sporadic bursts of activity there. After a full 10 minutes of this (as shown by the "top" line for vbox), I forced a power-off to the VM.

I tried again with the VM network adapter set to NAT (the original attempt was bridged, which is my usual setup of any VM so as to have full access to my SOHO LAN) with identical result. I then deleted the VM and its VDI file pending expert advice, so I can start over from scratch.

My questions are (1) should I allow more time for the installer download, and if so, how long? and (2) am I doing something wrong? My purpose is simply to set up a test-bed for trying some wild experiments...

EDIT: Jump to Post #9 for the solution!

---

### Post by DuckHook on 2013-11-23
Hi Jim,

Have you tried setting your network to bridged and choosing the virtio_net NIC? Every modern distro I'm aware of will sense this NIC and because it is paravirtualized, it should give the best throughput. Even with NAT configuration, this is the best virtual NIC. Another trick is to choose sshd on the initial install. In your case, this is not so much to hand over the install process itself to an ssh session as it is to run top, ifconfig, ping, nc, etc during the installation process to see what is holding things up.

Make sure I/O APIC is checked, EFI is not, and choose all accelerations (VT-x/AMD-V & Nested Paging). I also delete the IDE controller that is used by default, install a SATA controller and attach both VDI and CDROM to that. In the past I've found that IDE really slows everything down in comparison to SATA.

---

### Post by JKyleOKC on 2013-11-23
Thanks very much, DuckHook! Followed your instructions exactly and tried again, this time taking the default sizes for the VDI (8 GB) and RAM (512 MB). Same no-action result, so after 10 minutes I forced a power-down. Here's what I think is the pertinent portion of the log: ```
00:00:04.979638 Guest Log: BIOS: Booting from CD-ROM...
00:00:05.115438 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f97a4781000 w=640 h=480 bpp=24 cbLine=0x780, flags=0x1
00:00:13.834332 Guest Log: BIOS: KBD: unsupported int 16h function 03
00:00:13.834651 Guest Log: BIOS: AX=0305 BX=0000 CX=0000 DX=0000 
00:00:13.929669 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f97a4781000 w=800 h=600 bpp=16 cbLine=0x640, flags=0x1
00:00:14.446219 PIT: mode=2 count=0x12a5 (4773) - 249.98 Hz (ch=0)
00:00:14.875311 PIT: mode=0 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:15.056932 OHCI: Software reset
00:00:15.202159 AHCI#0: Reset the HBA
00:00:15.215541 AHCI#0: Port 0 reset
00:00:15.216498 EHCI: Hardware reset
00:00:15.216736 EHCI: Hardware reset
00:00:15.216828 EHCI: USB Operational
00:00:15.241445 OHCI: USB Reset
00:00:15.297035 OHCI: Software reset
00:00:15.297216 OHCI: USB Operational
00:00:16.093540 AHCI#0: Port 1 reset
00:00:18.564261 EHCI: USB Suspended
00:13:57.848934 Changing the VM state from 'RUNNING' to 'SUSPENDING'.
00:13:57.865457 AIOMgr: Endpoint for file '/home/jk/VirtualBox VMs/xxmini/xxmini.vdi' (flags 000c0781) created successfully
00:13:57.963871 PDMR3Suspend: 114 849 549 ns run time
00:13:57.963951 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.
00:14:03.808532 Console::powerDown(): A request to power off the VM has been issued (mMachineState=Stopping, InUninit=0)
00:14:03.814668 Changing the VM state from 'SUSPENDED' to 'POWERING_OFF'.

```If I'm reading this correctly, at 16 seconds after powering up, the mini.iso program reset the SATA controller's port 1, and 2.5 seconds later suspended USB for some reason -- then did nothing else until I forced the power-down by clicking the red X in the top right corner, with a fraction more than 10 minutes showing in the "top" display of the host. Obviously there's still something very wrong...

Could it be that I simply have a bad download of the minimal ISO file? Seems to be that if I did, it ought to bomb out while loading, rather than giving me the initial menu and the various configuration questions along the way. Do you have a URL for the minimal package that you use?

---

### Post by DuckHook on 2013-11-23
Ahhh... USB. Do you have Guest Additions loaded? If so, is it the OSE version or the proprietary one from Oracle's site? I always use the proprietary, after hearing reports that the absence of Guest Additions or the OSE version will sometimes cause problems. Since I have never worked with anything other than proprietary GA, I can't advise you much on the alternatives.

For now, try disabling USB on this VM for install. If that works, then enable but with USB 2.0 turned off. If that works, then turn USB 2.0 back on.

I simply used the mini.iso directly from Ubuntu found [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). I stick to 12.04, but don't see why the others wouldn't work. I should note that my minis are all cloned from an install done last year. Don't see how that can be relevant, but wanted you to know that mine isn't a recent install.

---

### Post by DuckHook on 2013-11-23
Jim,

Out of sheer curiosity, did an install of 13.10 into VBox 4.3.2 just now. I want a fresh install of the latest anyway, so this was no bother. Mine went off without a hitch. I'm trying to anticipate the difference between mine and yours and I can only cite the following:

- I am on Ubuntu 12.04.3. You are Xubuntu, same version. Cannot see how this could make any difference whatsoever.
- I only have 3 PPAs on my system, one of which is Oracle. This allows me to to install latest VBox which is currently 4.3.2
- Downloaded and installed Guest Additions from Oracle--also 4.3.2. VBox automatically checks for updates.
- Set VM to following: 2 cores, 2048MB RAM, PIIX3 Chipset, I/O APIC, UTC time, Enable PAE, All accelerations on, 32 MB VRAM, 1 Monitor, All drives SATA, Host I/O cache off, Pulse Audio-Intel HD, Bridged Adapter virtio-net, No serial port, Enabled USB 2.0 with New Filter 1, Shared *~/Public* folder.
- Optional (but useful)```
VBoxManage setextradata <name_of_VM> CustomVideoMode1 <example: 1200x1024x32 or your custom resolution>
```...this is useful later when you set the console to a much more usable resolution through GRUB with```
GRUB_GFXMODE=1200x1024x32
GRUB_GFXPAYLOAD_LINUX=keep
sudo update-grub
```
- Selected expert install on mini.iso
- Selected generic kernel
- Chose known reliable high-speed mirror instead of country default
- Selected only needed drivers instead of full install (for as minimal a system as possible)
- Selected OpenSSH-server as only "optional" package
- Everything else as per defaults

The installation took 15 minutes and went without a hitch. You may wish to choose a full set of modules rather than my only-needed-drivers to make sure you have all bases covered. Also, make sure your mirror is the same as the one already set for your Xubuntu host.

If this continues to balk you, please post results of:```
VBoxManage showvminfo "<name_of_your_VM>"
```Here's mine, sanitized of personal info, if it might prove useful:```
DuckHook@19th_hole:~$ VBoxManage showvminfo Console
Name:            Console
Groups:          /Linux
Guest OS:        Ubuntu (64 bit)
UUID:            xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
Config file:     /home/DuckHook/VirtualBox VMs/Linux/Console/Console.vbox
Snapshot folder: /home/DuckHook/VirtualBox VMs/Linux/Console/Snapshots
Log folder:      /home/DuckHook/VirtualBox VMs/Linux/Console/Logs
Hardware UUID:   xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
Memory size:     2048MB
Page Fusion:     off
VRAM size:       32MB
CPU exec cap:    100%
HPET:            off
Chipset:         piix3
Firmware:        BIOS
Number of CPUs:  2
PAE:             on
Long Mode:       on
Synthetic CPU:   off
CPUID overrides: None
Boot menu mode:  message and menu
Boot Device (1): HardDisk
Boot Device (2): DVD
Boot Device (3): Not Assigned
Boot Device (4): Not Assigned
ACPI:            on
IOAPIC:          on
Time offset:     0ms
RTC:             UTC
Hardw. virt.ext: on
Nested Paging:   on
Large Pages:     off
VT-x VPID:       on
VT-x unr. exec.: on
State:           powered off (since 2013-11-24T01:50:46.308000000)
Monitor count:   1
3D Acceleration: off
2D Video Acceleration: off
Teleporter Enabled: off
Teleporter Port: 0
Teleporter Address: 
Teleporter Password: 
Tracing Enabled: off
Allow Tracing to Access VM: off
Tracing Configuration: 
Autostart Enabled: off
Autostart Delay: 0
Default Frontend: 
Storage Controller Name (0):            SATA
Storage Controller Type (0):            IntelAhci
Storage Controller Instance Number (0): 0
Storage Controller Max Port Count (0):  30
Storage Controller Port Count (0):      2
Storage Controller Bootable (0):        on
SATA (0, 0): /home/DuckHook/VirtualBox VMs/Linux/Console/Console.vdi (UUID: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)
SATA (1, 0): Empty
NIC 1:           MAC: xxxxxxxxxxxx, Attachment: Bridged Interface 'eth0', Cable connected: on, Trace: off (file: none), Type: virtio, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
NIC 2:           disabled
NIC 3:           disabled
NIC 4:           disabled
NIC 5:           disabled
NIC 6:           disabled
NIC 7:           disabled
NIC 8:           disabled
Pointing Device: USB Tablet
Keyboard Device: PS/2 Keyboard
UART 1:          disabled
UART 2:          disabled
LPT 1:           disabled
LPT 2:           disabled
Audio:           enabled (Driver: PulseAudio, Controller: HDA)
Clipboard Mode:  Bidirectional
Drag'n'drop Mode: Bidirectional
VRDE:            disabled
USB:             enabled
EHCI:            enabled

USB Device Filters:

Index:            0
Active:           yes
Name:             New Filter 1
VendorId:         
ProductId:        
Revision:         
Manufacturer:     
Product:          
Remote:           
Serial Number:    

Available remote USB devices:

<none>

Currently Attached USB Devices:

<none>

Bandwidth groups:  <none>

Shared folders:  

Name: 'Public', Host path: '/home/DuckHook/Public' (machine mapping), writable

VRDE Connection:    not active
Clients so far:     0

Video capturing:    not active
Capture screens:    0
Capture file:       /home/DuckHook/VirtualBox VMs/Linux/Console/Console.webm
Capture dimensions: 1024x768
Capture rate:       512 kbps
Capture FPS:        25

Guest:

Configured memory balloon size:      0 MB
```

---

### Post by JKyleOKC on 2013-11-24
> **DuckHook said:**
> Ahhh... USB. Do you have Guest Additions loaded? If so, is it the OSE version or the proprietary one from Oracle's site?Can't load Guest Additions until there's an o/s in the VM in which they can install. My problem comes before that. I'm using vbox 4.2.18, from the Oracle site, with the propietary extension pack. I've gotten vbox from the Oracle site ever since my initial work with it back around the 3.1 version or so; switched over to there rather than the repository immediately after discovering that repository versions were not being updated to follow vbox.

I've spent the whole evening watching Big XII college football, so haven't continued the experiment. I'll pick it up tomorrow morning and follow your suggestion of completely disabling USB to see whether it makes any difference. Thanks much for all the details!

EDIT: Just compared my vminfo listing to yours and found several differences, but nothing that appears critical except one: I forgot to select Ubuntu 64-bit as the type, and simply have Ubuntu. I'll change that before the next attempt, and also make absolutely certain that the mini.iso file I'm using is also 64 bits; I'll grab a new copy from the link you gave, to make certain. The other major difference I found is that I'm using only one CPU, since my host is only dual-core and I've found that trying to use more than one CPU in a VM slows things down for me. This installation of vbox, by the way, is running a WinXP VM 24/7 to receive all my e-mail so I'm sure that vbox itself is working. The latest version is 4.3.2 but until they add it to the auto-update feature, I'm staying with 4.2.18; my initial trial of 4.3 made it impossible to load any of my VMs created back with vbox 3.2, since they failed to contain a serial number that it expected.

---

### Post by DuckHook on 2013-11-24
My bad. I meant Extensions. i.e. the stub that resides on the host and permits USB functionality. Guest *Additions* will not do you a whole lot on a minimal install anyway. I can only see it being useful for enabling the shared folder. Everything else on it is designed for X, which you won't have. I got confused because the procedure of downloading the *Extension* pack also inserts *Additions* into the VM directory for ready installation into VMs.

FWIW, I experienced no end of trouble with 4.2.18. It kept crashing my VMs and on a few occasions caused my host to freeze. After REISUB, syslog showed a sequential lockup of each CPU from the VBox driver, which is not only rogue behaviour but *very* worrisome. I haven't had a single problem since switching to 4.3.x. (NOTE: I miscalled it "3.4.2" above, now corrected--I'm not batting very well tonight). You may wish to upgrade to 4.3.2 which I think is not only stabler, but seems faster too.

College football is so much more pleasant than wrestling with cussed installs.

---

### Post by Bucky Ball on 2013-11-24
*Thread moved to **Virtualisation**.*

---

### Post by JKyleOKC on 2013-11-24
> **DuckHook said:**
> College football is so much more pleasant than wrestling with cussed installs.Agreed; however I got up this morning with renewed energy and tackled it anew. I followed your lead with choosing expert installation, and because I'm limiting CPU usage to 80%, decided to wait at least 20 minutes before forcing a power-down.

That led to success. At the "Configure network" stage, I discovered that using automatic configuration gave the wrong address for my LAN gateway (which is unconventional for historical reasons) and after using the correct address for gateway and DNS server, got reassuring blips of network activity. Finally after 17 minutes CPU time, the menu of installer additions appeared and from there things went quite smoothly although it took a total of 34 minutes CPU time before getting to the final reboot-into-new-system point.

I think the problem was entirely having a bad gateway address, but in the absence of any error message the mini.iso file simply churned in a large infinite loop. Thank you very much for all the suggestions. Now I should be able to experiment to my heart's content with a minimum system!

---

### Post by Bucky Ball on 2013-11-24
I hope you enjoy the minimal. I love it! Good luck.

Minimal install with xfce4 and only the apps I want/need. Computing heaven to me. I hate bloat which is one of the reasons I got into Ubuntu in the first place. After some research I realised I could get rid of a lot of it and customise to my heart's content. ;)

---

### Post by DuckHook on 2013-11-24
> **JKyleOKC said:**
> ...Ubuntu 64-bit as the type...64-bit should not be relevant. To my knowledge, all it does is set the defaults a certain way.> The other major difference I found is that I'm using only one CPU...I've installed with 1 CPU and the install works fine. Don't see how it would be a factor either. You may want to try switching to 2 CPU @ 100% just to install and then dialing back post-install.> my initial trial of 4.3 made it impossible to load any of my VMs created back with vbox 3.2, since they failed to contain a serial number that it expected.Breaking earlier VMs is unacceptable and I understand why it would deter you from upgrading. You may wish to have a look at [this]("http://www.virtualbox.org/manual/ch09.html#changedmi"). The relevant parts in your case would be:```
VBoxManage setextradata "VM name" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemSerial" "System Serial"
```...with "System Serial" being any string or integer you want, and```
VBoxManage setextradata "VM name" "VBoxInternal/Devices/pcbios/0/Config/DmiSystemUuid" "9852bf98-b83c-49db-a8de-182c42c7226b"
```...where I believe that "9852bf98-b83c-49db-a8de-182c42c7226b" can be replaced with a UUID of your choice provided it conforms to the hexadecimal template. If this doesn't work because the UUID must actually conform to some hidden algorithm, it is a simple matter to create a new empty VM, do a:```
VBoxManage showvminfo
```...on it, extract the UUID, delete the temporary VM, and insert the conforming UUID into your old VM. I suspect that you would then be able to run your 3.2 VMs on the latest releases.

A simple solution may be to just create a new VM with no VDI, set it up how you like it, and then just attach your old VDI to the new VM.

Another workaround that has worked for me as a last resort is to create a new VM complete with new empty VDI, attach your old VDI as a second disk and clone your contents to the new VDI using Clonezilla. It just doesn't seem as elegant as the first solution.

Needless to say for such an old Linux hound as you, but for others who may be reading, do none of the above until you have a full backup of the VMs and especially the VDIs you will be monkeying with.

On a related note, VBox does automatically upgrade, but with every release (let's designate them 4.x.y), x releases are considered major whereas y are minor. VBox will automatically recommend y releases (and download them if you have update manager set up that way) but not x releases. I had to manually remove 4.1.y before I could install 4.2.y, and had to do the same thing moving from 4.2.18 to 4.3.2. If you've installed the Oracle PPA and look in synaptic or even Software Center, you will find that 4.3.2 exists. The system just treats it as a separate program rather than as part of an upgrade set.

EDIT

Posted before reading your latest. However, some of my above observations might still be valuable to you especially with respect to updating your old VMs. Congrats and Happy Ubuntuing!

---

### Post by JKyleOKC on 2013-11-24
They definitely are valuable, and based on your recommendation I plan to try 4.3.2 on the system where the new minimal is installed. It has only one critical VM on it, and I can power that VM down while making the changeover (I normally save the state and restore it rather than powering down and back up again, when re-booting the host) to make certain that nothing gets damaged. I'll leave a test VM in saved state, too, so that I can verify the ability to restore after the upgrade to 4.3.

I do have the Oracle PPA installed on this host (not the same one we've been discussing) but still when I use vbox's own Help->Check for Updates feature, it keeps telling me I have the most recent version installed even though I'm still on 4.2.18. Very shortly after the introduction of 4.3.0, I followed a thread in Oracle's vbox forums in which one of the developers said they would not set 4.3 up for automatic update notification until they were satisfied it was meeting its objectives, so my belief is that they're still ironing out some of the regressions. However if 4.3.2 is now able to restore from saved state when the VM was created by older versions, it'll be worthwhile to get back up to the current revision.

The specific thing that I found broken was that any attempt to restore under 4.3 failed because of a missing or mismatched serial number. Wiping out the saved state allowed the VM to load, but then saving the state again and attempting to restore still got the same error. That thread on the vbox forum indicated that the problem was due to the VM having been created by an older version, and also that it was being treated as a very low priority.

One thing I've tried in the past, when a VM has become unusable for any reason, is to create a new VM with all the same attributes, and then assign the VDIs from the original VM to the new one. I've even had two separate VMs with the same VDIs attached to each, and it worked so long as I never tried to have both active at the same time. I may try that on the new round of 4.3.2 testing, if the restore problem is still present -- create a new VM under 4.3.2, and give it the virtual disks of the older one! Will keep you posted on results...

---

### Post by DuckHook on 2013-11-24
> **JKyleOKC said:**
> ...Will keep you posted on results...And also feel free to PM me on any cool new minimalist command-line discoveries. I'm always interested in those. \\:D/

---

### Post by JKyleOKC on 2013-11-25
Just to wrap up a loose end: I've replaced my 4.2.18 vbox on this machine with 4.3.2 and am happy to report that the problem with restoring saved state appears to be fixed and everything is running as expected. Next, I'll do the same replacement on the other box where my dozen or so production VMs reside. Thanks again for nudging me into re-testing. I prefer to keep everything up to date but was waiting for some confirmation that 4.3 was actually ready for prime time!

---

