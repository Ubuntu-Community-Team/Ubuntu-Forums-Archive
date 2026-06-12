---
title: "Hardware suggestions for a dedicated Virtualbox VM server."
date: 2011-08-03
forum: Virtualisation
---

### Post by hotstovejer on 2011-08-03
Hi all,

I am looking to build a dedicated machine just for my vm's, and was wondering what you would build if you wanted a dedicated machine. My thoughts were to go out, get a 6 core AMD cpu, max out the ram on the board, and put 4 small hard drives in there, to minimize machines writing to each other. Learning the in's and out's of virtualization when it comes to hardware needs, so I was just wondering what everyone would do if they wanted something like this in their own personal lab.

---

### Post by sonnet on 2011-08-03
make sure you buy a mainboard with a iommu (or vt-d in case you decide to opt for intel ) support.
Also, sinc eyou want to dedicate the machine to vms, I would choose the new AMD cpus are are to be release in the next weeks: Bulldozer who have 8 cores.

---

