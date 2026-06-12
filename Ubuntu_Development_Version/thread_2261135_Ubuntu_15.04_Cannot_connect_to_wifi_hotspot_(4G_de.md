---
title: "Ubuntu 15.04: Cannot connect to wifi hotspot (4G device)"
date: 2015-01-16
forum: Ubuntu Development Version
---

### Post by osmoma on 2015-01-16
[FONT=Ubuntu]Hello,
My Ubuntu 15.04 stopped connecting to wifi hotspot after upgrade. I re-installed the entire system, but it simply cannot connect to my 4G internet device. 

Ubuntu 14.10 and the first versions of Ubuntu 15.04 all connect well without problems.

My 4G hotspot is similar to this device (WöW by NOS in Portugal).
[http://www.custojusto.pt/viana-do-castelo/informatica-acessorios/wow-internet-4g-14027440](http://www.custojusto.pt/viana-do-castelo/informatica-acessorios/wow-internet-4g-14027440)

I also tried the latest (daily ISO) and run it live from an USB-pen. Neither it cannot connect. It asks for the wifi-password, but then nothing; no error messages or warning. 
I also press the WPS-button in the 4G-device.  Vivid can see the wifi-name but fails to connect.

The wifi-name (SSID) is repeated three times in the wireless menu (the names are listed like a menu-tree). Like this 
-- Internet 4G 
--------Internet 4G 1
--------Internet 4G 2

None of these work.  Maybe I pressed the WPS-button too many times.

[/FONT]$ uname -a
Linux ubuntu 3.18.0-9-generic #10-Ubuntu SMP Mon Jan 12 21:41:54 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ lshw
 *-network
                description: Wireless interface
                [B]product: Wireless 3160
                vendor: Intel Corporation[/B]
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 83
                serial: a0:88:69:31:27:77
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.18.0-9-generic **firmware=23.10.10.0 **latency=0 link=no multicast=yes wireless=IEEE 802.11abgn

---

### Post by mc4man on 2015-01-16
See the same, worked fine with a portable hotspot, then did some updates & can no longer authenticate the device.
(- As I don't pay much attention to 15.04 there were quite a number of updates available. Didn't do them all but still a fair number. 
Maybe I can pick thru the list later, libpam* & systemd stand out in a cursory glance.

---

### Post by osmoma on 2015-01-16
Ok, it might help to wait a week or two until they deliver new updates.

One thing I noticed that Ubuntu 15.04 has an older firmware version (for the Intel`s 3160 wifi card) than Ubuntu 14.10. 

$ lshw
...
...
configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-29-generic **firmware=25.228.9.0** ip=xxxx.xx.x.xxx latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn


Ubuntu 15.04 [B]firmware=23.10.10.0 
[/B]Ubuntu 14.10 firmware=25.228.9.0.

I do not know if this matters. Maybe the numbers refer to filenames, and not to version numbers.

$ lsmod | grep wifi
iwlwifi               183038  1 iwlmvm
cfg80211              510218  3 iwlwifi,mac80211,iwlmvm


$ ls -l  /lib/firmware/iwlwifi-3160-*
....

I tried to copy the firmware files from 14.10 to Vivid.  Then

$ sudo rmmod iwlmvm
$ sudo rmmod iwlwifi

$ sudo modprobe iwlmvm iwlwifi

$ sudo killall NetworkManager

No success.  
Obrigado. Boa Noite.

---

### Post by mc4man on 2015-01-17
Fine here now, I believe in my case it was user error rather than some change, ect.

---

### Post by osmoma on 2015-01-17
Ok, I will monitor this issue for some time ahead.
I need Vivid to port [audio-recorder]("https://launchpad.net/audio-recorder") to Ubuntu+1.

Até Já.

os-moma
Portugal

---

### Post by jeremy31 on 2015-01-26
With the intel wifi cards you might need to run this and reboot before you can connect to a hotspot ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

If it happens to not work correctly ```
gksudo gedit
``` and delete the line ```
options iwlwifi 11n_disable=8
``` save, exit, reboot

---

### Post by osmoma on 2015-01-28
Re-hi,
Sorry for my delayed reply.
I made a new installation with the latest Ubuntu Daily ISO-image.
This time the WIFI (over 4G) connects perfectly fine.

But for curiosity:  I made the re-installation in a cafe of our village because they have a good, rapid internet connection.
And I saw the error after first reboot. It could not connect to the cafe`s wireless net, and the network-applet listed the SSID name several times. So something sucked!
[[IMG]http://bildr.no/thumb/QjBMdDl3.jpeg[/IMG]]("http://bildr.no/view/QjBMdDl3")

But everything worked well when I rebooted the machine at home.  I had a plan to insert your [COLOR=#000000][FONT=Ubuntu Mono]11n_disable=8 [/FONT][/COLOR]option but this was not necessary.
But your option doesn`t seem to make any harm either.

BTW: I have a feeling that my Android table downloads web pages more rapidly. I will try to fine-tune the wifi card on my laptop to see if it helps.
Video drivers may also make a difference.

$ **lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet 64bit (development branch)
Release:    15.04
Codename:    vivid

$ **uname -a**
Linux vivid64 3.18.0-11-generic #12-Ubuntu SMP Fri Jan 23 22:53:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:80:E3:f7:51:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:667928 (667.9 KB)  TX bytes:667928 (667.9 KB)

wlan0     Link encap:Ethernet  HWaddr b0:51:77:12:92:5b  
          inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a177:69ff:ee31:981c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161119123 (161.1 MB)  TX bytes:21047514 (21.0 MB)

$ **cat /etc/modprobe.d/iwlwifi.conf**
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8

$ **lspci -v | grep -A6 Network**  
04:00.0 Network controller: Intel Corporation Wireless **3160** (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 3160
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f7d00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: **iwlwifi**

$ **modinfo iwlwifi**
```
filename:       /lib/modules/3.18.0-11-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3165-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     9730790705D25DB36AE15EE
alias:          pci:v00008086d000024F4sv*sd00000030bc*sc*i*
alias:          pci:v00008086d000024F3sv*sd00000004bc*sc*i*
...
...
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
...
...
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-11-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:23:D4:70:AC:74:B1:F9:D1:1F:FB:23:A4:E4:A7:B4:80:FE:56:F1
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

```

EDIT: I verified the connection after several reboots.  It connects well with or without the 11n_disable=8 option (at home / 4G).
I will monitor this issue further.

---

### Post by osmoma on 2015-01-29
Hello,
This bug seems to be more persistent than first thought.  It recurred to my Ubuntu 15.04 system.
The WIFI simply stopped to connect after some random reboot.  I do not remember if I did `apt-get upgrade` before the error re-appeared.

But I found a solution. This solution may be equally random as the error itself. I do not have any proof that this will help next time.
I got the WIFI back by feeding 11n_disable=1 to /etc/modprobe.d/iwlwifi.conf file,  and restarting the network services.

$ sudo service network-manager stop

$ echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf

$ sudo rmmod iwlmvm iwlwifi 
$ sudo modprobe  iwlmvm iwlwifi 

$ sudo service network-manager restart

Info about the 11n_disable parameter: 
Disable 11n functionality:  **1: full**, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)

---

### Post by osmoma on 2015-01-29
EDIT: Latest updates seems to have fixed this bug. WIFI now connects well as it did in Ubuntu 14.10.
I also installed the latest kernel 3.18.0-12 from the Ubuntu`s pre-proposed repository.

$ uname -a
Linux vivid64 3.18.0-12-generic #13-Ubuntu SMP Thu Jan 29 04:35:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ dpkg -l | grep network-manager
```
ii  network-manager               0.9.10.0-4ubuntu2   amd64     network management framework (daemon and userspace tools)
ii  network-manager-gnome         0.9.10.1-0ubuntu1   amd64     network management framework (GNOME frontend)
ii  network-manager-pptp          0.9.10.0-1ubuntu1   amd64     network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome    0.9.10.0-1ubuntu1   amd64     network management framework (PPTP plugin GNOME GUI)
```

EDIT: Sometime the network-manager (network applet) crashes. I have to restart it with:
$ sudo service network-manager restart
Then it re-connects well.

---

### Post by mydoveks on 2015-05-04
how do i do this with a wifi netgearWNDA3100 usb wifi stick .

---

### Post by cariboo on 2015-05-04
@mydoveks , it would be better to ask your question in the proper sub-forum, as this thread is closed.

---

