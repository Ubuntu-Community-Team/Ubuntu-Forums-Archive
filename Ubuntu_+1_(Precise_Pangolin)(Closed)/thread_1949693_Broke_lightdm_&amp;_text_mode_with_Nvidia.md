---
title: "Broke lightdm &amp; text mode with Nvidia"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zuti on 2012-03-30
Any help welcome. 

For the past week I have been using the official 295.33 drivers from Nvidia, but today decided to revert back to the ones provided in the repos, since they have been updated. Uninstalled the official package with nvidia-uninstall, rebooted and installed the package suggested by jockey. 

Now if I boot, all I get is a purple screen. No text, no lightdm. All I can do is ssh in and run sudo start lightdm, which works fine. 

I tried purging the drivers, and with the open source drivers lightdm starts right away. But as soon as I install nvidia-current... it won't. 

Any idea what I could do to fix this? The problem is quite frustrating, as I can't even use the virtual consoles because of the purple screen.

---

