---
title: "block ip range for a time interval"
date: 2011-04-05
forum: Security
---

### Post by corkscrew on 2011-04-05
I have never set up iptables before because my LAN is behind a router.

I want to block a range of ip addresses from 00:30 to 06:00 is this possible and how do you do it?

---

### Post by Cheesehead on 2011-04-05
One method:

IPtables commands can be scripted. So the scripts can be triggered by a cron job.

Create a new folder (I'll call it /etc/network/firewall-scripts) to put your new firewall scripts into.

Create two firewall scripts (/etc/network/firewall-scripts/overnight-firewall.sh and /etc/network/firewall-scripts/daytime-firewall.sh). These flush all the old rules and reload new rules from scratch each time they are run. They are run each time an interface comes up, and when the cron job tells them to.

(This is part of an example off my router. It is NOT complete, and will not provide full security. It's just to show you some of the sections you should have. Your interfaces will vary.)
```

#!/bin/sh
# daytime-firewall script.

PATH=/usr/sbin:/sbin:/bin:/usr/bin

# Delete all existing rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT

## Put all your custom stuff here

# This is the drop command for overnight. It's commented out on the daytime script. This is the only difference between the two scripts.
#iptables -I INPUT -s 221.0.0.0/255.0.0.0 -j DROP 

```

Finally, add cron jobs to fire off the scripts at the times you want:

```
# Root crontab
30 0 * * * root /bin/sh /etc/network/firewall-scripts/overnight-firewall.sh
00 6 * * * root /bin/sh /etc/network/firewall-scripts/daytime-firewall.sh
```

Since you still need a firewall when the system is restarted, add a firewall-startup script in /etc/if-up.d/ to figure which firewall script to use (based on the time) each time an interface comes up.

---

### Post by The Cog on 2011-04-06
A couple of additional suggestions:

The daytime and nighttime scripts could re-write a symlink to point to themselves. Then have the if-up script run the symlink. That way, whn the interface comes up, it runs the appropriate day/night config script.

These scripts will prevent new connections, but I think existing connections will not get cut off. To actively cut existing connections, I think the iptables tracking table needs clearing, something that the **conntrack** package will have a tool for.

---

### Post by bodhi.zazen on 2011-04-06
You can use time in iptables.

You do this in the OUTPUT chain (does not work so well on the INPUT chain).

```
iptables -A OUTPUT -o eth0 -p tcp -m multiport --dports 80,443 -m time --timestart 12:00 --timestop 13:00 -j ACCEPT

iptables -A OUTPUT -p tcp -m multiport --dports 80,443 -j DROP
```

allows web traffic over the lunch hour only.

[http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips)

Scroll down a bit ;)

---

### Post by The Cog on 2011-04-06
Well, I never knew that! I should read the entire man page from start to finish and see what other snippets I've been missing, as well as bodhizazen's notes.

---

### Post by Cheesehead on 2011-04-06
> **bodhi.zazen said:**
> You can use time in iptables.

Wicked cool!  Thank you!

---

### Post by bodhi.zazen on 2011-04-07
you are both welcome =)

---

