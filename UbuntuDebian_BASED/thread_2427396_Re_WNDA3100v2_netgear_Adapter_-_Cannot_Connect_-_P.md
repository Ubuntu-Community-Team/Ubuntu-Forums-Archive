---
title: "Re: WNDA3100v2 netgear Adapter - Cannot Connect - POP! os"
date: 2019-09-21
forum: Ubuntu/Debian BASED
---

### Post by ianmcneill2 on 2019-09-21
Hello, I have scrounged the forums for help with this issue and I cannot seem to get my WNDA3100v2 Adapter to work with PopOs. I understand that POP and ubuntu systems are not that different from one another so I have been able to follow some other post steps to remedy this issue. 
ALL info is below, if more is  needed please let me know... I would really like to not keep using my phone to tether my desktop...


My current situation: 
```

lo        no wireless extensions.

eno1      no wireless extensions.

enp0s29u1u6  no wireless extensions.

```

I have the correct .inf installed

```

~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present


```

My system recognizes the usb.  

```

:~$ lsusb
Bus 002 Device 006: ID 04e8:6863 Samsung Electronics Co., Ltd Galaxy series, misc. (tethering mode)
Bus 002 Device 005: ID 1a2c:4324 China Resource Semico Co., Ltd 
Bus 002 Device 004: ID 1e7d:2e22 ROCCAT 
Bus 002 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1058:25fa Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

ndiswrapper info: 

```

:~$ dmesg | grep ndis
[    9.662720] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   10.004620] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   10.004803] Modules linked in: ndiswrapper(OE+) parport_pc ppdev lp parport ip_tables x_tables autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear system76_io(OE) ses enclosure scsi_transport_sas hid_generic usbhid hid uas usb_storage nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops firewire_ohci drm ahci firewire_core e1000e i2c_i801 lpc_ich libahci crc_itu_t ipmi_devintf ipmi_msghandler wmi
[   10.004857]  wrap_submit_irp+0x3a3/0x9b0 [ndiswrapper]
[   10.004869]  pdoDispatchDeviceControl+0x2d/0x70 [ndiswrapper]
[   10.004877]  win2lin_pdoDispatchDeviceControl_2+0x18/0x20 [ndiswrapper]
[   10.004884]  ? win2lin_IoInvalidDeviceRequest_2+0x20/0x20 [ndiswrapper]
[   10.004891]  lin2win2+0xd/0x20 [ndiswrapper]
[   10.004899]  ? KeReleaseSpinLock+0x56/0x60 [ndiswrapper]
[   10.004910]  IofCallDriver+0x73/0x80 [ndiswrapper]
[   10.004917]  win2lin_IofCallDriver_2+0x18/0x20 [ndiswrapper]
[   10.004925]  ? ExAllocatePoolWithTag+0x37/0x70 [ndiswrapper]
[   10.004933]  ? ExAllocatePoolWithTag+0x37/0x70 [ndiswrapper]
[   10.004940]  ? NdisAllocateMemoryWithTag+0x16/0x30 [ndiswrapper]
[   10.004949]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[   10.004958]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[   10.004966]  ? ExAllocatePoolWithTag+0x37/0x70 [ndiswrapper]
[   10.004973]  ? ExAllocatePoolWithTag+0x37/0x70 [ndiswrapper]
[   10.004981]  ? win2lin_NdisAllocateMemoryWithTag_3+0x1b/0x30 [ndiswrapper]
[   10.004989]  ? lin2win6+0x22/0x28 [ndiswrapper]
[   10.004998]  ? mp_init+0x7c/0x1f0 [ndiswrapper]
[   10.005006]  ? IoSyncForwardIrp+0x9e/0xe0 [ndiswrapper]
[   10.005014]  ? NdisDispatchPnp+0xc2/0x850 [ndiswrapper]
[   10.005026]  ? IoAllocateIrp+0x45/0x70 [ndiswrapper]
[   10.005033]  ? IoInitializeIrp+0x1e/0x50 [ndiswrapper]
[   10.005041]  ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
[   10.005048]  ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
[   10.005054]  ? win2lin_NdisDispatchDeviceControl_2+0x20/0x20 [ndiswrapper]
[   10.005061]  ? lin2win2+0xd/0x20 [ndiswrapper]
[   10.005069]  ? IofCallDriver+0x73/0x80 [ndiswrapper]
[   10.005077]  ? IoSendIrpTopDev+0xd6/0x130 [ndiswrapper]
[   10.005084]  ? wrap_pnp_start_device+0x20d/0x2d0 [ndiswrapper]
[   10.005092]  ? wrap_pnp_start_usb_device+0xd4/0xf0 [ndiswrapper]
[   10.005115]  ? loader_init+0xc2/0xe0 [ndiswrapper]
[   10.005122]  ? wrapper_init+0xa6/0x1000 [ndiswrapper]
[   10.005157] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   10.005158] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   10.005160] ndiswrapper (mp_halt:254): device 000000000fcc7faf is not initialized - not halting
[   10.005161] ndiswrapper: device eth%d removed
[   10.005181] ndiswrapper: probe of 2-1.2:1.0 failed with error -22
[   10.005954] usbcore: registered new interface driver ndiswrapper
[   11.008464] rndis_host 2-1.6:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.6, RNDIS device, b2:3f:a6:b3:f5:25
[   11.008487] usbcore: registered new interface driver rndis_host
[   11.010137] rndis_host 2-1.6:1.0 enp0s29u1u6: renamed from usb0



