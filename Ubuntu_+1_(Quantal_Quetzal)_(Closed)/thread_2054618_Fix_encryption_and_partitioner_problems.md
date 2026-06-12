---
title: "Fix encryption and partitioner problems"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by superice on 2012-09-07
First of all, there is one bug that has been mentioned before that I experienced a few times in virtualbox, but then it went away and that is that the step where you must set up the encryption passphrase is empty. It worked for me after about 5 tries. Another thing is that the ubiquity partitioner should be updated. Since there is support for encryption and lvm, the partitioner should support both creating and editing these types of partitions (and not just seeing them). I hope these changes will be put in the final build and I hope you will all enjoy it. I, however, use RAID0 and will stick with my 12.04.1.

P.S. This was in 64-bit. I'm not sure if the bug happens only in 64-bit. Also, I'm not sure if the other variants of ubuntu have this problem (although if they use the same installer, I would suppose they do)

---

