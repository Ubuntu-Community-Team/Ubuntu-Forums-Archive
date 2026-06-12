---
title: "PXE install with kickstart does not work with expert mode?"
date: 2010-10-23
forum: Server Platforms
---

### Post by vikjon0 on 2010-10-23
I have a working pxe installation server using kickstart to install from the server instead of from the net.

The problem is thet the priority=low seem to ignored when used in combination with the kickstart file. It works if I remove the ks file.

Any ideas? 
I need the kickstart to install from web instead of CD. Can I do that any other way? I can set the mirror with preseed but I assume it only set the mirror as in normal CD installation?

> label 6
	MENU LABEL Install Lucid from local server - expert mode
        KERNEL Ubuntu/lucidALtCD/linux
	APPEND priority=low ks=http://192.168.0.130/pxe/lucidalt.cfg initrd=Ubuntu/lucidALtCD/initrd.gz
        TEXT HELP
        Install Lucid from local server - expert mode
        ENDTEXT

---

