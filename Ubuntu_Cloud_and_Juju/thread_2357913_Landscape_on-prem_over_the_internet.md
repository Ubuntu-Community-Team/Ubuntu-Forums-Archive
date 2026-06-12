---
title: "Landscape on-prem over the internet"
date: 2017-04-07
forum: Ubuntu Cloud and Juju
---

### Post by lsipple on 2017-04-07
Hey! We have a couple cloud servers we want to connect into our on-prem Landscape server. I have been through the firewall stuff and nothing is being blocked. Here, you'll see I can ping and telnet to 80 and 443 on the remote landscape server:

```
Request a new registration for this computer now? (Y/n):Please wait... We were unable to contact the server. Your internet connection may be down. The landscape client will continue to try and contact the server periodically.root@serverxyz:~# ping landscape.mycompany.com
PING landscape.mycompany.com (199.12.34.56) 56(84) bytes of data.
64 bytes from 199.12.34.56: icmp_seq=1 ttl=45 time=120 ms
64 bytes from 199.12.34.56: icmp_seq=2 ttl=46 time=120 ms
^C
--- landscape.mycompany.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 120.655/120.746/120.838/0.359 ms
root@serverxyz:~# telnet landscape.mycompany.com 443
Trying 199.12.34.56...
Connected to landscape.mycompany.com.
Escape character is '^]'.
^]
telnet> q
Connection closed.
root@serverxyz:~# telnet landscape.mycompany.com 80
Trying 199.12.34.56...
Connected to landscape.mycompany.com.
Escape character is '^]'.
^]
telnet> q
Connection closed.
```

If I run tcpdump on the landscape server... I can actually see the two machines talking:

```
12:31:21.781456 IP SITE1-Landscape01.https > 123.456.177.178.52398: Flags [.], ack 246, win 235, options [nop,nop,TS val 40785460 ecr 35630266], length 012:31:21.781761 IP SITE1-Landscape01.https > 123.456.177.178.52398: Flags [P.], seq 1:92, ack 246, win 235, options [nop,nop,TS val 40785460 ecr 35630266], length 9112:31:21.934986 IP 123.456.177.178.52398 > SITE1-Landscape01.https: Flags [P.], seq 246:315, ack 92, win 32, options [nop,nop,TS val 35630305 ecr 40785460], length 69
12:31:21.935290 IP SITE1-Landscape01.https > 123.456.177.178.52398: Flags [P.], seq 92:161, ack 315, win 235, options [nop,nop,TS val 40785499 ecr 35630305], length 69
12:31:21.935433 IP SITE1-Landscape01.https > 123.456.177.178.52398: Flags [F.], seq 161, ack 315, win 235, options [nop,nop,TS val 40785499 ecr 35630305], length 0
12:31:21.936601 IP 123.456.177.178.52398 > SITE1-Landscape01.https: Flags [F.], seq 315, ack 92, win 32, options [nop,nop,TS val 35630305 ecr 40785460], length 0
12:31:21.936620 IP SITE1-Landscape01.https > 123.456.177.178.52398: Flags [.], ack 316, win 235, options [nop,nop,TS val 40785499 ecr 35630305], length 0
12:31:22.057932 IP 123.456.177.178.52398 > SITE1-Landscape01.https: Flags [R], seq 1929665390, win 0, length 0
12:31:22.057968 IP 123.456.177.178.52398 > SITE1-Landscape01.https: Flags [R], seq 1929665390, win 0, length 0
12:31:22.058961 IP 123.456.177.178.52398 > SITE1-Landscape01.https: Flags [R], seq 1929665391, win 0, length 0
```

What gives? Is there something in the code blocking non-RFC1918 to force people to Landscape in the cloud?

---

