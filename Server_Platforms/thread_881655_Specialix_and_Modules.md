---
title: "Specialix and Modules"
date: 2008-08-06
forum: Server Platforms
---

### Post by DjangosClouds on 2008-08-06
Hi,
   I'm a bit of a noob with this stuff. I'm setting up a server for someone and they need Ubuntu Server Feisty Fawn working with a Specialix box.

   So I hack around the net and it says that I can enable it if I rebuild the kernel (I've not done that before - minor panic!) so I download the source and start flicking through the config file /boot/config-2.6.20-15-server and it says:
```
CONFIG_SPECIALIX=m
```
Which, I think, means that it's already compiled as a module. That would mean that I don't need to recompile the kernel, just stick the module name in /etc/modules

My question is this: What is the module name? I can get a list of loaded modules (lsmod) but I can find a list of all the modules that I can use anywhere.
I've tried adding 'specialix' to the end of /etc/modules but it doesn't show up when I do an 'lsmod'.

I'm a bit stuck - anyone got any ideas?
Cheers,
   Al

---

### Post by DjangosClouds on 2008-08-06
Okay, it seems that the module is loading but for some reason I can't see it when I do lsmod. by using dmesg I can see some output from the module so it must be working - I just haven't got it set up right.
If I work out how to install this thing I'll update this thread - maybe someone else will find this thread useful one day.

   -Al

---

