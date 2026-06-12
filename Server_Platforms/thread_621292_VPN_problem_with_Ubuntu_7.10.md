---
title: "VPN problem with Ubuntu 7.10"
date: 2007-11-23
forum: Server Platforms
---

### Post by goatcabin on 2007-11-23
I am trying to connect to my company's VPN server via pptp. I have read several threads about this, including Lithorus'. It looks like it is working, but I cannot ping any machines on the VPN network and after 2 minutes the connection is broken.

First, here are the contents of my file "LL" in /etc/ppp/peers:

BEGIN file contents

Toshiba:root:/etc/ppp/peers> cat LL
#name of the connection
remotename LL

linkname LL

ipparam LL

#ip/dns to connect to

pty "pptp 66.172.234.1 --nolaunchpppd"

#domain name
#ame 

#username
user alan.shank

usepeerdns
require-mppe
refuse-eap

noauth

#add the default options from the pptp-linux package
file /etc/ppp/options.pptp

END file contents

Here are the contents of my /etc/ppp/options.pptp file:

BEGIN file contents:

# Lock the port
lock

# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
refuse-eap
refuse-chap
refuse-mschap

# Compression
# Turn off compression protocols we know won't be used
nobsdcomp
nodeflate

# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose with of the following sections you will use.  Note that MPPE
# requires the use of MSCHAP-V2 during authentication)

# [http://ppp.samba.org/](http://ppp.samba.org/) the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
require-mppe-128
# }}}

# [http://polbox.com/h/hs001/](http://polbox.com/h/hs001/) fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}

END file contents

I also put this script in /etc/ppp/ip-up.d

BEGIN script contents

#!/bin/sh
if [ "${PPP_IPPARAM}" = "LL" ]; then
  route add -net 10.1.0.0 netmask 255.255.0.0 dev ${IFNAME}
fi
ifconfig ${IFNAME} mtu 1400

END script contents

I ran this as root:

BEGIN debug output






Script pptp 66.172.234.1 --nolaunchpppd finished (pid 6458), status = 0x0
Modem hangup
Connect time 2.1 minutes.
Sent 1147917354 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 6499)

END debug output

AT this point, I had these processes running:

BEGIN ps output

root      6458  6447  0 11:04 pts/0    00:00:00 sh -c pptp 66.172.234.1 --nolaunchpppd
root      6461  6458  0 11:04 pts/0    00:00:00 pptp: GRE-to-PPP gateway on /dev/ptmx
root      6470     1  0 11:04 pts/0    00:00:00 pptp: call manager for 66.172.234.1

END ps output

It looks good, no? However, when I tried to ping any boxes on the internal network, I got 100% packet loss. When I tried traceroute, to either the external IP address of the VPN server, or the internal one, I got this:

BEGIN traceroute

Toshiba:root:/root> traceroute 10.1.31.1
traceroute to 10.1.31.1 (10.1.31.1), 30 hops max, 40 byte packets
send: No buffer space available
Toshiba:root:/root> traceroute 66.172.234.1
traceroute to 66.172.234.1 (66.172.234.1), 30 hops max, 40 byte packets
send: No buffer space available

END traceroute

Then after a couple of minutes, the debug output continues:

BEGIN debug output

Script pptp 66.172.234.1 --nolaunchpppd finished (pid 6458), status = 0x0
Modem hangup
Connect time 2.1 minutes.
Sent 1147917354 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 6499)
MPPE disabled
sent [LCP TermReq id=0x2 "MPPE disabled"]
Connection terminated.
Waiting for 1 child processes...
  script /etc/ppp/ip-down, pid 6499
Script /etc/ppp/ip-down finished (pid 6499), status = 0x0

END debug output

I noticed this line:

Cannot determine ethernet address for proxy ARP

On another forum, someone said this is just a warning and not a problem. ???

Also on another forum, someone posted his debug output, and it showed:

Jan 26 23:07:48 localhost pppd[1911]: local IP address 10.4.10.238
Jan 26 23:07:48 localhost pppd[1911]: remote IP address 10.4.8.1
Jan 26 23:07:48 localhost pppd[1911]: primary DNS address 151.196.0.38
Jan 26 23:07:48 localhost pppd[1911]: secondary DNS address 151.196.0.39

whereas mine did not show any DNS addresses.

Any help would be greatly appreciated.

Goatcabin
Woodland, CA

---

### Post by goatcabin on 2007-11-23
Whoops!! I see I missed most of the debug output from "pon LL". Here is all of it:

BEGIN debug output

Toshiba:root:/root> pon LL debug dump logfd 2 nodetach
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
linkname LL             # (from /etc/ppp/peers/LL)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap           # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
user alan.shank         # (from /etc/ppp/peers/LL)
remotename LL           # (from /etc/ppp/peers/LL)
                # (from /etc/ppp/options.pptp)
pty pptp 66.172.234.1 --nolaunchpppd            # (from /etc/ppp/peers/LL)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam LL              # (from /etc/ppp/peers/LL)
proxyarp                # (from /etc/ppp/options)
usepeerdns              # (from /etc/ppp/peers/LL)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
require-mppe            # (from /etc/ppp/peers/LL)
require-mppe-128                # (from /etc/ppp/options.pptp)
noipx           # (from /etc/ppp/options)
using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb365f86> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x94f4f0ae> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x94f4f0ae> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xb365f86]
rcvd [CHAP Challenge id=0x1 <1c57e8e9ae24621c9be03b989a0b9506>, name = "CORP-FW-1"]
sent [CHAP Response id=0x1 <2b20fabb93752ccbfb6de2c7979e8f7900000000000000003dcf58f1ffdccde67daa160990b4a6fb20f1cab863565edb00>, name = "alan.shank"]
rcvd [LCP EchoRep id=0x0 magic=0x94f4f0ae]
rcvd [CHAP Success id=0x1 "S=FAAF78FED9C5680C079F9D1D2B0389C090D5FF93"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [IPCP ConfReq id=0x1 <addr 66.172.234.1> <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
sent [IPCP TermAck id=0x1]
rcvd [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <mppe +H +M +S +L -D +C> <bsd v1 15>]
sent [CCP ConfRej id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x2 <mppe +H +M +S +L -D +C>]
sent [CCP ConfNak id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x3 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x3 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 10.1.31.214>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 10.1.31.214>]
rcvd [IPCP ConfAck id=0x3 <compress VJ 0f 01> <addr 10.1.31.214>]
rcvd [IPCP ConfReq id=0x1 <addr 66.172.234.1> <compress VJ 0f 01> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
sent [IPCP ConfRej id=0x1 <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x2 <addr 66.172.234.1> <compress VJ 0f 01>]
sent [IPCP ConfAck id=0x2 <addr 66.172.234.1> <compress VJ 0f 01>]
Cannot determine ethernet address for proxy ARP
local  IP address 10.1.31.214
remote IP address 66.172.234.1
Script /etc/ppp/ip-up started (pid 6712)
Script /etc/ppp/ip-up finished (pid 6712), status = 0x0

END debug output

This is where it stays for 2 minutes, during which time I tried ping and traceroute, with the results I posted.

Cheers,
Goatcabin

---

