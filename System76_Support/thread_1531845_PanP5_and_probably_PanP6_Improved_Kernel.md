---
title: "PanP5 and probably PanP6 Improved Kernel"
date: 2010-07-15
forum: System76 Support
---

### Post by HotShotDJ on 2010-07-15
I have been experimenting with upgrading the Ubuntu 10.04 LTS kernel and found that the latest stable Mainline kernel (2.6.34) improves performance AND corrects some of the power management features on my PanP5.  It may have similar effects on the PanP6, which has very similar hardware.

You'll need to download manually from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/) and get the linux-headers and linux-image for your architecture (for me, I'm using amd64) and also get the linux-headers...all.deb. I find it easiest to install from the command line using the following command:```
sudo dpkg -i linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
```It has been working a treat for me. I highly recommend testing it.  If it causes you problems, just revert back to the regular Lucid kernel and please post your experience here.

---

### Post by marshmallow1304 on 2010-07-15
Excellent; downloading now.  Does it fix the issue wherein the processors are throttled after resuming from suspend?


Edit:  It doesn't appear to.  It does screw up the splash screen (replaces Ubuntu logo and 5 large dots with text saying "Ubuntu 10.04" and 4 small dots), but that's not a big deal.

---

### Post by HotShotDJ on 2010-07-15
> **marshmallow1304 said:**
> Excellent; downloading now.  Does it fix the issue wherein the processors are throttled after resuming from suspend?

Edit:  It doesn't appear to.  It does screw up the splash screen (replaces Ubuntu logo and 5 large dots with text saying "Ubuntu 10.04" and 4 small dots), but that's not a big deal.As you've already discovered, it doesn't solve that issue. Also, I didn't notice the change in the splash-screen... probably because I didn't care about the splash screen anyway. :)

---

### Post by marshmallow1304 on 2010-07-16
It must have something to do with the NVIDIA driver, as I removed it for testing and the splash screen was fine.  I installed it again and the splash screen was back to ugly.  Maybe I'll try the latest version if I get around to it.

I did notice that unplugging/plugging the power source is handled more quickly (i.e. the screen darkens/brightens and the notification bubble appears quicker).

---

