---
title: "qla2xxx SNS scan failed -- no LUNs for HBA found"
date: 2009-08-05
forum: Server Platforms
---

### Post by Oakenshields on 2009-08-05
Hello,
we are running the Ubuntu Server Edition (jaunty) using kernel 2.6.28-11-server. A HBA from QLogic (QLE2462) is supposed to connect to a SAN of the computing department of our university.

If anyone else had problems loading the firmware at boot-time (qla2xxx)- there is a solution under:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/328550/comments/11](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/328550/comments/11)

What remains is the problem that we cannot see any LUNs. From the departments perspective everything seems to be fine. As soon as one reloads the QLogic drivers the following messages appear:

qla2xxx 0000:08:00.1: LIP reset occurred (f700).
qla2xxx 0000:08:00.1: LOOP UP detected (4 Gbps).
qla2xxx 0000:08:00.1: SNS scan failed -- assuming zero-entry result...

As far as I know at least the LIP reset and the SNS scan failed are not normal... with the consequence that I don't find any devices in /dev. Also lsscsi brings nothing.

This issue has been discussed several times but everytimes with results like "be have reconfigured the SAN and then it magically worked". Some say one should unplug the cables first, before configuring the LUNs and partitions- does not work as well.

Has anyone had this problem and found a solution for that?

Best wishes,

Peter

---

### Post by Oakenshields on 2009-08-13
In answer to myself: After the SAN has been set up we had to do some work on the server and switched the cabels at the HBA... that caused the problem. The fabrics got the switched WWNs and alas- it did not work. I've seen some forum entries where the problem was solved by setting up the zoning etc. again from scratch. That would have worked here as well- but checking the cables first can be worth a try ;-).

---

