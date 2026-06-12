---
title: "Ubuntu - rtl8821ce and varying hardware support in different distros"
date: 2019-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by alexukalex on 2019-01-19
OK, you may read this question and go "really?!" but I'm genuinely interested in some opinions/answers.
Ive been tinkering with various linux distros for a while on the same laptop. Fedora, (Arch based Manjaro, Antegos), Debian and debian based distros (mint, Ubuntu etc). None of them support the rtl8821ce (wifi bluetooth combo) out of the box, which isnt a problem as there are plenty of methods/help to get it going. Question though - why is it when compiling the "driver" from git or AUR the wifi works on some distros but no bluetooth, the wifi & bluetooth works on other distros (such as Ubuntu) and doesnt work at all on other distros. It's the same compile method isnt it? So is it because of the different Kernels? Why the difference, do different architectures build the code with different results? As the code is open source surely there shouldnt be such a variety of success with each install, or are the different Linux camps loathe to share code with each other?
I tried Debian (stable/weekly builds/with-without proprietary drivers) and couldnt get various aspect of my hardware working (graphics, screen brightness adjustment)... install Ubuntu and I'm able to install the drivers needed no problems with most things working out of the box... yet Ubuntu is based on Debian.
Maybe the answer is as simple as different teams different priorities but I'd be interested in some opinions in particular as I am a relative newbie with no programming knowledge.

---

### Post by TheFu on 2019-01-21
Debian doesn't use proprietary licensed code. That is a core value for them.
Ubuntu will use proprietary "blobs", when practical and the license allows them to.

**Not all open source code has the same idea about what "open" mean. **  Different people have different ideas about what FOSS means.  MongoDB has an idea that RedHat and Debian disagree about (and removed MongoDB packages). They switched from the AGPLv3 license to a license that requires support and management code also be released, not just improvements to MongoDB.

One thing I've learn over the decades is to buy equipment, especially network stuff, that is the most standard, well-supported, available.  For the last 10 yrs, that has been Intel.  Intel GigE network stuff just works and uses fewer interrupts than the lessor vendors.  It is a tad more expensive than the cheaper options, but if $5 more saves me 15 minutes of troubleshooting, it is well worth it.  And intel NICs push more data with less overhead and post-install, they "just work."

As for Bluetooth - I don't use it.  Too many security problems to even be considered an option.
Wifi ... I use only when necessary and never trust it.  Even inside my own home, wifi is untrusted and requires a VPN to access other systems internally.  So many issues with all the wifi protocols that I just cannot trust it.

---

### Post by alexukalex on 2019-01-24
Thanks for taking the time to reply... fascinating about different peoples/organisations take on FOSS. I havent found an unbiased summary of foss and how different organisations/groups embrace or manipulate it for their own means. Good point about the hardware and bluetooth (no great loss). Its interesting that more distro groups are starting to offer their own compatible hardware/rigs for sale (Manjaro etc) I hope they are successful enough to leave the niche market. Interesting times for Linux/FOSS/Open Source/FREEware etc with the aquisition of some distros by big corporations.... a big thank you to all those techies that keep free and open source distros alive.

---

