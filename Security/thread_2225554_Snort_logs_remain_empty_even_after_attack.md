---
title: "Snort logs remain empty even after attack"
date: 2014-05-22
forum: Security
---

### Post by hdry on 2014-05-22
So I was following [this guide]("http://www.symmetrixtech.com/articles/016-snortinstallguide2953.pdf") on how to install Snort, Barnyard 2 and the like.

I've set up Snort so it would run automatically, by editing the rc.local file:
```

    ifconfig eth1 up
    
    /usr/local/snort/bin/snort -D -u snort -g snort \
    -c /usr/local/snort/etc/snort.conf -i eth1
    /usr/local/bin/barnyard2 -c /usr/local/snort/etc/barnyard2.conf \
    -d /var/log/snort \
    -f snort.u2 \
    -w /var/log/snort/barnyard2.waldo \
    -D
```

And I then restarted the computer. Snort was able to run and detect the attack, but the log files (including barnyard2.waldo) remained blank, even if a new log entry was created for each attack.

And then I tested out Snort to see if it's working, and here is the output:

```
Running in Test mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/usr/local/snort/etc/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 36 80:90 311 383 555 591 593 631 801 808 818 901 972 1158 1220 1414 1533 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7000:7001 7071 7144:7145 7510 7770 7777 7779 8000 8008 8014 8028 8080:8082 8085 8088 8090 8118 8123 8180:8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090:9091 9111 9443 9999:10000 11371 12601 15489 29991 33300 34412 34443:34444 41080 44449 50000 50002 51423 53331 55252 55555 56712 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1024:65535 ]
PortVar 'SSH_PORTS' defined :  [ 22 ]
PortVar 'FTP_PORTS' defined :  [ 21 2100 3535 ]
PortVar 'SIP_PORTS' defined :  [ 5060:5061 5600 ]
PortVar 'FILE_DATA_PORTS' defined :  [ 36 80:90 110 143 311 383 555 591 593 631 801 808 818 901 972 1158 1220 1414 1533 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7000:7001 7071 7144:7145 7510 7770 7777 7779 8000 8008 8014 8028 8080:8082 8085 8088 8090 8118 8123 8180:8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090:9091 9111 9443 9999:10000 11371 12601 15489 29991 33300 34412 34443:34444 41080 44449 50000 50002 51423 53331 55252 55555 56712 ]
PortVar 'GTP_PORTS' defined :  [ 2123 2152 3386 ]
Detection:
   Search-Method = AC-Full-Q
    Split Any/Any group = enabled
    Search-Method-Optimizations = enabled
    Maximum pattern length = 20
Tagged Packet Limit: 256
Loading dynamic engine /usr/local/snort/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic detection libs from /usr/local/snort/lib/snort_dynamicrules...
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/misc.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/web-activex.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/bad-traffic.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/web-iis.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/multimedia.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/snmp.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/p2p.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/icmp.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/web-client.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/netbios.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/chat.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/specific-threats.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/imap.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/nntp.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/dos.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/exploit.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/smtp.so... done
  Loading dynamic detection library /usr/local/snort/lib/snort_dynamicrules/web-misc.so... done
  Finished Loading all dynamic detection libs from /usr/local/snort/lib/snort_dynamicrules
Loading all dynamic preprocessor libs from /usr/local/snort/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_modbus_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_gtp_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_imap_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_dnp3_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_sdf_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_sip_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_reputation_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/local/snort/lib/snort_dynamicpreprocessor//libsf_pop_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/local/snort/lib/snort_dynamicpreprocessor/
Log directory = /var/log/snort
WARNING: ip4 normalizations disabled because not inline.
WARNING: tcp normalizations disabled because not inline.
WARNING: icmp4 normalizations disabled because not inline.
WARNING: ip6 normalizations disabled because not inline.
WARNING: icmp6 normalizations disabled because not inline.
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Bound Address: default
    Target-based policy: WINDOWS
    Fragment timeout: 180 seconds
    Fragment min_ttl:   1
    Fragment Anomalies: Alert
    Overlap Limit:     10
    Min fragment Length:     100
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 262144
    TCP cache pruning timeout: 30 seconds
    TCP cache nominal timeout: 3600 seconds
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: ACTIVE
    Max UDP sessions: 131072
    UDP cache pruning timeout: 30 seconds
    UDP cache nominal timeout: 180 seconds
    Track ICMP sessions: INACTIVE
    Track IP sessions: INACTIVE
    Log info if session memory consumption exceeds 1048576
    Send up to 2 active responses
    Wait at least 5 seconds between responses
    Protocol Aware Flushing: ACTIVE
        Maximum Flush Point: 16000
      Max Expected Streams: 768
Stream5 TCP Policy config:
    Bound Address: default
    Reassembly Policy: WINDOWS
    Timeout: 180 seconds
    Limit on TCP Overlaps: 10
    Maximum number of bytes to queue per session: 1048576
    Maximum number of segs to queue per session: 2621
    Options:
        Require 3-Way Handshake: YES
        3-Way Handshake Timeout: 180
        Detect Anomalies: YES
    Reassembly Ports:
      21 client (Footprint) 
      22 client (Footprint) 
      23 client (Footprint) 
      25 client (Footprint) 
      36 client (Footprint) server (Footprint)
      42 client (Footprint) 
      53 client (Footprint) 
      70 client (Footprint) 
      79 client (Footprint) 
      80 client (Footprint) server (Footprint)
      81 client (Footprint) server (Footprint)
      82 client (Footprint) server (Footprint)
      83 client (Footprint) server (Footprint)
      84 client (Footprint) server (Footprint)
      85 client (Footprint) server (Footprint)
      86 client (Footprint) server (Footprint)
      87 client (Footprint) server (Footprint)
      88 client (Footprint) server (Footprint)
      89 client (Footprint) server (Footprint)
      90 client (Footprint) server (Footprint)
      additional ports configured but not printed.
Stream5 UDP Policy config:
    Timeout: 180 seconds
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /usr/local/snort/etc/unicode.map
      IIS Unicode Map Codepage: 1252
      Memcap used for logging URI and Hostname: 150994944
      Max Gzip Memory: 838860
      Max Gzip Sessions: 9532
      Gzip Compress Depth: 65535
      Gzip Decompress Depth: 65535
    DEFAULT SERVER CONFIG:
      Server profile: All
      Ports (PAF): 36 80 81 82 83 84 85 86 87 88 89 90 311 383 555 591 593 631 801 808 818 901 972 1158 1220 1414 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7000 7001 7071 7144 7145 7510 7770 7777 7779 8000 8008 8014 8028 8080 8081 8082 8085 8088 8090 8118 8123 8180 8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090 9091 9111 9443 9999 10000 11371 12601 15489 29991 33300 34412 34443 34444 41080 44449 50000 50002 51423 53331 55252 55555 56712 
      Server Flow Depth: 0
      Client Flow Depth: 0
      Max Chunk Length: 500000
      Small Chunk Length Evasion: chunk size <= 10, threshold >= 5 times
      Max Header Field Length: 750
      Max Number Header Fields: 100
      Max Number of WhiteSpaces allowed with header folding: 200
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
      Normalize HTTP Headers: NO
      Inspect HTTP Cookies: YES
      Inspect HTTP Responses: YES
      Extract Gzip from responses: YES
      Unlimited decompression of gzip data from responses: YES
      Normalize Javascripts in HTTP Responses: YES
      Max Number of WhiteSpaces allowed with Javascript Obfuscation in HTTP responses: 200
      Normalize HTTP Cookies: NO
      Enable XFF and True Client IP: NO
      Log HTTP URI data: NO
      Log HTTP Hostname data: NO
      Extended ASCII code support in URI: NO
      Ascii: YES alert: NO
      Double Decoding: YES alert: NO
      %U Encoding: YES alert: YES
      Bare Byte: YES alert: NO
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
    alert_large_fragments: INACTIVE
    alert_incomplete: INACTIVE
    alert_multiple_requests: INACTIVE
FTPTelnet Config:
    GLOBAL CONFIG
      Inspection Type: stateful
      Check for Encrypted Traffic: YES alert: NO
      Continue to check encrypted data: YES
    TELNET CONFIG:
      Ports: 23 
      Are You There Threshold: 20
      Normalize: YES
      Detect Anomalies: YES
    FTP CONFIG:
      FTP Server: default
        Ports (PAF): 21 2100 3535 
        Check for Telnet Cmds: YES alert: YES
        Ignore Telnet Cmd Operations: YES alert: YES
        Ignore open data channels: NO
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: YES
        Ignore Telnet Cmd Operations: YES alert: YES
        Max Response Length: 256
SMTP Config:
    Ports: 25 465 587 691 
    Inspection Type: Stateful
    Normalize: ATRN AUTH BDAT DATA DEBUG EHLO EMAL ESAM ESND ESOM ETRN EVFY EXPN HELO HELP IDENT MAIL NOOP ONEX QUEU QUIT RCPT RSET SAML SEND STARTTLS SOML TICK TIME TURN TURNME VERB VRFY X-EXPS XADR XAUTH XCIR XEXCH50 XGEN XLICENSE X-LINK2STATE XQUE XSTA XTRN XUSR CHUNKING X-ADAT X-DRCP X-ERCP X-EXCH50 
    Ignore Data: No
    Ignore TLS Data: No
    Ignore SMTP Alerts: No
    Max Command Line Length: 512
    Max Specific Command Line Length: 
       ATRN:255 AUTH:246 BDAT:255 DATA:246 DEBUG:255 
       EHLO:500 EMAL:255 ESAM:255 ESND:255 ESOM:255 
       ETRN:246 EVFY:255 EXPN:255 HELO:500 HELP:500 
       IDENT:255 MAIL:260 NOOP:255 ONEX:246 QUEU:246 
       QUIT:246 RCPT:300 RSET:246 SAML:246 SEND:246 
       SIZE:255 STARTTLS:246 SOML:246 TICK:246 TIME:246 
       TURN:246 TURNME:246 VERB:246 VRFY:255 X-EXPS:246 
       XADR:246 XAUTH:246 XCIR:246 XEXCH50:246 XGEN:246 
       XLICENSE:246 X-LINK2STATE:246 XQUE:246 XSTA:246 XTRN:246 
       XUSR:246 
    Max Header Line Length: 1000
    Max Response Line Length: 512
    X-Link2State Alert: Yes
    Drop on X-Link2State Alert: No
    Alert on commands: None
    Alert on unknown commands: No
    SMTP Memcap: 838860
    MIME Max Mem: 838860
    Base64 Decoding: Enabled
    Base64 Decoding Depth: Unlimited
    Quoted-Printable Decoding: Enabled
    Quoted-Printable Decoding Depth: Unlimited
    Unix-to-Unix Decoding: Enabled
    Unix-to-Unix Decoding Depth: Unlimited
    Non-Encoded MIME attachment Extraction: Enabled
    Non-Encoded MIME attachment Extraction Depth: Unlimited
    Log Attachment filename: Enabled
    Log MAIL FROM Address: Enabled
    Log RCPT TO Addresses: Enabled
    Log Email Headers: Enabled
    Email Hdrs Log Depth: 1464
SSH config: 
    Autodetection: ENABLED
    Challenge-Response Overflow Alert: ENABLED
    SSH1 CRC32 Alert: ENABLED
    Server Version String Overflow Alert: ENABLED
    Protocol Mismatch Alert: ENABLED
    Bad Message Direction Alert: DISABLED
    Bad Payload Size Alert: DISABLED
    Unrecognized Version Alert: DISABLED
    Max Encrypted Packets: 20  
    Max Server Version String Length: 100  
    MaxClientBytes: 19600 (Default) 
    Ports:
	22
DCE/RPC 2 Preprocessor Configuration
  Global Configuration
    DCE/RPC Defragmentation: Enabled
    Memcap: 102400 KB
    Events: co 
    SMB Fingerprint policy: Disabled
  Server Default Configuration
    Policy: WinXP
    Detect ports (PAF)
      SMB: 139 445 
      TCP: 135 
      UDP: 135 
      RPC over HTTP server: 593 
      RPC over HTTP proxy: None
    Autodetect ports (PAF)
      SMB: None
      TCP: 1025-65535 
      UDP: 1025-65535 
      RPC over HTTP server: 1025-65535 
      RPC over HTTP proxy: None
    Invalid SMB shares: C$ D$ ADMIN$ 
    Maximum SMB command chaining: 3 commands
    SMB file inspection: Disabled
DNS config: 
    DNS Client rdata txt Overflow Alert: ACTIVE
    Obsolete DNS RR Types Alert: INACTIVE
    Experimental DNS RR Types Alert: INACTIVE
    Ports: 53
SSLPP config:
    Encrypted packets: not inspected
    Ports:
      443      465      563      636      989
      992      993      994      995     7801
     7802     7900     7901     7902     7903
     7904     7905     7906     7907     7908
     7909     7910     7911     7912     7913
     7914     7915     7916     7917     7918
     7919     7920
    Server side data is trusted
Sensitive Data preprocessor config: 
    Global Alert Threshold: 25
    Masked Output: DISABLED
SIP config: 
    Max number of sessions: 40000  
    Max number of dialogs in a session: 4 (Default) 
    Status: ENABLED
    Ignore media channel: DISABLED
    Max URI length: 512  
    Max Call ID length: 80  
    Max Request name length: 20 (Default) 
    Max From length: 256 (Default) 
    Max To length: 256 (Default) 
    Max Via length: 1024 (Default) 
    Max Contact length: 512  
    Max Content length: 2048  
    Ports:
	5060	5061	5600
    Methods:
	  invite cancel ack bye register options refer subscribe update join info message notify benotify do qauth sprack publish service unsubscribe prack
IMAP Config:
    Ports: 143 
    IMAP Memcap: 838860
    MIME Max Mem: 838860
    Base64 Decoding: Enabled
    Base64 Decoding Depth: Unlimited
    Quoted-Printable Decoding: Enabled
    Quoted-Printable Decoding Depth: Unlimited
    Unix-to-Unix Decoding: Enabled
    Unix-to-Unix Decoding Depth: Unlimited
    Non-Encoded MIME attachment Extraction: Enabled
    Non-Encoded MIME attachment Extraction Depth: Unlimited
POP Config:
    Ports: 110 
    POP Memcap: 838860
    MIME Max Mem: 838860
    Base64 Decoding: Enabled
    Base64 Decoding Depth: Unlimited
    Quoted-Printable Decoding: Enabled
    Quoted-Printable Decoding Depth: Unlimited
    Unix-to-Unix Decoding: Enabled
    Unix-to-Unix Decoding Depth: Unlimited
    Non-Encoded MIME attachment Extraction: Enabled
    Non-Encoded MIME attachment Extraction Depth: Unlimited
Modbus config: 
    Ports:
	502
DNP3 config: 
    Memcap: 262144
    Check Link-Layer CRCs: ENABLED
    Ports:
	20000
Reputation config: 
WARNING: Can't find any whitelist/blacklist entries. Reputation Preprocessor disabled.

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
4632 Snort rules read
    4632 detection rules
    0 decoder rules
    0 preprocessor rules
4632 Option Chains linked into 186 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

+-------------------[Rule Port Counts]---------------------------------------
|             tcp     udp    icmp      ip
|     src    1647       7       0       0
|     dst    2414     470       0       0
|     any      91       1       3       0
|      nc      14       0       0       0
|     s+d       1       1       0       0
+----------------------------------------------------------------------------

+-----------------------[detection-filter-config]------------------------------
| memory-cap : 1048576 bytes
+-----------------------[detection-filter-rules]-------------------------------
-------------------------------------------------------------------------------

+-----------------------[rate-filter-config]-----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[rate-filter-rules]------------------------------------
| none
-------------------------------------------------------------------------------

+-----------------------[event-filter-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[event-filter-global]----------------------------------
+-----------------------[event-filter-local]-----------------------------------
| none
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->sdrop->reject->alert->log
Verifying Preprocessor Configurations!
ICMP tracking disabled, no ICMP sessions allocated
IP tracking disabled, no IP sessions allocated
WARNING: flowbits key 'imap.cram_md5' is set but not ever checked.
WARNING: flowbits key 'file.lanman' is set but not ever checked.
WARNING: flowbits key 'file.fon' is set but not ever checked.
WARNING: flowbits key 'file.xfdl' is set but not ever checked.
WARNING: flowbits key 'file.vwr' is set but not ever checked.
WARNING: flowbits key 'kit.blackhole' is set but not ever checked.
WARNING: flowbits key 'file.msi' is set but not ever checked.
WARNING: flowbits key 'file.nab' is set but not ever checked.
WARNING: flowbits key 'hplogin' is set but not ever checked.
WARNING: flowbits key 'file.fpx' is set but not ever checked.
WARNING: flowbits key 'file.ram' is checked but not ever set.
WARNING: flowbits key 'file.xps' is set but not ever checked.
WARNING: flowbits key 'file.hhk' is set but not ever checked.
WARNING: flowbits key 'file.xwd' is set but not ever checked.
WARNING: flowbits key 'file.wri' is set but not ever checked.
WARNING: flowbits key 'cocsoft.stream' is set but not ever checked.
123 out of 1024 flowbits in use.

[ Port Based Pattern Matching Memory ]
+- [ Aho-Corasick Summary ] -------------------------------------
| Storage Format    : Full-Q 
| Finite Automaton  : DFA
| Alphabet Size     : 256 Chars
| Sizeof State      : Variable (1,2,4 bytes)
| Instances         : 153
|     1 byte states : 143
|     2 byte states : 10
|     4 byte states : 0
| Characters        : 84014
| States            : 64606
| Transitions       : 6797841
| State Density     : 41.1%
| Patterns          : 4661
| Match States      : 5184
| Memory (MB)       : 32.29
|   Patterns        : 0.37
|   Match Lists     : 0.61
|   DFA
|     1 byte states : 0.90
|     2 byte states : 30.25
|     4 byte states : 0.00
+----------------------------------------------------------------
[ Number of patterns truncated to 20 bytes: 295 ]
pcap DAQ configured to passive.
Acquiring network traffic from "eth1".
Set gid to 1001
Set uid to 1001

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.9.6.0 GRE (Build 47) 
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/snort/snort-team
           Copyright (C) 2014 Cisco and/or its affiliates. All rights reserved.
           Copyright (C) 1998-2013 Sourcefire, Inc., et al.
           Using libpcap version 1.4.0
           Using PCRE version: 8.31 2012-07-06
           Using ZLIB version: 1.2.8

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 2.1  <Build 1>
           Rules Object: web-misc  Version 1.0  <Build 1>
           Rules Object: smtp  Version 1.0  <Build 1>
           Rules Object: exploit  Version 1.0  <Build 1>
           Rules Object: dos  Version 1.0  <Build 1>
           Rules Object: nntp  Version 1.0  <Build 1>
           Rules Object: imap  Version 1.0  <Build 1>
           Rules Object: specific-threats  Version 1.0  <Build 1>
           Rules Object: chat  Version 1.0  <Build 1>
           Rules Object: netbios  Version 1.0  <Build 1>
           Rules Object: web-client  Version 1.0  <Build 1>
           Rules Object: icmp  Version 1.0  <Build 1>
           Rules Object: p2p  Version 1.0  <Build 1>
           Rules Object: snmp  Version 1.0  <Build 1>
           Rules Object: multimedia  Version 1.0  <Build 1>
           Rules Object: web-iis  Version 1.0  <Build 1>
           Rules Object: bad-traffic  Version 1.0  <Build 1>
           Rules Object: web-activex  Version 1.0  <Build 1>
           Rules Object: misc  Version 1.0  <Build 1>
           Preprocessor Object: SF_POP  Version 1.0  <Build 1>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 9>
           Preprocessor Object: SF_REPUTATION  Version 1.1  <Build 1>
           Preprocessor Object: SF_SIP  Version 1.1  <Build 1>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 4>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 3>
           Preprocessor Object: SF_SDF  Version 1.1  <Build 1>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 3>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 13>
           Preprocessor Object: SF_DNP3  Version 1.1  <Build 1>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 4>
           Preprocessor Object: SF_IMAP  Version 1.0  <Build 1>
           Preprocessor Object: SF_GTP  Version 1.1  <Build 1>
           Preprocessor Object: SF_MODBUS  Version 1.1  <Build 1>

Snort successfully validated the configuration!
Snort exiting
```

