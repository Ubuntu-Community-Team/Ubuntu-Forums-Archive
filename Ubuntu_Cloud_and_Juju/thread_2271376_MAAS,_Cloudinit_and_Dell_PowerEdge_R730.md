---
title: "MAAS, Cloudinit and Dell PowerEdge R730"
date: 2015-03-29
forum: Ubuntu Cloud and Juju
---

### Post by braker2 on 2015-03-29
Hi,

I have a new fleet of Dell PowerEdge servers and for some reason my R703s are freezing during the initial PXE boot into our MAAS environment.

maas version 1.7.2+bzr3355-0ubuntu1~trusty1 is installed on our provisioning host running U14.04.2 x86 (Dell PE 2950, stripped to bare essentials).

BIOS 1.0.2 is installed on the R730.  Configs are 16x16gb ram, PERC330 with 2x300gb SAS RAID1 and 6x1.2tb passthrough in a 16-slot 2u chassis.  Broadcom 1/10GB combo mezz NIC.  iDRAC Enterprise license, bound to the dedicated port.  I am not intending to use Lifecycle Manager.

The first image will stop invariably on these R730 hosts around the configuration of network device security.  It varies on occasion where in the boot process it hangs, which suggests that it's not what I actually see in the display, but a background process.  I would provide a copy/pasta of where it boots, but it seems cloudinit disregards kernel console redirection.  Screenshot is below.

I can reproduce this on two other R730 servers I have.  The interesting thing is that I have six R630 in a similar configuration (24x16gb, PERC330 w/ 2x300gb SAS RAID1 in an eight-bay 1u chassis, same Broadcom 1/10gb mezz as above.  iDRAC Express on dedicated port) but these do not exhibit any of the problems of the R730 and boot properly and completely into a Ready state in the same MAAS server.

Please let me know if there is information that I am missing that can help resolve this issue.

Thank you and best regards,

-Brian

---

### Post by braker2 on 2015-04-10
Thank you for the lack of answers or help.  We will be rebuilding our OpenStack environment in Mirantis instead.

So long and thanks for the fish.  

Sort of.

---

