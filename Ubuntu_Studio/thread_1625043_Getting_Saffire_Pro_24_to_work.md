---
title: "Getting Saffire Pro 24 to work"
date: 2010-11-18
forum: Ubuntu Studio
---

### Post by prokoudine on 2010-11-18
Hi,

So, I have here: 10.04, FFADO built from stable SVN.

$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2010-11-18 22:42 /dev/raw1394

Nevertheless...

$ ffado-dbus-server

 Discovering devices...
04260463525: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
04260463565: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
04260463574: Error (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
04260963682: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
04260963736: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
04261462855: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
04261462873: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
04261462890: Error (avc_avdevice.cpp)[  88] probe: Subunit info command failed
 Starting DBUS service...
 Running... (press ctrl-c to stop & exit)

And if I run ffado-mixer after that, it says "No supported device found."

Just in case when I switch the saffire on, /var/log/messages has this:

Nov 18 23:04:37 darkroom kernel: [ 2447.360065] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Nov 18 23:04:37 darkroom kernel: [ 2447.360071] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[00130e0401c0173c]
Nov 18 23:04:41 darkroom kernel: [ 2451.496020] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Nov 18 23:04:44 darkroom kernel: [ 2454.112017] ieee1394: Error parsing configrom for node 0-00:1023
Nov 18 23:04:44 darkroom kernel: [ 2454.793019] ieee1394: Error parsing configrom for node 0-01:1023
Nov 18 23:04:45 darkroom kernel: [ 2455.085804] ieee1394: Node reactivated: ID:BUS[0-00:1023]  GUID[00130e0401c0173c]

I'm really neither hardware, no system administration person despite of having used linux for past 11 years. Could eanybody please enlighten me what's wrong?

---

### Post by JC Cheloven on 2010-12-21
Hi, you marked this as "solved". Could you please give us a hint? It's of my interest, for example ;)
Thanks

---

### Post by mango42 on 2010-12-29
Hi - if your Pro24 issue is still 'Unsolved' [AutoStatic]("https://launchpad.net/~autostatic/+archive/ffado/+packages") has it mostly sussed.

---

