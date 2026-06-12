---
title: "NTPD won't sync"
date: 2011-12-14
forum: Server Platforms
---

### Post by sirgad on 2011-12-14
Hi,

NTPD 4.2.6.p2 on Ubuntu 11.10 Kernel 3.0.0-13-server.  *ntp.conf* is as follows:

```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable

# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See http://www.pool.ntp.org/join.html for
# more information.
#server 0.ubuntu.pool.ntp.org
#server 1.ubuntu.pool.ntp.org
#server 2.ubuntu.pool.ntp.org
#server 3.ubuntu.pool.ntp.org
## The named entries are all Stratum Two servers taken from here:
## http://support.ntp.org/bin/view/Servers/StratumTwoTimeServers
## The pool entries are all taken from here:
## http://www.pool.ntp.org/zone/uk
server ntp.cis.strath.ac.uk iburst #Glasgow
server 0.uk.pool.ntp.org #UK Pool Entry 1
server ntp2b.mcc.ac.uk #Manchester
server 1.uk.pool.ntp.org #UK Pool Entry 2
server 2.uk.pool.ntp.org #UK Pool Entry 3

# Use Ubuntu's ntp server as a fallback.
server ntp.ubuntu.com

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

No matter how long I wait, I never receive the following message in my syslog:

```
hostname ntpd[xxxx]: synchronized to x.x.x.x, stratum 2
```

According to the [_walkthrough_]("http://ubuntuforums.org/showthread.php?t=862620") I'm following, this indicates I'm not properly synchronized.  All *syslog* actually reports is this:

```
Dec 14 22:06:07 ubuntu-server ntpd[16006]: ntpd 4.2.6p2@1.2194 Fri Sep  2 18:42:25 UTC 2011 (1)
Dec 14 22:06:07 ubuntu-server ntpd[16007]: proto: precision = 1.257 usec
Dec 14 22:06:07 ubuntu-server ntpd[16007]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Dec 14 22:06:07 ubuntu-server ntpd[16007]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Dec 14 22:06:07 ubuntu-server ntpd[16007]: Listen and drop on 1 v6wildcard :: UDP 123
Dec 14 22:06:07 ubuntu-server ntpd[16007]: Listen normally on 2 lo 127.0.0.1 UDP 123
Dec 14 22:06:07 ubuntu-server ntpd[16007]: Listen normally on 3 eth0 <ipv4 address> UDP 123
Dec 14 22:06:07 ubuntu-server ntpd[16007]: Listen normally on 4 eth0 <ipv6 address> UDP 123
Dec 14 22:06:07 ubuntu-server ntpd[16007]: Listen normally on 5 lo ::1 UDP 123
```

Running *ntpq -c* reports the following:

```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*ntp1.cis.strath 193.62.22.74     2 u   65  128  377   33.158    0.273  28.907
+fifi.v4.colo.m. 194.100.2.198    2 u   54  128  377   15.933   -6.764  27.869
+dir.mcc.ac.uk   194.66.31.14     2 u  111  128  377   28.767    6.354  32.016
+scarlett.lon.re 216.218.192.202  2 u  116  128  377   28.055    0.359  55.242
+resntp-a-vip.lo 77.75.105.169    3 u  113  128  377   20.382   -0.889  24.030
+europium.canoni 193.79.237.14    2 u  116  128  377   23.073    0.024  15.896
```

The IRC channel is dead so no help there.  I can't find any other info on this topic.  Can someone help me out here?

---

### Post by warehouse@karmickoala on 2011-12-14
Hi there, I usually follow these steps:
Terminal>sudo ntpdate (url of the ntp server) ENTER
That's It. And It Works All The Time

---

### Post by sirgad on 2011-12-14
Hi,

Not quite what I'm looking for.  Anyone able to help with my current set-up instead of suggesting I abandon it entirely?

---

### Post by warehouse@karmickoala on 2011-12-14
Ok, Assuming That All The Necessary Packages Are Installed, Why Don't You Try One Server At A Time ? :-)

---

### Post by jonobr on 2011-12-14
Hello


If I remember right there should be a client packet going to the server on port 123 and then a server packet in response that provides the synch info

in that case,
maybe run

```
sudo tcpdump -i any -vvv port 123
```


See if anything goes out,
if you do see if anything comes back again

Cheers

Jonobr

---

### Post by sirgad on 2011-12-15
Turns out I am synched. The walkthrough I'm following is out of date - ntpd no longer reports synchronization in the logs.  This was relayed to me on the mailing list.

Thanks for responses - appreciated :)

---

