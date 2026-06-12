---
title: "Games Lagging"
date: 2021-12-04
forum: Ubuntu/Debian BASED
---

### Post by silverdisk on 2021-12-04
I recently switched my PC from windows to Pop OS and now I am experiencing lag in single player games that I did not with windows as well as substandard graphics. I don't know if this is from errors with Nvidia drivers or something else entirely. Please help.

---

### Post by deadflowr on 2021-12-04
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by scarletnyaa on 2021-12-04
When you installed the OS, did you make sure that you installed the image from the "Download 20.04 LTS (NVIDIA) button? If you did not install this one, then you are likely using the Nouveau driver which has very poor 3d acceleration support leading to low graphics and lag. In either case, try to run "sudo apt install system76-driver-nvidia". This should install the Nvidia drivers if they are not installed, and if they are installed it will simply reinstall them/notify that they are installed. Let me know if this helps, if it doesn't then I can help more, especially if it's a game on Steam.

---

### Post by silverdisk on 2021-12-05
I tried what you suggested and it didn’t seem to make a difference. I was trying to play Minecraft and I’m assuming I would have the error with other games as well.

---

