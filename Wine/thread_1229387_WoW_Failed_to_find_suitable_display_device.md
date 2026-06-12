---
title: "WoW: Failed to find suitable display device"
date: 2009-08-02
forum: Wine
---

### Post by Onikage on 2009-08-02
Okay, the long and the short of it is that I had managed (with help) to install WoW on to my computer. Had it going fine the longest time, but when it came time to slap on the Lich King, the EULA wouldn't let me click "Accept". Checked around, solved the problem, but now, every time I try to play, after I click "Play" on the preloader it give me a message saying that it "Failed to find suitable display device".
I looked around and followed some of the suggestions like replacing the .dll files and such, but still no go.
What makes it especially tricky for me is that I'm not very skilled with Linux commands at all.
I would really appreciate some noob friendly help, please.

---

### Post by Soulcage on 2009-08-02
Try adding -windowed to the end of the exe.

---

### Post by Onikage on 2009-08-02
Nope. Says the same thing.

---

### Post by NightMKoder on 2009-08-02
What's the output of:

glxinfo | egrep -i '(OpenGL|direct)'

?

---

### Post by Onikage on 2009-08-03
It says:
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:

I don't think it's a hardware issue, but rather a software issue, as it was running smoothly before I installed Wrath of the Lich King.

---

### Post by Soulcage on 2009-08-04
Try updating your video drives your using a pretty old version.
check out [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
and [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by Onikage on 2009-08-04
Urrgggg..... Tried installing the new drivers by following the directions on the NVIDIA site, but when I put the commands in it says "sh: Can't open NVIDIA-Linux-x86-185.18.31-pkg1.run".
Not sure what I'm doing wrong, as I said above, I'm not that skilled with Linux commands and such...

---

### Post by Soulcage on 2009-08-04
Did you remember to give it permission? chmod +x NVIDIA-Linux-x86-185.18.31-pkg1.run
Then u gota run w/ ctrl alt F1 stopping gdm with: sudo /etc/init.d/gdm stop
Then you install and reboot: sudo reboot

Make sure you installed and uninstall what is needed like it says on [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

