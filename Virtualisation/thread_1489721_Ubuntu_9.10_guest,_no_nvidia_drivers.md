---
title: "Ubuntu 9.10 guest, no nvidia drivers"
date: 2010-05-21
forum: Virtualisation
---

### Post by Ysam on 2010-05-21
Hello,

I wasn't quite sure where to post this but seeing as I am running ubuntu 9.10 inside VirtualBox on a Windows 7 system, this will probably be the right place for my question.

A few days ago I reinstalled windows on my PC and yesterday I installed virtualbox and downloaded an image of ubuntu 10.04.
 
After installing the ubuntu guest on my VM, I discovered that it wasn't detecting any available proprietary drivers. I downloaded a driver off the Nvidia website but I could not install it. I received a message that there was no Nvidia GPU detected.

Thinking it had something to do with the still (slightly) fresh ubuntu 10.04, I downloaded an ubuntu 9.10 image (which has worked previously). But I was surprised to see that the issue was not solved.

I have been googling this issue all morning but I cannot seem to find a solution.

Does anyone have a clue how to solve this?

Thanks in advance.

---

### Post by fjgaude on 2010-05-21
Virtual Machines use their own drivers... you can't load others. That's the way it is, at least for now and has been since the beginning.

---

### Post by TheFu on 2010-05-22
[fjgaude]("http://ubuntuforums.org/member.php?u=236865") tells the truth, not that there was any doubt.

All virtual machines provide a virtual hardware environment to the client operating systems. At this point, video card passthru is not supported by any of the virtualization technologies that I'm aware. In some virtualiation technologies, PCI adapter pass thru can be configured, but that PCI card is not available to any other OS, including the host. It is common to use this method for disk controllers and SAN storage, but I've never heard anyone adding a 2nd PCI video card to a system for client OS use.  Just to clarify further, I've only heard of PCI, not PCIx or PCIe with the passthru.

Anyway, now you have some more terms to throw at google in your quest.

---

