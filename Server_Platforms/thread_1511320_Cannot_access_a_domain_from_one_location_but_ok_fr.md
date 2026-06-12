---
title: "Cannot access a domain from one location but ok from another location"
date: 2010-06-16
forum: Server Platforms
---

### Post by leonardoxiao on 2010-06-16
Cannot access our company's webmail (webmail.synergywebservices.ca)from office but can access it from home (both are using the same Shaw cable high-speed internet). But can access the portal ([www.synergywebservices.ca](www.synergywebservices.ca)) from both locations.

Here is the output from office:
```
user@gateway:~$ sudo tcptraceroute www.synergywebservices.ca
traceroute to www.synergywebservices.ca (69.49.101.51), 30 hops max, 60 byte packets
 1  * * *
 2  rd2bb-ge0-0-0-1.vc.shawcable.net (64.59.174.131)  11.564 ms  12.992 ms  12.988 ms
 3  rc2bb-tge0-2-2-0.vc.shawcable.net (66.163.69.133)  12.977 ms  12.972 ms  12.960 ms
 4  66.163.78.17 (66.163.78.17)  28.556 ms  28.592 ms  28.582 ms
 5  rc2ar-ge9-2.ed.shawcable.net (66.163.70.9)  29.827 ms  29.763 ms  29.755 ms
 6  rd2ha-atm1-0-3.ss.shawcable.net (66.163.76.62)  49.614 ms  41.339 ms  42.663 ms
 7  rc1sh-pos1-0-0.mt.shawcable.net (66.163.77.170)  66.867 ms  70.545 ms  70.522 ms
 8  rc2fs-ge0-0-0.mt.shawcable.net (66.163.66.98)  70.399 ms  80.947 ms  80.861 ms
 9  gw-megarouting.torontointernetxchange.net (198.32.245.28)  80.626 ms  79.770 ms  79.726 ms
10  core4-ge60p.151.megarouting.com (216.251.39.204)  77.867 ms  68.038 ms  69.131 ms
11  core2-srp30p.300.megarouting.com (216.251.39.193)  72.163 ms  71.127 ms  70.948 ms
12  c6500-vl5.300.megarouting.com (216.251.39.3)  71.474 ms  71.572 ms  81.493 ms
13  hostedc11.megawebservers.com (69.49.101.51)  74.136 ms  74.129 ms  74.173 ms
user@gateway:~$ sudo tcptraceroute webmail.synergywebservices.ca
traceroute to webmail.synergywebservices.ca (69.49.101.55), 30 hops max, 60 byte packets
 1  * * *
 2  rd2bb-ge0-0-0-1.vc.shawcable.net (64.59.174.131)  10.818 ms  10.757 ms  10.748 ms
 3  rc2bb-tge0-9-2-0.vc.shawcable.net (66.163.69.41)  10.814 ms  11.023 ms  12.108 ms
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *

```


Here is the output from home:
```
user@home:~$ sudo tcptraceroute webmail.synergywebservices.ca
traceroute to webmail.synergywebservices.ca (69.49.101.55), 30 hops max, 60 byte packets
 1  unknown (192.168.1.1)  0.954 ms  1.446 ms  1.650 ms
 2  * * *
 3  rd1bb-ge5-0-0-3.vc.shawcable.net (64.59.159.50)  14.739 ms  14.759 ms  16.077 ms
 4  rc2bb-tge0-7-0-0.vc.shawcable.net (66.163.69.145)  17.012 ms  16.820 ms  16.818 ms
 5  rc3ar-pos0-15-5-0.ed.shawcable.net (66.163.77.221)  29.888 ms  39.285 ms  39.193 ms
 6  rc1we-tge0-1-5-0.ed.shawcable.net (66.163.70.21)  39.109 ms  32.875 ms  32.720 ms
 7  rc2ch-pos2-0-0.il.shawcable.net (66.163.77.65)  48.231 ms  44.340 ms  44.464 ms
 8  rc1sh-pos15-0.mt.shawcable.net (66.163.76.221)  69.597 ms  68.759 ms  68.698 ms
 9  rc2fs-ge11-0-0.mt.shawcable.net (66.163.66.110)  69.751 ms  66.200 ms  69.074 ms
10  gw-megarouting.torontointernetxchange.net (198.32.245.28)  69.956 ms  70.206 ms  70.148 ms
11  core4-ge60p.151.megarouting.com (216.251.39.204)  69.649 ms  67.986 ms  69.034 ms
12  core2-srp30p.300.megarouting.com (216.251.39.193)  66.971 ms  66.518 ms  66.529 ms
13  c6500-vl5.300.megarouting.com (216.251.39.3)  72.085 ms  71.264 ms  69.815 ms
14  webmailc11.megawebservers.com (69.49.101.55)  71.135 ms  72.880 ms  73.044 ms
user@home:~$ fc -s webmail=www
sudo tcptraceroute www.synergywebservices.ca
traceroute to www.synergywebservices.ca (69.49.101.51), 30 hops max, 60 byte packets
 1  unknown (192.168.1.1)  0.653 ms  1.150 ms  1.356 ms
 2  * * *
 3  rd1bb-ge5-0-0-3.vc.shawcable.net (64.59.159.50)  16.891 ms  17.075 ms  17.028 ms
 4  rc2bb-tge0-15-0-0.vc.shawcable.net (66.163.69.137)  17.332 ms  17.680 ms  17.685 ms
 5  66.163.78.17 (66.163.78.17)  32.436 ms  32.615 ms  32.635 ms
 6  rc1we-tge0-8-4-0.ed.shawcable.net (66.163.70.37)  33.971 ms  31.361 ms  31.375 ms
 7  rc2sc-tge0-0-0-0.wp.shawcable.net (66.163.76.77)  47.599 ms  44.760 ms  44.856 ms
 8  rc1sh-pos1-0-0.mt.shawcable.net (66.163.77.170)  74.378 ms  74.331 ms  73.897 ms
 9  rc2fs-ge11-0-0.mt.shawcable.net (66.163.66.110)  72.401 ms  69.312 ms  69.300 ms
10  gw-megarouting.torontointernetxchange.net (198.32.245.28)  73.320 ms  72.226 ms  69.670 ms
11  core4-ge60p.151.megarouting.com (216.251.39.204)  69.387 ms  69.968 ms  69.185 ms
12  core2-srp30p.300.megarouting.com (216.251.39.193)  71.595 ms  68.489 ms  67.607 ms
13  c6500-vl5.300.megarouting.com (216.251.39.3)  69.756 ms  74.977 ms  70.972 ms
14  hostedc11.megawebservers.com (69.49.101.51)  72.661 ms  69.663 ms  69.834 ms

```

Sorry for this stupid question but I really have little knowledge about network and routing: is the problem from ISP (Shaw cable) or our gateway server (running Ubuntu server)?

Thanks for any input!

---

