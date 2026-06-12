---
title: "Cron activity"
date: 2008-11-14
forum: Security
---

### Post by learning208 on 2008-11-14
In my syslog I saw a change from cron.daily to cron.hourly
Can this change occur without any input from root?

In the past I was not the only person with root access and I think they may have set something up to monitor my activity I did not initiate a cron in the first place and didn't change it.

Also I called the person I suspected to ask and while on the phone with them I had the syslog open and saw a pid file being deleted and some other activity (see below).  I wasn't touching anything at that point.  I quickly disconnected from the network.

Nov 14 16:09:26  There is already a pid file /var/run/dhclient.pid with pid 8224

Nov 14 16:09:26  dhclient: killed old client process, removed PID file
Nov 14 16:09:26  dhclient: Listening on LPF/eth1/00:1b::cb:ac:32

Nov 14 16:09:26  dhclient: Sending on   LPF/eth1/00:1b::cb:ac:32

Nov 14 16:09:26  dhclient: Sending on   Socket/fallback

Nov 14 16:09:26  dhclient: DHCPRELEASE on eth1 to 192.168.. port 67

Nov 14 16:09:26  avahi-daemon[5095]: Withdrawing address record for 192.168.. on eth1.

Nov 14 16:09:26  avahi-daemon[5095]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.10.

Nov 14 16:09:26  avahi-daemon[5095]: Interface eth1.IPv4 no longer relevant for mDNS.

Nov 14 16:09:28  avahi-daemon[5095]: Withdrawing address record for fe80::21b:77ff:fecb: on eth1.

Nov 14 16:09:28  dhclient: receive_packet failed on eth1: Network is down




Does any of this have the ring of secretive access and trying to cover tracks?  I wasn't touching anything at that point.

thanks alot for your help

---

### Post by mssever on 2008-11-15
You didn't specify what the change from cron.daily to cron.hourly was. It could be some person changing files for some reason. Or it could be some program that runs as root that made the change. It could be legit, or it might not be. It's impossible to say without knowing what script was changed--and it might be necessary to know how the script was changed.

As far as the syslog messages you posted go, those are perfectly normal. They happen automatically on a regular basis, and I believe they're the result of the DHCP lease being renewed. They're nothing to be concerned about.

---

