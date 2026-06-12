---
title: "Adding &quot;clocksource=hpet&quot; to your kernel command line with grub2"
date: 2011-06-07
forum: Server Platforms
---

### Post by y3ahright on 2011-06-07
I've searched for a while on these forums and google but I haven't found an answer on how to edit the #kopt= line in grub2.

Basically I'm getting the clocksource unstable tsc error after updating the the latest BIOS for my motherboard.  I've read a couple of suggestions telling me to add ""clocksource=hpet" to your kernel command line. The kernel command line is specified in /boot/grub/menu.lst at the line starting with "# kopt=..."."

I am on Grub2 which menu.lst was replaced with grub.cfg.  I couldn't find the #kopt line.  Is there any way to edit/add this line into my grub?

Thanks.

---

### Post by MacMan on 2011-07-02
As root, you have to edit the config file /etc/default/grub .

You should find a line like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Add whatever extra commands you need, like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=hpet"

Then save the changed file, and run this command in the console:
sudo update-grub

If you check the /boot/grub/grub.cfg now, it should be updated with your custom command.

More info here: [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

I hope this helps.
Have fun.

---

