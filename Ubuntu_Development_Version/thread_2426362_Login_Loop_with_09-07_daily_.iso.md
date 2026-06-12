---
title: "Login Loop with 09-07 daily .iso"
date: 2019-09-07
forum: Ubuntu Development Version
---

### Post by rbmorse on 2019-09-07
Had the expected adventure getting Eoan to boot to Gnome due to the presence of an Nvidia 2080 RTX graphics adapter.  Installer failed with the proprietary driver, but a redo installing the Nouveau driver (and the nomodeset kernel option at GRUB boot) brought the system up.  

Updater reported packages to update, so i told it to go ahead.  Half-way through the update I received the "Ubuntu has experienced a problem" dialog and then the GUI crashed to the point where the display went into standby.   Could not bring up a tty.  Waited until the disk activity light and network activity indicators settled, walked the dogs, then rebooted.  Now I get the login loop. 

Fresh re-install with Nouveau. Passed on the updates, tried the proprietary Nvidia driver via driver manager.  Installation successful, machine came right up with the proper resolution.  Login dialog looks great at 1920 X 1200, but that's as far as it goes.  

Bug reports on all issues previously filed so I didn't add to the clutter.  I'll pull another .iso later in the week and try again.

This is a brand new machine, AMD Ryzen 3700x in an ASUS x570 motherboard.  Runs 19.04 and a bunch of other distros without fuss now that the RANDR issue has been addressed.

---

### Post by rbmorse on 2019-09-27
Problem comes from selecting "automatically log in user" instead of requiring user to enter a password at the beginning of each session. Not really solved, but I know what triggers it now so I can file a proper bug report.

---

