---
title: "snort not logging to logfile or mysql db"
date: 2008-07-30
forum: Security
---

### Post by JordanCB on 2008-07-30
Hello,

I'm trying to get Snort+MySql+Base running on a HH install of Ubuntu.

I have followed a howtoforge tutorial on this and seem to have everything okay.  Snort does not appear to be logging anywhere though,  I have installed BASE fine and can access it, but it will never display any alerts.  

I have portscanned and pinged the crap out of the box but never get any alerts.  I have also downloaded the latest rules from snort.org and installed those as well.

in my /etc/snort/snort.conf I have the following set up
```
var HOME_NET 192.168.2.0/24
var EXTERNAL_NET any
var RULE_PATH /etc/snort/rules
output database: log, mysql, user=snort password=****** dbname=snort host=localhost

```

I originally had external net set to !$HOME_NET , but then realized that I want my box to alert me for LAN traffic as well so I changed it to any. 

the output of "snort -c /etc/snort/snort.conf -i eth0" is as follows


```
Parsing Rules file /etc/snort/snort.conf
PortVar 'HTTP_PORTS' defined :  [ 80 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: FIRST
    Fragment timeout: 60 seconds
    Fragment min_ttl:   1
    Fragment ttl_limit (not used): 5
    Fragment Problems: 1
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 8192
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: INACTIVE
    Track ICMP sessions: INACTIVE
Stream5 TCP Policy config:
    Reassembly Policy: FIRST
    Timeout: 30 seconds
    Min ttl:  1
    Options:
        Static Flushpoint Sizes: YES
    Reassembly Ports:
      21 client (Footprint)
      23 client (Footprint)
      25 client (Footprint)
      42 client (Footprint)
      53 client (Footprint)
      80 client (Footprint)
      110 client (Footprint)
      111 client (Footprint)
      135 client (Footprint)
      136 client (Footprint)
      137 client (Footprint)
      139 client (Footprint)
      143 client (Footprint)
      445 client (Footprint)
      513 client (Footprint)
      514 client (Footprint)
      1433 client (Footprint)
      1521 client (Footprint)
      2401 client (Footprint)
      3306 client (Footprint)
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /etc/snort/unicode.map
      IIS Unicode Map Codepage: 1252
    DEFAULT SERVER CONFIG:
      Server profile: All
      Ports: 80 8080 8180
      Flow Depth: 300
      Max Chunk Length: 500000
      Max Header Field Length: 0
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
      Ascii: YES alert: NO
      Double Decoding: YES alert: YES
      %U Encoding: YES alert: YES
      Bare Byte: YES alert: YES
      Base36: OFF
      UTF 8: OFF
      IIS Unicode: YES alert: YES
      Multiple Slash: YES alert: NO
      IIS Backslash: YES alert: NO
      Directory Traversal: YES alert: NO
      Web Root Traversal: YES alert: YES
      Apache WhiteSpace: YES alert: NO
      IIS Delimiter: YES alert: NO
      IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG
      Non-RFC Compliant Characters: NONE
      Whitespace Characters: 0x09 0x0b 0x0c 0x0d
rpc_decode arguments:
    Ports to decode RPC on: 111 32771
    alert_fragments: INACTIVE
    alert_large_fragments: ACTIVE
    alert_incomplete: ACTIVE
    alert_multiple_requests: ACTIVE
Portscan Detection Config:
    Detect Protocols:  TCP UDP ICMP IP
    Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan
    Sensitivity Level: Low
    Memcap (in bytes): 10000000
    Number of Nodes:   36900

Tagged Packet Limit: 256
Loading dynamic engine /usr/local/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/local/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/local/lib/snort_dynamicpreprocessor/
FTPTelnet Config:
    GLOBAL CONFIG
      Inspection Type: stateful
      Check for Encrypted Traffic: YES alert: YES
      Continue to check encrypted data: NO
    TELNET CONFIG:
      Ports: 23
      Are You There Threshold: 200
      Normalize: YES
      Detect Anomalies: NO
    FTP CONFIG:
      FTP Server: default
        Ports: 21
        Check for Telnet Cmds: YES alert: YES
        Identify open data channels: YES
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: YES
        Max Response Length: 256

SMTP Config:
    Ports: 25 587 691
    Inspection Type: Stateful
    Normalize: EXPN RCPT VRFY
    Ignore Data: No
    Ignore TLS Data: No
    Ignore SMTP Alerts: No
    Max Command Line Length: Unlimited
    Max Specific Command Line Length:
       ETRN:500 EXPN:255 HELO:500 HELP:500 MAIL:260
       RCPT:300 VRFY:255
    Max Header Line Length: Unlimited
    Max Response Line Length: Unlimited
    X-Link2State Alert: Yes
    Drop on X-Link2State Alert: No
    Alert on commands: None

DCE/RPC Decoder config:
    Autodetect ports ENABLED
    SMB fragmentation ENABLED
    DCE/RPC fragmentation ENABLED
    Max Frag Size: 3000 bytes
    Memcap: 100000 KB
    Alert if memcap exceeded DISABLED

DNS config:
    DNS Client rdata txt Overflow Alert: ACTIVE
    Obsolete DNS RR Types Alert: INACTIVE
    Experimental DNS RR Types Alert: INACTIVE
    Ports: 53
SSLPP config:
    Encrypted packets: not inspected
    Ports:
      443      465      563      636      989
      992      993      994      995

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
2830 Snort rules read
    2830 detection rules
    0 decoder rules
    0 preprocessor rules
2830 Option Chains linked into 215 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

+-------------------[Rule Port Counts]---------------------------------------
|             tcp     udp    icmp      ip
|     src     122      12       0       0
|     dst    2382     163       0       0
|     any      68      50      50      20
|      nc      22       8      15      18
|     s+d       3       3       0       0
+----------------------------------------------------------------------------

+-----------------------[thresholding-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[thresholding-global]----------------------------------
| none
+-----------------------[thresholding-local]-----------------------------------
| gen-id=1      sig-id=3543       type=Threshold tracking=src count=5   seconds=2
| gen-id=1      sig-id=2496       type=Both      tracking=dst count=20  seconds=60
| gen-id=1      sig-id=2494       type=Both      tracking=dst count=20  seconds=60
| gen-id=1      sig-id=3273       type=Threshold tracking=src count=5   seconds=2
| gen-id=1      sig-id=3152       type=Threshold tracking=src count=5   seconds=2
| gen-id=1      sig-id=3527       type=Limit     tracking=dst count=5   seconds=60
| gen-id=1      sig-id=3542       type=Threshold tracking=src count=5   seconds=2
| gen-id=1      sig-id=2523       type=Both      tracking=dst count=10  seconds=10
| gen-id=1      sig-id=2923       type=Threshold tracking=dst count=10  seconds=60
| gen-id=1      sig-id=2275       type=Threshold tracking=dst count=5   seconds=60
| gen-id=1      sig-id=2495       type=Both      tracking=dst count=20  seconds=60
| gen-id=1      sig-id=2924       type=Threshold tracking=dst count=10  seconds=60
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Verifying Preprocessor Configurations!
Warning: flowbits key 'realplayer.playlist' is checked but not ever set.
Warning: flowbits key 'dce.bind.veritas' is set but not ever checked.
Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set.
Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked.
35 out of 512 flowbits in use.

Initializing Network Interface eth0
Decoding Ethernet on interface eth0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = snort
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = 192.168.2.200
database:     sensor id = 1
database: schema version = 107
database: using the "log" facility

[ Port Based Pattern Matching Memory ]
+-[AC-BNFA Search Info Summary]------------------------------
| Instances        : 187
| Patterns         : 11445
| Pattern Chars    : 98971
| Num States       : 52363
| Num Match States : 7589
| Memory           :   1.47Mbytes
|   Patterns       :   0.31M
|   Match Lists    :   0.35M
|   Transitions    :   0.77M
+-------------------------------------------------

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.2.1 (Build 16)
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/team.html
           (C) Copyright 1998-2008 Sourcefire Inc., et al.
           Using PCRE version: 7.7 2008-05-07

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.8  <Build 14>
           Preprocessor Object: SF_DCERPC  Version 1.1  <Build 4>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 7>
           Preprocessor Object: SF_FTPTELNET  Version 1.1  <Build 10>
           Preprocessor Object: SF_SSLPP  Version 1.0  <Build 1>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 2>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 1>
           Preprocessor Object: SF_Dynamic_Example_Preprocessor  Version 1.0  <Build 1>
Not Using PCAP_FRAMES
```

