---
title: "Ubuntu Studio 12.10 Quantal Quetzal Released!"
date: 2012-10-18
forum: Ubuntu Studio
---

### Post by smartboyhw on 2012-10-18
Ladies and Gentlemen, the Ubuntu Studio team hereby would like to introduce the new Ubuntu Studio release--Ubuntu Studio 12.10 Quantal Quetzal is now officially released!

From the release notes of Ubuntu Studio 12.10 Quantal Quetzal:
[B]
New Features in Ubuntu Studio 12.10[/B]

 Ubuntu Studio is the Ubuntu flavour designed for content creation.

 It’s produced as a DVD image that can also be converted to an USB stick and includes support for most languages by default.

Improved Interface:


[LIST]
[*]   A new web page is out. The help button on the main menu points there.
[*] Task Manager has been switched to System Monitor for better memory use display.
[*] A main menu tool has been added to setting to allow the user to change their menu.
[*] Add/fix text plymouth theme for those video cards that won’t see graphics so it says Ubuntu studio.
[*] Set up Software Center menu items for our workflows.
[*] Fixed submenu icons for accessories, education and network.
[/LIST]
 
New software include:


[LIST]
[*]   Xfce updated to version 4.10 (based off of Xubuntu)
[*] Kernel (lowlatency) is now of version 3.5
[/LIST]
**Ubuntu Studio Applications**


[LIST]
[*]  The menu has been fixed moving audio production tools out of Media Playback.
[*]A MIDI router and MIDI tools menu have been added.
[*]Add qmidiroute to audio workflow to cover missing functionality
[*]Added open-clip-art package to graphics seed
[*]Move mixer applications from media playback menu to audio menu.
[*]Nautilus is default file manager for everything now
[/LIST]
**Common Infrastructure**
  
  **Secure Boot**
 
 Ubuntu 12.10 is the first Ubuntu release to support [UEFI Secure Boot,]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot")  a standard for controlling what software can be run on a computer in an  effort to curtail malware that takes over the system at boot time.  Supporting Secure Boot, a part of the Windows 8 certification  requirements for client systems, ensures that Ubuntu will continue to  provide an “it just works” experience on new hardware.

 Due to time pressures, only some flavors released with 12.10 will install and boot on Secure Boot hardware:

[LIST]
[*]  Ubuntu desktop
[*]Ubuntu server
[*]Edubuntu
[/LIST]
We expect to enable all other flavors in 13.04.
  [B]
  Migration-support deprecated[/B]

 The tool responsible for migrating user accounts from other operating systems to Ubuntu (migration-assistant) has been [removed]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-May/035263.html") from the installer.
  [B]
  Linux kernel 3.5.5[/B]

 The Ubuntu 12.10 Quantal Quetzal release includes the [3.5.0-17.28 Ubuntu Linux kernel ]("https://launchpad.net/ubuntu/+source/linux/3.5.0-17.28")which was based on the [v3.5.5 upstream Linux kernel]("http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.5.5.tar.bz2"). This is an update from the [3.2.0-23.36 Ubuntu Linux kernel]("https://launchpad.net/ubuntu/+source/linux/3.2.0-23.36") which shipped in Ubuntu 12.04 LTS Precise Pangolin and was based on the [v3.2 upstream Linux kernel]("http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.2.tar.bz2"). Other notable changes with the Ubuntu 12.10 Quantal Quetzal kernel include:

