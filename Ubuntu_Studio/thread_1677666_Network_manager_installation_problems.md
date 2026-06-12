---
title: "Network manager installation problems"
date: 2011-01-29
forum: Ubuntu Studio
---

### Post by Wejdan on 2011-01-29
Hi,

I've just had Ubuntu Studio Installed without internet access "it was telling me that we couldn't find network...etc"
after having it all installed well, I found out the I have no network manager, so I found this: [https://help.ubuntu.com/community/UbuntuStudioNetworkSetup]("https://help.ubuntu.com/community/UbuntuStudioNetworkSetup")... I installed *libnm-glib*, *libnm-uti* from network-manager folder, BUT, when I try to install the rest of deb files in these folders (network manager & network-manager applet) I get "Error: Dependency is not satisfiable"

any help with that please?

thank you

---

### Post by cchhrriiss121212 on 2011-01-29
All the dependencies are there on the disk, and the installer should tell you what one you need. All you need to do is install them in the right order.

---

### Post by mango42 on 2011-01-29
If I could be confident that I had all the facts at hand I would add to that wiki on this perennial knotty problem - but what do I know? ;-)

As **cchhrriiss** (who helped me out on this a while back) says, it seems to be important the order in which you apply the changes necessary to achieve net connection on UbuntuStudio. In 10.04 there was a new twist in that one needs to install *mobile-broadband-provider-xxx* from /pool/main/m before installing **nm-applet**

Just search this sub-forum for nm-applet and you should come across the right magic incantations, as I've temporarily forgotten* them - again! ;-)

* PCMCIA stands for "People Cannot Memorize Computer Interface Acronyms"...

---

### Post by Wejdan on 2011-01-29
Actually, it just worked with same steps that wouldn't work before, but after I got "wicd" installed...
I guess getting "wicd" added some missing dependencies that I couldn't find..

thanks :)

---

