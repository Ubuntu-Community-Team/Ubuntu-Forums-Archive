---
title: "To mount Sharedserver Permanently"
date: 2011-08-05
forum: Server Platforms
---

### Post by buntu2020 on 2011-08-05
I just mount my sharedserver and Photos on my newly installed LUBUNTU, Is there any ways i can mount it permanently on MY COMPUTER OR DESKTOP? Because every time i want to access it i need to go to "FILE MANAGER" "GO" and I have to retype the address before i access it.

---

### Post by Morbius1 on 2011-08-05
The easiest way is with something called Gigolo. Here's a mini HowTo on how to use it to automount: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

I'm not that familiar with Lubuntu specifically but to have Gigolo start at boot I copied /usr/share/applications/Gigolo to /home/user-name/.config/autostart. I also had to create the "autostart" folder first. 

If there's a more sophisticated way to autostart an application in Lubuntu please let me know.

[COLOR=Blue]EDIT:[/COLOR] This auto mounting happens at login not at boot so all you need to do to test it is logoff and login again not reboot.

---

### Post by volkswagner on 2011-08-05
Assuming Lubuntu is your client and SAMBA is the server you'll want to [create an entry in fstab]("http://ubuntuforums.org/showpost.php?p=10549677") to mount it on boot.  

Otherwise if it is NFS, you'll want to do the same.  [How to permanently mount an NFS share]("http://ubuntuforums.org/showthread.php?t=249889"). 

If you run into trouble please offer more information about the server share, ie: how was the share created?

---

### Post by kerry_s on 2011-08-05
Have you tried just bookmarking it?

---

