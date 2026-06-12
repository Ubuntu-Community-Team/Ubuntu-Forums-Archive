---
title: "Getting consistent md5sum values when remastering a distro"
date: 2010-11-01
forum: The Cafe
---

### Post by jhsu802701 on 2010-11-01
On two different occasions, I installed a Linux distro (antiX Linux versin on M8.5 base version for a 686 processor) to a VirtualBox hard drive and then immediately remastered the distro to produce an ISO file. On both occasions, the md5sum values did not match the original md5sum value, and the results didn't even match each other.

Is this normal? Obviously, if even one tiny and insignificant thing changes in one of the files that are part of the distro, the md5sum value will change. But doesn't this make it tricky for a team of developers to make sure that they are all on the same page?

---

### Post by NovaAesa on 2010-11-01
If one single bit changes, you can expect about half of the bits in the md5 sum to toggle, resulting in a radically different md5 sum. Developers working in a team would be using some sort of version control, so wouldn't run into this sort of problem. The md5 sums are only for distribution as a sanity check that a downloaded file hasn't been corrupted.

---

### Post by jhsu802701 on 2010-11-01
Thanks.  Then how do you implement version control for a whole operating system, as opposed to a single document?  I'm using VirtualBox, and I've discovered the great feature called snapshots.

---

