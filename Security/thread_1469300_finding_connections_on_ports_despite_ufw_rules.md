---
title: "finding connections on ports despite ufw rules"
date: 2010-05-02
forum: Security
---

### Post by jasonmchristos on 2010-05-02
my ufw rules have been loaded and active yet using iptraf i see tcp connections on ports that were never allowed by ufw. can anyone explain this too me does ufw just not work?

---

### Post by jasonmchristos on 2010-05-02
> **jasonmchristos said:**
> my ufw rules have been loaded and active yet using iptraf i see tcp connections on ports that were never allowed by ufw. can anyone explain this too me does ufw just not work?

iptraf shows

&#9484;85.190.0.3:40866                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:3961                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:41606                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:40053                                                                     =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:38036                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:4167                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:59374                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:44757                                                                     =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:39287                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:50305                                                                     =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:33428                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:5716                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:43203                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:6000                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:60116                                                                         =       3                  180       S---          eth0      

... the list continues all with similar connections from this same ip
-------------------------------------------------------------------------------------------------------
85.190.0.3 Whois Information
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net](http://www.ripe.net)[Who Is Domain][trace][Reverse DNS Search]/db/support/db-terms-conditions.pdf

% Note: This output has been filtered.
% To receive output for a database update, use the "-B" flag.

% Information related to '85.190.0.0[Who Is IP][trace][Reverse IP Search] - 85.190.0.255[Who Is IP][trace][Reverse IP Search]'

inetnum: 85.190.0.0[Who Is IP][trace][Reverse IP Search] - 85.190.0.255[Who Is IP][trace][Reverse IP Search]
netname: PROBE-NETWORKS-III-FFM3
descr: Probe Networks Colo3-Telecity FFM
country: DE
admin-c: PROB1-RIPE
tech-c: PROB1-RIPE
status: ASSIGNED PA
mnt-by: PROBE-MNT
mnt-lower: PROBE-MNT
remarks:
remarks: ****************************************************
remarks: ****************************************************
remarks: If you see portscans/abuse from 85.190.0.3[Who Is IP][trace][Reverse IP Search]
remarks: Please read [http://freenode.net](http://freenode.net)[Who Is Domain][trace][Reverse DNS Search]/policy.shtml#proxies
remarks: ****************************************************
remarks: ****************************************************
remarks:
remarks: INFRA-AW
source: RIPE # Filtered

role: Probe Networks
address: Probe Networks
address: Auf Struetzberg 26
address: 66663 Merzig
address: Germany
phone: +49 180 5959723
fax-no: +49 180 5998480
remarks: trouble: In case of trouble please mail [Who Is Domain][trace][Reverse DNS Search]
remarks: trouble: Abuse contact [Who Is Domain][trace][Reverse DNS Search]
remarks: for more information check [http://www.probe-networks.de](http://www.probe-networks.de)[Who Is Domain][trace][Reverse DNS Search]
admin-c: JF855-RIPE
tech-c: JF855-RIPE
nic-hdl: PROB1-RIPE
mnt-by: PROBE-MNT
source: RIPE # Filtered
abuse-mailbox: [Who Is Domain][trace][Reverse DNS Search]

% Information related to '85.190.0.0[Who Is IP][trace][Reverse IP Search]/16AS29686'

route: 85.190.0.0[Who Is IP][trace][Reverse IP Search]/16
descr: Probe Networks european network
origin: AS29686
mnt-by: PROBE-MNT
source: RIPE # Filtered

% Information related to '85.190.0.0[Who Is IP][trace][Reverse IP Search]/19AS29686'

route: 85.190.0.0[Who Is IP][trace][Reverse IP Search]/19
descr: Probe Networks european network
origin: AS29686
mnt-by: PROBE-MNT
source: RIPE # Filtered

---

### Post by jasonmchristos on 2010-05-02
here is my firewall rules so that you can see that those ports were not allowed

ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
51413                      ALLOW IN    Anywhere

80/tcp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
8.8.8.8 53/udp             ALLOW OUT   Anywhere
8.8.4.4 53/udp             ALLOW OUT   Anywhere
8001/tcp                   ALLOW OUT   Anywhere
19800/tcp                  ALLOW OUT   Anywhere
11371/tcp                  ALLOW OUT   Anywhere

---

### Post by spynappels on 2010-05-02
Are they RELATED connections?

---

### Post by jasonmchristos on 2010-05-04
> **jasonmchristos said:**
> iptraf shows

&#9484;85.190.0.3:40866                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:3961                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:41606                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:40053                                                                     =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:38036                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:4167                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:59374                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:44757                                                                     =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:39287                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:50305                                                                     =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:33428                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:5716                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:43203                                                                         =       3                  180       S---          eth0          &#9474;
&#9474;&#9492;my ip address:6000                                                                      =       0                    0       ----          eth0          &#9474;
&#9474;&#9484;85.190.0.3:60116                                                                         =       3                  180       S---          eth0      

... the list continues all with similar connections from this same ip
-------------------------------------------------------------------------------------------------------
85.190.0.3 Whois Information
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net](http://www.ripe.net)[Who Is Domain][trace][Reverse DNS Search]/db/support/db-terms-conditions.pdf

% Note: This output has been filtered.
% To receive output for a database update, use the "-B" flag.

% Information related to '85.190.0.0[Who Is IP][trace][Reverse IP Search] - 85.190.0.255[Who Is IP][trace][Reverse IP Search]'

inetnum: 85.190.0.0[Who Is IP][trace][Reverse IP Search] - 85.190.0.255[Who Is IP][trace][Reverse IP Search]
netname: PROBE-NETWORKS-III-FFM3
descr: Probe Networks Colo3-Telecity FFM
country: DE
admin-c: PROB1-RIPE
tech-c: PROB1-RIPE
status: ASSIGNED PA
mnt-by: PROBE-MNT
mnt-lower: PROBE-MNT
remarks:
remarks: ****************************************************
remarks: ****************************************************
remarks: If you see portscans/abuse from 85.190.0.3[Who Is IP][trace][Reverse IP Search]
remarks: Please read [http://freenode.net](http://freenode.net)[Who Is Domain][trace][Reverse DNS Search]/policy.shtml#proxies
remarks: ****************************************************
remarks: ****************************************************
remarks:
remarks: INFRA-AW
source: RIPE # Filtered

role: Probe Networks
address: Probe Networks
address: Auf Struetzberg 26
address: 66663 Merzig
address: Germany
phone: +49 180 5959723
fax-no: +49 180 5998480
remarks: trouble: In case of trouble please mail [Who Is Domain][trace][Reverse DNS Search]
remarks: trouble: Abuse contact [Who Is Domain][trace][Reverse DNS Search]
remarks: for more information check [http://www.probe-networks.de](http://www.probe-networks.de)[Who Is Domain][trace][Reverse DNS Search]
admin-c: JF855-RIPE
tech-c: JF855-RIPE
nic-hdl: PROB1-RIPE
mnt-by: PROBE-MNT
source: RIPE # Filtered
abuse-mailbox: [Who Is Domain][trace][Reverse DNS Search]

% Information related to '85.190.0.0[Who Is IP][trace][Reverse IP Search]/16AS29686'

route: 85.190.0.0[Who Is IP][trace][Reverse IP Search]/16
descr: Probe Networks european network
origin: AS29686
mnt-by: PROBE-MNT
source: RIPE # Filtered

% Information related to '85.190.0.0[Who Is IP][trace][Reverse IP Search]/19AS29686'

route: 85.190.0.0[Who Is IP][trace][Reverse IP Search]/19
descr: Probe Networks european network
origin: AS29686
mnt-by: PROBE-MNT
source: RIPE # Filtered


ahh i figured it out the s flag means a onnection was never made but attempted, usually a port scan - hmmm why am i bieng scanned

[IMG]http://iptraf.seul.org/2.7/stylesheet-images/tip.gif[/IMG]**Tip** If you notice unusual SYN activity (too many initial (S---) but frozen SYN entries, or rapidly increasing initial SYN packets for a single connection), you may be under a SYN flooding attack or TCP port scan. Apply appropriate measures, or the targeted machines may begin denying network services.
from ... [http://iptraf.seul.org/2.7/itrafmon.html](http://iptraf.seul.org/2.7/itrafmon.html)

more info on why i was mistaken shown hgere [http://upload.wikimedia.org/wikipedia/commons/3/37/Netfilter-packet-flow.svg](http://upload.wikimedia.org/wikipedia/commons/3/37/Netfilter-packet-flow.svg) :KS

---

### Post by jasonmchristos on 2010-05-04
RELATED? i mean they were all from the same ip apparently i was bieng port scanned

---

### Post by cariboo on 2010-05-04
Welcome to the Internet, scans and attempted cracks go on 24/7.

---