[LIST]
[*]  Transitioning of the i386 generic-pae flavor to become the generic flavor offering
[*]Collapsing of the virtual flavor back into the generic flavor
[*]Homogenizing the entire linux-meta package
[*]Arrival of a new highbank arm server kernel flavor
[*]Changing of the default scheduler from cfq to deadline
[*]Packaging updates for signed kernels
[/LIST]
**Python 3.2**

 The Ubuntu desktop has begun migrating from Python 2 to [Python 3]("http://docs.python.org/py3k/whatsnew/3.0.html").  Most Python applications included in the desktop and their dependent  libraries have been ported to Python 3. In most cases, Python 3 versions  of libraries are available alongside their Python 2 counterparts.  Ported applications will only run with Python 3. Work will continue in  Ubuntu 13.04.

 If you have your own programs based on Python 2, fear not! Python 2 will continue to be available (as the python  package) for the foreseeable future. However, to best support future  versions of Ubuntu you should consider porting your code to Python 3. [Python/3]("https://wiki.ubuntu.com/Python/3") has some advice and resources on this.
  
  **GNU Toolchain**

 Ubuntu 12.10 is distributed with an updated default toolchain that includes: [GCC]("http://www.gnu.org/software/gcc/") 4.7.2 (was GCC 4.6 in 12.04 LTS), a binutils snapshot from the 2.23 branch (was 2.22 in 12.04 LTS), eglibc 2.15, and gdb 7.5.

 Further information can be found upstream ([GCC-4.7]("http://gcc.gnu.org/gcc-4.7/changes.html"), [gdb]("http://sourceware.org/gdb/download/ANNOUNCEMENT")).
  
  **Java Toolchain**

 Ubuntu 12.10 ships [OpenJDK7]("http://openjdk.java.net/") as  the default Java implementation. This brings improved performance, new  features and better compatibility with other Java 7 implementations.

 Use of the OpenJDK6 is now deprecated and the openjdk-6-* packages in universe for Ubuntu 12.10 will not be provided in future releases of Ubuntu.
   
