---
title: "after clean install -  network cards not installed"
date: 2010-02-10
forum: Server Platforms
---

### Post by es02 on 2010-02-10
I have a Proliant 7000 with 4 interfaces across 2 cards - 3 intel 10/100Tx  and 1 intel 100FX.

During install it detected the 3 tx interfaces - but couldnt see the network - post install the network devices were no longer there, their devices missing from /dev/.

Neither google nor a forum search have been particularly edifying, is this a known issue with any cards? If so is there a known fix?

ifconfig gives me information for loopback only as expected.

---

### Post by es02 on 2010-02-10
Just tried again with the same problem but atleast this time thought to write down what it detected them as: "Intel 82557/8/9/0/1 Ethernet Pro"

I am starting to think this could be a hardware issue.

---

