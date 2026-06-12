---
title: "Programs won't load"
date: 2014-03-25
forum: Ubuntu Development Version
---

### Post by ramesses2 on 2014-03-25
Hi, I've just installed 14.04 amd64 and after installing some stuff it won't load. 2 programs I've discovered so far are virtualbox and synaptic. They look as tho they are loaded in the sidebar but nothing is coming up on the screen. With synaptic it asks for a password and once I've submitted it, nothing happens. If I start up vbox through terminal I get a list of what appears to be benign qt warnings. No errors show up when attempting to start synaptic through terminal.

---

### Post by ramesses2 on 2014-03-25
I'm going to try i386 I forgot that amd64 can be kinda buggy.

---

### Post by Toz on 2014-03-26
*Moving to **Ubuntu+1***

14.04 is still in beta. That being said, I don't think "amd64 can be kinda buggy" is a fair statement. I'm using amd64 in officially released versions and it works just fine. You may be suffering from "beta bleeding". I'll leave it in this sub-forum to see if others can confirm these issues.

---

### Post by ventrical on 2014-03-26
> **ramesses2 said:**
> Hi, I've just installed 14.04 amd64 and after installing some stuff it won't load. 2 programs I've discovered so far are virtualbox and synaptic. They look as tho they are loaded in the sidebar but nothing is coming up on the screen. With synaptic it asks for a password and once I've submitted it, nothing happens. If I start up vbox through terminal I get a list of what appears to be benign qt warnings. No errors show up when attempting to start synaptic through terminal.


Have you done all of your updates and upgrades?

```


sudo apt-get update


sudo apt-get dist-upgrade


```

---

### Post by ramesses2 on 2014-03-26
I just kept going backwards until I found a version of vbox that would  work off of the normal local repos. Ended up with 13.04 64. I needed  something that will work out of the box so I wouldn't have to deal with  others who weren't 'nix savvy.

---

### Post by grahammechanical on 2014-03-26
I have just installed the image from 25/03/2014 and I have not had any problem installing Synaptic and using it to install other software. I do not use Virtual Box. The software centre is offer version 4.3.6

Regards.

---

### Post by su:bhatta on 2014-03-28
I am using an updated version of Ubuntu Studio 14.04 AMD64, installed daily version of Early February, never had an issue with Synaptic.
Cannot say about Vbox though, have not installed/used in this installation.

---

