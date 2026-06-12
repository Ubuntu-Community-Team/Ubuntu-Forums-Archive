---
title: "vm types"
date: 2011-05-04
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-05-04
I have to know how the vm types are allocated. For example c1.xlarge there wasn't any free resources available. The RAM of NC is 2 GB 

[email]cloud@node:~/.euca[/email]$ euca-describe-availability-zones verbose
AVAILABILITYZONE    cluster1    10.1.1.222
AVAILABILITYZONE    |- vm types    free / max   cpu   ram  disk
AVAILABILITYZONE    |- m1.small    0002 / 0002   1    192     2
AVAILABILITYZONE    |- c1.medium    0002 / 0002   1    256     5
AVAILABILITYZONE    |- m1.large    0001 / 0001   2    512    10
AVAILABILITYZONE    |- m1.xlarge    0001 / 0001   2   1024    20
AVAILABILITYZONE    |- c1.xlarge    0000 / 0000   4   2048    20

---

### Post by kim0 on 2011-05-06
so it's not enough either because you cannot use the full 2G of ram (since the host itself has to use some ram) or because the 4 cpu cores are not enough

---

