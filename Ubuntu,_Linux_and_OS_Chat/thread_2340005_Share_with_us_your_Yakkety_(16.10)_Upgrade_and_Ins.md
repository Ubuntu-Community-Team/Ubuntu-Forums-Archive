---
title: "Share with us your Yakkety (16.10) Upgrade and Installation Experiences"
date: 2016-10-14
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2016-10-14
It's that time again, Yakkety (16.10) was released October 13, 2016 Please tell us about your experience upgrading, or doing a fresh install of Yakkety Yak.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

Poll and thread for the previous release:

[https://ubuntuforums.org/showthread.php?t=2321306](https://ubuntuforums.org/showthread.php?t=2321306)

---

### Post by cariboo on 2016-10-14
This time I had a few problems doing a fresh install, all related to a UEFI install. When partitioning, I told the installer to create a new partition table, as I wasn't using Windows 10, I wanted to create an Ubuntu only system, I created the new partitions, and clicked the install button. A message box popped up saying that an operating system had been created in BIOS mode, and if I wanted to force a UEFI install to click the continue button. Clicking the button seemed to do nothing, and there was no progress indicator, or busy cursor icon. I may have been to impatient, as nothing seemed to happen, so I rebooted the system and tried again, still no joy :(. The only way I could install was to use the OEM option.

The next problem was that the OEM install option wouldn't let me install grub to /dev/sda, it automagically installed to the usb drive I was using to do the installation. Installing boot-repair solved that problem.

The rest of the installation went the way it should.

**Note:** I haven't tried Unity 8 yet so nothing to say about it.

---

### Post by Frogs Hair on 2016-10-14
The Budgie panel crashed while testing , but the native Unity desktop has no problems. This was an upgrade of 16.04 to 16.10 beta and then updated to the final release.
 
HP Elitebook
Intel i5
4 GB Ram
Integrated Gaphics
Broadcom BCM43224 802.11a/b/g/n (rev 01)

---

### Post by SantaFe on 2016-10-14
Upgraded from Ubuntu-MATE 16.04.1 to 16.10.  Zipped right along & no problems found so far.

---

### Post by oldrocker99 on 2016-10-19
I had nuttin' but problems installing from a USB: the dreaded "Cannot install GRUB" error.

I burnt a DVD, and success!

---

### Post by g33zr on 2016-11-08
I just bought a new System76 Sable PC with Ubuntu 16.04 installed. I was having a video problem (flickering, off-color screen) during Skype chats, so I installed Mint 18 where the problem persisted, but with help from System76 and my own research I was able to fix it. But I had a couple of other problems with Mint, so I installed Ubuntu 16.10, which runs perfectly. No problems whatsoever with audio, video, wireless, or peripherals. Great job devs! :)

---

### Post by Stilian_Zagorov on 2016-11-16
I tried updating from 16.04, but the updater crashed, so I restarted the laptop and now my UI is *bleeped* up and I can't do anything besides logging in.

But wait, there is more. I can't even boot into Ubuntu now because the laptop thinks that the cryptswap1 encryption is disk-wide. So now I can't access 50% of my drive (500GB for Ubuntu and 500GB for Windows)

Ugh.

---

### Post by uberalex88 on 2017-01-09
I actually posted my experience under hardware for the Y700.  Everything was already working fine on my Y700 other than the laptop was getting a little hot where the PCIe hard drive. Since I got it on-line with both a 128GB SSD and a 1TB hard drive, I just simply removed the hard drive.  

On my Dell Inspiron 15, it was already running Ubuntu Mate 16.04 so I had no problems with an install of 16.10.

I really like some of the new features in the 16.10 that I found under Mate Tweak.

