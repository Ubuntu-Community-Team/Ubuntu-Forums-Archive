---
title: "Hi, The Server version come with Graphic mode?"
date: 2006-09-18
forum: Server Platforms
---

### Post by collazo98 on 2006-09-18
Thanks](*,)

---

### Post by bswilson on 2006-09-18
No.  That's one of the differences between the server and desktop versions of Ubuntu (among many others).  If you've installed the server edition and found you want the graphical interface, the easiest way is to install the ubuntu-desktop package.

```
$ sudo apt-get update;sudo apt-get install ubuntu-desktop
```

That will do it for you.  However, note that there are other desktop environments such as **xfce** that you can install that many feel perform better than Gnome or KDE.

---

### Post by cptnapalm on 2006-09-18
You can install X if you want to.  Best idea, if that is what you'd like, would be to install X, but not gdm (or kdm or wdm).  Then when you are on the server and want to do something, you can type startx at the shell prompt, do your stuff and then exit X when you are done.  That way, you can keep the machine as dedicated to server stuff, while providing a graphical environment when you want one.

My recommendation would be to run a light weight window manager rather than the bulkier ones.  Fluxbox, XFCE or Window Maker are all good candidates.

---

### Post by -J- on 2006-09-18
Most servers that I've setup Xforwarding with ssh is plenty. If your looking to run a GUI installer, such as Oracle it works fine without having all the Xorg/Gnome/KDE... installed.

Just make sure you have Xforwarding enabled on the server in /etc/ssh/sshd_config:
X11Forwarding yes
X11DisplayOffset 10

from a graphical client -X enables xforwarding:
ssh -X user@host

references:
man sshd_config
man ssh_config 

then run your app, beware, this can be laggy over a slow network connection.

less packages, less to break, less to patch... something like that.

---

### Post by wwitthoff1 on 2006-09-19
> **cptnapalm said:**
> You can install X if you want to.  Best idea, if that is what you'd like, would be to install X, but not gdm (or kdm or wdm).  Then when you are on the server and want to do something, you can type startx at the shell prompt, do your stuff and then exit X when you are done.  That way, you can keep the machine as dedicated to server stuff, while providing a graphical environment when you want one.

My recommendation would be to run a light weight window manager rather than the bulkier ones.  Fluxbox, XFCE or Window Maker are all good candidates.

How does one go about doing that with the server CD.

---

### Post by OmahaVike on 2006-09-19
from what i've been reading, the reason why there is no GUI component on a server install is *only* because it sucks down so many resources.

so can anyone please shed some light on this following technique?

install regular desktop method, then change the /etc/X11/default-display-manager (wipe out the entry, don't forget to make a backup copy).

therefore, it'll boot you into command line and not load the heavyweight GUI, but yet use startx to get to the GUI portion?

anything amiss with this approach?

thanks for any guidance.

---

