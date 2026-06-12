---
title: "The Definitive 9.10 Broadcom Solution Guide"
date: 2009-12-31
forum: Tutorials
---

### Post by nallen00 on 2009-12-31
Broadcom hardware only.  Credit to respective solution providers included below.  Feel free to chime in if I've missed something.

[SIZE=4]**  Broadcom BCM4311/12/21/22 Hardware (STA driver):**[/SIZE]
[SIZE=1]_**NOTE**_: ASSUMES FRESH INSTALL. FOR LAPTOPS,[/SIZE][SIZE=1] ONCE THE SYSTEM REBOOTS AFTER INSTALL,[/SIZE][SIZE=1] REBOOT AGAIN
AND TOGGLE THE WIRELESS BUTTON *(YES,*[/SIZE][SIZE=1]* IT COULD BE THAT EASY).*[/SIZE]

Plug into the network via cable:

[LIST=1]
[*][SIZE=2]**  IF WIRED CONNECTION WORKS:**[/SIZE]
[LIST=1]
[*]Open System -> Admin -> Update Manager
[*]Check for updates, install, and reboot
[*]After reboot, open System -> Admin -> Hardware Drivers
[*]Look for "Broadcom STA wireless driver";
[LIST=1]
[*]_[SIZE=1]IF DRIVER IS PRESENT *AND *ACTIVATED:[/SIZE]_
[LIST=1]
[*]  Remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "bcmwl-kernel-source" *(if not available, move to step 2)*
[/LIST]

