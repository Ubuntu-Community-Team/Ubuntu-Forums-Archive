---
title: "Wireless issues after update."
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by virtuousd on 2012-03-29
Hey everyone, I am having some problems with my wireless since trying the 12.04 Beta.

I have two wireless devices on my machine,

```
$ iwconfig
lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:"something"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:FE:09:A7   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:72   Missed beacon:0

eth0      no wireless extensions.

```

wlan1 is a Rosewill RNX-N180UBE USB wireless adapter. This is the one I use most of all as it gets much better signal. Unfortunately, as you can see, it is not working. In network manager it comes up as

```
Wireless Network (Manufacturer Realtek RNX-N180UBE) device not ready
```

wlan0 gets horrid signal, and is an Atheros AR922X PCI adapter.

Here's some more info:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 002 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 005: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
```

Further observations: For some reason plugging in the Rosewill adapter improves the signal on the Atheros adapter. I consistently have trouble connecting to the network when the usb adapter is unplugged, and the signal is usually 1bar. Plugging the usb in almost instantly makes the signal go up to 4bars and overall makes it useable (hence being able to post this).

Also, upon some starts both of the adapters come up as "device not ready". I think it happens when I restart with the usb one plugged in. Taking it out and waiting for the Atheros PCI adapter to connect, and then plugging the USB one in has given me the best results for connectivity.

This makes me think it might be an issue with the network manager and not the drivers? Why would connecting my USB antennae improve my PCI signal strength otherwise?

Please help!

---

### Post by virtuousd on 2012-03-29
Update:

Following my hunch, I took out the PCI Wireless card. Indeed, my USB adapter now works just fine. It seems there is some weirdness that happens while trying to have them both connected. Current info, with just the USB device running:


```
$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"something"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:FE:09:A7   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/100  Signal level=57/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 002 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 005: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
```

---

