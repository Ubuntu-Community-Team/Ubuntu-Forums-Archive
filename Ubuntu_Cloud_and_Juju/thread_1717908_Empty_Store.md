---
title: "Empty Store"
date: 2011-03-30
forum: Ubuntu Cloud and Juju
---

### Post by shahin on 2011-03-30
I just implemented a new UEC instance, and looking under the "store" tab of the management interface, I do not see any images.  Do I need to create my own images?  Should there be some images by default?

---

### Post by kim0 on 2011-03-31
Hi,
There should be some images yes, please check if the CLC machine has unrestricted internet access. Can you browse to google.com from that machine for example ?

sudo apt-get install elinks -y ; elinks --dump google.com

---

### Post by shahin on 2011-03-31
I am behind a proxy, but I can do apt-get just fine.  I think I have configured proxy just fine.  How do I update the files that should be in the store please?

---

### Post by kim0 on 2011-04-02
No idea how to directly do that .. however you might want to download the images manually then publish them to the cloud controller .. check this out
[https://help.ubuntu.com/community/UEC/BundlingImages](https://help.ubuntu.com/community/UEC/BundlingImages)

---

