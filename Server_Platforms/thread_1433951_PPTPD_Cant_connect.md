---
title: "PPTPD Cant connect"
date: 2010-03-19
forum: Server Platforms
---

### Post by jenza85 on 2010-03-19
Hello

Have installed pptpd on my webserver.
The idea is to connect to it via VPN and then access  their web folder via samba distribution.

I was able to login via VPN but has  probably made some changes, the question is just where!?

I send the configfile och results from netstat.

pptpd.conf
```
#
###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#       Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#       Specifies the location of the PPP options file.
#       By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#       Turns on (more) debugging to syslog
#
#debug

# TAG: stimeout
#       Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#       Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#       Turns on broadcast relay to clients from interface <if>
#
#bcrelay eth1

# TAG: localip
# TAG: remoteip
#       Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of  the
#       routing.  But if you want to use MS-Windows networking, you  should
#       use IP addresses out of the LAN address space and use the  proxyarp
#       option in the pppd options file, or run bcrelay.
#
#       You can specify single IP addresses seperated by commas or you  can
#       specify ranges, or both. For example:
#
#               192.168.0.234,192.168.0.245-249,192.168.0.254
#
#       IMPORTANT RESTRICTIONS:
#
#       1. No spaces are permitted between commas or within addresses.
#
#       2. If you give more IP addresses than MAX_CONNECTIONS, it will
#          start at the beginning of the list and go until it gets
#          MAX_CONNECTIONS IPs. Others will be ignored.
#
#       3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#          you must type 234-238 if you mean this.
#
#       4. If you give a single localIP, that's ok - all local IPs will
#          be set to the given one. You MUST still give at least one  remote
#          IP for each simultaneous client.
#
# (Recommended)
localip 192.168.2.1
remoteip 192.168.2.20-192.168.2.30
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245

``````
root@srv01:~# netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:993             0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:995             0.0.0.0:*                LISTEN
tcp        0      0 127.0.0.1:10024         0.0.0.0:*                LISTEN
tcp        0      0 127.0.0.1:10025         0.0.0.0:*                LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:587             0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:110             0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:143             0.0.0.0:*                LISTEN
tcp        0      0 127.0.0.1:10031         0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*                LISTEN
tcp        0      0 127.0.0.1:2000          0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:465             0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:21              0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*                LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*                LISTEN
tcp6       0      0 :::22                   :::*                     LISTEN

```

---

