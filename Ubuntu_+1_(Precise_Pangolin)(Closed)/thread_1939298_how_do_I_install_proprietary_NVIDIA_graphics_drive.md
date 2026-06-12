---
title: "how do I install proprietary NVIDIA graphics driver in Precise?"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by chazinams on 2012-03-11
Every time I boot into Precise, my monitor turns off for about 45 seconds before turning on again and completing the boot process.

I'm hoping installing an NVIDIA proprietary driver for the GPU will fix this and some other graphics issues. How do I do this in Precise?

---

### Post by terry_gardener on 2012-03-11
open dash and type additional drivers it is in there

---

### Post by dino99 on 2012-03-11
sudo apt-get install synaptic
sudo synaptic
- select and purge all the installed nvidia packages
- select and purge all the installed jockey packages

- reinstall dkms nvidia-current nvidia-common nvidia-settings jockey-gtk

sudo jockey-gtk

---

### Post by chazinams on 2012-03-11
well that didn't work.

anybody else got any ideas?

---