```

edit*

Here is a tag of the wireless-info.txt that I found from another user on the forum using code

```

wget -N -t 5 -T 10  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info  && chmod +x wireless-info && ./wireless-info 
```

```


########## wireless info START ##########

Report from: 21 Sep 2019 13:08 EDT -0400

Booted last: 21 Sep 2019 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Pop!_OS 19.04
Release:    19.04
Codename:    disco

##### kernel ############################

Linux 5.0.0-29-generic #31-Ubuntu SMP Thu Sep 12 13:05:32 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Pop

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 006: ID 04e8:6863 Samsung Electronics Co., Ltd Galaxy series, misc. (tethering mode)
Bus 002 Device 005: ID 1a2c:4324 China Resource Semico Co., Ltd 
Bus 002 Device 004: ID 1e7d:2e22 ROCCAT 
Bus 002 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1058:25fa Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

wl                   6451200  0
cfg80211              671744  1 wl
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  45056  1 asus_wmi
wmi_bmof               16384  0
mxm_wmi                16384  0
ndiswrapper           294912  0
wmi                    28672  3 asus_wmi,wmi_bmof,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
source-directory /etc/network/interfaces.d

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
3: enp0s29u1u6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s29u1u6' [IF2]> brd <MAC address>
    inet 192.168.42.8/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s29u1u6
       valid_lft 3136sec preferred_lft 3136sec
    inet6 2600:1004:b001:92ba:b5a8:5578:6e69:ff97/64 scope global temporary dynamic 
       valid_lft 602741sec preferred_lft 84254sec
    inet6 2600:1004:b001:92ba:3e32:cc15:4801:ee87/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::6e0d:e115:3a64:f5cb/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

enp0s29u1u6  no wireless extensions.

##### route #############################

