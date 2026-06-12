---
title: "dmatest.ko - how use it?"
date: 2012-11-30
forum: Ubuntu Dev Link Forum
---

### Post by fuzolan on 2012-11-30
I want to initiate a DMA-Transfer for testing. 

I stumbled accross a dmatest.c in the kernel sources (drivers/dma). I compiled a Kernel with this Module and tried it without any params.

```
sudo modprobe dmatest
```and i get with dmesg

```
__dma_request_channel: fail ((null))
```What are the prerequisites for dmatest.ko?
Should I load a special DMA-Engine?z
Is a special param for dmatest.ko required (default should probe anything!?)?

Best Regards
Fuz

---

