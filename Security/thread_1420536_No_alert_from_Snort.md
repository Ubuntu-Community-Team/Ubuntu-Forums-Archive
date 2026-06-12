---
title: "No alert from Snort"
date: 2010-03-03
forum: Security
---

### Post by Saif24 on 2010-03-03
Hello,
i have installed snort + mysql + acid base,i add some rules into /etc/snort/rules/local.rules  to test the alert:

alert icmp 192.168.1.20 any -> 192.16.1.21 any (flags:A;ack:0;msg:"NMap icmp ping")\

alert icmp 192.168.1.20 any -> 192.16.1.21 any (content:"abcdefgh";;msg:"ping de windows")\

alert icmp 192.168.1.20 any <> 192.16.1.21 any (flags: S; msg: “HOULA SYN Packet!”:wink:\

after i restart snort and i tied 2 pc by *cross cable ( 192.168.1.20 for windows and the victim is 192.168.1.21 for Linux where the snort is installed ) , my HOME_NET* *192.168.1.21 and the EXTEREL_NET !$HOME_NET. The problem is  *when i run

 snort -dvi eth0 -c /etc/snort/snort.conf

 i see the packet transsmited and recived (the recived conten "abcdefgh" ), when i stoped snort CTRL+C i don't found any alert in the result!!!
Run time prior to being shutdown was 218.523030 seconds
==================================================  =============================
Packet Wire Totals:
   Received:         1346
   Analyzed:         1342 (99.703%)
    Dropped:            0 (0.000%)
Outstanding:            4 (0.297%)
==================================================  =============================
Breakdown by protocol (includes rebuilt packets):
      ETH: 1342       (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 0          (0.000%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 1213       (90.387%)
  IP4disc: 394        (29.359%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 0          (0.000%)
      UDP: 35         (2.608%)
     ICMP: 390        (29.061%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 394        (29.359%)
   FRAG 6: 0          (0.000%)
      ARP: 129        (9.613%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 0          (0.000%)
  DISCARD: 394        (29.359%)
InvChkSum: 0          (0.000%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 1342      
==================================================  =============================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
==================================================  =============================
Frag3 statistics:
        Total Fragments: 394
      Frags Reassembled: 0
               Discards: 0
          Memory Faults: 0
               Timeouts: 0
               Overlaps: 0
              Anomalies: 0
                 Alerts: 0
     FragTrackers Added: 394
    FragTrackers Dumped: 394
FragTrackers Auto Freed: 0
    Frag Nodes Inserted: 394
     Frag Nodes Deleted: 394
==================================================  =============================
Stream5 statistics:
            Total sessions: 0
              TCP sessions: 0
              UDP sessions: 0
             ICMP sessions: 0
                TCP Prunes: 0
                UDP Prunes: 0
               ICMP Prunes: 0
TCP StreamTrackers Created: 0
TCP StreamTrackers Deleted: 0
              TCP Timeouts: 0
              TCP Overlaps: 0
       TCP Segments Queued: 0
     TCP Segments Released: 0
       TCP Rebuilt Packets: 0
         TCP Segments Used: 0
              TCP Discards: 0
      UDP Sessions Created: 0
      UDP Sessions Deleted: 0
              UDP Timeouts: 0
              UDP Discards: 0
                    Events: 0
           TCP Port Filter
                   Dropped: 0
                 Inspected: 0
                   Tracked: 0
           UDP Port Filter
                   Dropped: 0
                 Inspected: 0
                   Tracked: 0
==================================================  =============================
==================================================  =============================
dcerpc2 Preprocessor Statistics
  Total sessions: 0
==================================================  =============================
==================================================  =============================
database: Closing connection to database "snort"
database: Closing connection to database "snort"
Snort exiting


Please if someone can teel me where's the problem! thanks.

---

### Post by Sarmacid on 2010-03-03
Did you try any attacks on the machine with snort? If not, it shouldn't be generating alerts.

The easiest way I've found to test snort, is to enable the ICMP rules, start snort, and ping it from another machine.

---

### Post by Saif24 on 2010-03-03
Yes i try to attack from another machine ( DOS ) with :

ping 192.168.1.21 -t -l 2000

also i try the test by enable ICMP rules and attecked form another machine but no result !!! :confused:

---

### Post by juancarlospaco on 2010-03-03
Snort never worker properly for me...

---

### Post by Kinstonian on 2010-03-03
Your rules are wrong.  ICMP doesn't use TCP flags or any flags for that matter.  Use google images to search for ICMP header.  Try a rule like this:

alert icmp any any -> any any (msg: "ICMP Detected";)

Then ping a computer, or just go to [http://www.testmyids.com/](http://www.testmyids.com/)

---