[LIST=1]
[*]Right-click and mark for installation
[*] Apply changes and reboot.
[*]Repeat steps 1.3-1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]**[SIZE=2]IF WIRED CONNECTION DOES NOT WORK:[/SIZE]**
[LIST=1]
[*]From **LiveCD ***(solution provided by jomtois [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288865") - edited for clarity):*
[LIST=1]
[*]Open Sytem -> Admin -> Synaptic Package Mgr
[*]Ensure 9.10 LiveCD is in the drive
[*]In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
[*]Check "Installable from CD-ROM/DVD" and close
[*]Reload *(disregard connectivity errors)*
[*]Search for "bcmwl-kernel-source"
[*]Right-click and mark for installation
[*]Apply changes and reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 **  [SIZE=4]Broadcom BCM4301/03/06/09 Hardware (B43 driver):[/SIZE]**
[SIZE=1]_**NOTE**_: IF YOUR CARD IS A BCM4306 REV 2, OR ONLY HAS 802.11B CAPABILITY, IT USES
B43LEGACY. ALL OTHER MODELS USE B43. THE STEPS BELOW WILL BUILD BOTH B43 AND
B43LEGACY (AND GET FIRMWARE FOR BOTH TOO). THE KERNEL AUTOLOADER WILL
AUTOMATICALLY DO THE RIGHT THING AND LOAD THE CORRECT DRIVER FOR YOUR DEVICE.
ADDITIONAL INFO [[COLOR=Red]HERE[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43"). ASSUMES FRESH INSTALL.  FOR LAPTOPS, ONCE THE SYSTEM REBOOTS
AFTER INSTALL, REBOOT AGAIN AND TOGGLE THE WIRELESS BUTTON (YES, IT COULD BE THAT
EASY).[/SIZE]

Plug into the network via cable:[SIZE=1]
[/SIZE]
[LIST=1]
[*][SIZE=2]**  IF WIRED CONNECTION WORKS:**[/SIZE]
[LIST=1]
[*]Open System -> Admin -> Update Manager
[*]Check for updates, install, and reboot
[*]After reboot, open System -> Admin -> Hardware Drivers
[*]Look for "Broadcom B43 wireless driver";
[LIST=1]
[*]_[SIZE=1]IF DRIVER IS PRESENT *AND *ACTIVATED:[/SIZE]_
[LIST=1]
[*]  Remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "b43-fwcutter" *(if not available, move to step 2)*
[*]Right-click and mark for installation
[*] Apply changes *(answer yes when asked "Fetch and install firmware?")*
[*]Reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]**[SIZE=2]IF WIRED CONNECTION DOES NOT WORK:[/SIZE]**
[LIST=1]
[*]From **LiveCD ***(based on solution provided by jomtois [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288865") - edited for clarity):*
[LIST=1]
[*]Open Sytem -> Admin -> Synaptic Package Mgr
[*]Ensure 9.10 LiveCD is in the drive
[*]In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
[*]Check "Installable from CD-ROM/DVD" and close
[*]Reload *(disregard connectivity errors)*
[*]Search for "b43-fwcutter"
[*]Right-click and mark for installation
[*]Apply changes *(answer yes when asked "Fetch and install firmware?")*
[*]Reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
[B][SIZE=4]Transfer Files from Another Computer
[/SIZE][/B][SIZE=1]_**NOTE**_:  IF NECESSARY, THE STA AND B43 PACKAGES CAN BE
DOWNLOADED USING THE LINKS BELOW.  BE SURE TO INCLUDE THE
APPROPRIATE DEPENDENCIES.
[/SIZE]
_STA Driver Source_
[[COLOR=Red]http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source[/COLOR]]("http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source")

_B43 Driver Source_
[[COLOR=Red]http://packages.ubuntu.com/karmic/b43-fwcutter[/COLOR]]("http://packages.ubuntu.com/karmic/b43-fwcutter")[SIZE=1]
[/SIZE]
Cheers.[SIZE=1]
[/SIZE]

---

### Post by alpacadaddy on 2009-12-31
Thanks for the response & info Nathan, but my nic is model 4318 and your info only refers to models 4301, 03, 06, 09, 11, 12, 21, 22...so I am not sure if it is applicable...

Thanks again and looking forward to learning more!

---

### Post by nallen00 on 2009-12-31
> **alpacadaddy said:**
> Thanks for the response & info Nathan, but my nic is model 4318 and your info only refers to models 4301, 03, 06, 09, 11, 12, 21, 22...so I am not sure if it is applicable...

Thanks again and looking forward to learning more!

I just noticed something :-k   Isn't it a little suspicious that we have a guitar-playing emoticon and not a coffee-drinking one...?  What with all the references to *beans *and what not #-o

Annnyway, thanks for mentioning this.  I'll do some research and either add it to the existing instructions, or create a new section.  Will depend on how unique the solution is.

---

### Post by Jason ON on 2010-01-05
Didn't work for me,  I had to put the LiveCD and load the software from there, and while Synaptic Manager lists both B43-fwcutter and the bcmwl-kernel-source (little green squares) and although I uninstalled and reinstalled both drivers hardware manager does not list the driver at all.  I hit a loop then as the directions all lead back to the install.

Any thoughts?

I'm working with the Broadcom 4306 rev 3 chipset and the AMD64 install of Ubuntu if that matters.  No matter what I do Hardware Drivers will not list the driver at all.  The only time it had is with a fresh install but as soon as I activate it, it disappears and all I have is Software Modem.

---

### Post by hyperhelium on 2010-01-05
Thank you, Thank you, thank you.

---

### Post by bbiandov on 2010-01-07
I too have BCM 4318, the Admin > Hardware Driver shows up, is active but no wireless connection under Networking. It is NOT an issue with the button as that one is ON and one can see it visually (it is a mechanical switch rather than fn-F4 key combination)

I did try the other BCM 43xx guides knowing that they refer to slightly different BCM model and none worked.

I suppose there is something very strange about 4318 since I see posts here and there but no working solution.

Will appreciate an expert's view on this chipset :)

Thanks

---

### Post by hijodedios2 on 2010-01-07
I have an HP Compaq Presario 2100 with what lspci -nnv reports as a Broadcom BCM4306 (rev 02) wireless card. Oddly enough, the PCI-ID is [14e4:4320], which [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) seems to think is the rev 03 version. Either way, after much searching I came up with a set of techniques roughly equivalent to your definitive guide. Still having no luck, I reinstalled and walked through the guide (wired connection worked, hardware drivers came up just fine with b43legacy and fwcutter, network manager reported a new attachment). I am able to scan and see network connections, but it stalls out actually connecting to my wireless router.

In the 2 days I've been playing with 9.10 the wireless card has connected twice. I am able to ping google, but by the time I bring up firefox the connection has dropped. Connecting again is neither predictable nor reproducible, including rebooting or restarting /etc/init.d/networking.

Looking at the system log I see a number of lines like:
```

kernel [228.308238] wlan0: direct probe to AP xx:xx:xx:xx:xx:27 try 1
kernel [228.308238] wlan0: direct probe to AP xx:xx:xx:xx:xx:27 try 2
kernel [228.308238] wlan0: direct probe to AP xx:xx:xx:xx:xx:27 try 3
kernel [228.308238] wlan0: direct probe to AP xx:xx:xx:xx:xx:27 timed out

```
My router is very definitely xx:xx:xx:xx:xx:26. iwlist reports :27, as well. Is there any known bug causing this behavior? What else should I check?

The router is a Linksys WRT54G using WPA2/PSK with AES encryption.

---

### Post by Blackthorne2 on 2010-01-08
I am seeing the EXACT same behaviour as hijodedios2.

I have the 4312 with the STA drivers. I see the network, can choose to connect, am prompted for my WPA key, and I can actually see the netbook show up in my routers connection list, then the netbook drops the connection. Router is D-Link DIR-615 w/ latest firmware.


SO, it's connecting, authenticating, getting an IP, and then dropping the connection. 

I am an Ubuntu noob, so if there are any logs troubleshooters here need dumped just let me know the commands and I will post em up.

---

### Post by bbiandov on 2010-01-08
Ok, so after some testing here is a verified guide for Broadcom BCM 4318 under Ubuntu 9.1

First I started by fresh install using ubuntu-9.10-desktop-i386.iso

After the install was done under hardware driver BCM43 was detected and after activating the driver, as expected, NADA. No wireless adapter reported by ifconfig.

[IMG]http://s193925491.onlinehome.us/pix/broadcom.png[/IMG]

However after rebooting, the wireless adapter showed up in ifconfdig. 

Note that I did not even have to do Ubuntu Updates Manager. This worked straight out of the ISO.

FYI: Here is the Broadcom device that I have as it is reported by lspci:

**1:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

---

### Post by zankapfel on 2010-01-11
I have the same problem as Jason ON, the driver will not show up in Hardware Drivers.

The most frustrating part is that the first time I tried to boot from my USB install, it was there, and worked perfectly. Then one day it was just gone and I have no idea why. Reinstalling does absolutely nothing, I've tried over and over.

I'm using a Compaq Presario V6420US. I'm not sure what broadcom chipset it uses.

---

### Post by yanvolking on 2010-01-13
Hi There,

I am trying to solve my internal broadcom WLAN device not working.  When I read your instruction :

Remove network cable, toggle wireless button, and log into network.

What do you mean by toggle wireless button?  Where is the wireless button?

Thanks

Yan

---

### Post by Zuseppe on 2010-01-13
> **bbiandov said:**
> Ok, so after some testing here is a verified guide for Broadcom BCM 4318 under Ubuntu 9.1

First I started by fresh install using ubuntu-9.10-desktop-i386.iso

After the install was done under hardware driver BCM43 was detected and after activating the driver, as expected, NADA. No wireless adapter reported by ifconfig.

[IMAGE]

However after rebooting, the wireless adapter showed up in ifconfdig. 

Note that I did not even have to do Ubuntu Updates Manager. This worked straight out of the ISO.

FYI: Here is the Broadcom device that I have as it is reported by lspci:

**1:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

Hi bbiandov.
I performed a fresh Ubuntu 9.10 install from "ubuntu-9.10-desktop-amd64.iso" (64-bit release) on my Acer 5024wlmi (with BCM4318 [AirForce One 54g] rev02).
Unfortunately, following your guide, I couldn't activate my wi-fi adapter using Ubuntu 64-bit out of the box.
So I installed b43-fwcutter following this guide from Ubuntu Community -> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
The result:
1. wlan0 active and recognized by Network Manager/ifconfig/iwconfig
2. Acer front Led is on (goes off if I deactivate wifi from Network Manager

Unfortunately, I cannot connect to wifi networks (even open ones) because connection process fails. I tried with Network Manager/wicd/Wi-fi radar without success.
Maybe it's Ubuntu 64 bit version?
Thank you for your help.

---

### Post by corck on 2010-01-13
I think I have the same problem as Blackthorne2 and hijo2...,

I experience that my connection works with my home router (WEP) and some others, however a lot of WEP/WPA connection just don't work.

I was in a hostel last weekend and could not connect to their WEP encrypted network, "thankfully" I kept the default windows installation to use.

Yesterday I was at a friends house, he has an apple airport, we tried all different things, WEP, WPA, no encryption, but I just could not get(keep) the connection. It was saying it tries to get an IP address but timed out then.

Pretty annoying. was wondering to install opensuse, to see if this is a Kubuntu problem.

btw I am on 64bit.


I just tried to connect to an open network "Trendnet", it used to work perfectly (maybe before my upgrade to 9.10). I can't connect to it, and it gets back to my personal network (VIEuVau).

I attach the daemon.log output, hopefully this helps
```

Jan 13 07:49:32 vostro wpa_supplicant[1287]: CTRL-EVENT-SCAN-RESULTS 
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): device state change: 8 -> 3 (reason 0)
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): deactivating device (reason: 0).      
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 7018
Jan 13 07:49:54 vostro NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) starting connection 'TRENDnet'                              
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)                                
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...                  
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...                    
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...                
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.                     
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...                 
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)                                
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1/wireless): connection 'TRENDnet' requires no security.  No secrets needed.
Jan 13 07:49:54 vostro NetworkManager: <info>  Config: added 'ssid' value 'TRENDnet'                                                      
Jan 13 07:49:54 vostro NetworkManager: <info>  Config: added 'scan_ssid' value '1'                                                        
Jan 13 07:49:54 vostro avahi-daemon[1103]: Withdrawing address record for 192.168.1.127 on eth1.                                          
Jan 13 07:49:54 vostro NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'                                                      
Jan 13 07:49:54 vostro avahi-daemon[1103]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.127.                
Jan 13 07:49:54 vostro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.                                
Jan 13 07:49:54 vostro avahi-daemon[1103]: Interface eth1.IPv4 no longer relevant for mDNS.                                               
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected                            
Jan 13 07:49:54 vostro avahi-daemon[1103]: querier.c: querier_remove() called but no querier to remove.                                   
Jan 13 07:49:54 vostro avahi-daemon[1103]: last message repeated 7 times                                                                  
Jan 13 07:49:54 vostro wpa_supplicant[1287]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys                                     
Jan 13 07:49:54 vostro NetworkManager: <info>  Config: set interface ap_scan to 1                                                         
Jan 13 07:49:54 vostro NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning                             
Jan 13 07:50:05 vostro wpa_supplicant[1287]: CTRL-EVENT-SCAN-RESULTS                                                                      
Jan 13 07:50:05 vostro wpa_supplicant[1287]: WPS-AP-AVAILABLE                                                                             
Jan 13 07:50:05 vostro wpa_supplicant[1287]: Trying to associate with 00:14:d1:64:6e:35 (SSID='TRENDnet' freq=2437 MHz)                   
Jan 13 07:50:05 vostro NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating                              
Jan 13 07:50:05 vostro wpa_supplicant[1287]: Association request to the driver failed                                                     
Jan 13 07:50:06 vostro wpa_supplicant[1287]: Associated with 00:14:d1:64:6e:35                                                            
Jan 13 07:50:06 vostro wpa_supplicant[1287]: CTRL-EVENT-CONNECTED - Connection to 00:14:d1:64:6e:35 completed (reauth) [id=0 id_str=]     
Jan 13 07:50:06 vostro NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated                            
Jan 13 07:50:06 vostro NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed                              
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TRENDnet'.
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.                                                   
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...                                                   
Jan 13 07:50:06 vostro NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)                                                                   
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)                                             
Jan 13 07:50:06 vostro NetworkManager: <info>  dhclient started with pid 7481                                                                                   
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...                                                  
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.                                                    
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...                                                    
Jan 13 07:50:06 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.                                                     
Jan 13 07:50:06 vostro dhclient: Internet Systems Consortium DHCP Client V3.1.2                                                                                 
Jan 13 07:50:06 vostro dhclient: Copyright 2004-2008 Internet Systems Consortium.                                                                               
Jan 13 07:50:06 vostro dhclient: All rights reserved.                                                                                                           
Jan 13 07:50:06 vostro dhclient: For info, please visit http://www.isc.org/sw/dhcp/                                                                             
Jan 13 07:50:06 vostro dhclient:                                                                                                                                
Jan 13 07:50:06 vostro NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit                                                           
Jan 13 07:50:06 vostro dhclient: Listening on LPF/eth1/00:24:2b:34:88:7a                                                                                        
Jan 13 07:50:06 vostro dhclient: Sending on   LPF/eth1/00:24:2b:34:88:7a                                                                                        
Jan 13 07:50:06 vostro dhclient: Sending on   Socket/fallback                                                                                                   
Jan 13 07:50:10 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4                                                                     
Jan 13 07:50:14 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6                                                                     
Jan 13 07:50:20 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11                                                                    
Jan 13 07:50:31 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8                                                                     
Jan 13 07:50:32 vostro wpa_supplicant[1287]: CTRL-EVENT-SCAN-RESULTS                                                                                            
Jan 13 07:50:39 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15                                                                    
Jan 13 07:50:51 vostro NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.                                                             
Jan 13 07:50:51 vostro NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 7481                                                          
Jan 13 07:50:51 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...                                              
Jan 13 07:50:51 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...                                                
Jan 13 07:50:51 vostro NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)                                                                   
Jan 13 07:50:51 vostro NetworkManager: <info>  Activation (eth1) failed for access point (TRENDnet)                                                             
Jan 13 07:50:51 vostro NetworkManager: <info>  Marking connection 'TRENDnet' invalid.                                                                           
Jan 13 07:50:51 vostro NetworkManager: <info>  Activation (eth1) failed.                                                                                        
Jan 13 07:50:51 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.                                                 
Jan 13 07:50:51 vostro NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)                                                                   
Jan 13 07:50:51 vostro NetworkManager: <info>  (eth1): deactivating device (reason: 0).                                                                         
Jan 13 07:50:51 vostro wpa_supplicant[1287]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys                                                           
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) starting connection 'VIEuVAU'                                                                  
Jan 13 07:50:54 vostro NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)                                                                   
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...                                                     
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...                                                       
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...                                                   
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.                                                        
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...                                                    
Jan 13 07:50:54 vostro NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)                                                                   
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1/wireless): connection 'VIEuVAU' has security, and secrets exist.  No new secrets needed.        
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'ssid' value 'VIEuVAU'                                                                             
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'scan_ssid' value '1'                                                                              
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'                                                                            
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'                                                                       
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'wep_key1' value '<omitted>'                                                                       
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'wep_key2' value '<omitted>'                                                                       
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'                                                                          
Jan 13 07:50:54 vostro NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed                              
Jan 13 07:50:54 vostro NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed                              
Jan 13 07:50:54 vostro NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.                                                      
Jan 13 07:50:54 vostro NetworkManager: <info>  Config: set interface ap_scan to 1                                                                               
Jan 13 07:50:54 vostro NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning                                                   
Jan 13 07:50:59 vostro wpa_supplicant[1287]: CTRL-EVENT-SCAN-RESULTS                                                                                            
Jan 13 07:50:59 vostro wpa_supplicant[1287]: Trying to associate with 00:18:f8:71:13:f2 (SSID='VIEuVAU' freq=2462 MHz)                                          
Jan 13 07:50:59 vostro wpa_supplicant[1287]: Association request to the driver failed                                                                           
Jan 13 07:50:59 vostro NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating                                                    
Jan 13 07:50:59 vostro wpa_supplicant[1287]: Associated with 00:18:f8:71:13:f2                                                                                  
Jan 13 07:50:59 vostro wpa_supplicant[1287]: CTRL-EVENT-CONNECTED - Connection to 00:18:f8:71:13:f2 completed (reauth) [id=0 id_str=]                           
Jan 13 07:50:59 vostro NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated                                                  
Jan 13 07:50:59 vostro NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed                                                    
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'VIEuVAU'. 
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.                                                   
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...                                                   
Jan 13 07:50:59 vostro NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)                                                                   
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)                                             
Jan 13 07:50:59 vostro dhclient: Internet Systems Consortium DHCP Client V3.1.2                                                                                 
Jan 13 07:50:59 vostro dhclient: Copyright 2004-2008 Internet Systems Consortium.                                                                               
Jan 13 07:50:59 vostro dhclient: All rights reserved.                                                                                                           
Jan 13 07:50:59 vostro dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 13 07:50:59 vostro dhclient:
Jan 13 07:50:59 vostro NetworkManager: <info>  dhclient started with pid 7486
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 13 07:50:59 vostro NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Jan 13 07:50:59 vostro dhclient: Listening on LPF/eth1/00:24:2b:34:88:7a
Jan 13 07:50:59 vostro dhclient: Sending on   LPF/eth1/00:24:2b:34:88:7a
Jan 13 07:50:59 vostro dhclient: Sending on   Socket/fallback
Jan 13 07:50:59 vostro dhclient: DHCPREQUEST of 192.168.1.127 on eth1 to 255.255.255.255 port 67
Jan 13 07:50:59 vostro dhclient: DHCPACK of 192.168.1.127 from 192.168.1.1
Jan 13 07:50:59 vostro dhclient: bound to 192.168.1.127 -- renewal in 17915 seconds.
Jan 13 07:50:59 vostro NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jan 13 07:50:59 vostro NetworkManager: <info>    address 192.168.1.127
Jan 13 07:50:59 vostro NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan 13 07:50:59 vostro NetworkManager: <info>    gateway 192.168.1.1
Jan 13 07:50:59 vostro NetworkManager: <info>    hostname 'vostro'
Jan 13 07:50:59 vostro NetworkManager: <info>    nameserver '192.168.1.1'
Jan 13 07:50:59 vostro NetworkManager: <info>    domain name 'lan'
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 13 07:50:59 vostro NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jan 13 07:50:59 vostro avahi-daemon[1103]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.127.
Jan 13 07:50:59 vostro avahi-daemon[1103]: New relevant interface eth1.IPv4 for mDNS.
Jan 13 07:50:59 vostro avahi-daemon[1103]: Registering new address record for 192.168.1.127 on eth1.IPv4.
Jan 13 07:51:00 vostro NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Jan 13 07:51:00 vostro NetworkManager: <info>  Policy set 'VIEuVAU' (eth1) as default for routing and DNS.
Jan 13 07:51:00 vostro NetworkManager: <info>  Activation (eth1) successful, device activated.
Jan 13 07:51:00 vostro NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jan 13 07:51:01 vostro ntpdate[7536]: adjust time server 91.189.94.4 offset 0.015373 sec


```

---

### Post by bgiannes on 2010-01-13
I have a WPC600 v1.0 linksys card which uses the Broadcom BCM43xx chip-set.  I've using the WXP driver from the linksys.com & ndiswrapper.

When i setup my wireless router w/ dd-wrt for WEP i can log on without problems, the connection is solid.  The router is set to N only.

But when i try and setup WPA or WPA2 i _can_ connect, but i can't get an IP address, (times out)?  With either network-manager or the interfaces, or even tryed wicd.  I've try using the network-manager from PPA as well.

maybe i should try a native driver?

update: lspci calls it a
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

well i install the driver, but it doesnt support my card.

---

### Post by corck on 2010-01-13
After some experimenting and logging in as a different user into KDE I could connect to the open network.

I logged back into my users KDE account removed all configuration in 
.kde/share/config/knetworkmanagerrc
.kde/share/config/networkmanagementrc

restarted knetworkmanager and I could connect to the network.

will try this next time I am at my friends house and hope to succeed.

---

### Post by arakele on 2010-01-13
I had this issue after upgrading from 9.04 to 9.10 on my dell latitude e6500.

Everything on this did not seem to work. Finally I noticed under 9.10 my button was no longer working to control my wireless(worked with bluetooth however)

I disabled the button in the BIOS and made sure wlan was enabled. Once I did this, the driver activated itself and I have not had any issues.


I did not have any of these problems in 9.04, but I figured I'd pass along the button issue. It worked fine in windows, but not in ubuntu 9.10.

---

### Post by Ukko22 on 2010-01-14
Didn't work for me. See my post and discussion at
[http://ubuntuforums.org/showthread.php?t=1380371](http://ubuntuforums.org/showthread.php?t=1380371)

---

### Post by bgiannes on 2010-01-14
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

howto....
[http://bbs.archlinux.org/viewtopic.php?id=59148](http://bbs.archlinux.org/viewtopic.php?id=59148)
i will try this out asap...

broadcoms latest stuff...
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

UPDATE:
i can't get this to work.
ps windozs calls the chip-set a bcm4321ab, (fyi draft N wireless) only Ndiswrapper with XP drivers works, tryed both dell & linksys XP drivers.  Only WEP works, no wpa or wpa2, but i do get N speeds.

---

### Post by mister_playboy on 2010-01-14
Thanks for this guide.  I just experienced this problem while installing Kubuntu 9.10 on my brother's Dell Inspiron 1521.

---

### Post by md80hb-iuh on 2010-01-23
Presario V5000US, Kubuntu with kernel 2.6.31-17. BCM4318, rev 2.
Dualboot, wifi OK with XP. Zip on Linux.
Absolutely no luck with all the tricks found on the web...Cannot see the restricted driver at all. Been trying to make it work since Karmic came out: Aka lost a week of my life since October trying to make that thing working.

---

### Post by The Glidd on 2010-01-23
Hope this is helpful to someone.  

I upgraded to 9.1 a few weeks ago and after going around the block with several solutions, I never had wireless.

Nothing worked.

I backed everything up and re-installed.  Now I'm following this simple guide.  If it doesn't work, I'll re-install 9.04.  So far, I've enabled STA.  Enable wireless is showing up in gray when I right-click network manager.  I can't enable the wireless.  I'll try and follow the b43 directions.

---

### Post by The Glidd on 2010-01-23
After disabling the STA driver, I followed the directions for b43.  Now no wireless at all is recognized.  Under network manager, all I get it an option for the wired network.

I've had enough of this.  Back to 9.04 for me.  I'd recommend that unless you have a very healthy sense of curiosity or are pretty technically minded, don't waste the time on all the other recommended fixes out there, go back to 9.04.

---

### Post by vacillator on 2010-01-24
"_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "bcmwl-kernel-source" *(if not available, move to step 2)*
[/LIST]

[LIST=1]
[*]Right-click and mark for installation"
[/LIST]
Thank heaven for this forum.  The above worked for me after foolishly looking elsewhere for the answer for days.  Thanks!

---

### Post by kat_ams on 2010-01-27
I was able to get it to work on a HP TX2-1050ed with broadcom 4322 from a fresh install by first installing the propriatary video card driver from ATI...
Then turned OFF the wireless radio... (this is important)
Then installed the STA driver while the wireless radio is still off...
I then removed the battery (HP has a wierd issue with the battery with this laptop) powered down to a complete halt. 
Removed the powercable 
then reinstered the powercable and battery and started the computer.
I waited for about two mintues after fully logging in,
 then turned on the wireless radio. 
Presto, wireless network.

---

### Post by daanvbaal on 2010-01-29
The proprietary drivers that came with Ubuntu didn't work for me.
I tried the B43-drivers but my card was not supported. The closed-source drivers form Broadcom itself do work flawlessly though.

You can check if your card is supported by the opensource B43 driver on: [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

My card (Broadcom Corporation BCM4322 802.11a/b/g/n) is not supported.

If it isn't, no need to mess with the ndiswrapper. Go to [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and follow the instructions in the README.txt

Edit:
After startup it didn't work anymore. Apparently the ssb driver interferes with the driver from Broadcom. I blacklisted the ssb driver, but this has no effect ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218763](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218763)).
I wrote a trivial script to remove ssb and reload the Broadcom wl driver:
```

#!/bin/sh

rmmod ssb
rmmod wl
modprobe wl

```

I saved it in /etc/init.d/broadcomwireless
And made it part of the startup scripts:
```

$ sudo update-rc.d broadcomwireless defaults

```

I also added lib80211 and wl to /etc/modules since they didn't load automatically.

The problem with ssb may also be the cause of the problems with the proprietary drivers that came with Ubuntu. I have not tested this.

---

### Post by mmmmna on 2010-01-29
To be fair, right up front I'll say I tried everything here several times, in several orders: did some things in order and then did some things out of order. I tried other things from one place in between some things from the other place, so now that I've managed to get this resolved, I can only say that I'm not 100% certain *how* things got worked out.

I **CAN** describe the issues I saw.

**Background:**
I have installed Ubuntu Netbook Remix 9.10 on a Desktop system but UNR might eventually get wiped since I am actually using a 64bit capable system. Before you jump.... I've only installed UNR 9.1 after installing and trying to configure _3_ other Ubuntu 9.1 distros (ulite 9.10, kubuntu 9.10, and U9.10 for 64 bit) and those other 3 failed and were successively replaced until I did this latest fresh install of UNR 9.10. Why UNR on a desktop? Because installing and using UNR 9.01 on my Asus EeePC 900A is first time I've had any version of Ubuntu that worked after being installed. I have gained a little bit of Ubuntu experience with that EeePC 900A, and so I felt this situation could be a sensible starting point for me to figure out how to get any other Ubuntu onto my Desktop box. I'm posting from UNR 9.10 on the Desktop box, I can only hope it stays configured after I reboot for the first time since I got the 4306 to work.

**What I tried (and where I got the information):**	](*,)
--Everything in this thread (up to kat_ams post 1 day ago) failed for _me_. Each step may have acted like it worked properly (I saw b43fw-cutter, the kernel sources and the bcmwl-modaliases each said they were installed at some time or another).
--Earlier, I also had been trying the steps beginning at "http://linuxwireless.org/en/users/Drivers/b43" [over here at Linux Wireless](http://linuxwireless.org/en/users/Drivers/b43).

**What I think made the difference:**
After everything I had tried that didn't work, I figured I would try uninstalling stuff. Uninstalling these 3 things made it all work!

Using Synaptic, I **un**installed:
[LIST]
[*]bcmwl-kernel-sources
[*]b43fwcutter
[*]bcmwl-modaliases
[/LIST]
After rebooting, I ran the hardware driver tool and tadaa.

Sorry for being so uninformative, but maybe what some folks need to try is the 3 uninstall steps I took, reboot and do the hardware driver install. While you could say that makes no sense, it is, no matter what, how I fixed my BCM4306R3 which previously did not work in Ubuntu Netbook Remix 9.10.

---

### Post by Eutaw on 2010-02-04
Thanks nallen00. This worked perfectly with my Dell Inspiron on Mint 8. Big thumbs up and extra beans, friend!

---

### Post by schmolch on 2010-02-04
Doesn't work for me.
As soon as i install the bcm-kernel-source my card is no longer been seen.
Without the bcm-kernel-source it sees it but times out connecting repeatingly.

---

### Post by blingenfelter on 2010-02-07
Thanks for all the info. On my Acer Extensa, at first I had trouble, but after installing both drivers (ending with STA), it worked! I wish it worked ootb, though, like some other distros.
Listed here:

[http://linux-programming.suite101.com/article.cfm/new-linux-distros-work-with-broadcom-wireless](http://linux-programming.suite101.com/article.cfm/new-linux-distros-work-with-broadcom-wireless)

The BCM43xx has been the bane of my linux experience. Can't wait to upgrade soon to a new laptop.

---

### Post by PetoB on 2010-02-07
Hi all,

I read whole this thread and many more, but still I did not find an answer...
I have DELL studio 1555 with wireless DELL 1397 Mini card 
...stupid things is taht i had installed Ubuntu on my USB hard drive and I manage up and run wifi (after manually instalation of restricted driver for broadcom), than I decide to run from internal hard derive...

...I did million of installation, try some magic and so, but I not managed wifi... finally I try to run from USB stick, where I have my Live Installation and I was able to run wifi from USB stick, I reboot and install from USB stick, after installation proces and reboot, I can manage just text mode... that is nothing for me

Now (after last installation) I can open Hardware drivers and i can see my driver for my card (which I use also on USB stick), but I am not able to activate, after activate finally nothing happend and driver is not active

...have somebody any idea? I see this card working on Ubuntu 9.10 ...after a week on front of computer I am sceptic that i will manage it, because I want to learn more about Linux and in the future may by switch only to linux...but for that I need linux with internet and I have no chance to use wired connection...

---

### Post by streever on 2010-02-08
Oddly enough, mmmmna's solution ACTUALLY WORKED for me :) Although I did install cutter, because I had not previously installed it, then followed the following instructions. Using Broadcom 4311 on V6120us (Compaq presario)
> **mmmmna said:**
> To be fair, right up front I'll say I tried everything here several times, in several orders: did some things in order and then did some things out of order. I tried other things from one place in between some things from the other place, so now that I've managed to get this resolved, I can only say that I'm not 100% certain *how* things got worked out.

I **CAN** describe the issues I saw.

**Background:**
I have installed Ubuntu Netbook Remix 9.10 on a Desktop system but UNR might eventually get wiped since I am actually using a 64bit capable system. Before you jump.... I've only installed UNR 9.1 after installing and trying to configure _3_ other Ubuntu 9.1 distros (ulite 9.10, kubuntu 9.10, and U9.10 for 64 bit) and those other 3 failed and were successively replaced until I did this latest fresh install of UNR 9.10. Why UNR on a desktop? Because installing and using UNR 9.01 on my Asus EeePC 900A is first time I've had any version of Ubuntu that worked after being installed. I have gained a little bit of Ubuntu experience with that EeePC 900A, and so I felt this situation could be a sensible starting point for me to figure out how to get any other Ubuntu onto my Desktop box. I'm posting from UNR 9.10 on the Desktop box, I can only hope it stays configured after I reboot for the first time since I got the 4306 to work.

**What I tried (and where I got the information):**	](*,)
--Everything in this thread (up to kat_ams post 1 day ago) failed for _me_. Each step may have acted like it worked properly (I saw b43fw-cutter, the kernel sources and the bcmwl-modaliases each said they were installed at some time or another).
--Earlier, I also had been trying the steps beginning at "http://linuxwireless.org/en/users/Drivers/b43" [over here at Linux Wireless](http://linuxwireless.org/en/users/Drivers/b43).

**What I think made the difference:**
After everything I had tried that didn't work, I figured I would try uninstalling stuff. Uninstalling these 3 things made it all work!

Using Synaptic, I **un**installed:
[LIST]
[*]bcmwl-kernel-sources
[*]b43fwcutter
[*]bcmwl-modaliases
[/LIST]
After rebooting, I ran the hardware driver tool and tadaa.

Sorry for being so uninformative, but maybe what some folks need to try is the 3 uninstall steps I took, reboot and do the hardware driver install. While you could say that makes no sense, it is, no matter what, how I fixed my BCM4306R3 which previously did not work in Ubuntu Netbook Remix 9.10.

---

### Post by mark-e-mark on 2010-02-14
Terrific guide; thanks for putting it together.  I've had the drivers installed for my BCM4322 on Ubuntu 9.10 for some months now, and I've been attempting to diagnose a "Slow SAMBA" issue.  After getting SAMBA to where it's not logging errors and mounts shares reliably, I've finally figured out that the sluggish performance on my home wireless network (XP Server shares) is matched by poor performance on the web.  Today I went to a newbie "testmyspeed" site and it told me I should get off dial-up. :o

Since then, I've been after my STA driver, and I compiled the latest WL driver according to instructions at Broadcom ([http://www.broadcom.com/docs/linux_sta/README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt")).  Since I'm a Windows guy and barely familiar with Unix, I was surprised that I successfully untarred and compiled the source correctly, but the driver is functioning.  I can reboot and jump right on my network.

However, I still have piss-poor network speed.  I'm writing this from my dual-boot HP dV4 Pavilion 64 bit where I can't watch my own movies unless I reboot to Vista. That's just not how things should be, so I am asking the community for suggestions.  I see that mmmmna had success with a re-install, so I'll try that but I don't hold much hope for it. Does anyone know what else I might try?

---

### Post by mark-e-mark on 2010-02-15
First test: Using Synaptic, I uninstalled:
[LIST]
[*]bcmwl-kernel-sources
[*]b43fwcutter
[*]bcmwl-modaliases
[/LIST]

If this sounds familiar, it's because I followed mmmmna's steps above.  Looking at the Hardware Drivers tool, it shows the Broadcom STA driver NOT activated.  

Here's the thing: I just doubled my wireless speed.  Triumphantly, I returned to the newbie speedtest site and clicked the silly icon.  Sure enough, I hit a download speed of 5mbs, twice that of before. :) I queued a movie from my XP share in Miro and it started playing so fast I didn't realize, and no stutter-stops this time!

My only guess is that the WL driver I compiled earlier is loaded from a different directory and the STA driver was interfering??  Any ideas on how to figure this out?  Is this as good as it gets?

---

### Post by 3DCGdesign on 2010-02-15
When I booted Ubuntu from Live CD I could install the proprietary Broadcom STA wireless driver no prob.  I was on the internet, surfing.  I could NOT however get the same driver to work w/ Kubuntu from Live CD.

I installed Kubuntu (9.10 x64) to hard drive and am finally dual booting between Kubuntu and (cough) Vista...

But when I go to look at hardware drivers, there are *none*, it just says there are none. "No proprietary drivers are in use on this system" ... so I can't even TRY.

So I tried putting the live disk in to get them from there, but have NO clue how to do it.  I'm the most UN-programmer geek I know... so speak slowly and use small words, please.

I don't even understand the "uninstall xyz" in the above posts because I have no idea how to uninstall/install a driver... it just 'worked' from the Live CD, and now, there's not even the option.

can't even find a "System -> Admin -> Synaptic Pkg Mgr" ...

---

### Post by PetoB on 2010-02-19
Hi, I am also new and your problem looks exactly same like my.

I try everything in the world, but nothing help me... i do not like this way, which is explained upper this installing and uninstalling and so and so in some exact way....

...I think, should by some easy way and is it!
Try this link [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) there are 2 package with drivers for broadcom.

I was able to installing by reading README.txt which is also able to download. Try it and do not forgot to put driver b43 to blacklist - in README is also explained how.

I do not have now time, but try it... if you will be not able to manage it, write info, I will try to help you... but really try it, I spend 8 days to understand and try to find problem and in that time I learn so much... after that I download this driver and in few minutes I installed driver and now is work :) ...do not forgot to put this b43 driver to blacklist, because after rebooting you will have same problem wifi will not work.

---

### Post by elkoselim on 2010-02-19
I have an laptop HP6735s (BCM4322 wireless adapter). I have installed drivers for wireless adapter. The problem is aircrack. When I type in:
aireplay-ng -9 eth2 
An error appears as:
...
sure RFMON is enabled: run 'airmon-ng start eth2 <#>'
sysfs injection support was not found either.

What should I do? PLS for solution!

---

### Post by teh603 on 2010-02-27
This guide worked on my Dell 1564 on Lucid Alpha 3.

---

### Post by spenny77 on 2010-02-28
Thanks for the tips, so helpful.  Got wireless to work after following the instructions, and activating the wireless card using Fn+F2 buttons on my Dell Inspiron 1501.  Happy to be posting this using my wireless connection!

---

### Post by Naggobot on 2010-03-14
I too had a problem which Ubuntu 9.10 is described in this thread a few times.

After fresh installation the system did not list any proprietary drivers under Administration->Hardware drivers. I tried to install the drivers from live-cd but failed to do so (probably since I had no idea what I should have installed since at the time I did not know what the hardware is. )

Instead of debugging a lot I made a fresh reinstall so that 

1. After booting from live CD I checked that the drivers are available and I activated the driver. 
2. I plugged in hardwire to internet
3. I run the fresh installation

I also noted that during the installation process the installer spent some time installing (and probably downloading)  b43-fwcutter.

After installation the system found proprietary drivers from Administration->Hardware drivers and I got everything working fine (except for some reason after hibernate the wireless remains disabled. This is problem only if I accidentally put the computer to hibernation instead of suspend)

Hardware is 
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

on Acer aspire 5020 (5021wlmi)
Edit: Fixed the model and I need to point out that I have not bothered to try and get bluetooth working and I do not know if it is possible. I need to point this out so that if someone happens to make some sort of purchasing decision based on this post there is all of the relevant info available. Also while writing this I did try the SD card reader and it works. I did have to use my teeth to pry the card out but this problem is not software related, its either just bad design, manufacturing or ageing.   
[URL="http://ubuntuforums.org/member.php?u=987979"]
[/URL]

---

### Post by drfurly on 2010-03-24
I've installed Linux on my Dell Inspiron 1420 laptop (which runs the BCM4312 wireless card) and completely uninstalled Linux on two separate occasions because I couldn't find a way to make my wireless card work. Finally, after some more refined Google searches I came across this thread and my wireless is up to snuff.

Great guide, I'm glad someone finally made a retard-proof walkthru for me.

---

### Post by nibbles.hax on 2010-04-05
I finally got it to work but I had to load it from a Kubuntu disc I had laying around, Thanks. :guitar:

---

### Post by Bobmnh on 2010-04-17
> **nallen00 said:**
> Broadcom hardware only.  Credit to respective solution providers included below.  Feel free to chime in if I've missed something.

[SIZE=4]**  Broadcom BCM4311/12/21/22 Hardware (STA driver):**[/SIZE]
[SIZE=1]_**NOTE**_: ASSUMES FRESH INSTALL. FOR LAPTOPS,[/SIZE][SIZE=1] ONCE THE SYSTEM REBOOTS AFTER INSTALL,[/SIZE][SIZE=1] REBOOT AGAIN
AND TOGGLE THE WIRELESS BUTTON *(YES,*[/SIZE][SIZE=1]* IT COULD BE THAT EASY).*[/SIZE]

Plug into the network via cable:

[LIST=1]
[*][SIZE=2]**  IF WIRED CONNECTION WORKS:**[/SIZE]
[LIST=1]
[*]Open System -> Admin -> Update Manager
[*]Check for updates, install, and reboot
[*]After reboot, open System -> Admin -> Hardware Drivers
[*]Look for "Broadcom STA wireless driver";
[LIST=1]
[*]_[SIZE=1]IF DRIVER IS PRESENT *AND *ACTIVATED:[/SIZE]_
[LIST=1]
[*]  Remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "bcmwl-kernel-source" *(if not available, move to step 2)*
[/LIST]

[LIST=1]
[*]Right-click and mark for installation
[*] Apply changes and reboot.
[*]Repeat steps 1.3-1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]**[SIZE=2]IF WIRED CONNECTION DOES NOT WORK:[/SIZE]**
[LIST=1]
[*]From **LiveCD ***(solution provided by jomtois [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288865") - edited for clarity):*
[LIST=1]
[*]Open Sytem -> Admin -> Synaptic Package Mgr
[*]Ensure 9.10 LiveCD is in the drive
[*]In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
[*]Check "Installable from CD-ROM/DVD" and close
[*]Reload *(disregard connectivity errors)*
[*]Search for "bcmwl-kernel-source"
[*]Right-click and mark for installation
[*]Apply changes and reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 **  [SIZE=4]Broadcom BCM4301/03/06/09 Hardware (B43 driver):[/SIZE]**
[SIZE=1]_**NOTE**_: IF YOUR CARD IS A BCM4306 REV 2, OR ONLY HAS 802.11B CAPABILITY, IT USES
B43LEGACY. ALL OTHER MODELS USE B43. THE STEPS BELOW WILL BUILD BOTH B43 AND
B43LEGACY (AND GET FIRMWARE FOR BOTH TOO). THE KERNEL AUTOLOADER WILL
AUTOMATICALLY DO THE RIGHT THING AND LOAD THE CORRECT DRIVER FOR YOUR DEVICE.
ADDITIONAL INFO [[COLOR=Red]HERE[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43"). ASSUMES FRESH INSTALL.  FOR LAPTOPS, ONCE THE SYSTEM REBOOTS
AFTER INSTALL, REBOOT AGAIN AND TOGGLE THE WIRELESS BUTTON (YES, IT COULD BE THAT
EASY).[/SIZE]

Plug into the network via cable:[SIZE=1]
[/SIZE]
[LIST=1]
[*][SIZE=2]**  IF WIRED CONNECTION WORKS:**[/SIZE]
[LIST=1]
[*]Open System -> Admin -> Update Manager
[*]Check for updates, install, and reboot
[*]After reboot, open System -> Admin -> Hardware Drivers
[*]Look for "Broadcom B43 wireless driver";
[LIST=1]
[*]_[SIZE=1]IF DRIVER IS PRESENT *AND *ACTIVATED:[/SIZE]_
[LIST=1]
[*]  Remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "b43-fwcutter" *(if not available, move to step 2)*
[*]Right-click and mark for installation
[*] Apply changes *(answer yes when asked "Fetch and install firmware?")*
[*]Reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]**[SIZE=2]IF WIRED CONNECTION DOES NOT WORK:[/SIZE]**
[LIST=1]
[*]From **LiveCD ***(based on solution provided by jomtois [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288865") - edited for clarity):*
[LIST=1]
[*]Open Sytem -> Admin -> Synaptic Package Mgr
[*]Ensure 9.10 LiveCD is in the drive
[*]In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
[*]Check "Installable from CD-ROM/DVD" and close
[*]Reload *(disregard connectivity errors)*
[*]Search for "b43-fwcutter"
[*]Right-click and mark for installation
[*]Apply changes *(answer yes when asked "Fetch and install firmware?")*
[*]Reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
[B][SIZE=4]Transfer Files from Another Computer
[/SIZE][/B][SIZE=1]_**NOTE**_:  IF NECESSARY, THE STA AND B43 PACKAGES CAN BE
DOWNLOADED USING THE LINKS BELOW.  BE SURE TO INCLUDE THE
APPROPRIATE DEPENDENCIES.
[/SIZE]
_STA Driver Source_
[[COLOR=Red]http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source[/COLOR]]("http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source")

_B43 Driver Source_
[[COLOR=Red]http://packages.ubuntu.com/karmic/b43-fwcutter[/COLOR]]("http://packages.ubuntu.com/karmic/b43-fwcutter")[SIZE=1]
[/SIZE]
Cheers.[SIZE=1]
[/SIZE]

Thank You very much. I just installed Ubuntu yesterday and I couldn't connect with the wireless. I have a Broadcom adapter which didn't have a driver. Update Manager installed 233MB worth of files. 

Thanks again. :)
Bobmnh

---

### Post by Sacrin on 2010-04-21
Hi, new to Linux and the forum.  I recently installed 9.10 on two computers - both have broadcom wifi cards.  I followed these instructions for both - worked great on my netbook, not so great on the second.

One of my computers (Dell XPS w/ 4322 card & 9.10 64) does not connect at start up.  I have to manually delete the automatic connection and re-connect every boot.  The connection also sometimes disconnects, and I have to go through the same process.  However, when the connection holds, it seems to be at a similar speed to the other computer.

Suggestions???  I saw someone posted a similar problem with their 4322, but I didn't understand what to do or if he had results.

Edit: the other computer seems to have the same problem - getting frustrating.  BTW, wifi connection is a WPA through an Edimax N router.

---

### Post by Canada Lee on 2010-04-23
I am running Ubuntu Karmic 9.10 (fresh install) on an Acer Aspire 3000 laptop with a Broadcom BCM4318 Airforce One 54g Rev 02 wireless...

I have wireless connectivity with the B43 driver showing up in the Hardware Drivers application.  I have used fwcutter, and can't be certain it completed and downloaded the necessary firmware, as there is a known bug relating to it, where it has a YES / NO question about downloading the firmware, and once selecting YES it exits...without any explanations as to success or failure...search for that fwcutter bug, and you'll know what I mean.

Anyways, what I am experiencing like so many others with broadcom's are experiencing is connectivity with random disconnects.  I have been trying to troubleshoot this for months, and I think we need to be digging deeper...not looking on the surface...  Here's what I've found out...

Need to have a controlled environment, so...
Laptop is running on AC with battery disconnected to rule out any power saving modes or functions attempting to interfere with operation.  Also, screen saver has been deactivated, and in power saving settings it is set while on AC to leave monitor on and never turn it off.

I have a big torrent downloading, and my wifi led light is flashing, and I have System Monitor running to show a graph of SENT & RECEIVED...when I see the LED light stop flashing (sometimes it may be off, or it may be on - but its state will remain constant, as in if its off, it stays off and doesnt fluctuate, if on, it stays on and doesnt fluctuate...and when I say the led may be off and stays in that state, I mean the wifi is on, but the led is blinking on and off to represent data xfer and the light just happened to be in the off state when it got HUNG UP.

When the led light gets stuck in whatever state, I know its about to loose connectivity, so I go to my terminal, and I >> ping -c 1 -I wlan0 [www.google.com](www.google.com) << and sure enough, the ping fails...so I do a >> sudo ifconfig wlan0 down << and if the led was stuck in the ON state, I will see the led go out, and the network manager starts scanning (it wont connect though till)...I then do a >> sudo ifconfig wlan0 up << and then the led light comes up...and the networking manager is still scanning and connects.

So...you dont have to do a reboot to get back your network connectivity...
So I made a little wireless script to KEEP-ALIVE the connection, and if lost, do the DOWN and UP command...sounds like it'd work you think...but makes me think something else may be causing the wireless to BE IGNORED...

Here's my keep-alive script...
#!/bin/bash
while [ 1 = 1 ]
do
if [[ ! `ping -c 1 -I wlan0 www.google.co.uk` ]]; then
echo "$(date)"
ifconfig wlan0 down
sleep 5s
ifconfig wlan0 up
sleep ${1}s
fi
done

I place it in my /usr/local/bin folder, make it executable...open a term, and run it with
sudo keep-alive 60
the 60 can be whatever you want it to be, it tells it to wait 60 seconds then ping, then wait 60 seconds then ping...it will run till you stop it with a CTRL-C...if a ping fails it will DROP the wlan0 interface, wait 5 seconds and then bring it back UP.  It will also echo in the terminal the ping failure and the time and date.

Thing I noticed, the terminal window is open, my keep-alive is running (I even had it echoing the successful pings every 60 secs) and I can see my cursor blinking in the terminal window...but when I notice the wifi led light not blinking, I know it is going to loose connectivity...and the cursor in the terminal has stopped blinking, and the clock on the top panel has stopped updating...everything on the screen is frozen to a snapshot of when the wifi was working...if I hit the mouse touchpad, the cursor in the terminal starts blinking, the clock in the top panel updates, my torrent display updates.  Its like the display went to sleep...and me touching the pad woke it...and it wasnt ASLEEP long enough for loss of connectivity, I know this cuz I waited longer before hitting the touchpad, and when that woke it, then I see a bubble saying disconnected from my network...and then the network manager scanning...and it wont connect, then my keep-alive script drops the wlan and brings it up, and then the netman scanning connects...

You have to remember, I have told it not to spin down hard drives, never to turn off or blank the display, nor screensaver.

But I know my keep-alive script was frozen, everything was frozen...no heavy CPU usage, just like asleep. and me touching the pad woke it from that sleep, and it continued where it was before the sleep...

What makes it sleep like that?  What components of Ubuntu perform that job?  It cant be the wifi driver just stopped communicating to the kernal, cuz me waking it by swiping my finger on the mouse touchpad should not be able to influence a modem communication driver...

On the other hand, a power savings mode, inactivity, screensavers and so on can be influenced by user input to interrupt their behavior.

So even when power savings is off, something is suspending things...and it is not at constant intervals, it is at random intervals.  There is no overheating going on here, and the cpu in not throttling.  I am using only max of 10% when torrent is dloading.  And if there was overheating or throttling, who ever heard of influencing their state by swiping the touchpad!

Anybody know where to look for something that is making the kernal or some other area going to sleep?

---

### Post by Canada Lee on 2010-04-23
Also, I have followed instructions from the following site to set up my firmware, as that site seemed to relate different scenarios for the b43legacy the b43 and the b43xx drivers, while other sites seem to only use the b43 for all scenarios...

[http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp)

I had the same connectivity with random disconnects before using the b43 provided by the Hardware Devices application, and after following that website.

No change in random disconnects...but it never disconnects when I'm at the laptop using it...because my every move keeps the computer in a state of being awake.

Its only once I have left it alone, that it seems to go to sleep and when it does, everything even the screen display, and the wifi led light, just freezes or pauses...and will stay that way...and my keep-alive program wont save it, cuz it has stopped doing pings, cuz its been paused.

I set it to echo the time and date of each successful ping every 60 seconds, and it would, and it would...but then when the wifi led light's state gets stuck, I know the prob is happening again, and sure enough, no more successful pings, no more failed pings being echoe'd to the screen...clock aint updating...touch the pad...everything on the display updates, then a min later a failed ping (3 mins after the last ping shown on screen - a ping should be happening every 60 seconds)...then a bubble for disconnected network...then the netman scanning, then cuz my prog did a DOWN & UP, connection.

But I shouldnt have to be here to wake it from sleep.  There is no setting in the BIOS for this.

Someone must have an idea where to look?!

---

### Post by SanjoEel on 2010-04-24
Thanks this is a great solution!!:guitar:

---

### Post by Canada Lee on 2010-04-25
Well, I found a way to prevent my broadcom from disconnecting at random intervals...

You know when you watch a movie, it prevents the screensaver from starting while your watching the movie...it must be preventing the INACTIVITY timer from tripping...

Thats one way...or another way, less cpu intensive, is to play a MP3 with rhythmbox...set the volume low and have it repeat...

My keep-alive program, thats why I tried echoing successful pings every minute, to show Ubuntu there is a program active, and sending info to the screen...but that didnt stop the INACTIVITY timer I guess...

So now I can file a bug report, but against what PROCESS?  The inactivity timer?

---

### Post by dushy4 on 2010-04-30
> **nallen00 said:**
> Broadcom hardware only.  Credit to respective solution providers included below.  Feel free to chime in if I've missed something.

[SIZE=4]**  Broadcom BCM4311/12/21/22 Hardware (STA driver):**[/SIZE]
[SIZE=1]_**NOTE**_: ASSUMES FRESH INSTALL. FOR LAPTOPS,[/SIZE][SIZE=1] ONCE THE SYSTEM REBOOTS AFTER INSTALL,[/SIZE][SIZE=1] REBOOT AGAIN
AND TOGGLE THE WIRELESS BUTTON *(YES,*[/SIZE][SIZE=1]* IT COULD BE THAT EASY).*[/SIZE]

Plug into the network via cable:

[LIST=1]
[*][SIZE=2]**  IF WIRED CONNECTION WORKS:**[/SIZE]
[LIST=1]
[*]Open System -> Admin -> Update Manager
[*]Check for updates, install, and reboot
[*]After reboot, open System -> Admin -> Hardware Drivers
[*]Look for "Broadcom STA wireless driver";
[LIST=1]
[*]_[SIZE=1]IF DRIVER IS PRESENT *AND *ACTIVATED:[/SIZE]_
[LIST=1]
[*]  Remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "bcmwl-kernel-source" *(if not available, move to step 2)*
[/LIST]

[LIST=1]
[*]Right-click and mark for installation
[*] Apply changes and reboot.
[*]Repeat steps 1.3-1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]**[SIZE=2]IF WIRED CONNECTION DOES NOT WORK:[/SIZE]**
[LIST=1]
[*]From **LiveCD ***(solution provided by jomtois [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288865") - edited for clarity):*
[LIST=1]
[*]Open Sytem -> Admin -> Synaptic Package Mgr
[*]Ensure 9.10 LiveCD is in the drive
[*]In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
[*]Check "Installable from CD-ROM/DVD" and close
[*]Reload *(disregard connectivity errors)*
[*]Search for "bcmwl-kernel-source"
[*]Right-click and mark for installation
[*]Apply changes and reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 **  [SIZE=4]Broadcom BCM4301/03/06/09 Hardware (B43 driver):[/SIZE]**
[SIZE=1]_**NOTE**_: IF YOUR CARD IS A BCM4306 REV 2, OR ONLY HAS 802.11B CAPABILITY, IT USES
B43LEGACY. ALL OTHER MODELS USE B43. THE STEPS BELOW WILL BUILD BOTH B43 AND
B43LEGACY (AND GET FIRMWARE FOR BOTH TOO). THE KERNEL AUTOLOADER WILL
AUTOMATICALLY DO THE RIGHT THING AND LOAD THE CORRECT DRIVER FOR YOUR DEVICE.
ADDITIONAL INFO [[COLOR=Red]HERE[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43"). ASSUMES FRESH INSTALL.  FOR LAPTOPS, ONCE THE SYSTEM REBOOTS
AFTER INSTALL, REBOOT AGAIN AND TOGGLE THE WIRELESS BUTTON (YES, IT COULD BE THAT
EASY).[/SIZE]

Plug into the network via cable:[SIZE=1]
[/SIZE]
[LIST=1]
[*][SIZE=2]**  IF WIRED CONNECTION WORKS:**[/SIZE]
[LIST=1]
[*]Open System -> Admin -> Update Manager
[*]Check for updates, install, and reboot
[*]After reboot, open System -> Admin -> Hardware Drivers
[*]Look for "Broadcom B43 wireless driver";
[LIST=1]
[*]_[SIZE=1]IF DRIVER IS PRESENT *AND *ACTIVATED:[/SIZE]_
[LIST=1]
[*]  Remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log into network.
[/LIST]
 
[*]_[SIZE=1]IF DRIVER IS NOT PRESENT:[/SIZE]_
[LIST=1]
[*]Open System -> Admin -> Synaptic Pkg Mgr
[*]Search for "b43-fwcutter" *(if not available, move to step 2)*
[*]Right-click and mark for installation
[*] Apply changes *(answer yes when asked "Fetch and install firmware?")*
[*]Reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]**[SIZE=2]IF WIRED CONNECTION DOES NOT WORK:[/SIZE]**
[LIST=1]
[*]From **LiveCD ***(based on solution provided by jomtois [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288865") - edited for clarity):*
[LIST=1]
[*]Open Sytem -> Admin -> Synaptic Package Mgr
[*]Ensure 9.10 LiveCD is in the drive
[*]In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
[*]Check "Installable from CD-ROM/DVD" and close
[*]Reload *(disregard connectivity errors)*
[*]Search for "b43-fwcutter"
[*]Right-click and mark for installation
[*]Apply changes *(answer yes when asked "Fetch and install firmware?")*
[*]Reboot
[*]Repeat steps 1.3 thru 1.4.2
[/LIST]
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]
 
[/LIST]
[B][SIZE=4]Transfer Files from Another Computer
[/SIZE][/B][SIZE=1]_**NOTE**_:  IF NECESSARY, THE STA AND B43 PACKAGES CAN BE
DOWNLOADED USING THE LINKS BELOW.  BE SURE TO INCLUDE THE
APPROPRIATE DEPENDENCIES.
[/SIZE]
_STA Driver Source_
[[COLOR=Red]http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source[/COLOR]]("http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source")

_B43 Driver Source_
[[COLOR=Red]http://packages.ubuntu.com/karmic/b43-fwcutter[/COLOR]]("http://packages.ubuntu.com/karmic/b43-fwcutter")[SIZE=1]
[/SIZE]
Cheers.[SIZE=1]
[/SIZE]

:):):):) thanks a lot dear,,,,,,, i tried to activate drivers for my lenovo s10 2 2-3 onths back. i dont see this page and after days of hassle,i failed. today i come across your post,,,do exactly as you said and finally,,,,,,,,wifi works.

(though while insalling bcmwl-kernel-source it failed to get 3 packages which i installed manually).

thanks a ton again,,,,,,,,

---

### Post by Robohawk on 2010-05-08
When I try to activate the driver, I get an error that reads:
System Error: installArchives() failed

I am using Ubuntu 9.10 and Broadcom Corporation BCM4312 802.11b/g (rev 01)

Thanks in advance!

---

### Post by Kafubie on 2010-05-08
This need to be updated.  Unless it is the same for Lynx.

---

### Post by Canada Lee on 2010-06-09
This is an update about the random disconnects, in case this can benefit anyone else.

I thought it might have been the network manager periodically scanning to see what available wifi is in the area, and it randomly hanging...like when it sends a command to scan for avail wifi, it hangs, or maybe waiting for a response, it waits forever.

But I doubt that is the issue.

So far since I diagnosed my problem and solved it by playing a MP3 forever using rhythmnbox, my prob has stayed in the closet and has never shown its face.  So thats a few months of it being suppressed.

I recently connected to my net using the ethernet cable, and turned off my wifi radio, as well as right clicking on Network Manager and turning off Enable Wireless.

Being as I was using ethernet, and all wireless was off, I thought, HEY I should be able to QUIT rhythmnbox now...I dont need to keep the wifi AWAKE...

Surely enough, minutes later everything was sleeping...the little led light by the ethernet cable was lit solid...and the display was showing a still image of what was displayed last when it WAS awake.  Swiped my finger cross the touchpad...and immediately the display updated...this confirmed my suspicion that it was sleeping...then the ethernet light starts flashing...I watch the display and all the speed counters are dropping to ZERO...then a couple of minutes it starts making connections and the speed counters start increasing...

So, this random disconnects of mine, due to some kind of inactivity timer is not the BROADCOM driver...I thought the broadcom driver might have been written to be power saving or something...But when I right click on Network Manager and click on Connection Information, it shows the ETH0 connector using a different driver, not a broadcom one...

So this prob is either some kinda power savings mode, or inactivity for all communications.  Not just broadcom, not just wifi...  A little more system wide than that.

In my Ubuntu, I have turned off all forms of power savings I can find...spin down drives...turn of monitor...suspend etc etc.

And being a laptop, it may be a part of the BIOS.  I have flashed the BIOS with the latest available from the Acer website.  And going into the BIOS settings, there are no ACPI or power savings settings anywhere.  So they do not allow you to change them.

Playing an MP3 repeatedly keeps the system awake when using the ethernet as well...so I am still forced to play a MP3 to solve my prob whether I use wireless or wired.

Ubuntu may not even have any control over this problem if its embedded inside the BIOS itself.

Hope this helps someone.

---

### Post by WylieE on 2010-06-09
> **nallen00 said:**
> Broadcom hardware only.  Credit to respective solution providers included below.  Feel free to chime in if I've missed something.
 
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]


Thank you, still don't have anything up and running.  I'd like to try from a LiveUSB.  Will someone explain "navigate to pool -> main -> d -> dkms"
is this in Synaptic or am I missing something with the liveUSB I created?
I created it with UNetbootin (because I had problems with the USB creator).
THanks for any advice

---

### Post by StaRetji on 2010-06-15
Yep, would also need explanation on how to make it work on
Ubuntu Netbook Lucid Linx LiveUSB stick with permanent storage.

Thx in advance!

---

### Post by nallen00 on 2010-06-25
Thanks for your feedback, everyone.  I will be updating the OP this evening to cover a couple procedural details I've encountered, which should help with some of the issues mentioned here.  Also 100% success w/ several different machines on Lucid...

Nate

---

### Post by JosephBus on 2010-07-05
Thx 4 Ur advice on loading broadcom driver...
My problem: 
      Network Manager displays only Desktop & "Windows Network" (Is that x11?)...
      LAPTOP DOES NOT APPEAR...Wireless is disabled...Wired Networking 'Auto eth0'   active...
 
My laptop  (Hp Pavilion dv7 w/ Broadcom STA Network Ctrlr BCM 4312 802.11b/g is ACTIVATED & in use...)

Thank You for Ur consideration...ANY Thoughts appreciated...JosephBus@gmail.com

---

### Post by lvshankar on 2010-07-11
I have 4312 and Broadcom STA wireless driver is available but not activated.

When I try to activate it, I get an error. Please check the log. I've checked /etc/modprobe.d/<all blacklist files> and everything related to b43. The log says its been blacklisted. Any help?

---

### Post by paras301 on 2010-07-12
Hello Nathan,

> 

[LIST=1]
[*]_[SIZE=1]IF DRIVER IS  PRESENT BUT *NOT *ACTIVATED:[/SIZE]_
[LIST=1]
[*]Activate and reboot;
[*]After reboot, remove network cable, toggle wireless button, and log  into network.
[/LIST]
[/LIST]


I am in this situation, but I am not able to find out how to activate it. It shows everything fine, but still its not working. Here are some of things that might help you to find the insight of my problem - 

```


paras@ubuntu:~$ sudo lshw -C network
[sudo] password for paras: 
  *-network DISABLED      
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: f0:7b:cb:7f:a6:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:22:0a:15
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.18 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:35 memory:f0800000-f080ffff
paras@ubuntu:~$ 
paras@ubuntu:~$ 
paras@ubuntu:~$ lsmod|grep -e b43 -e ssb -e wl
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
paras@ubuntu:~$ 
paras@ubuntu:~$ 
paras@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.


```

Thank you

---

### Post by yaaarrrgg on 2010-07-13
> **paras301 said:**
>  
  *-network DISABLED      
       

I noticed this advice on another thread, I wonder if it could be the issue?

> 
... make sure your card is turned on. Laptops with built-in wifi usually have a key combination (most often fn+F2), check your manual. If you are not using a mobile computer, check your BIOS to see if you need to enable detection of PCI devices. You can enter the BIOS of your computer by pressing a button as it boots up, and the machine will tell you which button(s) to use. You will only have a second or two to see what you need to press. Most computers use one of the following keys to enter BIOS: ESC, DEL, F1, F2, F10. Just have a look through your BIOS, but heed this warning! Don't change anything unless you know what you are doing! Mess this up and you could be left with an unbootable computer! If this happens all is not lost though. Just hard reset your machine, enter BIOS, and find the option to reset BIOS to factory defaults and that will fix your problem.


from: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by paras301 on 2010-07-13
There is a network toggle switch at the top of my laptop. I tried toggling it, but it does not work with Ubuntu and wireless network is always off.

Regarding BIOS, i have checked that too. Its all enable at boot time in BIOS, so not sure of problem at all.

Thanks

---

### Post by TheBoz on 2010-07-21
This is a busy thread and I wanted to post my 2¢ for anyone who happens to run across this in their own search. I searched endless posts and other sites for a fix, but it ended up being quite simple.

The Dell Latitude D830 laptop I have shows the wifi driver as a "Dell Wireless 1505 Draft..." When I booted Ubuntu 10.04 and run LSPCI in a terminal, it comes back with

Broadcom BCM4328 802.11a/b/g/n (rev 03)

Didn't load drivers for the wifi hardware on install. So, the solution for me was to hook it up to a wired connection, run the update manager (System --> Administration --> Update Manager) and get the latest drivers and other installables.

Upon reboot, the wifi card was recognized and I was able to connect to the network.

Hope this helps someone.

---

### Post by help help help on 2010-07-21
I'm about to pull my hair out.  I have a old Dell Mini 9 and put the new version of Linux Netbook on it.  No Wireless .....

where do I get a driver ? 

what else do I need to do ? 

It works with a network cable but not with the wireless. I hate to go back to XP 



Please Help

---

### Post by gawy on 2010-09-02
> **Robohawk said:**
> When I try to activate the driver, I get an error that reads:
System Error: installArchives() failed

I am using Ubuntu 9.10 and Broadcom Corporation BCM4312 802.11b/g (rev 01)

Thanks in advance!

I solved this problem by installing the bcmwl-kernel-source driver through apt-get instead. (Also installed the broadcom-sta-common, don't think that is necessary though).

---

### Post by Orin on 2010-09-02
Resolved my issue on HP Mini 210. Thanks a lot for the guide!

---

### Post by lavendergoons on 2010-10-02
I have Broadcom BCM 4312 on Ubuntu 10.04. Do these same steps apply to 10.04??
If they do then everything was working fine in step 2 until I got to number 5 when I tried to reload. Then it tried to download something and an error ocurred saying it "Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg). Could not resolve 'ie.archive.ubuntu.com' "
And there are a few others just like that.

Just to note that I am also running as a totally separate OS Windows 7 which the wireless works perfectly on.

---

### Post by rifter on 2010-10-02
> **lavendergoons said:**
> I have Broadcom BCM 4312 on Ubuntu 10.04. Do these same steps apply to 10.04??
If they do then everything was working fine in step 2 until I got to number 5 when I tried to reload. Then it tried to download something and an error ocurred saying it "Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg). Could not resolve 'ie.archive.ubuntu.com' "
And there are a few others just like that.

Just to note that I am also running as a totally separate OS Windows 7 which the wireless works perfectly on.

Use us.archive.ubuntu.com instead and see if that helps.

---

### Post by Doobster1 on 2010-11-04
Dell Inspiron mini 10 wireless and wired will no connect to the internet.  I have followed all of these instruction here and these:


[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

 					Originally Posted by **jomtois** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8090292#post8090292") 				
 				[I]Perhaps this will help someone out there.

I was using Jaunty fine on my laptop (Dell e1705) with wireless working.   I installed 9.10 beta and could not get it to work.  In jaunty I was  using the Broadcom Wireless driver that showed up in System >  Administration > Hardware drivers.  

When I installed 9.10 as a fresh install from the live cd, it would list  only the Broadcom Wireless driver.  I kept choosing "Activate" and  entering my password, but it would never activate.  Having no network  connectivity, I was unable get any updates.

However this worked for me:

1) Open Synaptic Pacakage Manager
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh 
6) Search for "bcmwl-kernel-source"
7) Mark for installation
:cool: Install it
9) Reboot computer

That worked for me.  It was activated Hardware Drivers now.  Also, after  doing this (I think because dkms installed with it) now the graphics  drivers appeared in the Hardware Drivers scan, which hadn't before.

Basically, installing bcmwl-kernel-source was the key to success for me.  Handily, it is on the livecd.

Jon[/I]
 			 		 	 	 I had similar issues, and resolved them exactly how you did. My  wireless used to work out-of-the-box, but with 9.10 its never worked  unless I've manually installed that package.

When I go to install the BCMWL even from a pen drive, it fails looking for a CD.  I plugged in a portable HP CD drive and it doesn't even see the drive.  I am brand new to Ubuntu so I am pretty clueless... Please advise me what else I can do...

Thanks,
Bob

---

### Post by smuthavarapu on 2011-01-08
Thanks to First Post @ [nallen00]("http://ubuntuforums.org/member.php?u=500158")

The Live USB(10.10) Solution worked for me in Natty Nahrwal 11.04 Acer Aspire 4720z Wireless , Kernal 2.6.37-12

[LIST=1]
[*]From **LiveUSB**:
[LIST=1]
[*]Navigate to pool -> main -> d -> dkms
[*]Run "dkms_2.1.0.1-0ubuntu1_all.deb"
[*]Navigate to pool -> restricted -> b -> bcmwl
[*]Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
[*]Reboot
[*]Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
[/LIST]
 
[/LIST]

---

### Post by jchw on 2011-01-24
> **gawy said:**
> I solved this problem by installing the bcmwl-kernel-source driver through apt-get instead. (Also installed the broadcom-sta-common, don't think that is necessary though).

I have the same problem but I do not understand what apt-get is. Can someone explain in easy steps how to do this?

---

### Post by jchw on 2011-01-26
I found a solution to this in Bug no 651010 post 3 by Kontza.

"
                 Had the same problem, then I noticed that instead of  firmware-b43-installer I had to install (manually, via synaptic)  firmware-b43-lpphy-installer.  My install is a x64-version via netboot,  i.e. mini.iso. Just the other  day when I tried x86 netbook live-cd, it  managed succesfully to  automatically set up my wireless.
 I would still keep this as a valid bug, since the system couldn't automatically resolve this."


This has solved both my DVD and wifi problems in one simple fix. Wow what a relief. Thanks Kontza.

---

### Post by teamanx on 2011-10-02
For those having the issue with connection dropping ramdomly, it looks like it is some kind of problem with power management (looks like the card is turned off when the machine has low processor load). The solution is to turn power management off for the wireless card, with the following commands:
```
sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf
```

That's way more elegant than having a mp3 playing all the time. Got the solution from Arch Linux Forums ([https://bbs.archlinux.org/viewtopic.php?id=96560](https://bbs.archlinux.org/viewtopic.php?id=96560))

Regards.

---