default via 192.168.42.129 dev enp0s29u1u6 proto dhcp metric 100 
169.254.0.0/16 dev enp0s29u1u6 scope link metric 1000 
192.168.42.0/24 dev enp0s29u1u6 proto kernel scope link src 192.168.42.8 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1157     1  0 12:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s29u1u6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Samsung Electronics Co., Ltd
GENERAL.PRODUCT:                        Galaxy series, misc. (tethering mode)
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s29u1u6' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/net/enp0s29u1u6
GENERAL.IP-IFACE:                       enp0s29u1u6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       8334fc6b-6cd1-3c66-9ded-31b478b7b38d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.8/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[2]:                        dad_wait_time = 0
DHCP4.OPTION[3]:                        dhcp_lease_time = 3600
DHCP4.OPTION[4]:                        dhcp_message_type = 5
DHCP4.OPTION[5]:                        dhcp_rebinding_time = 3037
DHCP4.OPTION[6]:                        dhcp_renewal_time = 1687
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[9]:                        expiry = 1569088862
DHCP4.OPTION[10]:                       host_name = pop-os
DHCP4.OPTION[11]:                       ip_address = 192.168.42.8
DHCP4.OPTION[12]:                       network_number = 192.168.42.0
DHCP4.OPTION[13]:                       next_server = 192.168.42.129
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       requested_domain_search = 1
DHCP4.OPTION[18]:                       requested_host_name = 1
DHCP4.OPTION[19]:                       requested_interface_mtu = 1
DHCP4.OPTION[20]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_root_path = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_subnet_mask = 1
DHCP4.OPTION[29]:                       requested_time_offset = 1
DHCP4.OPTION[30]:                       requested_wpad = 1
DHCP4.OPTION[31]:                       routers = 192.168.42.129
DHCP4.OPTION[32]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[33]:                       vendor_encapsulated_options = ANDROID_METERED
IP6.ADDRESS[1]:                         2600:1004:b001:92ba:b5a8:5578:6e69:ff97/64
IP6.ADDRESS[2]:                         2600:1004:b001:92ba:3e32:cc15:4801:ee87/64
IP6.ADDRESS[3]:                         fe80::6e0d:e115:3a64:f5cb/64
IP6.GATEWAY:                            fe80::6859:16ff:feab:d355
IP6.ROUTE[1]:                           dst = ::/0, nh = fe80::6859:16ff:feab:d355, mt = 20100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             2001:4888:20:ff00:201:d::
IP6.DNS[2]:                             2001:4888:22:ff00:208:d::
DHCP6.OPTION[1]:                        dad_wait_time = 0
DHCP6.OPTION[2]:                        dhcp6_client_id = 0:4:78:df:ba:35:9e:a7:f1:11:27:6b:a8:8e:74:1e:ef:b7
DHCP6.OPTION[3]:                        dhcp6_fqdn = 1:6:70:6f:70:2d:6f:73:0
DHCP6.OPTION[4]:                        dhcp6_name_servers = 2001:4888:20:ff00:201:d:: 2001:4888:22:ff00:208:d::
DHCP6.OPTION[5]:                        dhcp6_server_id = 0:1:0:1:1e:ce:44:c9:62:f1:89:5b:da:5
DHCP6.OPTION[6]:                        fqdn_encoded = true
DHCP6.OPTION[7]:                        fqdn_fqdn = pop-os
DHCP6.OPTION[8]:                        fqdn_hostname = pop-os
DHCP6.OPTION[9]:                        fqdn_no_client_update = false
DHCP6.OPTION[10]:                       fqdn_server_update = true
DHCP6.OPTION[11]:                       requested_dhcp6_client_id = 1
DHCP6.OPTION[12]:                       requested_dhcp6_domain_search = 1
DHCP6.OPTION[13]:                       requested_dhcp6_name_servers = 1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8334fc6b-6cd1-3c66-9ded-31b478b7b38d | Wired connection 2

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579V Gigabit Network Connection (P8P67 Deluxe Motherboard)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               3 (limited)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

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

##### Netplan config ####################

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

enp0s29u1u6  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

