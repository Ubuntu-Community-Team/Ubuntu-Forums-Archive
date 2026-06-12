---
title: "MAAS region controller as http proxy"
date: 2016-09-14
forum: Ubuntu Cloud and Juju
---

### Post by ageiger-at-intellic on 2016-09-14
I'm setting up a MAAS 2 cloud, and want to use my region controller as the bridge for the cloud to the internet. That is, NIC 1 on the region controller is the only card with access to the office's internet connection. I have a managed switch attached to the region controller's NIC 2, and that switch is connected to NIC 1 and 2 of the other 5 machines (and their IPMI connections).

Do I just adjust the Squid proxy that MAAS installs to allow all the subnets in the cloud access?

Full disclosure: I thought I had this lic'd before (see my [SO question/answer]("http://serverfault.com/a/801250/371238")), but I'm still getting some issues. Basically, I'm not really sure how to even troubleshoot this, since I can't deploy to any of the machines now (but they were commisioned). Might be a bug in MAAS 2, or maybe Juju 2 botched a config somewhere, or maybe Squid was never really right?

Any advice on making this sort of layout work would be incredibly appreciated!

```

Office WAN
   |
NIC 1
   |
<MAAS region controller>
         |
      NIC 2
         |
      Managed Switch
         |
      (All node's NIC 1 and NIC 2)
```

---