I have checked the mysql database, my database exists and tables exists, I can log in with my user 'snort' just fine and have granted all privileges.  It just doesn't appear to be logging anything.  /var/log/snort does not have anything written to logs either.   Anyone have any idea what my problem may be?? I'm stumped here.  Thanks for any advice or suggestions.

-- J

---

### Post by chazzzle on 2008-12-01
was this ever resolved?

---

### Post by bodhi.zazen on 2008-12-01
> **chazzzle said:**
> was this ever resolved?

Take a look at the snort tutorial "Intrusion Detection" sticky.

As an aside you will not be able to monitor your LAN without a HUB or a smart switch (or a router which has a monitoring port).

I tried to buy a HUB for this, and they do not make them any longer (go figure)

---

### Post by Kinstonian on 2008-12-01
bodhi.zazen, I have a Linksys EW5HUB that I got off ebay a while ago.  They still have a couple of them for sale, however I think it's only 10 Mbps.

---

### Post by bodhi.zazen on 2008-12-01
> **Kinstonian said:**
> bodhi.zazen, I have a Linksys EW5HUB that I got off ebay a while ago.  They still have a couple of them for sale, however I think it's only 10 Mbps.

Thanks :)

I have an alternate method ...

---

### Post by Kinstonian on 2008-12-01
> **bodhi.zazen said:**
> Thanks :)

I have an alternate method ...

What are you using instead?  Do you have a box between your router and modem or something?

---

### Post by bodhi.zazen on 2008-12-01
No, I needed a switch anyways, so I got a smart switch.

---

### Post by Kinstonian on 2008-12-01
> **bodhi.zazen said:**
> No, I needed a switch anyways, so I got a smart switch.

Ahh, that's a little more money than I wanted to spend, but it looks like a good solution. :)  I guess I won't mind so much that they aren't really making hubs anymore as long as switches that can SPAN/mirror ports are becoming more common and affordable...

---

### Post by bodhi.zazen on 2008-12-01
Yea, google is your friend. They are not *that* pricey, and I wanted a fast switch as everything is changing to 10/100/1000

---

