---
title: "sl-modem dependency probleme"
date: 2004-12-30
forum: Repositories &amp; Backports
---

### Post by dude on 2004-12-30
I have a laptop with a build-in modem. From lspci:
0000:00:1f.6 Modem: Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 03)
0

In order to work it needs the sl-modem-module which I builded and installed using the module-assistant tool. I have the 2.6.8.1-4-686 kernel from Ubuntu installed. Now getting to the probleme: using sudo module-assistant  auto-install sl-modem-source I get the following the error:

sl-modem-modules-2.6.8.1-4-686 depends on kernel-image-2.6.8.1-4-686, but: kernel-image-2.6.8.1-4-686 is not installed.

Off cause, using ubuntu kernel, I have linux-image-2.6-686 installed and not kernel-image-2.6.8.1-4-686. Is this a bug or have I missed something?

Best wishes,
Thorbjoern

---

### Post by conall on 2005-06-15
You have to edit the package's control file to get it running. At the control file (find it at /usr/src/modules/sl-modem/) there's a line that tells you the dependencies the package needs. You will find "kernel-image" there, switch to "linux-image". Then, rebuild the package via module-assistant and voilá. I hope that it helped.

---

### Post by az on 2005-06-15
No!  That module was compiled for the stock kernel.  Either boot into your system with the 386 kernel or find another way to get onto the net and install the source.  (sl-modem-source)

You need to compile the module for the 686 kernel yourself.

sudo apt-get install build-essential 

Also install the linux-headers for the 686 kernel (it is not on the cd) and the sl-modem-source package

unpack the source
and cd into the directory

sudo debian/rules binary

install the deb packages it makes for you.

---

### Post by delltony on 2005-07-26
[QUOTE=azz]No!  That module was compiled for the stock kernel.  Either boot into your system with the 386 kernel or find another way to get onto the net and install the source.  (sl-modem-source)

You need to compile the module for the 686 kernel yourself.

sudo apt-get install build-essential 

Also install the linux-headers for the 686 kernel (it is not on the cd) and the sl-modem-source package

unpack the source
and cd into the directory

sudo debian/rules binary

install the deb packages it makes for you.[/QUOTE]

I have downloaded the build-essentials and the header files for 686-smp 
i then downloaded sl-modem-source and followed he binary build instructions you stated.
here is the error i get any idea why?
```
sudo debian/rules binary
dh_testdir
cd modem ; /usr/bin/make SUPPORT_ALSA=1
make[1]: Entering directory `/home/delltony/mytemp/modules/sl-modem/modem'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/delltony/mytemp/modules/sl-modem/modem'
make: *** [build-arch-stamp] Error 2

```

---

