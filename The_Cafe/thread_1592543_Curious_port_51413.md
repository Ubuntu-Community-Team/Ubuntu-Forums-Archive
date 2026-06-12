---
title: "Curious port 51413"
date: 2010-10-10
forum: The Cafe
---

### Post by MooPi on 2010-10-10
Transmission bit-torent client uses port 51413. I used Transmission to download Maverick Meerkat and  had to open this port to get past the firewall at my home. When I closed Transmission I also closed the port. I am now getting tons of port hits on 51413.  Why ? Does transmission or torrent clients hold an ip address for future use ? I'm doing a search on the subject but haven't found much.

I posted here because it's not a request for help just curious.

---

### Post by mikewhatever on 2010-10-10
Peers are still trying to connect, thats normal. By the way, why not leave it open and seed for others?

---

### Post by MooPi on 2010-10-10
I did but left and shut down for a couple of hours because I was switching boxes to load 10.10 later. Just under a 1-1 ratio in a couple of hours.

---

### Post by lovinglinux on 2010-10-10
The torrent client queries the tracker in regular intervals in order to retrieve the list of peers sharing the same file. When you close the client, your ip address is still listed on many peers clients as a potential peer to connect to, until they contact the tracker again to update their list. So after you close your client, you will still get many hits from some time. They will go away eventually. If you restart your router and connect again,  then you will get a new IP (if yours is dynamic) and these connections attempts will stop.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) for more info.

---

