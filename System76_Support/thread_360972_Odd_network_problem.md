---
title: "Odd network problem"
date: 2007-02-13
forum: System76 Support
---

### Post by AusIV4 on 2007-02-13
I got my Gazelle yesterday and I'm having a strange problem with my network devices.

When I boot up my computer, the wired ethernet card is eth1 and the wireless is eth2.
Here is the result of iwconfig after I had connected to a network:

```

lo        no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11g  ESSID:"XXXXX"  Nickname:"XXXXX"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:F2:31:D8
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-45 dBm  Noise level=-109 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:943   Missed beacon:0

sit0      no wireless extensions.

```
I suspend my computer, bring it back up, run iwconfig again, and get this:
```

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0

```
Note that wired device has become eth0 and the wireless is now eth1. This is problematic for me, because I prefer wifi-radar for connecting to wireless networks, and it requires that the device be specified in the config file.

The reason I use wifi-radar is that it allows me to create a list of profiles and prioritize them, then I can have it connect to the highest priority network that is available as a part of the boot up phase.

If there are any programs that auto-detect the wireless interface, prioritize networks, and can be run before the login screen, I'd be happy with that, but in my searching, wifi-radar is the only program that fits this criteria.

---

### Post by crichell on 2007-02-14
This is odd.  You may need to add the interfaces and mac addresses to the /etc/iftab file to make sure they remain the same.  Network Manager doesn't require this but I don't think it can be run before the login screen.

---

### Post by AusIV4 on 2007-02-14
> You may need to add the interfaces and mac addresses to the /etc/iftab file to make sure they remain the same.
That did the trick. Thanks.

---

