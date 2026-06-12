---
title: "UEC Hardware Requirements Questions"
date: 2010-02-03
forum: Server Platforms
---

### Post by Ithizar on 2010-02-03
Hi, folks. I have two quick questions regarding the hardware requirements for setting up an Ubuntu Enterprise Cloud environment:

1. [This document]("http://www.ubuntu.com/system/files/UbuntuEnterpriseCloudWP-Architecture-20090820.pdf") from the Ubuntu site says, regarding node controllers, that "...the CPU on the Node Controller needs to have either the Intel VT or AMD-V extensions" (Hardware considerations section, page 16). I really haven't found a place that gives a simple summary of the hardware requirements for UEC, as opposed to straight Ubuntu, but do I understand correctly that nodes in the cloud cannot run on any hardware that does not have virtualization technology? We have some servers with Intel VT, but we have several servers without, and I just want to see if that means they are going to be useless as part of our cloud.

2. I'm a little fuzzy on how UEC allocates resources from the cloud to the various server instances. If, for example, we have some physical server nodes that have 64-bit processors with virtualization support, and others that are only 32-bit, and we want to deploy some 64-bit server instances, will we only be able to run as many 64-bit instances as we have 64-bit nodes? What would happen to a 64-bit instance if a key 64-bit node crashed, leaving only 32-bit nodes active in the cloud?

Thanks for any and all help!

- Tom

---

