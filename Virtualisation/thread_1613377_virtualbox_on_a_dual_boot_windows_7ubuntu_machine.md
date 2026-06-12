---
title: "virtualbox on a dual boot windows 7/ubuntu machine?"
date: 2010-11-04
forum: Virtualisation
---

### Post by robertbub on 2010-11-04
So, I've had endless problems trying to get the Windows 7 installed in a separate partition booting (as uest) with VirtualBox running on Ubuntu 9.10 Karmic (as host).  It always blue screens, even if I try the old "repair via the Repair Rescue Restore CD" trick.

My new plan is to run the Ubuntu partition as guest from Windows 7 as host.

I have looked and looked on the web and cannot find anything that is recent (the documents seem to be referring to old versions of grub, I think).

Does anyone know how to run Ubuntu guest from Windows 7 host in a dual-boot environment?  If you do not know personally, is there a web site which says how to do this?  If you don't know that, is there a web search which will reveal this information for a recent version of Ubuntu (Karmic; Lucid would probably work, too)?

Thanks.

---

### Post by robertbub on 2010-11-14
I was able to get this going.

At first, I tried grub-mkrescue to create the ISO but I could not get it to work, no matter what I tried.

I finally settled on downloading the SuperGrub CD ISO and using that.  It correctly finds the grub installed on the partition and boots perfectly.

---

