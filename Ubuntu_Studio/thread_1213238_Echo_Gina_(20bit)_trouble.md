---
title: "Echo Gina (20bit) trouble"
date: 2009-07-14
forum: Ubuntu Studio
---

### Post by Bartje on 2009-07-14
Hi all,

about a year ago I posted something about this already, but the thread is archived, so I have to start a new one. No problem at all for me though ;).

I'm running the latest ubuntustudio for my multimedia needs and easy access to a rt-kernel. Last year I've put my pci-audio card, with breakout box (Echo Gina, 20bit) in my brand new PC. That did not work. The problem is, it still doesnt get detected, but I want to give it another try. 

Here are the steps I took, just to get the card detected on my new system, not to get it to work yet.

1. Checked the connection of the Echo PCI card, : **It didn't work**
2. Took it back out, tried it again on my old PC : **It worked**
3. Put another PCI card (wireless network card) in the slot I previously tried my Echo card in : **It worked**
4. Placed the Echo PCI card, back in the slot of my new PC : **It didn't work**

With "Worked" I mean, getting detected using lspci or lshw.

Conclusion : 

Echo PCI-card is functional
PCI-slot is functional
Connection is fine, I can't change, move, clean more anymore
But it does not get detected!!!

How is this possible?

---

### Post by Stochastic on 2009-07-14
I had a ton of troubles as a beginner with an old Echo Darla 20bit card (same chipset) before I moved onto a different card.  I don't think I ever did get it working (sorry for the shining ray of hope).

For now I'd suggest taking a read through the official alsa docs on the Gina20bit: [http://www.alsa-project.org/main/index.php/Matrix:Module-gina20](http://www.alsa-project.org/main/index.php/Matrix:Module-gina20)

---

### Post by Bartje on 2009-07-15
thanks for the tip. But it is useless to attempt to get it running if the system does not detect the soundcard. It has to be seen by the system to enable it.

The problem is not only, how to get it running, but why does it get seen by the system on one computer and not on the other, using the same operating system?

---

### Post by Stochastic on 2009-07-15
when you say "same operating system" do you mean exact same version of Ubuntu?  maybe that the version differences could provide the first clues to why...

---

### Post by Mars73 on 2009-08-13
Today I have plunged into Ubuntu Studio, after working happily with Ubuntu for 3 years now.
I have a Gina20 card (around 11 years already) and always used W98/xp with it but was curious if it worked with Ubuntu Studio.
I downloaded Ubuntu Studio and came with the RT kernel, lspci saw the Motorola DSP card (the Gina) and checked on the Alsa site to see how I could get it to work.
After downloading the files needed (driver, lib, firmware and utils), I compiled it and it got stuck/freezed.
Seemed that the RT version that came with Ubuntu Studio didn't liked my setup.
After trying different things I installed the vanilla Ubuntu 9.04 on it and then installed the Studio components.
I also downloaded the 2.6.29.6 kernel and rt23 patch and compiled the kernel myself.
(step-by-step on: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu))

After that followed what was on: [https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)
But instead of mia I put in gina20, restarted and voila alsamixer -c0 gave Intel ICH5 and alsamixer -c1 gave the Gina20.
Tested with some instruments and everything works and till now is superb stable.
I'm a happy man/musician.
I have the custom kernel/header Debs if anyone is interested (it's for 32bits),
though it's not difficult to build your own, it only took a few hours...

[http://www.freesystemprojekt.nl](http://www.freesystemprojekt.nl)

---

### Post by rjl6591 on 2009-08-26
I have the Gina 24 card, which is very similar. AIUI (The Gina 20 is just the same as far as software is concerned - it just ignores the 4 least significant bits.)

On a vanilla Ubuntu or UbuntuStudio installation, it needs the alsa-firmware package from medibuntu.

The best mixer to use is echomixer, which is written to support all the features on these cards and is in the alsa-tools-gui package.

---

### Post by LesPaul85 on 2009-08-28
Hi all -

I'm new to the forums, but a long-time Linux/(K)Ubuntu user.

My Gina20 card works fine in an older Athlon XP box with both Winblows and UbuntuStudio.  My wife bought me a newer quad-core 4GB Dell 530n with Ubuntu pre-installed (a surprise gift, she's not a techie, so I'm trying to make it work).  

In prep for putting UbuntuStudio 9.04 64-bit on the system, I installed my Gina20 into a PCI slot and pressed the power switch.  The system powered on...and nothing happened.  Couldn't even get to the BIOS settings.

I'm sure this is some kind of PCI/hardware issue and not Ubuntu (so I apologize if this is the wrong place to post).  But has anyone else had issues like this with an older Gina20 and a newer system?  Any info or insight would be greatly appreciated.

---

