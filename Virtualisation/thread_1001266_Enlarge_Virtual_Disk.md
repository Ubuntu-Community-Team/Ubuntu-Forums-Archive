---
title: "Enlarge Virtual Disk"
date: 2008-12-03
forum: Virtualisation
---

### Post by johnmata on 2008-12-03
Hi,

I am running Virtual Box on Windows, and in the Virtual Box I am running Ubuntu.  I have recently run out of 'virtual' hard drive space.  Is there a way to enlarge the virtual hard drive?  

Kind regards,
John

---

### Post by stinger30au on 2008-12-03
i assume you selected a static hdd size and not a dynamic hdd size (resizeable)

in that case if you have a static hdd, your pretty much stuffed

i suggest if you need a bigger hdd, create another hhd and make it a dynamic and add it is a second hdd


or your going to have to create a new dynamic resizing hdd and reinstall the os from scratch

---

### Post by bodhi.zazen on 2008-12-04
Yes you can do this from the command line, at least on Linux you can.

[http://www.linux.com/feature/151029](http://www.linux.com/feature/151029)

You will need to look up the Windows commands, perhaps in the VirtualBox documentation (PDF).

---

### Post by HotShotDJ on 2008-12-04
> **bodhi.zazen said:**
> Yes you can do this from the command line, at least on Linux you can.

[http://www.linux.com/feature/151029](http://www.linux.com/feature/151029)bodhi.zazen -- Maybe I've completely lost my mind (always a possibility) but I don't see anything from that link about increasing the size of a virtual disk.

---

### Post by bodhi.zazen on 2008-12-04
> **HotShotDJ said:**
> bodhi.zazen -- Maybe I've completely lost my mind (always a possibility) but I don't see anything from that link about increasing the size of a virtual disk.

:lolflag: It has been a while since I played with resizing a disk, looks like that link does not answer the question.

Probably easiest thing is to make a new disk, mount it in the guest, and copy the partition with dd or gparted.

---

### Post by HermanAB on 2008-12-04
I always keep the VM as small as possible and mount all the application data on the host (or somewhere else) using NFS.  That way, it is easy to copy or backup the VM.

Cheers,

Herman

---

