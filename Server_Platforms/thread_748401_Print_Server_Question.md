---
title: "Print Server Question"
date: 2008-04-07
forum: Server Platforms
---

### Post by garfonzo on 2008-04-07
Hello,

I am in the process of setting up a home server with Ubuntu and want to set up a print server. The problem I have is that the printer I have seems to be unsupported in the Linux world (Canon IP1300 - I've read numerous reports of success with the 2200 driver so I will be trying that.). 

I'm wondering if it is possible that as long as the printer's driver is installed on all WinXP computers, they would be able to print to the Canon hanging off my server *even if* the server *itself *can't print to it. Is this possible? I was thinking along the lines of CUPS or a Samba print server.

Cheers,

Garfonzo

---

### Post by HermanAB on 2008-04-07
If Linux can't print then nothing will.  Linux makes any printer look like a Postscript printer.  So if Linux works then you don't need a Windows driver.  A Windows machine can literally use any availaible postscript driver to print.  I always use Apple Laser Writer since it is at the top of the list.

---

### Post by garfonzo on 2008-04-07
sigh.... ya, I kind of thought so. Well, here's hoping that the driver for the 2200 will work with my Canon 1300. 

You know, the cost of the black and color cartridges is $58.00. The cost of a new Canon printer (different model ... better model) is $59.00. I think I've found my solution.

---

### Post by HermanAB on 2008-04-07
Don't give up too quickly.  Try a bunch of drivers for older and newer printers.

---

### Post by netlogic on 2008-04-07
> **garfonzo said:**
> sigh.... ya, I kind of thought so. Well, here's hoping that the driver for the 2200 will work with my Canon 1300. 

You know, the cost of the black and color cartridges is $58.00. The cost of a new Canon printer (different model ... better model) is $59.00. I think I've found my solution.

hmm... sorry. I thought 2200 should have worked.

have you downloaded it from here?
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1300](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1300)

---

### Post by garfonzo on 2008-04-08
> **netlogic said:**
> hmm... sorry. I thought 2200 should have worked.

The 2200 driver very well might work, I haven't had a chance to try it yet. I'm not really in a position yet to go hard core into setting everything up. I've got other commitments that are tieing up my time. I'm trying to gather as much information as I can (literature) before I dive into actually getting my server up and running. 

I'm doing all of my testing on an old Toshiba laptop (SSHing into it via my main desktop) and when the time comes to implement all of this, I'll install everything on the actual server.

Right now my 'server' is a WinXP box that has a shared hard drive and a shared printer. I'm not sure how all of this relates to a printer driver, but I thought I'd share.

Cheers! :popcorn:

Garfonzo

---

