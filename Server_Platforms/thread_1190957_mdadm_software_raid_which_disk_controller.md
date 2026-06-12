---
title: "mdadm software raid: which disk controller?"
date: 2009-06-18
forum: Server Platforms
---

### Post by DaMaster_Architect on 2009-06-18
Hi,

recently I have been looking to expand my nas, which is currently running mdadm with 4x 1TB drives in raid 5. The disks are connected using the onboard sata connectors of the motherboard, an Asus A8N-sli. 
This has all gone well so far. However, I am looking to expand the capacity to 16 disks. For this, I need a disk controller to support the aditional disks, obviously.
Here comes the problem. Even after much research, it is not clear to me what disk controller to go for. The disk controllers do not need to have raid support, as I will keep on using mdadm. But they all come with raid support none the less.
Currently, I have eyeballed the following cards:
- Dell perc 5/i. Reported problems of all kinds, warm-boot problems on nforce chipsets
- Adaptec 21610SA. Ubuntu driver support (aacraid?) but low theoretical throughput.
- Raidcore 8-port. EOL, company doesn't exist anymore, no driver support in debian/ubuntu.

The only requirement I set is for the disk controller to be cheap. I'm planning on using Ubuntu server 9.04.

Now my question: do I need additional drivers for one of these cards to simply use it as a disk controller in ubuntu?
What would be wise to pay attention to if looking for a disk controller for software raid in ubuntu, in general?

So the main issue I'm having is which of these cards will work 'out-of-the-box' in ubuntu as a disk controller, no hardraid needed. I hope you can help me out :)

---

