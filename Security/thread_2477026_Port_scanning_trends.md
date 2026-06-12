---
title: "Port scanning trends"
date: 2022-07-12
forum: Security
---

### Post by Doug S on 2022-07-12
I just thought I would share recent (last couple of years) observations/trends in port scanning. Summary:

[LIST]The trend has been towards the long game. Very low scan rate over a very great period of time. Presumably to avoid detection due to the very low packets per unit time.[/LIST]
[LIST]Extensive use of multiple IP addresses from within the same sub-net. Sometimes maybe due to load balancing for hosting sites, sometimes not.[/LIST]
[LIST]While destination ports appear random, they rarely repeat.[/LIST]

**Example 1:**

Event start: 2022-05-19 09:16:55 although there were only 4 packets until 2022-06-13 14:25:19. Multiple packets per hour (~10 to ~20) didn't start until 2022-06-14 00:00:31
Event end: Has not. Ongoing (as of 2022.07.12).
EDIT: Ended: 2022-07-26 22:35:34

IP: 198.144.159.62 mainly , but 198.144.159.20. became involved around 2022-06-30 19:11:09.

Total packets: 20,998 (~29 packets per hour average)
Total ports scanned: 20,983 ; min port 3000 ; max port 34,695
Non-duplicates: 20,974
Duplicates ("times scanned" "port number"):
```

      2 30700
      2 31200
      2 3314
      2 3721
      2 3830
      2 7200
      2 7201
      3 3390
      7 3389
```

EDIT: 198.144.159.42 joined the game on 2022.07.20 12:42:24

**Example 2:**

Event start: before 2021-12-27 09:10:06, where this data set starts.
Event end: after now (2022.07.13), where this data set ends. i.e. it is ongoing.
Note: there are multi day gaps in the packets, where none were received.

IPs: 193.201.9.0/24 and 193.201.8.21
IPs from 192.201.9.0/24 involved: 41
Min packets from any given IP: 1 (192.201.9.74 and 192.201.9.179)
Max packets from any given IP, excluding 193.201.8.21: 813 (192.201.9.161)

Total packets: 12,554 (about an overall average of 2.6 packets per hour)
Total from 193.201.8.21 3,350
Total from 193.201.9.0/24 9,204

Total ports scanned:  8590 ; min port 2 ; max port 65534
Non-duplicates: 6003
ports scanned 2 times: 1881
ports scanned 3 times: 491
ports scanned 4 times: 125
ports scanned 5 times: 21
ports scanned 6 times: 22
...
The max few are listed:
("times scanned" "port number"):

```

     12 993
     12 995
     13 110
     13 3388
     13 3399
     14 3398
     14 444
     14 4444
     15 8443
     19 4433
     38 80
     50 443
```
Note the port 80 and 443 attempts were blocked via iptables rules, as I already knew these source IP were up to no good.

