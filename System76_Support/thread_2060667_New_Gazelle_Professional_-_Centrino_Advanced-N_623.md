---
title: "New Gazelle Professional - Centrino Advanced-N 6235 wireless issue"
date: 2012-09-20
forum: System76 Support
---

### Post by BrandonIngalls on 2012-09-20
Just got this laptop to use for college and the wireless only seems to work sporadicly and when it does work it will disconnect me at random. I rarely get more than three mins of wireless use out of it.

I already feel like this was a bit of a waste of money(One expensive paper weight) I hope I can resolve this and make this desktop into a laptop so I can use it for classes but if not I hope I can return it and get a reliable Lenovo.

I have never had this much trouble with a laptop or ubuntu before this laptop.
---

What I have done so far...
1. Re-installed Ubuntu twice (with separate cds just to make sure).
2. Disable wireless n...
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1
3. Removed network manager and replaced with wicd
4. removed wicd and re-installed network manager
5. Updated everything
6. Restarted at least fifty times.
7. Created another user account to try to connect with.
8. Tried to connect to the campus open network.

Errors in syslog...
```
[ 1086.253601] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1086.452131] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1086.651874] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1086.851774] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1090.653099] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1090.852414] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1091.052274] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1091.252112] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1095.668409] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1095.864314] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1096.064169] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1096.264062] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1100.583478] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1100.780288] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1100.980153] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1101.180049] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1109.491275] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1109.689026] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1109.888921] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1110.088758] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1118.296270] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1118.493801] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1118.693643] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1118.893546] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1127.096333] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1127.294615] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1127.494433] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1127.694296] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1135.902657] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1136.099430] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1136.299343] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1136.499101] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1152.793189] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1152.989699] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1153.189487] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1153.389378] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1161.594923] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1161.794403] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1161.994249] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1162.194122] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1170.400377] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1170.599170] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1170.799065] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1170.998915] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1179.303667] wlan0: authenticate with 00:24:6c:73:7f:90 (try 1)
[ 1179.305983] wlan0: authenticated
[ 1179.306305] wlan0: associate with 00:24:6c:73:7f:90 (try 1)
[ 1179.308553] wlan0: RX AssocResp from 00:24:6c:73:7f:90 (capab=0x411 status=0 aid=2)
[ 1179.308559] wlan0: associated
[ 1179.312937] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1196.178228] wlan0: no IPv6 routers present
[ 1452.235407] wlan0: authenticate with 00:24:6c:73:7f:80 (try 1)
[ 1452.237156] wlan0: 00:24:6c:73:7f:80 denied authentication (status 17)
[ 1488.464412] wlan0: deauthenticating from 00:24:6c:73:7f:90 by local choice (reason=2)
[ 1488.531954] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1488.531958] cfg80211: Restoring regulatory settings
[ 1488.531964] cfg80211: Calling CRDA to update world regulatory domain
[ 1488.534490] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1488.534493] cfg80211: World regulatory domain updated:
[ 1488.534494] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1488.534496] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1488.534498] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1488.534499] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1488.534501] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1488.534502] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1488.536103] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1488.735567] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1488.935393] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1489.135378] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1492.656815] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1492.663449] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[ 1492.780419] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1493.015668] r8169 0000:03:00.2: PME# enabled
[ 1493.050269] r8169 0000:03:00.2: PME# disabled
[ 1493.058753] r8169 0000:03:00.2: eth0: link down
[ 1493.059934] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1493.250281] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1493.323302] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1493.329917] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[ 1493.441399] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1501.041900] wlan0: authenticate with 00:24:6c:73:7f:90 (try 1)
[ 1501.043298] wlan0: authenticated
[ 1501.043809] wlan0: associate with 00:24:6c:73:7f:90 (try 1)
[ 1501.045684] wlan0: RX AssocResp from 00:24:6c:73:7f:90 (capab=0x411 status=0 aid=2)
[ 1501.045690] wlan0: associated
[ 1501.049910] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1512.140244] wlan0: no IPv6 routers present
[ 1527.875389] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1527.875397] cfg80211: Restoring regulatory settings
[ 1527.875403] cfg80211: Calling CRDA to update world regulatory domain
[ 1527.880725] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1527.880731] cfg80211: World regulatory domain updated:
[ 1527.880733] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1527.880738] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1527.880742] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1527.880745] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1527.880749] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1527.880752] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1531.036965] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1531.234331] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1531.434339] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1531.634316] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1532.631824] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1532.638464] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[ 1532.756915] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1533.019326] r8169 0000:03:00.2: PME# enabled
[ 1533.061976] r8169 0000:03:00.2: PME# disabled
[ 1533.070435] r8169 0000:03:00.2: eth0: link down
[ 1533.072423] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1533.179138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1533.282467] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1533.289102] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[ 1533.399892] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1541.067319] wlan0: authenticate with 00:24:6c:73:7f:90 (try 1)
[ 1541.068559] wlan0: authenticated
[ 1541.068904] wlan0: associate with 00:24:6c:73:7f:90 (try 1)
[ 1541.070800] wlan0: RX AssocResp from 00:24:6c:73:7f:90 (capab=0x411 status=0 aid=2)
[ 1541.070808] wlan0: associated
[ 1541.075495] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1551.623909] wlan0: no IPv6 routers present
[ 1633.066102] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1633.265152] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1633.465121] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1633.665092] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1644.778705] wlan0: deauthenticating from 00:24:6c:73:7f:90 by local choice (reason=2)
[ 1644.782796] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1644.782803] cfg80211: Restoring regulatory settings
[ 1644.782809] cfg80211: Calling CRDA to update world regulatory domain
[ 1644.788086] wlan0: direct probe to 00:24:6c:73:7f:80 (try 1/3)
[ 1644.789089] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1644.789096] cfg80211: World regulatory domain updated:
[ 1644.789100] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1644.789106] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1644.789112] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1644.789117] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1644.789122] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1644.789127] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1644.985454] wlan0: direct probe to 00:24:6c:73:7f:80 (try 2/3)
[ 1645.185435] wlan0: direct probe to 00:24:6c:73:7f:80 (try 3/3)
[ 1645.385302] wlan0: direct probe to 00:24:6c:73:7f:80 timed out
[ 1647.548278] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1647.554897] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[ 1647.673399] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1647.853779] r8169 0000:03:00.2: PME# enabled
[ 1647.888739] r8169 0000:03:00.2: PME# disabled
[ 1647.897163] r8169 0000:03:00.2: eth0: link down
[ 1647.898829] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1648.051487] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1648.157918] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1648.164569] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[ 1648.280814] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```My campus has a WPA2-PEAP network and it also has an open network. I have only been able to connect to the wpa2 one and that is the one that works rarely. I have never been able to connect to the open one with this laptop.

