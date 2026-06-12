---
title: "DV6T sound Card issue"
date: 2009-08-01
forum: Ubuntu Studio
---

### Post by moosamca on 2009-08-01
Hi All,

I am new to linux.. 
I installed UBUNTU 9.0.4 version on my HP dv6t series laptop which is running on MS Vista 64 bit.

I did't install Ubuntu 64 bit version. But my SOUND CARD is not working in Ubuntu. The sound card is working fin in vista. I tried all trouble shoot. Added new line of code on the alsa-base.conf file also. 

I believe there is no fix for this sound card IDT 92HD75B3X5. Please help me.

Thanks
Moosa

---

### Post by igorzwx on 2009-08-03
Applications -> Accessories -> Terminal

commands (on Terminal)

aplay -l

lspci -v

lspci > hardwareinfo.txt


The last command will produce a text file " hardwareinfo.txt"


Install several Ubuntu 9.04 on the same box

try:

1. ALSA + esound (without pulseaudio)

2. OSS4 (without alsa and pulse)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

one of these solutions may work


**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by moosamca on 2009-10-24
No luck! Is there any fix for this issue!! Please help me out.

---

### Post by sgx on 2009-10-25
I would try different linux versions that do not use the identical hardware detection as found in your current linux version. A suse 11.1
live/install linux dvd would be worth checking, its on various linux magazine dvd media quite often, if downloading a .iso file to burn your own is not possible. I have an alsaconf command here that looks for soundcards and configures the one you choose.

sudo alsaconf

Its worth a try. Cheers

---

### Post by AutoStatic on 2009-10-26
Hello moosamca, your soundcard does not work with the version of Alsa that is shipped with 9.04. You can either wait for Karmic, then it will work OOTB, or upgrade Alsa yourself using this [topic]("http://georgia.ubuntuforums.org/showthread.php?p=7657666") as a reference (I wouldn't recommend that though).

---

