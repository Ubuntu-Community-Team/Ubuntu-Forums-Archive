---
title: "Apache only accepts connection to IP address, not domain name"
date: 2021-08-08
forum: Server Platforms
---

### Post by Rich_Stanton on 2021-08-08
Hi, I'm running a website using Drupal, via Apache, on Ubuntu 18.04. It's worked fine since it was set up, however recently I've been having problems. I can view the site fine if I'm logged in to the server. However when I view the site remotely, access is intermittent - my android phone never views it (chrome), it just says connection refused. My laptop (chrome/edge) sometimes views it fine and other times says connection refused. I can always view the site fine when using the IP address, it's only when using the hostname that access is intermittent.  I can access other services (e.g. ssh) on the server using the hostname fine.

When I get 'connection refused' the apache logs don't log the connection attempt at all. I have UFW enabled, but I've tried disabling it, and it makes no difference. There's only 1 site on the server. Running Test-NetConnection against the hostname from powershell on a remote compute always shows the port as open.

Any ideas where I go next?

---

### Post by Doug S on 2021-08-08
Suggest to monitor things at the packet level with tcpdump, or (wireshark, if you prefer) to confirm the packets are actually arriving and leaving your server. Example, where enp1s0 is my WAN facing NIC, and I have changed my IP:
```
doug@s15:~$ sudo tcpdump -n -tttt -i enp1s0 port 80
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
2021-08-08 08:25:06.308129 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 1819158303, win 65535, length 0
2021-08-08 08:25:06.308169 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [.], ack 2064005470, win 64240, length 0
2021-08-08 08:25:11.601966 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 366483753, win 29200, length 0
2021-08-08 08:25:11.602001 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [.], ack 1, win 64240, length 0
2021-08-08 08:25:12.164461 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 523901079, win 65504, length 0
2021-08-08 08:25:12.164496 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [.], ack 1, win 64240, length 0
2021-08-08 08:25:12.510298 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [S.], seq 572245037, ack 2064005470, win 64240, options [mss 1460], length 0
2021-08-08 08:25:18.213266 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 2031725537, win 8240, length 0
2021-08-08 08:25:18.213303 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [.], ack 1, win 64240, length 0
2021-08-08 08:25:24.150340 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 2034883888, win 8240, length 0
2021-08-08 08:25:24.150377 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [.], ack 1, win 64240, length 0
2021-08-08 08:25:24.332960 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 1588207435, win 29000, length 0
2021-08-08 08:25:24.792888 IP 45.61.142.178.61703 > zzz.xxx.yyy.www.80: Flags [S], seq 1447968328, win 63613, length 0
2021-08-08 08:25:24.792923 IP zzz.xxx.yyy.www.80 > 45.61.142.178.61703: Flags [.], ack 1, win 64240, length 0
^C
14 packets captured
14 packets received by filter
0 packets dropped by kernel
```

---

### Post by volkswagner on 2021-08-08
Is the server listening on both port 80 and 443?

Check the url when you get "refused". If you're
not using https on the server, your browser maybe
"doing you a favor" by rewriting to "https".

Try removing the "s" and use http://
to see if that makes a difference.

---

### Post by Rich_Stanton on 2021-08-08
We have a winner! It was auto-redirecting to https. I'll get that fixed now. Thanks!

---

