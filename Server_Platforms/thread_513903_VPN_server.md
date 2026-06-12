---
title: "VPN server"
date: 2007-07-31
forum: Server Platforms
---

### Post by virushioyo on 2007-07-31
hi all,

i new to ubuntu server, i decide to setup a vpn server in my home. 

i already apt-get install pptpd on my server and apt-get network-manager-pptp pptp-linux in my ubuntu 7.04 laptop

i been grab alot of tutorial by googling but still cant work and ask gurus for help
here is my server configuration:
1. vi /etc/pptpd.conf
###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################
# TAG: ppp
#	Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd
# TAG: option
#	Specifies the location of the PPP options file.
#	By default PPP looks in '/etc/ppp/options'
#
option	/etc/ppp/pptpd-options
# TAG: debug
#	Turns on (more) debugging to syslog
#
#debug
# TAG: stimeout
#	Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10
# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam
# TAG: logwtmp
#	Use wtmp(5) to record client connections and disconnections.
#
# logwtmp        ## comment this out!! broken deb package!!
# TAG: bcrelay 
#	Turns on broadcast relay to clients from interface 
#
#bcrelay eth1
# TAG: localip
# TAG: remoteip
#	Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#	You can specify single IP addresses seperated by commas or you can
#	specify ranges, or both. For example:
#
#		192.168.0.234,192.168.0.245-249,192.168.0.254
#
#	IMPORTANT RESTRICTIONS:
#
#	1. No spaces are permitted between commas or within addresses.
#
#	2. If you give more IP addresses than MAX_CONNECTIONS, it will
#	   start at the beginning of the list and go until it gets 
#	   MAX_CONNECTIONS IPs. Others will be ignored.
#
#	3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#	   you must type 234-238 if you mean this.
#
#	4. If you give a single localIP, that's ok - all local IPs will
#	   be set to the given one. You MUST still give at least one remote
#	   IP for each simultaneous client.
#
# (Recommended)
localip	192.168.1.1
remoteip	192.168.1.90-99
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245
speed	115200

2. then vi /etc/ppp/options
lock

3. then touch /etc/ppp/pptpd-options
4. then edit vi /etc/ppp/pptpd-options
lock
ms-dns 192.168.1.1
ms-wins 192.168.1.1
domain my.domain.com
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

5. next vi /etc/ppp/chap-secrets
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
username  vpn  password  "*"

6. then /etc/init.d/pptp restart

my laptop configuration(GUI)
righ click the network icon -> select configure vpn -> gateway = my server fixed ip 

it prompt out the password dialog and when i key in the username and password like what i set in chap-secret. 

the network icon show attempting to connect.........then after tat nothing happen.

need guru help to check my configuration ok or not? thanks

---

