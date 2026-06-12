---
title: "Nvidia driver stoped working with upgrade"
date: 2008-10-24
forum: Server Platforms
---

### Post by Oracles on 2008-10-24
Recently there was an upgrade posted on the upgrade manager, it caused The Nvidia driver to stop working on the Ubuntu 8.10 server. The nvidia xserver Settings no longer work I tried to reinstall them from the command line and the package manger.  Apparently the upgrade installed a file nvidia-glx new
When trying to reinstall Nvidia settings and Nvidia xconfig in the package manager this Nvidia-glx new file is un-installed. We did not remove the files completely from the package manager just installed and uninstalled them. The nvidia x server settings in the administration category , the icon is missing. When you click it it suggest &#8220; you do not appear to be using the NVIDIA X Driver. Please edit your X Configuration file ( just run &#8216;nvidia-xconfig&#8217; as root), and restart the X server. &#8220;
We tried this in the terminal window and could not get it to work.  At start up there are a lot of new messages including No resume message doing normal boot. And then the window Ubuntu is running in low-graphics mode etc. we tried to configure it does not work.  May we add that the driver worked perfectly before this upgrade.  Yes it is usually not a requirement for a server to run in this type of graphics mode, but we use it for other things. We are only moderate ubuntu server experienced users.
It would be nice if this upgrade could be taken off.  Can anyone tell us how to get the driver back to a running state.
We use duel monitors. The driver was uploaded last week the date today is 10-24-209 It would be a disappointment to have to reinstall.

---

### Post by cariboo on 2008-10-25
Intreipd no longer uses the Nvidia-glx-new module. remove  it, then go to System-->Administraion-->Hardware Drivers, if things haven't been changed to much you should be able to select new drivers for your video card.

BTW this is the server forum, servers don't use a gui, so this probably ins't the right place to ask questions about video cards. You` may want to direct any question here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Jim

---

