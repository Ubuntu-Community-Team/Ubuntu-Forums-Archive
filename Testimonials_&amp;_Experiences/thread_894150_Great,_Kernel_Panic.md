---
title: "Great, Kernel Panic"
date: 2008-08-19
forum: Testimonials &amp; Experiences
---

### Post by etomic13 on 2008-08-19
I installed Ubuntu 8.04 on my laptop about a month ago and it was fairly smooth sailing. The only small problems I had where sometimes when I suspended it, it would not come back or it would come back but I wouldnt have wireless working, strangely I noticed this was only when I closed the lid. So a few weeks ago I just started suspending it from the menu which solves everything. I was pretty happy especially considering everything, wireless, Compiz, and suspend worked out the box (mostly). So tonight I decided I was going to try out 8.10 so I started the upgrade process and it was about done installing the components and it was completely frozen for over a half an hour, I couldn't even move the mouse. So I turned it off and I turned it back on only to see that it had a kernel panic and is currently in an un-operable state so I guess I'll be re-installing Ubuntu tomorrow luckily I make regular backups of my home folder. BTW kernel panics are fun on Ubuntu it had my caps lock, wireless, numlock, scroll lock, lights all blinking simultaneously.

---

### Post by hyper_ch on 2008-08-19
Why didn't you just simply install 8.10 in an own small partition to check it out as it is still alpha?

---

### Post by Joeb454 on 2008-08-19
> **hyper_ch said:**
> Why didn't you just simply install 8.10 in an own small partition to check it out as it is still alpha?

Or as a Virtual Machine?

---

### Post by kevin11951 on 2008-08-19
> **etomic13 said:**
> I installed Ubuntu 8.04 on my laptop about a month ago and it was fairly smooth sailing. The only small problems I had where sometimes when I suspended it, it would not come back or it would come back but I wouldnt have wireless working, strangely I noticed this was only when I closed the lid. So a few weeks ago I just started suspending it from the menu which solves everything. I was pretty happy especially considering everything, wireless, Compiz, and suspend worked out the box (mostly). So tonight I decided I was going to try out 8.10 so I started the upgrade process and it was about done installing the components and it was completely frozen for over a half an hour, I couldn't even move the mouse. So I turned it off and I turned it back on only to see that it had a kernel panic and is currently in an un-operable state so I guess I'll be re-installing Ubuntu tomorrow luckily I make regular backups of my home folder. **BTW kernel panics are fun on Ubuntu it had my caps lock, wireless, numlock, scroll lock, lights all blinking simultaneously.**

yeah, i had a kernel panic a week ago (first ever) and it was so cool seeing EVERYTHING with an led in my computer light up and blink!

---

### Post by cardinals_fan on 2008-08-19
I don't know what you were expecting; Intrepid is still in Alpha.

---

### Post by Keyper7 on 2008-08-19
Bah, the last kernel panic I had wasn't fun: only caps lock blinked.

You guys are so lucky...

---

### Post by vikramaditya on 2008-08-20
oooh!  oooh! [IMG]http://i205.photobucket.com/albums/bb264/Ginchiest/icon_icon95.gif[/IMG]  i want one!  plz, how can i make hardy panic???

---

### Post by unoodles on 2008-08-20
> **vikramaditya said:**
> oooh!  oooh! [IMG]http://i205.photobucket.com/albums/bb264/Ginchiest/icon_icon95.gif[/IMG]  i want one!  plz, how can i make hardy panic???

Do you have an Intel pro 3945 wireless card? If you do and you install the backports-modules and then try to suspend, you get a kernel panic.
It could be my configuration, or it could have been fixed, so if it doesn't work, don't come crying to me :D

Sorry mods, double post, I accidentally hit the submit button twice. Please delete the below.

---

### Post by unoodles on 2008-08-20
> **vikramaditya said:**
> oooh!  oooh! [IMG]http://i205.photobucket.com/albums/bb264/Ginchiest/icon_icon95.gif[/IMG]  i want one!  plz, how can i make hardy panic???

Do you have an Intel pro 3945 wireless card? If you do and you install the backports-modules and then try to suspend, you get a kernel panic.
It could be my configuration, or it could have been fixed, so if it doesn't work, don't come crying to me :D

---

### Post by Irihapeti on 2008-08-20
> **vikramaditya said:**
> oooh!  oooh! [IMG]http://i205.photobucket.com/albums/bb264/Ginchiest/icon_icon95.gif[/IMG]  i want one!  plz, how can i make hardy panic???

If you're really that keen, I think you can do it by playing with the Grub commands. No, don't fiddle with your /boot/grub/menu.lst - just hit "e" when the Grub bootup screen appears and then change your bootup commands (it's only temporary) so that the bootloader goes looking for initrd.img in a place where it isn't. 

It's a while since it happened to me (by accident) so my memory's a bit rusty on the details. But, if you're keen, you'll work it out :)

---

