---
title: "Nvidia driver stoped working with upgrade OUR FIX"
date: 2008-10-25
forum: Server Platforms
---

### Post by Oracles on 2008-10-25
This is our fix.
(For the record our video card was and Nvidia Gforce FX 5200)
We found that the Linnux-restricted-modules-2.6.24-21-server was the problem they were Missing 
(or possibly corrupted (you might try removing them first) They are linked to the Linux-restricted-modules-common module, 
atomically added when the Linnux-restricted-modules-2.1.24-21-server is reinstalled. 
(you might remove it too before you installed/reinstall.)
This became evident to us when under the System/Administration/Hardware Drivers, the Nvidia driver was missing.
They can be uninstalled/reinstalled under the Package manager.
AS A NOTE:
Before doing this we did boot to:
Under the options menu at the log on screen
Fail Safe Gnome
While in there we opened the terminal and typed:
sudo apt-get remove nvidia-xconfig Hit (enter)
sudo apt-get remove nvidia-settings Hit (enter)
sudo apt-get autoclean nvidia-xconfig Hit (enter)
sudo apt-get autoclean nvidia-settings Hit (enter)
sudo apt-get install nvidia-xconfig Hit (enter)
sudo apt-get install nvidia-settings Hit (enter)
exit Hit (enter)
(this may not have been necessary for the fix but was an attempt to reinstall the clean copies of the nvidia configuration files.
after reboot Under the options menu at the log on screen
change the session boak to Gnome!
CHANGING NVIDIA SETTING DELIMA AND OUR SOLUTION.
After fixing the Nvidia driver and going to nvidia xserver settings under System/Administrator category.
We changed the settings but could not successfully get them to save to x Configuration file in the options.
The following is our fix:
(there may be another easier way and this may have caused the problem that influenced the original upgrade to fail)
After making your changes in the Nvidia X configuration choose the Save to x configuration option then
Select show preview then copy all text.
Click Cancel
Go to terminal
Type:
gksudo nautilus
(If you don’t use this command you will find it difficult to get permission to save the file)
Hit (enter)
Navigate to the following file
/etc/X11/xorg.conf
Save it as xorgold.conf (in case you need it later)
Navigate back to /etc/X11/xorg.conf open it and replace/paste the text you copied from show preview file earlier. Save it.
After exiting all windows hit control Alt Backspace to restart xserver

Many thanks and much luck to all.
Comments and suggestions are very welcome and desired.
Oracles

---

### Post by cariboo on 2008-10-25
Is this a desktop system you're posting this inforamtion about?

Jim

---

### Post by Oracles on 2008-11-02
Actually it was the Ubuntu server 8.04.
But the Nvidia driver crashed during screen saver operation after our fix.
We fixed this but reinstalling the server
The nvidia-xconfig package caused the problem. It was previously installed and does not work with the newer Nvidia driver, more exactly the Linnux-restricted-modules-2.6.24-21-server. Somehow during the driver upgrade from the pervious version that used the nvidia-xconfig there was some corruption. We would like to add that the New Ubuntu 8.10 server, the Nvidia drivers do not work with the gnome desk top.  Somewhere we got the impression that this feature was not included in the upgrade/current version. We tried upgrading and a new installation neither worked with the Nvidia Gforce FX5200. The upgrade on the desktop version of Ubuntu 8.10 did work with a little configuration. We will continue to explore and welcome any input.

---

