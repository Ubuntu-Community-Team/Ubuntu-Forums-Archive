---
title: "Help with NFS-RDMA"
date: 2011-02-13
forum: Server Platforms
---

### Post by reactive on 2011-02-13
Hi All,

I'm attempting to get NFS-RDMA working on Ubuntu 10.04, I'm very close but I've found a problem I can't seem to solve. 

So far I've -
Installed vanilla 10.04 server
Updated
Installed OFED 1.5.1 - All modules
Setup and tested IP over IB

The nfs share is coming from an OpenSolaris storage box which is setup and ready to go. I've mounted it using TCP only which is working perfect. I now want to use RDMA for an increase in speed but it fails to mount. Message shows -
```
Feb 13 23:55:20 KVM02 kernel: [20368.054223] xprtrdma: disagrees about version of symbol ib_create_cq
Feb 13 23:55:20 KVM02 kernel: [20368.054227] xprtrdma: Unknown symbol ib_create_cq
Feb 13 23:55:20 KVM02 kernel: [20368.054340] xprtrdma: disagrees about version of symbol ib_alloc_fast_reg_page_list
Feb 13 23:55:20 KVM02 kernel: [20368.054343] xprtrdma: Unknown symbol ib_alloc_fast_reg_page_list
Feb 13 23:55:20 KVM02 kernel: [20368.054446] xprtrdma: disagrees about version of symbol rdma_resolve_addr
Feb 13 23:55:20 KVM02 kernel: [20368.054448] xprtrdma: Unknown symbol rdma_resolve_addr
Feb 13 23:55:20 KVM02 kernel: [20368.054554] xprtrdma: disagrees about version of symbol ib_reg_phys_mr
Feb 13 23:55:20 KVM02 kernel: [20368.054556] xprtrdma: Unknown symbol ib_reg_phys_mr
Feb 13 23:55:20 KVM02 kernel: [20368.055060] xprtrdma: disagrees about version of symbol ib_dereg_mr
Feb 13 23:55:20 KVM02 kernel: [20368.055062] xprtrdma: Unknown symbol ib_dereg_mr
Feb 13 23:55:20 KVM02 kernel: [20368.055171] xprtrdma: disagrees about version of symbol ib_query_qp
Feb 13 23:55:20 KVM02 kernel: [20368.055173] xprtrdma: Unknown symbol ib_query_qp
Feb 13 23:55:20 KVM02 kernel: [20368.055281] xprtrdma: disagrees about version of symbol ib_alloc_fmr
Feb 13 23:55:20 KVM02 kernel: [20368.055283] xprtrdma: Unknown symbol ib_alloc_fmr
Feb 13 23:55:20 KVM02 kernel: [20368.055386] xprtrdma: disagrees about version of symbol rdma_disconnect
Feb 13 23:55:20 KVM02 kernel: [20368.055388] xprtrdma: Unknown symbol rdma_disconnect

```A modprobe of xprtrdma shows the same as above in message and also puts out the below in the shell
```
$ sudo modprobe xprtrdma
FATAL: Error inserting xprtrdma (/lib/modules/2.6.32-24-server/kernel/net/sunrpc/xprtrdma/xprtrdma.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```Googling has suggested I recompile the module against the kernel. Is this right and if so, how do I go about recompiling the xprtrdma  module?

Thanks everyone
-Matt

---