And so I removed Snort so that it wouldn't run as a daemon during startup, and ran it using this command instead:

```
sudo /usr/local/snort/bin/snort -dev -l /var/log/snort -b -u snort -g snort -c /usr/local/snort/etc/snort.conf -i eth1
```

Which resulted in this:

```
So I edited out what you suggested and ran snort, and when I ran it around 10.47 am, it displayed this:

=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

05/22-10:49:13.435375 00:26:18:8B:75:8C -> FF:FF:FF:FF:FF:FF type:0x800 len:0x5C
192.168.2.1:137 -> 192.168.2.127:137 UDP TTL:128 TOS:0x0 ID:1389 IpLen:20 DgmLen:78
Len: 50
E2 2B 01 10 00 01 00 00 00 00 00 00 20 45 42 46  .+.......... EBF
47 45 42 46 45 45 42 46 43 46 44 43 4F 45 47 46  GEBFEEBFCFDCOEGF
4A 46 43 45 46 43 4F 45 44 45 50 41 41 00 00 20  JFCEFCOEDEPAA.. 
00 01                                            ..

=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

05/22-10:49:14.184843 00:26:18:8B:75:8C -> FF:FF:FF:FF:FF:FF type:0x800 len:0x5C
192.168.2.1:137 -> 192.168.2.127:137 UDP TTL:128 TOS:0x0 ID:1390 IpLen:20 DgmLen:78
Len: 50
E2 2B 01 10 00 01 00 00 00 00 00 00 20 45 42 46  .+.......... EBF
47 45 42 46 45 45 42 46 43 46 44 43 4F 45 47 46  GEBFEEBFCFDCOEGF
4A 46 43 45 46 43 4F 45 44 45 50 41 41 00 00 20  JFCEFCOEDEPAA.. 
00 01                                            ..

=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

05/22-10:49:14.935081 00:26:18:8B:75:8C -> FF:FF:FF:FF:FF:FF type:0x800 len:0x5C
192.168.2.1:137 -> 192.168.2.127:137 UDP TTL:128 TOS:0x0 ID:1391 IpLen:20 DgmLen:78
Len: 50
E2 2B 01 10 00 01 00 00 00 00 00 00 20 45 42 46  .+.......... EBF
47 45 42 46 45 45 42 46 43 46 44 43 4F 45 47 46  GEBFEEBFCFDCOEGF
4A 46 43 45 46 43 4F 45 44 45 50 41 41 00 00 20  JFCEFCOEDEPAA.. 
00 01                                            ..

=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

^C*** Caught Int-Signal
===============================================================================
Run time for packet processing was 142.18442 seconds
Snort processed 9531 packets.
Snort ran for 0 days 0 hours 2 minutes 22 seconds
   Pkts/min:         4765
   Pkts/sec:           67
===============================================================================
Memory usage summary:
  Total non-mmapped bytes (arena):       106119168
  Bytes in mapped regions (hblkhd):      6868992
  Total allocated space (uordblks):      56650088
  Total free space (fordblks):           49469080
  Topmost releasable block (keepcost):   57496
===============================================================================
Packet I/O Totals:
   Received:       218750
   Analyzed:         9531 (  4.357%)
    Dropped:       209219 ( 48.886%)
   Filtered:            0 (  0.000%)
Outstanding:       209219 ( 95.643%)
   Injected:            0
===============================================================================
Breakdown by protocol (includes rebuilt packets):
        Eth:         9554 (100.000%)
       VLAN:            0 (  0.000%)
        IP4:         9529 ( 99.738%)
       Frag:            0 (  0.000%)
       ICMP:           34 (  0.356%)
        UDP:         3900 ( 40.821%)
        TCP:         5595 ( 58.562%)
        IP6:           23 (  0.241%)
    IP6 Ext:           23 (  0.241%)
   IP6 Opts:            0 (  0.000%)
      Frag6:            0 (  0.000%)
      ICMP6:            0 (  0.000%)
       UDP6:           23 (  0.241%)
       TCP6:            0 (  0.000%)
     Teredo:            0 (  0.000%)
    ICMP-IP:            0 (  0.000%)
    IP4/IP4:            0 (  0.000%)
    IP4/IP6:            0 (  0.000%)
    IP6/IP4:            0 (  0.000%)
    IP6/IP6:            0 (  0.000%)
        GRE:            0 (  0.000%)
    GRE Eth:            0 (  0.000%)
   GRE VLAN:            0 (  0.000%)
    GRE IP4:            0 (  0.000%)
    GRE IP6:            0 (  0.000%)
GRE IP6 Ext:            0 (  0.000%)
   GRE PPTP:            0 (  0.000%)
    GRE ARP:            0 (  0.000%)
    GRE IPX:            0 (  0.000%)
   GRE Loop:            0 (  0.000%)
       MPLS:            0 (  0.000%)
        ARP:            2 (  0.021%)
        IPX:            0 (  0.000%)
   Eth Loop:            0 (  0.000%)
   Eth Disc:            0 (  0.000%)
   IP4 Disc:            0 (  0.000%)
   IP6 Disc:            0 (  0.000%)
   TCP Disc:            0 (  0.000%)
   UDP Disc:            0 (  0.000%)
  ICMP Disc:            0 (  0.000%)
All Discard:            0 (  0.000%)
      Other:            0 (  0.000%)
Bad Chk Sum:            0 (  0.000%)
    Bad TTL:            0 (  0.000%)
     S5 G 1:            0 (  0.000%)
     S5 G 2:           23 (  0.241%)
      Total:         9554
===============================================================================
Action Stats:
     Alerts:            0 (  0.000%)
     Logged:            0 (  0.000%)
     Passed:            0 (  0.000%)
Limits:
      Match:            0
      Queue:            0
        Log:            0
      Event:            0
      Alert:            0
Verdicts:
      Allow:         9531 (  4.357%)
      Block:            0 (  0.000%)
    Replace:            0 (  0.000%)
  Whitelist:            0 (  0.000%)
  Blacklist:            0 (  0.000%)
     Ignore:            0 (  0.000%)
===============================================================================
Frag3 statistics:
        Total Fragments: 0
      Frags Reassembled: 0
               Discards: 0
          Memory Faults: 0
               Timeouts: 0
               Overlaps: 0
              Anomalies: 0
                 Alerts: 0
                  Drops: 0
     FragTrackers Added: 0
    FragTrackers Dumped: 0
FragTrackers Auto Freed: 0
    Frag Nodes Inserted: 0
     Frag Nodes Deleted: 0
===============================================================================
Stream5 statistics:
            Total sessions: 843
              TCP sessions: 828
              UDP sessions: 15
             ICMP sessions: 0
               IP sessions: 0
                TCP Prunes: 0
                UDP Prunes: 0
               ICMP Prunes: 0
                 IP Prunes: 0
TCP StreamTrackers Created: 836
TCP StreamTrackers Deleted: 836
              TCP Timeouts: 0
              TCP Overlaps: 0
       TCP Segments Queued: 2029
     TCP Segments Released: 2029
       TCP Rebuilt Packets: 319
         TCP Segments Used: 1964
              TCP Discards: 29
                  TCP Gaps: 190
      UDP Sessions Created: 15
      UDP Sessions Deleted: 15
              UDP Timeouts: 0
              UDP Discards: 0
                    Events: 54
           Internal Events: 0
           TCP Port Filter
                  Filtered: 0
                 Inspected: 0
                   Tracked: 5572
           UDP Port Filter
                  Filtered: 0
                 Inspected: 48
                   Tracked: 15
===============================================================================
HTTP Inspect - encodings (Note: stream-reassembled packets included):
    POST methods:                         0         
    GET methods:                          6         
    HTTP Request Headers extracted:       17        
    HTTP Request Cookies extracted:       0         
    Post parameters extracted:            0         
    HTTP response Headers extracted:      29        
    HTTP Response Cookies extracted:      0         
    Unicode:                              0         
    Double unicode:                       0         
    Non-ASCII representable:              0         
    Directory traversals:                 0         
    Extra slashes ("//"):                 0         
    Self-referencing paths ("./"):        0         
    HTTP Response Gzip packets extracted: 0         
    Gzip Compressed Data Processed:       n/a       
    Gzip Decompressed Data Processed:     n/a       
    Total packets processed:              2396      
===============================================================================
SMTP Preprocessor Statistics
  Total sessions                                    : 0
  Max concurrent sessions                           : 0
===============================================================================
dcerpc2 Preprocessor Statistics
  Total sessions: 10

  Transports
    SMB
      Total sessions: 10
      Packet stats
        Packets: 65
        Ignored bytes: 18
        Maximum outstanding requests: 1
        SMB command requests/responses processed
          Tree Disconnect (0x71) : 3/3
          Negotiate (0x72) : 9/9
          Session Setup AndX (0x73) : 9/9
          Logoff AndX (0x74) : 5/5
          Tree Connect AndX (0x75) : 3/3
          Nt Create AndX (0xA2) : 3/3
===============================================================================
===============================================================================
SIP Preprocessor Statistics
  Total sessions: 0
===============================================================================
Reputation Preprocessor Statistics
  Total Memory Allocated: 0
===============================================================================
Snort exiting


```

