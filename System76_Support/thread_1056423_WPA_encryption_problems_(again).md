---
title: "WPA encryption problems (again)"
date: 2009-01-31
forum: System76 Support
---

### Post by jbraswell on 2009-01-31
I know this has been discussed to death, but all the solutions I've tried so far haven't worked.  I got a new machine with 8.10 on it two days ago, and I still can't connect to my WPA network.

I'm using wicd, and I can see my network listed, but whenever I try to connect, it fails.  Under hardware drivers, I have "Support for 5xxx series of Atheros 802.11 wireless LAN cards." installed and activated.  

Under wicd's preferences, I have my wireless interface set to ath0, and my WPA supplicant driver set to wext.  Below are the outputs of the usual commands.  If anyone could tell me what dumb thing I'm doing wrong, I'd really appreciate it.

```
jbraswell@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:91:15:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.3-0 ip=192.168.1.101 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:58:96:50:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:43:dc:c3:9e:1f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

```
jbraswell@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"monkeybites"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:77225  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extenjbraswell@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"monkeybites"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:77225  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
ath5k
ath_pci
```

---

### Post by jdb on 2009-01-31
> **jbraswell said:**
> I know this has been discussed to death, but all the solutions I've tried so far haven't worked.  I got a new machine with 8.10 on it two days ago, and I still can't connect to my WPA network.

I'm using wicd, and I can see my network listed, but whenever I try to connect, it fails.  Under hardware drivers, I have "Support for 5xxx series of Atheros 802.11 wireless LAN cards." installed and activated.  

Under wicd's preferences, I have my wireless interface set to ath0, and my WPA supplicant driver set to wext.  Below are the outputs of the usual commands.  If anyone could tell me what dumb thing I'm doing wrong, I'd really appreciate it.

```
jbraswell@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:91:15:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.3-0 ip=192.168.1.101 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:58:96:50:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:43:dc:c3:9e:1f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

```
jbraswell@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"monkeybites"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:77225  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extenjbraswell@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"monkeybites"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:77225  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
ath5k
ath_pci
```

I've never used wicd, but the iwconfig output looks pretty bad.

It doesn't see your access point at all:
Access Point: Not-Associated 
Signal level = Noise level = -96 dBm

also I don't know why:
Encryption key:off

System76 computers should connect right up right out of the box.
Why are you using wicd??

jdb

---

### Post by jbraswell on 2009-02-01
Well, I started out with network manager when I got it, expecting it to work fine, but then it seems I ran into the bug described here: [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")
where my passkey was getting scrambled.  I tried the solution in that post, but every time I changed the configs they discussed, they would change back every time I tried to connect to the network.  After frustration over that, I decided to give wicd a try since at least I could tell my passkey was correct.  

Ugh, furthermore, I'm not sure what I'm doing, but sometimes after trying to connect with wicd and then rebooting, I get this from iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"monkeybites"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Why do I now get wlan0??!

---

### Post by jdb on 2009-02-01
> **jbraswell said:**
> Well, I started out with network manager when I got it, expecting it to work fine, but then it seems I ran into the bug described here: [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")
where my passkey was getting scrambled.  I tried the solution in that post, but every time I changed the configs they discussed, they would change back every time I tried to connect to the network.  After frustration over that, I decided to give wicd a try since at least I could tell my passkey was correct.  

Ugh, furthermore, I'm not sure what I'm doing, but sometimes after trying to connect with wicd and then rebooting, I get this from iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"monkeybites"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Why do I now get wlan0??!

This is what I get on my Daru2 using network manager and booted to 8.10

```
uname -a
Linux dads 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

iwconfig
wlan0     IEEE 802.11abg  ESSID:"zoom"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:12:BF:2A:8F:ED   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:4D5A-504C-6E5C-90CC-5F21- [4]   Security mode:open
          Power Management:off
          Link Quality=93/100  Signal level:-37 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The Encryption key was a lot longer than that but I deleted most of it.


What model System76 do you have?
You probably need someone with the same model to help you out.

jdb

---

### Post by jbraswell on 2009-02-01
Got the Wild Dog.

By the way, when I try to connect on the command line using wpa_supplicant using these instructions:
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")
If I use the -W flag, it gives me the following but then does nothing after the last line; it just waits.  What does it mean that wlan0's "monitor" doesn't attach?

```
jbraswell@ubuntu:~$ sudo wpa_supplicant -Dwext -W -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='monkeybites'
Initializing interface (2) 'wlan0'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1e:58:96:50:1d
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
CTRL_IFACE - wlan0 - wait for monitor to attach
```

---

### Post by jdb on 2009-02-01
> **jbraswell said:**
> Got the Wild Dog.

By the way, when I try to connect on the command line using wpa_supplicant using these instructions:
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")
If I use the -W flag, it gives me the following but then does nothing after the last line; it just waits.  What does it mean that wlan0's "monitor" doesn't attach?

```
jbraswell@ubuntu:~$ sudo wpa_supplicant -Dwext -W -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='monkeybites'
Initializing interface (2) 'wlan0'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1e:58:96:50:1d
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
CTRL_IFACE - wlan0 - wait for monitor to attach
```

When I boot to vanilla Ubuntu wpa_supplicant.conf is buried under /etc/dbus-1/system.d and contains some pretty cryptic stuff.

When I boot to Archlinux I don't use any kind of network manager but have done all my configuration manually.

In that case my /etc/wpa_supplicant.conf is:

network={
	ssid="zoom"
	psk="my_password_here"
	priority=5
}

You might try something like this in /etc/wpa_supplicant/wpa_supplicant.conf:

network={
	ssid="monkeybites"
	psk="your_password_here"
	priority=5

jdb

---

### Post by jbraswell on 2009-02-01
Well, my .conf file in system.d just has some weird XML stuff in it, but I had made my own in etc/wpa_supplicant/wpa_supplicant.conf that looks like this:
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="monkeybites"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="MYPASSWD"
pairwise=TKIP
group=TKIP
}
```

Similarly, my wicd.conf in system.d looks wacky, but the one in /etc/wicd looks appropriate:

```
[00:18:F8:F7:00:C6]
afterscript = None
bssid = 00:18:F8:F7:00:C6
ip = None
quality = 85
gateway = None
use_global_dns = 0
strength = -64
disconnect = None
encryption = True
beforescript = None
hidden = False
channel = 6
essid = monkeybites
has_profile = True
netmask = None
key = PASSWD
enctype = wpa
dns3 = None
dns2 = None
dns1 = None
use_settings_globally = 0
use_static_dns = 0
encryption_method = WPA
mode = Master
automatic = True
```

---

### Post by jbraswell on 2009-02-01
I have no clue how, but after I posted my wicd.conf file, I scrolled way down in less, and I noticed there was another entry in there for a different network in my building.  I have no idea how it got there (maybe I accidentally clicked 'connect' on it once?), but I deleted it, rebooted, and now it works. Weird. 


Thanks for the help.

---

### Post by jdb on 2009-02-01
> **jbraswell said:**
> I have no clue how, but after I posted my wicd.conf file, I scrolled way down in less, and I noticed there was another entry in there for a different network in my building.  I have no idea how it got there (maybe I accidentally clicked 'connect' on it once?), but I deleted it, rebooted, and now it works. Weird. 


Thanks for the help.

Pure magic :popcorn:

jdb

---

