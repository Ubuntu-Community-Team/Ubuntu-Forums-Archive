---
title: "Server Kernel versus Desktop Kernel"
date: 2008-02-12
forum: Server Platforms
---

### Post by lespaul_rentals on 2008-02-12
Has anyone here ever used a desktop kernel for a server?  I'm curious to know if it made a large performance impact.  Obviously, if you are running X and a full-fledged desktop enviroment, the daemon performance is going to be affected no matter what kernel you use, but if you have a command-line system using the desktop kernel, is there really much of a difference?  Seems to me that the flags the kernels are compiled with would make a difference (i.e. process priority) but anyone have an opinion?

---

### Post by Jjan on 2008-02-12
That's what I'm trying (desktop kernel for server) We'll see how far it goes.

---

### Post by ikonia on 2008-02-12
you won't find anything in performance at a home user level.

The server kernel just has more common server hardware configurations supported and installed.

---

### Post by houk on 2008-04-21
server kernel see 4GB of RAM on AMD x2 5200 and MSI K9N SLI but NVIDIA restricted driver not install. It say "could't install on a xen kernel" ?

---

### Post by formol on 2008-06-07
how do you switch to a kernel to another?

I installed Ubuntu-Server for Raid capacity, then I installed 
> apt-get install ubuntu-desktop 
for gnome graphical interface.

now I want the 2.6.24.18-desktop kernel instead of the server one - to be able to install the nVidia drivers.

thank you in advance

---

### Post by lordViN on 2008-06-16
hi,

I have the same problem, when I try to install the nvidia driver, the installation fails and it says that I have a xen kernel which I sopouse is because I'm using ubuntu server. any ideas??

---

### Post by Rhubarb on 2008-06-16
I have the desktop kernel installed on my Ubuntu server (CLI only, no GUI or desktop) - simply because the server kernel doesn't support my Crusoe CPU.
My server is a small power efficient old laptop with a broken screen :D

I haven't found any clear performance issues, but I haven't tried the server kernel to compare.

---

### Post by formol on 2008-06-16
lordVIN:

you can install the appropriate kernel using the .deb at [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-ubuntu-modules]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-ubuntu-modules")

installing this also give you the choice in the grub menu.

personnaly, I installed linux-ubuntu-modules-2.6.24-18-generic_2.6.24-18.26_i386.deb
and I was able at this point to install the nvidia drivers.

---

