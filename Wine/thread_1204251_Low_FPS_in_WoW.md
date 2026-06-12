---
title: "Low FPS in WoW"
date: 2009-07-04
forum: Wine
---

### Post by Marblemouth on 2009-07-04
Hello all!
I'm having issues with my installation of World of Warcraft and I could really use some help.  The game is installed and playable after much try and error.  The issues I'm having now are: ridiculously low frame rate (2-5fps on average with spikes up to 10-15fps), getting disconnected from the server fairly often when hopping a boat or taking a portal somewhere.  I have made the regedit changes already and that did nothing for my fps.  I have also added to or changed entries in wtf/config.wtf, this also did nothing for my fps. 

  I originally had WOW installed on the same machine while using Windows XP and I never had a problem with my fps or my connection.  The only thing that has changed since then is I've lost Windows and am currently using Ubuntu 8.04.  I don't know if it's a compatibility issue with my video card and Ubuntu or if it's an issue with Wine.  I'm running the versions  shown below because I had read somewhere that they were the ones to use as opposed to the most recent versions. 

Thanks for any help you can offer.

Compaq Presario SR1115CL
AMD Athlon(tm) XP 2800+
!.5GB of Ram
Radeon 9200 PRO
Ubuntu Hardy Heron 8.04
Kernel Linux 2.6.24-24-Generic
Wine 1.1.23

---

### Post by Hairybudda on 2009-07-04
It's a combination of your hardware being a bit on the low end and ATi drivers not being that great in linux as well as the performance hit that comes with running wine, I can run it on a q6600 @ 3.2 with 4gig of ram and a 4870x2 and it doesn't run too great, ~40fps in places like dalaran.

Do you have direct rendering etc.. enabled?

---

### Post by Marblemouth on 2009-07-04
I figured the system was on the low end... we bought it several years ago to store mp3's and pics on, definately not to game on...lol.  Direct rendering is enabled.  I ran the command: glxinfo | grep rendering.  The terminal came back with: direct rendering: Yes.  Not sure what else you're looking for information wise.  I just started using linux about two weeks ago and I'm slowly feeling my way around the system.

---

### Post by CharmyBee on 2009-07-04
> **Marblemouth said:**
> 
Radeon 9200 PRO

This is just one model shy away from R300, which is where the ATI drivers really pick up speed. That's dropped in the latest drivers though, so if you're going to upgrade, you'll want a HD3x00 PCI-E card at the least.

---

