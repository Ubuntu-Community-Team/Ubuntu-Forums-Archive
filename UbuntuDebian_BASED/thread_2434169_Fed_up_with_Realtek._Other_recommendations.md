---
title: "Fed up with Realtek. Other recommendations?"
date: 2019-12-31
forum: Ubuntu/Debian BASED
---

### Post by inappropriate on 2019-12-31
I have tried unsuccessfully for many hours trying to get wifi on my laptop with the realtek RTL8111/8168/8411. I'm at the point of just replacing it with a Linux friendly alternative. Any suggestions?

P.S. When I opened up my HP Omen the wifi card was an Intel card which I don't fully understand (I was expecting a realtek brand?).

---

### Post by wildmanne39 on 2019-12-31
Hello and welcome to the forum, is it your wifi card that is not working? I suggest that you let our networking volunteers have a shot at helping you fix your issue, they are very good here, if you decide you would like help please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will probably be able to help you, if not I am sure they can also make recommendations but it is still best to see the results of the script so they know what your hardware is currently and if that is even the issue.

*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by praseodym on 2020-01-01
Realtek 8168 is a LAN card. Please run the wireless script from the sticky thread and show the outputs

---

### Post by inappropriate on 2020-01-01
Ok, see below. I'll admit I'm currently running this from Mint but it has the same error as Ubuntu. I just installed MInt to see if it would be any different or not and there is no difference.


```
########## wireless info START ##########

Report from: 01 Jan 2020 10:12 PST -0800

Booted last: 01 Jan 2020 00:00 PST -0800

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 19.2 Tina
Release:    19.2
Codename:    tina

##### kernel ############################

Linux 4.15.0-54-generic #58-Ubuntu SMP Mon Jun 24 10:55:24 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Cinnamon

##### lspci #############################

3c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 16)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8603]
    Kernel driver in use: r8168

3e:00.0 Network controller [0280]: Intel Corporation Device [8086:2723] (rev 1a)
    Subsystem: Intel Corporation Device [8086:0084]

##### lsusb #############################

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0408:5300 Quanta Computer, Inc. 
Bus 001 Device 003: ID 8087:0029 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

cfg80211              622592  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
wmi                    24576  4 hp_wmi,intel_wmi_thunderbolt,wmi_bmof,mxm_wmi

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
2: enp60s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp60s0' [IF1]> brd <MAC address>
    inet 10.0.0.130/24 brd 10.0.0.255 scope global dynamic noprefixroute enp60s0
       valid_lft 602896sec preferred_lft 602896sec
    inet6 2601:600:9e80:6770::7082/128 scope global dynamic noprefixroute 
       valid_lft 602899sec preferred_lft 602899sec
    inet6 2601:600:9e80:6770:70a8:55af:4564:c7ac/64 scope global temporary dynamic 
       valid_lft 297014sec preferred_lft 83945sec
    inet6 2601:600:9e80:6770:15be:4b94:e577:bc2e/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 297014sec preferred_lft 297014sec
    inet6 fe80::33c1:8f5e:3f55:b39e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp60s0   no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 10.0.0.1 dev enp60s0 proto dhcp metric 100 
10.0.0.0/24 dev enp60s0 proto kernel scope link src 10.0.0.130 metric 100 
169.254.0.0/16 dev enp60s0 scope link metric 1000 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search hsd1.wa.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       878     1  0 09:39 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp60s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8168
GENERAL.DRIVER-VERSION:                 8.045.08-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp60s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.5/0000:3c:00.0/net/enp60s0
GENERAL.IP-IFACE:                       enp60s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7db89575-f246-3afe-a088-f5ceac896654
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         10.0.0.130/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.0.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 10.0.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.wa.comcast.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 10.0.0.130
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 10.0.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 10.0.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[16]:                       routers = 10.0.0.1
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.wa.comcast.net
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1578505235
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = Omen
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.0.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 604800
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2601:600:9e80:6770::7082/128
IP6.ADDRESS[2]:                         2601:600:9e80:6770:70a8:55af:4564:c7ac/64
IP6.ADDRESS[3]:                         2601:600:9e80:6770:15be:4b94:e577:bc2e/64
IP6.ADDRESS[4]:                         fe80::33c1:8f5e:3f55:b39e/64
IP6.GATEWAY:                            fe80::3e7a:8aff:fe09:aefe
IP6.ROUTE[1]:                           dst = 2601:600:9e80:6770::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::3e7a:8aff:fe09:aefe, mt = 100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[6]:                           dst = 2601:600:9e80:6770::7082/128, nh = ::, mt = 100
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:47:4d:91:fe:fc:9b:9d:35:78:92:98:5f:1b:68:1c:73
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[4]:                        rebind = 483840
DHCP6.OPTION[5]:                        max_life = 604800
DHCP6.OPTION[6]:                        preferred_life = 604800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1577845396
DHCP6.OPTION[10]:                       dhcp6_status_code = success Assigned an address.
DHCP6.OPTION[11]:                       ip6_address = 2601:600:9e80:6770::7082
DHCP6.OPTION[12]:                       ip6_prefixlen = 64
DHCP6.OPTION[13]:                       renew = 302400
DHCP6.OPTION[14]:                       iaid = 6a:19:4d:0e
DHCP6.OPTION[15]:                       starts = 1577845396
DHCP6.OPTION[16]:                       dhcp6_server_id = 0:1:0:1:25:8c:b8:1b:3c:7a:8a:9:ae:fe
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7db89575-f246-3afe-a088-f5ceac896654 | Wired connection 1

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

##### Netplan config ####################

[/etc/netplan/1-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

enp60s0   no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp60s0   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-54-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C615A4309BFED95CEE6CECF
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-54-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/r8168-dkms.conf]
alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   17.194612] Bluetooth: hci0: Found device firmware: intel/ibt-20-1-3.sfi
[   18.750743] Bluetooth: hci0: Waiting for firmware download to complete
[   25.294880] IPv6: ADDRCONF(NETDEV_UP): enp60s0: link is not ready
[   25.295018] enp60s0: 0xffffb5de00079000, <MAC 'enp60s0' [IF1]>, IRQ 148
[   25.349267] IPv6: ADDRCONF(NETDEV_UP): enp60s0: link is not ready
[  103.185129] r8168: enp60s0: link up
[  103.185161] IPv6: ADDRCONF(NETDEV_CHANGE): enp60s0: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2020-01-01
Use the Update Manager and install a 5.3 kernel or you can do a dkms install of iwlwifi backports but that will only support Intel wifi
```
sudo add-apt-repository ppa:canonical-hwe-team/backport-iwlwifi
sudo apt-get update
sudo apt-get install backport-iwlwifi-dkms
```
Reboot

---

### Post by inappropriate on 2020-01-01
I upgraded the kernel to 5.0 and that did not fix it. However your manual installation did fix it. Thank you!

---

### Post by jeremy31 on 2020-01-01
I did say kernel 5.3, not 5.0 as 5.3 is the only Ubuntu kernel to support your device as the drv.c file has this entry
```
	{IWL_PCI_DEVICE(0x2723, 0x0084, iwl_ax200_cfg_cc)},
```

---

### Post by inappropriate on 2020-01-01
Yeah I saw that. Unfortunately both 5.0 and 5.3 kernels cause my laptop to not shut down due to some acpi error. I had to revert to the 4.15 kernel. However I have wifi working once doing the backport.

---

### Post by inappropriate on 2020-01-02
So for some reason the backport is not working now. All I did was install a new SSD drive to the laptop but did not do anything to the existing HDD that I was running linux on. Any ideas? Would installing a new SSD have any impact at all?

---