Which resulted in Snort not being able to log the attack, instead, it didn't even create a log entry like it's supposed to, like when I typed this command:

```
ls -l /var/log/snort
```
```

-rw------- 1 snort snort 0 Mei  18 22:27 snort.u2.1400423234
-rw------- 1 snort snort 0 Mei  20 00:32 snort.u2.1400517178
-rw------- 1 snort snort 0 Mei  22 10:30 snort.u2.1400725851
```

Snort was only able to record data only on the 20th and 22nd, but it didn't capture an data on any tests ran on
the 21st. And it was only able to record the data today's data around 10.30 am with the command:
```

sudo /usr/local/snort/bin/snort -u snort -g snort \
-c /usr/local/snort/etc/snort.conf -i eth1
```

And here's the snort.conf file

```
#--------------------------------------------------
#   VRT Rule Packages Snort.conf
#
#   For more information visit us at:
#     http://www.snort.org                   Snort Website
#     http://vrt-blog.snort.org/    Sourcefire VRT Blog
#
#     Mailing list Contact:      snort-sigs@lists.sourceforge.net
#     False Positive reports:    fp@sourcefire.com
#     Snort bugs:                bugs@snort.org
#
#     Compatible with Snort Versions:
#     VERSIONS : 2.9.6.0
#
#     Snort build options:
#     OPTIONS : --enable-gre --enable-mpls --enable-targetbased --enable-ppm --enable-perfprofiling --enable-zlib --enable-active-response --enable-normalizer --enable-reload --enable-react --enable-flexresp3
#
#     Additional information:
#     This configuration file enables active response, to run snort in
#     test mode -T you are required to supply an interface -i <interface>
#     or test mode will fail to fully validate the configuration and
#     exit with a FATAL error
#--------------------------------------------------

###################################################
# This file contains a sample snort configuration. 
# You should take the following steps to create your own custom configuration:
#
#  1) Set the network variables.
#  2) Configure the decoder
#  3) Configure the base detection engine
#  4) Configure dynamic loaded libraries
#  5) Configure preprocessors
#  6) Configure output plugins
#  7) Customize your rule set
#  8) Customize preprocessor and decoder rule set
#  9) Customize shared object rule set
###################################################

###################################################
# Step #1: Set the network variables.  For more information, see README.variables
###################################################

# Setup the network addresses you are protecting
ipvar HOME_NET any

# Set up the external network addresses. Leave as "any" in most situations
ipvar EXTERNAL_NET any

# List of DNS servers on your network 
ipvar DNS_SERVERS $HOME_NET

# List of SMTP servers on your network
ipvar SMTP_SERVERS $HOME_NET

# List of web servers on your network
ipvar HTTP_SERVERS $HOME_NET

# List of sql servers on your network 
ipvar SQL_SERVERS $HOME_NET

# List of telnet servers on your network
ipvar TELNET_SERVERS $HOME_NET

# List of ssh servers on your network
ipvar SSH_SERVERS $HOME_NET

# List of ftp servers on your network
ipvar FTP_SERVERS $HOME_NET

# List of sip servers on your network
ipvar SIP_SERVERS $HOME_NET

# List of ports you run web servers on
portvar HTTP_PORTS [36,80,81,82,83,84,85,86,87,88,89,90,311,383,555,591,593,631,801,808,818,901,972,1158,1220,1414,1533,1741,1830,2231,2301,2381,2809,3029,3037,3057,3128,3443,3702,4000,4343,4848,5117,5250,6080,6173,6988,7000,7001,7071,7144,7145,7510,7770,7777,7779,8000,8008,8014,8028,8080,8081,8082,8085,8088,8090,8118,8123,8180,8181,8222,8243,8280,8300,8500,8509,8800,8888,8899,9000,9060,9080,9090,9091,9111,9443,9999,10000,11371,12601,15489,29991,33300,34412,34443,34444,41080,44449,50000,50002,51423,53331,55252,55555,56712] 

# List of ports you want to look for SHELLCODE on.
portvar SHELLCODE_PORTS !80

# List of ports you might see oracle attacks on
portvar ORACLE_PORTS 1024:

# List of ports you want to look for SSH connections on:
portvar SSH_PORTS 22

# List of ports you run ftp servers on
portvar FTP_PORTS [21,2100,3535]

# List of ports you run SIP servers on
portvar SIP_PORTS [5060,5061,5600]

# List of file data ports for file inspection
portvar FILE_DATA_PORTS [$HTTP_PORTS,110,143]

# List of GTP ports for GTP preprocessor
portvar GTP_PORTS [2123,2152,3386]

# other variables, these should not be modified
ipvar AIM_SERVERS [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9.0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24]

# Path to your rules files (this can be a relative path)
# Note for Windows users:  You are advised to make this an absolute path,
# such as:  c:\snort\rules
var RULE_PATH ../rules
var SO_RULE_PATH ../so_rules
var PREPROC_RULE_PATH ../preproc_rules

# If you are using reputation preprocessor set these
var WHITE_LIST_PATH /usr/local/snort/rules
var BLACK_LIST_PATH /usr/local/snort/rules

###################################################
# Step #2: Configure the decoder.  For more information, see README.decode
###################################################

# Stop generic decode events:
config disable_decode_alerts

# Stop Alerts on experimental TCP options
config disable_tcpopt_experimental_alerts

# Stop Alerts on obsolete TCP options
config disable_tcpopt_obsolete_alerts

# Stop Alerts on T/TCP alerts
config disable_tcpopt_ttcp_alerts

# Stop Alerts on all other TCPOption type events:
config disable_tcpopt_alerts

# Stop Alerts on invalid ip options
config disable_ipopt_alerts

# Alert if value in length field (IP, TCP, UDP) is greater th elength of the packet
# config enable_decode_oversized_alerts

# Same as above, but drop packet if in Inline mode (requires enable_decode_oversized_alerts)
# config enable_decode_oversized_drops

# Configure IP / TCP checksum mode
config checksum_mode: all

# Configure maximum number of flowbit references.  For more information, see README.flowbits
# config flowbits_size: 64

# Configure ports to ignore 
# config ignore_ports: tcp 21 6667:6671 1356
# config ignore_ports: udp 1:17 53

# Configure active response for non inline operation. For more information, see REAMDE.active
# config response: eth0 attempts 2

# Configure DAQ related options for inline operation. For more information, see README.daq
#
# config daq: <type>
# config daq_dir: <dir>
# config daq_mode: <mode>
# config daq_var: <var>
#
# <type> ::= pcap | afpacket | dump | nfq | ipq | ipfw
# <mode> ::= read-file | passive | inline
# <var> ::= arbitrary <name>=<value passed to DAQ
# <dir> ::= path as to where to look for DAQ module so's

# Configure specific UID and GID to run snort as after dropping privs. For more information see snort -h command line options
#
# config set_gid:
# config set_uid:

# Configure default snaplen. Snort defaults to MTU of in use interface. For more information see README
#
# config snaplen:
#

# Configure default bpf_file to use for filtering what traffic reaches snort. For more information see snort -h command line options (-F)
#
# config bpf_file:
#

# Configure default log directory for snort to log to.  For more information see snort -h command line options (-l)
#
# config logdir:


###################################################
# Step #3: Configure the base detection engine.  For more information, see  README.decode
###################################################

# Configure PCRE match limitations
config pcre_match_limit: 3500
config pcre_match_limit_recursion: 1500

# Configure the detection engine  See the Snort Manual, Configuring Snort - Includes - Config
config detection: search-method ac-split search-optimize max-pattern-len 20

# Configure the event queue.  For more information, see README.event_queue
config event_queue: max_queue 8 log 5 order_events content_length

###################################################
## Configure GTP if it is to be used.
## For more information, see README.GTP
####################################################

# config enable_gtp

###################################################
# Per packet and rule latency enforcement
# For more information see README.ppm
###################################################

# Per Packet latency configuration
#config ppm: max-pkt-time 250, \
#   fastpath-expensive-packets, \
#   pkt-log

# Per Rule latency configuration
#config ppm: max-rule-time 200, \
#   threshold 3, \
#   suspend-expensive-rules, \
#   suspend-timeout 20, \
#   rule-log alert

###################################################
# Configure Perf Profiling for debugging
# For more information see README.PerfProfiling
###################################################

#config profile_rules: print all, sort avg_ticks
#config profile_preprocs: print all, sort avg_ticks

###################################################
# Configure protocol aware flushing
# For more information see README.stream5
###################################################
config paf_max: 16000

###################################################
# Step #4: Configure dynamic loaded libraries.  
# For more information, see Snort Manual, Configuring Snort - Dynamic Modules
###################################################

# path to dynamic preprocessor libraries
dynamicpreprocessor directory /usr/local/snort/lib/snort_dynamicpreprocessor/

# path to base preprocessor engine
dynamicengine /usr/local/snort/lib/snort_dynamicengine/libsf_engine.so

# path to dynamic rules libraries
dynamicdetection directory /usr/local/snort/lib/snort_dynamicrules

###################################################
# Step #5: Configure preprocessors
# For more information, see the Snort Manual, Configuring Snort - Preprocessors
###################################################

# GTP Control Channle Preprocessor. For more information, see README.GTP
# preprocessor gtp: ports { 2123 3386 2152 }

# Inline packet normalization. For more information, see README.normalize
# Does nothing in IDS mode
preprocessor normalize_ip4
preprocessor normalize_tcp: ips ecn stream
preprocessor normalize_icmp4
preprocessor normalize_ip6
preprocessor normalize_icmp6

# Target-based IP defragmentation.  For more inforation, see README.frag3
preprocessor frag3_global: max_frags 65536
preprocessor frag3_engine: policy windows detect_anomalies overlap_limit 10 min_fragment_length 100 timeout 180

# Target-Based stateful inspection/stream reassembly.  For more inforation, see README.stream5
preprocessor stream5_global: track_tcp yes, \
   track_udp yes, \
   track_icmp no, \ 
   max_tcp 262144, \
   max_udp 131072, \
   max_active_responses 2, \
   min_response_seconds 5
preprocessor stream5_tcp: policy windows, detect_anomalies, require_3whs 180, \
   overlap_limit 10, small_segments 3 bytes 150, timeout 180, \
    ports client 21 22 23 25 42 53 70 79 109 110 111 113 119 135 136 137 139 143 \
        161 445 513 514 587 593 691 1433 1521 1741 2100 3306 6070 6665 6666 6667 6668 6669 \
        7000 8181 32770 32771 32772 32773 32774 32775 32776 32777 32778 32779, \
    ports both 36 80 81 82 83 84 85 86 87 88 89 90 110 311 383 443 465 563 555 591 593 631 636 801 808 818 901 972 989 992 993 994 995 1158 1220 1414 1533 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7907 7000 7001 7071 7144 7145 7510 7802 7770 7777 7779 \
        7801 7900 7901 7902 7903 7904 7905 7906 7908 7909 7910 7911 7912 7913 7914 7915 7916 \
        7917 7918 7919 7920 8000 8008 8014 8028 8080 8081 8082 8085 8088 8090 8118 8123 8180 8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090 9091 9111 9443 9999 10000 11371 12601 15489 29991 33300 34412 34443 34444 41080 44449 50000 50002 51423 53331 55252 55555 56712
preprocessor stream5_udp: timeout 180

# performance statistics.  For more information, see the Snort Manual, Configuring Snort - Preprocessors - Performance Monitor
# preprocessor perfmonitor: time 300 file /var/snort/snort.stats pktcnt 10000

# HTTP normalization and anomaly detection.  For more information, see README.http_inspect
preprocessor http_inspect: global iis_unicode_map unicode.map 1252 compress_depth 65535 decompress_depth 65535
preprocessor http_inspect_server: server default \
    http_methods { GET POST PUT SEARCH MKCOL COPY MOVE LOCK UNLOCK NOTIFY POLL BCOPY BDELETE BMOVE LINK UNLINK OPTIONS HEAD DELETE TRACE TRACK CONNECT SOURCE SUBSCRIBE UNSUBSCRIBE PROPFIND PROPPATCH BPROPFIND BPROPPATCH RPC_CONNECT PROXY_SUCCESS BITS_POST CCM_POST SMS_POST RPC_IN_DATA RPC_OUT_DATA RPC_ECHO_DATA } \
    chunk_length 500000 \
    server_flow_depth 0 \
    client_flow_depth 0 \
    post_depth 65495 \
    oversize_dir_length 500 \
    max_header_length 750 \
    max_headers 100 \
    max_spaces 200 \
    small_chunk_length { 10 5 } \
    ports { 36 80 81 82 83 84 85 86 87 88 89 90 311 383 555 591 593 631 801 808 818 901 972 1158 1220 1414 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7000 7001 7071 7144 7145 7510 7770 7777 7779 8000 8008 8014 8028 8080 8081 8082 8085 8088 8090 8118 8123 8180 8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090 9091 9111 9443 9999 10000 11371 12601 15489 29991 33300 34412 34443 34444 41080 44449 50000 50002 51423 53331 55252 55555 56712 } \
    non_rfc_char { 0x00 0x01 0x02 0x03 0x04 0x05 0x06 0x07 } \
    enable_cookie \
    extended_response_inspection \
    inspect_gzip \
    normalize_utf \
    unlimited_decompress \
    normalize_javascript \
    apache_whitespace no \
    ascii no \
    bare_byte no \
    directory no \
    double_decode no \
    iis_backslash no \
    iis_delimiter no \
    iis_unicode no \
    multi_slash no \
    utf_8 no \
    u_encode yes \
    webroot no

# ONC-RPC normalization and anomaly detection.  For more information, see the Snort Manual, Configuring Snort - Preprocessors - RPC Decode
preprocessor rpc_decode: 111 32770 32771 32772 32773 32774 32775 32776 32777 32778 32779 no_alert_multiple_requests no_alert_large_fragments no_alert_incomplete

# Back Orifice detection.
preprocessor bo

# FTP / Telnet normalization and anomaly detection.  For more information, see README.ftptelnet
preprocessor ftp_telnet: global inspection_type stateful encrypted_traffic no check_encrypted
preprocessor ftp_telnet_protocol: telnet \
    ayt_attack_thresh 20 \
    normalize ports { 23 } \
    detect_anomalies
preprocessor ftp_telnet_protocol: ftp server default \
    def_max_param_len 100 \
    ports { 21 2100 3535 } \
    telnet_cmds yes \
    ignore_telnet_erase_cmds yes \
    ftp_cmds { ABOR ACCT ADAT ALLO APPE AUTH CCC CDUP } \
    ftp_cmds { CEL CLNT CMD CONF CWD DELE ENC EPRT } \
    ftp_cmds { EPSV ESTA ESTP FEAT HELP LANG LIST LPRT } \
    ftp_cmds { LPSV MACB MAIL MDTM MIC MKD MLSD MLST } \
    ftp_cmds { MODE NLST NOOP OPTS PASS PASV PBSZ PORT } \
    ftp_cmds { PROT PWD QUIT REIN REST RETR RMD RNFR } \
    ftp_cmds { RNTO SDUP SITE SIZE SMNT STAT STOR STOU } \
    ftp_cmds { STRU SYST TEST TYPE USER XCUP XCRC XCWD } \
    ftp_cmds { XMAS XMD5 XMKD XPWD XRCP XRMD XRSQ XSEM } \
    ftp_cmds { XSEN XSHA1 XSHA256 } \
    alt_max_param_len 0 { ABOR CCC CDUP ESTA FEAT LPSV NOOP PASV PWD QUIT REIN STOU SYST XCUP XPWD } \
    alt_max_param_len 200 { ALLO APPE CMD HELP NLST RETR RNFR STOR STOU XMKD } \
    alt_max_param_len 256 { CWD RNTO } \
    alt_max_param_len 400 { PORT } \
    alt_max_param_len 512 { SIZE } \
    chk_str_fmt { ACCT ADAT ALLO APPE AUTH CEL CLNT CMD } \
    chk_str_fmt { CONF CWD DELE ENC EPRT EPSV ESTP HELP } \
    chk_str_fmt { LANG LIST LPRT MACB MAIL MDTM MIC MKD } \
    chk_str_fmt { MLSD MLST MODE NLST OPTS PASS PBSZ PORT } \
    chk_str_fmt { PROT REST RETR RMD RNFR RNTO SDUP SITE } \
    chk_str_fmt { SIZE SMNT STAT STOR STRU TEST TYPE USER } \
    chk_str_fmt { XCRC XCWD XMAS XMD5 XMKD XRCP XRMD XRSQ } \ 
    chk_str_fmt { XSEM XSEN XSHA1 XSHA256 } \
    cmd_validity ALLO < int [ char R int ] > \    
    cmd_validity EPSV < [ { char 12 | char A char L char L } ] > \
    cmd_validity MACB < string > \
    cmd_validity MDTM < [ date nnnnnnnnnnnnnn[.n[n[n]]] ] string > \
    cmd_validity MODE < char ASBCZ > \
    cmd_validity PORT < host_port > \
    cmd_validity PROT < char CSEP > \
    cmd_validity STRU < char FRPO [ string ] > \    
    cmd_validity TYPE < { char AE [ char NTC ] | char I | char L [ number ] } >
preprocessor ftp_telnet_protocol: ftp client default \
    max_resp_len 256 \
    bounce yes \
    ignore_telnet_erase_cmds yes \
    telnet_cmds yes


# SMTP normalization and anomaly detection.  For more information, see README.SMTP
preprocessor smtp: ports { 25 465 587 691 } \
    inspection_type stateful \
    b64_decode_depth 0 \
    qp_decode_depth 0 \
    bitenc_decode_depth 0 \
    uu_decode_depth 0 \
    log_mailfrom \
    log_rcptto \
    log_filename \
    log_email_hdrs \
    normalize cmds \
    normalize_cmds { ATRN AUTH BDAT CHUNKING DATA DEBUG EHLO EMAL ESAM ESND ESOM ETRN EVFY } \
    normalize_cmds { EXPN HELO HELP IDENT MAIL NOOP ONEX QUEU QUIT RCPT RSET SAML SEND SOML } \
    normalize_cmds { STARTTLS TICK TIME TURN TURNME VERB VRFY X-ADAT X-DRCP X-ERCP X-EXCH50 } \
    normalize_cmds { X-EXPS X-LINK2STATE XADR XAUTH XCIR XEXCH50 XGEN XLICENSE XQUE XSTA XTRN XUSR } \
    max_command_line_len 512 \
    max_header_line_len 1000 \
    max_response_line_len 512 \
    alt_max_command_line_len 260 { MAIL } \
    alt_max_command_line_len 300 { RCPT } \
    alt_max_command_line_len 500 { HELP HELO ETRN EHLO } \
    alt_max_command_line_len 255 { EXPN VRFY ATRN SIZE BDAT DEBUG EMAL ESAM ESND ESOM EVFY IDENT NOOP RSET } \
    alt_max_command_line_len 246 { SEND SAML SOML AUTH TURN ETRN DATA RSET QUIT ONEX QUEU STARTTLS TICK TIME TURNME VERB X-EXPS X-LINK2STATE XADR XAUTH XCIR XEXCH50 XGEN XLICENSE XQUE XSTA XTRN XUSR } \
    valid_cmds { ATRN AUTH BDAT CHUNKING DATA DEBUG EHLO EMAL ESAM ESND ESOM ETRN EVFY } \ 
    valid_cmds { EXPN HELO HELP IDENT MAIL NOOP ONEX QUEU QUIT RCPT RSET SAML SEND SOML } \
    valid_cmds { STARTTLS TICK TIME TURN TURNME VERB VRFY X-ADAT X-DRCP X-ERCP X-EXCH50 } \
    valid_cmds { X-EXPS X-LINK2STATE XADR XAUTH XCIR XEXCH50 XGEN XLICENSE XQUE XSTA XTRN XUSR } \
    xlink2state { enabled }

# Portscan detection.  For more information, see README.sfportscan
# preprocessor sfportscan: proto  { all } memcap { 10000000 } sense_level { low }

# ARP spoof detection.  For more information, see the Snort Manual - Configuring Snort - Preprocessors - ARP Spoof Preprocessor
# preprocessor arpspoof
# preprocessor arpspoof_detect_host: 192.168.40.1 f0:0f:00:f0:0f:00

# SSH anomaly detection.  For more information, see README.ssh
preprocessor ssh: server_ports { 22 } \
                  autodetect \
                  max_client_bytes 19600 \
                  max_encrypted_packets 20 \
                  max_server_version_len 100 \
                  enable_respoverflow enable_ssh1crc32 \
                  enable_srvoverflow enable_protomismatch

# SMB / DCE-RPC normalization and anomaly detection.  For more information, see README.dcerpc2
preprocessor dcerpc2: memcap 102400, events [co ]
preprocessor dcerpc2_server: default, policy WinXP, \
    detect [smb [139,445], tcp 135, udp 135, rpc-over-http-server 593], \
    autodetect [tcp 1025:, udp 1025:, rpc-over-http-server 1025:], \
    smb_max_chain 3, smb_invalid_shares ["C$", "D$", "ADMIN$"]

# DNS anomaly detection.  For more information, see README.dns
preprocessor dns: ports { 53 } enable_rdata_overflow

# SSL anomaly detection and traffic bypass.  For more information, see README.ssl
preprocessor ssl: ports { 443 465 563 636 989 992 993 994 995 7801 7802 7900 7901 7902 7903 7904 7905 7906 7907 7908 7909 7910 7911 7912 7913 7914 7915 7916 7917 7918 7919 7920 }, trustservers, noinspect_encrypted

# SDF sensitive data preprocessor.  For more information see README.sensitive_data
preprocessor sensitive_data: alert_threshold 25

# SIP Session Initiation Protocol preprocessor.  For more information see README.sip
preprocessor sip: max_sessions 40000, \
   ports { 5060 5061 5600 }, \
   methods { invite \
             cancel \
             ack \
             bye \
             register \
             options \
             refer \
             subscribe \
             update \
             join \
             info \
             message \
             notify \
             benotify \
             do \
             qauth \
             sprack \
             publish \
             service \
             unsubscribe \
             prack }, \
   max_uri_len 512, \
   max_call_id_len 80, \
   max_requestName_len 20, \
   max_from_len 256, \
   max_to_len 256, \
   max_via_len 1024, \
   max_contact_len 512, \
   max_content_len 2048 

# IMAP preprocessor.  For more information see README.imap
preprocessor imap: \
   ports { 143 } \
   b64_decode_depth 0 \
   qp_decode_depth 0 \
   bitenc_decode_depth 0 \
   uu_decode_depth 0

# POP preprocessor. For more information see README.pop
preprocessor pop: \
   ports { 110 } \
   b64_decode_depth 0 \
   qp_decode_depth 0 \
   bitenc_decode_depth 0 \
   uu_decode_depth 0

# Modbus preprocessor. For more information see README.modbus
preprocessor modbus: ports { 502 }

# DNP3 preprocessor. For more information see README.dnp3
preprocessor dnp3: ports { 20000 } \
   memcap 262144 \
   check_crc

# Reputation preprocessor. For more information see README.reputation
preprocessor reputation: \
   memcap 500, \
   priority whitelist, \
   nested_ip inner, \
   whitelist $WHITE_LIST_PATH/white_list.rules, \
   blacklist $BLACK_LIST_PATH/black_list.rules 

###################################################
# Step #6: Configure output plugins
# For more information, see Snort Manual, Configuring Snort - Output Modules
###################################################

# unified2 
# Recommended for most installs
# output unified2: filename merged.log, limit 128, nostamp, mpls_event_types, vlan_event_types
output unified2: filename snort.u2, limit 128
# Additional configuration for specific types of installs
output alert_unified2: filename snort.alert, limit 128, nostamp
output log_unified2: filename snort.log, limit 128, nostamp 

# syslog
output alert_syslog: LOG_AUTH LOG_ALERT

# pcap
output log_tcpdump: tcpdump.log

# metadata reference data.  do not modify these lines
include classification.config
include reference.config


###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
include $RULE_PATH/local.rules

include $RULE_PATH/app-detect.rules
include $RULE_PATH/attack-responses.rules
include $RULE_PATH/backdoor.rules
include $RULE_PATH/bad-traffic.rules
include $RULE_PATH/blacklist.rules
include $RULE_PATH/botnet-cnc.rules
include $RULE_PATH/browser-chrome.rules
include $RULE_PATH/browser-firefox.rules
include $RULE_PATH/browser-ie.rules
include $RULE_PATH/browser-other.rules
include $RULE_PATH/browser-plugins.rules
include $RULE_PATH/browser-webkit.rules
include $RULE_PATH/chat.rules
include $RULE_PATH/content-replace.rules
include $RULE_PATH/ddos.rules
include $RULE_PATH/dns.rules
include $RULE_PATH/dos.rules
include $RULE_PATH/experimental.rules
include $RULE_PATH/exploit-kit.rules
include $RULE_PATH/exploit.rules
include $RULE_PATH/file-executable.rules
include $RULE_PATH/file-flash.rules
include $RULE_PATH/file-identify.rules
include $RULE_PATH/file-image.rules
include $RULE_PATH/file-java.rules
include $RULE_PATH/file-multimedia.rules
include $RULE_PATH/file-office.rules
include $RULE_PATH/file-other.rules
include $RULE_PATH/file-pdf.rules
include $RULE_PATH/finger.rules
include $RULE_PATH/ftp.rules
include $RULE_PATH/icmp-info.rules
include $RULE_PATH/icmp.rules
include $RULE_PATH/imap.rules
include $RULE_PATH/indicator-compromise.rules
include $RULE_PATH/indicator-obfuscation.rules
include $RULE_PATH/indicator-scan.rules
include $RULE_PATH/indicator-shellcode.rules
include $RULE_PATH/info.rules
include $RULE_PATH/malware-backdoor.rules
include $RULE_PATH/malware-cnc.rules
include $RULE_PATH/malware-other.rules
include $RULE_PATH/malware-tools.rules
include $RULE_PATH/misc.rules
include $RULE_PATH/multimedia.rules
include $RULE_PATH/mysql.rules
include $RULE_PATH/netbios.rules
include $RULE_PATH/nntp.rules
include $RULE_PATH/oracle.rules
include $RULE_PATH/os-linux.rules
include $RULE_PATH/os-mobile.rules
include $RULE_PATH/os-other.rules
include $RULE_PATH/os-solaris.rules
include $RULE_PATH/os-windows.rules
include $RULE_PATH/other-ids.rules
include $RULE_PATH/p2p.rules
include $RULE_PATH/phishing-spam.rules
include $RULE_PATH/policy-multimedia.rules
include $RULE_PATH/policy-other.rules
include $RULE_PATH/policy.rules
include $RULE_PATH/policy-social.rules
include $RULE_PATH/policy-spam.rules
include $RULE_PATH/pop2.rules
include $RULE_PATH/pop3.rules
include $RULE_PATH/protocol-dns.rules
include $RULE_PATH/protocol-finger.rules
include $RULE_PATH/protocol-ftp.rules
include $RULE_PATH/protocol-icmp.rules
include $RULE_PATH/protocol-imap.rules
include $RULE_PATH/protocol-nntp.rules
include $RULE_PATH/protocol-pop.rules
include $RULE_PATH/protocol-rpc.rules
include $RULE_PATH/protocol-scada.rules
include $RULE_PATH/protocol-services.rules
include $RULE_PATH/protocol-snmp.rules
include $RULE_PATH/protocol-telnet.rules
include $RULE_PATH/protocol-tftp.rules
include $RULE_PATH/protocol-voip.rules
include $RULE_PATH/pua-adware.rules
include $RULE_PATH/pua-other.rules
include $RULE_PATH/pua-p2p.rules
include $RULE_PATH/pua-toolbars.rules
include $RULE_PATH/rpc.rules
include $RULE_PATH/rservices.rules
include $RULE_PATH/scada.rules
include $RULE_PATH/scan.rules
include $RULE_PATH/server-apache.rules
include $RULE_PATH/server-iis.rules
include $RULE_PATH/server-mail.rules
include $RULE_PATH/server-mssql.rules
include $RULE_PATH/server-mysql.rules
include $RULE_PATH/server-oracle.rules
include $RULE_PATH/server-other.rules
include $RULE_PATH/server-samba.rules
include $RULE_PATH/server-webapp.rules
include $RULE_PATH/shellcode.rules
include $RULE_PATH/smtp.rules
include $RULE_PATH/snmp.rules
include $RULE_PATH/specific-threats.rules
include $RULE_PATH/spyware-put.rules
include $RULE_PATH/sql.rules
include $RULE_PATH/telnet.rules
include $RULE_PATH/tftp.rules
include $RULE_PATH/virus.rules
include $RULE_PATH/voip.rules
include $RULE_PATH/web-activex.rules
include $RULE_PATH/web-attacks.rules
include $RULE_PATH/web-cgi.rules
include $RULE_PATH/web-client.rules
include $RULE_PATH/web-coldfusion.rules
include $RULE_PATH/web-frontpage.rules
include $RULE_PATH/web-iis.rules
include $RULE_PATH/web-misc.rules
include $RULE_PATH/web-php.rules
include $RULE_PATH/x11.rules

###################################################
# Step #8: Customize your preprocessor and decoder alerts
# For more information, see README.decoder_preproc_rules
###################################################

# decoder and preprocessor event rules
# include $PREPROC_RULE_PATH/preprocessor.rules
# include $PREPROC_RULE_PATH/decoder.rules
# include $PREPROC_RULE_PATH/sensitive-data.rules

###################################################
# Step #9: Customize your Shared Object Snort Rules
# For more information, see http://vrt-blog.snort.org/2009/01/using-vrt-certified-shared-object-rules.html
###################################################

# dynamic library rules
# include $SO_RULE_PATH/bad-traffic.rules
# include $SO_RULE_PATH/chat.rules
# include $SO_RULE_PATH/dos.rules
# include $SO_RULE_PATH/exploit.rules
# include $SO_RULE_PATH/icmp.rules
# include $SO_RULE_PATH/imap.rules
# include $SO_RULE_PATH/misc.rules
# include $SO_RULE_PATH/multimedia.rules
# include $SO_RULE_PATH/netbios.rules
# include $SO_RULE_PATH/nntp.rules
# include $SO_RULE_PATH/p2p.rules
# include $SO_RULE_PATH/smtp.rules
# include $SO_RULE_PATH/snmp.rules
# include $SO_RULE_PATH/specific-threats.rules
# include $SO_RULE_PATH/web-activex.rules
# include $SO_RULE_PATH/web-client.rules
# include $SO_RULE_PATH/web-iis.rules
# include $SO_RULE_PATH/web-misc.rules

# Event thresholding or suppression commands. See threshold.conf 
include threshold.conf

```

