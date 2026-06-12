---
title: "Updating The OS - securiy fixes etc"
date: 2005-08-19
forum: Server Platforms
---

### Post by 0tk on 2005-08-19
HI,

How can I update my Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) with the latest security patches and version etc? i.e. something similar to the Windows update?

Also, I installed other applications like Midnight commander etc with apt-get.  Is there a way I can upgrade these to the latest version as well?  Something similar to portupgrade of BSD?

Is there anything to do with apt-get etc please?  Tried to search the ubuntu site documentation, but didnt find much information.

regards,
0tk
[http://www.0tk.net](http://www.0tk.net)

---

### Post by duffman25 on 2005-08-19
[QUOTE=0tk]HI,

How can I update my Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) with the latest security patches and version etc? i.e. something similar to the Windows update?

Also, I installed other applications like Midnight commander etc with apt-get.  Is there a way I can upgrade these to the latest version as well?  Something similar to portupgrade of BSD?

Is there anything to do with apt-get etc please?  Tried to search the ubuntu site documentation, but didnt find much information.

regards,
0tk
[http://www.0tk.net](http://www.0tk.net)[/QUOTE]

Ubuntu 5.04 comes configured to search for updates with the update-notifier applet (a small icon in the taskbar which shows the updates you are missing). Another way is running:

# sudo apt-get update
# sudo apt-get upgrade

By the way: the applet also uses the apt infrastructure, so it's the same thing :) Apt will search for updates on the repository of packages for every app you have installed, so everytime you apt-get update && upgrade all upgradable packages will update.

---

### Post by 0tk on 2005-08-19
HI Duffman,

thanks .. it worked :)

regards
0tk

---

