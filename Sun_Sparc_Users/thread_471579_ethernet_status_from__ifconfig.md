---
title: "ethernet status from  ifconfig"
date: 2007-06-12
forum: Sun Sparc Users
---

### Post by Malley H.Kasuga on 2007-06-12
Hello, sir.

I am using a SUN Netra X1 standard NIC(davicom tulip compatible).
All transmitting and receiving are OK!
But some stat of result by `ifconfig -a '.
It shows errors is reversed to TX packets, like below:
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:445 dropped:0 overruns:0 carrier:445
Of course normalcy communicates in this state.

If there is a solution, I want to know it.:(

---

### Post by netztier on 2007-06-12
> **Malley H.Kasuga said:**
> Hello, sir.

I am using a SUN Netra X1 standard NIC(davicom tulip compatible).
All transmitting and receiving are OK!
But some stat of result by `ifconfig -a '.
It shows errors is reversed to TX packets, like below:
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:445 dropped:0 overruns:0 carrier:445
Of course normalcy communicates in this state.

If there is a solution, I want to know it.:(

what are the results of **sudo mii-diag -v eth0** and/or **sudo ethtool eth0 **, if either of these works with the driver module that is being used?

I am wondering if speed and duplex negotiation between the NIC and the Hub/Switch have been successful and what result came out of it.

best regards

Marc

---

### Post by Malley H.Kasuga on 2007-06-12
Thanks for your quickly response. 

An Ethernet environment(negotiation and lower layers) may be OK.
I think this problem is caused by only an error of merely indication.
It has been occurred at eth1, so the result of mii-diag at each ports attached...

sudo mii-diag -v eth0
---
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 1 (BMCR 0x3100).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #1 transceiver registers:
   3100 782d 0181 b840 01e1 45e1 0001 0000
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 8018 7800 1000 0000 0000 0000 0000
   0000 0000 0000 0000 0000 0000 0000 0000.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 Basic mode status register 0x782d ... 782d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:60:6e:--:--:--, model 4 rev. 0.
   Vendor/Part: Davicom (unknown type).
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.
  Davicom vendor specific registers: 0x0000 0x8018 0x7800.
---
sudo mii-diag -v eth1
mii-diag.c:v2.11 3/21/2005 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
  Using the new SIOCGMIIPHY value on PHY 1 (BMCR 0x3100).
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 Basic mode status register 0x7829 ... 782d.
   Link status: previously broken, but now reestablished.
   This transceiver is capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

libmii.c:v2.11 2/28/2005  Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
 MII PHY #1 transceiver registers:
   3100 782d 0181 b840 01e1 45e1 0001 0000
   0000 0000 0000 0000 0000 0000 0000 0000
   0000 8018 7800 1000 0002 0004 0000 0000
   0000 0000 0000 0000 0000 0000 0000 0000.
 Basic mode control register 0x3100: Auto-negotiation enabled.
 Basic mode status register 0x782d ... 782d.
   Link status: established.
   Capable of  100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Able to perform Auto-negotiation, negotiation complete.
 Vendor ID is 00:60:6e:--:--:--, model 4 rev. 0.
   Vendor/Part: Davicom (unknown type).
 I'm advertising 01e1: 100baseTx-FD 100baseTx 10baseT-FD 10baseT
   Advertising no additional info pages.
   IEEE 802.3 CSMA/CD protocol.
 Link partner capability is 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT.
   Negotiation  completed.
  Davicom vendor specific registers: 0x0000 0x8018 0x7800.
---

Best regards.
Malley

---

### Post by chatuser on 2007-06-17
If use on Intel:

ethtool eth0
mii-tool eth0

These commands are not known but they are very useful.

---