---

### Post by Danger_Monkey on 2014-05-22
I had a similar issue.  I'm using a tap connected to the cable just inside my router, connected to eth1.   I can see ALL traffic coming into my network, but I wasn't getting any logs.  I discovered that in my threshold.conf file, on of my suppression's had changed, and was blocking attacks from getting logged.  You might want to comment out any that you have in there, and restart Snort.
Also, if you aren't using DNP3, you might want to comment it out, it uses quite a bit of ram for no reason:

```

# DNP3 preprocessor. For more information see README.dnp3
preprocessor dnp3: ports { 20000 } \
   memcap 262144 \
   check_crc

```

To test attacks, uncomment the sfportscan perprocessor, set the parameters (like the logfile), and scan the machine with NMAP to see what results you get.

```

preprocessor sfportscan: proto  { all } memcap { 100000000 } sense_level { low } scan_type { decoy_portscan }  watch_ip { XXXXXXXX/24,CCCCCCC/24 } ignore_scanners { XXXXXXXXX/24 } ignore_scanned { XXXXXXXXX/24 } logfile { /var/log/snort/ps.log }

nmap -A <ipaddress>

```

Then check the logfile you defined.

---

### Post by hdry on 2014-05-24
Thanks for your suggestion, I'll try it out.

Also, I noticed this while I ran snort on test mode and I noticed this:

