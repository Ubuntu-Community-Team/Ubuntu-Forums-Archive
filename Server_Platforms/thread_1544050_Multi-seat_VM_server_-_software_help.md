---
title: "Multi-seat VM server - software help"
date: 2010-08-02
forum: Server Platforms
---

### Post by charliehorse55 on 2010-08-02
After a total nightmare at my school with our computer lab (Un-standardized hardware/software, meddling kids etc..) I have been looking at upgrading the computer lab to a multi-seat server. 

The lab currently has 18 computers. 

My original idea was to grab the ASUS Dual socket G34 mobo and load it up with 24 cores and 32 GB of memory. However this would introduce a single point of failure and create the need for really  long cables. (30 feet). 

My second plan for hardware was to use two servers, one for each side of the room. This would add redundancy as well as significantly reducing cable length. I figured one 12 core CPU @ 2 GHz with 16 GB of RAM should be able to power 9 computers easily. Especially since 99% of the time the lab is being used for web surfing and word processing. 

For graphics, the motherboard has 4 PCI-E slots, so I can drive up to 8 monitors with standard two display cards, or 16 with quad display dual gpu (yet still single slot) video cards. My problem with graphics is mainly with the software. Can two VMs use the same GPU to power 3D acceleration on their respective monitors? 

For data storage each of the two servers will have 5 250 GB HDs in Raid 5. That will yield 1 TB of total storage and data redundancy. Not to mention the speed increase as the disk load from the 9 users will be spread across 5 drives. 

This computer will run Ubuntu Server 10.04 LTS at it's core. Each seat at this multi-seat computer will have it's own VM running. Some users will be using Windows, some Linux. But all will be VMs. Having all of the computers running VMs will both simplify software installation (install once then clone the VMs) and prevent kids from tampering with the computers, as the VMs can simply be reset nightly. This will also prevent viruses from doing too much damage. (In the past poorly maintained computers have become spam-bots and subsequently gotten our internet temporarily cancelled). 


So now that you have read this grand plan, please comment on any short-comings or other failure points that might possibly arise. 

I also need a lot of help with the software side. I do have a decent amount of linux experience, as well as programming knowledge, however I have never used VMs before. A step by step guide would be nice. (Google wasn't that helpful for me).

---

