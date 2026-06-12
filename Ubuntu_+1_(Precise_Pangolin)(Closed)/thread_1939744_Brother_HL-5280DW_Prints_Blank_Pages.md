---
title: "Brother HL-5280DW Prints Blank Pages"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-12
I've seen this problem elsewhere. On my Xubuntu partition (11.04), however, everything works as intended. On the new Ubuntu 12.04 install, all I get are blank pages. This is a deal breaker - but could be BETA related. If anyone knows of a solution to this (knows where I can find a PPD file perhaps?) or thinks this is worthy of a bug report, let me know. Also, would it be possible to copy the driver instsall over from my Xubuntu partition? If so, what files would I need to copy over and where are they? I'll be home this evening.:popcorn:

---

### Post by ronacc on 2012-03-12
check the brother web site , thats where I found the drivers for my MFC 7440N .

---

### Post by neu5eeCh on 2012-03-12
I have, but call me stupid. I wasn't able to find, specifically, a "PPD file". Does one have to extract it from an .exe file? Besides, why does this driver work in every other distro but Unity 12.04? It must be related to Unity?

---

### Post by dino99 on 2012-03-12
which of the brother* packages are installed on your system (see synaptic) ?

might be : brother-cups-wrapper-laser for your hardware. If its already installed, then purge & reinstall it then.

---

### Post by icb410 on 2012-03-12
I have this issue at work with a Brother-HL5250DN laser printer.  It worked perfectly under 11.10.  Using the driver provided in ubuntu, it detects the printer just fine and sends it print jobs.  However, I only get blank pages.  If I tell it to print a self-diagnostic test page I get something out.  However, the ubuntu test page doesn't print (it's blank).  Don't know if it's related but I get a message through the printer dialog that the toner is empty. However, toner was recently replaced and shouldn't be a problem.

---

### Post by icb410 on 2012-03-12
There's a bug report here: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/950713](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/950713)

---

### Post by ronacc on 2012-03-12
you will find a PPD file for your printer here .[ http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5280DW ]( http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5280DW )

---

### Post by neu5eeCh on 2012-03-12
Just got home and tried installing the PPD. No go. The printer still prints blank pages. Weird.

**Edit:** Just added myself to the bug-list. Looks like solving it is above my pay grade. Well... that's why it's a Beta and that's why I installed it on a separate partition. Other than this, I'm liking the new Unity very much.

---

### Post by neu5eeCh on 2012-03-13
If any of you are continuing to have problems with you printer, it's worth going here:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/950713](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/950713)

An active effort is being made to sort this problem out. Any further information would be helpful.

**Edit: **A fix was committed in March and this bug, at least on my own system, appears to be solved.

---

