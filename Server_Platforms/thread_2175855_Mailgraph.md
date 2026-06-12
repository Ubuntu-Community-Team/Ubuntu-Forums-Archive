---
title: "Mailgraph"
date: 2013-09-21
forum: Server Platforms
---

### Post by sefs on 2013-09-21
Can someone explain the below?
What do they mean when they say message delivery and messages received

I really want to know how much a particular domain I am running is sending and receiving.

Suppose that I am hosting domainB.com does the below mean 
domainB sent out 46 mails ad received 12?

Thanks.



```

Host/Domain Summary: Message Delivery 
--------------------------------------
 sent cnt  bytes   defers   avg dly max dly host/domain
 -------- -------  -------  ------- ------- -----------
     46   248231        0     0.6 s    2.6 s  domainB.com
     22    20449      254    13.9 h   92.4 h  yahoo.com
      5     4537      199    55.0 h   92.0 h  domainC.com
      1      715        0     1.8 s    1.8 s  domainA.com

Host/Domain Summary: Messages Received 
---------------------------------------
 msg cnt   bytes   host/domain
 -------- -------  -----------
     22   187700   yahoo.com
     12    26670  domainB.com
      8    22824   domainA.com
      2     9251   domainC.com

```

---

