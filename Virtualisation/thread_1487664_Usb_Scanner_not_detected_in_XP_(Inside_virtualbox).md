---
title: "Usb Scanner not detected in XP (Inside virtualbox)"
date: 2010-05-19
forum: Virtualisation
---

### Post by simon0404 on 2010-05-19
Hi, I'm running Windows XP inside virtualbox.

I cannot use my Canon scanner in Ubuntu, but would like to get it working on Virtualbox...... If I can!


The scanner is seen by Virtualbox itself, as I can create a USB filter for "Canon Scanner" in "Settings"............ BUT...... when I go into windows, there is no plug & play detection of the scanner....

Is there a way of making XP detect my scanner??


Thanks in advance,
Simon.

---

### Post by opacatica on 2010-05-21
Most people use the Open Source Edition (OSE).  This is what happends if you use apt-get or use Ubuntu's GUI.  VBox OSE does not provide support for USB.  Go to Sun's page and download the Personal Use or Evaluation License (PUEL) version:
 
[http://download.virtualbox.org/virtualbox/3.2.0/](http://download.virtualbox.org/virtualbox/3.2.0/) 
 
It's free for Personal Use (as it name states) but cost $50 if you use it commercially.  This should solve your problem.

---

### Post by dsjstc on 2011-01-09
Frequently the problem is a bug in the VB's ECHI support.  Just go into the VM's USB settings and disable EHCI (usb 2.0) support.

[http://forums.virtualbox.org/viewtopic.php?f=6&t=18569](http://forums.virtualbox.org/viewtopic.php?f=6&t=18569)

---

