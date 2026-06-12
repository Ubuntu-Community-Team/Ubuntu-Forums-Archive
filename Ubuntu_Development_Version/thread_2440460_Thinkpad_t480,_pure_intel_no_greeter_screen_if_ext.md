---
title: "Thinkpad t480, pure intel: no greeter screen if external monitors are connected"
date: 2020-04-10
forum: Ubuntu Development Version
---

### Post by timrichardson on 2020-04-10
When booting from a live USB (beta release), external monitors connected to the laptop are not detected,but log in succeeds.
I have installed 20.04 to this laptop. Clean install, not an upgrade.
When booting from the install, the greeter screen is never reached if external monitors are connected at startup.
I get the spinning ubuntu logo, and nothing more. I can not change to virtual terminals. 
In recovery mood, I can log in. 
I am used to having such problems with Nvidia graphics is involved, but this is not the case on this laptop. It has been happily running 18.04. 

External displays are recognised if they are connected after login. 

On the last login, I killed the machine by hardware forcing a power-off.

in Xorg.0.log but nothing looks wrong. 

In dmesg there is this:
   14.174138] kernel: typec_displayport port1-partner.0: failed to enter mode

googling for this shows quite a few recent hits, relating to kernel 5.4 and arch.

---

### Post by timrichardson on 2020-04-10
remove splash from /etc/default/grub
has fixed it.

---

### Post by timrichardson on 2020-04-11
bug report against plymouth is here: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1872159](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1872159)

---

