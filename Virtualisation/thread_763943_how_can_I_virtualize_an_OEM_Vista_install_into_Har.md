---
title: "how can I virtualize an OEM Vista install into Hardy?"
date: 2008-04-23
forum: Virtualisation
---

### Post by srllorente on 2008-04-23
Hi folks,

I am seeking your advice to set up the best configuration around:

* having Hardy as my primary OS in my brand new laptop
* keeping the Vista Professional OEM installation that I had to pay
* being able to run Vista onto Hardy by means of a virtual machine so that I can run this particular program only available on Windows that I like a lot.

At the moment, the new laptop is still in the box, so the OEM installation has not been "touched" (activated,...etc).

I am not sure what Virtual machine to use.

What i had in mind is

1.- use a hardy live CD to boot and repartition disk into 3 partitions: 1 for the Vista OEM installs as it comes, 2 for the hardy boot, 3 for my personal data
2.- have a virtual machine installed into hardy (which one?)
3.- have the OEM installs of vista installed into the Virtual Machine (is this doable?)
4.- keep the oem Vista partition as it is for good and use the installed VM Vista entity.

now I need some help in fine tunning the idea and take it to practice, as last time I messed around with partitioning in linux it was black&white :)

Thanks in advance
San.

---

### Post by Chayak on 2008-04-24
That will be an issue as VMware/virtualbox will appear as different hardware to the vista install and it will normally crash due to the lack of drivers.  If it were to work then Vista would likely deauthorize as the hardware had changed from it's known configuration.

on a side note...
Vista is a memory hog as well which doesn't lend to virtualization much.  It's already poor performance just gets worse when virutalized.  XP would be a better choice as I've used images with 256mb of ram allocated to them and it worked fine though I'll normally give an image at least 512mb.

---

