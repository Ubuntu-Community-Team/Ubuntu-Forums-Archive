---
title: "Ndiswrapper problem"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by verymadpip on 2012-03-10
Hi again folks.
I thought I'd give a quick rundown of how things have gone so far.

I've installed a barebones system to a Compaq TC1000 tablet using the non-PAE mini iso from March 3rd. My TC1000 has 472 Mb RAM & a 1GHz Transmeta Crusoe CPU.

The TC1000 has onboard wireless in the form of an Atmel at76c506 802.11b wireless adaptor, which is unable to handle WPA/WPA2 encryption, & consequently is pretty useless to me.  The Atmel also requires firmware to be loaded during (or after, I suppose) the installation.  A little like the Debian installer.
 
Instead I used a "Newlink" 802.11n wireless USB adaptor which I bought for something else.  It was fairly affordable at £15 (just under $25), & has an Atheros AR9271 chip that does all the work.  I was able to complete the whole installation without a wired connection  I just had to enter the SSID, encryption type & password when prompted.

I then installed Ice WM, Firefox, synaptic, xfe file manager, lx terminal, alsa utils, USB mount, wicd-gtk & a couple of other bits too.  I'm not using a DM so I log in, start x & shutdown/reboot form the CLI.

I have used a WPN111 wireless adaptor with ndiswrapper with the TC1000 before (& I would prefer to) but at the moment when I check to see if it's installed I get:

ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

you may need to upgrade driver and/or utils to latest versions available at blah, blah, blah

I'm at a bit of a loss with the ndiswrapper thing.

That's the story so far.  Mixed news, more good than bad I'd say though.

---

### Post by cariboo on 2012-03-10
Moved to a thread of it's own, as it really doesn't have much to do with the non-pae kernel thread.

---

### Post by verymadpip on 2012-03-10
> **cariboo907 said:**
> Moved to a thread of it's own, as it really doesn't have much to do with the non-pae kernel thread.

Ah, true, true.  I thought the firs bit was slightly helpful re non-PAE & installation, but it does then descend into a wireless issue.

Thanks cariboo907 fingers crossed for a fix :D

Tomorrow I'll try installing Lubuntu 12.04 beta1 to my laptop (which I also use ndiswrapper on) to see if it's an early stages of 12.04 thing.

---

### Post by verymadpip on 2012-03-11
Bit of an update:

Ndiswrapper is available in the Lubuntu 12.04 beta1 live environment.  To save myself some time I thought I'd give it a whirl from there as opposed to doing an install.  

I issued ndiswrapper -v & got the same results as before; module too old blah, blah, blah.

I guess a real install on physical hardware might yield a different result, but I'm not hopeful.
Is this entering the territory of a bug that needs reporting?

---

### Post by verymadpip on 2012-03-13
I installed ndiswrapper successfully from a tar.gz, which was interesting :)
WPN111 up & running again.

The same issue occured with RTL8187 wireless adaptor in a Lubuntu 12.04 beta1 fresh install on physical hardware, solved the same way.

---