enp0s29u1u6  Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/5.0.0-29-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.0.0-29-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/5.0.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F0CAF5346FF71FCE9CB198
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-29-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:22:AC:C2:
        05:CB:E9:9A:49:D6:D0:00:37:10:54:E4:CF:C2:DE:34:1C:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:9F:AA:17:1D:42:D7:C0:47:EA:EA:CD:
        48:BB:F1:D7:42:0F:28:55:54:41:38:A7:C5:F0:D3:01:E3:FD:30:2B:
        30:B6:44:9C:28:32:8A:FC:E4:95:D0:1D:D7:0F:31:58:1A:59:8F:52:
        3D:ED:6F:91:E1:34:27:D5:12:69:26:B1:1B:1D:84:E7:B8:78:FE:DE:
        02:A2:E0:E5:FC:DA:42:86:1D:58:EB:25:91:C9:27:FB:D8:48:EA:30:
        B9:EA:F8:4A:58:59:20:05:AB:83:43:06:D6:A1:46:F2:EF:BE:76:01:
        3A:67:82:0B:DE:8A:34:46:2D:90:39:52:88:B8:7F:35:6E:10:BB:2B:
        CA:16:4D:E2:69:42:1E:66:CA:BC:A2:8F:A8:7F:7D:7E:E5:29:A3:44:
        49:1A:9E:2F:EC:D3:D1:23:8A:14:9A:D3:FE:90:06:94:94:63:6F:70:
        66:0E:0D:04:87:3E:97:03:DF:E0:47:0B:37:AB:32:02:B8:50:63:51:
        EC:DB:EE:A4:C6:69:32:AA:61:FA:AB:D5:95:DA:F8:A1:3A:E5:E4:2B:
        F8:28:6D:BE:2F:9E:9F:23:B3:08:62:98:80:EB:2A:6D:56:F1:F2:39:
        4C:71:5C:1E:A2:74:82:57:2E:E4:80:17:4E:D8:C5:1A:A3:09:7E:D4:
        93:D3:F8:A5:C1:0F:A9:3B:DC:F5:C8:12:AB:1D:50:94:E3:B3:89:6D:
        52:FB:5F:67:64:98:5C:C1:26:3D:DB:8F:85:47:5A:8A:5A:1E:36:66:
        E1:B6:2A:FE:58:DC:85:BD:96:30:23:62:95:CF:17:A2:C8:4F:96:01:
        1E:16:89:DB:6F:ED:6E:86:68:DF:EF:1D:DB:81:7F:3F:09:57:26:FB:
        EB:C5:AE:0B:86:D2:F5:40:E6:99:43:BC:1C:47:1C:22:F1:1E:18:20:
        59:54:AE:C3:FF:ED:F8:E6:23:0C:09:05:2D:9B:DB:A0:C5:79:A5:12:
        D2:7C:AD:24:B1:E8:F6:63:B5:EB:23:05:8A:C3:95:C6:12:B4:94:0C:
        D8:85:20:E5:E4:9D:FE:EB:72:CB:82:F9:B1:2D:6D:17:B9:28:7F:06:
        E1:E6:45:BA:57:EF:44:62:79:55:5F:5F:36:1C:9D:7E:B4:BC:87:48:
        3B:D9:4B:9E:97:6D:94:E6:68:08:55:3A:1B:BD:0B:20:A2:28:44:6D:
        3D:D5:C1:64:B8:B8:88:3E:65:7A:F3:FF:38:D0:2E:72:26:1E:21:B0:
        E6:20:EB:AB:A6:D2:D7:9B:0A:E7:FD:C1:7E:A9:EB:50:39:D8:A5:9A:
        F9:26:22:AC:B9:72:3F:F5:5B:20:E2:2A:23:55:88:DF:03:32:D2:4A:
        F5
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/5.0.0-29-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     73BBB1664118DA7C504B31A
depends:        
retpoline:      Y
name:           ndiswrapper
vermagic:       5.0.0-29-generic SMP mod_unload 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

ndiswrapper
b43

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

[/etc/modprobe.d/system76-power.conf]
blacklist i2c_nvidia_gpu
alias i2c_nvidia_gpu off

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############

```

update:

I purged the kernel source

```

