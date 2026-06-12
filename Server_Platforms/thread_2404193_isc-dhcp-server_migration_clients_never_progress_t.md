---
title: "isc-dhcp-server migration: clients never progress to DHCPREQUEST phase"
date: 2018-10-21
forum: Server Platforms
---

### Post by entilza2 on 2018-10-21
Hi team,

This DHCP Server issue has me stumped - I'd appreciate any suggestions/insight.

I am migrating a DHCP server from an aged Smoothwall box to **Ubuntu 16.04.5 LTS** (fully patched) running on FreeNAS via bhyve. (I'd use Ubuntu 18, except there are issues with 18 on FreeNas+bhyve). Smoothwall appears to run isc-dhcp-server, as the .conf and lease files are identical to the latest isc-dhcp-server I installed via apt-get.

In this example, the following IPs are used:
```
10.0.2.0: Network
10.0.2.145: Windows 10 client, for testing
10.0.2.229: "prd-dhcp-01", the new DHCPD Ubuntu host, new DNS and new NTP server.
10.0.2.254: The old DHCPD and DNS. Also, current router (it will remain the router). Smoothwall host.
10.0.2.255: Network broadcast
```

First a review. The DHCP request cycle should go like this:
DHCPDISCOVER: from the client, asking for a lease
DHCPOFFER: from the DHCPD host, offering a lease
DHCPREQUEST: from the client, confirming it wants to take the OFFERed lease
DHCPACK: from the host, confirming is has now granted to REQUESTed lease.

[B]The issue
[/B]After disabling the current (old) DHCP server, Clients never pick up leases from the new Ubuntu 16 server. They timeout.
Syslog shows endless DHCPDISCOVER and DHCPOFFER entries (MAC addresses changed to aaa, bbb):
```
[FONT=fixedsys]Oct 21 18:34:28 prd-dhcp-01 dhcpd[1028]: DHCPDISCOVER from aaa via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:34:28 prd-dhcp-01 dhcpd[1028]: DHCPOFFER on 10.0.2.84 to aaa via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:34:32 prd-dhcp-01 dhcpd[1028]: DHCPDISCOVER from bbb via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:34:32 prd-dhcp-01 dhcpd[1028]: DHCPOFFER on 10.0.2.23 to bbb via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:34:52 prd-dhcp-01 dhcpd[1028]: DHCPDISCOVER from bbb via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:34:52 prd-dhcp-01 dhcpd[1028]: DHCPOFFER on 10.0.2.23 to bbb via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:35:12 prd-dhcp-01 dhcpd[1028]: DHCPDISCOVER from bbb via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 18:35:12 prd-dhcp-01 dhcpd[1028]: DHCPOFFER on 10.0.2.23 to bbb via enp0s3[/FONT]
```

The clients never progress to phase 3, DHCPREQUEST - that is, they never request the OFFER'ed lease.

I don't think its a network routing issue, because I am connecting to the Ubuntu host from one of the clients that won't pick up a lease.
This issue appears to impact all clients.

I am trying to avoid starting with a blank config in PRD, because it would ... be messy. And I don't have a test network. I am hoping to find some glaring hole before going down that path.

**Migration process**
I copied the existing dhcp.conf and dhcpd.leases files. The leases file could stay as-is (format hasn't changed and it would enable devices to pick up their same IPs), but I altered the .conf file to use "interim" for ddns-update-style, and changed the IP of the new local domain-name-servers and ntp-servers (an easy way to see if the client is using the right server). The file loads OK with no issues and everything is fine in syslog. dhcpd.conf file contents:

```
[FONT=fixedsys]authoritative;[/FONT]
[FONT=fixedsys]ddns-update-style interim;[/FONT]
[FONT=fixedsys]
[/FONT][FONT=fixedsys]subnet 10.0.2.0 netmask 255.255.255.0[/FONT]
[FONT=fixedsys]  {[/FONT]
[FONT=fixedsys]    option subnet-mask 255.255.255.0;[/FONT]
[FONT=fixedsys]    option domain-name "lan";[/FONT]
[FONT=fixedsys]    option routers 10.0.2.254;
[/FONT][FONT=fixedsys]    option broadcast-address 10.0.2.255;[/FONT]
[FONT=fixedsys]    option domain-name-servers 10.0.2.229, 8.8.8.8;[/FONT]
[FONT=fixedsys]    option ntp-servers 10.0.2.229;[/FONT]
[FONT=fixedsys]    range dynamic-bootp 10.0.2.11 10.0.2.189;[/FONT]
[FONT=fixedsys]    default-lease-time 172800;[/FONT]
[FONT=fixedsys]    max-lease-time 345600;[/FONT]
[FONT=fixedsys]    host 1 { hardware ethernet xx:xx:xx:xx:xx; fixed-address 10.0.2.2; option host-name "vir"; }[/FONT]
[FONT=fixedsys][FONT=arial]*(12 of these hosts, removed for reading ease)*[/FONT]
  }
[/FONT][FONT=fixedsys]log-facility local7;[/FONT]
```

**Fault finding**
Besides the syslog and evidence gathering from clients, I captured the DHCP [FONT=fixedsys]**ipconfig /release**[/FONT] process on a Windows client. It showed the client trying to talk directly to the OLD DCHP server, which also happens to be the router, which I will admit I was not expecting:

```
[FONT=fixedsys]102    7.382042    10.0.2.145    10.0.2.254    DHCP    358    DHCP Request  - Transaction ID 0x5f33a84
103    7.382460    10.0.2.254    10.0.2.145    ICMP    386    Destination unreachable (Port unreachable)[/FONT]

```
I did expect the service not to answer however, as it is disabled. There are 4 of these pairs over time, before the renew fails. But right before/during the 4th and final attempt, the following occurs (in bold): 

[FONT=fixedsys]**203    18.639981    0.0.0.0    255.255.255.255    DHCP    342    DHCP Discover - Transaction ID 0x582131ac**
228    20.382489    10.0.2.145    10.0.2.254    DHCP    358    DHCP Request  - Transaction ID 0x5f33a84
229    20.382867    10.0.2.254    10.0.2.145    ICMP    386    Destination unreachable (Port unreachable)
**336    38.649423    0.0.0.0    255.255.255.255    DHCP    342    DHCP Discover - Transaction ID 0x582131ac**[/FONT]

Those 2 Discover broadcasts do not end up in the syslog! I wonder why. Plenty other Discovers in the syslog.

I then did a full /release and /renew with better results in syslog, but still a failure:

Win 10 client capture:
```
[FONT=fixedsys]5    1.159897    0.0.0.0    255.255.255.255    DHCP    326    DHCP Discover - Transaction ID 0xaa62a41f
38    3.760613    10.0.2.145    10.0.2.254    DHCP    342    DHCP Release  - Transaction ID 0x99dfcf1
39    3.760969    10.0.2.254    10.0.2.145    ICMP    370    Destination unreachable (Port unreachable)
111    7.131078    0.0.0.0    255.255.255.255    DHCP    332    DHCP Discover - Transaction ID 0xb46c7c70
138    7.767436    0.0.0.0    255.255.255.255    DHCP    344    DHCP Discover - Transaction ID 0x3489e56c[/FONT]
```
(this Discover occurs 30 times in total)

DHCPD entry in syslog (mac address changed to ccc):
```
[FONT=fixedsys]Oct 21 22:15:51 prd-dhcp-01 dhcpd[2072]: DHCPDISCOVER from ccc via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 22:15:52 prd-dhcp-01 dhcpd[2072]: DHCPOFFER on 10.0.2.145 to ccc (DESKTOP-9CRBAR3) via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 22:15:55 prd-dhcp-01 dhcpd[2072]: DHCPDISCOVER from ccc (DESKTOP-9CRBAR3) via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 22:15:55 prd-dhcp-01 dhcpd[2072]: DHCPOFFER on 10.0.2.145 to ccc (DESKTOP-9CRBAR3) via enp0s3[/FONT]
```
(message pair appears 10 times in total, not the 30 I would have expected from the capture above)

I also found the DHCP server pinged the old address of the Windows 10 client during all of this, which was unexpected:
```
[FONT=fixedsys]139    7.768028    10.0.2.229    10.0.2.145    ICMP    62    Echo (ping) request  id=0x68d8, seq=0/0, ttl=64 (no response found!)[/FONT]
```

Because the network is "somewhat busy" I cannot confidently say I have seen everything in the capture. There is likely to be something in there I have not found yet. But I did trace the BOOTP traffic which is how I got the DHCP content above.

I am stumped.

Any help/suggestions appreciated.

Kind regards,
Ent.

---

### Post by Doug S on 2018-10-25
Hi, and welcome to Ubuntu forums.

I see you are not getting any help for your issue. Please know that it doesn't mean we are not trying to help. I spent some time on your issue, but didn't come up with anything useful.
The only thing I notice for my system is that almost always (but not always) there are additional lines in the syslog file about writing to the leases file. Example (where my son came to our house and his phone was trying to get on the network. the re-try is likely due to poor wi-fi signal):

```
Oct 22 18:18:25 DOUG-64 dhcpd[1277]: DHCPDISCOVER from aaa via enp2s0
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: DHCPOFFER on 192.168.111.44 to aaa (Galaxy-A5-2017) via enp2s0
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: DHCPDISCOVER from aaa (Galaxy-A5-2017) via enp2s0
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: DHCPOFFER on 192.168.111.44 to aaa (Galaxy-A5-2017) via enp2s0
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: Wrote 0 deleted host decls to leases file.
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: Wrote 0 new dynamic host decls to leases file.
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: Wrote 48 leases to leases file.
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: DHCPREQUEST for 192.168.111.44 (192.168.111.1) from aaa (Galaxy-A5-2017) via enp2s0
Oct 22 18:18:26 DOUG-64 dhcpd[1277]: DHCPACK on 192.168.111.44 to aaa (Galaxy-A5-2017) via enp2s0

```
It might be that the leases file updates are due to the DHCPREQUEST rather than the DHCPOFFER, I don't know.

The only other suggestion I have is to not try reusing your dhcpd.leases file. In past years, I have had to delete my dhcpd.leases file a few times when I have had troubles.

---

### Post by entilza2 on 2018-10-27
Hi Doug, thanks for taking a look.

I'm definitely not getting any "Wrote" logs. But as you say, it may be down to the Request function, not the Offer.

I think you are right - I need to test it by deleting the leases file. Interesting to see you say you have had to do this in the past. I'll give it a shot, cause mayhem :-) and report back in. I don't really have much left to try.

Thanks!

---

### Post by entilza2 on 2018-10-27
Hi again,

I renamed the leases file and its backup, touched some new empty ones. The server wrote a heading to the new files, so no permission issues. Everything started up OK in syslog as per usual. I do note that the DHCPD start-up lines are duplicated, once for "dhcpd" and once for "sh". Eg:

```
Oct 27 21:58:32 prd-dhcp-01 dhcpd[8453]: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Oct 27 21:58:32 prd-dhcp-01 sh[8453]: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Oct 27 21:58:32 prd-dhcp-01 dhcpd[8453]: Config file: /etc/dhcp/dhcpd.conf
Oct 27 21:58:32 prd-dhcp-01 sh[8453]: Config file: /etc/dhcp/dhcpd.conf
Oct 27 21:58:32 prd-dhcp-01 dhcpd[8453]: Database file: /var/lib/dhcp/dhcpd.leases
Oct 27 21:58:32 prd-dhcp-01 sh[8453]: Database file: /var/lib/dhcp/dhcpd.leases

```

I also note I get "Wrote" entries when DHCPD first starts, and only then (duplicate "sh" entries deleted from example):

```
Oct 27 21:58:32 prd-dhcp-01 dhcpd[8453]: Wrote 0 deleted host decls to leases file.
Oct 27 21:58:32 prd-dhcp-01 dhcpd[8453]: Wrote 0 new dynamic host decls to leases file.
Oct 27 21:58:32 prd-dhcp-01 dhcpd[8453]: Wrote 0 leases to leases file.

```

I also deleted all previous network settings from the client and started fresh.

However, after disabling the old DHCPD server, I get the same result - the client never picks up a lease, and the DHCPD server never goes beyond DHCPOFFER:

Syslog:
```
Oct 27 22:06:30 prd-dhcp-01 dhcpd[8657]: Server starting service.
Oct 27 22:06:53 prd-dhcp-01 dhcpd[8657]: DHCPDISCOVER from 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:06:54 prd-dhcp-01 dhcpd[8657]: DHCPOFFER on 10.0.2.11 to 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:06:56 prd-dhcp-01 dhcpd[8657]: DHCPDISCOVER from 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:06:56 prd-dhcp-01 dhcpd[8657]: DHCPOFFER on 10.0.2.11 to 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:07:01 prd-dhcp-01 dhcpd[8657]: DHCPDISCOVER from 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:07:01 prd-dhcp-01 dhcpd[8657]: DHCPOFFER on 10.0.2.11 to 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:07:26 prd-dhcp-01 dhcpd[8657]: DHCPDISCOVER from 9c:5c:f9:30:0a:7a via enp0s3
Oct 27 22:07:26 prd-dhcp-01 dhcpd[8657]: DHCPOFFER on 10.0.2.11 to 9c:5c:f9:30:0a:7a via enp0s3

```


tcpdump:
```
    0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 9c:5c:f9:30:0a:7a (oui Unknown), length 290, xid 0x7239ada3, Flags [none]
    prd-dhcp-01.bootps > 10.0.2.11.bootpc: BOOTP/DHCP, Reply, length 300, xid 0x7239ada3, Flags [none]
    0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 9c:5c:f9:30:0a:7a (oui Unknown), length 290, xid 0x7239ada3, secs 2, Flags [none]
    prd-dhcp-01.bootps > 10.0.2.11.bootpc: BOOTP/DHCP, Reply, length 300, xid 0x7239ada3, secs 2, Flags [none]
    0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 9c:5c:f9:30:0a:7a (oui Unknown), length 290, xid 0x7239ada3, secs 7, Flags [none]
    prd-dhcp-01.bootps > 10.0.2.11.bootpc: BOOTP/DHCP, Reply, length 300, xid 0x7239ada3, secs 7, Flags [none]
    0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 9c:5c:f9:30:0a:7a (oui Unknown), length 290, xid 0x7239ada3, secs 33, Flags [none]
    prd-dhcp-01.bootps > 10.0.2.11.bootpc: BOOTP/DHCP, Reply, length 300, xid 0x7239ada3, secs 33, Flags [none]

```

Finally, I deleted the static hosts from the dhcpd.conf, so the file was very basic. Still did not work after a reload.

I am truly stumped. I have to wonder if there isn't some hardware issue at play, except the hypervisor server (which is FreeNAS and runs as a NAS) happily reads and writes files at gigabit speeds and I have never seen any sign of a flakey port or a large amount of dropped packets.

Doug, I appreciate your attempt to help.

Ent.

---

### Post by Doug S on 2018-10-27
> **entilza2 said:**
> I am truly stumped.Me also. Hopefully someone else will chime in with a suggestion. Please update this thread if/when you figure it out.

---

### Post by darkod on 2018-10-27
Was the leases file the only one you copied over from the old system? Once I saw weird issue with samba after copying over my smb.conf. But it worked with the default smb.conf after I purged it and reinstalled samba. I then added the parts I needed.
Try to trace your steps and do not copy over any dhcp related files. See if it works with all its own default files.
Then you can start making adjustments you need.

---

### Post by entilza2 on 2018-10-27
@Doug count on it, as soon as this gets cracked, I'll be back here.

@darkod the dhcpd.conf file was not copied - I copy/pasted relevant lines into the default one. I tried deleting the dozen-odd fixed-address definitions but that did not help. isc-dhcp-server does not complain about the config. I did remove the leases file which was the only one copied - isc-dhcp-server then wrote a fresh file, but no improvement.

The server appears to be operating correctly - its just that every "offer" hits the logs but does not appear to reach the network. Recall this Wireshark capture from when I tested with a Win10 client:

[FONT=fixedsys](Broadcast for DHCP):
5    1.159897    0.0.0.0    255.255.255.255    DHCP    326    DHCP Discover - Transaction ID 0xaa62a41f

(Asking old server to release):
38    3.760613    10.0.2.145    10.0.2.254    DHCP    342    DHCP Release  - Transaction ID 0x99dfcf1

(Old server rejects):
39    3.760969    10.0.2.254    10.0.2.145    ICMP    370    Destination unreachable (Port unreachable)

(More broadcasts):
111    7.131078    0.0.0.0    255.255.255.255    DHCP    332    DHCP Discover - Transaction ID 0xb46c7c70
138    7.767436    0.0.0.0    255.255.255.255    DHCP    344    DHCP Discover - Transaction ID 0x3489e56c
[/FONT]
Not a single answer amongst them. Yet the logs show a series of discovers and offers:

[FONT=fixedsys]Oct 21 22:15:51 prd-dhcp-01 dhcpd[2072]: DHCPDISCOVER from ccc via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 22:15:52 prd-dhcp-01 dhcpd[2072]: DHCPOFFER on 10.0.2.145 to ccc (DESKTOP-9CRBAR3) via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 22:15:55 prd-dhcp-01 dhcpd[2072]: DHCPDISCOVER from ccc (DESKTOP-9CRBAR3) via enp0s3[/FONT]
[FONT=fixedsys]Oct 21 22:15:55 prd-dhcp-01 dhcpd[2072]: DHCPOFFER on 10.0.2.145 to ccc (DESKTOP-9CRBAR3) via enp0s3
[/FONT]
Ent.

---

### Post by entilza2 on 2018-10-27
I am now focusing on the interface and hardware. I overlooked this:

While the switch shows no dropped packets RX or TX, the guest VM (The DHCP server I am trying to get working) shows the following on its only interface:

enp0s3    Link encap:Ethernet  HWaddr 00:a0:98:78:bf:12
          inet addr:10.0.2.229  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:98ff:fe78:bf12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1449675 errors:0 **dropped:74356** overruns:0 frame:0
          TX packets:325255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:357438309 (357.4 MB)  TX bytes:30046251 (30.0 MB)

I'm not sure if this plays into our scenario at all: it is dropping (failing to process) almost 1 in every 20 of the packets it receives. BUT the DHCPD logs show it is happily receiving DHCP requests. Its the transmitted responses that don't make the network. The tcpdump from enp0s3 shows it as being sent, but they don't appear at the client (or at least didn't when I did the wireshark capture).

I am going to change switch ports, reboot everything (including the switch) and try again.

Cheers,
Ent.

---

### Post by darkod on 2018-10-27
I'm out of ideas too. What I would do (to make sure you use clean new isc-dhcp-server):
1. Purge the isc-dhcp-server package. Install it again. Don't copy any part of your old files, just set up manually the basic stuff, router info, subnet range... No reservations, no old clients... See if that helps.
2. Try to give it some time after replacing the dhcp server. Maybe that will allow clients to figure it out. Until the lease expires they will all work anyway. And the lease won't expire for all at once.
3. You can test the new server with new subnet. I know you want to keep the same, but you can do a quick test if new subnet ip will be assigned to a client.

---

### Post by entilza2 on 2018-10-27
Hi all, thanks for the continued support. It is appreciated :-)

