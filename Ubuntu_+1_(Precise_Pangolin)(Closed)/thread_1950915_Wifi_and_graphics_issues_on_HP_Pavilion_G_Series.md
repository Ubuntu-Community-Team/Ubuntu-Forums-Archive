---
title: "Wifi and graphics issues on HP Pavilion G Series"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by unabatedshagie on 2012-04-01
Installed 12.04 in my HP Pavilion G Series.

I'm having a couple of issues with it.

[LIST=1]
[*]When I start the machine I have to press the increase brightness button in order for the screen to display.
[*]The wifi signal is very poor and intermittantly disconnects. Sitting in the same location with Windows 7 on the same laptop and I get 5 bars but with Ubuntu I'm getting 2.
[*]The wifi button on the keyboard constantly shows the red led, even when connected to the wifi.
[/LIST]

I've not used ubuntu in about 2 years so I'm a little rusty with things.

---

### Post by wildmanne39 on 2012-04-01
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Iowan on 2012-04-01
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by unabatedshagie on 2012-04-06
**cat /etc/lsb-release; uname -a**
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux Starscream 3.2.0-21-generic-pae #34-Ubuntu SMP Thu Mar 29 22:33:16 UTC 2012 i686 i686 i386 GNU/Linux
```

**lspci -nnk | grep -iA2 net**
```
alex@Starscream:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel driver in use: brcmsmac
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1671]
	Kernel driver in use: r8169
```

**lsusb**
```
alex@Starscream:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 

```

**iwconfig**
```
alex@Starscream:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

**rfkill list all**
```
alex@Starscream:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```
**lsmod**
```
alex@Starscream:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
joydev                 17393  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
wl                   2646601  0 
lib80211               14040  1 wl
bcma                   25651  0 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
brcmsmac              540875  0 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                72846  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13027  0 
mac80211              436455  1 brcmsmac
uvcvideo               67203  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               86588  1 uvcvideo
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
rts_pstor             353215  0 
cordic                 12487  1 brcmsmac
wmi                    18744  1 hp_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36570  0 
i915                  414512  3 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18907  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 

```

---

### Post by wildmanne39 on 2012-04-06
Hi, according to this information you can not connect with your wireless at all right now.

Please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist hp_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh
/sbin/iwconfig wlan0 power off
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by unabatedshagie on 2012-04-06
Followed the instructions above and rebooted.

Now when I press the wifi button on the keyboard the LED on it still isn't turning white and it seems to be turning the bluetooth on and off.

Also the wifi isn't picking up my network at all now.

---

### Post by wildmanne39 on 2012-04-06
Hi, make sure your wireless is on then please post the output of:
```
rfkill list all
```
```
lsmod
```
I want to see if the changes had any effects in the output.
Thanks

---

