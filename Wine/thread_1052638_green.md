---
title: "green"
date: 2009-01-27
forum: Wine
---

### Post by jmutonyi on 2009-01-27
i like downloaded ubuntu yesterday so i'm very green. I heard about wine so i'm wondering, where do i get it? how do i install it offline? It sucks being in africa coz i don't have internet at home. i've never used unix based o/s before so i really need you to break everything down for me

---

### Post by cogadh on 2009-01-28
Wine can be difficlut to install offline because it does require a few dependent packages. If you can get your Ubuntu machine internet acess even briefly, the easiest way to install it is to just use the Add/Remove Programs applet in the Applications menu, it will take care of everything automatically. Alternatively, you can get the latest unstable version of Wine by following the instructions [here]("http://www.winehq.org/download/deb").

If even temporary internet access is not an option, then you will need to download individual packages from the [Ubuntu repository]("http://packages.ubuntu.com/"). I believe the minimum required packages you will need to download will be wine, wine-gecko, binfmt-support, winbind and libaudio2. Each of those packages may have additional dependencies that are not already installed in Ubuntu, I'm not really sure. After downloading the packages, you need to install them in the correct order. I'm not 100% certain of this, but I believe it should be like this:
libaudio2
winbind
binfmt-support
wine
wine-gecko
When you run each installation, it will warn you if one of the dependencies has not been met. Make note of what package it wants, you will also have to download and install those first. 

As you can see, the manual process is a lot more difficult the the automatic process, so I strongly recommend that, if at all possible.

---

### Post by jmutonyi on 2009-01-28
thx. i'll do that then get back to you

---

