---
title: "Which kernel for xen on intel"
date: 2013-01-24
forum: Virtualisation
---

### Post by medipick on 2013-01-24
Sorry for this stupid question, but everywhere i find only a Howto, which explains how to install xen with amd64.

sudo apt-get install xen-hypervisor-amd64

But my system is intel-based. Pls can anyone explain me how to install xen on this system?

I tried the above scenario, it works. I can create dom-u's but the thing is, that i can't passthrough a dvb-adapter. It says, that VT-d isn't supported or not enabled - but it is!

What's wrong?

---

### Post by gordintoronto on 2013-01-24
Both Intel and AMD CPUs support "AMD64" programs. AMD invented it, Intel licensed it.

Programs running in a VM use the hardware which the VM defines for them. For example, the VM might tell programs that the video adapter is an Intel GMA 950, even though the the actual hardware video card is Nvidia. The VM doesn't have a dvb adapter.

---

