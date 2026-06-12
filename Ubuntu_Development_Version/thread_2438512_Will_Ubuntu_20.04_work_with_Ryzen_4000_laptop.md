---
title: "Will Ubuntu 20.04 work with Ryzen 4000 laptop?"
date: 2020-03-13
forum: Ubuntu Development Version
---

### Post by greg2lapa on 2020-03-13
Came across this Phoronix article: [https://www.phoronix.com/scan.php?page=news_item&px=Renoir-Graphics-Not-Experiment](https://www.phoronix.com/scan.php?page=news_item&px=Renoir-Graphics-Not-Experiment)

Does this mean there's no hope of being able to run Ubuntu 20.04 (which I believe is using the 5.4 kernel) on a newly purchased Thinkpad with Ryzen 4000 CPU?

---

### Post by oldfred on 2020-03-13
Does Dell already have that chip in a PC?

It is normal that kernel, drivers & support software take a bit to be fully included in a distribution to support the very newest hardware. Future updates will include newer kernels. 

You can add your own kernel, the Phoronix site often uses a distribution but adds a newer kernel for testing.

For the older distributions, this shows how kernels get updated.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by slickymaster on 2020-03-13
*Thread moved to **Ubuntu Development Version**.*

---

### Post by Yellow Pasque on 2020-03-13
> **greg2lapa said:**
> Does this mean there's no hope of being able to run Ubuntu 20.04 (which I believe is using the 5.4 kernel) on a newly purchased Thinkpad with Ryzen 4000 CPU?

Your options:
1. Wait for 20.04.2, which will have a newer kernel
2. Use a newer kernel with 20.04
3. Boot with the experimental flag if you stick with the stock kernel (assuming Canonical doesn't backport/patch the change in the stock kernel). It doesn't guarantee it'll be bug free, but nothing is guaranteed for that.

---

### Post by kurt18947 on 2020-03-21
> **greg2lapa said:**
> Came across this Phoronix article: [https://www.phoronix.com/scan.php?page=news_item&px=Renoir-Graphics-Not-Experiment](https://www.phoronix.com/scan.php?page=news_item&px=Renoir-Graphics-Not-Experiment)

Does this mean there's no hope of being able to run Ubuntu 20.04 (which I believe is using the 5.4 kernel) on a newly purchased Thinkpad with Ryzen 4000 CPU?

If you already own the machine why not try a live USB version? No risk there AFAIK. I can say that 20.04 is the first release that works as expected with a Ryzen 3 2200G/Vega8 graphics. If Live 20.04 works maybe install on a separate partition? Or a totally separate hard drive if the hard drive is readily accessible on your Thinkpad. I'm not familiar with newer Thinkpad models.

---

