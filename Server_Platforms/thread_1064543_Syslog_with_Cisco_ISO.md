---
title: "Syslog with Cisco ISO"
date: 2009-02-08
forum: Server Platforms
---

### Post by LWTechsupport on 2009-02-08
Hi I am currently running a Ubuntu 8.04 server and need some help with syslogd. 

My syslog.conf has these lines added to them
```

#
# Router Logging starts here.
#
local3.*                        -/var/log/cisco/ciscofw.log
local4.*                        -/var/log/cisco/ciscold.log
local6.*                        -/var/log/cisco/ciscocss.log
local7.debug                    -/var/log/cisco/ciscoac1.log
local7.notice                   -/var/log/cisco/ciscoinfo.log

```

I have the -r flag turned on for remote logging and I am receiving a single debug message from the router.

I have added the udp 514 port in iptables just to be sure as well

```

ACCEPT     udp  --  Snort.usapsys.com    lswitcha.*******.com udp dpt:syslog
ACCEPT     udp  --  Snort.usapsys.com    hswitchb.*******.com udp dpt:syslog

```

Yet I am only getting a single log and cannot figure out why.
I am trying to get all router WAN, LAN, and router logins logged.

I do not have access to the routers, but our network admin setup the logging trap level at 7.
Doesn't this mean that all messages from the router should be logged? Or is this just debug messages only?

I am kind of new to the linux OS and am learning as I go.
Could someone please help with this?

---

