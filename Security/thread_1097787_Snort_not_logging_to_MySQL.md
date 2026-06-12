---
title: "Snort not logging to MySQL"
date: 2009-03-16
forum: Security
---

### Post by MatsB on 2009-03-16
I'm running Snort 2.8.3.2 on Ubuntu Desktop 8.10. The problem is that nothing seems to get logged to MySQL. Can anyone help me?



Installed packages:
apt-get -y install build-essential libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev

# dpkg -l | grep mysql
ii  libdbd-mysql-perl                          4.007-1build1                           A Perl5 database interface to the MySQL data
ii  libmysqlclient15-dev                       5.0.67-0ubuntu6                         MySQL database development files
ii  libmysqlclient15off                        5.0.67-0ubuntu6                         MySQL database client library
ii  mysql-client-5.0                           5.0.67-0ubuntu6                         MySQL database client binaries
ii  mysql-common                               5.0.67-0ubuntu6                         MySQL database common files
ii  mysql-server-5.0                           5.0.67-0ubuntu6                         MySQL database server binaries
ii  php5-mysql                                 5.2.6-2ubuntu4.1                        MySQL module for php5

Configured MySQL as follows:
mysql -u root &#8211;p
mysql> create database snort;
mysql> grant all privileges on snort.* to &#8217;snort&#8217;@'localhost&#8217; identified by &#8217;snort&#8217;;
database imported with: mysql -D snort -u snort -p < /usr/src/snort-2.8.3.2/schemas/create_mysql


mysql> show tables;
+------------------+
| Tables_in_snort  |
+------------------+
| acid_ag          |
| acid_ag_alert    |
| acid_event       |
| acid_ip_cache    |
| base_roles       |
| base_users       |
| data             |
| detail           |
| encoding         |
| event            |
| icmphdr          |
| iphdr            |
| opt              |
| reference        |
| reference_system |
| schema           |
| sensor           |
| sig_class        |
| sig_reference    |
| signature        |
| tcphdr           |
| udphdr           |
+------------------+
22 rows in set (0.01 sec)


changes made to: etc/snort/snort.conf
var HOME_NET any
var EXTERNAL_NET any
var RULE_PATH /etc/snort/rules
output database: log, mysql, user=snort password=#snort dbname=snort host=localhost

# ls -la /var/log/snort/
total 8
drwxrwx---  2 root snort 4096 2009-03-16 16:15 .
drwxr-xr-x 16 root root  4096 2009-03-16 15:02 ..
-rw-------  1 root root     0 2009-03-16 15:28 alert
-rw-------  1 root root     0 2009-03-16 16:15 snort.log.1237216521

/var/log/messages & /var/log/syslog asys nothing about snort

I'm running snort as: snort -c /etc/snort/snort.conf -i eth0 -D

