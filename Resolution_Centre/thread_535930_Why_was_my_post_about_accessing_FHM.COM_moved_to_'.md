---
title: "Why was my post about accessing FHM.COM moved to 'The Jail'"
date: 2007-08-27
forum: Resolution Centre
---

### Post by DistantDave on 2007-08-27
What's going on? I have a genuine problem, and I do not understand why this was moved - please move it back.
I need help.

Look at these two alternate pings:

traceroute fhm.com
traceroute: Warning: fhm.com has multiple addresses; using 204.74.99.100
traceroute to fhm.com (204.74.99.100), 30 hops max, 40 byte packets
 1  [www.routerlogin.com](www.routerlogin.com) (192.168.0.1)  5.298 ms  2.823 ms  35.767 ms
 2  dr4.bllon.uk.easynet.net (212.134.12.203)  26.403 ms  25.969 ms  25.244 ms
 3  ge-3-2-0-46.br0.bllon.uk.easynet.net (82.109.182.129)  25.966 ms  28.806 ms                                                                                                    26.387 ms
 4  ge0-1-1.er3.bllon.uk.easynet.net (212.135.12.41)  25.680 ms  26.724 ms  26.5                                                                                                  20 ms
 5  ge0-0-0.er4.bllon.uk.easynet.net (212.135.12.34)  25.928 ms  26.747 ms  26.2                                                                                                  83 ms
 6  ge1-0-0.er3.tclon.uk.easynet.net (82.108.6.146)  34.958 ms  25.878 ms  26.51                                                                                                  9 ms
 7  ge0-0-0.er3.thlon.uk.easynet.net (82.108.6.150)  26.409 ms  25.707 ms  26.48                                                                                                  0 ms
 8  ip-217-204-60-226.easynet.co.uk (217.204.60.226)  27.440 ms  40.089 ms  26.0                                                                                                  14 ms
 9  ge-4-1-0.ar3.LON2.gblx.net (208.51.142.129)  27.644 ms ge-5-0-2.402.ar2.LON3                                                                                                  .gblx.net (67.17.212.93)  26.249 ms ge-4-1-0.ar3.LON2.gblx.net (208.51.142.129)                                                                                                    29.208 ms
10  pos0-0-0-155M.ar1.WDC2.gblx.net (67.17.68.178)  102.336 ms  103.361 ms  101.                                                                                                  072 ms
11  UltraDNS.s11-0-0.ar1.wdc2.gblx.net (208.48.23.182)  104.297 ms  102.317 ms                                                                                                    102.390 ms
12  * * *
13  *

- - -

traceroute fhm.com
traceroute: Warning: fhm.com has multiple addresses; using 204.74.99.100
traceroute to fhm.com (204.74.99.100), 30 hops max, 40 byte packets
 1  [www.routerlogin.com](www.routerlogin.com) (192.168.0.1)  5.298 ms  2.823 ms  35.767 ms
 2  dr4.bllon.uk.easynet.net (212.134.12.203)  26.403 ms  25.969 ms  25.244 ms
 3  ge-3-2-0-46.br0.bllon.uk.easynet.net (82.109.182.129)  25.966 ms  28.806 ms                                                                                                    26.387 ms
 4  ge0-1-1.er3.bllon.uk.easynet.net (212.135.12.41)  25.680 ms  26.724 ms  26.5                                                                                                  20 ms
 5  ge0-0-0.er4.bllon.uk.easynet.net (212.135.12.34)  25.928 ms  26.747 ms  26.2                                                                                                  83 ms
 6  ge1-0-0.er3.tclon.uk.easynet.net (82.108.6.146)  34.958 ms  25.878 ms  26.51                                                                                                  9 ms
 7  ge0-0-0.er3.thlon.uk.easynet.net (82.108.6.150)  26.409 ms  25.707 ms  26.48                                                                                                  0 ms
 8  ip-217-204-60-226.easynet.co.uk (217.204.60.226)  27.440 ms  40.089 ms  26.0                                                                                                  14 ms
 9  ge-4-1-0.ar3.LON2.gblx.net (208.51.142.129)  27.644 ms ge-5-0-2.402.ar2.LON3                                                                                                  .gblx.net (67.17.212.93)  26.249 ms ge-4-1-0.ar3.LON2.gblx.net (208.51.142.129)                                                                                                    29.208 ms
10  pos0-0-0-155M.ar1.WDC2.gblx.net (67.17.68.178)  102.336 ms  103.361 ms  101.                                                                                                  072 ms
11  UltraDNS.s11-0-0.ar1.wdc2.gblx.net (208.48.23.182)  104.297 ms  102.317 ms                                                                                                    102.390 ms
12  * * *
13  *

---

### Post by DistantDave on 2007-08-27
Sorry, the second Traceroute should be as follows:

traceroute fhm.com
traceroute: Warning: fhm.com has multiple addresses; using 195.69.153.20
traceroute to fhm.com (195.69.153.20), 30 hops max, 40 byte packets
 1  [www.routerlogin.com](www.routerlogin.com) (192.168.0.1)  4.891 ms  10.937 ms  3.900 ms
 2  dr4.bllon.uk.easynet.net (212.134.12.203)  24.584 ms  26.514 ms  27.091 ms
 3  ge-3-2-0-46.br0.bllon.uk.easynet.net (82.109.182.129)  42.565 ms  43.255 ms  62.761 ms
 4  ge0-1-0.er3.bllon.uk.easynet.net (212.135.12.37)  26.704 ms  27.142 ms  27.150 ms
 5  ge0-0-0.er4.bllon.uk.easynet.net (212.135.12.34)  30.021 ms  27.322 ms  26.641 ms
 6  ge1-0-0.er3.tclon.uk.easynet.net (82.108.6.146)  29.107 ms  30.421 ms  28.802 ms
 7  ge0-0-0.er3.thlon.uk.easynet.net (82.108.6.150)  28.848 ms  25.761 ms  26.056 ms
 8  ip-217-204-60-114.easynet.co.uk (217.204.60.114)  30.929 ms  28.664 ms  30.850 ms
 9  ge-4-1-0.ar3.LON2.gblx.net (208.51.142.129)  30.311 ms ge-5-0-2.402.ar2.LON3.gblx.net (67.17.212.93)  26.773 ms  26.108 ms
10  ge4-3-10G.ar4.LON3.gblx.net (67.17.104.2)  27.392 ms  25.462 ms  27.712 ms
11  level3-2.ar2.LON3.gblx.net (208.50.13.194)  25.864 ms  27.675 ms  26.985 ms
12  ge-10-2.ipcolo1.London1.Level3.net (4.68.116.137)  27.350 ms ge-11-2.ipcolo1.London1.Level3.net (4.68.116.169)  29.243 ms ge-10-0.ipcolo1.London1.Level3.net (4.68.116.9)  27.618 ms
13  unknown.Level3.net (212.113.10.138)  27.529 ms  27.479 ms  28.736 ms

---

### Post by Technoviking on 2007-08-28
Moved back, the FHM front page can be somewhat risqué.

---

