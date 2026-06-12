---
title: "Trunk direct to windows server"
date: 2012-12-06
forum: Server Platforms
---

### Post by drakesword on 2012-12-06
So we have a nas we built (6 drives in raid 5 + 1 hot spare + 1 system drive) running ubuntu server 12.04. We are not pleased with the data transfer rate over 1 Gbit networking. On the server itself we can write to the raid at roughly 1GB/s for large block files but smaller files drops down to 300-500 MB/s.

Over the network with either ISCSI or cifs we get roughly 30-100 MB/s.

To increase our performance we were looking at either getting a 10Gbit pcie card or a 4port 1Gbit per port card.

What are the possibilities of trunking directly from windows server to the ubuntu server for using iscsi and or cifs?

---

### Post by darkod on 2012-12-06
If you are talking about NIC bonding (link aggregation), it looks easy according to this:
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

