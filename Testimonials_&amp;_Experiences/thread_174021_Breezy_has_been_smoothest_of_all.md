---
title: "Breezy has been smoothest of all"
date: 2006-05-11
forum: Testimonials &amp; Experiences
---

### Post by osaeris on 2006-05-11
Hi all,

I wish to recount the trouble I had with installing SUSE on a collegue's machine and how Breezy helped out. I presented her with a breakdown of lots of major distros and she chose OpenSuse 10 (based on sort of Windows familiarity and polish). I put in a second IDE drive (20Gb) to install Suse on leaving her 40Gb XP drive in there. The main reason for the installation in the first place is to protect the machine when her other family members are surfing the net they have had some pretty nasty viruses in XP and had to completely re-install it at least once. This despite an anti-virus and firewall running in XP!

The Suse install went smoothly and everything appeared fine until I tried to use her external modem. Oh dear. It was possible to configure the modem through YAST and (as root) dial up to the ISP using wvdial. I then tried to allow the other user accounts to dialup and this is where I ran into a brick wall. When the computer was rebooted there was no dialup access for any user. 

After much forum searching and endless changes to symlinks and config file permissions I gave up. This is unlike me but it was too infuriating to continue. 
I also discovered that Thunderbird is a nightmare in Suse which I did not enter into because I couldn't find an rpm and it wasn't available through the default YAST repos. 

I popped the Breezy install disc in and ran through the now very familiar install routine. After running all the updates through my Ethernet connection I disabled eth0, enabled ppp0 and entered the ISP details. On activation the machine connects to the ISP and surfing is possible. I set up 2 other users and tested their dialup functionality. No problems!

I then ran EasyUbuntu and apt installed Inkscape, Scribus and Thunderbird finally copying her mail from the windows drive to her new /home/.Thunderbird folder. This whole process took less than 2 hours.

I have also installed 6 Dell C600 laptops with Breezy for a local youth centre so they can record short pieces for radio with Audacity. They received the laptops as a donation. My wife uses a C600 running Breezy to surf and check her email and also as a presentation machine with an LCD projector. I have a Dell precision 410 running Breezy as a workstation. I plan to upgrade my machine to Dapper after the official release so looking forward to that.

I wish to say a big thankyou to all involved in working on Ubuntu it's a really brilliant OS.

Steve

---

### Post by MasonM on 2006-05-13
Honestly, I've never understood why SuSE has been so popular. I've never had anything but trouble with it.

---

