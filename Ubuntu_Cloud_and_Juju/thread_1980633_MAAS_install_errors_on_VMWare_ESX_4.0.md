---
title: "MAAS install errors on VMWare ESX 4.0"
date: 2012-05-15
forum: Ubuntu Cloud and Juju
---

### Post by EJJones on 2012-05-15
[SIZE=3][FONT=Calibri]I have downloaded the newest Ubuntu server iso image and have problems with setting up the cloud. Here is what has happened so far.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Using a VMWare 4.0 server as the install platform.[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]Attempt #1[/SIZE][/FONT]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]created controller on VMWare server. Install went smooth with no problems. IP address for MAAS controller was 192.168.1.9 (from network DHCP server –Endian firewall).[/FONT][/SIZE]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]Created maas superuser as per instructions. Worked correctly.[/FONT][/SIZE]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][FONT=Calibri][SIZE=3]Opened IE9 on Win7 desktop and went to MAAS page 192.168.1.9/MAAS as per instructions. Page opened correctly.[/SIZE][/FONT]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]Performed sudo maas-import-isos. Worked correctly.[/FONT][/SIZE]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]Created 2 nodes in VMWare. Installed correctly. Nodes shut down correctly.[/FONT][/SIZE]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][FONT=Calibri][SIZE=3]Opened IE9 on Win7 desktop and went to MAAS page 192.168.1.9/MAAS as per instructions. Page opened correctly.[/SIZE][/FONT]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]Attempted to “Accept and Commission” nodes. System hung on me. I had to shutdown controller and reboot.[/FONT][/SIZE]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]Could not get back to MAAS Admin page at 192.168.1.9/MAAS.[/FONT][/SIZE]
[FONT=Symbol][SIZE=3]·[/SIZE] [/FONT][SIZE=3][FONT=Calibri]Deleted all VMWare machines from disk and inventory on VMWare server and started over.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Attempt #2 through-------- several more !![/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Did all of the same as above. When I tried to open the webpage at 192.168.1.9/MAAS or any other IP address that I tried during various install attempts I would get an webpage error. If I entered just the controller IP address I would get the Apache [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]IT WORKS” but there is no content loaded for this webpage notice.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have tried this with several different IP addresses, on a bare metal machine, a different subnet on the network and with Firefox, Chrome and IE 8 and IE 9 on different desktop machines. Every attempt has provided the same response: If I entered just the controller IP address I would get the Apache IT WORKS” but there is no content loaded for this webpage notice. If I enter the ip/MAAS address I get a webpage error.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I have even re-downloaded the Ubuntu 12.04 iso image and tried all over again. Same problem.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]What am I missing?[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Thanks.:)[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Evan[/FONT][/SIZE]

---

