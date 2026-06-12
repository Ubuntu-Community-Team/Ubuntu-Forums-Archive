---
title: "Getting DCA/IOAT working with networking"
date: 2009-12-07
forum: Server Platforms
---

### Post by coffeemug on 2009-12-07
Hi,

I am working towards evaluating DCA/IOAT networking performance. It appears that I've setup the software correctly, but whenever I check /sys/class/dma/dma0chanX/bytes_transferred and /sys/class/dma/dma0chanX/memcpy_count I always get zero.

Here's the relevant dmesg output:

```

[    5.280237] ioatdma 0000:00:0f.0: PCI INT A -> GSI 57 (level, low) -> IRQ 57
[    5.280282] ioatdma 0000:00:0f.0: setting latency timer to 64
[    5.280297] ioatdma 0000:00:0f.0: Intel(R) I/OAT DMA Engine found, 4 channels, device version 0x20, driver version 3.64
[    5.280393]   alloc irq_desc for 95 on node 0[    5.280394]   alloc kstat_irqs on node 0
[    5.280399] ioatdma 0000:00:0f.0: irq 95 for MSI/MSI-X[    5.280401]   alloc irq_desc for 96 on node 0
[    5.280403]   alloc kstat_irqs on node 0
[    5.280406] ioatdma 0000:00:0f.0: irq 96 for MSI/MSI-X
[    5.280408]   alloc irq_desc for 97 on node 0
[    5.280410]   alloc kstat_irqs on node 0
[    5.280412] ioatdma 0000:00:0f.0: irq 97 for MSI/MSI-X
[    5.280413]   alloc irq_desc for 98 on node 0
[    5.280415]   alloc kstat_irqs on node 0
[    5.280418] ioatdma 0000:00:0f.0: irq 98 for MSI/MSI-X
[    5.379772] igb 0000:07:00.0: DCA enabled
[    5.379800] igb 0000:07:00.1: DCA enabled

```

To test, I scp a large file across a high speed network, but bytes_transferred is always zero. I am running 2.6.31-16-server kernel. Could someone advise on how to troubleshoot this?

---

