---
title: "Combined VMDK/Boot from External HD, nvidia/virtualbox-guest additions"
date: 2009-02-19
forum: Virtualisation
---

### Post by Takilara on 2009-02-19
Hello.

I have installed ubuntu 8.10 on my external HD.
I run this installation in two different ways:
1. Boot from the external HD
2. Run the external HD as a write-through disk in VirtualBox

This works very good except for one thing: Screenadapter drivers.

When i boot from the external HD, ubuntu detects the nvidia graphics card, and uses the correct drivers. All is good.
However, when i boot it in VirtualBox, it gives a 'failed to load module "type1" (module does not exist, 0)'.
I am then given the option to Run in low graphics mode, Reconfigure, or Troubleshoot.

I assume this is because ubuntu does not find the nvidia graphics adapter while in virtualbox, and that is fine, however, how can i get it to use the guest additions when booted like this? (they are installed).
If i choose low graphics mode, it is stuck in 800x600 and 640x480, independent of how many modes/resolutions i add to xorg.conf

Is there a way to have it "fall back" to virtualbox drivers when no nvidia card is detected?

Or if this is not possible, is it then possible to make a script one can run after boot, that can change the driver? So i could boot up, then run the script, and restart X in order to utilize the virtualbox graphics driver.

(i've tried to add the virtualbox entries from the virtualbox xorg to the normal nvidia generated xorg, without much results)
Also, the guest additions is working (mouse intergration, copy-paste etc, all except the graphics stuff).
I've attached my xorg.conf

Regards
Espen

---

