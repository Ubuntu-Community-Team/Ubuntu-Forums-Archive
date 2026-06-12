---
title: "wifi card note detected"
date: 2020-05-09
forum: Ubuntu Development Version
---

### Post by joaompr on 2020-05-09
Hi all, I dis an upgrade from 20.04 to 20.10 and my wifi card isn't detected. What can I do? 
Thanks

---

### Post by wildmanne39 on 2020-05-09
Hi, you do know that 20.10 is just for testing right? if you want a more stable version of Ubuntu you should use 18.04 or 20.04.

Please click on the wireless script in my signature and post the results here and someone should be able to help.

---

### Post by zebra2 on 2020-05-09
Greetings People!
zebra here dual booting Windows 10 and Ubuntu 20.10 on a legacy bios.

speed/min/max: 2301/400/2300 MHz Kernel: 5.4.0-29-generic x86_64 
Up: 3d 14h 15m Mem: 1378.0/11856.1 MiB (11.6%) 
Storage: 931.51 GiB (7.5% used) Procs: 200 Shell: bash 5.0.16 inxi: 3.1.00 
zebra2@zebra2-Lenovo-ideapad-110-15ISK:~$ inxi1
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Groovy Gorilla (development branch)
Release:	20.10
Codename:	groovy
inxi -Sxx
System:
  Host: zebra2-Lenovo-ideapad-110-15ISK Kernel: 5.4.0-29-generic x86_64 
  bits: 64 compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.1 wm: gnome-shell 
  dm: GDM3 Distro: Ubuntu 20.10 (Groovy Gorilla) 
$DESKTOP_SESSION
ubuntu-wayland
$XDG_SESSION_TYPE
wayland
GNOME Shell 3.36.1
Version: 3.36.2-1ubuntu1
Version: 3.36.1-5ubuntu2
loginctl type
Type=wayland


Regarding the Wifi card. It may help to boot a 20.10 startup disk and see if it can get wifi. My experience so far is that focal to groovy can cause hardware issues. No harm in giving it a try.  Don't know your setup so can't say much else.

---

### Post by joaompr on 2020-05-10
yes I know it's still in development, but I like to test, doing this I may help others. I'll run the script and post result here
Thanks!

```


########## wireless info START ##########

Report from: 10 May 2020 12:36 WEST +0100

Booted last: 10 May 2020 00:00 WEST +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu Groovy Gorilla (development branch)
Release:    20.10
Codename:    groovy

##### kernel ############################

Linux 5.4.0-30-generic #34-Ubuntu SMP Tue May 5 10:44:55 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: NAMI
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:80cb]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. Root Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. BCM43142A0 Bluetooth 4.0
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. Root Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    32768  2 hp_wmi,wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.0.102/24 brd 192.168.0.255 scope global dynamic noprefixroute enp3s0
       valid_lft 603390sec preferred_lft 603390sec
    inet6 fe80::d506:a9c2:420f:e5db/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp3s0 proto dhcp metric 100 
169.254.0.0/16 dev enp3s0 scope link metric 1000 
192.168.0.0/24 dev enp3s0 proto kernel scope link src 192.168.0.102 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search VodafoneMobile.wifi

##### network managers ##################

Installed:

    NetworkManager

Running:

root         735       1  0 12:13 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0047056f-a01d-3849-8188-d56c4643bf99
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.102/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          VodafoneMobile.wifi
DHCP4.OPTION[1]:                        dhcp_lease_time = 604800
DHCP4.OPTION[2]:                        domain_name = VodafoneMobile.wifi
DHCP4.OPTION[3]:                        domain_name_servers = 192.168.0.1 192.168.0.1
DHCP4.OPTION[4]:                        expiry = 1589714008
DHCP4.OPTION[5]:                        ip_address = 192.168.0.102
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        requested_domain_name_servers = 1
DHCP4.OPTION[9]:                        requested_domain_search = 1
DHCP4.OPTION[10]:                       requested_host_name = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[13]:                       requested_nis_domain = 1
DHCP4.OPTION[14]:                       requested_nis_servers = 1
DHCP4.OPTION[15]:                       requested_ntp_servers = 1
DHCP4.OPTION[16]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_root_path = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       requested_subnet_mask = 1
DHCP4.OPTION[21]:                       requested_time_offset = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       routers = 192.168.0.1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::d506:a9c2:420f:e5db/64
IP6.GATEWAY:                            fe80::529f:27ff:fe72:9b5a
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::529f:27ff:fe72:9b5a, mt = 20100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::529f:27ff:fe72:9b5a
DHCP6.OPTION[1]:                        dhcp6_name_servers = fe80::529f:27ff:fe72:9b5a
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/5
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0047056f-a01d-3849-8188-d56c4643bf99 | Wired connection 1

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

[[/etc/NetworkManager/system-connections/NetBoa.nmconnection]] (600 root)
[connection] id=NetBoa | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=NetBoa
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sabonete.nmconnection]] (600 root)
[connection] id=sabonete | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=sabonete
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Casa.nmconnection]] (600 root)
[connection] id=Casa | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Casa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/saboneteExt.nmconnection]] (600 root)
[connection] id=saboneteExt | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=saboneteExt
[ipv4] method=manual
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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

enp3s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   22.999883] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0a5c-216d.hcd failed with error -2
[   22.999891] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-0a5c-216d.hcd not found
[   48.490164] r8169 0000:03:00.0 enp3s0: Link is Down
[   49.964915] r8169 0000:03:00.0 enp3s0: Link is Up - 100Mbps/Full - flow control rx/tx
[   49.964941] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############



```

