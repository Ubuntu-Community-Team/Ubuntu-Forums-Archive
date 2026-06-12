---
title: "Time not kept on NTP server"
date: 2011-02-07
forum: Server Platforms
---

### Post by radiognome on 2011-02-07
I try to have one NTP-server on my network and have others synchronize with it.

I installed NTP on one (fysical) server and tried various variations of /etc/ntp.conf which all lead to the following:

[LIST]
[*]I stop NTP.
[*]set my time with ntpdate from one of the timeservers
[*]I start NTP 
[*]My server runs the correct time for a couple of minutes, and then jumps 257.3 seconds backwards and keeps this distance to the timeservers.
[*]I stop NTP .... set time ... start NTP 15 minutes later.... 257.3 seconds in the past.... etc...
[/LIST]

The clients follow the server-time or find huge offsets depending on whether they use only this or other timeservers as well.

Also when I don't start NTP, my server falls back about 257 seconds somewhere within 10 minutes and stays there. I did set the hardware-clock with hwclock --systohc to a 'propper' time, but this did not influence the behavior.

Anyone got a clue? I am out of them. After a wile, ntpdc -p reads:

```
     remote           local      st poll reach  delay   offset    disp
=======================================================================
*ipv6.net        192.168.34.90    2   64  377 0.03630 257.51047 0.03069
=europium.canoni 192.168.34.90    2   64  377 0.01447 257.52319 0.03081
=nfs01.ip2.net   192.168.34.90    3   64  377 0.03232 257.48066 0.03059
^192.168.34.255  192.168.34.95   16   64    0 0.00000  0.000000 4.00000
=ntp.networking4 192.168.34.90    2   64  377 0.02934 257.51364 0.03061
=ntp0.mediamatic 192.168.34.90    2   64  377 0.02516 257.51202 0.03073

```

in which 192.168.34.255 is my local subnet.


Thanks for reading,

Martin

p.s. This is the last ntp.conf I used

```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server 0.debian.pool.ntp.org iburst
server 1.debian.pool.ntp.org iburst
server 2.debian.pool.ntp.org iburst
server 3.debian.pool.ntp.org iburst
server ntp.ubuntu.com

#server europe.pool.ntp.org


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
#restrict 192.168.34.0 mask 255.255.255.0 nomodify notrap

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.34.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

---

