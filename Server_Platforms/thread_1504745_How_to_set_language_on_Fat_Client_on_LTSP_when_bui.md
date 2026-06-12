---
title: "How to set language on Fat Client on LTSP when building the IMG file ???"
date: 2010-06-08
forum: Server Platforms
---

### Post by ckleuser on 2010-06-08
Hi there,

I am having some trouble to setup a default language on a FAT Client on a LTSP install.
My running server is a Ubuntu 9.10 - LTSP install in 64 bits and my server default language in Portuguese-BR.

But when I try to run the command "sudo ltsp-build-client" with the apropriate
settings created on ltsp-build-client.conf file (as [https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)) I ALWAYS get the image created all in English and when I boot
up all my fat client terminals, everything is in english and I didn't find anything that
could change this, even on the System -> Admin -> Supported Lang  Tab....

The question are, IS there a way to build this image and specify the language on ltsp-build-client.conf file or any other way ????


Thanks

[],s Cristian

---

### Post by tasper on 2011-03-29
sudo apt-get install ltsp.docs
man lts.conf
env | grep ^LANG=
locate lts.conf

edit the right one
add line to lts.conf like this:
LDM_LANGUAGE= (LANG fron env)

---

