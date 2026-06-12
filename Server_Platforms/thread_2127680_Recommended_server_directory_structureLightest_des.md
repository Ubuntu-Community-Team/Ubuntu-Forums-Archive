---
title: "Recommended server directory structure/Lightest desktop possible"
date: 2013-03-20
forum: Server Platforms
---

### Post by DarrylLicke on 2013-03-20
I intend to use my recently acquired Shuttle PC (1.8Ghz celeron) as a sand box application and web server for my internal network. Knowing I'll be going off of this [http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html) webpage, where would be the ideal location to install application beyond what comes with Ubuntu server. I already have Tomcat installed as well as a few others but beyond apt I may want to install my own stuff.

/

I'm not sure the set up can handle having a desktop running as the response time even using Xubunut (Lubuntu was bugging too) so once I have it set up I may want a extremely minimal (window manager and a basic browser) desktop. Recommendations?

When I get home I can give more details on the set up of the box.

---

### Post by cariboo on 2013-03-21
My server only has a power cord and network cable connected, so I administer it remotely, file manipulation is done via sftp, and everything else I do via ssh. That being said, you can install any graphical desktop, just  don't install a desktop manager eg: gdm, kdm, xdm etc, then at the prompt, use:

```
startx
```

to start the desk top when needed, and log out when you are finished.

---

