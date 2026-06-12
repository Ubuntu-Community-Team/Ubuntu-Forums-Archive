---
title: "Installed elementary had wifi then updated and rebooted now no wifi"
date: 2016-09-17
forum: Ubuntu/Debian BASED
---

### Post by bkentmoore on 2016-09-17
Hi,
   Installed Elementary OS Freya next to Windows. Everything appeared to be fine. I had both wired and wireless access and could see available wifi networks. Then used the updater to make sure I had up to date software. It said I needed to reboot so I did. After reboot I had only wired network connections available. It is as if it doesn't know I have a wifi card at all. Any ideas how I can resolve this?
Thanks.

---

### Post by howefield on 2016-09-17
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by wildmanne39 on 2016-09-17
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by bkentmoore on 2016-09-17
```
########## wireless info START ##########

Report from: 17 Sep 2016 14:57 CDT -0500

Booted last: 17 Sep 2016 14:47 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    elementary OS
Description:    elementary OS Freya
Release:    0.3.2
Codename:    freya

##### kernel ############################

Linux 3.19.0-68-generic #76~14.04.1-Ubuntu SMP Fri Aug 12 11:46:25 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Pantheon

##### lspci #############################

07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e071]
    Kernel driver in use: bcma-pci-bridge

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b3aa Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0489:e062 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: nfc0: NFC
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

bcma                   53248  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:8bea:d480:bd01:f183:578d:7f1a/64 Scope:Global
          inet6 addr: 2602:306:8bea:d480:<IP6 'eth0' [IF1]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247368941 (247.3 MB)  TX bytes:1079962 (1.0 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       933     1  0 14:47 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.75
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

  IPv6 Settings:
    Address:         2602:306:8bea:d480:bd01:f183:578d:7f1a
    Prefix:          64
    Gateway:         fe80::ae5d:10ff:fe7e:c259

    Address:         2602:306:8bea:d480:<IP6 'eth0' [IF1]>
    Prefix:          64
    Gateway:         fe80::ae5d:10ff:fe7e:c259

    Address:         fe80::<IP6 'eth0' [IF1]>
    Prefix:          64
    Gateway:         fe80::ae5d:10ff:fe7e:c259

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[bcma]
filename:       /lib/modules/3.19.0-68-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-68-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:E8:C8:B7:4D:D5:E3:3A:9F:92:F3:29:D4:B3:E0:F8:96:8B:F7:32
sig_hashalgo:   sha512

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.946820] bcma: bus0: Found chip with id 43142, rev 0x01 and package 0x08
[   13.946860] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[   13.946891] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[   13.946948] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[   13.947018] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[   13.963873] bcma: bus0: Bus registered
[   14.312697] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0489-e062.hcd failed with error -2
[   14.312707] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-0489-e062.hcd not found
[   20.354741] r8169 0000:0e:00.0 eth0: link down (repeated 2 times)
[   20.354797] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.851575] r8169 0000:0e:00.0 eth0: link up
[   22.851590] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by bkentmoore on 2016-09-17
The weird think is that when I first installed Freya, wireless worked fine but when I used the update manager and updated and rebooted it appears that it no longer sees the wireless adapter.

---

### Post by wildmanne39 on 2016-09-17
Please do:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
if it does not work do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by wildmanne39 on 2016-09-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by bkentmoore on 2016-09-17
Cool Thanks. I ran 
sudo apt-get install --reinstall bcmwl-kernel-source

and that appears to have fixed it. Thank You

---

### Post by wildmanne39 on 2016-09-17
Your welcome!
Enjoy!

---

### Post by wildmanne39 on 2016-09-17
Please do:
```
sudo su 
echo wl>> /etc/modules 
exit
```
Reboot

---

### Post by bkentmoore on 2016-09-17
drew083114@drew083114-SVF1521GCXB:~$ echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist bcma
drew083114@drew083114-SVF1521GCXB:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hunspell-fr hyphen-en-us libllvm3.6 libreoffice-help-ca libreoffice-help-cs
  libreoffice-help-da libreoffice-help-de libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-help-fr libreoffice-help-hu
  libreoffice-help-it libreoffice-help-ja libreoffice-help-ko
  libreoffice-help-nl libreoffice-help-pl libreoffice-help-pt
  libreoffice-help-pt-br libreoffice-help-ru libreoffice-help-sv
  libreoffice-help-vi libreoffice-help-zh-tw libreoffice-l10n-bg
  libreoffice-l10n-ca libreoffice-l10n-cs libreoffice-l10n-da
  libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-fr libreoffice-l10n-hu libreoffice-l10n-id
  libreoffice-l10n-it libreoffice-l10n-ja libreoffice-l10n-ko
  libreoffice-l10n-nb libreoffice-l10n-nl libreoffice-l10n-pl
  libreoffice-l10n-pt libreoffice-l10n-pt-br libreoffice-l10n-ru
  libreoffice-l10n-sv libreoffice-l10n-th libreoffice-l10n-uk
  libreoffice-l10n-vi libreoffice-l10n-zh-tw linux-headers-3.13.0-95
  linux-headers-3.13.0-95-generic linux-headers-3.19.0-39
  linux-headers-3.19.0-39-generic linux-image-3.19.0-39-generic
  linux-image-extra-3.19.0-39-generic linux-image-extra-4.4.0-36-generic
  linux-signed-image-3.19.0-39-generic myspell-pt myspell-sv-se mythes-en-au
  mythes-sv openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,511 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 334320 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) over (6.30.223.248+bdcom-0ubuntu0.2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 4.4.0-38-generic
Building for architecture x86_64
Building initial module for 4.4.0-38-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-38-generic/extra/

depmod....

DKMS: install completed.
modprobe: ERROR: could not insert 'wl': Required key not available
update-initramfs: deferring update (trigger activated)
Processing triggers for shim-signed (1.19~14.04.1+0.8-0ubuntu2) ...
Processing triggers for initramfs-tools (0.103ubuntu4.4) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic

---

### Post by bkentmoore on 2016-09-17
I did this:
sudo su 
echo wl>> /etc/modules 
exit

but it appears to not have had an effect

---

### Post by bkentmoore on 2016-09-18
When I run : 
sudo apt-get install --reinstall bcmwl-kernel-source

I get a message saying the computer has "secure boot" and I have to enter the admin password to disable it. I did that. But am not sure if that makes a difference.

---

### Post by wildmanne39 on 2016-09-18
Yes will need to disable secure boot because you upgraded your kernel or operating system to 16.04 after we got it working the first time.

Please go to the link post 81 and follow the directions just for turning secure boot off and not the part for trying to create a key.
[https://ubuntuforums.org/showthread.php?t=2304607&page=9&highlight=secure+boot%2BWild+Man](https://ubuntuforums.org/showthread.php?t=2304607&page=9&highlight=secure+boot%2BWild+Man)

Once you have done that the driver should load if not reinstall it like before and make sure to leave secure boot off.

If you want to create a key you can follow all the directions to do that where it has the driver substitute your which is wl.

Edit:
If your computer has the option you can disable secure boot in the bios. I am to tired to help any more to night t is late here but if you need help tomorrow with secure boot I will help.

---

