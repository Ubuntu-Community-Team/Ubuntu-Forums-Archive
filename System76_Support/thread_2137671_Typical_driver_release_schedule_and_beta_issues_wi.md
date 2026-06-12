---
title: "Typical driver release schedule and beta issues without driver support."
date: 2013-04-21
forum: System76 Support
---

### Post by tonyr2k8 on 2013-04-21
How soon after Ubuntu makes a release does System76 provide drivers?

Everything seemed to work out of the box for Ubuntu 13.04 beta, with the following exceptions.

1 – Bluetooth would work sometimes would work, it would see the device, but would not connect. The function key to turn it on/off would not work. After a suspend/resume would not work at all.

2 – The MIC worked fine unless I did a suspend/resume, then would not work at all after a resume.

---

### Post by Arioch on 2013-04-21
I am also interested in the Sys76 driver release schedule.
Testing 13.04 now on my Gazp6, with Nvidia card. It has been quite painful installing 13.04 on a SSD, plus problems to get the proprietary driver to work properly. 1 out of every 3 times I boot my machine it does not boot into X and freezes. Trackpad does not support scrolling without Syst76 drivers, and a few other glitches, unstable wifi, unreliable suspend, system wise freezes. Hard to tell if that is 13.04 beta failures or something just related to the proprietary drivers, or the lack of sys76 drivers.

Waiting for final release to make a formal impression. So far...not great on that machine, so holding it on my production work system (lemur ultra).
BTW, skype is a true mess. Even with the fix posted in some forums it is very very unstable and micro fails very often.

12.10 works like a charm on my Lemur though. Never been so happy with a release before...prly due to the integrated intel card and not Nvdia binary blobs.

---

### Post by 3Miro on 2013-04-22
> **tonyr2k8 said:**
> How soon after Ubuntu makes a release does System76 provide drivers?


System76 doesn't make any drivers. The so called driver only makes adjustments to the system settings and installs packages and modules as necessary.

The advantage of System76 is that they only sell hardware that has good driver from the manufacturers. However, if Nvidia decides to stop their support in the future, then there is nothing that System76 can do about it.

System76 cannot provide "stable" drivers for a distribution that isn't considered "stable" by Canonical. Sometimes it even takes some time after the official release to get all the bugs cleaned. If you want a stable system, don't upgrade immediately, wait for a while. This is true on any OS and any hardware.

---

### Post by ufugu on 2013-04-22
FWIW, I have not found anything that requires the System 76 driver on my Gazp7 with 13.04.  Everything is working fine without it.

---

### Post by Leslie Dorner on 2013-04-22
I've been told the System76 device driver has nothing to do with the Realtek RTL8411 SD card reader in my Lemur (lemu4) PC; this has been committed upstream to Canonical in Ubuntu 13.04. I've been having problems formatting 128 GB SDXC cards to /ext4 file system with LUKS-1 encryption using Ubuntu 13.04 Alpha, Beta 2, and Release Candidate without the updated System76 device driver. So, I'm waiting for my second RMA for a PNY Technologies 128 GB Class 10 UHS-1 SDXC card to be delivered to my home via UPS Ground this Wednesday or Thursday and then I will wait until Ubuntu 13.04 64 bit and System76 release their official final shipping interim release versions before I try anything else more daring on my existing installation. I don't think I'll format that PNY 128 GB SDXC card. I'll leave it with the default ExFAT file system which Ubuntu 13.04 64 bit supports right out of the box nowadays. I'm going to use it as a portable data drive. It gets 35 MBps read and write performance which is pretty decent. I got it for free from Amazon because they made a mistake with my order.

---

### Post by isantop on 2013-04-23
We've seen many issues with 128 GB cards and LUKS encryption. For this situation, I'm going to say that Ubuntu is having issues with the large cards and encryption. For encryption, I'd recommend using 64 GB cards. There isn't anything we can do driver-wise to fix that.

---

