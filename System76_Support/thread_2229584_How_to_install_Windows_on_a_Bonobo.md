---
title: "How to install Windows on a Bonobo"
date: 2014-06-14
forum: System76 Support
---

### Post by hourback on 2014-06-14
Hi, all.

I haven't installed Windows 8 before and would like to know how to go about doing so on my brand new Bonobo.  I have a 250GB SSD and a 1TB hard drive, and I really don't want to have to reformat anything and mess up this pristine configuration any more than I have to.

Thanks in advance.

---

### Post by monkeybrain20122 on 2014-06-14
Virtualbox.

---

### Post by jakslev on 2014-06-15
Lol - is that a joke? You want to install Windows on a System76 machine??? Why on earth? 
But yes, Virtualbox is what you should do. Get legal virtualboxes with Windows on by googling "modern virtualbox windows", and taking the website that is located in Ireland (.ie).

---

### Post by hourback on 2014-06-16
Thanks, but I need a non-virtualized installation.  There is software, such as Ableton, that I want to run on this machine.

---

### Post by Dlambert on 2014-06-17
Then honestly your best bet would be to fill one of the empty hard drive slots with a new hdd or ssd and install windows on that. The bonobo can hold 2x 2.5" drives and 2x mSata drives.

---

### Post by racaspercom on 2014-06-20
I installed Windows 7 on my Bonobo.  There are probably a few ways to set it up, but this is what I did.  My computer has a 120G SSD and a 750G hard drive.  After backing up data, I wiped both drives and installed Windows 7 on the SSD.  Then I installed Ubuntu on the larger hard drive.  So it's a "dual boot" set up.  It boots into Ubuntu by default, but I can override this on the GRUB screen and choose the other drive if I want to.

I thought about Virtualbox, but I mainly wanted Windows to play games, and thought this would give me better performance with the nvidia card.

\

---

### Post by allcoms on 2014-06-23
hourback:

Have you tried Bitwig or Tracktion for Linux? There's a vst-bridge app that lets you use many Windows VSTs under Linux if you aren't happy with the avaiable Linux plugins.

Steam is improving the gaming situation but there are of course many games that aren't on Steam for Linux and won't run under Wine.

---