:~$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnvidia-cfg1-430 libnvidia-common-430 libnvidia-compute-430 libnvidia-compute-430:i386
  libnvidia-decode-430 libnvidia-decode-430:i386 libnvidia-encode-430
  libnvidia-encode-430:i386 libnvidia-fbc1-430 libnvidia-fbc1-430:i386 libnvidia-gl-430
  libnvidia-gl-430:i386 libnvidia-ifr1-430 libnvidia-ifr1-430:i386 nvidia-compute-utils-430
  nvidia-dkms-430 nvidia-driver-430 nvidia-kernel-common-430 nvidia-kernel-source-430
  nvidia-utils-430 xserver-xorg-video-nvidia-430
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 8,067 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 214681 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Removing all DKMS Modules
rmdir: failed to remove 'updates/dkms': Directory not empty
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.131ubuntu19.1pop1) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-29-generic
cryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries 
    nor crypto modules. If that's on purpose, you may want to uninstall the 
    'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs 
    integration and avoid this warning.
(Reading database ... 214595 files and directories currently installed.)
Purging configuration files for bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.131ubuntu19.1pop1) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-29-generic
cryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries 
    nor crypto modules. If that's on purpose, you may want to uninstall the 
    'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs 
    integration and avoid this warning.

```

performed a blacklist as per another forum post 

```

~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove '/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory

```

modprobed b43 and listed them and addressed dmesg b43:


```

:~$ sudo modprobe b43

:~$ lsmod | grep b43
b43                   413696  0
cordic                 16384  1 b43
bcma                   57344  1 b43
mac80211              806912  1 b43
ssb                    69632  1 b43
cfg80211              671744  3 wl,b43,mac80211

:~$ dmesg | grep b43


```

and did an iwconfig and still no luck...

```

:~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

enp0s29u1u6  no wireless extensions.



```

did a thing:

```

:~$ lspci -nn | grep 0280


:~$ lsusb
Bus 002 Device 006: ID 04e8:6863 Samsung Electronics Co., Ltd Galaxy series, misc. (tethering mode)
Bus 002 Device 005: ID 1a2c:4324 China Resource Semico Co., Ltd 
Bus 002 Device 004: ID 1e7d:2e22 ROCCAT 
Bus 002 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1058:25fa Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ rfkill list all


:~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

enp0s29u1u6  no wireless extensions.



```

and here is some added info.

```

:~$ arch
x86_64


```

```

:~$ ifconfig -a
eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 30:85:a9:96:4b:cd  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  memory 0xf9100000-f9120000  

enp0s29u1u6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.8  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 2600:1004:b001:92ba:b5a8:5578:6e69:ff97  prefixlen 64  scopeid 0x0<global>
        inet6 2600:1004:b001:92ba:3e32:cc15:4801:ee87  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::6e0d:e115:3a64:f5cb  prefixlen 64  scopeid 0x20<link>
        ether ee:48:66:6e:48:8d  txqueuelen 1000  (Ethernet)
        RX packets 16578  bytes 10013030 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16935  bytes 4149858 (4.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4391  bytes 445114 (445.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4391  bytes 445114 (445.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

Oh and if I do 

sudo modprobe ndiswrapper 

after starting my computer and I am not tethered, it hangs forever then when I shut down or restart my computer I get the 
Target reached shutdown but my system doesn't shut down or restart it just hangs in a perpetual loop.  

So if anyone can help me out i would deeply appreciate it. 

If it doesnt work after trying this long, I will just have to buy a linux compatible Wifi Adapter. I would really just like to use what I have that I know still works.  :)

---

### Post by jeremy31 on 2019-09-21
Moved to Ubuntu/Debian based

---

### Post by rafaelalves on 2020-02-17
I have the exact same issues... I am running 18.04.4 LTS. After searching the forum for "WNDA3100v2" I am convinced it is not going to work, ever.

---

### Post by indeedhappy80 on 2020-07-24
any updates?

---

