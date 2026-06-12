---
title: "Ubuntu 14.04 Server. ISO Install, Adding drivers to ISO"
date: 2017-07-14
forum: Server Platforms
---

### Post by maydaydown on 2017-07-14
Hi All,

I'm trying to set up Mellanox VPI Ethernet drivers to be pre loaded when we install Ubuntu server. Currently I've just downloaded the ISO, mounted it to a flash drive and tested the install. But when it gets to detecting network setup it only sees onboard Intel i3 devices (as I expected) If I GREP LSPCI it does see the card. I do have drivers from the site I just have no clue how to modify the install ISO to include the correct drivers.



Excuse my lack of knowledge and poor language as I do not know much about linux (and used to CentOS mostly) 


Also to note, 14.04 is a hard requirement. 


Thanks

---

### Post by mastablasta on 2017-07-17
have a look:

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)


not sure but maybe any of the GUI apps could do it as well on server image (alt. for remastersys):

[https://askubuntu.com/questions/190133/what-are-the-alternatives-for-remastersys](https://askubuntu.com/questions/190133/what-are-the-alternatives-for-remastersys)

another option is to add drivers to the ISO and then run a script when instalation is finished or something like that.

---

### Post by maydaydown on 2017-07-17
Thanks for the info, I'll look into it.

Looks like we need firmware from Mellanox as well, however their manual actually has a guide for setting up the drivers in a "Diskless Machine" via initrd. territory  of which I'm new too. :popcorn:

---

