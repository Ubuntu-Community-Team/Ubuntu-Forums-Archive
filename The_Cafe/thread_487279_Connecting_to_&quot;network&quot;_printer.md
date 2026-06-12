---
title: "Connecting to &quot;network&quot; printer"
date: 2007-06-28
forum: The Cafe
---

### Post by vehorenkamp on 2007-06-28
I posted quite awhile ago with an issue of connecting to printers that are physically plugged in to my XP machine from my Ubuntu machine.  I can't find that post.  Whoever answered it referred me to:

[https://help.ubuntu.com/community/WindowsXPPrinter?action=print](https://help.ubuntu.com/community/WindowsXPPrinter?action=print)

I tried the suggestions in that response.  I got nowhere with my HP Photosmart C410 series printer.  So tonight I tried my other printer, HP Deskjet 3840 series.  When I selected Deskjet 3840 from the HP list of printers, I thought I had hit paydirt.  At the bottom of the screen, a recommended driver popped up.  I clicked on Install Driver and got a "window" that asked me to open a PPD file -- something that completely baffled me.  So I went back and skipped the install figuring that my XP machine would dowload the driver just as it does in a total Windows environment.  I got further in that the 3840 printer popped up in the list of printers.  I was even able to send a test page to the queue.  But I never got a connection to the 3840 printer.  The file just sat there in the queue.  At first it said printing, then it went to paused which is where it is right now.

Is it not possible to print from Ubuntu to a network printer that is physically attached to an XP machine?

If it is possible, what am I missing in the chain of events?

Thanks for your help.

Vince Horenkamp

---

### Post by Detonate on 2007-06-28
Assumptions:

You have a working samba network.

You have Cups installed.

The printer has been shared in windows.

If yes, the try installing the printer using the cups interface at [http://localhost:631](http://localhost:631)

That always works better for me.

---

