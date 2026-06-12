---
title: "[SOLVED] snort fail to start"
date: 2008-10-22
forum: Security
---

### Post by remy06 on 2008-10-22
Hi all,

I have followed the article on intrusion detection to install snort and base by bodhi.zazen to try it out.

didnt notice any error throughout the process and it seems to install successfully.

However,after the install I log in to base and base seems to not reporting anything at all(all alerts and traffics are 0%).

I rebooted my pc afterwhich and the startup process indicate this message:

snort fail to start     [failed]

Any assistance pls?
Thanks in advance.

---

### Post by Sarmacid on 2008-10-22
Post the output of
```
/usr/sbin/snort -c /etc/snort/snort.conf
```

---

### Post by remy06 on 2008-10-22
it says:

```
bash: /usr/sbin/snort: No such file or directory
```

do you require the contents of /etc/snort/snort.conf however?

---

### Post by Sarmacid on 2008-10-23
Seems Snort wasn't installed.

What's the output of
```
which snort
```

I followed this howto for Snort [http://ubuntuforums.org/showthread.php?t=483488&highlight=oinkmaster](http://ubuntuforums.org/showthread.php?t=483488&highlight=oinkmaster)

In it Snort is installed with apt, not compiled from source.

*EDIT*

Reading that howto you mentioned, I found out where Snort should be, so run this
```
/usr/local/bin/snort -c /etc/snort/snort.conf
```

---

### Post by remy06 on 2008-10-23
Hi Sarmacid,

here goes the output:

which snort:
```

/usr/local/bin/snort

```

and

/usr/local/bin/snort -c /etc/snort/snort.conf:
```

Snort BPF option: output
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf
PortVar 'HTTP_PORTS' defined :  [ 80 2301 3128 8000 8080 8180 8888 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
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
Stream5 TCP Policy config:
    Reassembly Policy: WINDOWS
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
      465 client (Footprint) 
      513 client (Footprint) 
      691 client (Footprint) 
      1433 client (Footprint) 
      1521 client (Footprint) 
      2100 client (Footprint) 
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
      Ports: 80 2301 3128 8000 8080 8180 8888 
      Server Flow Depth: 1460
      Client Flow Depth: 300
      Max Chunk Length: 500000
      Max Header Field Length: 0
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
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_dcerpc_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_dns_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_ftptelnet_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_smtp_preproc.so... done
Loading dynamic preprocessor library /usr/local/lib/snort_dynamicpreprocessor/libsf_ssh_preproc.so... done
FTPTelnet Config:
    GLOBAL CONFIG
      Inspection Type: stateful
      Check for Encrypted Traffic: YES alert: YES
      Continue to check encrypted data: YES
    TELNET CONFIG:
      Ports: 23 
      Are You There Threshold: 20
      Normalize: YES
      Detect Anomalies: YES
    FTP CONFIG:
      FTP Server: default
        Ports: 21 2100 
        Check for Telnet Cmds: OFF
        Identify open data channels: NO
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: NO
        Max Response Length: 200

SMTP Config:
    Ports: 25 465 691 
    Inspection Type: Stateful
    Normalize: ATRN AUTH BDAT DATA DEBUG EHLO EMAL ESAM ESND ESOM ETRN EVFY EXPN HELO HELP IDENT MAIL NOOP ONEX QUEU QUIT RCPT RSET SAML SEND SIZE STARTTLS SOML TICK TIME TURN TURNME VERB VRFY X-EXPS XADR XAUTH XCIR XEXCH50 XGEN XLICENSE X-LINK2STATE XSTA XTRN XUSR PIPELINING CHUNKING DSN XQUEU 
    Ignore Data: No
    Ignore TLS Data: No
    Ignore SMTP Alerts: No
    Max Command Line Length: Unlimited
    Max Specific Command Line Length: 
       ATRN:255 AUTH:246 BDAT:255 DATA:246 DEBUG:255 
       EHLO:500 EMAL:255 ESAM:255 ESND:255 ESOM:255 
       ETRN:246 EVFY:255 EXPN:255 HELO:500 HELP:500 
       IDENT:255 MAIL:260 NOOP:255 ONEX:246 QUEU:246 
       QUIT:246 RCPT:300 RSET:246 SAML:246 SEND:246 
       SIZE:255 STARTTLS:246 SOML:246 TICK:246 TIME:246 
       TURN:246 TURNME:246 VERB:246 VRFY:255 X-EXPS:246 
       XADR:246 XAUTH:246 XCIR:246 XEXCH50:246 XGEN:246 
       XLICENSE:246 X-LINK2STATE:246 XSTA:246 XTRN:246 XUSR:246 
       PIPELINING:246 CHUNKING:246 DSN:246 XQUEU:246 
    Max Header Line Length: 1000
    Max Response Line Length: 512
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
    Reassembly increment: DISABLED

DNS config: 
    DNS Client rdata txt Overflow Alert: ACTIVE
    Obsolete DNS RR Types Alert: INACTIVE
    Experimental DNS RR Types Alert: INACTIVE
    Ports: 53

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
8935 Snort rules read
    8935 detection rules
    0 decoder rules
    0 preprocessor rules
8935 Option Chains linked into 542 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

+-------------------[Rule Port Counts]---------------------------------------
|             tcp     udp    icmp      ip
|     src    1019      39       0       0
|     dst    6812     441       0       0
|     any     507     119      20       7
|      nc      14       4       3       4
|     s+d      16      16       0       0
+----------------------------------------------------------------------------

+-----------------------[thresholding-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[thresholding-global]----------------------------------
| none
+-----------------------[thresholding-local]-----------------------------------
| gen-id=1      sig-id=8467       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13852      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9655       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6377       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6290       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6336       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6228       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6373       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6189       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5794       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=13856      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12003      type=Both      tracking=src count=10  seconds=5  
| gen-id=1      sig-id=5993       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7587       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7760       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6496       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7567       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13497      type=Limit     tracking=src count=1   seconds=100
| gen-id=1      sig-id=13810      type=Limit     tracking=src count=1   seconds=3500
| gen-id=1      sig-id=13507      type=Limit     tracking=src count=1   seconds=200
| gen-id=1      sig-id=5954       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5824       type=Limit     tracking=src count=1   seconds=60 
| gen-id=1      sig-id=13849      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14085      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=10169      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7572       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13489      type=Limit     tracking=src count=1   seconds=200
| gen-id=1      sig-id=5866       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=12697      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7739       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6250       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7526       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7594       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5943       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13509      type=Limit     tracking=src count=1   seconds=400
| gen-id=1      sig-id=12159      type=Limit     tracking=src count=1   seconds=120
| gen-id=1      sig-id=12759      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6386       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9839       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=12485      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10166      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9648       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8549       type=Limit     tracking=src count=2   seconds=300
| gen-id=1      sig-id=9829       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7551       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6237       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=10094      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13242      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12291      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5897       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10438      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13648      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9652       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7552       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=8544       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=3152       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=10181      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=13942      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5978       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6107       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5973       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=6481       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6374       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6254       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6488       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7533       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=8542       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7539       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10168      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7504       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6341       type=Limit     tracking=src count=1   seconds=60 
| gen-id=1      sig-id=5891       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12481      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6360       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6127       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13499      type=Limit     tracking=src count=1   seconds=100
| gen-id=1      sig-id=10095      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7193       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12679      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7613       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7712       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=11312      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7758       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7570       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12122      type=Limit     tracking=src count=1   seconds=18000
| gen-id=1      sig-id=5917       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10185      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7190       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6213       type=Limit     tracking=src count=1   seconds=1800
| gen-id=1      sig-id=3542       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=5838       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7642       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12295      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12727      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7571       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7523       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6281       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6359       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7624       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5910       type=Limit     tracking=dst count=1   seconds=300
| gen-id=1      sig-id=13940      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6480       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6219       type=Both      tracking=src count=1   seconds=1800
| gen-id=1      sig-id=12126      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6384       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5846       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7839       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10452      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14055      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7144       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6487       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12698      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5971       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=6146       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10440      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6482       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7505       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9657       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7589       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7531       type=Limit     tracking=src count=1   seconds=6000
| gen-id=1      sig-id=6199       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7655       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13341      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6197       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9827       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7557       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5749       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7822       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5926       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5796       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7603       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7706       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5929       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5925       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6398       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9644       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12794      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13812      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12702      type=Limit     tracking=src count=1   seconds=500
| gen-id=1      sig-id=8545       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7732       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12720      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6192       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=11948      type=Limit     tracking=src count=1   seconds=30 
| gen-id=1      sig-id=5939       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5750       type=Limit     tracking=src count=1   seconds=1800
| gen-id=1      sig-id=5950       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5930       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9650       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13651      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7576       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14086      type=Limit     tracking=src count=1   seconds=100
| gen-id=1      sig-id=5903       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12674      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=11952      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12367      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6385       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8464       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13867      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13343      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5835       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7837       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14057      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7524       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6239       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7550       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=3527       type=Limit     tracking=dst count=5   seconds=60 
| gen-id=1      sig-id=5945       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5767       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6196       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5944       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=9663       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7828       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=11317      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5773       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12721      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7802       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5889       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6372       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5899       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=9830       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5896       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13941      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12138      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5932       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5760       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5802       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7581       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7547       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7169       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5890       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13282      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6364       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8358       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14066      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7195       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6223       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5915       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5976       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5922       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5949       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6271       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6203       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=12693      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7569       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6361       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5776       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7848       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=11950      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5828       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12761      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12700      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5980       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6490       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12132      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12134      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12052      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5918       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=4984       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=12002      type=Both      tracking=src count=100 seconds=25 
| gen-id=1      sig-id=5951       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6489       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12294      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5982       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5977       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7139       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10096      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5995       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12121      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6484       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6222       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6363       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=12162      type=Limit     tracking=src count=1   seconds=120
| gen-id=1      sig-id=5986       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5807       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13655      type=Limit     tracking=src count=1   seconds=200
| gen-id=1      sig-id=12365      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8073       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5775       type=Limit     tracking=src count=1   seconds=1800
| gen-id=1      sig-id=5974       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=12224      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=12151      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7593       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7194       type=Limit     tracking=src count=1   seconds=300


| gen-id=1      sig-id=7191       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5940       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7582       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7143       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5927       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=6208       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=7177       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5970       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=5805       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7514       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10441      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7646       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=3543       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=10089      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13936      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7573       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5830       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5996       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5979       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12378      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=11306      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=12369      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5989       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=12678      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7647       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=2923       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=13813      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5914       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10091      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7727       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7141       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5946       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5966       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12482      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7597       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12371      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7050       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12366      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10108      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7532       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7180       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5837       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10088      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6321       type=Limit     tracking=src count=1   seconds=3000
| gen-id=1      sig-id=5801       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7154       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=5975       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5825       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5836       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=13568      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12149      type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=10443      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8360       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13285      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8359       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5831       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=9667       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6241       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5916       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12793      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7759       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6176       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7069       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6494       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=7827       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6206       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7138       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6232       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7832       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5992       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=12791      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=11307      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8071       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6174       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10107      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7055       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10447      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5987       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5852       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5994       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5765       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6365       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5858       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13855      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6275       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7142       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=13558      type=Limit     tracking=src count=1   seconds=50 
| gen-id=1      sig-id=7192       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5832       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7558       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7801       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6200       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6191       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6225       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6198       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10182      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=11951      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12368      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13653      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10180      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5981       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12795      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7525       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5942       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=8468       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5841       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12228      type=Limit     tracking=src count=1   seconds=30 
| gen-id=1      sig-id=6220       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12127      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7511       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7669       type=Limit     tracking=src count=1   seconds=120
| gen-id=1      sig-id=7649       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7691       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5871       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6207       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=11954      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=2523       type=Both      tracking=dst count=10  seconds=10 
| gen-id=1      sig-id=13876      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5829       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5865       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5881       type=Limit     tracking=src count=1   seconds=60 
| gen-id=1      sig-id=8072       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5961       type=Limit     tracking=src count=1   seconds=1800
| gen-id=1      sig-id=6251       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5764       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10446      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6233       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7518       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7562       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7516       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=2275       type=Threshold tracking=dst count=5   seconds=60 
| gen-id=1      sig-id=7515       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5742       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6342       type=Limit     tracking=src count=1   seconds=60 
| gen-id=1      sig-id=10179      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10092      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12486      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5842       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6128       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5803       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14065      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7537       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5867       type=Limit     tracking=src count=1   seconds=900
| gen-id=1      sig-id=7185       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10164      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6252       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7529       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7549       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7074       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7711       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6270       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=14087      type=Limit     tracking=src count=1   seconds=150
| gen-id=1      sig-id=7856       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7829       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=13948      type=Threshold tracking=src count=200 seconds=30 
| gen-id=1      sig-id=10184      type=Both      tracking=src count=3   seconds=300
| gen-id=1      sig-id=7118       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=11311      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6324       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6282       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7527       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5744       type=Limit     tracking=src count=1   seconds=1800
| gen-id=1      sig-id=7535       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=13503      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6358       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5774       type=Limit     tracking=src count=1   seconds=1800
| gen-id=1      sig-id=6212       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6122       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=2924       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=5879       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7534       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5990       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=6209       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5921       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12004      type=Both      tracking=src count=25  seconds=10 
| gen-id=1      sig-id=12137      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6322       type=Limit     tracking=src count=1   seconds=3000
| gen-id=1      sig-id=7140       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=5988       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7559       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=10451      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=10183      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6483       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6478       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7548       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=3273       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=6477       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7522       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7068       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5928       type=Limit     tracking=src count=1   seconds=1200
| gen-id=1      sig-id=12661      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=6343       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=12487      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7575       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5853       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=7563       type=Limit     tracking=src count=1   seconds=600
| gen-id=1      sig-id=13652      type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=5983       type=Limit     tracking=src count=1   seconds=300
| gen-id=1      sig-id=7835       type=Limit     tracking=src count=1   seconds=300
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Verifying Preprocessor Configurations!
Warning: 'ignore_any_rules' option for Stream5 UDP disabled because of UDP rule with flow or flowbits option
Warning: flowbits key 'emf.request' is set but not ever checked.
Warning: flowbits key 'access.download' is set but not ever checked.
Warning: flowbits key 'http.bmp' is checked but not ever set.
Warning: flowbits key 'mssearch_file.request' is set but not ever checked.
Warning: flowbits key 'sylk.download' is set but not ever checked.
Warning: flowbits key 'mspub_header' is set but not ever checked.
Warning: flowbits key 'works.download' is set but not ever checked.
Warning: flowbits key 'vnc.pv.setup' is set but not ever checked.
Warning: flowbits key 'backup_file.request' is set but not ever checked.
369 out of 512 flowbits in use.
ERROR: Failed to lookup for interface: no suitable device found. Please specify one with -i switch
Fatal Error, Quitting..

```

---

### Post by Sarmacid on 2008-10-23
> ERROR: Failed to lookup for interface: no suitable device found. Please specify one with -i switch
Fatal Error, Quitting..
You need to tell Snort wich interface it should listen to. Usually it's eth0 so it would be

```
/usr/local/bin/snort -c /etc/snort/snort.conf -i eth0
```

If that doesn't work, then post the output of

```
ifconfig
```

---

### Post by remy06 on 2008-10-24
after running the command:

Code:

/usr/local/bin/snort -c /etc/snort/snort.conf -i eth0 and br0

both I got this error:
```
ERROR: database: mysql_error: Access denied for user 'snort'@'localhost' (using password: YES)

```

and ifconfig gives me this:
```
br0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.xx.xx  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe94:1e00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40268941 (38.4 MB)  TX bytes:3874898 (3.6 MB)

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: fe80::21a:4dff:fe94:1e00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40948432 (39.0 MB)  TX bytes:4049556 (3.8 MB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105700 (103.2 KB)  TX bytes:105700 (103.2 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:41:1b:bd:f8  
          inet6 addr: fe80::2ff:41ff:fe1b:bdf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:3350 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I forgot to mention I set up the host networking for virtualbox following an article previously thus the br0.So in bodhi.zazen's script i edited and include this following his article:
```
IFACE="br0"
```
Sigh..:confused:

Another thing to check.As for the whitelist part,he mentioned that we may whitelist IP addresses such as our router and our public ip address.But I believe my public ip address is not static.So how do i set it properly to whitelist my network?I have few pcs getting their ips from the router dynamically.

Please advice.Thanks!

---

### Post by Sarmacid on 2008-10-25
You should check again the password you gave Snort to report to mysql. Try```
mysql -u snort -p
```
That will ask for your snort pass, type it. If you manage to get into mysql then check the snort pass in /etc/snort/srnot.conf, if not, you'll have to enter as root and change the pass.

---

### Post by The Tronyx on 2008-10-26
> **remy06 said:**
> I have few pcs getting their ips from the router dynamically.

Please advice.Thanks!

In the above, you list the contents of ifconfig.  It looks like your inetaddr is "192.168.xx.xx."  You would need to whitelist the block that is being handled by your router, i.e. 192.168.0.1/30 or maybe you could do 192.168.0.1 - 192.168.0.254.  I forget the addressing scheme OSSEC respects but you can block a range of IPs.  This should take care of your LAN.

Check out the [OSSEC wiki]("http://www.ossec.net/wiki/index.php/Know_How:White_list") for more info.  Good luck!

---

### Post by remy06 on 2008-10-26
> **Sarmacid said:**
> You should check again the password you gave Snort to report to mysql. Try```
mysql -u snort -p
```
That will ask for your snort pass, type it. If you manage to get into mysql then check the snort pass in /etc/snort/srnot.conf, if not, you'll have to enter as root and change the pass.

hi,
I tried running the above code and got this:
```

ERROR 1045 (28000): Access denied for user 'snort'@'localhost' (using password: YES)

```
I actually wrote down the password i use but doesnt seem to work.

do I change the pass by running this command?
```

sudo passwd mysql
sudo passwd snort

```

I think i messed it up already.How do i uninstall everything and reinstall?

hi 2point0,
Thanks for the link.I will read that up.

---

### Post by The Tronyx on 2008-10-26
You didn't break everything.  You need to reset that user's MySQL password as apparently something with the current one isn't right.

Log into MySQL as root (mysql -u root -p) and type the following:
```

mysql> grant all privileges on snort.* to 'snort'@'localhost' identified by 'RESETPASSWORD';
mysql> flush privileges;
mysql> exit
```

Now, you can even enter that MySQL line exactly as you see it, and then attempt the following command:
```

mysql -u snort -p 
Enter password: (This is where you enter RESETPASSWORD)
```

Does this make sense?  I haven't even made it to my second cup of coffee yet so if I left something out let me know.

---

### Post by remy06 on 2008-10-31
hi 2point0,
Understood,thanks.Im still new to linux and hope to learn various cool stuff here.

after some tries i'm still unable to get it running.Decided to install on virtual machine this time and now it seems to be working finally.geezz..

Thanks guys

---

### Post by remy06 on 2008-11-04
to update my status,i have installed snort and base on my guest ubuntu successfully.Everything works fine.

Now i tried installing on my host but base does not present anything.o% traffic,0 sensors etc.

snort is running and installed as the output of
```
pgrep -l snort
```
returns me the id and snort

In bodhi.zazen's script i've declared the following for my host,
```
IFACE="br0"
```

Is there anything i've done wrong here or any workaround to get it working?

---

### Post by cariboo on 2008-11-04
Shouldn't

> iface br0

be

```
iface eth0
```

If you are using the host computer? Do you connect to the internet via eth0 or br0?

Jim

---

### Post by Sarmacid on 2008-11-05
> **remy06 said:**
> to update my status,i have installed snort and base on my guest ubuntu successfully.Everything works fine.

Now i tried installing on my host but base does not present anything.o% traffic,0 sensors etc.

snort is running and installed as the output of
```
pgrep -l snort
```
returns me the id and snort

In bodhi.zazen's script i've declared the following for my host,
```
IFACE="br0"
```

Is there anything i've done wrong here or any workaround to get it working?

If it doesn't report maybe there's nothing to report. Have you tried doing portscans? or maybe activating the ICMP rules and pinging the ubuntu box?

If starting snort manually shows no errors, that means it is running.

---

### Post by remy06 on 2008-11-05
hi Jim,

I am using my host computer now.It should be br0.This is my ifconfig output after setting up bridging for virtualbox.
```
br0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.xx.xx  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe94:1e00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40268941 (38.4 MB)  TX bytes:3874898 (3.6 MB)

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: fe80::21a:4dff:fe94:1e00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40948432 (39.0 MB)  TX bytes:4049556 (3.8 MB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105700 (103.2 KB)  TX bytes:105700 (103.2 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:41:1b:bd:f8  
          inet6 addr: fe80::2ff:41ff:fe1b:bdf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:3350 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Hi Sarmacid,
I did a port scan using system>administration>network tools on my host address and shows nothing in base.How to activate the ICMP rules by the way?

Im also trying to install vmware server now instead as mentioned by a friend but having problem installing it due to some gcc and kernel version compatibility error.

I thought vmware server may be better since I do not need to set up bridge as I am able to get snort+base running without the bridge.

---

### Post by Sarmacid on 2008-11-06
To activate the icmp rules just open the snort.conf file and go to the lines where the rules are and search for```
# Extremely chatty rules:
# include $RULE_PATH/info.rules
# include $RULE_PATH/icmp-info.rules

```

Remove the # symbol and start snort, and now everytime you get a ping, snort will report it.

---

### Post by remy06 on 2008-11-06
Just tried your suggestion and portscan again but still doesn't seem to work.

Give up for now.Removed the bridge,back to eth0 now and it works...:???:

So I went ahead to install vmware server despite the minor warning,now am able to use their bridge utility together with snort+base.

hope sun can make virtualbox networking easier in their future versions..

thanks so much again.:)

---

### Post by jack8888 on 2009-07-13
There is no process bind to port 5111.  [plus size lingerie]("http://www.pamperedpassions.com/plus_size_lingerie_55_ctg.html") [guitar lesson dvd review]("http://www.bestguitardvds.com") I have changed different ports, but it still having the same  roblem.

---

