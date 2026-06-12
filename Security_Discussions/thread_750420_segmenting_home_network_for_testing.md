---
title: "segmenting home network for testing"
date: 2008-04-09
forum: Security Discussions
---

### Post by jba6511 on 2008-04-09
Here is what I would like to accomplish. I want to setup a separate segment on my LAN for testing out new exploits, tools, etc. and still maintain the current segment for general use. I would like to be able to get out to the internet on my test segment to download patches, apps, etc. However, since this segment will most likely contain unpatched systems, I am worried about others also exploiting these systems to gain access into my LAN. What would be the best way to go about setting up this configuration? iptables, port forwarding?? I have a Dlink 625 DIR that I am currently using as a router as well as a Linksys WRT54G running OpenWRT.

---

### Post by FakeOutdoorsman on 2008-04-10
I think you're looking for a [DMZ]("http://en.wikipedia.org/wiki/Demilitarized_zone_%28computing%29").  I have the WRT54G with DD-WRT and it has the DMZ option: "Enabling this option will expose the specified host to the Internet. All ports will be accessible from the Internet."  I can apply this to certain IP addresses on my LAN, but I don't know if it will be segregated from the other LAN machines or not.

---

