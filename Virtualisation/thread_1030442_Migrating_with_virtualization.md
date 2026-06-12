---
title: "Migrating with virtualization"
date: 2009-01-04
forum: Virtualisation
---

### Post by MTHarden on 2009-01-04
I used to be a professional computer guy and all my friends and family know this. I am most frequently called upon to "speed" up computers because of malware and whatnot.

Recently instead of a litany of sweepers and cleaners and such, I migrated a friend to Ubuntu. This is what I did:

[LIST=1]
[*]I used an Acronis CD to get an image of his WinXP Hard Drive and put it on my USB HDD. (He had used 40GB out of 250GB
[*]I reformatted his computer with Intrepid Ibex and made a 60GB partition for the disk image.
[*]I installed Virtual Box
[*]I used Acronis Universal Restore to restore the disk image into the virtual machine. (The VDI is on that 60GB partition)
[/LIST]

So, all that worked, but I'd like to do it all more ... freely? I mean Acronis is great but is there a FOSS alternative? Was this the right way to go about the above? I suspect I will do similar things for other friends and the future and I'd like to develop some best practices of sorts for it, and I thought I'd ask the community, so... what do you think?

---

### Post by bodhi.zazen on 2009-01-05
There are several ways you can go about it.

IMO the easiest is to just pull the data and then install Ubuntu + VBox, then restore the data to a data partition and do a fresh install of Windows in VBox. Take a snapshot of the fresh install.

Second there are a number of ways to do a physical to virtual migration.

Last you might want to look at partimage.

---

### Post by HermanAB on 2009-01-05
Essentially, you need to use your VM software to create a virtual disk.  Then you can use 'dd' to copy the physical disk partition to the virtual partition.

'Hope that helps!

Herman

---

### Post by Dedoimedo on 2009-01-06
You may want to read this:

Tutorial on free CloneZilla and PartImage:
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

I find CloneZilla to be easier, but that's subjective.

Cheers,
Dedoimedo

---

### Post by bodhi.zazen on 2009-01-06
> **Dedoimedo said:**
> You may want to read this:

Tutorial on free CloneZilla and PartImage:
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

I find CloneZilla to be easier, but that's subjective.

Cheers,
Dedoimedo

Nice tutorials.

Call me old fashioned, but I like partimage :lolflag:

---

### Post by Dedoimedo on 2009-01-06
Thanks!

The beauty about having two programs is that ... you can use both :)
CloneZilla is probably simpler for Windows users, PartImage is the "old school." But it's a good and reliable problem, nevertheless.

Cheers,
Dedoimedo

---

