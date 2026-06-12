---
title: "trouble with installing HP usb printer in 8.04 server"
date: 2009-05-14
forum: Server Platforms
---

### Post by joefizz on 2009-05-14
Hi

I hope someone can give me a hand with this.  I have been trying for hours to get an HP PSC-1510 printer working on an 8.04 server using HPLIP but still haven't been able to even get a test page.

Output from hp-check:

HP Linux Imaging and Printing System (ver. 3.9.4b)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or    
.run) to determine if the proper dependencies are installed to successfully compile HPLIP.                             
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an  
already built HPLIP supplied tarball has the proper dependencies installed to successfully run.                        
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both  
compile- and run-time dependencies).                                                                                   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt 4.x version...
OK, version 4.3.3 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.7
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.9.4b currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.4b

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-3.9.4b
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
cups-ppd-install=no
cups-drv-install=no
internal-tag=3.9.4b.10
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[installation]
version = 3.9.4b.10
date_time = 05/15/09 15:33:32



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_PSC1510
----------
Type: Printer
Device URI: hp:/usb/PSC_1500_series?serial=MY56NBC0G00498
PPD: /etc/cups/ppd/HP_PSC1510.ppd
PPD Description: HP PSC 1500 Series hpijs, 3.9.4b
Printer Filter "foomatic-rip" for printer "HP_PSC1510" not available: No such file or directory
error: Unable to connect to dbus session bus.
error: Unable to communicate with device (code=12): hp:/usb/PSC_1500_series?serial=MY56NBC0G00498
error: Device not found
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.





output from lsusb:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



I'm not sure if the printer should be showing when I run lsusb.  It is plugged in and switched on and I know it has shown up somewhere before.

The server has no GUI and is currently used mainly as a web and mail server.  Trying to add file and printing to it as well.

Any help would be greatly appreciated.

Thanks

Joe

---

