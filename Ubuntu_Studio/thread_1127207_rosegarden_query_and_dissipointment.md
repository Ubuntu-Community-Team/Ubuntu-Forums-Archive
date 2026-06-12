---
title: "rosegarden query and dissipointment"
date: 2009-04-16
forum: Ubuntu Studio
---

### Post by AXeS on 2009-04-16
running ubuntu 8.10... 
wanted a Propellerhead Reason 4 linux equivalent...
manually installed the dependencies and kde environment(took me few days, because mobile dont wana connect as modem:()
installed rosgarden finally...

start it up and nothing!!!
now what gives? no splash screen , no error , nothings missing, just click and nothing happens?

should i install ubuntu studio just to run rosegarden?
should i rather try it on Kubuntu because of the environment?

im lost... things seemed easy till lately, bugs creeping up like besides rosegarden not starting up i installed VLC with the codecs and everything (yes manually downloaded .deb files and installed via synaptic or terminal's dpkg) start it up it plays and then cuts out and freezes? 
what could've gone wrong?

any hypothesis? because im not dissing ubuntu...but if i wana watch movies or play music i goto go to windows? im trying to phase windows out completely but it's starting to look a bit grim for ubunutu.

i was thinking on othe linux distro's, maybe i'll have better luck there?

---

### Post by cariboo on 2009-04-16
What error message do you get when you try to start roseegarden in an Applications-->Accessories-->Terminal?

Jim

---

### Post by Stochastic on 2009-04-17
why are you installing dependencies 'manually'

all you need to do to install rosegarden is type ```
sudo apt-get install rosegarden
``` into a terminal

same thing goes for VLC.

And in order to troubleshoot your rosegarden install cariboo907 is right, we need to see what the output is when it's started from a terminal.  Simply type rosegarden in and press enter, then copy the output here.

Just a heads up though, you probably won't find Rosegarden to be a Propellerheads Reason 4 equivalent.  It's more like an old version of Cuebase.

---

### Post by eye208 on 2009-04-17
> **AXeS said:**
> (yes manually downloaded .deb files and installed via synaptic or terminal's dpkg) start it up it plays and then cuts out and freezes? 
what could've gone wrong?
Your method of installing programs is causing the trouble. You don't need to download or install anything manually. Just select "rosegarden" or "vlc" for installation and let Synaptic resolve the dependencies for you automatically. Do not download .deb files yourself. Do not use dpkg to install them. You are messing up your system that way.

Note that you can abort and resume the download process in Synaptic at any time. The package manager will not begin installation until all required packages have fully downloaded and their integrity has been verified using the cryptographic keys.

---

### Post by bolex100 on 2009-04-17
> Your method of installing programs is causing the trouble. You don't need to download or install anything manually. 
Good tip, but what does he do to get out of it?   How does he get the rubbish out of the system before installing it correctly? (or does he not need to?)

---

