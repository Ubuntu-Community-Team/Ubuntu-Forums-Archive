---
title: "VirtualBox: Which combination of filesystem is best choice for VM"
date: 2009-10-08
forum: Virtualisation
---

### Post by deadland on 2009-10-08
Hi ubuntufriends,

I would like to setup a VM with ubuntu 9.10 as host and guest. So im wondering which filesystem combination has the best performance. 

For example:

   HOST   GUEST

1) ext4    ext4
2) zfs     ext3


Thanks in advanced

---

### Post by HermanAB on 2009-10-09
IBM JFS is the fastest and most efficient journaling file system.

---

### Post by tkoco on 2009-10-09
I would go with the defaults (#1). The nice thing about VMs is that you can set up multiple VMs with the same OS, but different filesystems. Just a suggestion... Perhaps you would consider doing the honors of testing different FSes in a VM and report back which one gives you the best performance.

> **deadland said:**
> Hi ubuntufriends,

I would like to setup a VM with ubuntu 9.10 as host and guest. So im wondering which filesystem combination has the best performance. 

For example:

   HOST   GUEST

1) ext4    ext4
2) zfs     ext3


Thanks in advanced

---

### Post by deadland on 2009-10-09
@HermanAB: Thanks for your suggestion!

@tkoco: Do you have an suggestion which:

1.) filesystems I should benchmark? Because if do a Test of only three different Filesystems I already have 8 combinations

2.) and which "easy to use" testsuite I should chose 

3.) and which representiv tests I should run

4.) and I'm using an older Laptop. Is this representiv?

5.) and just to verify the "command-line-version" of the alternate cd is the smallest installation of ubuntu, right?

Thanks in advanced

---

