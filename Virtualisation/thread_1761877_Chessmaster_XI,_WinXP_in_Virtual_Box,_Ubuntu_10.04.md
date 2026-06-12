---
title: "Chessmaster XI, WinXP in Virtual Box, Ubuntu 10.04 host. Is it possible?"
date: 2011-05-18
forum: Virtualisation
---

### Post by oblador on 2011-05-18
Hi, 

Is it possible to run Chessmaster XI within WinXP (guest, VirtualBox) when Ubuntu 10.04 is the host?

I managed to install Chessmaster XI, but when I try to run the game, I get an error message about "opengL32.dll" ...

I installed wined3d and the guest additions, but nothing seemed to work and trouble persisted.

Has anyone been successful running this game within Virtual Box?

Thanks.

---

### Post by lmarmisa on 2011-05-18
Have you ticked the Enable 3D Acceleration option on the Display settings?. You should install the Guess Additions with the 3D option enabled too.

---

### Post by oblador on 2011-05-18
yes, I did that, but when the game was loading it ended up showing an error message and closing.

The error message mentioned "opengL32.dll"

But I really ticked "Enable 3d Acceleration" (also 2d acceleration) and installed guest additions... I even tried running the guest additions within WinXp safe mode to make sure it would install the video options.

thanks, but the problem persists.

---

### Post by rclowery on 2012-01-07
You may or may not be interested in a solution to this problem anymore, but I managed to get Chessmaster XI working by altering the cm.ini file. If you open this file and scroll down to Settings and change opengl=0 to opengl=1 Chessmaster should switch from using DirectX to OpenGL. VirtualBox seems to handle OpenGL rendering more easily.

---

