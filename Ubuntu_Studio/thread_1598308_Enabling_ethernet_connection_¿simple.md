---
title: "Enabling ethernet connection ¿simple?"
date: 2010-10-16
forum: Ubuntu Studio
---

### Post by Triphido on 2010-10-16
I've just received my first internet connection kit and now I'm trying to use Ubuntu Studio with it. Windows XP detected the new connection automaticaly (and this is now working fine) but UbuntuStudio didn't.

Documentation says I've to enable it manually in a configuration menu like this -System>Administration>Network, well, in English-.
  [IMG]http://www.guia-ubuntu.org/images/4/4a/Network-admin.jpg[/IMG]

But, in UbuntuStudio, this menu is quite different: it hasn't the most important tab, the first one, *Connections. *So i can't enable connections here. 

I've red that I can enable a new ADSL connection using a notify icon wich alerts me there is no internet connection, but, in my UbuntuStudio, notify area is allways empty!

The unique ethernet connection appears always disable. ¿What can i do now?

Sorry for my bad English. Thank you all!!

---

### Post by JC Cheloven on 2010-10-18
Hi, first some background: 

Perhaps you don't know that UbuntuStudio doesn't ship the default network manager of regular Ubuntu, called "network-manager". This is by purpose, as network-manager seems to interfere with the audio performance and rt kernels. So, it installs another program, called "gnome-network-admin", to control the networking. Unfortunately, this one doesn't work smooth for many people. 

Whether the interference of network-manager with audio is severe or not (or even noticeable) seems to be a matter of discussion out there. My advice in the next paragraph is applicable only at your own risk. In my experience, no noticeable interference of network-manager with audio occurs, but your mileage may vary.

To install network-manager, please folow the instructions in this thread among many others: [http://ubuntuforums.org/showthread.php?t=1525705](http://ubuntuforums.org/showthread.php?t=1525705)
Basically: uninstall gnome-network-admin using synaptic, and instal network-manager using the .deb's that you'll find in your ubuntustudio install dvd, under /media/cdrom1/pool/main/n/network-manager  and  /media/cdrom1/pool/main/n/network-manager-applet.

When you're done, reboot, and surely everything will go fine.
Should be easy!

---

