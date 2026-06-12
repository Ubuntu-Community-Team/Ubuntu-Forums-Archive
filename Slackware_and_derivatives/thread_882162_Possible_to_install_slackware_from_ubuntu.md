---
title: "Possible to install slackware from ubuntu?"
date: 2008-08-06
forum: Slackware and derivatives
---

### Post by super.rad on 2008-08-06
I've got an empty partition and fancy having a go with slackware. Before i download the cd's or dvd I was wondering if its possible to install from ubuntu? If so are there any guides on how to do it?
If it's not possible, do I need all 3 cd's for the installation? (I want the base system and KDE4)

---

### Post by GreenN00b on 2008-08-06
This is a possible solution, I do not know if it works:
- download a disk image for slackware.com & packages needed for installation
- mount it and copy the contents to the new partition
- edit grub configuration to add the new partition to the boot menu
- attempt to boot from the new partition
If this works you should be able to continue whit the rest of the installation steps.

---

### Post by kpkeerthi on 2008-08-07
Yes. This is possible along the same lines GreenN00b has put down. A google search on the topic should get you what you are looking for.

---

### Post by super.rad on 2008-08-11
Thanks i'll get round to trying this soon, have to make a new partition though as I installed Arch and loving it at the moment

---

### Post by andrew.46 on 2008-08-11
Hi:

> **super.rad said:**
> I've got an empty partition and fancy having a go with slackware. Before i download the cd's or dvd I was wondering if its possible to install from ubuntu? If so are there any guides on how to do it?
If it's not possible, do I need all 3 cd's for the installation? (I want the base system and KDE4)

3 cds is all that is needed but if you have the bandwidth the dvd is a better optiion as this will give you access to the source files and the slackbuild scripts used to assemble the packages.

Best way may be to install slackware to your spare partition and install slackware's lilo to the root of that partition and then chainload from your ubuntu grub on the mbr.

  Andrew

---