```
pcap DAQ configured to passive.
Acquiring network traffic from "eth1".
ERROR: Cannot set gid: 1001
Fatal Error, Quitting..


```

Does this mean anything?

---

### Post by hdry on 2014-05-24
> **Danger_Monkey said:**
> I had a similar issue.  I'm using a tap connected to the cable just inside my router, connected to eth1.   I can see ALL traffic coming into my network, but I wasn't getting any logs.  I discovered that in my threshold.conf file, on of my suppression's had changed, and was blocking attacks from getting logged.  You might want to comment out any that you have in there, and restart Snort.
Also, if you aren't using DNP3, you might want to comment it out, it uses quite a bit of ram for no reason:

```

# DNP3 preprocessor. For more information see README.dnp3
preprocessor dnp3: ports { 20000 } \
   memcap 262144 \
   check_crc

```

To test attacks, uncomment the sfportscan perprocessor, set the parameters (like the logfile), and scan the machine with NMAP to see what results you get.

```

preprocessor sfportscan: proto  { all } memcap { 100000000 } sense_level { low } scan_type { decoy_portscan }  watch_ip { XXXXXXXX/24,CCCCCCC/24 } ignore_scanners { XXXXXXXXX/24 } ignore_scanned { XXXXXXXXX/24 } logfile { /var/log/snort/ps.log }

nmap -A <ipaddress>

```

