---
title: "No Wireles Option After Installing Distro Update"
date: 2019-02-27
forum: Ubuntu/Debian BASED
---

### Post by tylam6746 on 2019-02-27
Hello everyone. I'm a linux newbie from Hong Kong. Forgive my bad English.

In this morning, I was still able to use wireless network perfectly on  my Macbook Air(2015 ver.) Installed with Elementary OS 5.0. However,  after an update in app centre, I'm not able to use the wifi anymore.  I've tried reinstalling bcmwl-kernel-source but still. It won't work and  I'm using personal hotspot on my iPhone to connect to internet.

Here is my wireless script result.

```
########## wireless info START ##########

  

 Report from: 27 Feb 2019 17:15 HKT +0800
  
 Booted last: 27 Feb 2019 00:00 HKT +0800
  
 Script from: 22 Oct 2018 03:34 UTC +0000
  
 ##### release ###########################
  
 Distributor ID: elementary
 Description:    elementary OS 5.0 Juno
 Release:    5.0
 Codename:   juno
  
 ##### kernel ############################
  
 Linux 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
  
 Parameters: ro, quiet, splash, vt.handoff=1
  
 ##### desktop ###########################
  
 Pantheon
  
 ##### lspci #############################
  
 03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

     Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0117]
     Kernel modules: bcma
  
 ##### lsusb #############################
  
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

 Bus 001 Device 003: ID 05ac:0291 Apple, Inc. 
 Bus 001 Device 006: ID 05ac:828f Apple, Inc. 
 Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
 Bus 001 Device 008: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
 ##### PCMCIA card info ##################
  
 ##### rfkill ############################
  
 0: hci0: Bluetooth
     Soft blocked: no
     Hard blocked: no
  
 ##### secure boot #######################
  
 This system doesn't support Secure Boot
  
 ##### lsmod #############################
  
 ##### interfaces ########################
  
 [/etc/network/interfaces]
 auto lo
 iface lo inet loopback
  
 ##### ifconfig ##########################
  
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
     link/loopback <MAC address> brd <MAC address>

     inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
     inet6 ::1/128 scope host 
        valid_lft forever preferred_lft forever
 3: enp0s20u1c4i2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
     link/ether <MAC 'enp0s20u1c4i2' [IF1]> brd <MAC address>

     inet 172.20.10.3/28 brd 172.20.10.15 scope global dynamic noprefixroute enp0s20u1c4i2
        valid_lft 84889sec preferred_lft 84889sec
     inet6 fe80::218a:9aa7:1fac:6e1f/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever
  
 ##### iwconfig ##########################

  
 lo        no wireless extensions.
  
 enp0s20u1c4i2  no wireless extensions.
  
 ##### route #############################
  
 default via 172.20.10.1 dev enp0s20u1c4i2 proto dhcp metric 100 
 169.254.0.0/16 dev enp0s20u1c4i2 scope link metric 1000 
 172.20.10.0/28 dev enp0s20u1c4i2 proto kernel scope link src 172.20.10.3 metric 100 
  
 ##### resolv.conf #######################
  
 [644 root '/etc/resolv.conf']
 nameserver 127.0.0.53
  
 ##### network managers ##################
  
 Installed:
  
     NetworkManager
  
 Running:
  
 root       771     1  0 16:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
  
 ##### NetworkManager info ###############
  
 GENERAL.DEVICE:                         enp0s20u1c4i2
 GENERAL.TYPE:                           ethernet
 GENERAL.NM-TYPE:                        NMDeviceEthernet
 GENERAL.VENDOR:                         Apple Inc.
 GENERAL.PRODUCT:                        iPhone
 GENERAL.DRIVER:                         ipheth
 GENERAL.DRIVER-VERSION:                 --

 GENERAL.FIRMWARE-VERSION:               --
 GENERAL.HWADDR:                         <MAC 'enp0s20u1c4i2' [IF1]>

 GENERAL.MTU:                            1500
 GENERAL.STATE:                          100 (connected)
 GENERAL.REASON:                         0 (No reason given)
 GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:4.2/net/enp0s20u1c4i2

 GENERAL.IP-IFACE:                       enp0s20u1c4i2
 GENERAL.IS-SOFTWARE:                    no
 GENERAL.NM-MANAGED:                     yes
 GENERAL.AUTOCONNECT:                    yes
 GENERAL.FIRMWARE-MISSING:               no
 GENERAL.NM-PLUGIN-MISSING:              no
 GENERAL.PHYS-PORT-ID:                   --
 GENERAL.CONNECTION:                     Wired connection 1
 GENERAL.CON-UUID:                       b067a86d-0de9-38ea-84da-52e2d54d7bee
 GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
 GENERAL.METERED:                        no (guessed)
 CAPABILITIES.CARRIER-DETECT:            yes
 CAPABILITIES.SPEED:                     unknown
 CAPABILITIES.IS-SOFTWARE:               no
 CAPABILITIES.SRIOV:                     no
 WIRED-PROPERTIES.CARRIER:               on
 IP4.ADDRESS[1]:                         172.20.10.3/28
 IP4.GATEWAY:                            172.20.10.1
 IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.20.10.1, mt = 100
 IP4.ROUTE[2]:                           dst = 172.20.10.0/28, nh = 0.0.0.0, mt = 100
 IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
 IP4.DNS[1]:                             172.20.10.1
 DHCP4.OPTION[1]:                        expiry = 1551343806
 DHCP4.OPTION[2]:                        requested_domain_search = 1
 DHCP4.OPTION[3]:                        server_name = tzl
 DHCP4.OPTION[4]:                        requested_host_name = 1
 DHCP4.OPTION[5]:                        requested_time_offset = 1
 DHCP4.OPTION[6]:                        requested_domain_name = 1
 DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
 DHCP4.OPTION[8]:                        requested_broadcast_address = 1
 DHCP4.OPTION[9]:                        requested_netbios_scope = 1
 DHCP4.OPTION[10]:                       requested_wpad = 1
 DHCP4.OPTION[11]:                       next_server = 172.20.10.1
 DHCP4.OPTION[12]:                       requested_ntp_servers = 1
 DHCP4.OPTION[13]:                       dhcp_message_type = 5
 DHCP4.OPTION[14]:                       requested_subnet_mask = 1

 DHCP4.OPTION[15]:                       dhcp_lease_time = 85536
 DHCP4.OPTION[16]:                       routers = 172.20.10.1
 DHCP4.OPTION[17]:                       ip_address = 172.20.10.3
 DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
 DHCP4.OPTION[19]:                       requested_interface_mtu = 1
 DHCP4.OPTION[20]:                       requested_static_routes = 1

 DHCP4.OPTION[21]:                       broadcast_address = 172.20.10.15
 DHCP4.OPTION[22]:                       domain_name_servers = 172.20.10.1
 DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
 DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
 DHCP4.OPTION[25]:                       requested_routers = 1
 DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.240
 DHCP4.OPTION[27]:                       network_number = 172.20.10.0
 DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.20.10.1
 IP6.ADDRESS[1]:                         fe80::218a:9aa7:1fac:6e1f/64
 IP6.GATEWAY:                            --
 IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
 IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
 IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
 CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
 CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b067a86d-0de9-38ea-84da-52e2d54d7bee | Wired connection 1
  
 GENERAL.DEVICE:                         <MAC address>

 GENERAL.TYPE:                           bt
 GENERAL.NM-TYPE:                        NMDeviceBt
 GENERAL.VENDOR:                         --
 GENERAL.PRODUCT:                        --
 GENERAL.DRIVER:                         bluez
 GENERAL.DRIVER-VERSION:                 --
 GENERAL.FIRMWARE-VERSION:               --
 GENERAL.HWADDR:                         <MAC address>

 GENERAL.MTU:                            0
 GENERAL.STATE:                          30 (disconnected)
 GENERAL.REASON:                         0 (No reason given)
 GENERAL.UDI:                            /org/bluez/hci0/dev_F0_79_60_C0_63_8C
 GENERAL.IP-IFACE:                       --
 GENERAL.IS-SOFTWARE:                    no
 GENERAL.NM-MANAGED:                     yes
 GENERAL.AUTOCONNECT:                    yes
 GENERAL.FIRMWARE-MISSING:               no
 GENERAL.NM-PLUGIN-MISSING:              no
 GENERAL.PHYS-PORT-ID:                   --

 GENERAL.CONNECTION:                     --
 GENERAL.CON-UUID:                       --
 GENERAL.CON-PATH:                       --
 GENERAL.METERED:                        unknown
 CAPABILITIES.CARRIER-DETECT:            no
 CAPABILITIES.SPEED:                     unknown

 CAPABILITIES.IS-SOFTWARE:               no
 CAPABILITIES.SRIOV:                     no
 BLUETOOTH.CAPABILITIES:                 NAP
 CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
 CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cb1d8d3b-db64-41ae-9a52-ed92fc4128e7 | tzl Network
  
 ##### NetworkManager.state ##############
  
 [main]
 NetworkingEnabled=true
 WirelessEnabled=true
 WWANEnabled=true
  
 ##### NetworkManager config #############
  
 [[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
 [connection]
 wifi.powersave = 3
  
 [[/etc/NetworkManager/NetworkManager.conf]]
 [main]
 plugins=ifupdown,keyfile
 [ifupdown]
 managed=false
 [device]
 wifi.scan-rand-mac-address=no

  
 [[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
 [main]
 dns=systemd-resolved
  
 [[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
 [keyfile]
 unmanaged-devices=*,except:type:wifi,except:type:wwan
  

 [[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
 [connectivity]
 uri=http://connectivity-check.ubuntu.com/
  
 [[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]

 [device-mac-addr-change-wifi]

 match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
 wifi.scan-rand-mac-address=no

 wifi.cloned-mac-address=preserve

 ethernet.cloned-mac-address=preserve

  
 ##### NetworkManager profiles ###########
  
 [[/etc/NetworkManager/system-connections/CityU WLAN (WPA)]] (600 root)
 [connection] id=CityU WLAN (WPA) | type=wifi | permissions=
 [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CityU WLAN (WPA)

 [ipv4] method=auto
 [ipv6] method=auto
  
 [[/etc/NetworkManager/system-connections/Family Lam]] (600 root)
 [connection] id=Family Lam | type=wifi | permissions=
 [wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Family Lam

 [ipv4] method=auto
 [ipv6] method=auto
  
 ##### Netplan config ####################
  
 [/etc/netplan/01-network-manager-all.yaml]
 network:
   version: 2
   renderer: NetworkManager
  
 ##### iw reg get ########################
  
 Region: Asia/Hong_Kong (based on set time zone)
  
 global
 country 00: DFS-UNSET
     (2402 - 2472 @ 40), (6, 20), (N/A)
     (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
     (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
     (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN

     (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
     (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
     (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
     (57240 - 63720 @ 2160), (N/A, 0), (N/A)
  
 ##### iwlist channels ###################

  
 lo        no frequency information.
  
 enp0s20u1c4i2  no frequency information.
  
 ##### iwlist scan #######################
  
 lo        Interface doesn't support scanning.
  
 enp0s20u1c4i2  Interface doesn't support scanning.
  
 ##### module infos ######################
  
 ##### module parameters #################
  
 ##### /etc/modules ######################
  
 ##### modprobe options ##################
  
 [/etc/modprobe.d/amd64-microcode-blacklist.conf]
 blacklist microcode
  
 [/etc/modprobe.d/blacklist-ath_pci.conf]
 blacklist ath_pci
  
 [/etc/modprobe.d/blacklist-bcm43.conf]
 blacklist b43
 blacklist b43legacy
 blacklist ssb
 blacklist bcm43xx
 blacklist brcm80211
 blacklist brcmfmac

 blacklist brcmsmac

 blacklist bcma
  

 [/etc/modprobe.d/blacklist.conf]
 blacklist evbug
 blacklist usbmouse
 blacklist usbkbd
 blacklist eepro100
 blacklist de4x5

 blacklist eth1394
 blacklist snd_intel8x0m
 blacklist snd_aw2
 blacklist i2c_i801
 blacklist prism54
 blacklist bcm43xx
 blacklist garmin_gps
 blacklist asus_acpi
 blacklist snd_pcsp
 blacklist pcspkr
 blacklist amd76x_edac
  
 [/etc/modprobe.d/blacklist-rare-network.conf]
 alias net-pf-3 off
 alias net-pf-6 off
 alias net-pf-9 off
 alias net-pf-11 off
 alias net-pf-12 off
 alias net-pf-19 off
 alias net-pf-21 off
 alias net-pf-36 off
  
 [/etc/modprobe.d/broadcom-sta-dkms.conf]
 blacklist b43
 blacklist b43legacy
 blacklist b44
 blacklist bcma
 blacklist brcm80211
 blacklist brcmsmac

 blacklist ssb
  
 [/etc/modprobe.d/intel-microcode-blacklist.conf]
 blacklist microcode
  
 [/etc/modprobe.d/iwlwifi.conf]
 remove iwlwifi \
 (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
 && /sbin/modprobe -r mac80211

  
 ##### rc.local ##########################
  
 ##### pm-utils ##########################
  
 ##### udev rules ########################
  
 ##### dmesg #############################
  
 [  119.073588] ipheth 1-1:4.2 enp0s20u1c4i2: renamed from eth0
 [  119.097577] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1c4i2: link is not ready (repeated 2 times)
 [  120.828268] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s20u1c4i2: link becomes ready
 [  362.353258] ipheth 1-1:4.2 enp0s20u1c4i2: renamed from eth0
 [  362.373125] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1c4i2: link is not ready (repeated 2 times)
 [  363.965563] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s20u1c4i2: link becomes ready
  

 ########## wireless info END ############
```

---

### Post by howefield on 2019-02-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

