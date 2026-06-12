---
title: "ext3/ext4 full disc encryption performance"
date: 2010-02-03
forum: Security
---

### Post by DZ* on 2010-02-03
I've been using full disk encryption with luks on two Dell laptops for about 2.5 years. One is 64 bit Fedora (upgraded to 12), another is 32 bit Ubuntu (upgraded to 9.10), both were ext3, until recently.

Over time, performance degraded substantially, especially on Fedora, which was put to a heavier use. That laptop has 4 Gb RAM, two 2.5 GHz T9300 CPUs, and 56 Gb of free space.

It was especially unbearable after a reboot. Programs like firefox and thunderbird would take close to a minute to start when ran for the first time after a boot. The login process was painfully slow, and some Gnome applets (e.g. Tomboy notes, keyboard layout switcher) would fail to load on the first login, with an error. I experienced this problem on both laptops with full encryption.

I had to log out and relogin to make the applets appear. I tried various boot and mount options and was thinking about switching to ecryptfs (encrypted home).

I also use 3 desktops with no encryption and a netbook with ecryptfs on /home, which all work fine. All are Dell, 2 Ubuntu and 2 Fedora. The Gnome applets problem seems to be due to slowness of the installs with the full disk encryption.

The last thing I tried is to migrate ext3 to ext4.  I also converted /home, /usr, /opt to extents, following

[http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem](http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem)

That seemed to do the trick. Gnome applets now load fine on both laptops, and startup time is back to tolerable.

Is this a typical experience: ext3 performance degradation with time and a much better performance with full disk encryption once ext3 is migrated to ext4?

---

### Post by bodhi.zazen on 2010-02-03
Most people feel ext4 and ext2 perform better then ext3.

I notice a huge difference on my netbook , but not as much on my workstation. Of course my workstation has more ram and a far superior CPU ...

---

