---
title: "VMware and Vista Partitions"
date: 2009-01-24
forum: Virtualisation
---

### Post by jaminux on 2009-01-24
Hi everyone,

I would like to get VMware Workstation or Server working with my Windows partition rather than with a virtual pc inside my Ubuntu partition (both 64 bit versions).

I have failed to find any clear instructions on how to do this specifically with Vista and Linux. The instructions I found on the VMware site were very unhelpful and ambiguous.

Has anyone got any suggestions?

Cheers,
James

---

### Post by HermanAB on 2009-01-24
Just look though the other threads.  It is a common question.

---

### Post by dcstar on 2009-01-25
> **jaminux said:**
> Hi everyone,

I would like to get VMware Workstation or Server working with my Windows partition rather than with a virtual pc inside my Ubuntu partition (both 64 bit versions).
........

Apart from the dangers that are identified by using things this way, I found it easier to use the free VMWare tool to convert a running Windows system into a VM and then use that.

I rarely ever boot my original Windows partition any more, it is far easier to just fire up the VM inside Ubuntu.

---

### Post by veloce on 2009-01-25
> **jaminux said:**
> Hi everyone,

I would like to get VMware Workstation or Server working with my Windows partition rather than with a virtual pc inside my Ubuntu partition (both 64 bit versions).

I have failed to find any clear instructions on how to do this specifically with Vista and Linux. The instructions I found on the VMware site were very unhelpful and ambiguous.

Has anyone got any suggestions?

Cheers,
James

One suggestion: don't use VMWare Server 2.0.  This version doesn't support physical hard drives for vms.

---

