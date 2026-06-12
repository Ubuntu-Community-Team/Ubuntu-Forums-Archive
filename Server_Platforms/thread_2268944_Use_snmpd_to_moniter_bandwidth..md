---
title: "Use snmpd to moniter bandwidth."
date: 2015-03-12
forum: Server Platforms
---

### Post by derr12 on 2015-03-12
Hello!

Im using a vmware system, the virtual switch does not allow me to poll network traffic via snmp like a traditional switch.

So i installed the snmpd service in ubuntu server 14.04.   I can see lots of MIBs,  but it does not seem to allow polling of ethernet traffic out of the box.  Have come up empty handed googleing.  

any idea how i get the snmp service to hand out Ethernet traffic stats?  Im thinking average interface usage over the last 2 minutes?

---

### Post by derr12 on 2015-03-17
Is this even doable?

---

### Post by tgalati4 on 2015-03-17
Don't know how to get snmp to do it if the MIB's are not visible, but *netstat* will give you network stats:

> tgalati4@Mint17 ~ $ netstat -s | grep received
    462291 total packets received
    84 ICMP messages received
    344 connection resets received
    404429 segments received
    843 bad segments received.
    45648 packets received
    12930 packets to unknown port received.
    38873 acknowledgments not containing data payload received
    530 DSACKs received
    3 DSACKs for out of order packets received


---

### Post by derr12 on 2015-03-27
I need it to be pol-lable and graph-able by an mrtg server. The micromanagement department Loves graphs.

---