### Post by unabatedshagie on 2012-04-06
**rfkill list all**
```
alex@Starscream:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
**lsmod**
```
alex@Starscream:~$ lsmod
Module                  Size  Used by
btusb                  17912  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
joydev                 17393  0 
rfcomm                 38139  12 
bnep                   17830  2 
bluetooth             158438  23 btusb,rfcomm,bnep
wl                   2646601  0 
lib80211               14040  1 wl
arc4                   12473  2 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
brcmsmac              540875  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                72846  0 
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436455  1 brcmsmac
i915                  414512  3 
snd                    62064  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmutil               14675  1 brcmsmac
rts_pstor             353215  0 
wmi                    18744  0 
cfg80211              178679  2 brcmsmac,mac80211
mac_hid                13077  0 
crc8                   12781  1 brcmsmac
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
cordic                 12487  1 brcmsmac
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18907  1 i915
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
```

---

### Post by wildmanne39 on 2012-04-06
Hi, the block is gone, I think we need to also blacklist one more driver.
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then reboot.
Thanks

---

### Post by unabatedshagie on 2012-04-06
Doesn't seem to have made a difference.

Wifi button still turns on both wifi and bluetooth although now the wifi isn't connecting.

---

### Post by wildmanne39 on 2012-04-06
Hi, lets switch drivers I believe this will get the connection working correctly, but I was never working on bluetooth.
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
remove [COLOR="Red"]blacklist wl[/COLOR]
save, close gedit then reboot.
Thanks

---

### Post by unabatedshagie on 2012-04-07
The button doesn't seem to be turning on the wifi now, just seems to be turning the bluetooth on/off now.

---

### Post by wildmanne39 on 2012-04-07
Hi, so you can not connect? 

This is a little experiment because 12.04 is new and what worked with previous releases may not work with it.

Please post the output of:
```
nm-tool
rfkill list all
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```
Thanks

---

### Post by robwilkens on 2012-04-07
Just for the record i have a pavillion G6 and don't have any of these problems with 12.04 (Well, except maybe weak wifi antenna - i'm sitting 8 feet away from the router and i have 3 out of 4 bars, but it works fine).  As per video - I'd suggest trying the fglrx video driver, it seems to usually work better than the open source driver (in fact, in previous ubuntu releases, i couldn't install at all because of the open source video driver).



> **unabatedshagie said:**
> Installed 12.04 in my HP Pavilion 
G Series.

I'm having a couple of issues with it.

[LIST=1]
[*]When I start the machine I have to press the increase brightness button in order for the screen to display.
[*]The wifi signal is very poor and intermittantly disconnects. Sitting in the same location with Windows 7 on the same laptop and I get 5 bars but with Ubuntu I'm getting 2.
[*]The wifi button on the keyboard constantly shows the red led, even when connected to the wifi.
[/LIST]

I've not used ubuntu in about 2 years so I'm a little rusty with things.

---

### Post by unabatedshagie on 2012-04-07
**nm-tool**```
alex@Starscream:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        EC:9A:74:63:AE:A7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        64:27:37:1E:23:64

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```
**rfkill list all**```
alex@Starscream:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```**cat /var/lib/NetworkManager/NetworkManager.state**```
alex@Starscream:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```**sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55**```
alex@Starscream:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
[sudo] password for alex: 
Apr  7 08:26:32 Starscream NetworkManager[849]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr  7 08:26:32 Starscream NetworkManager[849]: <info> (wlan0): bringing up device.
Apr  7 08:26:32 Starscream kernel: [   18.820692] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
Apr  7 08:26:32 Starscream kernel: [   18.820701] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
Apr  7 08:26:32 Starscream kernel: [   18.820710] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
Apr  7 08:26:32 Starscream kernel: [   18.820718] ieee80211 phy0: wl0: brcms_c_wme_setparams : no-clock
Apr  7 08:26:32 Starscream kernel: [   18.821432] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 08:26:32 Starscream NetworkManager[849]: <warn> (wlan0): device not up after timeout!
Apr  7 08:26:32 Starscream NetworkManager[849]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr  7 08:26:32 Starscream kernel: [   18.909013] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  7 08:26:32 Starscream dbus[789]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Apr  7 08:26:33 Starscream dbus[789]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Apr  7 08:26:33 Starscream wpa_supplicant[920]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Apr  7 08:26:33 Starscream wpa_supplicant[920]: Could not set interface 'wlan0' UP
Apr  7 08:26:33 Starscream wpa_supplicant[920]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Apr  7 08:26:33 Starscream wpa_supplicant[920]: Failed to initialize driver interface
Apr  7 08:26:33 Starscream NetworkManager[849]: <info> wpa_supplicant started
Apr  7 08:26:33 Starscream NetworkManager[849]: <error> [1333783593.269509] [nm-supplicant-interface.c:804] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Apr  7 08:26:33 Starscream NetworkManager[849]: <info> (wlan0): supplicant interface state: starting -> down
Apr  7 08:41:32 Starscream kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion g7 Notebook PC      /1671, BIOS F.42 12/08/2011
Apr  7 08:41:32 Starscream kernel: [   18.245463] wl: module license 'MIXED/Proprietary' taints kernel.
Apr  7 08:41:32 Starscream kernel: [   18.265009] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  7 08:41:32 Starscream kernel: [   18.265029] wl 0000:01:00.0: setting latency timer to 64
Apr  7 08:41:32 Starscream kernel: [   18.434585] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Apr  7 08:41:33 Starscream NetworkManager[795]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth1, iface: eth1)
Apr  7 08:41:33 Starscream NetworkManager[795]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth1/rfkill0) (driver (unknown))
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): using WEXT for WiFi device control
Apr  7 08:41:33 Starscream NetworkManager[795]: <error> [1333784493.123122] [nm-device-wifi.c:2590] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): now managed
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): bringing up device.
Apr  7 08:41:33 Starscream NetworkManager[795]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr  7 08:41:33 Starscream kernel: [   19.113698] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  7 22:53:53 Starscream kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion g7 Notebook PC      /1671, BIOS F.42 12/08/2011
Apr  7 22:53:53 Starscream kernel: [   20.035070] wl: module license 'MIXED/Proprietary' taints kernel.
Apr  7 22:53:53 Starscream kernel: [   20.038581] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  7 22:53:53 Starscream kernel: [   20.038590] wl 0000:01:00.0: setting latency timer to 64
Apr  7 22:53:53 Starscream kernel: [   20.199983] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth1/rfkill0) (driver (unknown))
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): using WEXT for WiFi device control
Apr  7 22:53:53 Starscream NetworkManager[743]: <error> [1333835633.641987] [nm-device-wifi.c:2590] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): now managed
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): bringing up device.
Apr  7 22:53:53 Starscream NetworkManager[743]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr  7 22:53:53 Starscream kernel: [   20.619077] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

---

### Post by wildmanne39 on 2012-04-07
Hi, check the switch by tapping the key once then please try:
```
rfkill unblock all
```
see if it comes on if not check with
```
rfkill list all
```
to see if it has a soft or hardblock still.
Thanks

---

### Post by unabatedshagie on 2012-04-07
First command worked. Wifi is now working. Only problem now is the wifi button is turning both the wifi and bluetooth on/off.

---

### Post by wildmanne39 on 2012-04-07
Hi, I do not know how to fix that it may be a bug in 12.04 still, there is a parameter that can be set with a lot of drivers but not this one.

Did it only start after we started working on the issue you were having? we blacklisted the modules that was keeping your system soft blocked but it should not cause problems with bluetooth but I have never worked with bluetooth issues only wireless. 

Is your wireless working good now?
Thanks

---

