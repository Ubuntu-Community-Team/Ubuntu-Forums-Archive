---
title: "Network boot"
date: 2010-03-23
forum: Server Platforms
---

### Post by vader95 on 2010-03-23
Hi, 

I was wondering if there is anyway that i could put ubuntu onto a server, then when i want to go to ubuntu, do a network boot.

Is there anyway that i can do this through ubuntu?


thanks,
vader95

---

### Post by EmanresuusernamE on 2010-03-23
I'm not fully sure if this will work for you as I only have a private server on the internet and not on a personal network to boot off of just yet, but give this a try:

[http://nixcraft.com/getting-started-tutorials/474-ubuntu-linux-network-installation-using-boot-server.html](http://nixcraft.com/getting-started-tutorials/474-ubuntu-linux-network-installation-using-boot-server.html)

---

### Post by vader95 on 2010-03-23
Thanks for the reply,

that isn't exactly what i meant, i meant have an ubuntu install on a network location and boot to that and use the image on the server.

Thanks anyway,

vader95

---

### Post by KB1JWQ on 2010-03-23
Yes.

Your client has to support PXE booting, and you need to have the infrastructure to support it (typically a DHCP server that knows what you're doing and an NFS server that hosts the image you want to use).
[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server) seems like a good starting point.

Fun idea-- I like it!

---

### Post by vader95 on 2010-03-23
Thanks,

I'll look at that.  I have a computer with 3 windows partitions and can't get ubuntu installed with swap, which i would like.  I am looking into this.


Thank you,
vader95

---

### Post by KB1JWQ on 2010-03-23
Even though they talk about installers, try running the liveCD initially.  That may get you at least moving in the proper direction.  If you get stuck, just ask!

---

### Post by vader95 on 2010-03-23
I have used the live cd.


Thanks,
vader95

---

### Post by dudumomo on 2010-03-23
Why not installing 2 ubuntu on the same machine ?
Your Server and your Desktop ?
Or why not only a Desktop but with a virtual machine running Ubuntu Server.

---

### Post by KB1JWQ on 2010-03-23
Probably because a network boot grants increased flexibility without endangering his local disks. :-)

---

### Post by natbob1 on 2010-03-23
I have been working on a system to accomplish the same thing.  Even if your network card doesn't support PXE, a GRUB boot floppy with complied in support for your network card can load the kernel and initrd from a tftp server. The root filesystem can then be mounted through a nfs running from the same server.

---

### Post by vader95 on 2010-03-23
@dudumomo,  Because i already have 3 partitions for windows, and i would like to have some kind of swap.

@natbob1,  Do you have a way to do this

---

