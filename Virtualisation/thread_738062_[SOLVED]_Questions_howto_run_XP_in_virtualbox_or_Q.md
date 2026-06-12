---
title: "[SOLVED] Questions: howto run XP in virtualbox or QEMU"
date: 2008-03-28
forum: Virtualisation
---

### Post by larsdk on 2008-03-28
Hi there,

I need to setup a virtualization of XP and I figured I would use either QEMU or Virtualbox - these are the questions I have:

1) Which of the two is the best one?
2) RAM issues - I only have 512 mb. Is that a problem?
3) There are two versions of Virtualbox - which one is considered to be the best?
4) Is it possible to use my existing XP installation for the virtualization instead of having to install a new, which would take quite some time to configere (and to upgrade with servicepacks).
5) If 4) is not possible, is it then possible to use the same installation CD as the one that I used for my existing windows installation? And would I have to make a seperate partition for the virtualized XP ?


I guess that was it - any help is very appreciated :)
Lars

---

### Post by luisromangz on 2008-03-28
1) VirtualBox, because of features, ease of use, speed, etc.
2) Yes, that is a problem, you should think about buying more ram, so both the guest and the host system have enough ram.
3) The non open-source version has more features. The open source gives you more freedom.
4) VirtualBox is not able to load physical partitions/drives as disks for the virtual machines, but the free (as in free beer) version of VMWare is able to do so.
5) It is possible, but maybe it is not legal to do so. If that bothers you, you should read the Windows XP EULA carefully to find out how many machines can be using the operative system at a given time. You wouldn't need to make a separate partition, virtual hard disks for virtual machines are just files in the host machine file system.

---