---

### Post by CelticWarrior on 2020-05-10
Please check this instructions for Broadcom chips: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by wildmanne39 on 2020-05-10
The driver is not loaded, please do:
```
sudo modprobe wl
```
does wifi come on? if not do:
```
sudo apt install --reinstall bcmwl-kernel-source
```
if you do not already have the kernel headers installed you will need to do:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms 
```
then run the previous command, after all commands complete reboot, does wifi work now? if not please file a bug report.

Here is a link to help you to create a bug report if it is necessary:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by joaompr on 2020-05-10
I followed the links referring my wifi card and end up with this error: 

```

root@joao-hp:~# apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  liblzma5:i386
Use 'apt autoremove' to remove it.
The following packages will be REMOVED:
  wireless-bcm43142-oneiric-dkms
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1549 kB of archives.
After this operation, 3688 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 254148 files and directories currently installed.)
Removing wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 254085 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu6_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu6) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu6) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 5.4.0-30-generic
Building for architecture x86_64
Building initial module for 5.4.0-30-generic
ERROR (dkms apport): kernel package linux-headers-5.4.0-30-generic is not supported
Error! Application of patch 0028-add-support-for-linux-5.6.patch failed.
Check /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/ for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 installed bcmwl-kernel-source package post-installation script subprocess returned error exit status 6
Processing triggers for initramfs-tools (0.136ubuntu7) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-30-generic
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by wildmanne39 on 2020-05-10
Have you only did upgrades for the last se3veral years? 
> Removing wireless-bcm43142-oneiric-dkms (6.20.55.19~bdcom0602.0400.1000.0400-0somerville1) ...
That is a very old package that was removed, that many upgrades can lead to several issues, like with installing software.

You can try:
```
sudo dpkg &#8211;&#8211;configure &#8211;a
```
```
sudo apt-get install &#8211;f
```
```
sudo apt-get purge --remove package_name
```
You can remove the offending package but since it is:
```
Error! Application of patch 0028-add-support-for-linux-5.6.patch failed.
```
I am not sure about trying to remove it.

I am going to leave it to someone that has more experience with apt issues.

---

### Post by joaompr on 2020-05-17
Thanks you all for your suggestions. I filled this as a bug:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1878045](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1878045)

---

### Post by joaompr on 2020-05-21
The solution, from [https://bugs.launchpad.net/ubuntu/+s...l/+bug/1878045]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1878045")

apt purge bcmwl-kernel-source
apt-get install broadcom-sta-source
apt-get install broadcom-sta-dkms
apt-get install broadcom-sta-common

---

