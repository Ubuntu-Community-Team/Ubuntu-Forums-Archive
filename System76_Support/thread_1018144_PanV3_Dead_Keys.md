---
title: "PanV3 Dead Keys"
date: 2008-12-21
forum: System76 Support
---

### Post by Zxaos on 2008-12-21
So, after installing 8.10 on my panv3 and installing and running the System76 driver, I still cannot use two of the additional keys on the keyboard (wow video and wow audio). It's not that they're just not configured, they aren't even being detected by gnome (that is, I can go into the keyboard shortcuts options and rebind the web browser and email keys, but the audio and video ones don't seem to register).

This is on a clean install of Intrepid. They were working fine on Hardy a couple of days ago, so it's not a hardware issue.

Any suggestions?

---

### Post by Lee_Machine on 2008-12-21
Sometimes hardware is depressioated for some reason or another.

Just go to synamtic and add the Intrepid backport modules.

The version number will be for whatever kernel you are running. 

This is something that needs to be added to the install for ubuntu and have the system check to see if hardare is working and auto install it.


Hope this works for you.

---

### Post by thomasaaron on 2008-12-22
The System76 Driver does not configure those buttons. I'm out of town for the week and don't have access to any test computers. When I get back next Monday, though, I can help you work on it further.

Lee Machine's idea is a good one. Let us know how it works out.

---

### Post by andrewdied on 2008-12-22
Definitely let us know when you find out more.  I never got those to give out any output with xev on those, even running 8.04 Ubuntu.

---