EDIT: 193.201.8.121 joined the game on 2022.07.16 02:15:08. It shows as from Russia on [https://ipstack.com/](https://ipstack.com/) but is not currently on the ru-aggregated.zone list from [http://www.ipdeny.com/ipblocks/data/aggregated/ru-aggregated.zone](http://www.ipdeny.com/ipblocks/data/aggregated/ru-aggregated.zone) which I use for my ipset deny Russia source. Actually, there seems to be a gap between 193.201.7.255 (France) and 193.201.16.0 (Sweden).

**Example 3:**

Event start: before 2021-12-27 09:10:06, where this data set starts.
Event end: after now (2022.07.13), where this data set ends. i.e. it is ongoing.

IPs: 89.248.160.0/20
IPs involved: 174
Min packets from any given IP: 1 from several
Max packets from any given IP: 39396 from 89.248.165.87

Total packets: 216,763 (about an average of 45 packets per hour.)
Note: Obviously there will be many duplicates in this example as packet = 3.3 times available ports.

Total ports scanned:  51,180 ; min port 0 ; max port 65535
Non-duplicates: 8630
ports scanned 2 times: 17,563
ports scanned 3 times: 10,125
ports scanned 4 times: 4,408
ports scanned 5 times: 2,362
ports scanned 6 times: 1,574
ports scanned 7 times: 1,146
ports scanned 8 times: 893
...
The max few are listed:
("times scanned" "port number"):

```

    242 3391
    243 8081
    271 80
    283 8332
    287 3399
    293 3390
    500 23
    514 3389
    555 443
    868 22

```

**Example 4:**

Event start: before 2021-12-27 09:10:06, where this data set starts.
Event end: after now, where this data set ends. i.e. it is ongoing.

IPs: 79.124.62.0/24
IPs involved: 14
Min packets from any given IP: 2 from 79.124.62.57
Max packets from any given IP: 35,971 from 79.124.62.82

Total packets: 203,363 (about an average of 42 packets per hour.)
Note: Obviously there will be many duplicates in this example as packets = 3.1 times available ports.

Total ports scanned:  65,531 ; min port 1; max port 65535
Ports not scanned: 0, 7547, 48771, 54472, 64414
Non-duplicates: 7215
ports scanned 2 times: 37,532
ports scanned 3 times: 4,096
ports scanned 4 times: 2,905
ports scanned 5 times: 5,054
ports scanned 6 times: 5,113
ports scanned 7 times: 1,643
ports scanned 8 times: 946
...
The max few are listed:
("times scanned" "port number"):

```

    150 33891
    150 3399
    151 3333
    156 13389
    157 3390
    157 3393
    158 3391
    161 3392
    164 33389
   1481 3389

```

**Example 5:**

Event start: before 2021-12-27 09:10:06, where this data set starts.
Event end: after now (2022.07.16), where this data set ends. i.e. it is ongoing.
Note: this is not a good example of non repeating scans of destination ports, but is a good example of many source port used.

IPs: 193.163.125.128/25 and 193.163.125.64/26
IPs involved: 189 (all possible - 3: 193.163.125. 64, 254, 255)
Min packets from any given IP: 1 (193.163.125.195)
Max packets from any given IP: 156 (193.163.125.89)

Total packets: 14,633 (about an overall average of 3 packets per hour)

Total ports scanned:  3383 ; min port 1 ; max port 65535
Non-duplicates: 692
ports scanned 2 times: 665
ports scanned 3 times: 49
ports scanned 4 times: 624
ports scanned 5 times: 125
ports scanned 6 times: 457
...
The max few are listed:
("times scanned" "port number"):

```

     29 995
     30 25
     64 21
     65 22
     66 443
     67 8080
     67 8443
     68 80
```
Note the port 80 and 443 attempts were blocked via iptables rules, as I already knew these source IP were up to no good.

---

### Post by TheFu on 2022-07-13
For years, I've seen coordinated scans and attacks for specific services coming from different IPs around the world.  Once they find a service, say HTTPS, they start their search for vulnerable setups (mainly php management apps), but limit the attempts to under 120 per IP.  With thousands of IPs involved, seeing tens -to- hundreds of thousands of probing attacks isn't unusual.  Fortunately, with fail2ban, it isn't too hard to see the failed 404 or 403 attempts and dynamically block the IPs involved.  I really need to add them to the ipset rules for faster processing than individual iptables rules, which can really slow a server.

---

### Post by Doug S on 2022-07-13
> **TheFu said:**
> For years, I've seen coordinated scans and attacks for specific services coming from different IPs around the world.  Once they find a service, say HTTPS, they start their search for vulnerable setups (mainly php management apps), but limit the attempts to under 120 per IP.  With thousands of IPs involved, seeing tens -to- hundreds of thousands of probing attacks isn't unusual.  Fortunately, with fail2ban, it isn't too hard to see the failed 404 or 403 attempts and dynamically block the IPs involved.  I really need to add them to the ipset rules for faster processing than individual iptables rules, which can really slow a server.Yes, agree, I have seen those type of probes for years also. Example (total was 119):

```

75.83.86.180 - - [22/Jun/2022:07:14:14 -0700] "GET ... sql sys admin stuff ... deleted due to "forbidden" stuff on Ubuntu forums..."
...
75.83.86.180 - - [22/Jun/2022:07:14:27 -0700] "GET ... php myadmin stuff ... deleted due to "forbidden" stuff on Ubuntu forums..."

```
These tend to come in quick bursts. I manually keep a short list of badguy sub-nets on my iptables rules block list, but yes an ipset would be faster.

By the way, I block several countries entirely via ipsets and an interesting observation was that packets from Russia dropped to almost 0 per unit time at the outbreak of the war on Ukraine. Packets per unit time have increased again, but not to pre-war levels.

Anyway, the newer trend I am seeing is this SLOW non service specific, i.e. higher numbered, port scans.  I'll edit in an example 3 to the original post in a few hours (it takes several hours to extract an example).

---

