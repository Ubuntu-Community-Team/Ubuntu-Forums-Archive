---
title: "Lenovo U31 - 2 problem"
date: 2016-01-01
forum: Ubuntu/Debian BASED
---

### Post by strangelove2 on 2016-01-01
Hello everyone,

Just got a new laptop and made a fresh install on it. Now I have two problems with it.

1. On the terminals from 1-6 the text flashes from right to left in an extremely high speed. Completely unusable that way.

2. I can't seem to get the Wifi to work. I think it's somekind of Qualcomm adapter. Found some firmware to some adapters on git, but they all didn't work.

rfkill list seems to show the adapter, but still can't seem to get it to work.

```
rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

Googled for 2 days now and starting to lose hope.

Anyone got an idea?

Greetings,
Strangelove

Update: Found out that the Wifi adapter isn't compatible with Linux as of now. So I ordered a USB Wifi stick which is conserning to google perfectly compatible to Linux.

Still have the other problem, though. tty1-6 has the whole text output just moving extremely fast from right to left. I have now idea how to solve this. Googled a lot but couldn't find any solutions. Anyone an idea?

---

### Post by jeremy31 on 2016-01-02
What does terminal output for this command ```
lspci -nnk | grep -iA2 net
```

There have been quite a few Qualcomm chipset getting Linux support recently

---

### Post by strangelove2 on 2016-01-02
Output is:

```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3828]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]


```

---

### Post by jeremy31 on 2016-01-02
See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940/comments/75](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940/comments/75)

---

### Post by strangelove2 on 2016-01-02
Thanks for your help, I've installed the deb package from that site, but WLAN still doesn't work. I'm probably missing some steps because I'm still a beginner. Do you know what else to do?

---

### Post by jeremy31 on 2016-01-02
Open terminal and paste this command ```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]chmod +x wireless-info && ./wireless-info
```

Paste the contents of wireless-info.txt or if the file is too big it will create a wireless-info file with a .tar.gz extension[/FONT][/COLOR]

---

### Post by strangelove2 on 2016-01-02
```

########## wireless info START ##########

Report from: 03 Jan 2016 01:27 CET +0100

Booted last: 03 Jan 2016 00:44 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Kali
Description:    Kali GNU/Linux 2.0
Release:    2.0
Codename:    sana

##### kernel ############################

Linux 4.0.0-kali1-amd64 #1 SMP Debian 4.0.4-1+kali2 (2015-06-03) x86_64 unknown unknown GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

default

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3828]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 004: ID 174f:14ee Syntek 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 1038:137c SteelSeries ApS 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

snd_soc_rt286          36864  0 
ideapad_laptop         20480  0 
snd_soc_core          147456  1 snd_soc_rt286
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 
rfkill                 20480  3 ideapad_laptop,bluetooth
snd_pcm                90112  6 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:120b:2c0f:5af0:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73506761 (70.1 MiB)  TX bytes:3522682 (3.3 MiB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

search home home.
nameserver 192.168.1.1
nameserver 2a02:120b:2c0f:5af0:226:42ff:feb6:c00

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       693     1  0 00:45 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Kabelgebundene Verbindung 1
GENERAL.CON-UUID:                       0d1ae166-5198-4360-a6f7-180bdfaeed4a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0d1ae166-5198-4360-a6f7-180bdfaeed4a | Kabelgebundene Verbindung 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   f2b5bd21-ab83-46af-9273-4da1b9a94a1e | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.146/24, gw = 192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        relay_agent_information = 1:9:41:56:4d:ea:e:14:0:72:5f:2:6:<MAC 'eth0' [IF]>
DHCP4.OPTION[6]:                        ip_address = 192.168.1.146
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1451864720
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 0.0.0.0
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         ip = 2a02:120b:2c0f:5af0:<IP6 'eth0' [IF]>/64, gw = fe80::226:42ff:feb6:c00
IP6.ADDRESS[2]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = fe80::226:42ff:feb6:c00
IP6.ROUTE[1]:                           dst = 2a02:120b:2c0f:5af0::/64, nh = fe80::226:42ff:feb6:c00, mt = 1
IP6.ROUTE[2]:                           dst = 2a02:120b:2c0f:5af0:226:42ff:feb6:c00/128, nh = fe80::226:42ff:feb6:c00, mt = 0
IP6.DNS[1]:                             2a02:120b:2c0f:5af0:226:42ff:feb6:c00
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:d:6b:58:fa:6a:e3:7:fc:99:6a:60:2e:85:5b:c2:cf
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2a02:120b:2c0f:5af0:226:42ff:feb6:c00
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_domain_search = home.
DHCP6.OPTION[8]:                        dhcp6_preference = 255
DHCP6.OPTION[9]:                        dhcp6_server_id = 0:1:0:1:1d:c:6c:2d:2:26:42:b6:c:3

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/nli-03373]] (600 root)
[connection] id=nli-03373 | type=wifi
[wifi] ssid=nli-03373 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath10k-dkms.conf]
options ath10k_core skip_otp=1

[/etc/modprobe.d/blacklist-libnfc.conf]
blacklist nfc
blacklist pn533

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

[/etc/modprobe.d/rtl-sdr-blacklist.conf]
blacklist dvb_usb_rtl28xxu
blacklist e4000
blacklist rtl2832

##### rc.local ##########################

exit 0

##### pm-utils ##########################

find: `/etc/pm/*.d': No such file or directory

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.690405] r8169 0000:02:00.0: firmware: direct-loading firmware rtl_nic/rtl8168h-2.fw
[   15.706316] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   18.399933] r8169 0000:02:00.0 eth0: link up
[   21.253210] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   21.253257] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.429291] r8169 0000:02:00.0 eth0: link down
[   21.429329] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.108751] r8169 0000:02:00.0 eth0: link up
[   24.108758] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by howefield on 2016-01-03
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by arochester on 2016-01-03
Kali Linux might be "based" on Debian but it is not Debian. 

>>>[https://forums.kali.org/](https://forums.kali.org/)

---

### Post by strangelove2 on 2016-01-03
I already made a thread there before I came here, but the forum isn't really active. Or they just don't want to answer my questions. That's why I came here.

---

### Post by jeremy31 on 2016-01-03
Did you reboot after installing the deb file

---

### Post by strangelove2 on 2016-01-03
Yes, I restarted. Oh welp, I ordered a USB Wlan stick that should work.

Now I still have the problem with tty1-6 having the text moving from right to left in an extremely high speed. Any way of solving this?

---

### Post by jeremy31 on 2016-01-03
You might find something in /var/log/dmesg or /var/log/syslog that gives a hint to the issue of the text

Something to try to get your wireless going
```
sudo chattr +i /lib/firmware/ath10k/QCA6174
sudo chattr +i /etc/modprobe.d/ath10k-dkms.conf
sudo dkms remove backath10k/2.0 --all
```

reboot

This will prevent the firmware and module parameters from being deleted before *we remove the dkms from the deb I posted and then we can download newer backports and install
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
tar -zxvf backports-20151120.tar.gz
cd backports-20151120
make defconfig-ath10k
make
sudo make install
```

Reboot and hopefully things function correctly

---

### Post by strangelove2 on 2016-01-04
Unfortunately no luck with the new firmware. USB stick arrives tomorrow, though, so no sweat.

Was able to solve the problem with the tty's. Had to add ```
vga=normal nomodeset video=vesafb:off i915.modeset=0
``` to the grub.cfg menu entry. Now everything's perfect.

Thanks for your help!

---

