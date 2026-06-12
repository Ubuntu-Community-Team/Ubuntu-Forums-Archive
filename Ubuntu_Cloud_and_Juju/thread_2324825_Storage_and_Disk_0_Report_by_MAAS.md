---
title: "Storage and Disk 0 Report by MAAS"
date: 2016-05-16
forum: Ubuntu Cloud and Juju
---

### Post by Maile_Halatuituia on 2016-05-16
After Commission my two nodes, CPU and RAM is happily discovered and report by MAAS but my Disk and Storage are both 0. I believe there are tons of people going through the same error but none of the discussion has help my situation. Can someone please shed some light way forward as i have for sometime now ...thanks

---

### Post by phalen on 2016-05-21
In the maas interface you must not check the keep disk configuration while initial commissioning occors.  it will leave the disk section blank since that is what it originally was. took me a few days to figure that out.

---