Then check the logfile you defined.

Well, this might seem like a really stupid question, but what do I need to comment out in the threshold.conf file? I looked into it and I'm not sure what I need to do, actually.

Here's my threshold.conf file, and it appears everything's been edited out:

```
# Configure Thresholding and Suppression
# ======================================
#
# The threshold command is deprecated.  Use detection_filter for thresholds
# within a rule and event_filter for standalone threshold configurations.
# Please see README.filters for more information on filters.
#
# Thresholding:
#
# This feature is used to reduce the number of logged alerts for noisy rules.
# This can be tuned to significantly reduce false alarms, and it can also be
# used to write a newer breed of rules. Thresholding commands limit the number
# of times a particular event is logged during a specified time interval.
#
# There are 3 types of event_filters:
#
# 1) Limit
#    Alert on the 1st M events during the time interval, then ignore
#    events for the rest of the time interval.
#
# 2) Threshold
#    Alert every M times we see this event during the time interval.
#
# 3) Both
#    Alert once per time interval after seeing M occurrences of the
#    event, then ignore any additional events during the time interval.
#
# Threshold commands are formatted as:
#
# event_filter gen_id gen-id, sig_id sig-id, \
#     type limit|threshold|both, track by_src|by_dst, \
#     count n , seconds m
#
# Limit to logging 1 event per 60 seconds:
#
# event_filter gen_id 1, sig_id 1851, type limit, \
#     track by_src, count 1, seconds 60
#
# Global Threshold - Limit to logging 1 event per 60 seconds per IP triggering
# each rule (rules are gen_id 1):
#
# event_filter gen_id 1, sig_id 0, type limit, track by_src, count 1, seconds 60
#
# Global Threshold - Limit to logging 1 event per 60 seconds per IP triggering
# any alert for any event generator:
#
# event_filter gen_id 0, sig_id 0, type limit, track by_src, count 1, seconds 60
#
# Suppression:
#
# Suppression commands are standalone commands that reference generators and
# sids and IP addresses via a CIDR block (or IP list). This allows a rule to be
# completely suppressed, or suppressed when the causitive traffic is going to
# or comming from a specific IP or group of IP addresses.
#
# Suppress this event completely:
#
# suppress gen_id 1, sig_id 1852
#
# Suppress this event from this IP:
#
# suppress gen_id 1, sig_id 1852, track by_src, ip 10.1.1.54
#
# Suppress this event to this CIDR block:
#
# suppress gen_id 1, sig_id 1852, track by_dst, ip 10.1.1.0/24
#

# Global event filter to limit events from a unique src to 1 in 60 seconds
# Disabled by default turn on if you want this functionality
#

# event_filter gen_id 0, sig_id 0, type limit, track by_src, count 1, seconds 60

```

---

### Post by hdry on 2014-05-26
Alright, I'm still stuck with the same problem.

What I did yesterday was to reinstall everything again, and tried to find if there are any solutions. So I found this [solution,]("http://ubuntuforums.org/showthread.php?t=2090342") while it didn't really help me all the way, did provide me with some pointers.

So, first off, I edited my snort.conf file again, and the changes made are bolded out:

```
#--------------------------------------------------
#   VRT Rule Packages Snort.conf
#
#   For more information visit us at:
#     http://www.snort.org                   Snort Website
#     http://vrt-blog.snort.org/    Sourcefire VRT Blog
#
#     Mailing list Contact:      snort-sigs@lists.sourceforge.net
#     False Positive reports:    fp@sourcefire.com
#     Snort bugs:                bugs@snort.org
#
#     Compatible with Snort Versions:
#     VERSIONS : 2.9.6.0
#
#     Snort build options:
#     OPTIONS : --enable-gre --enable-mpls --enable-targetbased --enable-ppm --enable-perfprofiling --enable-zlib --enable-active-response --enable-normalizer --enable-reload --enable-react --enable-flexresp3
#
#     Additional information:
#     This configuration file enables active response, to run snort in
#     test mode -T you are required to supply an interface -i <interface>
#     or test mode will fail to fully validate the configuration and
#     exit with a FATAL error
#--------------------------------------------------

###################################################
# This file contains a sample snort configuration. 
# You should take the following steps to create your own custom configuration:
#
#  1) Set the network variables.
#  2) Configure the decoder
#  3) Configure the base detection engine
#  4) Configure dynamic loaded libraries
#  5) Configure preprocessors
#  6) Configure output plugins
#  7) Customize your rule set
#  8) Customize preprocessor and decoder rule set
#  9) Customize shared object rule set
###################################################

###################################################
# Step #1: Set the network variables.  For more information, see README.variables
###################################################

[B]# Setup the network addresses you are protecting
var HOME_NET any

# Set up the external network addresses. Leave as "any" in most situations
var EXTERNAL_NET any

# List of DNS servers on your network 
var DNS_SERVERS $HOME_NET

# List of SMTP servers on your network
var SMTP_SERVERS $HOME_NET

# List of web servers on your network
var HTTP_SERVERS $HOME_NET

# List of sql servers on your network 
var SQL_SERVERS $HOME_NET

# List of telnet servers on your network
var TELNET_SERVERS $HOME_NET

# List of ssh servers on your network
var SSH_SERVERS $HOME_NET

# List of ftp servers on your network
var FTP_SERVERS $HOME_NET

# List of sip servers on your network
var SIP_SERVERS $HOME_NET[/B]

# List of ports you run web servers on
portvar HTTP_PORTS [36,80,81,82,83,84,85,86,87,88,89,90,311,383,555,591,593,631,801,808,818,901,972,1158,1220,1414,1533,1741,1830,2231,2301,2381,2809,3029,3037,3057,3128,3443,3702,4000,4343,4848,5117,5250,6080,6173,6988,7000,7001,7071,7144,7145,7510,7770,7777,7779,8000,8008,8014,8028,8080,8081,8082,8085,8088,8090,8118,8123,8180,8181,8222,8243,8280,8300,8500,8509,8800,8888,8899,9000,9060,9080,9090,9091,9111,9443,9999,10000,11371,12601,15489,29991,33300,34412,34443,34444,41080,44449,50000,50002,51423,53331,55252,55555,56712] 

# List of ports you want to look for SHELLCODE on.
portvar SHELLCODE_PORTS !80

# List of ports you might see oracle attacks on
portvar ORACLE_PORTS 1024:

# List of ports you want to look for SSH connections on:
portvar SSH_PORTS 22

# List of ports you run ftp servers on
portvar FTP_PORTS [21,2100,3535]

# List of ports you run SIP servers on
portvar SIP_PORTS [5060,5061,5600]

# List of file data ports for file inspection
portvar FILE_DATA_PORTS [$HTTP_PORTS,110,143]

# List of GTP ports for GTP preprocessor
portvar GTP_PORTS [2123,2152,3386]

# other variables, these should not be modified
ipvar AIM_SERVERS [64.12.24.0/23,64.12.28.0/23,64.12.161.0/24,64.12.163.0/24,64.12.200.0/24,205.188.3.0/24,205.188.5.0/24,205.188.7.0/24,205.188.9.0/24,205.188.153.0/24,205.188.179.0/24,205.188.248.0/24]

# Path to your rules files (this can be a relative path)
# Note for Windows users:  You are advised to make this an absolute path,
# such as:  c:\snort\rules
var RULE_PATH ../rules
var SO_RULE_PATH ../so_rules
var PREPROC_RULE_PATH ../preproc_rules

# If you are using reputation preprocessor set these
[B]var WHITE_LIST_PATH /usr/local/snort/rules
var BLACK_LIST_PATH /usr/local/snort/rules
[/B]
###################################################
# Step #2: Configure the decoder.  For more information, see README.decode
###################################################

# Stop generic decode events:
config disable_decode_alerts

# Stop Alerts on experimental TCP options
config disable_tcpopt_experimental_alerts

# Stop Alerts on obsolete TCP options
config disable_tcpopt_obsolete_alerts

# Stop Alerts on T/TCP alerts
config disable_tcpopt_ttcp_alerts

# Stop Alerts on all other TCPOption type events:
config disable_tcpopt_alerts

# Stop Alerts on invalid ip options
config disable_ipopt_alerts

# Alert if value in length field (IP, TCP, UDP) is greater th elength of the packet
# config enable_decode_oversized_alerts

# Same as above, but drop packet if in Inline mode (requires enable_decode_oversized_alerts)
# config enable_decode_oversized_drops

# Configure IP / TCP checksum mode
config checksum_mode: all

# Configure maximum number of flowbit references.  For more information, see README.flowbits
# config flowbits_size: 64

# Configure ports to ignore 
# config ignore_ports: tcp 21 6667:6671 1356
# config ignore_ports: udp 1:17 53

# Configure active response for non inline operation. For more information, see REAMDE.active
# config response: eth0 attempts 2

# Configure DAQ related options for inline operation. For more information, see README.daq
#
# config daq: <type>
# config daq_dir: <dir>
# config daq_mode: <mode>
# config daq_var: <var>
#
# <type> ::= pcap | afpacket | dump | nfq | ipq | ipfw
# <mode> ::= read-file | passive | inline
# <var> ::= arbitrary <name>=<value passed to DAQ
# <dir> ::= path as to where to look for DAQ module so's

# Configure specific UID and GID to run snort as after dropping privs. For more information see snort -h command line options
#
# config set_gid:
# config set_uid:

# Configure default snaplen. Snort defaults to MTU of in use interface. For more information see README
#
# config snaplen:
#

# Configure default bpf_file to use for filtering what traffic reaches snort. For more information see snort -h command line options (-F)
#
# config bpf_file:
#

# Configure default log directory for snort to log to.  For more information see snort -h command line options (-l)
#
# config logdir:


###################################################
# Step #3: Configure the base detection engine.  For more information, see  README.decode
###################################################

# Configure PCRE match limitations
config pcre_match_limit: 3500
config pcre_match_limit_recursion: 1500

# Configure the detection engine  See the Snort Manual, Configuring Snort - Includes - Config
config detection: search-method ac-split search-optimize max-pattern-len 20

# Configure the event queue.  For more information, see README.event_queue
config event_queue: max_queue 8 log 5 order_events content_length

###################################################
## Configure GTP if it is to be used.
## For more information, see README.GTP
####################################################

# config enable_gtp

###################################################
# Per packet and rule latency enforcement
# For more information see README.ppm
###################################################

# Per Packet latency configuration
#config ppm: max-pkt-time 250, \
#   fastpath-expensive-packets, \
#   pkt-log

# Per Rule latency configuration
#config ppm: max-rule-time 200, \
#   threshold 3, \
#   suspend-expensive-rules, \
#   suspend-timeout 20, \
#   rule-log alert

###################################################
# Configure Perf Profiling for debugging
# For more information see README.PerfProfiling
###################################################

#config profile_rules: print all, sort avg_ticks
#config profile_preprocs: print all, sort avg_ticks

###################################################
# Configure protocol aware flushing
# For more information see README.stream5
###################################################
config paf_max: 16000

###################################################
# Step #4: Configure dynamic loaded libraries.  
# For more information, see Snort Manual, Configuring Snort - Dynamic Modules
###################################################

[B]# path to dynamic preprocessor libraries
dynamicpreprocessor directory /usr/local/snort/lib/snort_dynamicpreprocessor/

# path to base preprocessor engine
dynamicengine /usr/local/snort/lib/snort_dynamicengine/libsf_engine.so

# path to dynamic rules libraries
dynamicdetection directory /usr/local/snort/lib/snort_dynamicrules
[/B]
###################################################
# Step #5: Configure preprocessors
# For more information, see the Snort Manual, Configuring Snort - Preprocessors
###################################################

# GTP Control Channle Preprocessor. For more information, see README.GTP
# preprocessor gtp: ports { 2123 3386 2152 }

# Inline packet normalization. For more information, see README.normalize
# Does nothing in IDS mode
preprocessor normalize_ip4
preprocessor normalize_tcp: ips ecn stream
preprocessor normalize_icmp4
preprocessor normalize_ip6
preprocessor normalize_icmp6

# Target-based IP defragmentation.  For more inforation, see README.frag3
preprocessor frag3_global: max_frags 65536
preprocessor frag3_engine: policy windows detect_anomalies overlap_limit 10 min_fragment_length 100 timeout 180

# Target-Based stateful inspection/stream reassembly.  For more inforation, see README.stream5
preprocessor stream5_global: track_tcp yes, \
   track_udp yes, \
   track_icmp no, \ 
   max_tcp 262144, \
   max_udp 131072, \
   max_active_responses 2, \
   min_response_seconds 5
preprocessor stream5_tcp: policy windows, detect_anomalies, require_3whs 180, \
   overlap_limit 10, small_segments 3 bytes 150, timeout 180, \
    ports client 21 22 23 25 42 53 70 79 109 110 111 113 119 135 136 137 139 143 \
        161 445 513 514 587 593 691 1433 1521 1741 2100 3306 6070 6665 6666 6667 6668 6669 \
        7000 8181 32770 32771 32772 32773 32774 32775 32776 32777 32778 32779, \
    ports both 36 80 81 82 83 84 85 86 87 88 89 90 110 311 383 443 465 563 555 591 593 631 636 801 808 818 901 972 989 992 993 994 995 1158 1220 1414 1533 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7907 7000 7001 7071 7144 7145 7510 7802 7770 7777 7779 \
        7801 7900 7901 7902 7903 7904 7905 7906 7908 7909 7910 7911 7912 7913 7914 7915 7916 \
        7917 7918 7919 7920 8000 8008 8014 8028 8080 8081 8082 8085 8088 8090 8118 8123 8180 8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090 9091 9111 9443 9999 10000 11371 12601 15489 29991 33300 34412 34443 34444 41080 44449 50000 50002 51423 53331 55252 55555 56712
preprocessor stream5_udp: timeout 180

# performance statistics.  For more information, see the Snort Manual, Configuring Snort - Preprocessors - Performance Monitor
# preprocessor perfmonitor: time 300 file /var/snort/snort.stats pktcnt 10000

# HTTP normalization and anomaly detection.  For more information, see README.http_inspect
preprocessor http_inspect: global iis_unicode_map unicode.map 1252 compress_depth 65535 decompress_depth 65535
preprocessor http_inspect_server: server default \
    http_methods { GET POST PUT SEARCH MKCOL COPY MOVE LOCK UNLOCK NOTIFY POLL BCOPY BDELETE BMOVE LINK UNLINK OPTIONS HEAD DELETE TRACE TRACK CONNECT SOURCE SUBSCRIBE UNSUBSCRIBE PROPFIND PROPPATCH BPROPFIND BPROPPATCH RPC_CONNECT PROXY_SUCCESS BITS_POST CCM_POST SMS_POST RPC_IN_DATA RPC_OUT_DATA RPC_ECHO_DATA } \
    chunk_length 500000 \
    server_flow_depth 0 \
    client_flow_depth 0 \
    post_depth 65495 \
    oversize_dir_length 500 \
    max_header_length 750 \
    max_headers 100 \
    max_spaces 200 \
    small_chunk_length { 10 5 } \
    ports { 36 80 81 82 83 84 85 86 87 88 89 90 311 383 555 591 593 631 801 808 818 901 972 1158 1220 1414 1741 1830 2231 2301 2381 2809 3029 3037 3057 3128 3443 3702 4000 4343 4848 5117 5250 6080 6173 6988 7000 7001 7071 7144 7145 7510 7770 7777 7779 8000 8008 8014 8028 8080 8081 8082 8085 8088 8090 8118 8123 8180 8181 8222 8243 8280 8300 8500 8509 8800 8888 8899 9000 9060 9080 9090 9091 9111 9443 9999 10000 11371 12601 15489 29991 33300 34412 34443 34444 41080 44449 50000 50002 51423 53331 55252 55555 56712 } \
    non_rfc_char { 0x00 0x01 0x02 0x03 0x04 0x05 0x06 0x07 } \
    enable_cookie \
    extended_response_inspection \
    inspect_gzip \
    normalize_utf \
    unlimited_decompress \
    normalize_javascript \
    apache_whitespace no \
    ascii no \
    bare_byte no \
    directory no \
    double_decode no \
    iis_backslash no \
    iis_delimiter no \
    iis_unicode no \
    multi_slash no \
    utf_8 no \
    u_encode yes \
    webroot no

# ONC-RPC normalization and anomaly detection.  For more information, see the Snort Manual, Configuring Snort - Preprocessors - RPC Decode
preprocessor rpc_decode: 111 32770 32771 32772 32773 32774 32775 32776 32777 32778 32779 no_alert_multiple_requests no_alert_large_fragments no_alert_incomplete

# Back Orifice detection.
preprocessor bo

# FTP / Telnet normalization and anomaly detection.  For more information, see README.ftptelnet
preprocessor ftp_telnet: global inspection_type stateful encrypted_traffic no check_encrypted
preprocessor ftp_telnet_protocol: telnet \
    ayt_attack_thresh 20 \
    normalize ports { 23 } \
    detect_anomalies
preprocessor ftp_telnet_protocol: ftp server default \
    def_max_param_len 100 \
    ports { 21 2100 3535 } \
    telnet_cmds yes \
    ignore_telnet_erase_cmds yes \
    ftp_cmds { ABOR ACCT ADAT ALLO APPE AUTH CCC CDUP } \
    ftp_cmds { CEL CLNT CMD CONF CWD DELE ENC EPRT } \
    ftp_cmds { EPSV ESTA ESTP FEAT HELP LANG LIST LPRT } \
    ftp_cmds { LPSV MACB MAIL MDTM MIC MKD MLSD MLST } \
    ftp_cmds { MODE NLST NOOP OPTS PASS PASV PBSZ PORT } \
    ftp_cmds { PROT PWD QUIT REIN REST RETR RMD RNFR } \
    ftp_cmds { RNTO SDUP SITE SIZE SMNT STAT STOR STOU } \
    ftp_cmds { STRU SYST TEST TYPE USER XCUP XCRC XCWD } \
    ftp_cmds { XMAS XMD5 XMKD XPWD XRCP XRMD XRSQ XSEM } \
    ftp_cmds { XSEN XSHA1 XSHA256 } \
    alt_max_param_len 0 { ABOR CCC CDUP ESTA FEAT LPSV NOOP PASV PWD QUIT REIN STOU SYST XCUP XPWD } \
    alt_max_param_len 200 { ALLO APPE CMD HELP NLST RETR RNFR STOR STOU XMKD } \
    alt_max_param_len 256 { CWD RNTO } \
    alt_max_param_len 400 { PORT } \
    alt_max_param_len 512 { SIZE } \
    chk_str_fmt { ACCT ADAT ALLO APPE AUTH CEL CLNT CMD } \
    chk_str_fmt { CONF CWD DELE ENC EPRT EPSV ESTP HELP } \
    chk_str_fmt { LANG LIST LPRT MACB MAIL MDTM MIC MKD } \
    chk_str_fmt { MLSD MLST MODE NLST OPTS PASS PBSZ PORT } \
    chk_str_fmt { PROT REST RETR RMD RNFR RNTO SDUP SITE } \
    chk_str_fmt { SIZE SMNT STAT STOR STRU TEST TYPE USER } \
    chk_str_fmt { XCRC XCWD XMAS XMD5 XMKD XRCP XRMD XRSQ } \ 
    chk_str_fmt { XSEM XSEN XSHA1 XSHA256 } \
    cmd_validity ALLO < int [ char R int ] > \    
    cmd_validity EPSV < [ { char 12 | char A char L char L } ] > \
    cmd_validity MACB < string > \
    cmd_validity MDTM < [ date nnnnnnnnnnnnnn[.n[n[n]]] ] string > \
    cmd_validity MODE < char ASBCZ > \
    cmd_validity PORT < host_port > \
    cmd_validity PROT < char CSEP > \
    cmd_validity STRU < char FRPO [ string ] > \    
    cmd_validity TYPE < { char AE [ char NTC ] | char I | char L [ number ] } >
preprocessor ftp_telnet_protocol: ftp client default \
    max_resp_len 256 \
    bounce yes \
    ignore_telnet_erase_cmds yes \
    telnet_cmds yes


# SMTP normalization and anomaly detection.  For more information, see README.SMTP
preprocessor smtp: ports { 25 465 587 691 } \
    inspection_type stateful \
    b64_decode_depth 0 \
    qp_decode_depth 0 \
    bitenc_decode_depth 0 \
    uu_decode_depth 0 \
    log_mailfrom \
    log_rcptto \
    log_filename \
    log_email_hdrs \
    normalize cmds \
    normalize_cmds { ATRN AUTH BDAT CHUNKING DATA DEBUG EHLO EMAL ESAM ESND ESOM ETRN EVFY } \
    normalize_cmds { EXPN HELO HELP IDENT MAIL NOOP ONEX QUEU QUIT RCPT RSET SAML SEND SOML } \
    normalize_cmds { STARTTLS TICK TIME TURN TURNME VERB VRFY X-ADAT X-DRCP X-ERCP X-EXCH50 } \
    normalize_cmds { X-EXPS X-LINK2STATE XADR XAUTH XCIR XEXCH50 XGEN XLICENSE XQUE XSTA XTRN XUSR } \
    max_command_line_len 512 \
    max_header_line_len 1000 \
    max_response_line_len 512 \
    alt_max_command_line_len 260 { MAIL } \
    alt_max_command_line_len 300 { RCPT } \
    alt_max_command_line_len 500 { HELP HELO ETRN EHLO } \
    alt_max_command_line_len 255 { EXPN VRFY ATRN SIZE BDAT DEBUG EMAL ESAM ESND ESOM EVFY IDENT NOOP RSET } \
    alt_max_command_line_len 246 { SEND SAML SOML AUTH TURN ETRN DATA RSET QUIT ONEX QUEU STARTTLS TICK TIME TURNME VERB X-EXPS X-LINK2STATE XADR XAUTH XCIR XEXCH50 XGEN XLICENSE XQUE XSTA XTRN XUSR } \
    valid_cmds { ATRN AUTH BDAT CHUNKING DATA DEBUG EHLO EMAL ESAM ESND ESOM ETRN EVFY } \ 
    valid_cmds { EXPN HELO HELP IDENT MAIL NOOP ONEX QUEU QUIT RCPT RSET SAML SEND SOML } \
    valid_cmds { STARTTLS TICK TIME TURN TURNME VERB VRFY X-ADAT X-DRCP X-ERCP X-EXCH50 } \
    valid_cmds { X-EXPS X-LINK2STATE XADR XAUTH XCIR XEXCH50 XGEN XLICENSE XQUE XSTA XTRN XUSR } \
    xlink2state { enabled }

# Portscan detection.  For more information, see README.sfportscan
# preprocessor sfportscan: proto  { all } memcap { 10000000 } sense_level { low }

# ARP spoof detection.  For more information, see the Snort Manual - Configuring Snort - Preprocessors - ARP Spoof Preprocessor
# preprocessor arpspoof
# preprocessor arpspoof_detect_host: 192.168.40.1 f0:0f:00:f0:0f:00

# SSH anomaly detection.  For more information, see README.ssh
preprocessor ssh: server_ports { 22 } \
                  autodetect \
                  max_client_bytes 19600 \
                  max_encrypted_packets 20 \
                  max_server_version_len 100 \
                  enable_respoverflow enable_ssh1crc32 \
                  enable_srvoverflow enable_protomismatch

# SMB / DCE-RPC normalization and anomaly detection.  For more information, see README.dcerpc2
preprocessor dcerpc2: memcap 102400, events [co ]
preprocessor dcerpc2_server: default, policy WinXP, \
    detect [smb [139,445], tcp 135, udp 135, rpc-over-http-server 593], \
    autodetect [tcp 1025:, udp 1025:, rpc-over-http-server 1025:], \
    smb_max_chain 3, smb_invalid_shares ["C$", "D$", "ADMIN$"]

# DNS anomaly detection.  For more information, see README.dns
preprocessor dns: ports { 53 } enable_rdata_overflow

# SSL anomaly detection and traffic bypass.  For more information, see README.ssl
preprocessor ssl: ports { 443 465 563 636 989 992 993 994 995 7801 7802 7900 7901 7902 7903 7904 7905 7906 7907 7908 7909 7910 7911 7912 7913 7914 7915 7916 7917 7918 7919 7920 }, trustservers, noinspect_encrypted

# SDF sensitive data preprocessor.  For more information see README.sensitive_data
preprocessor sensitive_data: alert_threshold 25

# SIP Session Initiation Protocol preprocessor.  For more information see README.sip
preprocessor sip: max_sessions 40000, \
   ports { 5060 5061 5600 }, \
   methods { invite \
             cancel \
             ack \
             bye \
             register \
             options \
             refer \
             subscribe \
             update \
             join \
             info \
             message \
             notify \
             benotify \
             do \
             qauth \
             sprack \
             publish \
             service \
             unsubscribe \
             prack }, \
   max_uri_len 512, \
   max_call_id_len 80, \
   max_requestName_len 20, \
   max_from_len 256, \
   max_to_len 256, \
   max_via_len 1024, \
   max_contact_len 512, \
   max_content_len 2048 

# IMAP preprocessor.  For more information see README.imap
preprocessor imap: \
   ports { 143 } \
   b64_decode_depth 0 \
   qp_decode_depth 0 \
   bitenc_decode_depth 0 \
   uu_decode_depth 0

# POP preprocessor. For more information see README.pop
preprocessor pop: \
   ports { 110 } \
   b64_decode_depth 0 \
   qp_decode_depth 0 \
   bitenc_decode_depth 0 \
   uu_decode_depth 0

# Modbus preprocessor. For more information see README.modbus
preprocessor modbus: ports { 502 }

# DNP3 preprocessor. For more information see README.dnp3
preprocessor dnp3: ports { 20000 } \
   memcap 262144 \
   check_crc

# Reputation preprocessor. For more information see README.reputation
preprocessor reputation: \
   memcap 500, \
   priority whitelist, \
   nested_ip inner, \
   whitelist $WHITE_LIST_PATH/white_list.rules, \
   blacklist $BLACK_LIST_PATH/black_list.rules 

###################################################
# Step #6: Configure output plugins
# For more information, see Snort Manual, Configuring Snort - Output Modules
###################################################

[B]# unified2 
# Recommended for most installs
# output unified2: filename merged.log, limit 128, nostamp, mpls_event_types, vlan_event_types
output unified2: filename snort.u2, limit 128
# Additional configuration for specific types of installs
output alert_unified2: filename snort.alert, limit 128, nostamp
output log_unified2: filename snort.log, limit 128, nostamp 

# syslog
output alert_syslog: LOG_AUTH LOG_ALERT

# pcap
output log_tcpdump: tcpdump.log[/B]

# metadata reference data.  do not modify these lines
include classification.config
include reference.config


###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
include $RULE_PATH/local.rules

include $RULE_PATH/app-detect.rules
include $RULE_PATH/attack-responses.rules
include $RULE_PATH/backdoor.rules
include $RULE_PATH/bad-traffic.rules
include $RULE_PATH/blacklist.rules
include $RULE_PATH/botnet-cnc.rules
include $RULE_PATH/browser-chrome.rules
include $RULE_PATH/browser-firefox.rules
include $RULE_PATH/browser-ie.rules
include $RULE_PATH/browser-other.rules
include $RULE_PATH/browser-plugins.rules
include $RULE_PATH/browser-webkit.rules
include $RULE_PATH/chat.rules
include $RULE_PATH/content-replace.rules
include $RULE_PATH/ddos.rules
include $RULE_PATH/dns.rules
include $RULE_PATH/dos.rules
include $RULE_PATH/experimental.rules
include $RULE_PATH/exploit-kit.rules
include $RULE_PATH/exploit.rules
include $RULE_PATH/file-executable.rules
include $RULE_PATH/file-flash.rules
include $RULE_PATH/file-identify.rules
include $RULE_PATH/file-image.rules
include $RULE_PATH/file-java.rules
include $RULE_PATH/file-multimedia.rules
include $RULE_PATH/file-office.rules
include $RULE_PATH/file-other.rules
include $RULE_PATH/file-pdf.rules
include $RULE_PATH/finger.rules
include $RULE_PATH/ftp.rules
include $RULE_PATH/icmp-info.rules
include $RULE_PATH/icmp.rules
include $RULE_PATH/imap.rules
include $RULE_PATH/indicator-compromise.rules
include $RULE_PATH/indicator-obfuscation.rules
include $RULE_PATH/indicator-scan.rules
include $RULE_PATH/indicator-shellcode.rules
include $RULE_PATH/info.rules
include $RULE_PATH/malware-backdoor.rules
include $RULE_PATH/malware-cnc.rules
include $RULE_PATH/malware-other.rules
include $RULE_PATH/malware-tools.rules
include $RULE_PATH/misc.rules
include $RULE_PATH/multimedia.rules
include $RULE_PATH/mysql.rules
include $RULE_PATH/netbios.rules
include $RULE_PATH/nntp.rules
include $RULE_PATH/oracle.rules
include $RULE_PATH/os-linux.rules
include $RULE_PATH/os-mobile.rules
include $RULE_PATH/os-other.rules
include $RULE_PATH/os-solaris.rules
include $RULE_PATH/os-windows.rules
include $RULE_PATH/other-ids.rules
include $RULE_PATH/p2p.rules
include $RULE_PATH/phishing-spam.rules
include $RULE_PATH/policy-multimedia.rules
include $RULE_PATH/policy-other.rules
include $RULE_PATH/policy.rules
include $RULE_PATH/policy-social.rules
include $RULE_PATH/policy-spam.rules
include $RULE_PATH/pop2.rules
include $RULE_PATH/pop3.rules
include $RULE_PATH/protocol-dns.rules
include $RULE_PATH/protocol-finger.rules
include $RULE_PATH/protocol-ftp.rules
include $RULE_PATH/protocol-icmp.rules
include $RULE_PATH/protocol-imap.rules
include $RULE_PATH/protocol-nntp.rules
include $RULE_PATH/protocol-pop.rules
include $RULE_PATH/protocol-rpc.rules
include $RULE_PATH/protocol-scada.rules
include $RULE_PATH/protocol-services.rules
include $RULE_PATH/protocol-snmp.rules
include $RULE_PATH/protocol-telnet.rules
include $RULE_PATH/protocol-tftp.rules
include $RULE_PATH/protocol-voip.rules
include $RULE_PATH/pua-adware.rules
include $RULE_PATH/pua-other.rules
include $RULE_PATH/pua-p2p.rules
include $RULE_PATH/pua-toolbars.rules
include $RULE_PATH/rpc.rules
include $RULE_PATH/rservices.rules
include $RULE_PATH/scada.rules
include $RULE_PATH/scan.rules
include $RULE_PATH/server-apache.rules
include $RULE_PATH/server-iis.rules
include $RULE_PATH/server-mail.rules
include $RULE_PATH/server-mssql.rules
include $RULE_PATH/server-mysql.rules
include $RULE_PATH/server-oracle.rules
include $RULE_PATH/server-other.rules
include $RULE_PATH/server-samba.rules
include $RULE_PATH/server-webapp.rules
include $RULE_PATH/shellcode.rules
include $RULE_PATH/smtp.rules
include $RULE_PATH/snmp.rules
include $RULE_PATH/specific-threats.rules
include $RULE_PATH/spyware-put.rules
include $RULE_PATH/sql.rules
include $RULE_PATH/telnet.rules
include $RULE_PATH/tftp.rules
include $RULE_PATH/virus.rules
include $RULE_PATH/voip.rules
include $RULE_PATH/web-activex.rules
include $RULE_PATH/web-attacks.rules
include $RULE_PATH/web-cgi.rules
include $RULE_PATH/web-client.rules
include $RULE_PATH/web-coldfusion.rules
include $RULE_PATH/web-frontpage.rules
include $RULE_PATH/web-iis.rules
include $RULE_PATH/web-misc.rules
include $RULE_PATH/web-php.rules
include $RULE_PATH/x11.rules

###################################################
# Step #8: Customize your preprocessor and decoder alerts
# For more information, see README.decoder_preproc_rules
###################################################

# decoder and preprocessor event rules
# include $PREPROC_RULE_PATH/preprocessor.rules
# include $PREPROC_RULE_PATH/decoder.rules
# include $PREPROC_RULE_PATH/sensitive-data.rules

###################################################
# Step #9: Customize your Shared Object Snort Rules
# For more information, see http://vrt-blog.snort.org/2009/01/using-vrt-certified-shared-object-rules.html
###################################################

# dynamic library rules
# include $SO_RULE_PATH/bad-traffic.rules
# include $SO_RULE_PATH/chat.rules
# include $SO_RULE_PATH/dos.rules
# include $SO_RULE_PATH/exploit.rules
# include $SO_RULE_PATH/icmp.rules
# include $SO_RULE_PATH/imap.rules
# include $SO_RULE_PATH/misc.rules
# include $SO_RULE_PATH/multimedia.rules
# include $SO_RULE_PATH/netbios.rules
# include $SO_RULE_PATH/nntp.rules
# include $SO_RULE_PATH/p2p.rules
# include $SO_RULE_PATH/smtp.rules
# include $SO_RULE_PATH/snmp.rules
# include $SO_RULE_PATH/specific-threats.rules
# include $SO_RULE_PATH/web-activex.rules
# include $SO_RULE_PATH/web-client.rules
# include $SO_RULE_PATH/web-iis.rules
# include $SO_RULE_PATH/web-misc.rules

# Event thresholding or suppression commands. See threshold.conf 
include threshold.conf

```