I have another laptop that is an older Lenovo with Ubuntu on it and that one works just fine -- connects instantly to both the wpa2 and the open network.

I have two external wireless usb adapters and when I use either of them I can connect but having to use that defeats the purpose of having  built in wireless card.

Is anyone else having this issue? Or is it just me and my laptop. I am tired I was up all night trying to get this to work and I am a bit sick of it.

Thank you for your time.
Side note: while typing this I kept count of the amount of times the wireless dropped out... seven times.

---

### Post by BrandonIngalls on 2012-09-20
Here is a video to go along with my post.

[https://dl.dropbox.com/u/35295310/pos.mkv](https://dl.dropbox.com/u/35295310/pos.mkv)

---

### Post by gaussian on 2012-09-21
Really shooting in the dark here, but try this (it cannot hurt):

```

sudo rmmod iwlwifi
sudo modprobe  iwlwifi bt_coex_active=0 

```

Other than that, out of ideas.

---

### Post by joe4ska on 2012-09-22
Hi Brandon,
A few longshots I'd try if you haven't already
Have you reinstalled the latest System76 Driver at [http://planet76.com/repositories/](http://planet76.com/repositories/) ? 
Have you tried another official official Ubuntu variant like Xubuntu, Kubuntu or Lubuntu to see if the problem is somehow specific to Ubuntu?

Does this problem only happen while on campus?

Does your campus offer IT support? Perhaps one of the server techs is a Linux guru.

I'm using the same wifi card in my Lemu4 and I have had similar problems on the college campus where I work using their open network. I suspect that it may have something to do with the wifi on my campus, too many users or not enough available IP addresses, perhaps the router(s) are old or unreliable and don't support the latest generation of intel wifi cards like they should.

If you happen to have a unused wifi router you could repeat the campus wifi signal or set up your own network if you live on campus.
[]("http://planet76.com/repositories/")

---

### Post by BrandonIngalls on 2012-09-23
I just thought I should post an update to this thread.
System76 has shipped me a new wireless card and when I get it I will test to see if it works. If it doesn't work still I will just stuck with the broadcom card I bought off of a friend here. That one works just fine with no issues whatsoever.

---

### Post by Pithikos on 2012-10-04
> **BrandonIngalls said:**
> I just thought I should post an update to this thread.
System76 has shipped me a new wireless card and when I get it I will test to see if it works. If it doesn't work still I will just stuck with the broadcom card I bought off of a friend here. That one works just fine with no issues whatsoever.

What are the results? I have the same issue with a Samsung series-5. Many disconnects and slow internet at campus. Sometimes it works fine though.

---

### Post by BrandonIngalls on 2012-10-04
> **Pithikos said:**
> What are the results? I have the same issue with a Samsung series-5. Many disconnects and slow internet at campus. Sometimes it works fine though.

They have yet to ship me a new card... So there is no real resolution as of yet.

---

### Post by BrandonIngalls on 2012-10-08
> **BrandonIngalls said:**
> They have yet to ship me a new card... So there is no real resolution as of yet.

I am done with System76. I will keep the laptop I bought from them but I will not buy another one. It has been weeks and they never shipped a new wireless card. I have asked them to cancel the order for one because the broadcom one I bought works just fine. I really should have gone for a Lenovo -- at least lenovo would have shipped me the replacement part in a timely fashion.

---

### Post by DomIncollingo on 2012-10-08
Ouch.  Thanks for your update.  I had been thinking of buying a Gazelle, but I think I will pass.  I've heard lots of horror stories. And my 2-year old Serval is crashing once or twice a week. Very frustrating.

Looks like it's time to look into a Mac - or maybe try ZaReason so I can stick with Linux.

---

### Post by isantop on 2012-10-10
> **BrandonIngalls said:**
> I am done with System76. I will keep the laptop I bought from them but I will not buy another one. It has been weeks and they never shipped a new wireless card. I have asked them to cancel the order for one because the broadcom one I bought works just fine. I really should have gone for a Lenovo -- at least lenovo would have shipped me the replacement part in a timely fashion.

What's your case number? I'll check it to find out what happened. This experience is far below our quality standards for service.

---

### Post by BrandonIngalls on 2012-10-10
> **isantop said:**
> what's your case number? I'll check it to find out what happened. This experience is far below our quality standards for service.

2405

---

### Post by isantop on 2012-10-10
> **BrandonIngalls said:**
> 2405

I see that we've gone ahead and cancelled it for you. If you like, I can still have them send the part out. I'll make sure it goes out in a timely manner as well.

---

### Post by BrandonIngalls on 2012-10-10
That is alright. This whole process has been way more than I signed on for. I currently have a lesser wireless card but I will chalk it up as a loss that is my fault. I should have listened to some of the other reviews/horror stories I had seen online. But it works as I have it now -- save for the weekly complete lock up.

---

### Post by lhb1142 on 2012-10-10
> **BrandonIngalls said:**
> That is alright. This whole process has been way more than I signed on for. I currently have a lesser wireless card but I will chalk it up as a loss that is my fault. I should have listened to some of the other reviews/horror stories I had seen online. **But it works as I have it now -- save for the weekly complete lock up**.

Dear Brandon,

Reinstalling Ubuntu from its discs means you have installed a 3.2.x version of the Linux Kernel. This version (and earlier versions) of the kernel are not compatible with the 3rd Generation "Ivy Bridge" processors.

I recommend that you add the "[UpUbuntu]("https://launchpad.net/~upubuntu-com/+archive/kernel")" repository to your < Update Manager -> Settings -> Software Sources > list and then install the Linux kernel version 3.3.6.

This will eliminate the freezing you are experiencing.

As the new "Quantal Quetzel" version (Ubuntu 12.10) will be introduced next week, you could wait for that introduction and, when you upgrade to that version, a much later kernel version (I believe 3.5.x) will be installed along with it. That too will solve your freezing problem.

Best of luck.

Lawrence

---

