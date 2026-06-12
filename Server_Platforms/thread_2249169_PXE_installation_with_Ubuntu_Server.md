---
title: "PXE installation with Ubuntu Server"
date: 2014-10-20
forum: Server Platforms
---

### Post by brice3 on 2014-10-20
Hello everybody,

I'm trying to configure my Ubuntu Server to make PXE installation on several computers in the same time with Ubuntu 14.04. 

Everything is fine until the installation on my futur well installed computer. 

Here is my code on /var/lib/tftpboot/pxelinux.cfg/default

```

[FONT=arial][COLOR=#000000]DEFAULT vesamenu.c32[/COLOR]timeout 100
display boot.msg
menu background splash.png
menu title Welcome to my awesome installer

label Install new computer
  kernel ubuntu-installer/amd64/linux
[/FONT][COLOR=#000000][FONT=Consolas][FONT=arial]  append ks=http://ip.local.server/ks.cfg vga=normal initird=ubuntu-installer/amd64/initrd.gz[/FONT]
[/FONT][/COLOR]
```

At the beginning I thought that my kickstart file wasn't found by I've added an static ip and I can see on my server (with a tcpdump) that some requests are done with this ip. 

Obviously, I added 

```

install
url --url http://ip.local.server/ubuntu-trusty
[...]
```

on my ks.cfg

One more detail, I checked the url [COLOR=#000000][FONT=Consolas]http://ip.local.server/ubuntu-trusty and it's working. 
[/FONT][/COLOR]
I don't know where this problem comes from. Does anybody have an idea?

Thank you in advance!

---

