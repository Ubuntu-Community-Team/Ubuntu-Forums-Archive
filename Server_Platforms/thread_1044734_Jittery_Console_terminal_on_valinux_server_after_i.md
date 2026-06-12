---
title: "Jittery Console terminal on valinux server after install"
date: 2009-01-19
forum: Server Platforms
---

### Post by bob-ofd on 2009-01-19
new to the forum, did some searches to see if terms hit - no joy.
Problem - installed 7.10, 8.04/8.10 on a valinux server, intel L440GX+ mobo, two cpus, on bd vid, 2 ethers, ide controller, etc.
1U valinux 1220 box I think,might also be called a full on server.

install goes fine, but after booting with new install, the standard ascii console terminals are jittery (sparkling characters) and the video display lines are sort of split - some chars on right and some on the left. Almost like the driver changed the display params or something. Yes, I tried a couple of diff displays, but nothing seems to change what is coming out of the box to the vid.

Nope, not using X or KDE or GNOME, just want a simple ascii console terminal


any help appreciated!!
bob-ofd

---

### Post by cariboo on 2009-01-20
If you ssh in to the server do you get the same thing? It almost sounds like the video adapter is going defective. If you've got a can of cold spray handy, give the video chip a good shot to see if that clears up the problem.

Jim

---

### Post by bob-ofd on 2009-01-22
Normal text console terminal when I log in via ssh.
If I install another OS on the box, it text console is fine.
It seems to be something with Ubuntu, during install from CD it is perfectly fine, it is just when the system boots from th install that the jitter/wacky screen issue happens.
me of the characters are on the right side of the screen, first letter of command, partial words on the left side of the screen.
It is almost like the video driver is not quite right.

I believe, from my testing the vid hardware is fine, I suspected
power issues, but rulled that out.  Scratching my head, but I am not using anything but ubuntu on these boxes, happens on both
of my valinux 1220 boxes.....
thanks
bob.

---

### Post by cariboo on 2009-01-22
Just out of curiosity what type of video adpaters do those things have?

Jim

---

