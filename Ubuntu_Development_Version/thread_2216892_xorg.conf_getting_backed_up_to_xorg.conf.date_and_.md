---
title: "xorg.conf getting backed up to xorg.conf.date and then deleted almost daily"
date: 2014-04-14
forum: Ubuntu Development Version
---

### Post by barrmulio on 2014-04-14
I am having an issue where my xorg.conf file is getting copied to xorg.conf.<date> (e.g. today was xorg.conf.04142014) and then deleted. This happens almost daily.

Upon next boot, there will be no GUI.  I have to ctrl+alt+f2 to get to a terminal and cp the xorg backup to xorg.conf and then reboot. Everything comes back up fine after that.

I had to install the nvidia drivers via package (in synaptic: nvidia-331-updates), rather than Additional Drivers.  Additional Drivers will hang on the applying updates with the progress bar making no progress ](*,)](*,)

After installing the package, the Additional Drivers tab does correctly show that I am using the nvidia updates driver.

During beta I am running daily updates, so I'm not sure if that's the trigger.

Thanks in advance for any tips or help

---

