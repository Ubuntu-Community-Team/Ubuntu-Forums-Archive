---
title: "Need persistent wireless connection with Server"
date: 2016-09-29
forum: Server Platforms
---

### Post by captnjunks on 2016-09-29
I am trying to stand up Ubuntu Server 16.04.  The box has a wireless card, I am too far away from the access to hardwire currently.  I had Ubuntu desktop for awhile, but want to implement server.  I had desktop configured and the wireless connection persisted.  However, with server the wireless connection drops after being idle.  This is a problem because I plan on hosting web applications, and accessing the server via ssh.  When the connection drops, I need to connect a monitor to the sever, and re-enter the iwconfig command with the essid and key values.  I do not want to do this all the time.

Is there a file setting that enables the sever to always be connected to the access-point?  Once I run the iwconfig command, all is good, for awhile, but it seems to time out, not sure where I can change it to never time out, or why it is doing so.

When its failing:
```
$ iwconfig
wlp2s0    IEEE 802.11abgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:4060179 (4.0 MB)  TX bytes:4060179 (4.0 MB)


wlp2s0    Link encap:Ethernet  HWaddr 64:66:b3:24:d3:d8
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6666:b3ff:fe24:d3d8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:222213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:277160363 (277.1 MB)  TX bytes:20056350 (20.0 MB)

```


I did not add lines to the /etc/network/interfaces file.  Anytime I add a new entry, the command /etc/init.d/networking restart fails.  Currently the only entry is:

```
auto lo
iface lo inet loopback
```

I tried to add:
```
auto wlp2s0
iface wlp2s0 inet dhcp
```  

This fails to allow the service to restart.  It will simply hang.

This is a critical issue to using the server the way I need.  It will not have a terminal, I need to be able to ssh into the server (along with other users) always.  Also if the machine is lossing its connection I will not be able to host applications either.

After I enter these two commands, all is fine again:
```
$ sudo iwconfig essid "networkID" key s:theKey
```

```
$ iwconfig
wlp2s0    IEEE 802.11abgn  ESSID:"NetworkID"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:7B:99:F5:E6
          Bit Rate=48 Mb/s   Tx-Power=16 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:102   Missed beacon:0

$ ifconfig

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:4134507 (4.1 MB)  TX bytes:4134507 (4.1 MB)


wlp2s0    Link encap:Ethernet  HWaddr 64:66:b3:24:d3:d8
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6666:b3ff:fe24:d3d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:277292494 (277.2 MB)  TX bytes:20214313 (20.2 MB)
```
Thank you!

---

### Post by darkod on 2016-09-30
If there is a password on the wifi you can't simply use:
```
iface xxxx inet dhcp
```

How will it know the pass to authenticate?

Try something like this: [https://linuxconfig.org/setup-wireless-interface-with-wpa-and-wpa2-on-ubuntu](https://linuxconfig.org/setup-wireless-interface-with-wpa-and-wpa2-on-ubuntu)

If the networking restart command doesn't work simply reboot the machine. It happens sometimes. Upon reboot it will try using the new modified /etc/network/interfaces and if all is good it should work.

---

### Post by captnjunks on 2016-09-30
Went through the process in the link, it will initially connect, but if I restart, the job - Raise network interfaces hangs and uses the full 5min 6s and then fails at start up.  It does not like the interfaces file entries.  My key is not WPA it is WEP so I think the entries need to work for WEP keys with interface?

---

### Post by captnjunks on 2016-09-30
so I did something that feels hacky and insecure.

I placed a few commands in the pre-up and up conditions and changed the interface to manual.  It works for start-up, I will wait to see if if resolves the time-out issue if the connection stays idle

My interface file is now:

```

auto wlp2s0
iface wlp2s0 inet manual
    pre-up iwconfig wlp2s0 essid ID key s:KEY
    up dhclient wlp2s0

```

This works to resolve the connection at startup, it however does not resolve the issue of the connection timing out after idle time.

Here is my dmesg output:
```

[   17.500164] wlp2s0: authenticate with 00:24:7b:99:f5:e6
[   17.509258] wlp2s0: send auth to 00:24:7b:99:f5:e6 (try 1/3)
[   17.511394] wlp2s0: authenticated
[   17.511421] ath9k 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[   17.512228] wlp2s0: associate with 00:24:7b:99:f5:e6 (try 1/3)
[   17.519350] wlp2s0: RX AssocResp from 00:24:7b:99:f5:e6 (capab=0x431 status=0 aid=3)
[   17.519430] wlp2s0: associated
[   17.519456] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   17.534952] cfg80211: Regulatory domain changed to country: US
[   17.534956] cfg80211:  DFS Master region: FCC
[   17.534958] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   17.534960] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[   17.534962] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[   17.534963] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[   17.534965] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[   17.534966] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[   17.534968] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[20615.344592] cfg80211: World regulatory domain updated:
[20615.344602] cfg80211:  DFS Master region: unset
[20615.344606] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[20615.344614] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[20615.344620] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[20615.344626] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[20615.344632] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[20615.344638] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[20615.344644] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[20615.344650] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[20615.344655] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[30213.019816] [drm:drm_edid_block_valid [drm]] *ERROR* EDID checksum is invalid, remainder is 5
[30213.019980] Raw EDID:
[30213.020026]      40 01 02 00 00 00 00 76 00 a5 00 a5 01 02 03 1a
[30213.020128]      1a a8 01 00 00 00 00 00 40 00 00 00 00 00 00 00
[30213.020229]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[30213.020330]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[30213.020430]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[30213.020530]      00 00 00 00 00 00 00 00 00 00 00 00 00 01 ff ff
[30213.020630]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[30213.020730]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[30213.021955] [drm:radeon_dvi_detect [radeon]] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID
[30213.138268] i2c i2c-1: sendbytes: NAK bailout.
[32282.225509] wlp2s0: authenticate with 00:24:7b:99:f5:e6
[32282.235130] wlp2s0: send auth to 00:24:7b:99:f5:e6 (try 1/3)
[32282.337448] wlp2s0: send auth to 00:24:7b:99:f5:e6 (try 2/3)
[32282.352327] wlp2s0: authenticated
[32282.352397] ath9k 0000:02:00.0 wlp2s0: disabling HT/VHT due to WEP/TKIP use
[32282.353471] wlp2s0: associate with 00:24:7b:99:f5:e6 (try 1/3)
[32282.356334] wlp2s0: RX AssocResp from 00:24:7b:99:f5:e6 (capab=0x431 status=0 aid=3)
[32282.356466] wlp2s0: associated
[32282.377172] cfg80211: Regulatory domain changed to country: US
[32282.377182] cfg80211:  DFS Master region: FCC
[32282.377187] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[32282.377194] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[32282.377201] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[32282.377209] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[32282.377215] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[32282.377220] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[32282.377225] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
```


Just above the EDID error there is an instance where the World Regulatory domain updated to what looks like NULL and the DFS Master region went unset.  What process handles this?  It seem to me this is where the failure in the network happens and the sever looses connection.  cfg80211 is a kernel process, but that is all I know about it.

---

### Post by captnjunks on 2016-10-05
Ended up going back to desktop version.  The network management seems more stable.  Maybe I needed to install a network manager, or I missed some other configuration that the desktop version takes care of via another process.  With desktop the wireless connection remains persistent, and without the /etc/network/interface having an extra entry for the wireless card.  I'll just pay the overhead cost of the UI until I can figure out why the server version seems to handle the wireless connection differently.

---

