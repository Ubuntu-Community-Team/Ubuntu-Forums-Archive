---
title: "ntop Network Triffic Monitoring. Making sense of it."
date: 2011-06-05
forum: Server Platforms
---

### Post by Demented ZA on 2011-06-05
I installed ntop, it works, I can log into [http://myserver:3000](http://myserver:3000).

Only problem is that the information it represents is not as easy/intuitive as I expected.

Its like ntop doesn't understand my network hierarchy/topology. I'd like to tell ntop to monitor my network interface ppp0 (maybe a bad idea?) and I'd like to make it aware that 192.168.0.0/24 is my local network. Everything else is alien/internet traffic. I'd also like to be able to show IPv4 traffic only (by means of disabling routing of IPv6).

I know IPv6 is the future, but I'm definitely not making use of it yet, and would like to disable it until such a time that I understand it and am using it.

I'm running Ubuntu server with Shorewall as firewall, and the following interfaces:

br0 -> local network -> 192.168.0.0/24
Firewall System -> 192.168.0.1
ppp0 -> internet -> dynamic ip

I've configured /etc/ntop/ntop.conf to look like:
```
--user ntop
--daemon
--db-file-path /usr/share/ntop
--interface br0,ppp0
-m 192.168.0.0/24
--trace-level 3 # Which is the default
--http-server 3001
```then did a
```
sudo service ntop stop
sudo service ntop start
```but ntop still works on port 3000 indicating that it doesn't use the config file. I've found ntop stores some settings under /var/lib/ntop/init.cfg. Mine looks like this:
```
USER="ntop"
INTERFACES="br0"
```It seems to work, but it still doesn't recognize my local subnet etc and I can't set any of the other options.

Is ntop the right program? Are you guys using this or something else? If you are using ntop, what configurations did you use?

Thanks.

---

