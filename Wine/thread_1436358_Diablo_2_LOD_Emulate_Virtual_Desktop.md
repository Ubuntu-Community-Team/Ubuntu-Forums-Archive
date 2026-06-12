---
title: "Diablo 2 LOD Emulate Virtual Desktop"
date: 2010-03-22
forum: Wine
---

### Post by amnite on 2010-03-22
I was able to run my D2 in fullscreen mode when i used my old Hardy version of ubuntu. Now that ive made the switch to Karmic i can only run it in emulate 8x6, if i try fullscreen it does the two begining logos then locks up any help?

---

### Post by Soulcage on 2010-03-23
Use this to run fullscreen at your desktop resolution [http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html") 1280x1024 for me. :)
After you install and set the program up run the video test and choose glide.

---

### Post by amnite on 2010-03-23
how do i tell if my card supports open gl?

---

### Post by amnite on 2010-03-23
Ok it makes it work fullscreen but locks up after the first two logo screens and all i get is sound and a mouse cursor... I dont know if this helps but when i played the game through Vista, when i ran the video test it gave me 2 options and now other than the 3dfx it only gives me 2d, could this be an improperly installed video card? its the same machine sooo i should still get the two original options right?... If so how do i properly re-install the card. This is a prebuilt machine so i dont know the specs... any help would be appreciated.

---

### Post by Soulcage on 2010-03-24
Did you install the video drivers? System > administration > hardware drivers. You can see what your card is by typing ```
lspci
```

---

### Post by amnite on 2010-03-25
lscpi: Iget this for graphics...
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


Thats the only thing i see that looks like a graphics thing... And hardware says i have no propriety drivers....

---

### Post by Shannon_VanWagner on 2010-03-27
Here's my suggestion:

alt+f2 then run update-manager -d

This will update you to Ubuntu Lucid 10.04, which (on my 5 computers at least) seems to be a pretty rock solid platform (even though it's beta).

I'm running DIILOD on my machine with Ubuntu 10.04 (formerly 9.10), but the difference is that I'm using NVIDIA 9400GT video card.

Here's a site with some videos of the games I'm running:
youtube.com/thecoolguy4linux
(I need to add DIILOD on there)

Just a suggestion... Hopefully you have your /home on a separate partition so that installing the system on / (sans losing user data in /home) is easy business.

Cheers!

---

