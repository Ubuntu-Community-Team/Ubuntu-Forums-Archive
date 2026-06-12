---
title: "Installing Webmin"
date: 2008-11-27
forum: Server Platforms
---

### Post by happyhacker on 2008-11-27
During the install of webmin I was asked to select an Apache option. Looking in the webmin manual I saw something relating to apache-perl so I selected that option.

Was this right or should I make any adjustments?

Also, does this mean I have a full Apache server running now so I acn serve websites, etc?

---

### Post by gg234 on 2008-11-27
try this guide [http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

---

### Post by rslrdx on 2008-11-27
> **cantthinkofanickname said:**
> During the install of webmin I was asked to select an Apache option. Looking in the webmin manual I saw something relating to apache-perl so I selected that option.

Was this right or should I make any adjustments?

Also, does this mean I have a full Apache server running now so I acn serve websites, etc?


webmin uses works out of its own http server, that way if your apache server goes down, you can access webmin still.

do you by chance know what the question was? i think webmin creates a install log, and i dont think you should worry to much about it, webmin only needs to information to know where the config files are, its not like webmin works as a apache module or even a plugin. if you need to make ajustments, you only need to make them on the webmin part, so that it will find the correct files to show you, or maybe you have to install some library that it needed to do something, but nothing that makes apache stop working.

installing webmin doesnt make your computer a server, did you install the server or Desktop version of ubuntu? 

as far as hosting goes, if apache was installed and is all that your pages require, than yes, you have a server working, but only in the sense that it servers pages over http, doesnt mean its out on the web.

---

### Post by happyhacker on 2008-11-28
Can't remember the question but Webmin filemanager is working OK after I reinstalled Java. Webmin does not show an Apache server running so I guess it was not important. I have a server and trying to grapple with the prehistoric command line and that 1950s stuff called VIM!

---

### Post by rslrdx on 2008-11-28
use nano to edit files... its easy..

---

