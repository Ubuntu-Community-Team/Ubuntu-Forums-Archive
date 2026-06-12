---
title: "KVM (Virtual Machine Manager) can't boot from CD"
date: 2011-11-14
forum: Virtualisation
---

### Post by Dale Marthaller on 2011-11-14
I have a KVM Qemu guest (Ubuntu 10.04) installed on a (Ubuntu 11.10) host. It works as expected. Now I need to boot from a CD using gpartd to change a partition size.
 
I can not get the guest host to boot from CD. I have configured the quest to boot from CD and prompt for boot device. The prompt comes up with a couple of options but not mater what I select it boots from disk.
 
How can I get it to boot from CD or from a iso image on the host?

---

### Post by Dale Marthaller on 2011-11-15
I still have not been able to find a solution to this. I have read a bunch of material on using qemu's monitor mode to logically eject and mount the CD but have not been  able to access monitor mode. I have read that it can be triggered by Ctrl-Alt-2 but this doesn't work either.
 
I hope that someone has experience with this issue.

---

