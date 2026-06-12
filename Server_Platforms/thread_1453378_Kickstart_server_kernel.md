---
title: "Kickstart server kernel"
date: 2010-04-13
forum: Server Platforms
---

### Post by fatfranko on 2010-04-13
Is there a way to use PXE to install the ubuntu-server edition so it uses the server kernel?  So far I can only get it to install the standard version with the generic kernel.  The post install script can install the server kernel and possibly  remove the generic one but I'd rather install the server one from the  beginning.  Is there a way to do it or am I left with the unclean  solution of install server kernel and purge the generic one?

I've looked through system-config-kickstart package and couldn't find an option for this, does it go by another name?

---

### Post by fatfranko on 2010-04-14
*bump* :)

---

### Post by vikjon0 on 2010-10-25
Not 100% sure how it is working with the installer, most of it seem to be built into the initrd, and there is only one netboot I think.

Have you tried running it in expert mode? 
You could also try running it agains the server cd (stored on the server). Point a web server to the CD and enter the address as mirror (select "enter manually" as country).
I guess the latter will not make any difference.

---

### Post by vikjon0 on 2010-10-26
I checked the server cd and your best best would be to run the server-seed 

label 999
	MENU LABEL Server expert mode
        KERNEL Ubuntu/lucidAltCD/linux
	APPEND  preseed/url=http://192.168.0.130/pxe/lucidAltCD/preseed/ubuntu-server.seed initrd=Ubuntu/lucidAltCD/initrd.gz
        TEXT HELP
        Boot Installer with server seed in expert mode
        ENDTEXT

Of course the ubuntu-server.seed must be in that location..which it will be if you replace AltCD with Server cd and copy the content of the CD there. netboot from any cd will do.

---

