---
title: "DHCLIENT Not Running At Bootup"
date: 2008-06-25
forum: Server Platforms
---

### Post by Krillin on 2008-06-25
I did a broad search of dhclient, and I thought I found what I thought was a good lead here, ([http://ubuntuforums.org/showthread.php?t=799393](http://ubuntuforums.org/showthread.php?t=799393)) but the results are not the same. I tried what sounded like a good solutuon here, ([http://ubuntuforums.org/showthread.php?t=807148](http://ubuntuforums.org/showthread.php?t=807148)) after rebooting the problem still existed (see my reply #6 there).
 
To get my network an IP I have to type in a terminal. 
```
sudo dhclient
```
 
It successfully runs and I get my reserved IP and my server is on the network ready to hosts the game server(s).
 
All I did which provoked this issue was update the system via KPackage in the 'UPDATED' tab.
 
When I rebooted, this is when the dhclient quit getting it's reserved ip address from the Windows Server 2003 R2 DHCP Service.
 
For the life of me, I can not pin point why this happend. I thought it was something I done, but that was not the case. I installed and updated this system 4 times today and it all points to an 'UPDATED' package insall.
 
The system is as follows:
```
Abit AI7 MB Intel 82865PE (MCH) + 82801ER (ICH5R)
ACPI Compatible
P4 2.8a GHz Processor
2816MB of DDR3200 Memory
EVGA GF FX 5200 / 256 DDR2 Memory Onboard
Onboard 10/100 LAN (Realtec)
Onboard Sound (enabled hardware)
160GB Maxtor EIDE HDD
Sony DVD-RW/CD-RW IDE Burner
```
 
Thanks in advance,
Krillin
](*,)

---

