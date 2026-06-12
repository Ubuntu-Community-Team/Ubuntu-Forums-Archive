---
title: "install virtualbox (non-free) without having X installed"
date: 2008-05-05
forum: Server Platforms
---

### Post by adieb on 2008-05-05
Hallo.

I want to install virtualbox on a server, where no X is installed. (And I don´t want X on it.)
So i added the Sources to my apt.sources file and when I typed:
```
apt-get install virtualbox
```
it wanted to install all the Xorg Stuff like:
 ```
defoma fontconfig fontconfig-config libaudio2 libdirectfb-1.0-0 libfontconfig1 libfreetype6
  libice6 libicu38 libidl0 libjpeg62 liblcms1 libmng1 libpng12-0 libqt3-mt libsdl1.2debian
  libsdl1.2debian-alsa libsm6 libx11-6 libx11-data libxalan110 libxau6 libxcb-xlib0 libxcb1
  libxcursor1 libxdmcp6 libxerces27 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxrandr2
  libxrender1 libxt6 ttf-dejavu ttf-dejavu-core ttf-dejavu-extra x11-common
```


Do I really really need these to run virtualmachines through
```
VBoxManage startvm VMNAME -type vrdp
```
??

I cannot imagine that, because there won´t be any X-Output generated. Everything is going to be streamed over VRDP.

So how can I install it and skip X??

Please help.


Best regards,

Adieb

---

### Post by azadpanchi on 2008-07-25
I do not see any replies to this for a long time so I will say this.  Those files and libraries are required for the package you are trying to install, as such I will recommend installing them.  Without intimate knowledge of inner workings of virtual box this is going to be the only answer.

---

