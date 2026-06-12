---
title: "Airodump wierd behaviour"
date: 2009-10-14
forum: Security
---

### Post by gabrielshier on 2009-10-14
Hey,
Lately got a new RaLink device for net monitoring. Worked for a few times and still workd perfectly well besides one wierd behaviour: when i set it to capture mode for a single network using airodump-ng it gets loads of beacons but almost no data. Is the reason a simple error or that the network is not broadcasting enought data?
Thanks,
Gab

(packet injection not helping...)

---

### Post by __p1n__ on 2009-10-14
A couple of things to check:

Did you switch the interface to monitoring with airmon-ng first?
Are you using mon0 as your airodump-ng interface?
What airodump-ng options are you using, are you filtering on BSSID or limiting the channel selection?

Hope that helps.

---

### Post by gabrielshier on 2009-10-14
*Did you switch the interface to monitoring with airmon-ng first?*
Yes. After shutting down the card and resetting the ip conf, switched it back on to the monitoring mode and got a confirmation from terminal.

*Are you using mon0 as your airodump-ng interface?*
I'm using ra0 as the monitoring interface since the card is detachable (USB).

*What airodump-ng options are you using, are you filtering on BSSID or limiting the channel selection?*
```
airodump-ng -w file -c 6 --bssid 00:11:22:33:44:55 ra0
```

---

### Post by __p1n__ on 2009-10-14
Just to confirm, is ra0 is the monitoring interface created by airmon-ng?

Otherwise if the network that you're monitoring is running on channel 6 and the BSSID in the command corresponds to its BSSID then it's either lightly used or you're too far away from the ap and/or its client to see all the traffic.

---

### Post by gabrielshier on 2009-10-14
Got it!
All needed to be done is removing all attempts of the ubuntu to connect to a network (without disabling the card!) and it works perfectly well!
Thanks :)

---

