---
title: "ntp server stops responding after a few days"
date: 2009-01-16
forum: Server Platforms
---

### Post by davidshere on 2009-01-16
I work in an organization with ~60 computers.  For clock synchronization, I would like to set up the following scenario:

We have one computer, "hawkeye", at 10.xxx.xxx.xxx that runs 804 and ntp.  It is set to get its time from pool.ntp.org and ntp.ubuntu.com.  It is configured to answer time requests from other machines in the building.  The other machines are set to use 10.xxx.xxx.xxx (hawkeye's IP) as their time server.

I installed ntp on hawkeye and configured /etc/ntp.conf to my above specifications.  Everything works fine until ~24 hours later, when the ntp server on hawkeye seems to not respond.  When I run ntpdate 10.xxx.xxx.xxx on the client machines, I get "no server suitable for synchronization found".

If I restart ntp (/etc/init.d/ntp restart), sometimes the server starts responding again.  If that doesn't work, I reboot the computer.

**Any advice or suggestions will be greatly appreciated. ** The follwing is the ntp.conf on hawkeye.

```
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server pool.ntp.org
server ntp.ubuntu.com

# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
#restrict -4 default kod notrap nomodify nopeer noquery
#restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust
restrict 192.168.xxx.xxx mask 255.255.255.0 nomodify notrap
restrict 10.xxx.xxx.xxx     mask 255.255.255.0 nomodify notrap

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient
```

---

### Post by davidshere on 2009-01-19
I think I've answered my own question.  I've been using only two remote servers for synchronization, and this causes problems.  From [http://support.ntp.org/bin/view/Support/ConfiguringNTP#Section_6.10.](http://support.ntp.org/bin/view/Support/ConfiguringNTP#Section_6.10.)
[B]
"First, ntpd needs a majority of servers to agree on the time before it can sync. ... If you have two or three servers and they disagree, no majority will be found.  If you are going to have server or peer lines in ntp.conf I recommend having at least four or five of them..."[/B]

When I had only two remote servers configured, I noticed that these lines in the log eventually stopped:  
```
Jan 19 04:03:24 hawkeye ntpd[4554]: synchronized to 132.163.4.103, stratum 1
```

... and after that the server stopped functioning.  It appears that because there was no majority of servers that agreed, my server looks like it gave up, and that's why the clients said "no suitable servers could be found".  It seems that the clients asked hawkeye for the time, and hawkeye replied that it did not have a reliable time to give, and because the clients didn't have any other servers configured, they gave the above error.

On Friday I configured the following on hawkeye at /etc/ntp.conf :

```
# You do need to talk to an NTP server or two (or three).
server pool.ntp.org iburst
server ntp.ubuntu.com iburst
server 0.pool.ntp.org iburst
server 1.pool.ntp.org iburst
server 2.pool.ntp.org iburst
server 3.pool.ntp.org iburst
server time.nist.gov iburst
server time-a.nist.gov iburst
server time-b.nist.gov iburst
server time-a.timefreq.bldrdoc.gov iburst
server time-b.timefreq.bldrdoc.gov iburst
server time-c.timefreq.bldrdoc.gov iburst
```

Hawkeye's ntp server has been on all weekend, and the "... synchronized to 132.163.4.103, stratum 1" lines appear at regular intervals.  Windows and Ubuntu clients alike are successfully synchronizing to hawkeye.

I'll mark this as solved when that feature is enabled again.  I hope this page helps others who may have this same problem.

---

