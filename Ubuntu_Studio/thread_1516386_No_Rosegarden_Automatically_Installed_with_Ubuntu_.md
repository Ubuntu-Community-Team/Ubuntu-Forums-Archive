---
title: "No Rosegarden Automatically Installed with Ubuntu Studio 10.04"
date: 2010-06-23
forum: Ubuntu Studio
---

### Post by Smithernz on 2010-06-23
Having installed Ubuntu Studio 10.04 several times now, I have noticed that Rosegarden has not been automatically installed any of these times, so I have had to get it through the Synaptic Package Manager. From the description on the website ([https://help.ubuntu.com/community/UbuntuStudio/Audio](https://help.ubuntu.com/community/UbuntuStudio/Audio)) I get the impression that it should have been included. Is this intentional or have I done something wrong when installing?

---

### Post by cchhrriiss121212 on 2010-06-23
Rosegarden has been left out of studio for a few releases now, which should demonstrate that there are community docs out there that are not always up to date. I'm not sure why it was removed, possibly because it is KDE dependent?

---

### Post by Smithernz on 2010-06-23
So does the fact that it is KDE dependent mean that it won't work in Ubuntu Studio?

---

### Post by Pablo_F on 2010-06-23
Possibly, it was removed because it WAS KDE dependant (but I don't know).

The fact is that Rosegarden has migrated to qt4 (from versions beginning with 10.) so the KDE libraries are not needed anymore. Anyway, you can run kde apps in a gnome environment.

Just don't worry about it. If it is in the ubuntu official repos, you can consider it as part of ubuntu and therefore, your ubuntustudio.

---

### Post by sgx on 2010-06-23
KDE4 has become a shiny new Titanic. Fortunately the old 3.5 versions
can be found in cyberdumpsters. I'm glad they are using QT now. There
are still rafts of ridiculous dependencies floating around linux. I saw one last night, where an app required installing googlearth, while removing all the system hardware configuration tools.
Some devs are in total :confused:

---

### Post by Smithernz on 2010-06-24
:rolleyes: Well I think I'll stick to Ubuntu Studio for the time being, and hope I don't get tangled up in dependencies. Who knows, I may even get JACK working!

---

### Post by sgx on 2010-06-24
> **Smithernz said:**
> :rolleyes: Well I think I'll stick to Ubuntu Studio for the time being, and hope I don't get tangled up in dependencies. Who knows, I may even get JACK working!

jackd -d alsa -r 44100

is a basis to work from. Then start qjackctl, then start a jackd aware app
zynaddsubfx, and connect it to rakarrack for fx

qjackctl guide:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Cheers

---

