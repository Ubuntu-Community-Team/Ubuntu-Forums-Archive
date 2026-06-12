---
title: "Ubunt u 7.10 LAMP server crashes on Ubuntu splah screen"
date: 2008-03-22
forum: Server Platforms
---

### Post by ohayle on 2008-03-22
This is a Raid-1(mirror) server using SAMBA to share files with multiply computers in my home. Ubuntu was installed and running with SAMBA serving files to all the Mac's and PCs in the house I have (5). After a power failure ,I restarted the Server , at the Ubuntu Splash screen showing the orange load status the system hangs to a black screen and a series of "y" characters on the left side of the screen. The characters continuously scrolls until I ALT+CTRL+DEL to reboot the server. I can log into the recovery mode , however cannot connect to SAMBA which seems to be loaded. My DNS is my linksys wireless router , I have two network cards and  bind SAMBA to one of the two  cards, however after the reboot the server got new IP addresses, can this be the problem? looking for help

---

### Post by ohayle on 2008-03-22
It seems to be SAMBA , which is bound to one of my network cards. I have included my log :

Mar 12 16:21:46 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 12 16:21:46 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 12 16:21:46 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 34964 seconds.
Mar 12 17:10:01 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 12 17:10:01 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 12 17:10:01 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 12 17:10:01 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 39330 seconds.
Mar 13 02:04:30 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 02:04:34 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 02:04:34 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 02:04:34 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 37091 seconds.
Mar 13 04:05:31 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 13 04:05:31 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 04:05:31 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 04:05:31 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 37223 seconds.
Mar 13 12:22:45 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 12:22:50 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 12:22:50 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 12:22:50 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 35495 seconds.
Mar 13 14:25:54 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 13 14:25:54 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 14:25:54 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 14:25:54 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 34408 seconds.
Mar 13 22:14:25 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 22:14:25 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 22:14:25 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 35267 seconds.
Mar 13 23:59:22 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 13 23:59:22 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 23:59:22 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 23:59:22 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 23:59:22 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 37366 seconds.
Mar 14 08:02:12 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 14 08:02:18 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 14 08:02:18 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 08:02:18 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 33049 seconds.
Mar 14 10:22:08 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 14 10:22:08 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 10:22:08 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 14 10:22:08 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 39606 seconds.
Mar 14 17:13:07 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 14 17:13:46 ubuntuhome last message repeated 3 times
Mar 14 17:14:49 ubuntuhome last message repeated 6 times
Mar 14 17:15:45 ubuntuhome last message repeated 3 times
Mar 14 17:16:43 ubuntuhome last message repeated 3 times
Mar 14 17:17:51 ubuntuhome last message repeated 5 times
Mar 14 17:18:41 ubuntuhome last message repeated 3 times
Mar 14 17:19:41 ubuntuhome last message repeated 4 times
Mar 14 17:20:50 ubuntuhome last message repeated 4 times
Mar 14 17:21:53 ubuntuhome last message repeated 6 times
Mar 14 17:22:52 ubuntuhome last message repeated 4 times
Mar 14 17:23:39 ubuntuhome last message repeated 4 times
Mar 14 17:24:34 ubuntuhome last message repeated 4 times
Mar 14 17:24:34 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 17:24:34 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 36312 seconds.
Mar 14 21:22:14 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 14 21:22:14 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 21:22:14 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 14 21:22:14 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 37138 seconds.
Mar 15 03:29:46 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 15 03:29:50 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 15 03:29:50 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 15 03:29:50 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 38045 seconds.
Mar 15 07:41:12 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 15 07:41:12 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 15 07:41:12 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 15 07:41:12 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 33768 seconds.
Mar 18 14:05:08 ubuntuhome dhclient: DHCPOFFER from 192.168.4.70
Mar 18 14:05:08 ubuntuhome dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Mar 18 14:05:08 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 18 14:05:08 ubuntuhome NetworkManager: <info>  starting... 
Mar 18 14:05:08 ubuntuhome dhclient: bound to 192.168.4.78 -- renewal in 41164 seconds.
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.386172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.532775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a2'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.534570] nm_hal_device_added(): New device added (hal udi is '/:
Mar 12 16:21:46 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 12 16:21:46 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 12 16:21:46 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 34964 seconds.
Mar 12 17:10:01 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 12 17:10:01 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 12 17:10:01 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 12 17:10:01 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 39330 seconds.
Mar 13 02:04:30 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 02:04:34 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 02:04:34 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 02:04:34 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 37091 seconds.
Mar 13 04:05:31 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 13 04:05:31 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 04:05:31 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 04:05:31 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 37223 seconds.
Mar 13 12:22:45 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 12:22:50 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 12:22:50 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 12:22:50 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 35495 seconds.
Mar 13 14:25:54 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 13 14:25:54 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 14:25:54 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 14:25:54 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 34408 seconds.
Mar 13 22:14:25 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 13 22:14:25 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 22:14:25 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 35267 seconds.
Mar 13 23:59:22 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 13 23:59:22 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 13 23:59:22 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 23:59:22 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 13 23:59:22 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 37366 seconds.
Mar 14 08:02:12 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 14 08:02:18 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 14 08:02:18 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 08:02:18 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 33049 seconds.
Mar 14 10:22:08 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 14 10:22:08 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 10:22:08 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
:
Mar 14 10:22:08 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 39606 seconds.
Mar 14 17:13:07 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 14 17:13:46 ubuntuhome last message repeated 3 times
Mar 14 17:14:49 ubuntuhome last message repeated 6 times
Mar 14 17:15:45 ubuntuhome last message repeated 3 times
Mar 14 17:16:43 ubuntuhome last message repeated 3 times
Mar 14 17:17:51 ubuntuhome last message repeated 5 times
Mar 14 17:18:41 ubuntuhome last message repeated 3 times
Mar 14 17:19:41 ubuntuhome last message repeated 4 times
Mar 14 17:20:50 ubuntuhome last message repeated 4 times
Mar 14 17:21:53 ubuntuhome last message repeated 6 times
Mar 14 17:22:52 ubuntuhome last message repeated 4 times
Mar 14 17:23:39 ubuntuhome last message repeated 4 times
Mar 14 17:24:34 ubuntuhome last message repeated 4 times
Mar 14 17:24:34 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 17:24:34 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 36312 seconds.
Mar 14 21:22:14 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 14 21:22:14 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 14 21:22:14 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 14 21:22:14 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 37138 seconds.
Mar 15 03:29:46 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 15 03:29:50 ubuntuhome dhclient: DHCPREQUEST on eth1 to 192.168.4.70 port 67
Mar 15 03:29:50 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 15 03:29:50 ubuntuhome dhclient: bound to 192.168.4.75 -- renewal in 38045 seconds.
Mar 15 07:41:12 ubuntuhome dhclient: DHCPREQUEST on eth0 to 192.168.4.70 port 67
Mar 15 07:41:12 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 15 07:41:12 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 15 07:41:12 ubuntuhome dhclient: bound to 192.168.4.74 -- renewal in 33768 seconds.
Mar 18 14:05:08 ubuntuhome dhclient: DHCPOFFER from 192.168.4.70
Mar 18 14:05:08 ubuntuhome dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Mar 18 14:05:08 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 18 14:05:08 ubuntuhome NetworkManager: <info>  starting... 
Mar 18 14:05:08 ubuntuhome dhclient: bound to 192.168.4.78 -- renewal in 41164 seconds.
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.386172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.532775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a2'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.534570] nm_hal_device_added(): New device added (hal udi is '/:
org/freedesktop/Hal/devices/pci_8086_2834'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.535669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.535964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.536233] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2835'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.536498] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.536761] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.537020] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283a'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.537276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.537532] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.537791] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283f'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.538088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2841'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.538350] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4364'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.538615] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2843'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.540368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.540647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.540912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_scsi_device_lun0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.541179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.541439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_0_scsi_device_lun0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.541723] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_0'). 
Mar 18 14:05:08 ubuntuhome NetworkManager: <debug> [1205863508.541994] nm_hal_device_added(): New device added (hal udi is '/:
Mar 22 12:58:03 ubuntuhome NetworkManager: <info>  starting... 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.641380] nm_hal_device_added(): New device added (hal udi is '/
org/freedesktop/Hal/devices/pci_8086_29a0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.759227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_29a2'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.761277] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2834'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.762407] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.762758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.763093] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2835'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.763433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.763978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.764315] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283a'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.764645] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.764981] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.795053] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283f'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.798131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2841'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.798502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_11ab_4364'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.798834] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2843'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.799156] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.799478] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.799840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_scsi_device_lun0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.800176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_197b_2363_scsi_host_0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.800545] nm_hal_device_added(): New device added (hal uorg/freedesktop/Hal/devices/acpi_CPU0'). 
Mar 22 12:58:03 ubuntuhome NetworkManager: <debug> [1206205083.945691] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_A__DH20A3P'). 
Mar 22 12:58:04 ubuntuhome mysqld_safe[5125]: started
Mar 22 12:58:04 ubuntuhome dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Mar 22 12:58:05 ubuntuhome mysqld[5128]: 080322 12:58:05  InnoDB: Started; log sequence number 0 43655
Mar 22 12:58:05 ubuntuhome mysqld[5128]: 080322 12:58:05 [Note] /usr/sbin/mysqld: ready for connections.
Mar 22 12:58:05 ubuntuhome mysqld[5128]: Version: '5.0.45-Debian_1ubuntu3.1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Mar 22 12:58:05 ubuntuhome /etc/mysql/debian-start[5163]: Upgrading MySQL tables if necessary.
Mar 22 12:58:05 ubuntuhome dhclient: DHCPOFFER from 192.168.4.70
Mar 22 12:58:05 ubuntuhome dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Mar 22 12:58:05 ubuntuhome dhclient: DHCPACK from 192.168.4.70
Mar 22 12:58:05 ubuntuhome dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Mar 22 12:58:05 ubuntuhome dhclient: bound to 192.168.4.80 -- renewal in 42064 seconds.
Mar 22 12:58:05 ubuntuhome /etc/mysql/debian-start[5168]: Looking for 'mysql' in: /usr/bin/mysql
Mar 22 12:58:05 ubuntuhome /etc/mysql/debian-start[5168]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Mar 22 12:58:05 ubuntuhome /etc/mysql/debian-start[5168]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Mar 22 12:58:05 ubuntuhome /etc/mysql/debian-start[5253]: Checking for insecure root accounts.
Mar 22 12:58:05 ubuntuhome /etc/mysql/debian-start[5261]: Checking for crashed MySQL tables.
Mar 22 12:58:06 ubuntuhome ntpdate[5228]: adjust time server 91.189.94.4 offset -0.000496 sec
Mar 22 13:54:04 ubuntuhome init: tty4 main process (4488) killed by TERM signal
Mar 22 13:54:04 ubuntuhome init: tty5 main process (4489) killed by TERM signal
Mar 22 13:54:04 ubuntuhome init: rc2 main process (4490) killed by TERM signal
Mar 22 13:54:04 ubuntuhome init: tty2 main process (4491) killed by TERM signal
Mar 22 13:54:04 ubuntuhome init: tty3 main process (4493) killed by TERM signal
Mar 22 13:54:04 ubuntuhome init: tty1 main process (4495) killed by TERM signal
Mar 22 13:54:04 ubuntuhome init: tty6 main process (4496) killed by TERM signal
Mar 22 13:54:06 ubuntuhome init: control-alt-delete respawning too fast, stopped
Mar 22 13:54:06 ubuntuhome last message repeated 5 times
Mar 22 13:54:08 ubuntuhome mysqld[5128]: 080322 13:54:08 [Note] /usr/sbin/mysqld: Normal shutdown
Mar 22 13:54:08 ubuntuhome mysqld[5128]: 
Mar 22 13:54:08 ubuntuhome mysqld[5128]: 080322 13:54:08  InnoDB: Starting shutdown...
Mar 22 13:54:11 ubuntuhome mysqld[5128]: 080322 13:54:11  InnoDB: Shutdown completed; log sequence number 0 43655
Mar 22 13:54:11 ubuntuhome mysqld[5128]: 080322 13:54:11 [Note] /usr/sbin/mysqld: Shutdown complete
Mar 22 13:54:11 ubuntuhome mysqld[5128]: 
Mar 22 13:54:11 ubuntuhome mysqld_safe[5555]: ended
di is '/:

This is my log for network activity. I am assuming SAMBA config file need to change , however how do I dynamic assign the card for samba or do I need static IPs for the server. Need some advise and help on setting this up to work even after a DNS release and renewal

---