[[IMG]http://i.imgur.com/7kkRqckm.png[/IMG]]("http://imgur.com/7kkRqck")

---

### Post by g3charlotte on 2017-01-27
Dell Latitude E7240
Intel Core i5 (4th Gen) 4300U / 1.9 GHz
Intel HD Graphics 4400
Intel Dual Band Wireless-AC 7260
128GB SSD
4GB RAM

I wanted to have a "play" to brush up on my *NIX knowledge as it had been a while so my boss let me grab a laptop from the pile that were due to be disposed of (none of the users want the E7240s as they're "too old"), so I was able to completely blow the Windows install away and perform a clean install of Ubuntu MATE.

Booting from a USB flash drive was nice and quick and the installation process was easy.  The only issue I had once I rebooted was that the WiFi would stop working after waking from sleep and I had to edit a file to force it to restart the WiFi adapter every time it wakes.

---

### Post by sgian on 2017-02-24
I have a big problem for me with kubuntu 16.10.  Kubuntu 16.04 worked fine, until it suddenly developed a problem that I chased for a day until figuring out that it was a bad RAM chip. By then, my installation was messed up, so I did a fresh install from dvd of 16.10.  I've worked through some issues as I am new to KDE, and already know just enough to get myself into a lot of trouble with linux, lol.  Anyways, my current issue is that apparently hplip is not fully supported on Kubuntu 16.10 for some reason.  I just ran hp-check and came up with these results
```
Saving output in log file: /home/scott/hp-check.log

HP Linux Imaging and Printing System (ver. 3.16.7)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode  
before compiling the HPLIP supplied tarball (.tar.gz or .run)
to determine if the proper dependencies are installed to     
successfully compile HPLIP.                                  
2. Run-time check mode (-r or --run): Use this mode to       
determine if a distro supplied package (.deb, .rpm, etc) or  
an already built HPLIP supplied tarball has the proper       
dependencies installed to successfully run.                  
3. Both compile- and run-time check mode (-b or --both)      
(Default): This mode will check both of the above cases (both
compile- and run-time dependencies).                         

Check types:                                                 
a. EXTERNALDEP - External Dependencies                       
b. GENERALDEP - General Dependencies (required both at       
compile and run time)                                        
c. COMPILEDEP - Compile time Dependencies                    
d. [All are run-time checks]                                 
PYEXT SCANCONF QUEUES PERMISSION                             

Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version

warning: 12-16.10 version is not supported. Using 12-16.04 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 GNU/Linux
 Host: slim-emach-1604kubu
 Proc: 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 GNU/Linux
 Distribution: 12 16.10
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.16.7
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for 12 distro  16.10 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.16.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip
html=/usr/share/doc/hplip-doc
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.16.7
restricted-build=no
ui-toolkit=qt5
qt3=no
qt4=no
qt5=yes
policy-kit=yes
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 02/24/17 08:54:36
version = 3.16.7


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

------------------------
| General Dependencies |
------------------------

 error: cups-devel    CUPS devel- Common Unix Printing System development files    REQUIRED        -               -               MISSING    'cups-devel needs to be installed'
 error: libcrypto     libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           MISSING    'libcrypto needs to be installed'
 error: python3-devel Python devel - Python development files                      REQUIRED        2.2             3.5.2           MISSING    'python3-devel needs to be installed'
 error: libusb        libusb - USB library                                         REQUIRED        -               1.0             MISSING    'libusb needs to be installed'
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 error: sane-devel    SANE - Scanning library development files                    REQUIRED        -               -               MISSING    'sane-devel needs to be installed'
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.4           OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.24'         OK         -
 error: libnetsnmp-devel libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           -               MISSING    'libnetsnmp-devel needs to be installed'
 error: python3-notify2 Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               MISSING    'python3-notify2 needs to be installed'
 error: python3-pyqt4-dbus PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             4.11.4          MISSING    'python3-pyqt4-dbus needs to be installed'
 error: libjpeg       libjpeg - JPEG library                                       REQUIRED        -               -               MISSING    'libjpeg needs to be installed'
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.5.2           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 python3-pyqt4        PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 error: cups-image    CUPS image - CUPS image development files                    REQUIRED        -               -               MISSING    'cups-image needs to be installed'
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.2.0           OK         -

----------------------
| Scan Configuration |
----------------------

'/etc/sane.d/dll.d/hpaio' not found.
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.16.7          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.16.7          OK         -

--------------
| COMPILEDEP |
--------------

 error: libtool       libtool - Library building support services                  REQUIRED        -               -               MISSING    'libtool needs to be installed'
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               6.2.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -

-------------------------
| External Dependencies |
-------------------------

 error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
 error: xsane         xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             -               MISSING    'xsane needs to be installed'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.19            OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 error: dbus          DBus - Message bus system                                    REQUIRED        -               1.10.10         MISSING    'DBUS may not be installed or not running'
 network              network -wget                                                OPTIONAL        -               1.18            OK         -
 error: avahi-utils   avahi-utils                                                  OPTIONAL        -               -               MISSING    'avahi-utils needs to be installed'
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.16.7          OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.16.7          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/net/deskjet_3630_series?ip=192.168.2.23&queue=false' is a Hewlett-Packard deskjet_3630_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
lpstat
------
Type: Unknown
Device URI: No destinations added.


--------------
| PERMISSION |
--------------

 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
error: 'libcups2-dev' package is missing/incompatible 
error: 'cups-bsd' package is missing/incompatible 
error: 'cups-client' package is missing/incompatible 
error: 'openssl' package is missing/incompatible 
error: 'python3-dev' package is missing/incompatible 
error: 'libusb-1.0.0-dev' package is missing/incompatible 
error: 'libsane-dev' package is missing/incompatible 
error: 'libsnmp-dev' package is missing/incompatible 
error: 'snmp-mibs-downloader' package is missing/incompatible 
error: 'libjpeg-dev' package is missing/incompatible 
error: 'libcupsimage2-dev' package is missing/incompatible 
error: 'libtool' package is missing/incompatible 
error: 'libtool-bin' package is missing/incompatible 
error: 'libcups2' package is missing/incompatible 
error: 'libdbus-1-dev' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'python3-notify2' package is missing/incompatible 
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'xsane' package is missing/incompatible 
error: 'avahi-utils' package is missing/incompatible 

Total Errors: 15
Total Warnings: 0


Done.

```

So now I have some dependencies to install.  If I can't figure it out today, then I will go back to 16.04 Kubuntu because I am frustrated.

---

### Post by unhammer on 2017-03-11
The Thinkpad X220 upgraded from 16.04 without any issues (well, except I had to remove the arc-theme repo because arc-theme is now in the official repos).

The HP Spectre x360, however, I had installed the [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) on, and on upgrading I somehow lost the xserver-xorg-input-all package which[ made the mousepad work like a touchscreen]("http://askubuntu.com/questions/890629/my-touchpad-works-like-a-touchscreen") (absolute coordinates). Simply reinstalling that package fixed it, but that seems like a bug in the upgrade.

---

