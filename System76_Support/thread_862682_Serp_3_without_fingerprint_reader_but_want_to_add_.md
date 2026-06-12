---
title: "Serp 3 without fingerprint reader but want to add one"
date: 2008-07-17
forum: System76 Support
---

### Post by PantherFarber on 2008-07-17
Hi. I purchased my serp 3 before the holidays and there was the option to have a fingerprint reader but i didnt select it because i didnt realize the benefits of having one. is there a way i can get one installed in my serp 3 or have the unit sent to me with instructions to install it? i assume it would be located under the LIFE@multimedia sticker that covers a square panel on the lower right corner of the keyboard area. anyone i could contact about this. If given the instructions on the assembly of the laptop i could easily install it myself if sent the module. Is it possible for it to be added after the fact or is that something that would have required it being done prior to shipping?

P. S. Is it also possible to have the built in wireless swapped out for something that actually works in linux for more then ten minutes (have tried all the solutions. same result)

---

### Post by thomasaaron on 2008-07-18
The fingerprint reader has to be installed on the computer before shipping. We can't provide you with just the reader.

Which wireless card do you have?
lspci | grep -i wireless

If it is dropping that often, it is probably a configuration issue, or a problem with your router (that is, if it is an older router). If you have the 3945 card, you might want to swap it out with an Intel 4965. Both work out of the box with Ubuntu and should be reliable.

---

