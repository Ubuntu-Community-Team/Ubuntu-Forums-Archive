---
title: "URGENT: Ubuntu Server 9.10 on Dell PowerEdge R410?"
date: 2009-12-02
forum: Server Platforms
---

### Post by yellowtip on 2009-12-02
Hi,

We're about to place an order for a Dell PowerEdge R410 rack server.

Specs:
- 2x Intel® Xeon® E5520, 2.26Ghz, 8M Cache, Turbo, HT, 1066MHz Max Mem
- 8GB Memory (4x2GB), 1066MHz, Dual Ranked RDIMMs for 2 Processor, Mirror
- Add-in SAS6/iR (SATA/SAS Controller) which supports 2 Hot-Plug Hard Drives - RAID 1
- 2x 73GB 10K RPM Serial-Attach SCSI 2.5" Hybrid Hot Plug Hard Drive in 3.5" Carrier

I was originally planning to install Ubuntu Server 8.04LTS on it, but I read some posts saying that it's not compatible with the DVD drive and the NIC. They make a very short mention that Ubuntu 9.04 does work out of the box on this server.

Could anybody on this forum please confirm that Ubuntu 9.10 Server (or 9.04 for that matter) will work out of the box with this server?

Please note the SAS6/iR RAID card. I read many articles that Ubuntu 8.04LTS supports this card without any problems. Can anybody confirm that Ubuntu 9.10 Server also supports this card?

We standardize on Ubuntu Server in our company, so Redhat or Suse distro's are not an option. As this will be a significant investment, I'd really appreciate anybody's feedback.

Thanks in advance!

---

### Post by yellowtip on 2009-12-02
bump

---

### Post by apel_2804 on 2009-12-02
> **yellowtip said:**
> Hi,

We're about to place an order for a Dell PowerEdge R410 rack server.

Specs:
- 2x Intel® Xeon® E5520, 2.26Ghz, 8M Cache, Turbo, HT, 1066MHz Max Mem
- 8GB Memory (4x2GB), 1066MHz, Dual Ranked RDIMMs for 2 Processor, Mirror
- Add-in SAS6/iR (SATA/SAS Controller) which supports 2 Hot-Plug Hard Drives - RAID 1
- 2x 73GB 10K RPM Serial-Attach SCSI 2.5" Hybrid Hot Plug Hard Drive in 3.5" Carrier

I was originally planning to install Ubuntu Server 8.04LTS on it, but I read some posts saying that it's not compatible with the DVD drive and the NIC. They make a very short mention that Ubuntu 9.04 does work out of the box on this server.

Could anybody on this forum please confirm that Ubuntu 9.10 Server (or 9.04 for that matter) will work out of the box with this server?

Please note the SAS6/iR RAID card. I read many articles that Ubuntu 8.04LTS supports this card without any problems. Can anybody confirm that Ubuntu 9.10 Server also supports this card?

We standardize on Ubuntu Server in our company, so Redhat or Suse distro's are not an option. As this will be a significant investment, I'd really appreciate anybody's feedback.

Thanks in advance!

Significant Investment? R410?

However, 9.10 will work. The older Debian / Ubuntu versions did not have the firmware for that ... broadcom NIC's but this is no issue in 9.10. The SAS6/iR is a LSI 1068 controller and will work fine (so far, the PERC6 (also LSI) is much faster and hase lot more RAID Option, also kewl stuff like foreign config handling and RAID retagging). Note that the R410 is loud you don't want to use it under your desk. (because it's a rack chassis it shouldn't stand there anyway)

---

### Post by yellowtip on 2009-12-02
> **apel_2804 said:**
> Significant Investment? R410?

However, 9.10 will work. The older Debian / Ubuntu versions did not have the firmware for that ... broadcom NIC's but this is no issue in 9.10. The SAS6/iR is a LSI 1068 controller and will work fine (so far, the PERC6 (also LSI) is much faster and hase lot more RAID Option, also kewl stuff like foreign config handling and RAID retagging). Note that the R410 is loud you don't want to use it under your desk. (because it's a rack chassis it shouldn't stand there anyway)

Thank you so much for your prompt and very useful information.

Glad to hear that 9.10 will work just fine out of the box.

---

