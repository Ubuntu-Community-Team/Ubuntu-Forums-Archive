---
title: "I added new disk but it does not show"
date: 2009-05-03
forum: Virtualisation
---

### Post by jdrodrig on 2009-05-03
Hi,

I just added a new disk to an ubuntu guest in Vmware workstation. I selected the default configuration that includes SCSI 0:1 for the second disk and 0:0 for the original one.

I started ubuntu but the second disk is nowhere in sight...

what am I missing? do I need to format this disk or something? how can I make the ubuntu guest to see this second disk?

---

### Post by jdrodrig on 2009-05-04
For completeness,

I found a "solution"...I installed gparted, sudo apt-get install gparted

and ran gparted to label and format ext3 the new disk...and voila it appeared.

There was, of course, the annoying think of making the disk accesible for non-root users. I ran at terminal, 
sudo -i
nautilus

and then right click in the new disk and made my regular user a member of the write/read group.

---

