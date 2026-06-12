---
title: "What are my options for using an equalizer for PulseAudio?"
date: 2013-01-28
forum: Ubuntu Development Version
---

### Post by rectec794613 on 2013-01-28
Hello, community. 

I just installed 13.04. I'm having trouble getting pulseaudio-equalizer, because the PPA that holds that package (webupd8) hasn't updated it for Raring.

I tried using PulseAudio's built-in equalizer, the equalizer sink module, but it gives me an error: *Failure: Module initialization failed*. I got the instructions to do this from the [ArchWiki]("https://wiki.archlinux.org/index.php/PulseAudio#Equalizer"), which may be the reason why I get that error, if Ubuntu's PA has a different way of loading modules.

Those are the only two methods I know to get an equalizer. Do you guys have any suggestions?

Thanks.

---

### Post by rectec794613 on 2013-01-28
I've semi-solved this. I just installed the [.deb package]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/pool/main/p/pulseaudio-equalizer/pulseaudio-equalizer_2.7.0.2-2~webupd8~oneiric3_all.deb"). I forgot I could do that : P

Still though, if anyone knows how to get the equalizer module working on Ubuntu, let me know. Thanks.

---

### Post by nilarimogard on 2013-03-13
Pulseaudio is finally build with equalizer support in Raring, but the actual equalizer is missing from the package and also, you need to load two modules (as opposed to just one in Arch; the dbus module is disabled by default in Ubuntu) to get it to work. I've created a PPA for Pulseaudio with built-in equalizer support, instructions and more info here: [Install Pulseaudio With Built-In System-Wide Equalizer In Ubuntu]("http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html")

---

### Post by rectec794613 on 2013-03-13
Thanks for the reply. So PA's equalizer is working better now in Raring? That's good news. However, I use Arch now, although I'm still actively involved with Ubuntu. : ) I've enabled the EQ in Arch but it yields terrible results. Lag, glitching, etc. Sigh. Thanks for the PPA, though. My friend just started using Ubuntu and if he ever needs an equalizer, I'll definitely point him in the direction of your article.

Thanks,
Robert.

---