```
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Verifying Preprocessor Configurations!
Warning: 'ignore_any_rules' option for Stream5 UDP disabled because of UDP rule with flow or flowbits option
Warning: flowbits key 'ScreenControl_capture2213' is set but not ever checked.
Warning: flowbits key 'AM_Remote_Client' is set but not ever checked.
Warning: flowbits key 'mspub_header' is set but not ever checked.
Warning: flowbits key 'http.bmp' is checked but not ever set.
Warning: flowbits key 'smalluploader_remotesh' is set but not ever checked.
Warning: flowbits key 'bit.3xBackdoorconnection' is set but not ever checked.
Warning: flowbits key 'Netspy_Command_Pattern' is set but not ever checked.
Warning: flowbits key 'mssearch_file.request' is set but not ever checked.
Warning: flowbits key 'Evade_File_Manager1' is set but not ever checked.
Warning: flowbits key 'Backdoor.Bersek.Remoteshell' is set but not ever checked.
Warning: flowbits key 'realplayer.playlist' is checked but not ever set.
Warning: flowbits key 'flux10.3' is set but not ever checked.
Warning: flowbits key 'access.download' is set but not ever checked.
Warning: flowbits key 'emf.request' is set but not ever checked.
Warning: flowbits key 'backup_file.request' is set but not ever checked.
Warning: flowbits key 'realmedia_file.request' is set but not ever checked.
Warning: flowbits key 'http.rtf' is set but not ever checked.
Warning: flowbits key 'ReVerSaBle_ExecuteCommand' is set but not ever checked.
Warning: flowbits key 'Backdoor.Apofis.Remotecontrol' is set but not ever checked.
Warning: flowbits key 'Mantis_Notify2' is set but not ever checked.
Warning: flowbits key 'MinicomLite' is set but not ever checked.
Warning: flowbits key 'vnc.pv.setup' is set but not ever checked.
Warning: flowbits key 'CookieMonster_FileExplorer' is set but not ever checked.
Warning: flowbits key 'works.download' is set but not ever checked.
Warning: flowbits key 'wav_file.request' is set but not ever checked.
Warning: flowbits key 'exe.download' is set but not ever checked.
Warning: flowbits key 'snipernet' is set but not ever checked.
Warning: flowbits key 'buttman.1' is set but not ever checked.
Warning: flowbits key 'wmf.download' is set but not ever checked.
Warning: flowbits key 'Only1RAT_Control' is set but not ever checked.
Warning: flowbits key 'PtakkS_Keepalive' is set but not ever checked.
Warning: flowbits key 'Backdoor.Bersek.Init' is set but not ever checked.
Warning: flowbits key 'Omniquad_IRC_InitConnection' is set but not ever checked.
Warning: flowbits key 'outbreak_ring_stc' is set but not ever checked.
376 out of 512 flowbits in use.

Initializing Network Interface eth0
Decoding Ethernet on interface eth0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = snort
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = x.x.x.x
database:     sensor id = 1
database: schema version = 107
database: using the "log" facility

[ Port Based Pattern Matching Memory ]
+-[AC-BNFA Search Info Summary]------------------------------
| Instances        : 815
| Patterns         : 206092
| Pattern Chars    : 1895508
| Num States       : 1061328
| Num Match States : 175532
| Memory           :   27.11Mbytes
|   Patterns       :   5.74M
|   Match Lists    :   8.39M
|   Transitions    :   12.80M
+-------------------------------------------------

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.3.2 (Build 22)
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2008 Sourcefire Inc., et al.
           Using PCRE version: 7.6 2008-01-28

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.9  <Build 15>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 1>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 7>
           Preprocessor Object: SF_FTPTELNET  Version 1.1  <Build 10>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 2>
           Preprocessor Object: SF_DCERPC  Version 1.1  <Build 4>
Not Using PCAP_FRAMES


Run time prior to being shutdown was 77.862845 seconds
===============================================================================
Packet Wire Totals:
   Received:           48
   Analyzed:           44 (91.667%)
    Dropped:            0 (0.000%)
Outstanding:            4 (8.333%)
===============================================================================
Breakdown by protocol (includes rebuilt packets):
      ETH: 44         (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 0          (0.000%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 39         (88.636%)
  IP4disc: 1          (2.273%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 35         (79.545%)
      UDP: 1          (2.273%)
     ICMP: 0          (0.000%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 0          (0.000%)
   FRAG 6: 0          (0.000%)
      ARP: 0          (0.000%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 7          (15.909%)
  DISCARD: 1          (2.273%)
InvChkSum: 13         (29.545%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 44
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
lowmem: queue size     = 12, max  = 32
lowmem: queue flushes  = 0
lowmem: queue inserts  = 164
lowmem: queue uinserts = 73
ac-bnfa: queue size     = 12, max = 32
ac-bnfa: queue flushes  = 0
ac-bnfa: queue inserts  = 164
ac-bnfa: queue uinserts = 73
mpse: queue size     = 12, max possible = 32
mpse: queue flushes  = 0
mpse: queue inserts  = 164
mpse: queue uinserts = 73
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
     FragTrackers Added: 0
    FragTrackers Dumped: 0
FragTrackers Auto Freed: 0
    Frag Nodes Inserted: 0
     Frag Nodes Deleted: 0
===============================================================================
Stream5 statistics:
            Total sessions: 3
              TCP sessions: 2
              UDP sessions: 1
             ICMP sessions: 0
                TCP Prunes: 0
                UDP Prunes: 0
               ICMP Prunes: 0
TCP StreamTrackers Created: 2
TCP StreamTrackers Deleted: 2
              TCP Timeouts: 0
              TCP Overlaps: 0
       TCP Segments Queued: 2
     TCP Segments Released: 2
       TCP Rebuilt Packets: 1
         TCP Segments Used: 2
              TCP Discards: 1
      UDP Sessions Created: 1
      UDP Sessions Deleted: 1
              UDP Timeouts: 0
              UDP Discards: 0
                    Events: 0
===============================================================================
HTTP Inspect - encodings (Note: stream-reassembled packets included):
    POST methods:                   0
    GET methods:                    4
    Headers extracted:              4
    Header Cookies extracted:       4
    Post parameters extracted:      0
    Unicode:                        0
    Double unicode:                 0
    Non-ASCII representable:        0
    Base 36:                        0
    Directory traversals:           0
    Extra slashes ("//"):           0
    Self-referencing paths ("./"):  0
    Total packets processed:        4
===============================================================================
```

---

### Post by bodhi.zazen on 2009-03-16
What makes you think snort is not logging to MySQL ?

What have you tested snort with ?

How are you looking at your data ? Does Base show a sensor ? If so, it is working.

---

### Post by MatsB on 2009-03-16
Well snort says logged: 0 when I stop snort

Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0

---

### Post by The Tronyx on 2009-03-16
Can you log into mysql with the user and password that you set in the configuration file?
> 
mysql -u snortuser -p -h localhost


How long do you let it run for?  Are you behind a router?  Is it possible that there has actually been nothing to log?  Did you try attacking your system to see if snort will log the alerts?

I also noticed this:
> 
Configured MySQL as follows:
mysql -u root &#8211;p
mysql> create database snort;
mysql> grant all privileges on snort.* to &#8217;snort&#8217;@'localhost&#8217; identified by &#8217;snort&#8217;;
database imported with: mysql -D snort -u snort -p < /usr/src/snort-2.8.3.2/schemas/create_mysql


You should also add the line "flush privileges;" in there.  If you can connect to the MySQL database with mysql -u snortuser -p -h localhost, try (from the mysql> prompt) show databases; and tell us what you see.

---

### Post by MatsB on 2009-03-16
> **2point0 said:**
> Can you log into mysql with the user and password that you set in the configuration file?


How long do you let it run for?  Are you behind a router?  Is it possible that there has actually been nothing to log?  Did you try attacking your system to see if snort will log the alerts?



Thanks guys, I didn't run it long enough. Now I see logs being created in base and MySQL. Problem solved ;)

---

### Post by bodhi.zazen on 2009-03-16
> **MatsB said:**
> Thanks guys, I didn't run it long enough. Now I see logs being created in base and MySQL. Problem solved ;)

That is the most common "problem", especially if your site has low traffic.

---

