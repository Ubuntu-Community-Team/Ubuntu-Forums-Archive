---
title: "VMware ESXi 6 + Ubuntu 14.04, pci passthrough problem"
date: 2016-03-09
forum: Virtualisation
---

### Post by PZ91 on 2016-03-09
Hi,
I installed on my server ( Fujitsu PRIMERGY TX2540 M1 ) VMware ESXI 6.0.0 and I created virtual machine for Ubuntu 14.04.
I set pci passthrough options and a device visible on Ubuntu, but I have problem with driver (driver can't see the device).

lspci -v:
> 
0b:00.0 Signal processing controller: Euresys S.A. Device 0503 (rev 03)
           Physical Slot: 192
           Flags: fast devsel, IRQ 19
           Memory at fd200000 (64-bit, non-prefetchable) [size=2M]
           Memory at eb800000 (64-bit, prefetchable) [size=2M]
           Memory at ea000000 (64-bit, prefetchable) [size=16M]
           Capabilities: [40] Power Management version 3
           Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
           Capabilities: [70] Express Endpoint, MSI 00
           Capabilities: [100] Advanced Error Reporting
           Capabilities: [140] Virtual Channel


Two last lines on dmesg:
> 
[24.353905] UxH264: StopBoardSctPolling: The SCT memory is still polled by the board !!!
[24.536254] UxH264: probe of 0000:0b:00.0 failed with error -1


Any help would be approciated.

---

