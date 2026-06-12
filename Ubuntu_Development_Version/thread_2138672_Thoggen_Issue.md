---
title: "Thoggen Issue"
date: 2013-04-24
forum: Ubuntu Development Version
---

### Post by TheMixtureMedia on 2013-04-24
Hey there I am aware that Thoggen will not be on 13.04 (SUCKS) but I tried there .deb and get this error. Dependency is not satisfiable: dbus-1 (>=0.23.2) can someone help me with this if it can be fixed please.

---

### Post by mc4man on 2013-04-24
> **TheMixtureMedia said:**
> Hey there I am aware that Thoggen will not be on 13.04 (SUCKS) **but I tried there .deb **and get this error. Dependency is not satisfiable: dbus-1 (>=0.23.2) can someone help me with this if it can be fixed please.

I don't see any issue installing [the quantal .deb,]("http://packages.ubuntu.com/quantal/thoggen") (screen1), so if by 'their' you mean some other .deb maybe try that  one instead.

Seems to start up correctly, searches & offers to install the 0.10 gst ffmpeg & bad plugins, ect. scr. 2

Didn't actually use because I don't use thoggen

---

### Post by TheMixtureMedia on 2013-04-24
Thank you for your help, the .deb they have on there web site is older and that is what I was having the issues with. Again mc4man thank you for your help.

---

### Post by grahammechanical on 2013-04-25
This problem may be that the application is dependent upon certain libraries which are older versions of those already installed in Raring. So, the installer will not remove those newer versions of the libraries (which it will have to do if it is to install older versions) because there is a chain of dependencies interconnected to the newer libraries.

The answer is for the developers of that application to package it for Raring. Or, do not install 13.04 if you like that application so much. And yet When I search for Thoggen in the Raring Software Centre I get a result. But when I click More Info I get "NOT FOUND there isn't a software package called "thoggen" in your current software sources."

So, there we have it.

Regards.

---

