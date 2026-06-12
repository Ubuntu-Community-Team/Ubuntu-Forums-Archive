---
title: "Can someone quickly solve this one please?"
date: 2012-01-07
forum: Ubuntu Studio
---

### Post by mikee55 on 2012-01-07
Hi all, a reinstall of Natty a while ago, I had annoying clicks running Jack. I looked here and found out the best way to set my PC up for Real time audio. Someone suggested a seperate user account called Audio. When I did this,I was able to do RT audio with little or no Xruns. Well, then I did a fresh install, as in upgrade to Oneric and my system was full of bugs and wasn't stable, I was looking for an Nvidia driver fix.
I decided to return to Natty, and haven't been able to find the post with the instructions in. please can you help? I've only got a mobile broadband connection and surfing is poor, i can promise you I have searched and I can't find my info.
Many thanks.

Mike

---

### Post by sgx on 2012-01-07
You can add your main user to the audio group using ubuntu admin.
The    groups    command shows what groups you are part of:

bash-4.1$ groups

username disk lp wheel floppy cdrom usb cdwriter audio video dialout users usbmux lpadmin pulse-access polkituser fuse


Adding more users is undesired complexity. People can help with configurations to remove noises, when your hardware details
are shared.
Cheers

---

