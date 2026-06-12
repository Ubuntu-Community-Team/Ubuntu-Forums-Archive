---
title: "snort setup problems"
date: 2011-02-02
forum: Security
---

### Post by sparkler on 2011-02-02
im getting this when following instruckstions in this thread to setup snort [http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696) anyone know what ive done wrong?


```
Running in Test mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/etc/snort/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 80 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
PortVar 'FTP_PORTS' defined :  [ 21 ]
Tagged Packet Limit: 256
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: FIRST
    Fragment timeout: 60 seconds
    Fragment min_ttl:   1
    Fragment Problems: 1
    Overlap Limit:     10
    Min fragment Length:     0
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 8192
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: INACTIVE
    Track ICMP sessions: INACTIVE
    Log info if session memory consumption exceeds 1048576
Stream5 TCP Policy config:
    Reassembly Policy: FIRST
    Timeout: 30 seconds
    Min ttl:  1
    Maximum number of bytes to queue per session: 1048576
    Maximum number of segs to queue per session: 2621
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
      Server Flow Depth: 300
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
    Number of Nodes:   31347
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
        Ignore Telnet Cmd Operations: OFF
        Identify open data channels: YES
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: YES
        Ignore Telnet Cmd Operations: OFF
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
SSH config: 
    Autodetection: DISABLED
    Challenge-Response Overflow Alert: ENABLED
    SSH1 CRC32 Alert: ENABLED
    Server Version String Overflow Alert: ENABLED
    Protocol Mismatch Alert: ENABLED
    Bad Message Direction Alert: DISABLED
    Bad Payload Size Alert: DISABLED
    Unrecognized Version Alert: DISABLED
    Max Encrypted Packets: 20  
    Max Server Version String Length: 80 (Default) 
    MaxClientBytes: 19600 (Default) 
    Ports:
    22
DCE/RPC 2 Preprocessor Configuration
  Global Configuration
    DCE/RPC Defragmentation: Enabled
    Memcap: 102400 KB
    Events: none
  Server Default Configuration
    Policy: WinXP
    Detect ports
      SMB: 139 445 
      TCP: 135 
      UDP: 135 
      RPC over HTTP server: 593 
      RPC over HTTP proxy: None
    Autodetect ports
      SMB: None
      TCP: 1025-65535 
      UDP: 1025-65535 
      RPC over HTTP server: 1025-65535 
      RPC over HTTP proxy: None
    Maximum SMB command chaining: 3 commands
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
    Server side data is trusted

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
Warning: /etc/snort/rules/dos.rules(42) => threshold (in rule) is deprecated; use detection_filter instead.
3382 Snort rules read
    3382 detection rules
    0 decoder rules
    0 preprocessor rules
3382 Option Chains linked into 282 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

+-------------------[Rule Port Counts]---------------------------------------
|             tcp     udp    icmp      ip
|     src     121      19       0       0
|     dst    2922     130       0       0
|     any     115      53      56      27
|      nc      31      10      15      20
|     s+d      12       6       0       0
+----------------------------------------------------------------------------

+-----------------------[detection-filter-config]------------------------------
| memory-cap : 1048576 bytes
+-----------------------[detection-filter-rules]-------------------------------
| none
-------------------------------------------------------------------------------

+-----------------------[rate-filter-config]-----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[rate-filter-rules]------------------------------------
| none
-------------------------------------------------------------------------------

+-----------------------[event-filter-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[event-filter-global]----------------------------------
| none
+-----------------------[event-filter-local]-----------------------------------
| gen-id=1      sig-id=3152       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=2523       type=Both      tracking=dst count=10  seconds=10 
| gen-id=1      sig-id=2923       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=100000312  type=Limit     tracking=src count=1   seconds=360
| gen-id=1      sig-id=2494       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=100000311  type=Limit     tracking=src count=1   seconds=360
| gen-id=1      sig-id=100000160  type=Both      tracking=src count=300 seconds=60 
| gen-id=1      sig-id=100000159  type=Both      tracking=src count=100 seconds=60 
| gen-id=1      sig-id=100000161  type=Both      tracking=dst count=100 seconds=60 
| gen-id=1      sig-id=2924       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=100000310  type=Limit     tracking=src count=1   seconds=360
| gen-id=1      sig-id=100000923  type=Threshold tracking=dst count=200 seconds=60 
| gen-id=1      sig-id=2496       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=100000158  type=Both      tracking=src count=100 seconds=60 
| gen-id=1      sig-id=3273       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=100000162  type=Both      tracking=src count=100 seconds=60 
| gen-id=1      sig-id=2495       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=2275       type=Threshold tracking=dst count=5   seconds=60 
| gen-id=1      sig-id=100000163  type=Both      tracking=src count=100 seconds=60 
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Verifying Preprocessor Configurations!
Warning: flowbits key 'community_uri.size.1050' is set but not ever checked.
Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set.
Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked.
Warning: flowbits key 'realplayer.playlist' is checked but not ever set.
37 out of 512 flowbits in use.
Decoding LoopBack on interface NULL
ERROR: database: Connection to database 'snort_db' failed
Fatal Error, Quitting..

```

