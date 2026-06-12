---
title: "VMware xorg.conf hardware virtualization"
date: 2011-05-12
forum: Virtualisation
---

### Post by Crash1hd on 2011-05-12
Hey Everyone,

I have VMware Player loading my Ubuntu installation loading in XP VMware player as a guest OS and all is working great as long as I remove the xorg.conf file (which means that when I boot Ubuntu natively i have to put it back.  I am looking for a way to have ubuntu know I am loading it in VMware and remove or rename the xorg.conf file or call an empty xorg.conf (preferred method)  I have tried everything I can think of from creating ~/.xsessionrc script and adding something like this
lspci | grep -i 'vmware svga ii' 2>&1 >/dev/null
export XORGCOFIG=xorg-vmware.conf

but all that does is cause me to get to the login page and it starts to load and then restarts over and over

Any advice?

---

