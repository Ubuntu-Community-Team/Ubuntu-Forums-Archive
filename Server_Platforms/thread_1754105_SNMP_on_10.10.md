---
title: "SNMP on 10.10"
date: 2011-05-09
forum: Server Platforms
---

### Post by xp2 on 2011-05-09
Hello,
I have a asterisk server running on my ubuntu 10.10 server box. I also have a zabbix server monitoring my networks. Asterisk have the possibility to show very interesting statistic with SNMP. But I cannot managed to set it up. This is the result i get when I try to get the version information with snmpwalk:
```
root@PBX:~# snmpwalk -v 3 -u asteriskUser -l authPriv -a MD5 -A <password> -x DES -X <Password> 127.0.0.1 ASTERISK-MIB::astVersionString
MIB search path: /root/.snmp/mibs:/usr/share/mibs/site:/usr/share/snmp/mibs:/usr/share/mibs/iana:/usr/share/mibs/ietf:/usr/share/mibs/netsnmp
Cannot find module (SNMPv2-TC): At line 9 in /usr/share/snmp/mibs/asterisk-mib
Cannot find module (SNMPv2-SMI): At line 5 in /usr/share/snmp/mibs/digium-mib
Did not find 'enterprises' in module #-1 (/usr/share/snmp/mibs/digium-mib)
Unlinked OID in DIGIUM-MIB: digium ::= { enterprises 22736 }
Undefined identifier: enterprises near line 7 of /usr/share/snmp/mibs/digium-mib
Did not find 'DisplayString' in module #-1 (/usr/share/snmp/mibs/asterisk-mib)
Did not find 'TruthValue' in module #-1 (/usr/share/snmp/mibs/asterisk-mib)
Did not find 'digium' in module DIGIUM-MIB (/usr/share/snmp/mibs/asterisk-mib)
Unlinked OID in ASTERISK-MIB: asterisk ::= { digium 1 }
Undefined identifier: digium near line 14 of /usr/share/snmp/mibs/asterisk-mib
ASTERISK-MIB::astVersionString: Unknown Object Identifier

```After I few research on google It seems I'm missing the net-snmp package witch I cannot find anywhere. 
Can anyone help me?

---

### Post by ekool on 2011-05-09
net-snmp contains the snmp daemon (snmpd) -- and should be available via apt/aptitude.

aptitude -y install net-snmp

---

### Post by xp2 on 2011-05-09
Thanks For the reply,
I already have snmpd installed and :
```
 aptitude -y install net-snmp
Couldn't find package "net-snmp".  However, the following
packages contain "net-snmp" in their name:
  libnet-snmp-perl
Couldn't find package "net-snmp".  However, the following
packages contain "net-snmp" in their name:
  libnet-snmp-perl
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

---

### Post by ekool on 2011-05-09
> **xp2 said:**
> Thanks For the reply,
I already have snmpd installed and :
```
 aptitude -y install net-snmp
Couldn't find package "net-snmp".  However, the following
packages contain "net-snmp" in their name:
  libnet-snmp-perl
Couldn't find package "net-snmp".  However, the following
packages contain "net-snmp" in their name:
  libnet-snmp-perl
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

I have an snmp daemon running on my box for Cacti, here's the installed packages:

```

:~$ aptitude search '~i' | grep -i snmp
i A libnet-snmp-perl                - Script SNMP connections                   
i A libsnmp-base                    - SNMP (Simple Network Management Protocol) 
i A libsnmp-session-perl            - Perl support for accessing SNMP-aware devi
i A libsnmp15                       - SNMP (Simple Network Management Protocol) 
i A php5-snmp                       - SNMP module for php5                      
i A snmp                            - SNMP (Simple Network Management Protocol) 
i   snmpd                           - SNMP (Simple Network Management Protocol)

```

---

### Post by xp2 on 2011-05-09
Yes I have about the same :
```
root@PBX:~# aptitude search '~i' | grep -i snmp
i   libnet-snmp-perl                - Script SNMP connections
i A libsnmp-base                    - SNMP (Simple Network Management Protocol)
i A libsnmp-perl                    - SNMP (Simple Network Management Protocol)
i   libsnmp-session-perl            - Perl support for accessing SNMP-aware devi
i A libsnmp15                       - SNMP (Simple Network Management Protocol)
i   php5-snmp                       - SNMP module for php5
i   python-pynetsnmp                - Python ctypes bindings for NET-SNMP with T
i   snmp                            - SNMP (Simple Network Management Protocol)
i   snmpd                           - SNMP (Simple Network Management Protocol)
i   snmptt                          - SNMP trap handler for use with snmptrapd

```
May I ask what files you have in /usr/share/snmp/mibs/
Thanks

---

