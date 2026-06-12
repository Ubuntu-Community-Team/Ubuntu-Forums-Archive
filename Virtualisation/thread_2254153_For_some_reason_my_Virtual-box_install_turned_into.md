---
title: "For some reason my Virtual-box install turned into a snale"
date: 2014-11-25
forum: Virtualisation
---

### Post by pqwoerituytrueiwoq on 2014-11-25
it is almost as if the HDD speed has dropped by 60% or so on the VM
after looking at dmesg i decided to remove swap and disable ipv6 since they were near the time jump, little to no effect
i tried re-profile ureadahead
here is the bootchart image [http://i.imgur.com/UGkS1Pg.png](http://i.imgur.com/UGkS1Pg.png)
any idea how i can speed this thing up?

---

### Post by slickymaster on 2014-11-25
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by pqwoerituytrueiwoq on 2014-11-25
seems this was not a virtualbox issue, well i suppose technically it was, but not with the vm install
i had terminated a virtualbox to disk image conversion cause it was going to take too long and the system did not like that and it killed my HDD speed, dropping it down to 17MB/s
a reboot fixed it

---

