---
title: "MS VPN Guest Behaving Badly"
date: 2009-03-09
forum: Virtualisation
---

### Post by seachnasaigh on 2009-03-09
Here's the setup:

Host - Ubuntu Server 8.04 LTS, no AppArmor. HP ML370G3 server, 3 NICs. One NIC dedicated to host management, 2 dedicated to guest. VMWare Server 2.0. IPTables rules are currently set to "accept all" though I can turn a more restrictive firewall on. The firewall, in other words, is not the issue.

Guest - Windows Standard Server 2000 SP4, patched, running Microsoft RRAS.

Bridged networking on two dedicated NICs; one is dedicated to the outside, given a public IP address on both host and guest. The other is dedicated to the inside (Active Directory) network, a dedicated private address on both host and guest. Host and Guest IP addresses are different of course but on the proper subnets. In case I'm not making this clear, NIC#1 on the host, public address, is bridged to NIC#1A on the guest, also public address. Same for NIC#2 on the host, bridged to NIC#2A on the guest, both with a private address.

The guest machine can see the outside world properly, and can see the active directory. I can termserve to the guest from inside the AD. The basic server setup and RRAS setup are a copy of a working Microsoft Windows 2000 RRAS server on our network; only the dedicated IP addresses differ. The guest server is registered as an IAS server in the AD domain.

The intention is that this guest server be a replacement for the RRAS (Microsoft VPN) server that we currently have.

I have Googled the heck out of this already with no success, which is why I'm posting it here. If there is a resource that is known, please accept my apology for the post and point me to the resource.

The problem:

The outside NIC seems to drop the authentication credentials when connecting from the host to the guest. Attempting to connect to the guest (virtual) vpn server from an outside network results consistently in either a RRAS error 691 (credentials invalid) or 734 (PPP reset). It must be stressed that the guest server is an exact copy, except for the IP address and hostname, of an existing (and working) vpn server. Similarly, the configuration of the vpn client on a Windows XP client computer attempting to connect to the guest vpn server is identical to the one used to connect to the working vpn server. Whilst reviewing the IAS logs on the virtual server, I noticed that the logon credentials are blank on the guest (virtual) vpn server. It seems that they are being stripped out somewhere along the line. This is the only log discrepancy I can see.

I've beat my head against this for a week now, and have exhausted my own resources as to a cause. This is the first virtual vpn server I've tried, and so I'm in terra incongita. Anyone ever run across this before? Any help or direction appreciated.

Here are two lines of the IAS log from the guest server. The IP address represented is that of the outside (public) NIC on the guest.

2XX.1XX.1XX.77,,03/09/2009,15:44:50,RAS,VPN1A,4,2XX.1XX.1XX.77,44,24,40,8,4108,2XX.1XX.1XX.77,0,,4136,4,4142,0
2XX.1XX.1XX.77,,03/09/2009,15:44:59,RAS,VPN1A,4,2XX.1XX.1XX.77,44,25,40,7,4108,2XX.1XX.1XX.77,0,,4136,4,4142,0

Thank you.

---

