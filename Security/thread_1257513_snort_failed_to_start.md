---
title: "snort failed to start"
date: 2009-09-03
forum: Security
---

### Post by Lori700698 on 2009-09-03
Ok, any idea what I did wrong?  I couldn't find any solutions to this error.

```
 /usr/local/bin/snort -c /etc/snort/snort.conf
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf
PortVar 'HTTP_PORTS' defined :  [ 80 2301 3128 7777 7779 8000 8008 8028 8080 8180 8888 9999 ]
PortVar 'SHELLCODE_PORTS' defined :  [ any ]
PortVar 'ORACLE_PORTS' defined :  [ 1024:65535 ]
PortVar 'AUTH_PORTS' defined :  [ 113 ]
PortVar 'DNS_PORTS' defined :  [ 53 ]
PortVar 'FINGER_PORTS' defined :  [ 79 ]
PortVar 'FTP_PORTS' defined :  [ 21 ]
PortVar 'IMAP_PORTS' defined :  [ 143 ]
PortVar 'IRC_PORTS' defined :  [ 6665:6669 7000 ]
PortVar 'MSSQL_PORTS' defined :  [ 1433 ]
PortVar 'NNTP_PORTS' defined :  [ 119 ]
PortVar 'POP2_PORTS' defined :  [ 109 ]
PortVar 'POP3_PORTS' defined :  [ 110 ]
PortVar 'SUNRPC_PORTS' defined :  [ 111 32770:32779 ]
PortVar 'RLOGIN_PORTS' defined :  [ 513 ]
PortVar 'RSH_PORTS' defined :  [ 514 ]
PortVar 'SMB_PORTS' defined :  [ 139 445 ]
PortVar 'SMTP_PORTS' defined :  [ 25 ]
PortVar 'SNMP_PORTS' defined :  [ 161 ]
PortVar 'SSH_PORTS' defined :  [ 22 ]
PortVar 'TELNET_PORTS' defined :  [ 23 ]
PortVar 'MAIL_PORTS' defined :  [ 25 143 465 691 ]
PortVar 'SSL_PORTS' defined :  [ 25 443 465 636 993 995 ]
PortVar 'DCERPC_NCACN_IP_TCP' defined :  [ 139 445 ]
PortVar 'DCERPC_NCADG_IP_UDP' defined :  [ 138 1024:65535 ]
PortVar 'DCERPC_NCACN_IP_LONG' defined :  [ 135 139 445 593 1024:65535 ]
PortVar 'DCERPC_NCACN_UDP_LONG' defined :  [ 135 1024:65535 ]
PortVar 'DCERPC_NCACN_UDP_SHORT' defined :  [ 135 593 1024:65535 ]
PortVar 'DCERPC_NCACN_TCP' defined :  [ 2103 2105 2107 ]
PortVar 'DCERPC_BRIGHTSTORE' defined :  [ 6503:6504 ]
Detection:
   Search-Method = AC-BNFA-Q
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: WINDOWS
    Fragment timeout: 180 seconds
    Fragment min_ttl:   1
    Fragment ttl_limit (not used): 5
    Fragment Problems: 0
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 8192
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: ACTIVE
    Max UDP sessions: 131072
    Track ICMP sessions: INACTIVE
    Log info if session memory consumption exceeds 1048576
Stream5 TCP Policy config:
    Reassembly Policy: WINDOWS
    Timeout: 30 seconds
    Min ttl:  1
    Maximum number of bytes to queue per session: 1048576
    Maximum number of segs to queue per session: 2621
    Options:
        Static Flushpoint Sizes: YES
    Reassembly Ports:
      21 client (Footprint) 
      22 client (Footprint) 
      23 client (Footprint) 
      25 client (Footprint) 
      42 client (Footprint) 
      53 client (Footprint) 
      79 client (Footprint) 
      80 client (Footprint) 
      109 client (Footprint) 
      110 client (Footprint) 
      111 client (Footprint) 
      113 client (Footprint) 
      119 client (Footprint) 
      135 client (Footprint) 
      136 client (Footprint) 
      137 client (Footprint) 
      139 client (Footprint) 
      143 client (Footprint) 
      161 client (Footprint) 
      443 client (Footprint) server (Footprint)
Stream5 UDP Policy config:
    Timeout: 30 seconds
    Options:
        Ignore Any -> Any Rules: YES
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /etc/snort/unicode.map
      IIS Unicode Map Codepage: 1252
    DEFAULT SERVER CONFIG:
      Server profile: All
      Ports: 80 2301 3128 7777 7779 8000 8008 8028 8080 8180 8888 9999 
      Server Flow Depth: 1460
      Client Flow Depth: 300
      Max Chunk Length: 500000
      Max Header Field Length: 0
      Max Number Header Fields: 0
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
      Normalize HTTP Headers: NO
      Normalize HTTP Cookies: NO
      Ascii: YES alert: NO
      Double Decoding: YES alert: NO
      %U Encoding: YES alert: YES
      Bare Byte: YES alert: NO
      Base36: OFF
      UTF 8: YES alert: NO
      IIS Unicode: YES alert: NO
      Multiple Slash: YES alert: NO
      IIS Backslash: YES alert: NO
      Directory Traversal: YES alert: NO
      Web Root Traversal: YES alert: NO
      Apache WhiteSpace: YES alert: NO
      IIS Delimiter: YES alert: NO
      IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG
      Non-RFC Compliant Characters: 0x00 0x01 0x02 0x03 0x04 0x05 0x06 0x07 
      Whitespace Characters: 0x09 0x0b 0x0c 0x0d 
rpc_decode arguments:
    Ports to decode RPC on: 111 32770 32771 32772 32773 32774 32775 32776 32777 32778 32779 
    alert_fragments: INACTIVE
    alert_large_fragments: ACTIVE
    alert_incomplete: ACTIVE
    alert_multiple_requests: ACTIVE
Tagged Packet Limit: 256
Loading dynamic engine /usr/local/lib/snort_dynamicengine/libsf_engine.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/bad-traffic.so... ERROR: Failed to load /usr/local/lib/snort_dynamicrules/bad-traffic.so: /usr/local/lib/snort_dynamicrules/bad-traffic.so: cannot open shared object file: No such file or directory
Fatal Error, Quitting..

```

---

### Post by TuckLive on 2009-09-04
nvm

---

### Post by ikt on 2009-09-30
> **TuckLive said:**
> nvm

what was the solution?

---

### Post by Spontan on 2009-10-01
The snort source comes with precombiles bad-traffic.so. You just have to find it and locate it in that area.


Also, if you do not want to deal with it, in snort.conf you can put a # in front of the statement declaring bad-traffic.so in that directory. It will just ignore it.

The same deal happens with local.rules. It is just a blank file unless you want to customise your snort rules.

---

### Post by juancarlospaco on 2009-10-02
Im trying to install snort, i already installed it before,
its so unstable, its broke again and again, and when mysql upgrades too.

I choosed to use Prelude IDS wich is better, 
more professional, and optional comercial support avaliable.

---

