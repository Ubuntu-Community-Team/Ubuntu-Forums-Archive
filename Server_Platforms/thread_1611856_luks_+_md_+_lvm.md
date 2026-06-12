---
title: "luks + md + lvm"
date: 2010-11-02
forum: Server Platforms
---

### Post by mdojka on 2010-11-02
I had this setup working in centos 5.5 and decided to switch to ubuntu 10.10 server last night.  I haven't been able to get it to work since.  I have 2 root drives (sdg and sdh).  /boot is md0 (sdg1 and sdh1) raid 1 volume and unencrypted.  md1 (sdg2 and sdh2) is a luks encrypted raid 1 volume.  Both md0 and md1 have the 0.90 metadata format.  Once md1 is unlocked, it contains vg0 which houses all of the lv's for the root disks.  During the server install, while it detected the raid, it did not prompt me for a password. So I had to manually unlock md1 and activate the lv's before scanning the disks.  This worked and I was able to install the os.  When I try to boot up, grub loads and after a minute or two I get an initramfs prompt complaining about lv-root not being available.  I never got a luks password prompt, so the raid was never unlocked.  I did some searching and tried to rebuild the initramfs image, however it made no changes.  If I boot into rescue mode I can manually unlock and mount the lv's, so luks and lvm aren't messed up.  I'm at a loss at this point.

---

