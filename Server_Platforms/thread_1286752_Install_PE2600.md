---
title: "Install PE2600"
date: 2009-10-09
forum: Server Platforms
---

### Post by richardporter on 2009-10-09
Posted a similar thread in the install forum yesterday, so sorry to those who recognise some of the details. This is an update as much a crosspost.

Trying to install Ubuntu on a Dell PowerEdge 2600. However the CD drive will ONLY boot the OMSA disk, everything else it says media not insterted. 

From OMSA i can install various Win and Redhat servers, but unfortunately there's no option for my to chose my own OS

Looking through the community doccumentation i've had a go with a Smart Boot Manager Floppy, however that just spits out a Disk Error 0x0C

F12 should put the Server into PXE mode, however that's telling me it cant find the right device (NIC i'm guessing)

Do i have many options ?

Cheers

Rich

---

### Post by trundlenut on 2009-10-10
I had problems installing ubuntu on a PE2800 and all it turned out to be was that the cd dive was full of dust and the lens was mucky.  I would read the discs and start to install but then fail randomly, I tried several times before I thought to chek the CD drive.

I also changed the option in the BIOS for OS installation mode, I don't think it was actually needed though as it does is limit the memory usage to 256mb.

---

