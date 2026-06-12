---
title: "Virtualbox and USB Drive problems"
date: 2008-11-22
forum: Virtualisation
---

### Post by carusoswi on 2008-11-22
. . . and a couple other glitches as well.

First, I'm running VB PUEL on Ubuntu 8.10 and have enabled my USB support.  A couple of times, I've actually been able to get both my USB drives to show in 'my computer' in my guest XPsp2 that I have installed.  When they show up, I can browse, open, save, everything.

However, if I close down, they will not reappear when I start the virtual machine up again.  Additionally, most of the time, I cannot get those USB drives to show up.  If I click either the USB status icon in the tool bar or use the Devices menue to enable those drives, one will disappear from my Ubuntu desktop, the other does nothing when I select it.  

If I deselect both in the VM, the drive that disappeared in Ubunut remounts itself in Ubuntu.

I've done some searching, tried a couple of the recommended code additions, but nothing seems to have helped.

What am I doing wrong?

Also, I have devined one firewire drive and my internal slave drive as shared folders, and can map them so that they show up in my Guest XP OS, but I cannot make them reappear after shutting down and restarting. . .  have to redevine as shared folders and re-map each time.

Again, what am I doing wrong.  Saving the machine state upon existing doesn't seem to do the trick.

Any advice welcome.

One more thing . . . my machine has an onboard sound card and a PCI sound card.  In Ubuntu or XP, I can enable both or one or the other, then select either for playback or record, either can be selected for both functions, either can be deselected in the same way.  

In my VB XP, the only driver that works is my onboard sound driver, and XP cannot even see my PCI sound card.

Suggestions here would be appreciated as well.

I have even loaded the driver files for the PCI card (it's an SB Audigy LS)in the virtual XP.  The driver loads ok, but cannot see the card.

Caruso

---

### Post by bodhi.zazen on 2008-11-22
What are your settings on the Ubuntu host (to enable USB devices) ?

The behaviour on the host sounds normal (you may not have a usb device mounted on both the host and guest at the same time. 

My guess is that the problem is with the windows drivers, I suggest you post on the virtualbox forums.

---

