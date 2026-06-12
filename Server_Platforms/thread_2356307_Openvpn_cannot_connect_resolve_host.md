---
title: "Openvpn cannot connect resolve host"
date: 2017-03-22
forum: Server Platforms
---

### Post by Spae on 2017-03-22
I haven't used openvpn for awhile and now realise it no longer works. I emailed the vpn service support and they said only that my DNS settings might need to be changed.

I don't think I've changed those settings since I last used openvpn. I don't actually know how to change DNS settings in ubuntu, I could do it in my router settings but I don't see that as relevant anyway.

I connect using
sudo openvpn --config servername.ovpn
The terminal says nothing different than it used to. Ending in: Initialization Sequence CompletedIt should be working.

So I really have no idea what is going on here..

Openvpn works on my family members windows laptop still with no problems.

Ubuntu 16.04

---

### Post by wildmanne39 on 2017-03-22
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-03-22
First, please specify if you are using Ubuntu Desktop or Server. An admin moved the thread in the server section but the question seems to be related to desktop client connecting to vpn server. Which has little to do with servers.

Then, to check possible dns issues, open the .ovpn file and check the FQDN (hostname) of the server it is trying to connect to. Once you have that, open terminal and check if your dns is working correctly with these commands:
```
nslookup <hostname>
dig <hostname>
ping <hostname>
```

If you need help explaining the output, post the whole output here in CODE tags (so that formatting is kept).

After that we will be able to give you some advice.

---

### Post by Spae on 2017-03-22
Hi, thanks for responding.
I'm using desktop ubuntu.

I have multiple ovpn files and the result is the same.
```
nslookup st-lx-openvpn.boxpnservers.com;; Got recursion not available from 67.215.230.82, trying next server
Server:		61.9.226.1
Address:	61.9.226.1#53


Non-authoritative answer:
Name:	st-lx-openvpn.boxpnservers.com
Address: 94.242.228.2

```
```
dig st-lx-openvpn.boxpnservers.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> st-lx-openvpn.boxpnservers.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 63365
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;st-lx-openvpn.boxpnservers.com.	IN	A


;; Query time: 175 msec
;; SERVER: 67.215.230.82#53(67.215.230.82)
;; WHEN: Thu Mar 23 12:09:11 ACDT 2017
;; MSG SIZE  rcvd: 59

```
```
ping st-lx-openvpn.boxpnservers.comPING st-lx-openvpn.boxpnservers.com (94.242.228.2) 56(84) bytes of data.
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=1 ttl=49 time=332 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=2 ttl=49 time=333 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=3 ttl=49 time=333 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=4 ttl=49 time=334 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=5 ttl=49 time=334 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=6 ttl=49 time=334 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=7 ttl=49 time=335 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=8 ttl=49 time=335 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2): icmp_seq=9 ttl=49 time=335 ms
64 bytes from HostedBy.Lusobits.com (94.242.228.2
```

---

### Post by darkod on 2017-03-23
Looks ok, wven though nslookup reports some message about the first nameserver and it seems to be using the next one. But anyway it does resolve the hostname to an ip.

Since you are opening the tunnel manually with the openvpn command anyway, I would add the option for more output (verbose) which could help you show some error messages or what is going on.

The adding this to your openvpn command when opening the tunnel:
```
--verb 3
```

For more output you can raise the level up to 11 but having it too high might show a lot of no relevant output too.

---

### Post by raybb on 2017-03-27
Did the solution above end up resolving your issue?
Otherwise you may be having a similar issue as we are here: [https://ubuntuforums.org/showthread.php?t=2356760&highlight=vpn](https://ubuntuforums.org/showthread.php?t=2356760&highlight=vpn)

Edit:
Your issue may be related to network manager.
My post here may help resolve your issue: [https://ubuntuforums.org/showthread.php?t=2356760&p=13626118#post13626118](https://ubuntuforums.org/showthread.php?t=2356760&p=13626118#post13626118)

---