as well as the barnyard2.conf file (Changes also shown in bold):

```


[B]config reference_file:      /usr/local/snort/etc/reference.config
config classification_file: /usr/local/snort/etc/classification.config
config gen_file:            /usr/local/snort/etc/gen-msg.map
config sid_file:            /usr/local/snort/etc/sid-msg.map[/B]

[B]config hostname:   localhost
config interface:  eth1[/B]

[B]output database: log, mysql, user=snort password=YOURPASSWORD dbname=snort \
host=localhost[/B]

```

I then changed the ownership of the /usr/local/snort/etc folder, from root to snort, using:

sudo chown -R snort:snort /usr/local/snort/etc, so now the output looks like this:

```
total 4188
-rw-r--r-- 1 snort snort   11666 Mei  25 21:29 barnyard2.conf
-rw-r--r-- 1 snort snort    3854 Mac  20 02:20 classification.config
-rw-r--r-- 1 snort snort   29648 Jan  28 06:16 gen-msg.map
-rw-r--r-- 1 snort snort     746 Mac  20 02:20 reference.config
-rw-r--r-- 1 snort snort 4143089 Mac  20 02:23 sid-msg.map
-rw-r--r-- 1 snort snort   27672 Mei  26 13:23 snort.conf
-rw-r--r-- 1 snort snort    2556 Mac  20 02:20 threshold.conf
-rw-r--r-- 1 snort snort   53841 Mac  20 02:20 unicode.map


```

Then, I tried to change the file permissions of the /var/log/snort folder with ```
chmod o+w /var/log/snort/
``` and then I performed a port scan and a ping attack on the machine, but when I checked it again I received this:

```

drwxr-xrwx 18 root  root  4096 Mei  26 13:32 ..
-rw-------  1 snort snort    0 Mei  26 13:32 tcpdump.log.1401082370
-rw-------  1 snort snort    0 Mei  26 13:32 snort.u2.1401082370
-rw-------  1 snort snort    0 Mei  26 13:32 snort.log
-rw-------  1 snort snort    0 Mei  26 13:32 snort.alert
drwxr-xrwx  2 snort snort 4096 Mei  26 13:32 .


```

Is there anything I might have left out?

---

