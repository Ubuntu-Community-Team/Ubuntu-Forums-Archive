---
title: "Ubuntu Studio 13.04 - Alsamixer - No mixer for USB audio Saffire 6"
date: 2013-05-04
forum: Ubuntu Studio
---

### Post by mjt464 on 2013-05-04
Hi there.

Installed the Ubuntu Stusio 13.04 test DVD to an external USB hard drive and updated as of today - all OK except recognition and function of the Saffire 6 USB audio which works fine on 12.10.

This is demonstrated in Alsa mixer which shows the Saffire 6 device in the F6 - select sound card drop down list, but when selected from that list, I get "This sound device does not have any controls".  This does not happen in US 12.10.

In Gladish I get the full device name list in the pulldown "Jack driver" drop down list, but not the generic "HW:1" descriptor.  WHen I attempt to start the studio, the Saffire 6 just blinks its lights and pops repeatedly as if it is trying to startup repeatedly (normally it blinks and pops just twice and then runs on US 12.10).

Similar behaviour in QJackctl, except that it shows both the generic HW:1 name and the full device name.

The onboard Intel sound i/out works fine.

Details below - Any ideas?

Cheers

mike@snowpea-us13:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 0718:1905 Imation Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks 
Bus 002 Device 003: ID 1235:8008 Novation EMS 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver

mike@snowpea-us13:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: S6USB20 [Saffire 6USB2.0], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by zequence on 2013-05-04
sounds like a possible alsa regression. I would report a bug. Create a launchpad account, and in a terminal, do: 

```
ubuntu-bug alsa-base
```

---

### Post by mjt464 on 2013-05-04
Thanks - done.  I did not know about that system for bug reporting before. Very handy.

---

