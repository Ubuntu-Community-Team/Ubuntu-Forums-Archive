---
title: "Galago pro TTY too small"
date: 2017-05-31
forum: System76 Support
---

### Post by Babaoupla on 2017-05-31
hey there, I have the new Galago Pro and my display is 3200x1800. The desktop itself is great with a bit of tweaking in the options but 1 issue that I was not able to solve is that when I press Ctrl+Alt+F1 to get to a TTY terminal the fonts are so tiny its unusable! I have done a lot of research on the web and tried doing various changes in my /etc/default/grub file like setting values like

GRUB_GFXMODE=1280x960x32
GRUB_GFXPAYLOAD=1280x960x32

or I also tried doing what I could with 
dpkg-reconfigure console-setup

But no matter what I tried the fonts in the TTY screens always remained tiny and unusable. Can anyone point me towards a solution where I can make the TTY screens on my Galago Pro usable despite the very HiDPI resolution?

Thank you!

---

### Post by anthonywc on 2017-06-02
Have you try opening a ticket /w system76 support?

---

### Post by april-system76 on 2017-06-05
I poked at it a little bit, but `dpkg-reconfigure console-setup` was the best I could find.

---

### Post by jweber53 on 2017-06-05
James from system76 gave me these instructions for my galago pro:

 sudo dpkg-reconfigure console-setup

 *Pick VGA and a larger size, then run (from the console):* 
 sudo setupcon

Note the extra step. Unfortunately, this doesn't work on ubuntu-gnome. Some missing packages won't give any larger size fonts to choose from during the reconfigure. I'll figure it out eventually, but for now I've got a magnifying glass close at hand :)


John

---

