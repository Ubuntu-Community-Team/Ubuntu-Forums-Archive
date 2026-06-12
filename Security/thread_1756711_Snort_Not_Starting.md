---
title: "Snort Not Starting"
date: 2011-05-12
forum: Security
---

### Post by Hopping_Ubu on 2011-05-12
I need assistance with my Snort Installation. I used Bodhi Zazen's Network Intrusion Detection System post and found it easier than the previous time I had done it. I am currently running Ubuntu 10.04 server and Snort 2.8.6.1 with BASE 1.4.5. I followed Bodhi Zazen's instructions and when I tested snort it ended with a Fatal Error due to ERROR: /etc/snort/rules/exploit.rules(264) => 'fast_pattern' does not take an argument
Fatal Error, Quitting..

Here is the entire output once I ran the test command: snort -c /etc/snort/snort.con -T
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
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
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
    Number of Nodes:   36900
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
ERROR: /etc/snort/rules/exploit.rules(264) => 'fast_pattern' does not take an argument
Fatal Error, Quitting..

I thought there maybe an issue with the rules and downloaded the rules again and copied it but I still get this problem.

Any assistance that can be provided is greatly appreciated.

Robert

---

### Post by Hopping_Ubu on 2011-05-13
After much research, I found the answer to the problem. By getting the snort package from the Ubuntu archives, I get version 2.8.5.2. When doing it via the apt-get method, I did not see what version was actually being installed. When I used the GUI for Package update, I found the version. When I did the rule update, the lowest revision that is for 2.8.6.1. 

The error that I got was a version mismatch. Snort 2.8.5.2 could not resolve the 2.8.6.1 rules and required an upgrade to Snort. 

Is Ubuntu going to update their archive packages to include a newer version of Snort?

Thanks,

Robert   :)

---

### Post by emiller12345 on 2011-05-13
You should download the source code for snort and install it from scratch. Take a look at: [http://minimalite.com/2011/02/linux/install-snort-2-9-0-4-and-daq-0-5/](http://minimalite.com/2011/02/linux/install-snort-2-9-0-4-and-daq-0-5/)  I haven't use this link personally, but it looks okay as far as the steps go.  Are you making an IDS or an IPS? libdnet I believe is mainly for IPS's...

---

