---
title: "Missing Textures after Nvidia driver update"
date: 2021-03-14
forum: Ubuntu/Debian BASED
---

### Post by sx200n on 2021-03-14
Hello,

I am running ubuntu 20.04 (well Pop_Os) and I have been gaming perfectly with my Nvidia GTX1050ti card for about a year. I play a number of games and all through Steam Play.

I have had a number of Nvidia driver updates of which all have been fine, but just the other day ran the update to move to the 460 nvidia driver - and I now have missing textures in some of my games - namely Far Cry 5 that I have happily been running a smooth as silk on the highest graphic settings. 

Even if i toggle the graphics to low - it makes no difference. The bulk of the games textures are fine, but there is clearly a missing texture (or one that the driver cannot display) as I seem to have gaps in the ground, and can see through some of the ground textures. 

Does anyone has n easy fix, or perhaps the best way to roll back the nvidia update, as the previous versions of the nvidia drivers had no issues whatsoever on any of the games in Steam Play.

Thanks

---

### Post by jeremy31 on 2021-03-14
Moved to Ubuntu/Debian based

---

### Post by rockorequin on 2021-03-19
I have the same issue in all versions of nvidia 460 (460.32, 460.53, 460.67) as do others (eg see comments in [https://www.protondb.com/app/552520](https://www.protondb.com/app/552520)), so I assume it's the 460 series giving you problems? I don't think anyone has reported it to nvidia, though.

Can you set it to use an earlier version of the driver,  eg nvidia-driver-450, with apt install or synaptic or your tool of choice on Pop_OS? If other versions don't show up, maybe use the PPA [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal)

Personally I just run the Vulkan beta development series, eg the latest is 455.50.10 (you can download it from [https://www.nvidia.com/en-us/drivers/unix/](https://www.nvidia.com/en-us/drivers/unix/)). I have an optimus setup so I can remove the nvidia 460 drivers completely and reboot (since I have an intel GPU as well I can reboot into the desktop, but you could also install it from recovery mode) and run the install file manually, telling it to go ahead even though it detects that there is a distribution method of installing and telling it yes, install the dkms driver. (The installation fails to run if you don't remove the old nvidia driver first.)

---

