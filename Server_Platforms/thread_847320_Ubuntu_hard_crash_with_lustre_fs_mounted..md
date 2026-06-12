---
title: "Ubuntu hard crash with lustre fs mounted."
date: 2008-07-02
forum: Server Platforms
---

### Post by Robstarusa on 2008-07-02
Hi guys,

I have a hardy install.  The lustre ubuntu packages do not work with this.  Recently Lustre 1.6.5 came out and the patchless client works with kernel source 2.6.22.14.

If I compile this source under Ubuntu (.config generated from "make defconfig"), it seems to work OK.

If I compile this source copying the 2.6.24.19-server .config to the /usr/src/linux-2.6.22.14 directory and recompile, install, etc, I can mount lustre shares, but issuing "du" on a directory crashes the entire box with a register dump.

Anyone know how to start troubleshooting this?

---

### Post by windependence on 2008-07-02
Why do you want to do this? Are you bulding a 10,000 node cluster?

-Tim

---

### Post by Robstarusa on 2008-07-03
> **windependence said:**
> Why do you want to do this? Are you bulding a 10,000 node cluster?

-Tim

Yes.

Do you have a solution?

---

### Post by Robstarusa on 2008-07-23
> **Robstarusa said:**
> Yes.

Do you have a solution?

solution is to turn off CONFIG_SLUB in the ubuntu .config before recompiling the kernel.

now it works!

---

### Post by Robstarusa on 2008-10-07
> **Robstarusa said:**
> solution is to turn off CONFIG_SLUB in the ubuntu .config before recompiling the kernel.

now it works!

Followup:

Not a single crash on 5 client notes for 2+ months.

---

### Post by raq on 2008-11-28
I am starting a 76 nodes cluster with Ubuntu 8.04 + lustre + Infiniband.

Have you got lustre in production or you are just testing it?

Regards

---

