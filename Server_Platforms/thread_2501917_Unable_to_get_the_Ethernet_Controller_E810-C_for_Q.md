---
title: "Unable to get the Ethernet Controller E810-C for QSFP installed in the Ubuntu 24.04"
date: 2024-10-26
forum: Server Platforms
---

### Post by prabhu20 on 2024-10-26
Hi all,

I'm having trouble getting the Ethernet Controller E810-C for QSFP installed on my Ubuntu 24.04 server. I downloaded the Intel ice driver and compiled it, but the controller is still not appearing.

lspci output:

lspci |grep -i e810
10006:0a:00.0 Ethernet controller: Intel Corporation Ethernet Controller E810-C for QSFP (rev 02)
10006:0a:00.1 Ethernet controller: Intel Corporation Ethernet Controller E810-C for QSFP (rev 02)


modules optput:

modinfo ice
filename:       /lib/modules/6.8.0-47-generic/updates/drivers/net/ethernet/intel/ice/ice.ko
firmware:       updates/intel/ice/ddp/ice.pkg
version:        1.15.4
license:        GPL v2
description:    Intel(R) Ethernet Connection E800 Series Linux Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     9FABCE8C94FD67853204970
alias:          pci:v00008086d00001888sv*sd*bc*sc*i*
alias:          pci:v00008086d000012DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000012DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000012DDsv*sd*bc*sc*i*
alias:          pci:v00008086d000012D8sv*sd*bc*sc*i*
alias:          pci:v00008086d000012DCsv*sd*bc*sc*i*
alias:          pci:v00008086d000012D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000012D3sv*sd*bc*sc*i*
alias:          pci:v00008086d000012D2sv*sd*bc*sc*i*
alias:          pci:v00008086d000012D1sv*sd*bc*sc*i*
alias:          pci:v00008086d0000579Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000579Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000579Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000579Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000151Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000124Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000124Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000124Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000124Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000189Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001899sv*sd*bc*sc*i*
alias:          pci:v00008086d00001898sv*sd*bc*sc*i*
alias:          pci:v00008086d00001897sv*sd*bc*sc*i*
alias:          pci:v00008086d00001894sv*sd*bc*sc*i*
alias:          pci:v00008086d00001893sv*sd*bc*sc*i*
alias:          pci:v00008086d00001892sv*sd*bc*sc*i*
alias:          pci:v00008086d00001891sv*sd*bc*sc*i*
alias:          pci:v00008086d00001890sv*sd*bc*sc*i*
alias:          pci:v00008086d0000188Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000188Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000188Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000188Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000188Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000159Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000159Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001599sv*sd*bc*sc*i*
alias:          pci:v00008086d00001593sv*sd*bc*sc*i*
alias:          pci:v00008086d00001592sv*sd*bc*sc*i*
alias:          pci:v00008086d00001591sv*sd*bc*sc*i*
depends:        gnss
retpoline:      Y
name:           ice
vermagic:       6.8.0-47-generic SMP preempt mod_unload modversions 
parm:           debug:netif level (0=none,...,16=all) (int)

-----
uname -a
Linux 6.8.0-47-generic #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 21:40:26 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

------



After downloading the drivers from Intel, I ran make install and modprobe, but I'm still not getting any output in ifconfig.

---

