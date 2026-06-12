---
title: "Snort Error"
date: 2009-07-31
forum: Security
---

### Post by Dananjaya86 on 2009-07-31
I have snort version 2.7 and mysql Version 14.12 Distrib. 5.0.75 running on Ubuntu 9.04..
after I configure snort I ran this code;

```
 snort -c /etc/snort/snort.conf

```

to verify configuration was correct and snort is up and running..but instead the acsii art of the snort-pig I should get at the end of the output,as a sign of configuration was successful..I get this;

```

Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Var 'any_ADDRESS' defined, value len = 15 chars, value = 0.0.0.0/0.0.0.0
Var 'lo_ADDRESS' defined, value len = 19 chars, value = 127.0.0.0/255.0.0.0
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
Var 'HOME_NET' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'EXTERNAL_NET' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'DNS_SERVERS' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'SMTP_SERVERS' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'HTTP_SERVERS' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'SQL_SERVERS' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'TELNET_SERVERS' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'SNMP_SERVERS' defined, value len = 14 chars, value = 192.168.1.0/24
Var 'HTTP_PORTS' defined, value len = 2 chars, value = 80
Var 'SHELLCODE_PORTS' defined, value len = 3 chars, value = !80
Var 'ORACLE_PORTS' defined, value len = 4 chars, value = 1521
Var 'AIM_SERVERS' defined, value len = 185 chars
   [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9
   .0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24]
Var 'RULE_PATH' defined, value len = 16 chars, value = /etc/snort/rules
,-----------[Flow Config]----------------------
| Stats Interval:  0
| Hash Method:     2
| Memcap:          10485760
| Rows  :          4099
| Overhead Bytes:  16400(%0.16)
`----------------------------------------------
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: FIRST
    Fragment timeout: 60 seconds
    Fragment min_ttl:   1
    Fragment ttl_limit (not used): 5
    Fragment Problems: 1
    Bound Addresses: 0.0.0.0/0.0.0.0
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
      1433 client (Footprint) 
      1521 client (Footprint) 
      3306 client (Footprint) 
    Bound Addresses:0.0.0.0/0.0.0.0
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

+-----------------------[thresholding-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[thresholding-global]----------------------------------
| none
+-----------------------[thresholding-local]-----------------------------------
| none
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/
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
      Ports: 25 
      Inspection Type:            STATEFUL
      Normalize Spaces:           YES
      Ignore Data:                NO
      Ignore TLS Data:            NO
      Ignore Alerts:              NO
      Max Command Length:         0
      Max Header Line Length:     0
      Max Response Line Length:   0
      X-Link2State Alert:         YES
      Drop on X-Link2State Alert: NO

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

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
3382 Snort rules read
    3382 detection rules
    0 decoder rules
    0 preprocessor rules
3382 Option Chains linked into 272 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

Verifying Preprocessor Configurations!
Warning: flowbits key 'community_uri.size.1050' is set but not ever checked.
Warning: flowbits key 'realplayer.playlist' is checked but not ever set.
Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked.
Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set.
37 out of 512 flowbits in use.
***
*** interface device lookup found: eth0
***

Initializing Network Interface eth0
OpenPcap() device eth0 network lookup: 
        eth0: no IPv4 address assigned
Decoding Ethernet on interface eth0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = snort
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = unknown:eth0
ERROR: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Fatal Error, Quitting..

```

could anybody kindly tell me what seems to be the problem? I checked whether i have the permission to access the mysql port and made sure iptables are allowing connection..and checked whether i have correctly configured the mysql port..
really appreciate if someone can give me some pointers..i did some research at first but could not get this solved.:confused:

---

