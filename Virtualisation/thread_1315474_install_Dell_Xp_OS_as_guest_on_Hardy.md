---
title: "install Dell Xp OS as guest on Hardy"
date: 2009-11-05
forum: Virtualisation
---

### Post by threegremlins on 2009-11-05
I have a Dell Vostro 1500, but I'm trying to install the Dells OS system as a guest on Hardy. I've tried once but it seems the disk doesn't recognize the laptop and acts like a normal Xp install and doesn't accept the serial numbers. Is there a way to let virtual Xp OS to recognize it's on the laptop it was shipped with? Or is there another work around?

---

### Post by RBertrand on 2009-11-05
Microsoft's Genuine Advantage Validation uses several hardware parameters given by the PC it runs on, and as "your PC" is a virtual one, the numbers won't come back correctly. That's why your version of XP won't accept the numbers.

For what I know, you have the right to run XP on that box if the corresponding OEM-sticker is attached or when you have an FPP with a valid license, be it virtual or not, so you may call MS and ask for a serial.

They should give it to you (maybe after asking you to prove the validity of your license).

---

### Post by threegremlins on 2009-11-07
Thanks RBertrand
I posted on the virtual box forum and was directed to this link which I found helpful and it worked.

[http://forums.virtualbox.org/viewtopic.php?p=37931#p37931](http://forums.virtualbox.org/viewtopic.php?p=37931#p37931)

---

