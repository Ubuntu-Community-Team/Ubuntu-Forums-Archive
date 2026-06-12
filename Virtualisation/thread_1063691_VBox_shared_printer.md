---
title: "VBox shared printer"
date: 2009-02-08
forum: Virtualisation
---

### Post by challenged on 2009-02-08
I am running 8.10 as Host, Vbox 2.1.2 PUEL with XP Home as Guest.
I have a printer attached via USB to the host set as shared and also in the guest as shared.  The printer works from both host and guest except when the guest is still open.  I have to log out of XP so Ubuntu can use the printer otherwise the message I get is 'printer may not be connected'.

Any ideas why?

---

### Post by lime4x4 on 2009-02-08
more then likely your guest os is grabbing the printer. Your guest and host system can't share the same usb device at the sametime

---

### Post by challenged on 2009-02-08
Thanks, any idea how I can share a printer between the guest and the host? I need to achieve a seamless shift between the guest and host both accessing printers and scanner without having to shut the guest down all the time

---

### Post by HotShotDJ on 2009-02-08
> **challenged said:**
> Thanks, any idea how I can share a printer between the guest and the host? I need to achieve a seamless shift between the guest and host both accessing printers and scanner without having to shut the guest down all the timeI've never tried this myself, but you should be able to set up the printer for networking on the host OS.  You need to make sure that it is not grabbed by the guest OS.  I DO know that I have no trouble with my laser printer, which is actually connected to my router via ethernet.  Both my host OS (Ubuntu 8.10) and my guest OS (Vista Home Premium) can see it and use it at the same time.  Take a look at this page to help you set up your printer for sharing across a network: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by challenged on 2009-02-09
Thanks HotshotDJ
I have started heading down that track without a lot of success at the moment.  I have a friend who also has a network printer that seems to work OK so I thought I would investigate.  Thanks for the link.  Lets see if I have any luck.  There are times when ugly Bill starts to look attractive, but then I remember he was ugly in the beginning and I just got used to him.

---

### Post by challenged on 2009-02-09
Well the guest is a greedy little thing  that keeps hold of the printer.  I am not using a router but both you and my friend are and have no trouble so I suspect the issue is that I may need to have the printer networked through a router although I can't understand why that should be so.  I'll have to borrow a router and try that out.

---

### Post by HotShotDJ on 2009-02-10
> **challenged said:**
> Well the guest is a greedy little thing  that keeps hold of the printer.Do you have a device filter set for the guest OS in Settings --> USB?  If you do, it will always grab the printer.  Delete the filter if you have one set to prevent it from automatically taking control of the printer when you start the VM.

---

