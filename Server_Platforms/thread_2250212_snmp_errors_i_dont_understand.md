---
title: "snmp errors i dont understand"
date: 2014-10-27
forum: Server Platforms
---

### Post by MrJake on 2014-10-27
while trying to use snimpy in python i get errors. and following there recommendations i get even more errors
here is an example of these errors

mrjake@server:/usr/share/snmp/mibs$ sudo smilint -s -l1 IF-MIB.txt 
IF-MIB.txt:6: [1] failed to locate MIB module `SNMPv2-SMI'
IF-MIB.txt:9: [1] failed to locate MIB module `SNMPv2-TC'
IF-MIB.txt:11: [1] failed to locate MIB module `SNMPv2-CONF'
IF-MIB.txt:12: [1] failed to locate MIB module `SNMPv2-MIB'
IF-MIB.txt:13: [1] failed to locate MIB module `IANAifType-MIB'
IF-MIB.txt:44: [1] unknown object identifier label `mib-2'
IF-MIB.txt:1047: [1] illegal base type `PhysAddress' in index element `ifRcvAddressAddress' of row ifRcvAddressEntry
IF-MIB.txt:1116: [1] unknown object identifier label `snmpTraps'

But when i do a ls in the same dir we clearly see the mibs are there
mrjake@server:~/Work/Python tutorials$ ls -l /usr/share/snmp/mibs
total 3816
-rw-r--r-- 1 root root  17455 Nov 21  2008 AGENTX-MIB.txt
-rw-r--r-- 1 root root  19342 Nov 21  2008 arris_cm_capability.mib
-rw-r--r-- 1 root root   3484 Nov 21  2008 arrishdr.mib
-rw-r--r-- 1 root root 110319 Nov 21  2008 arris_mta_device.mib
-rw-r--r-- 1 root root  36576 Nov 21  2008 BGP4-MIB.txt
-rw-r--r-- 1 root root 116952 Nov 21  2008 blp2.mib
-rw-r--r-- 1 root root  36959 Nov 21  2008 BRIDGE-MIB.txt
drwxr-xr-x 2 root root  65536 Oct 22  2013 cisco
-rw-r--r-- 1 root root  85739 Nov 21  2008 CISCO-DOCS-EXT-MIB.txt
-rw-r--r-- 1 root root  19396 Nov 21  2008 CISCO-IP-IF-MIB.txt
-rw-r--r-- 1 root root   9195 Nov 21  2008 CISCO-SMI.my
-rw-r--r-- 1 root root  43961 Nov 21  2008 dev0.mib
-rw-r--r-- 1 root root  68177 Nov 21  2008 DISMAN-EVENT-MIB.txt
-rw-r--r-- 1 root root  24613 Nov 21  2008 DISMAN-SCHEDULE-MIB.txt
-rw-r--r-- 1 root root  64311 Nov 21  2008 DISMAN-SCRIPT-MIB.txt
-rw-r--r-- 1 root root  69598 Nov 21  2008 DOCS-CABLE-DEVICE-MIB.my
-rw-r--r-- 1 root root  60076 Nov 21  2008 DOCS-CABLE-DEVICE-MIB-V1SMI.txt
-rw-r--r-- 1 root root  92936 Nov 21  2008 DOCS-IF.txt
-rw-r--r-- 1 root root  16830 Nov 21  2008 eSafe.mib
-rw-r--r-- 1 root root  84492 Nov 21  2008 EtherLike-MIB.txt
-rw-r--r-- 1 root root   1913 Apr  8  2014 GNOME-SMI.txt
-rw-r--r-- 1 root root   4660 Nov 21  2008 HCNUM-TC.txt
-rw-r--r-- 1 root root  52544 Nov 21  2008 HOST-RESOURCES-MIB.txt
-rw-r--r-- 1 root root  10583 Nov 21  2008 HOST-RESOURCES-TYPES.txt
-rw-r--r-- 1 root root   4743 Nov 21  2008 IANA-ADDRESS-FAMILY-NUMBERS-MIB.txt
-rw-r--r-- 1 root root  24065 Nov 21  2008 IANAifType-MIB.txt
-rw-r--r-- 1 root root   4299 Nov 21  2008 IANA-LANGUAGE-MIB.txt
-rw-r--r-- 1 root root   3518 Nov 21  2008 IANA-RTPROTO-MIB.txt
-rw-r--r-- 1 root root 103753 Nov 21  2008 ietf_sig_na.mib
-rw-r--r-- 1 root root   5066 Nov 21  2008 IF-INVERTED-STACK-MIB.txt
-rw-r--r-- 1 root root  71691 Nov 21  2008 IF-MIB.txt
-rw-r--r-- 1 root root  16782 Nov 21  2008 INET-ADDRESS-MIB.txt
-rw-r--r-- 1 root root  46366 Nov 21  2008 IP-FORWARD-MIB.txt
-rw-r--r-- 1 root root 185928 Nov 21  2008 IP-MIB.txt
-rw-r--r-- 1 root root  15936 Nov 21  2008 IPV6-ICMP-MIB.txt
-rw-r--r-- 1 root root  48703 Nov 21  2008 IPV6-MIB.txt
-rw-r--r-- 1 root root   7257 Nov 21  2008 IPV6-TCP-MIB.txt
-rw-r--r-- 1 root root   2367 Nov 21  2008 IPV6-TC.txt
-rw-r--r-- 1 root root   4400 Nov 21  2008 IPV6-UDP-MIB.txt
-rw-r--r-- 1 root root   5931 Oct  9  2012 LM-SENSORS-MIB.txt
-rw-r--r-- 1 root root  15901 Oct  9  2012 NET-SNMP-AGENT-MIB.txt
-rw-r--r-- 1 root root   9160 Oct  9  2012 NET-SNMP-EXAMPLES-MIB.txt
-rw-r--r-- 1 root root   9326 Oct  9  2012 NET-SNMP-EXTEND-MIB.txt
-rw-r--r-- 1 root root   2036 Oct  9  2012 NET-SNMP-MIB.txt
-rw-r--r-- 1 root root   1215 Oct  9  2012 NET-SNMP-MONITOR-MIB.txt
-rw-r--r-- 1 root root   3350 Oct  9  2012 NET-SNMP-PASS-MIB.txt
-rw-r--r-- 1 root root   2504 Oct  9  2012 NET-SNMP-PERIODIC-NOTIFY-MIB.txt
-rw-r--r-- 1 root root   1226 Oct  9  2012 NET-SNMP-SYSTEM-MIB.txt
-rw-r--r-- 1 root root   4814 Oct  9  2012 NET-SNMP-TC.txt
-rw-r--r-- 1 root root   5039 Oct  9  2012 NET-SNMP-VACM-MIB.txt
-rw-r--r-- 1 root root  24723 Nov 21  2008 NOTIFICATION-LOG-MIB.txt
-rw-r--r-- 1 root root  86115 Nov 21  2008 OSPF-MIB.txt
-rw-r--r-- 1 root root  16095 Nov 21  2008 OSPF-TRAP-MIB.txt
-rw-r--r-- 1 root root  45670 Nov 21  2008 pp.mib
-rw-r--r-- 1 root root 109920 Nov 21  2008 qos.mib
-rw-r--r-- 1 root root   3067 Nov 21  2008 RFC1155-SMI.txt
-rw-r--r-- 1 root root  79667 Nov 21  2008 RFC1213-MIB.txt
-rw-r--r-- 1 root root   1174 Nov 21  2008 RFC-1215.txt
-rw-r--r-- 1 root root  46685 Nov 21  2008 rfc1493.mib
-rw-r--r-- 1 root root  25065 Nov 21  2008 rfc1907.mib
-rw-r--r-- 1 root root  23490 Nov 21  2008 rfc2011.mib
-rw-r--r-- 1 root root   4078 Nov 21  2008 rfc2013.mib
-rw-r--r-- 1 root root   4397 Nov 21  2008 rfc2213.mib
-rw-r--r-- 1 root root  76046 Nov 21  2008 rfc2233.mib
-rw-r--r-- 1 root root  21970 Nov 21  2008 rfc2571.mib
-rw-r--r-- 1 root root   5611 Nov 21  2008 rfc2572.mib
-rw-r--r-- 1 root root  53027 Nov 21  2008 rfc2573.mib
-rw-r--r-- 1 root root  38038 Nov 21  2008 rfc2574.mib
-rw-r--r-- 1 root root  33427 Nov 21  2008 rfc2575.mib
-rw-r--r-- 1 root root  15488 Nov 21  2008 rfc2576.mib
-rw-r--r-- 1 root root  52976 Nov 21  2008 rfc2665.mib
-rw-r--r-- 1 root root  72190 Nov 21  2008 rfc2669.mib
-rw-r--r-- 1 root root 163628 Nov 21  2008 rfc2670.mib
-rw-r--r-- 1 root root  21115 Nov 21  2008 rfc2786.mib
-rw-r--r-- 1 root root  12258 Nov 21  2008 rfc2851.mib
-rw-r--r-- 1 root root  17345 Nov 21  2008 rfc2933.mib
-rw-r--r-- 1 root root  57768 Nov 21  2008 rfc3083.mib
-rw-r--r-- 1 root root 128705 Nov 21  2008 rfc3289.mib
-rw-r--r-- 1 root root  16715 Nov 21  2008 RIPv2-MIB.txt
-rw-r--r-- 1 root root 147822 Nov 21  2008 RMON-MIB.txt
-rw-r--r-- 1 root root   4595 Nov 21  2008 SMUX-MIB.txt
-rw-r--r-- 1 root root  15490 Nov 21  2008 SNMP-COMMUNITY-MIB.txt
-rw-r--r-- 1 root root  22342 Nov 21  2008 SNMP-FRAMEWORK-MIB.txt
-rw-r--r-- 1 root root   5496 Nov 21  2008 SNMP-MPD-MIB.txt
-rw-r--r-- 1 root root  20014 Nov 21  2008 SNMP-NOTIFICATION-MIB.txt
-rw-r--r-- 1 root root   9106 Nov 21  2008 SNMP-PROXY-MIB.txt
-rw-r--r-- 1 root root  22769 Nov 21  2008 SNMP-TARGET-MIB.txt
-rw-r--r-- 1 root root  39201 Nov 21  2008 SNMP-USER-BASED-SM-MIB.txt
-rw-r--r-- 1 root root   2205 Nov 21  2008 SNMP-USM-AES-MIB.txt
-rw-r--r-- 1 root root  21106 Nov 21  2008 SNMP-USM-DH-OBJECTS-MIB.txt
-rw-r--r-- 1 root root   8259 Nov 21  2008 snmpv2_conf.mib
-rw-r--r-- 1 root root   8263 Nov 21  2008 SNMPv2-CONF.txt
-rw-r--r-- 1 root root  29305 Nov 21  2008 SNMPv2-MIB.txt
-rw-r--r-- 1 root root   8933 Nov 21  2008 snmpv2_smi.mib
-rw-r--r-- 1 root root   8924 Nov 21  2008 SNMPv2-SMI.txt
-rw-r--r-- 1 root root  38117 Nov 21  2008 snmpv2_tc.mib
-rw-r--r-- 1 root root  38034 Nov 21  2008 SNMPv2-TC.txt
-rw-r--r-- 1 root root   5775 Nov 21  2008 SNMPv2-TM.txt
-rw-r--r-- 1 root root  34162 Nov 21  2008 SNMP-VIEW-BASED-ACM-MIB.txt
-rw-r--r-- 1 root root  14675 Nov 21  2008 SOURCE-ROUTING-MIB.txt
-rw-r--r-- 1 root root    540 Nov 21  2008 TCOMLABS-MIB.mib
-rw-r--r-- 1 root root  28564 Nov 21  2008 TCP-MIB.txt
-rw-r--r-- 1 root root   6263 Nov 21  2008 test.mib
-rw-r--r-- 1 root root  16414 Nov 21  2008 TRANSPORT-ADDRESS-MIB.txt
-rw-r--r-- 1 root root   2163 Oct  9  2012 UCD-DEMO-MIB.txt
-rw-r--r-- 1 root root   4613 Oct  9  2012 UCD-DISKIO-MIB.txt
-rw-r--r-- 1 root root   3087 Oct  9  2012 UCD-DLMOD-MIB.txt
-rw-r--r-- 1 root root   6476 Oct  9  2012 UCD-IPFILTER-MIB.txt
-rw-r--r-- 1 root root   8118 Oct  9  2012 UCD-IPFWACC-MIB.txt
-rw-r--r-- 1 root root  18274 Oct  9  2012 UCD-SNMP-MIB-OLD.txt
-rw-r--r-- 1 root root  48890 Oct  9  2012 UCD-SNMP-MIB.txt
-rw-r--r-- 1 root root  20882 Nov 21  2008 UDP-MIB.txt
-rw-r--r-- 1 root root  19627 Nov 21  2008 usb.mib

if I use snmpwalk to get interface counters using the same mib, it works fine

regardless of the mib i lookup using smilint i get major errors. Im a bit of a snmp noob in the cli. I usually do all my snmp via cacti but im trying to learn python and use it for snmp to script some stuff and snmipy seems to be the best way of doing so. But I think until i resolve my first problem then I cant use snimpy.
here is another example not using sudo and running it as myself
mrjake@server:~/Work/Python tutorials$ smilint -s -l1 /usr/share/snmp/mibs/SNMPv2-MIB.txt 
/usr/share/snmp/mibs/SNMPv2-MIB.txt:6: [1] failed to locate MIB module `SNMPv2-SMI'
/usr/share/snmp/mibs/SNMPv2-MIB.txt:9: [1] failed to locate MIB module `SNMPv2-TC'
/usr/share/snmp/mibs/SNMPv2-MIB.txt:11: [1] failed to locate MIB module `SNMPv2-CONF'
/usr/share/snmp/mibs/SNMPv2-MIB.txt:63: [1] unknown object identifier label `snmpModules'
/usr/share/snmp/mibs/SNMPv2-MIB.txt:75: [1] unknown object identifier label `mib-2'

Anyone can help or guide me hehe

thanks

---

### Post by MrJake on 2014-10-27
Oh and i forgot. im running:
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

updated also

---

### Post by MrJake on 2014-10-27
Fixed my issues installing snmp-mibs-downloader and smistrip

thanks anyways but I found my issue

---