**Installation**

  
  **Overview**

 Preparing your computer for Ubuntu Studio is now simpler, with a  wider range of disk setup options. Each of these are detailed at length  to provide you with a clear understanding of the actions that will take  place with your selection.

 You can now reinstall or upgrade an existing copy of Ubuntu Studio  with the Ubuntu Studio DVD installer, provided that your computer is  connected to the Internet.
  
  **Download**

 Ubuntu Studio 12.10 images can be downloaded from:
 [http://cdimage.ubuntu.com/ubuntustudio/releases/12.10/](http://cdimage.ubuntu.com/ubuntustudio/releases/12.10/) ([UbuntuStudio]("https://wiki.ubuntu.com/UbuntuStudio"))  
[B]
  System Requirements[/B]

 The minimum memory requirement for Ubuntu Studio 12.10 is 768 MB of  memory. It is highly recommended that you have 2GB or more memory though  so that the system will perform much better. More information about  other recommended hardware on the new Ubuntu Studio website when it is  released.
  
  **Upgrading**
 [B]

  Upgrading from Ubuntu Studio 12.04[/B]   

 To upgrade from Ubuntu Studio 12.04, press Alt+F2 and type in "upgrade-manager"(without the quotes) into the command box. Update  Manager should open up and display following message: "New distribution  release ’12.10&#8242; is available. Click Upgrade and follow the on-screen instructions".

 Since the upgrade does not include the new “photography” and  “publishing” metas, so if you want the photography and publishing  packages in your upgrade, please install them manually after upgrade by  typing "sudo apt-get install ubuntustudio-meta-photography  ubuntustudio-meta-publishing" in your terminal.
  
  **Upgrading from Other Releases**
 
 Users of other Ubuntu Studio releases need to upgrade first to 12.04, and then to 12.10.

 For further information on upgrading to 11.10, please see the [Ubuntu Precise upgrade instructions]("https://help.ubuntu.com/community/PreciseUpgrades").
  [B]
Known Issues[/B]

  
  **Graphics and Display**

  Proprietary drivers are now installed using software-properties-gtk (Software Sources), under the tab “Additional Drivers”. 

**Applications**

   
  **Installation**


[LIST]
[*]   We have received reports that booting the Ubuntu installer in UEFI  mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may  trigger a firmware bug that renders the machine unbootable. While this  bug has not been confirmed to affect Ubuntu 12.10, users are advised to  use caution when installing on Samsung laptops and ensure that they are  configured for legacy BIOS mode, not UEFI mode. ([1040557]("https://bugs.launchpad.net/bugs/1040557"))
[LIST]
[*]The consolidation of desktop installation media into a single image  means that some installation options that were previously available on  the alternate CD have no direct replacement on the desktop image.
[*]Users who were installing using the alternate CD to install with LVM  or full-disk encryption can now use the desktop image for this.
[*]To install LTSP, please install using the Ubuntu Server 12.10 image,  then add ltsp after installation. You can also continue to install with  Ubuntu 12.04 LTS media and upgrade to 12.10 from there.
[*]There are several options for installing using software RAID. You can:
[LIST]
[*]install using the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the ‘debian-installer’ directory on the mirrors;
[*]install using the desktop CD and migrate the disks to RAID post-install;
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade.
[/LIST]
 
[/LIST]
 
[*]The desktop image installer cannot unlock existing encrypted (LUKS)  volumes. If you need to make use of existing encrypted volumes during  partitioning, then use the “Try Ubuntu without installing” boot option  to start a live session, open the encrypted volumes (for example, by  clicking on their icons in the Unity launcher), enter your password when  prompted to unlock them, close them again, and run ubiquity to start the installer. ([1066480]("https://bugs.launchpad.net/bugs/1066480"))
[*]ARM OMAP4 machines will sometimes boot to a black screen during  installation. It’s likely that the system has booted fine, but you will  need to switch to another tty then back to tty7 (Ctrl+Alt+F1 and then  Alt+F7) to get graphics. ([1065902]("https://bugs.launchpad.net/bugs/1065902"))
[*]On ARM Panda boards with no external storage attached, the installer  interface will be confusing and installation is likely to fail. We  strongly recommend attaching an external hard disk when installing on  Panda boards. ([1053030]("https://bugs.launchpad.net/bugs/1053030"))
[*]On a mac with an external display can not run in framebuffer mode error occurs on the 2nd reboot onwards. ([1066883]("https://bugs.launchpad.net/bugs/1066883"))
[/LIST]
**Kernel**


[LIST]
[*]   Haswell processor graphics is not fully supported. ([1066975]("https://bugs.launchpad.net/bugs/1066975"))
[*]On some systems, when opening lid, there is a kerneloops with a suspend/resume failure message seen. ([1054732]("https://bugs.launchpad.net/bugs/1054732"))
[*]On certain ASUS machines with AMD graphic chips, a WMI event and  ACPI interrupt are sent at the same time when hitting the hotkey to  change display mode, resulting in the display mode being changed twice  in succession. Users can work around this using the Displays panel in System Settings for changing display modes. ([1052278]("https://bugs.launchpad.net/bugs/1052278"))
[*]On ASUS N53SN laptops, the kernel does not boot without noefi on commandline. ([1053897]("https://bugs.launchpad.net/bugs/1053897"))
[/LIST]

**Networking**


[LIST]
[*]   In order to improve compatibility with other local nameserver  packages, NetworkManager now assigns IP address 127.0.1.1 to the local  nameserver process that it controls instead of 127.0.0.1. If the  system’s /etc/resolv.conf is absent or is a static file instead of the symbolic link to ../run/resolvconf/resolv.conf  installed by default then this static file will have to be updated by  the administrator in order to continue using the  NetworkManager-controlled nameserver.
[/LIST]
**Libvirt**


[LIST]
[*]   Windows vms which previously worked with ‘vga’ video now need ‘cirrus’ video.
[/LIST]

**Toolchain**


[LIST]
[*]  Python 2.7.3 includes a fix for a security vulnerability affecting Python’s dict and set  implementations. Carefully crafted, untrusted input could lead to  extremely long computation times and denials of service. Although  disabled by default, vulnerable applications such as CGI scripts can  explicitly enable “hash randomization” to prevent this exploit. Due to  implementation details of this fix, virtualenvs created with older 2.7.x  releases may not work with 2.7.3. Specifically, the os module may not appear to have a urandom function. This problem can be solved by recreating the broken virtualenvs with the newer Python 2.7.3 version. See [http://bugs.python.org/issue13703](http://bugs.python.org/issue13703) for full details. ([954595]("https://bugs.launchpad.net/bugs/954595"))
[/LIST]
 
 [B]VMware Player
[/B] 

[LIST]
[*]  Installing either version 4 or 5 of VMware Player on Ubuntu 12.10 will trigger a crash report regarding lsb_release, because the lsb_release  command uses Python 3 but the VMware installation environment overrides  the Python settings to point to a bundled version of Python 2. ([938869]("https://bugs.launchpad.net/bugs/938869")) It is unknown what impact this has on VMware Player at runtime.
[/LIST]
 [B]
  Video Drivers[/B]


[LIST]
[*]   Several video drivers are not functioning with some legacy chip-sets.
[LIST]
[*]xserver-xorg-video-trident with some Trident Cyberblade chip-sets. Black screen and lock-up. [Bugs]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=trident&search=Search+Bug+Reports&field.scope=all&field.scope.target=t/")
[*]xserver-xorg-video-intel with i810 chip-sets. Segfault. [1060492]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1060492/")
[*]xserver-xorg-video-sis with 315 series (SiS 315/E/PRO, 550, [M]650,  651, 740, [M]661[FMG]X,[M]741[GX]) chip-sets. Black screen or loops  around login screen. [1034812]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1034812/")
[/LIST]
 
[/LIST]

[LIST]
[*]Workarounds
[LIST]
[*]Test with a [Live CD]("https://wiki.ubuntu.com/%20") to see if your hardware is effected.
[*]Trident Cyberblade – As the vesa driver doesn’t work with this chip-set the only solution is to remain with 12.04.
[*]Intel i810 – A new install can only be accomplished from the [Alternate ISO]("https://wiki.ubuntu.com/%20"). On reboot go to Recovery Mode and delete/blacklist video driver. On reboot create suitable [xorg.conf]("https://wiki.ubuntu.com/X/Config/Resolution") or use [RandR]("https://wiki.ubuntu.com/X/Config/Resolution") to get [correct resolution]("https://wiki.ubuntu.com/X/Config/Resolution") if necessary.
[*]SiS 315 Series – As Intel i810
[/LIST]
 
[/LIST]
**Support**
  

[LIST]
[*] Ubuntu Studio 12.10 is supported for 18 months.
[*]Security and bugfix updates for Ubuntu Studio are provided by the Ubuntu Studio Team and Community
[*]Support via email can be found at the [Ubuntu Studio Users Mailing List]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users").
[*]Support via IRC can be found in the #ubuntustudio channel on the freenode network
[/LIST]

Please download the release and try it out and we thank you for your support on Ubuntu Studio!


Regards,
Ubuntu Studio Team

---

### Post by jerrrys on 2012-10-19
Nice  :)

---

### Post by The Altruist on 2012-10-20
Where are the packages stored during the upgrade? Doesn't seem to be in the /var/cache/apt/archives ...
I'd like to also upgrade a second system without downloading everything all over again.

---

### Post by gregzeng on 2012-10-20
> **smartboyhw said:**
> Ladies and Gentlemen, the Ubuntu Studio team hereby would like to introduce the new Ubuntu Studio release--Ubuntu Studio 12.10 Quantal Quetzal is now officially released!

<SNIP>

Please download the release and try it out and we thank you for your support on Ubuntu Studio!


Regards,
Ubuntu Studio Team

[http://openjdk.java.net/](http://openjdk.java.net/)

Distrowatch tells me some versions of some of the packages included. Anyone know what other packages - or do we need to ..... time, $$ ... to find out what you are not telling us?

I assume Transmission, which I will immediately replace with qbittorrent. What other surprises: Kdenlive, ... ?

---

### Post by jejeman on 2012-10-20
> **gregzeng said:**
> [http://openjdk.java.net/](http://openjdk.java.net/)

Distrowatch tells me some versions of some of the packages included. Anyone know what other packages - or do we need to ..... time, $$ ... to find out what you are not telling us?

I assume Transmission, which I will immediately replace with qbittorrent. What other surprises: Kdenlive, ... ?
Here is the list from live DVD
[http://paste.ubuntu.com/1291376/](http://paste.ubuntu.com/1291376/)

---

### Post by Elfy on 2012-10-20
Please do not use this thread for support - start a new one in a suitable forum.

---

### Post by mjhouska on 2012-10-20
k

---

### Post by mahavishnu on 2012-11-12
Need opinions about installing Studio 12.10 on a Nettbook with 1,33GHz (Atom Z520) and 1GB DDR2 RAM. 

I'm concerned with Intel gma500 soundcard but it seems that it's solved with last versions of Ubuntu.

My main use of Studio will be for amp simulations (guitarix, rakarrack).

---

