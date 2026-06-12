---
title: "Nagios 3.4.1 Monitoring SNMP"
date: 2013-03-27
forum: Server Platforms
---

### Post by kamazoke on 2013-03-27
Hi guys,

I have 2 Canon iRC printers which Nagios cannot read snmp status from.
I also have 4 D-link switch which Nagios cannot read snmp status from.

Canon printers answers to snmpwalk 
snmpwalk -v 1 -c public IP Address

D-link switches answers to snmpwalk
snmpwalk -v 2c -c public IP address

But Nagios shows Error in packet or Service check time out :(

I am not an expert, and I have tried to find the solution and tried a lot of solutions, but still no go :(

---

### Post by tgalati4 on 2013-03-27
Many switches allow you to specify an IP for a running syslog server (any Linux/Unix machine).  Then you could query that machine for status.  Perhaps write a script using snmpwalk to send output to syslog--that would cover the printers as well.

Mar 26 23:01:01 freenas last message repeated 5 times
Mar 26 23:03:01 freenas mDNSResponder: ERROR: getOptRdata - unknown opt 4
Mar 26 23:03:49 tubuntu2 apcupsd[5176]: 000.0,000.0,000.0,00.00,00.00,00.0,00.0,000.0,000.0,000.0,000.0,1
Mar 26 23:08:50 tubuntu2 apcupsd[5176]: 000.0,000.0,000.0,00.00,00.00,00.0,00.0,000.0,000.0,000.0,000.0,0
Mar 26 23:09:01 tubuntu2 /USR/SBIN/CRON[12250]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindept
h 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Mar 26 23:13:50 tubuntu2 apcupsd[5176]: 000.0,000.0,000.0,00.00,00.00,00.0,00.0,000.0,000.0,000.0,000.0,1
Mar 26 23:14:17 freenas smbd[12650]: [2013/03/26 23:14:17.230180,  0] lib/util_sock.c:474(read_fd_with_timeout)
Mar 26 23:14:17 freenas smbd[12650]: [2013/03/26 23:14:17.231138,  0] lib/util_sock.c:1432(get_peer_addr_internal)
Mar 26 23:14:17 freenas smbd[12650]:   getpeername failed. Error was Socket is not connected
Mar 26 23:14:17 freenas smbd[12650]:   read_fd_with_timeout: client 0.0.0.0 read error = Socket is not connected.

I have a freenas server that was having problems.  Since it runs in RAM completely, any failures do not get saved, but you can redirect errors to syslog on another IP--in this case an Ubuntu desktop which runs syslog.  Many devices (switches, routers, UPS's, printers) have this capability.

---

### Post by koenn on 2013-03-27
what nagios plugin are you using, 
and what does it say when you run it from a shell ?

---

### Post by LHammonds on 2013-03-28
Run the SNMP utility from the command line on your Nagios server such as the following:
```

/usr/local/nagios/libexec/check_snmp -H IPAddress -C public -o sysUpTime.0

```

For more ideas, you can take a look at my thread which covers the setup of a Nagios server in my signature.

LHammonds

---

### Post by kamazoke on 2013-04-02
> **koenn said:**
> what nagios plugin are you using, 
and what does it say when you run it from a shell ?

I am running 1.4.15 I think.

check_icmp responds, but check_snmp doesn't

---

### Post by kamazoke on 2013-04-02
> **LHammonds said:**
> Run the SNMP utility from the command line on your Nagios server such as the following:
```

/usr/local/nagios/libexec/check_snmp -H IPAddress -C public -o sysUpTime.0

```

For more ideas, you can take a look at my thread which covers the setup of a Nagios server in my signature.

LHammonds

This command doesnt give me any respons, and I have had it "active" for 24 hours.

I am looking at your impressive guide right now :)

---

### Post by kamazoke on 2013-04-02
> **LHammonds said:**
> Run the SNMP utility from the command line on your Nagios server such as the following:
```

/usr/local/nagios/libexec/check_snmp -H IPAddress -C public -o sysUpTime.0

```

For more ideas, you can take a look at my thread which covers the setup of a Nagios server in my signature.

LHammonds

Hi LHammonds,

Your guide fixed the problem, now they all respond on snmp requests from Nagios.. Thank you so much :-)

---

### Post by LHammonds on 2013-04-02
Awesome.  :guitar:

---

### Post by immadmacs on 2013-05-14
I'm migrating from a previous nagios installation to a new Ubuntu 12.04 server. I have managed to get all the devices to report except the Cisco ASA. I'm getting this error 
External command error: Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/DIFFSERV-MIB)Undefined OBJECT-GROUP (diffServMIBMultiFieldClfrGroup): At line 2195 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Undefined OBJECT-GROUP (diffServMultiFieldClfrNextFree): At line 2157 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Undefined OBJECT-GROUP (diffServMIBMultiFieldClfrGroup): At line 2062 in /usr/share/mibs/ietf/IPSEC-SPD-MIB
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/MPLS-LSR-STD-MIB)
Unlinked OID in IPATM-IPMC-MIB: marsMIB ::= { mib-2 57 }
Undefined identifier: mib-2 near line 18 of /usr/share/mibs/ietf/IPATM-IPMC-MIB
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/DOCS-CABLE-DEVICE-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/IP-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/DISMAN-EVENT-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/ALARM-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/DIFFSERV-CONFIG-MIB)
Bad operator (INTEGER): At line 73 in /usr/share/mibs/ietf/SNMPv2-PDU
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/GMPLS-LSR-STD-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/MPLS-TE-STD-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/GMPLS-TE-STD-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/DISMAN-SCHEDULE-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/DISMAN-EXPRESSION-MIB)
Did not find 'zeroDotZero' in module SNMPv2-SMI (/usr/share/mibs/ietf/APPLICATION-MIB)
Expected "::=" (RFC5644): At line 493 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Expected "{" (EOF): At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Bad object identifier: At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB
Bad parse of OBJECT-IDENTITY: At line 651 in /usr/share/mibs/iana/IANA-IPPM-METRICS-REGISTRY-MIB

Timeout: No Response from 172[FONT=arial, verdana, serif][COLOR=#000000].xxx.xxx.xxx:161[/COLOR][/FONT]

---