### Post by ekool on 2011-05-09
```


:~$ ls /usr/share/snmp/mibs/
AGENTX-MIB.txt                       IP-FORWARD-MIB.txt         RFC1155-SMI.txt              SNMPv2-CONF.txt
DISMAN-EVENT-MIB.txt                 IP-MIB.txt                 RFC1213-MIB.txt              SNMPv2-MIB.txt
DISMAN-SCHEDULE-MIB.txt              IPV6-ICMP-MIB.txt          RFC-1215.txt                 SNMPv2-SMI.txt
DISMAN-SCRIPT-MIB.txt                IPV6-MIB.txt               RMON-MIB.txt                 SNMPv2-TC.txt
EtherLike-MIB.txt                    IPV6-TCP-MIB.txt           SCTP-MIB.txt                 SNMPv2-TM.txt
HCNUM-TC.txt                         IPV6-TC.txt                SMUX-MIB.txt                 SNMP-VIEW-BASED-ACM-MIB.txt
HOST-RESOURCES-MIB.txt               IPV6-UDP-MIB.txt           SNMP-COMMUNITY-MIB.txt       TCP-MIB.txt
HOST-RESOURCES-TYPES.txt             LM-SENSORS-MIB.txt         SNMP-FRAMEWORK-MIB.txt       TRANSPORT-ADDRESS-MIB.txt
IANA-ADDRESS-FAMILY-NUMBERS-MIB.txt  NET-SNMP-AGENT-MIB.txt     SNMP-MPD-MIB.txt             UCD-DEMO-MIB.txt
IANAifType-MIB.txt                   NET-SNMP-EXAMPLES-MIB.txt  SNMP-NOTIFICATION-MIB.txt    UCD-DISKIO-MIB.txt
IANA-LANGUAGE-MIB.txt                NET-SNMP-EXTEND-MIB.txt    SNMP-PROXY-MIB.txt           UCD-DLMOD-MIB.txt
IANA-RTPROTO-MIB.txt                 NET-SNMP-MIB.txt           SNMP-TARGET-MIB.txt          UCD-IPFWACC-MIB.txt
IF-INVERTED-STACK-MIB.txt            NET-SNMP-TC.txt            SNMP-USER-BASED-SM-MIB.txt   UCD-SNMP-MIB.txt
IF-MIB.txt                           NET-SNMP-VACM-MIB.txt      SNMP-USM-AES-MIB.txt         UDP-MIB.txt
INET-ADDRESS-MIB.txt                 NOTIFICATION-LOG-MIB.txt   SNMP-USM-DH-OBJECTS-MIB.txt

```

---

### Post by xp2 on 2011-05-10
I was sure this was my problem. I have none of those MIB file. I only have the 2 I created for asterisk. Where can I get those files? Is it in a package? If yes witch one?
Thanks

---

### Post by ekool on 2011-05-10
> **xp2 said:**
> I was sure this was my problem. I have none of those MIB file. I only have the 2 I created for asterisk. Where can I get those files? Is it in a package? If yes witch one?
Thanks

```


# apt-file search IPV6-MIB.txt
libsnmp-base: /usr/share/snmp/mibs/IPV6-MIB.txt
# apt-file search UCD-SNMP-MIB.txt
libsnmp-base: /usr/share/snmp/mibs/UCD-SNMP-MIB.txt

```

---

### Post by xp2 on 2011-05-18
Well looks like I have to bring the subject back :
```
root@PBX:~# apt-file search IPV6-MIB.txt
root@PBX:~#
```
Any other idea?
Thanks

---

### Post by fizz on 2011-06-04
was having the same problem..

mibs are in /usr/share/mibs/netsnmp

---

### Post by arshadparvez on 2011-12-15
You can find missing MIB files at
[http://www.net-snmp.org/docs/mibs/](http://www.net-snmp.org/docs/mibs/)

regards

---

### Post by uracolix on 2012-12-14
Sorry for waking up this stone old thread, but if somebody stumbles across
this issue, this solution might help.

I found this very helpfull link for solving the issue:
[http://pof.eslack.org/2010/11/29/installing-ietf-mib-files-in-ubuntu-10-10/](http://pof.eslack.org/2010/11/29/installing-ietf-mib-files-in-ubuntu-10-10/)

Just in case if this link disapears, here is the essential information:

[LIST=1]
[*] $ sudo apt-get install snmp-mibs-downloader
[*]$ sudo download-mibs
[*]$ sudo sed -i 's/^mibs/#mibs/g' /etc/snmp/snmp.conf
[/LIST]
Step 2 was done automatically in Ubuntu 11.10, step 3 is essential to do.

The main reason, if there are no plain text MIB's are displayed, are coyright issues
with distributing the MIB files along with a Linux distro.

Cheers, Axel

---

