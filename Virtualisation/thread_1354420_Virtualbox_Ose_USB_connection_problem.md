---
title: "Virtualbox Ose USB connection problem"
date: 2009-12-13
forum: Virtualisation
---

### Post by Vinomfire on 2009-12-13
As the title suggested, I am having some problems connecting any USB device in virtualbox ose. I've tried connecting my iPod touch 2. G with 3.0 os and a video recorder. Ubuntu (9.10) recognized both and mounted them, but vb ose didn't recognize either. I just downloaded the vb standard edition from their webstite, but I haven't tried it yet. Should that version work, or do I need to do somthing else. Thanks

---

### Post by gordintoronto on 2009-12-13
You need to add yourself to the virtualboxusers group.

---

### Post by ubu-for on 2009-12-14
> **Vinomfire said:**
> As the title suggested, I am having some problems connecting any USB device in virtualbox ose. I've tried connecting my iPod touch 2. G with 3.0 os and a video recorder. Ubuntu (9.10) recognized both and mounted them, but vb ose didn't recognize either. I just downloaded the vb standard edition from their webstite, but I haven't tried it yet. Should that version work, or do I need to do somthing else. Thanks

You'll probably need the closed source version.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

> Closed-source features

The following list shows the enterprise features that are only present in the closed-source edition. Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

    * Remote Display Protocol (RDP) Server 

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP 

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

---

### Post by Vinomfire on 2009-12-14
i got it to work thanks!

---

### Post by Flecko on 2009-12-15
Mind telling everyone how Vinomfire? It would certainly help anyone else having this problem out.

Thanks!

---

### Post by Gina on 2009-12-18
> **Flecko said:**
> Mind telling everyone how Vinomfire? It would certainly help anyone else having this problem out.

Thanks!Yes please, from me too :)  

I am using the closed source VB hosted by Ubuntu 9.04 (Jaunty) and have added myself to the VB users group.  I have set up filters for a couple of USB devices which the host system found correctly.  I have installed Windows XP as guest.  In the Machine menu the USB box is empty.  There is space for about six entries but the box is blank.

I would very much appreciate some help, please :)

---

### Post by Gina on 2009-12-19
UPDATE :-  It's suddenly started working :lolflag:

I don't think I've done anything to make it work.  All I've done in the meantime is to reboot several times and tried to install the Lucid development version.  Plus re-running VB and Win XP.  

It is now detecting my USB memory stick and more importantly my weather station connected via USB.  My whole reason for using VB and XP is to run Cumulus which is Windows software for my weather station (taking readings and uploading data and graphs to my weather website).  There is no Linux software as yet.  And AFAIK WINE doesn't support USB.

---

