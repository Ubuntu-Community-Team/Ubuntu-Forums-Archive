---
title: "Virtualbox 1.6.2 Released"
date: 2008-06-06
forum: Virtualisation
---

### Post by Hershey on 2008-06-06
VirtualBox 1.6.2 (released 2008-06-06)

This is a maintenance release. The following items were fixed and/or added:

    * GUI: fixed a bug which prevented to add more than one SATA drive from the GUI
    * GUI: fixed a regression introduced in 1.6.0: the fullscreen mode was left on every guest video mode switch
    * GUI: fixed several minor issues
    * Networking: fixed a host interface networking regression introduced in 1.6.0
    * VMM: fixed starting of VMs with AMD-V enabled
    * VMM: massive performance enhancements for AMD-V
    * VMM: stability improvements for AMD-V on Windows hosts
    * VMM: correctly detect AMD CPUs with erratum 170 (AMD-V)
    * VMM: detect inconsistent timestamp counters on certain AMD Phenom CPUs (Windows host only)
    * VMM: fixed KVM check (Linux hosts only) XPCOM: fixed several races
    * VMM: &#64257;xed a regression introduced in 1.6.0: Windows stuck during installation
    * SATA: improved performance with Vista guests
    * SATA: fixed statistics counter
    * Shared Folders: several fixes (iTunes download, speed up browsing)
    * ATA/IDE: fixed boot from CDROM if a medium was added while the boot menu was active
    * Networking: provide an Intel PRO/1000 T Server (82543GC) network device emulation which is recognized by Windows XP guests
    * Networking: fixes for the E1000 emulation (don't crash if not attached, fixed a bug in the statistics counter implementation)
    * NAT: don't crash if the guest sent a DHCPRELEASE message with an invalid IP address
    * NAT: fixed ARP reply for the NAT gateway and for the NAT name server if the guest IP range was changed
    * Internal Networking: fixed shutdown if more than two VMs are connected to the same network
    * BIOS: allow to change the DMI informatiton (see chapter 9.13, Con'guring the BIOS DMI information, page 125)
    * RTC: fixed UIP emulation to prevent jumping of time in Solaris guests
    * Windows host: VirtualBox installation directory corrected for 64 bits Windows
    * Windows host: fixed VBoxVRDP.exe symlink
    * Windows host: solved locking problems in raw partition VMDK support
    * Windows host: fixed stability during high system load (page fault in KeQueryActiveProcessors)
    * MacOS X host: fixed crashes under certain conditions
    * Shared Folders: limited users without admin rights now also can use Shared Folders on Windows guests
    * Linux hosts: fixed default runlevel for the kernel module helper script
    * Solaris hosts: enabled support for VT-x and AMD-V
    * Solaris hosts: dynamic loading of libdlpi fixes a problem where Solaris 10 was not able to start a VM
    * Linux additions: fixed runlevels for kernel module helper scripts
    * Linux additions: compatibility fixes with Linux 2.6.26
    * Linux additions: fixed occasional guest kernel crash during unload of the vboxadd guest kernel module 

[Download]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

### Post by Sand Lee on 2008-06-07
> * BIOS: allow to change the DMI informatiton (see chapter 9.13, Con'guring the BIOS DMI information, page 125)

I worked with a developer on this feature to try and stop Windows from reactivating in this tutorial, [Boot an existing XP (Physical HD) install with VirtualBox]("http://ubuntuforums.org/showthread.php?t=769883"). However, last time I checked w/ Vbox SVN it did not work. I will check again with the 1.6.2 release, but does anyone know exactly what Windows checks for in OEM PC's?

---

### Post by digerati on 2008-06-07
Any idea when this will be available in the supported repositories?  Correct me if I'm wrong but I believe this should be in the main repositories.

---

### Post by mixmatch on 2008-06-07
The AMD64 package is incorrectly identified as "Ubuntu 8.04 AMD" in the Platform drop-down, which should be "Ubuntu 8.04 AMD64". It would also be nice if we could get the Ubuntu source deb package from the same page. Otherwise, nice page.

---

### Post by Oldsoldier2003 on 2008-06-07
> **digerati said:**
> Any idea when this will be available in the supported repositories?  Correct me if I'm wrong but I believe this should be in the main repositories.

nope its the puel version. The Hardy repos were locked long ago so i doubt you'll see another virtualbox-ose update unless you install Intrepid

---

### Post by mixmatch on 2008-06-12
Upgrading the XP guest additions in my virtual machine from the 1.5.6 release to the 1.6.2 version causes me to lose access to my shared folders. Anyone else seeing this problem?

---

### Post by bluechargeboy on 2008-06-13
> **mixmatch said:**
> Upgrading the XP guest additions in my virtual machine from the 1.5.6 release to the 1.6.2 version causes me to lose access to my shared folders. Anyone else seeing this problem?

mixmatch, the fix detailed [_here_]("http://forums.virtualbox.org/viewtopic.php?p=25840&sid=ef182ce32a57fb1492aae71945f3a7e5") seems to work.

1. uninstall old version of Guest Additions
2. reboot
3. install Guest Additions v1.6.2
4. reboot (-> no access to shared folders)
5. install Guest Additions v1.6.2 again
6. reboot (-> now I have access as expected)

Works for me!

---

