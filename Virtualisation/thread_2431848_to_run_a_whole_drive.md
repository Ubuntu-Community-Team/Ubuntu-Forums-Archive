---
title: "to run a whole drive?"
date: 2019-11-22
forum: Virtualisation
---

### Post by Skaperen on 2019-11-22
for the purpose of having a virtual machine that has 2 drives, the 2nd from a copy of an Ubuntu ISO made to appear as a hard drive, and the 1st, attached to the whole 2nd drive (SSD) of my laptop, is one of the few VM software choices better or best for this, these days?  my _first intention_ is to install the various editions of 18.04 on that 2nd drive to be ready to boot it on the real laptop and to test the procedures and work on automating it.  that means there must be exact identity mapping of virtual sectors to real sectors for that drive attachment (not any drive image encoding).  i want to be able to simply configure the 2nd virtual drive to the .iso _file_ (i can rename it, symlink it, or copy, as needed) and configure the 1st virtual drive to the 2nd real drive (/dev/sdb) (copying it or using a file is not an option).

---

