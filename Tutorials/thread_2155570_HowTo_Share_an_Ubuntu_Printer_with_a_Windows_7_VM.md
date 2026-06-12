---
title: "HowTo Share an Ubuntu Printer with a Windows 7 VM"
date: 2013-06-18
forum: Tutorials
---

### Post by haz2a on 2013-06-18
[B]Overview
Print From the Windows Driver?
Ubuntu: Share the Printer
Host-Only Network for Virtualbox VM
Set Ubuntu Firewall Rules
Installing the Printer [Queue] in Windows
Troubleshooting[/B]



[SIZE=4]**Overview**[/SIZE]
Sharing like this is most useful where either:-
[LIST]
[*]a network printer is on a different subnet to Windows, eg: where Windows Virtual Machine (VM) has host-only networking (no access to the main LAN or internet) 
[*]or there is no driver for the printer compatible with the version of Windows (eg: very old printer) 
[*]or the Ubuntu printer is not a networked printer eg: directly connected by USB 
[/LIST]

This method uses CUPS on Ubuntu to share the printer.
Any protocol may be used between Ubuntu and the printer (or any intermediate print server) that is supported by them both eg: USB, LPD/LPR, IPP, AppSocket, etc. It is assumed the printer is already installed and working well in Ubuntu.
The share to Windows is easiest by CUPS/IPP. Samba can also be used to provide Windows style share addressing if required, but I don't cover that here.

**Examples Given Below**
My examples are for an old Epson EPL-5500 printer attached to a Silex Pricom SX-5000U2 print server on my LAN with the static IP of 192.168.1.11.  My host OS is Ubuntu 12.04 (LTS) and I have Windows 7 in a Virtualbox VM. The VM has Virtualbox Host-Only Networking to protect Windows from the internet -  so it can communicate with Ubuntu, but cannot connect to the LAN to use the printer directly. The DHCP option is used on the Virtualbox host-only network, which provides Ubuntu with the address: 192.168.56.1, and Windows with 192.168.56.101.




**[SIZE=4]Print From the Windows Driver?[/SIZE]**
The Windows driver might give better results or functionality. To use this instead of the Linux driver (to print from Windows) requires installing a RAW Printer Queue in Ubuntu. If the Ubuntu driver is adequate, or there is no Windows driver available, this 'Print From the Windows Driver' stage may be skipped.
If the shared Ubuntu (CUPS) printer is a RAW print queue (no driver/PPD assigned) then the raw data from the Windows driver is fed directly to the printer. This should enable any extra features of the Windows driver, which might not be available in the Linux driver, to be used from Windows.

**[SIZE=3]Install a new version of the printer in Ubuntu as normal, eg: as a USB or network printer, but choosing 'Raw Queue' instead of the usual driver to suit the printer model. [/SIZE]**

 
[SIZE=3]**Installing a Raw Printer Queue for a Network Printer**[/SIZE]
Choose a protocol which is compatible with the printer or any physical print server box the printer is attached to, just as for the normal non-raw printer queue you already have working. The following examples are alternatives for my Pricom SX-5000U2 print server.

**AppSocket/HP JetDirect (Port 9100)**

_From CLI (Simplest)_
```
$ sudo lpadmin -p <RawPtrName eg: EPL-5500-RAW> -E -v socket://192.168.1.11:9100/lp_u1
```
NB: the IP is the location of the physical printer on its network, just as for the normal non-raw version of the printer, but using port 9100; and again using the same queue (eg: 'lp_u1') on any Network Print Server as the non-raw version.

