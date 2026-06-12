---
title: "NTP failing to synch - offset too large"
date: 2010-06-11
forum: Server Platforms
---

### Post by mkotasek on 2010-06-11
Hi all,

I'm having trouble keeping NTP synchronized and able to provide time updates to other devices on the private network.  I believe this is because the server has a too large of offset, that causes all NTP clients syncing through the server to fail.

I have two setups, one working, one failing, with mostly identical installation and settings.  

Setup A is the working setup, as I will name it, is ubuntu server edition 8.04 with kernel 2.6.33.1. ntpd version is 4.2.4p4.

ntpq -p outputs this information:
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
*europium.canoni 193.79.237.14    2 u  925 1024  377  101.851    0.194   0.328

ntp.conf is:

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
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
restrict 192.168.0.0 mask 255.255.0.0 notrust notrap

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

Devices on the 192.168.x.x network can sync with it without issue.

Server B, ubuntu server edition 8.04, 2.6.33.1 kernel, and ntpd version 4.2.4p4.

ntpq -p reports:

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 europium.canoni 193.79.237.14    2 u   28   64   77  101.669  -337749 151045.

The configuration file is also identical:

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
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
#restrict 192.168.0.0 mask 255.255.0.0 notrust notrap
restrict 192.168.0.0 mask 255.255.0.0 nomodify notrap


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

So I'm pretty confused.  Both servers are identical in this setup, but every time I try to restart the ntpd service on server B, the offset quickly becomes the large negative value again.  

Any clues to what is going on would be much appreciated.

Thanks in advance,
Max

---

### Post by mkotasek on 2010-06-14
Bump.

---

