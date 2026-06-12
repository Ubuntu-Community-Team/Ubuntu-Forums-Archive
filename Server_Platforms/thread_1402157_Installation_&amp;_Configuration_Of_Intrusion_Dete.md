---
title: "Installation &amp; Configuration Of Intrusion Detection With Snort, ACIDBASE, MySQL"
date: 2010-02-08
forum: Server Platforms
---

### Post by metallica1973 on 2010-02-08
I am in the process of setting up snort on an Ubuntu Server 9.10. I am following this tutorial:

[URL=http://www.howtoforge.com/installation-and-configuration-of-intrusion-detection-with-snort-acidbase-mysql-and-apache2-on-ubuntu-9.04-using-spm[/URL]

when I get to the section when it ask me to test snort and I run the test:

[PHP]sudo snort -c /etc/snort/snort.conf  [/PHP]

I get this error mysql error saying that it is reading another database 'db':

[PHP]sudo snort -c /etc/snort/snort.conf
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
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
    Log info if session memory consumption exceeds 1048576
Stream5 TCP Policy config:
    Reassembly Policy: FIRST
    Timeout: 30 seconds
    Min ttl:  1
    Maximum number of bytes to queue per session: 1048576
    Maximum number of segs to queue per session: 2621
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

Tagged Packet Limit: 256
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
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

+-----------------------[thresholding-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[thresholding-global]----------------------------------
| none
+-----------------------[thresholding-local]-----------------------------------
| gen-id=1      sig-id=100000162  type=Both      tracking=src count=100 seconds=60 
| gen-id=1      sig-id=100000163  type=Both      tracking=src count=100 seconds=60 
| gen-id=1      sig-id=100000161  type=Both      tracking=dst count=100 seconds=60 
| gen-id=1      sig-id=100000160  type=Both      tracking=src count=300 seconds=60 
| gen-id=1      sig-id=100000159  type=Both      tracking=src count=100 seconds=60 
| gen-id=1      sig-id=100000923  type=Threshold tracking=dst count=200 seconds=60 
| gen-id=1      sig-id=2495       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=2494       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=3152       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=100000311  type=Limit     tracking=src count=1   seconds=360
| gen-id=1      sig-id=100000312  type=Limit     tracking=src count=1   seconds=360
| gen-id=1      sig-id=100000310  type=Limit     tracking=src count=1   seconds=360
| gen-id=1      sig-id=2924       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=2275       type=Threshold tracking=dst count=5   seconds=60 
| gen-id=1      sig-id=3273       type=Threshold tracking=src count=5   seconds=2  
| gen-id=1      sig-id=2923       type=Threshold tracking=dst count=10  seconds=60 
| gen-id=1      sig-id=2496       type=Both      tracking=dst count=20  seconds=60 
| gen-id=1      sig-id=2523       type=Both      tracking=dst count=10  seconds=10 
| gen-id=1      sig-id=100000158  type=Both      tracking=src count=100 seconds=60 
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Verifying Preprocessor Configurations!
Warning: flowbits key 'smb.tree.create.llsrpc' is set but not ever checked.
Warning: flowbits key 'realplayer.playlist' is checked but not ever set.
Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set.
Warning: flowbits key 'community_uri.size.1050' is set but not ever checked.
37 out of 512 flowbits in use.

Initializing Network Interface wlan0
Decoding Ethernet on interface wlan0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = root
database: password is set
database: database name = db
database:          host = localhost
database:   sensor name = 192.168.0.20
ERROR: database: mysql_error: Unknown database 'db'
Fatal Error, Quitting..  [/PHP]

I was using mysql/freepbx for my asterisk phone system but have decided not to use it and I think this 'db' database is for that. I am by no means and expert with mysql so bear with me. help

---

### Post by metallica1973 on 2010-02-08
update: I found the line in snort.conf:

[PHP]output database: log, mysql, user=xxxx password=xxxx dbname=snort host=localhost[/PHP]

and ran :

[PHP] sudo snort -c /etc/snort/snort.conf[/PHP]

and now I get a senor error in mysql:

[PHP]Initializing Network Interface wlan0
Decoding Ethernet on interface wlan0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = xxxx
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = 192.168.0.20
database: mysql_error: Table 'snort.sensor' doesn't exist
database: mysql_error: Table 'snort.sensor' doesn't exist
SQL=INSERT INTO sensor (hostname, interface, detail, encoding, last_cid) VALUES ('192.168.0.20','wlan0',1,0, 0)
database: mysql_error: Table 'snort.sensor' doesn't exist
database: Problem obtaining SENSOR ID (sid) from snort->sensor
ERROR:  When this plugin starts, a SELECT query is run to find the sensor id for the
 currently running sensor. If the sensor id is not found, the plugin will run
 an INSERT query to insert the proper data and generate a new sensor id. Then a
 SELECT query is run to get the newly allocated sensor id. If that fails then
 this error message is generated.

 Some possible causes for this error are:
  * the user does not have proper INSERT or SELECT privileges
  * the sensor table does not exist

 If you are _absolutely_ certain that you have the proper privileges set and
 that your database structure is built properly please let me know if you
 continue to get this error. You can contact me at (roman@danyliw.com).

Fatal Error, Quitting..
[/PHP] 

???????????

---

### Post by metallica1973 on 2010-02-09
I ran the script and it all worked fine until I restarted the computer and snort will not run I checked all the services:

mysql

[PHP]Server version		5.1.37-1ubuntu5
Protocol version	10
Connection		Localhost via UNIX socket
UNIX socket		/var/run/mysqld/mysqld.sock
Uptime:			1 hour 16 min 54 sec

Threads: 1  Questions: 259  Slow queries: 0  Opens: 448  Flush tables: 1  Open tables: 64  Queries per second avg: 0.56
[/PHP]

apache2

[PHP]* Apache is running (pid 3646)[/PHP]

and the error with snort when I try and start it. ????????????

[PHP]* Starting Network Intrusion Detection System  snort                                                                                  * /etc/snort/db-pending-config file found
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config
[/PHP]

---

