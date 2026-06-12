---
title: "Infiniband ib_sdp is gone"
date: 2013-02-23
forum: Server Platforms
---

### Post by pneumatic on 2013-02-23
Does anyone know how to get DRBD up and running with sockets direct protocol (sdp)?  There's nothing in the DRBD documentation except to say that it is possible - no examples or otherwise useful information.

One thing that I have noticed is that the "ib_sdp" kernel module is not available.  I am thinking that this was replaced by some RDMA protocol because the converged networking community does not want to admit that Infiniband was the best approach after all (instead of calling it "Infiniband over Ethernet", they call it RoCE).

Neither here nor there, I guess.  I just want to try DRBD with RDMA by any name (sockets direct is fine - just document it somewhere, already).

I have IPoIB up and running just fine.  I don't need help there.  I need to know what kernel modules are necessary and how I need to configure drbd.comf.

Thanks.

---

