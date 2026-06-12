---
title: "wine crashing system?!"
date: 2010-05-08
forum: Wine
---

### Post by Jay105 on 2010-05-08
hi guys

it seems my wine has gone crazy and keeps making my system restart. this only happens when running wine programs such as steam and spotify. it happens just before games initialise in steam and if i try to select a track during an advert (oddly) in spotify and takes me back to the login screen, closing all my programs and losing unsaved data. 

when going into 'configure wine', when clicking on drives it tells me it has failed to connect to mount manager. 

any suggestions?

---

### Post by asdfoo on 2010-05-08
> **Jay105 said:**
> hi guys

it seems my wine has gone crazy and keeps making my system restart. this only happens when running wine programs such as steam and spotify. it happens just before games initialise in steam and if i try to select a track during an advert (oddly) in spotify and takes me back to the login screen, closing all my programs and losing unsaved data. 

when going into 'configure wine', when clicking on drives it tells me it has failed to connect to mount manager. 

any suggestions?

Wine cannot crash your system, it runs with normal user privileges.  Wine uses OpenGL and X11, which talk to the video driver.  The video driver can crash your system.

Which video card and drivers?  Have you tried updating them?

---

### Post by Jay105 on 2010-05-09
cant really see where to find the card model, except GeForce 8200? nvidia driver version 185.18.36 currently active and working.

as it only becomes a problem in wine i was thinking it could be an unstable version or something, as ive had the problem when clicking on drives within wine config.

cheers

---

### Post by cogadh on 2010-05-09
Have you tried creating a fresh .wine directory? Perhaps there is something about your current config that is causing a problem. Try re-naming your existing .wine directory, then run winecfg to create a new one and see what happens when you click on the drives tab.

---

### Post by asdfoo on 2010-05-09
there are newer drivers available 195.x.x

---