---

### Post by bodhi.zazen on 2011-02-02
You have not set up the database.

> ERROR: database: Connection to database 'snort_db' failed

---

### Post by sparkler on 2011-02-02
ive got it working i got the localhost part wrong as my snort password wasn't snort_password

---

### Post by sparkler on 2011-02-02
i am getting more error's after doing the so_rules config and running the test


```
Running in Test mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/etc/snort/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 80 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
PortVar 'FTP_PORTS' defined :  [ 21 ]
Tagged Packet Limit: 256
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic detection libs from /usr/lib/snort_dynamicrule/...
  Loading dynamic detection library /usr/lib/snort_dynamicrule//snmp.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//imap.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//nntp.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//web-activex.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//dos.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//smtp.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//netbios.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//bad-traffic.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//web-client.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//web-iis.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//specific-threats.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//p2p.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//multimedia.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//icmp.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//pop3.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//misc.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//sql.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//chat.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//exploit.so... done
  Loading dynamic detection library /usr/lib/snort_dynamicrule//web-misc.so... done
  Finished Loading all dynamic detection libs from /usr/lib/snort_dynamicrule/
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: FIRST
    Fragment timeout: 60 seconds
    Fragment min_ttl:   1
    Fragment Problems: 1
    Overlap Limit:     10
    Min fragment Length:     0
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 8192
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: INACTIVE
    Track ICMP sessions: INACTIVE
    Log info if session memory consumption exceeds 1048576
Stream5 TCP Policy config:
    Reassembly Policy: FIRST
    Timeout: 30 seconds
    Min ttl:  1
    Maximum number of bytes to queue per session: 1048576
    Maximum number of segs to queue per session: 2621
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
      Server Flow Depth: 300
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
    Number of Nodes:   31347
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
        Ignore Telnet Cmd Operations: OFF
        Identify open data channels: YES
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: YES
        Ignore Telnet Cmd Operations: OFF
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
SSH config: 
    Autodetection: DISABLED
    Challenge-Response Overflow Alert: ENABLED
    SSH1 CRC32 Alert: ENABLED
    Server Version String Overflow Alert: ENABLED
    Protocol Mismatch Alert: ENABLED
    Bad Message Direction Alert: DISABLED
    Bad Payload Size Alert: DISABLED
    Unrecognized Version Alert: DISABLED
    Max Encrypted Packets: 20  
    Max Server Version String Length: 80 (Default) 
    MaxClientBytes: 19600 (Default) 
    Ports:
    22
DCE/RPC 2 Preprocessor Configuration
  Global Configuration
    DCE/RPC Defragmentation: Enabled
    Memcap: 102400 KB
    Events: none
  Server Default Configuration
    Policy: WinXP
    Detect ports
      SMB: 139 445 
      TCP: 135 
      UDP: 135 
      RPC over HTTP server: 593 
      RPC over HTTP proxy: None
    Autodetect ports
      SMB: None
      TCP: 1025-65535 
      UDP: 1025-65535 
      RPC over HTTP server: 1025-65535 
      RPC over HTTP proxy: None
    Maximum SMB command chaining: 3 commands
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
    Server side data is trusted

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
ERROR: /etc/snort/rules/exploit.rules(258) => 'fast_pattern' does not take an argument
Fatal Error, Quitting..

```

---

### Post by bodhi.zazen on 2011-02-03
You will have to review the rules manually and either disable the offending rule or modify it.

You may want to file a bug report with snort and/or use the snort mailing list.

If you post the rule that is problematic, we can look.

Please do not post the entire rule set.

---

### Post by sparkler on 2011-02-04
i think its because i used the 2.8.6 rules to update and snort 2.5.1 is in the repo's

---

### Post by isa.dsouza on 2012-09-19
I have the same error but the line before ERROR: database: Connection to database 'snort_db' failed is different

[ Number of patterns truncated to 20 bytes: 1065 ]
ERROR: database: Connection to database 'snort_db' failed
Fatal Error, Quitting..

After wondering what is going wrong as I followed you tutorial the best I could.

It is in this link [http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

Then searched for an answer again and voila as per this thread [http://ubuntuforums.org/showthread.php?t=1856275&highlight=snort_db](http://ubuntuforums.org/showthread.php?t=1856275&highlight=snort_db) just had to put my password in. In the end it almost always is a user issue and not a system issue.

---