_From Ubuntu Printer Config GUI_
Ubuntu dash > printing (Gnome CUPS config tool: system-config-printer) > Add Printer > Network printer
> AppSocket / HP JetDirect > Host:  192.168.1.11  > Port Nr: 9100 (can't add Print Server queue name here)
> Forward > Drivers > Choose Driver > Select from DB > Generic > Fwd > Raw Queue 
> Generic Raw Queue > Fwd > Short Name eg: EPL-5500-RAW > Apply
IF physical ptr on a physical Print Server: Right-Click on new ptr > Props > Device URI box: add Print Server queue name eg: '/lp_u1'. The full URI shd now be similar format as that for lpadmin cmd abv.

**LPD From Ubuntu Print Config GUI**
Ubuntu dash > printing (Gnome CUPS config tool: system-config-printer) > Add Printer > Network printer
> LPD > Host:  192.168.1.11 > Queue: lp_u1
> Forward > Drivers > Choose Driver > Select from DB > Generic > Fwd > Raw Queue 
> Generic Raw Queue > Fwd > Short Name eg: EPL-5500-RAW > Apply




**[SIZE=4]Ubuntu: Share the Printer[/SIZE]**
Use the Gnome CUPS config tool (system-config-printer): Ubuntu dash > printing

**Share the Printer**
Gnome Printing > Right-Click on printer > Share

**Publish Shared Printers**
Gnome Printing > Server (top menu) > Publish shared printers

**Check CUPS configs**: ```
$ less /etc/cups/cupsd.conf
```  ensure that got:-
Browsing On
BrowseAllow all
If not, then edit the file ($ sudo ...).

**Check Who Can Use**
Gnome Printing > Right-Click on printer > Props > access Control




**[SIZE=4]Host-Only Network for Virtualbox VM[/SIZE]**
If Windows is in a Virtualbox VM and is not attached to the main LAN (eg: to protect it from the inet) then it must be provided with a host-only network and DHCP support.

Virtualbox Manager > File > Prefs > Network > Add > vboxnet0 > Edit > DHCP Server (Enabled).

Windows VM > Settings > Adapter [1] > Enable > Attached  to > Host-Only (vboxnet0)

Starting Windows 7 shows (bottom right-hand icon) "Unidentified Network - No internet access".

$ ifconfig  (with Virtualbox running) will list the Host-Only virtual interface (eg: vboxnet0) alongside the other host interfaces eg: eth0, including the host's IP on this network eg: 192.168.56.1.
> ipconfig  in Windows will show its IP eg: 192.168.56.101.




**[SIZE=4]Set Ubuntu Firewall Rules[/SIZE]**
Dash > Gufw > add the following:-
Simple     Allow     In     Both (TCP + UDP)     631,9100
(Port 631 = CUPS, Port 9100 = IPP )
These might already be allowed OUT (if you're printing to other print servers) but need adding as IN rules.




**[SIZE=4]Installing the Printer [Queue] in Windows 7[/SIZE]**

**Check that IPP is installed**
Control Panel > Progs + Features > Turn Windows features on or off (LHS) > Windows Features > Print Services (expand) > Internet Printing Client > Enable if not already.

If Internet Printing Client was just enabled, then restart the Print Spooler:-
Start > "Administrative Tools" > Services > Right-Click Print Spooler > Restart.


**[SIZE=3]Install Printer (Queue) to Use Ubuntu Shared Printer[/SIZE]**
This assumes that the printer is working well in Ubuntu, since Windows will use Ubuntu to print.

**Confirm that CUPS is accessible and obtain the full URI of the printer**
Windows 7 > web browser > 192.168.56.1:631
(the Ubuntu host IP on the host-only network)
CUPS Web Interface > Printers should list the host's shared printers.
Click on the rqd printer eg: EPL-5500 (or EPL-5500-RAW to print using the Windows driver).
The URI in the address bar is the full address Windows 7 will need eg: 192.168.56.1:631/printers/EPL-5500

Start > Devices + Printers > Add printer > Network printer > Stop > Printer I want isn't listed

_Addressing the Shared Printer_
Do not "Add a printer using a TCP/IP address" (what MS call a "standard TCP/IP port")
Instead > Shared printer by name
Enter:  [http://192.168.56.1:631/printers/EPL-5500](http://192.168.56.1:631/printers/EPL-5500) (the 'http://' prefix is rqd)
"Connecting to..." > 

_Add Printer Driver wizard_
IF the shared Ubuntu (CUPS) printer has its own driver installed, then install the driver for the actual printer (if Windows lists it or one known to be compatible with it, eg: the Epson EPL-5500 has no Windows 7 compatible driver, but it emulates the HP Laserjet 4, so installing that driver here works); or any good Postscript driver eg: HP Color Laserjet 8500 PS or Xerox DocuTech 135 PS2. 

OR IF the shared Ubuntu (CUPS) printer is a Raw Local Printer (no driver assigned in Ub) then a driver compatible with the physical printer must be installed in Windows: if Windows 7 lists the exact model (or we can get it) then use that, or if it lists (or we can get) a known compatible (eg: the Epson EPL-5500 has no Windows 7 compatible driver, but it emulates the HP Laserjet 4, so that driver works) then use that.

> "Success" > Print Test Page

NB: Whether the compatible HP Laserjet 4 is used to print to a raw print queue on Ubuntu, or the Postscript Laserjet 8500 PS driver is used to print to a non-raw print queue (with compatible driver installed) on Ubuntu , the Windows Printer Test Page says: "Data format: RAW".




**[SIZE=4]Troubleshooting[/SIZE]**

**Check if Ubuntu Firewall is Blocking Anything**
Assuming we're using ufw (eg: configured via Gufw)
```
$ cat /var/log/ufw.log | grep 192.168.56 | grep BLOCK
``` 
(assuming this is the subnet we're trying to start the printing from, eg: Windows 7 VM above)
Adjust the firewall rules to allow if required, per: Set Ubuntu Firewall Rules above.

**Printing Garbage or Just Little or Badly**
Windows > Printer > Right-Click > Props > Ports > Bidirectional > UNchk - reported to fix some probs on some ptrs.
[B]
Printer Previously Working Doesn't Now[/B]
Try power-cycling all network devices: Switch, physical Print Server, etc, and the printer itself - that can help if jobs have just been accumulating in the Linux print queue as "Pending".

Check the Printer Status in any physical Print Server

---

