---
title: "Unsupported Printers and scanners"
date: 2014-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by mdouble on 2014-08-23
Unsupported perpherial devices are one of the weak points of Linux in general.  Every companies which claim to support linux fall short on this point.  As an example I have a Brother MFC-j430w printer / scanner. It's a terrific WiFi enabled printer, which a nice scanner including a really useful document feeder.  To their credit Brother does provide a printer and scanner driver for the printer.  Getting the printer working took some effort, but the scanner is totally useless.  There are various suggested workarounds one can try using the terminal, but to date I haven't had the time or patience to work through them.  I have tried and failed several times and have no joy working through the issues with terminal. These fixes involve editing various files, and the process is rather complicated if you aren't really familiar with terminal.  I am learning the command line interface, but that takes some time.

My solution has been to connect an older HP ScanJet via USB.  It works with XSane but not with Simple Scan - but at least does give me direct scanning capabilities.  However, I often need the use of my auto document feeder when scanning multipages into a single pdf, as one example.  Scanning single pages is a workable way to go, but a giant pain in the butt if one does it often.

The irony of all this is that brother makes a great little app for Android which allows full use of all the scan / print features of the device, and does so wirelessly.  Using that simple app, I can bulk scan a document and save or send it as a jpg or pdf in two simple steps.  To save it on my Linux machine I send a copy to myself by email.  It is an unduly complicated way to work, but it does allow me to carry on lacking a better solution.

I am sure many other Linux users share my frustrations on these points.  I would financially support a commercial third party developer of drivers for Linux users.  Such a developer would in fact pay manufactures to license out Linux specific drivers for all Linux distros.  Imagine an app which works much like the one created by Brother for Android.  It could scan for all devices, including WiFi printers and scanners, find the correct drivers and simply install them.

Linux and the whole open source software universe are excellent up to a point.  The whole Linux desktop inititive will totally stall without a way around this problem.  CUPS is a semi-soltuion, but also suffers from incomplete solution.  If Linux is ever going to have broad appeal we really need some way to solve these kinds of problems.  I'd be interested in your feedback

---

### Post by tgalati4 on 2014-08-24
Send an email to Brother referencing this thread and see what their response is.  If the command line setup procedure works, then try performing that.  You only have to do it once.

---

### Post by mastablasta on 2014-08-25
HP has opensource drivers so their stuff usually works as it should. In your case of HP use I think it is the software that is the problem.

I am not sure if Samsung keeps them open I think they are closed. Yet they do work. so Linux is supported. 

with porpper documentation and the soruce open everyone can write their own drivers. or pay someone to do it for them. or to fix them at least.

E.g. Samsung distributed Linux drivers for my model with an error. they just didn't work when you tried to install them from the CD. a good person fixed the error and provided a PPA for others after Samsung didn't really act. After a while Samsung fixed the issue and even made improvments to their Linux driver.

---

### Post by dave131 on 2014-08-25
Im a newbie, but just finished helping someone get their printer working in Ubuntu which they had not been able to do for 2 years.  Before I mention the brand, because I don't want to turn people away right away, note the a lot of the older Dell printers were cross-branded Lexmark printers, so this may very well work for some Dell printers as well.  The particular user has a Lexmark 2420, but the driver in question is sort of a "one-size-fits-all" driver for several Lexmark inkjet printers (and as mentioned, should work with some Dell printers).  This link shows how to get and install that driver:

[http://ubuntuforums.org/showthread.php?t=2240872](http://ubuntuforums.org/showthread.php?t=2240872)

---

