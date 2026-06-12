---
title: "VPN server Routing problem?"
date: 2008-02-01
forum: Server Platforms
---

### Post by n3m3s1s4i on 2008-02-01
Hello All, I am a little lost at the moment trying to get my vpn server working correctly.
I can connect to it via a MS vpn into the box fine. Once i am connected to it I cannot see the rest of the network. Any help would be handy. I know it is something to do with a route / setting in a file somewhere, not sure which or what.

Let me give you the scenario.

2 interfaces ETH1 and ETH2
ETH 2 - WAN to router
ETH1 - LAN to Network. Now there is one thing i want access to mainly on the network and that is our Terminal Server on 192.6.31.253
How do I get the Home PC once connected to see that server?

/etc/network/interfaces
auto lo eth1 eth2
iface lo inet loopback

iface eth1 inet static
address 192.8.41.18
netmask 255.255.255.0
gateway 192.8.41.1

iface eth2 inet static
address 192.6.32.220
netmask 255.255.255.0
gateway 192.6.32.246


/etc/pptpd.conf
###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################
# TAG: ppp
#    Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd
# TAG: option
#    Specifies the location of the PPP options file.
#    By default PPP looks in '/etc/ppp/options'
#
option    /etc/ppp/options.pptpd
# TAG: debug
#    Turns on (more) debugging to syslog
#
#debug
# TAG: stimeout
#    Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10
# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam
# TAG: logwtmp
#    Use wtmp(5) to record client connections and disconnections.
#
# logwtmp        ## comment this out!! broken deb package!!
# TAG: bcrelay
#    Turns on broadcast relay to clients from interface
#
#bcrelay eth1
# TAG: localip
# TAG: remoteip
#    Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#    You can specify single IP addresses seperated by commas or you can
#    specify ranges, or both. For example:
#
#        192.168.0.234,192.168.0.245-249,192.168.0.254
#
#    IMPORTANT RESTRICTIONS:
#
#    1. No spaces are permitted between commas or within addresses.
#
#    2. If you give more IP addresses than MAX_CONNECTIONS, it will
#       start at the beginning of the list and go until it gets
#       MAX_CONNECTIONS IPs. Others will be ignored.
#
#    3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#       you must type 234-238 if you mean this.
#
#    4. If you give a single localIP, that's ok - all local IPs will
#       be set to the given one. You MUST still give at least one remote
#       IP for each simultaneous client.
#
# (Recommended)
localip    192.6.32.220
remoteip    192.6.32.221-225
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245

/etc/ppp/options.pptpd
lock
ms-dns 192.6.32.220
ms-wins 192.6.32.220
debug
name pptp-vpn
auth
proxyarp
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
chapms-strip-domain
lcp-echo-failure 10
lcp-echo-interval 30
nobsdcomp

Output of netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.6.31.0      192.8.41.1      255.255.255.0   UG        0 0          0 eth1
192.8.41.0      0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.8.40.0      192.8.41.19     255.255.255.0   UG        0 0          0 eth1
192.8.39.0      192.8.41.1      255.255.255.0   UG        0 0          0 eth1
192.6.32.0      0.0.0.0         255.255.255.0   U         0 0          0 eth2
0.0.0.0         192.6.32.246    0.0.0.0         UG        0 0          0 eth2
0.0.0.0         192.8.41.1      0.0.0.0         UG        0 0          0 eth1


Thank you for any help - please ask if you need more information
ta

---

### Post by The Cog on 2008-02-02
I wonder if you have IP forwarding enabled on your server. Try this command to see:
```
cat /proc/sys/net/ipv4/ip_forward
```
1 means it is forwarding, 0 means it's not. 
If it isn't this command will turn forwarding on:
```
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
```
then try the VPN again. If that fix works, you need to make it permanent (after a reboot) by editing **/etc/sysctl.conf**
and adding this line:
```
net.ipv4.ip_forward=1
```
There's a commented-out line in the file already that claims to enable forwarding but ignore it - it doesn't work. Use the line I gave you.

P.S.
While youre at it, it might be a good idea to configure spoof protection by uncommenting the line about rp_filter.

---