I rebooted everything and changed switch ports. I also disabled link aggregation on the hypervisor host. The Drops went away for the interface. But it continued to fail as before. 

I retested from the windows client via wireshark and can only see DHCP requests going out, nothing returning. Syslog shows repeated requests and offers from the DHCP host in question. I did try to tcpdump all traffic with the win10 hosts's MAC, however it only shows the requests. Either I got the grep wrong on the dhcp host (very possible) or this time no offers were going out on the network. That would be at odds with past observations, where I did see offers going out. Sadly its difficult to test, because the wireshark client/win 10 machine is the only PC on the network and when I release the lease to test, I also lose the shell to the dhcp host in question, making tcpdump'ing very difficult :-)

@darkrod I will try this later in the week and report back. I am sadly out of time for testing today.

Thanks again for the continued support and interest.

Ent

---

### Post by entilza2 on 2018-10-28
I uninstalled isc-dhcp-server and all supporting packages that were not in use elsewhere. I reinstalled and used a simple config that was not based on my existing config.

I tried to make it outside of the current range, but the isc-dhcpd borked when the host's interface was not part of the range. So I made the range and subnet part of the server's interface.

It still does not work. Same outcome. I captured the following from the DHCPD host via tcpdump, which shows a single request and response.

```
22:11:41.407741 IP (tos 0x0, ttl 255, id 53372, offset 0, flags [none], proto UDP (17), length 336)
    0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 70:ee:50:00:e2:3a (oui Unknown), length 308, xid 0xc7c61818, Flags [none]
          Client-Ethernet-Address 70:ee:50:00:e2:3a (oui Unknown)
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Discover
            MSZ Option 57, length 2: 1500
            Parameter-Request Option 55, length 4:
              Subnet-Mask, Default-Gateway, BR, Domain-Name-Server
22:11:41.407905 IP (tos 0x0, ttl 64, id 30394, offset 0, flags [DF], proto UDP (17), length 69)
    prd-dhcp-01.43897 > prd-fw-01.domain: 11610+ PTR? 100.2.0.10.in-addr.arpa. (41)
22:11:41.415222 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 69)
    prd-fw-01.domain > prd-dhcp-01.43897: 11610 NXDomain 0/0/0 (41)
22:11:41.415325 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
    prd-dhcp-01.bootps > 10.0.2.100.bootpc: BOOTP/DHCP, Reply, length 300, xid 0xc7c61818, Flags [none]
          Your-IP 10.0.2.100
          Server-IP prd-dhcp-01
          Client-Ethernet-Address 70:ee:50:00:e2:3a (oui Unknown)
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Offer
            Server-ID Option 54, length 4: prd-dhcp-01
            Lease-Time Option 51, length 4: 120
            Subnet-Mask Option 1, length 4: 255.255.255.0
            Default-Gateway Option 3, length 4: prd-fw-01
            BR Option 28, length 4: 10.0.2.255
            Domain-Name-Server Option 6, length 8: google-public-dns-a.google.com,dns.quad9.net

```

