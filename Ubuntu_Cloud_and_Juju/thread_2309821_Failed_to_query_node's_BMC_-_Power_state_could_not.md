---
title: "Failed to query node's BMC - Power state could not be queried: connection timeout"
date: 2016-01-13
forum: Ubuntu Cloud and Juju
---

### Post by sakura2 on 2016-01-13
Hello,

I have 4 Dell PowerEdge 1950 machines 16GB RAM. I have installed maas version 1.8.3 ubuntu 15.10 on one of machine which acts as a cluster controller.

I PXE boot the nodes. They come up and power down as expected. They have 14.04 boot image installed. 

I have 1 NIC. The network interface manages both DHCP and DNS. I have specified the dynamic ip and static ip ranges.

The node is auto detected. However, when I try to commission nodes I get this ERROR: [COLOR=#333333][FONT=Ubuntu]Failed to query node's BMC - Power state could not be queried: connection timeout

The default power type is set to ipmi with IPMI 2.0 power driver. IP address, power user and power password fields are auto filled  in node settings. 


I have also tried the same set up with ubuntu 14.04 and get the same error.  Any help that would help me commission these nodes is much appreciated.[/FONT][/COLOR]

---

### Post by urbasius on 2016-01-27
Hello. We are also having similar issues. Our setup consists of 5 Dell servers. 2 of them are 1950 and others are 2950. The funny thing is one of the servers runs and works without problem, while others are having issues. Very frustrating experience.

---