One thing I note above - the response (Offer) is sent directly to the IP that is being offered (10.0.2.100). I would have thought this would have been another broadcast, as the client doesn't "have" that IP yet??! How can the client listen on this IP when it doesn't own it? Is this the cause of my issues? (I doubt it - I probably just don't understand how DHCP works at that level!) 

The other thread I was following was disappearing Offers once they hit the network: I can't prove it just yet, but I am suspecting these Offer responses are not making it to the clients. I only have one client that can capture interface traffic, and I do not see the response "Offer" reach it. Instead I only see a series of "Discover"s. I can't capture the Host and the Server at the same time, as I get disconnected from the host when I perform the test. I need a second client :-) (no I don't have one)

So, if the disappearing Offer turns out to be a smoking gun ... what would eat an Offer response on the network? Is it something to do with the fact the offer is sending to the same IP it is offering?

Thanks for the continued help!
Ent.

---

### Post by entilza2 on 2018-10-29
Good news everybody! I solved the problem.

It is a switch problem (Netgear GS724T), not DHCPD or Ubuntu.

I followed the theory that the Offers were going out on the interface, but weren't reaching the clients. I checked broadcasts and subnets, but all OK.

So I dug deeper into the switch config, and there I found a sub menu called "System, Services". And under Services was a single item, "Admin mode", which was Enabled. It in turn gave access to this suspiciously named menu "DHCP filtering interface configuration". Someone had found this years ago and studiously turned on DHCP filtering for every port, bar the one running the DHCP server.

Yes, the DHCP Offers were being stripped from what was an "illegal DHCP server". Once I added the new host's port as trusted, it worked immediately. It always was working.

Special thanks to Doug S and darkod for sticking with me! I appreciate it. I feel like a turkey for the wild goose chase, but hopefully this will help someone later. :-)

Regards
Ent.

---

### Post by darkod on 2018-10-29
Wow, great catch!!! You can mark the thread as Solved in Thread Tools above the first post.

---

### Post by Doug S on 2018-10-30
well done figuring it out. And thanks for coming back here and finishing this thread.

---

