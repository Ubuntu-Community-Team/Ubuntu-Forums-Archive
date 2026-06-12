---
title: "Ubuntu Jails (Virtualization Options)"
date: 2012-02-17
forum: Server Platforms
---

### Post by monarckco on 2012-02-17
I've been searching the web for the past few days looking for something for Ubuntu that rivals that of FreeBSD's jails system. I've come up fairly empty handed, but probably just missed it.
 
I think it might be easier if I went ahead and explained my situation. I'm working for a company that offers web hosting and currently does this through an older version of FreeBSD. The tech before me was comfortable with it, but I'm much better with Ubuntu. They currently have 4 (soon to be 5) jails running inside of the machine all with their own IP address (apparently did this because of SSL). 
 
I would really love to build the new server with Ubuntu, but need to be able to accomodate the current setup. Any ideas?

---

### Post by kevdog on 2012-02-17
Do you need an ssh jail? jailkit?

---

### Post by monarckco on 2012-02-17
All I really need is an option that allows multiple SSL certificates for both Apache, POP, and SMTP.  That's really all I need.  
 
I've read through jailkit a bit, but wasn't sure if it could handle it (each jail with its own IP)?  I'll be honest though, although I have quite a bit of server management experience, I've never needed to deal with jails before.  
 
Could jailkit do the same thing as FreeBSD jails?

---

### Post by monarckco on 2012-02-22
So I'm guessing the reason I haven't gotten a response is because nothing really exists currently for Ubuntu?

It would be disappointing to see Ubuntu not be able to do something that FreeBSD does so easily.  I really prefer running Ubuntu over anything else, so I am definitely not attacking it.  I am honestly disappointed.

Anyway, I have decided to grit my teeth, study up on some FreeBSD, and go ahead and install its latest version as the new server's OS.  Oh well, I'm sure there will be an option in the future for Ubuntu, considering how amazing jails are and how big the community is.

---

### Post by redmk2 on 2012-02-22
> **monarckco said:**
> So I'm guessing the reason I haven't gotten a response is because nothing really exists currently for Ubuntu?

It would be disappointing to see Ubuntu not be able to do something that FreeBSD does so easily.  I really prefer running Ubuntu over anything else, so I am definitely not attacking it.  I am honestly disappointed.

Anyway, I have decided to grit my teeth, study up on some FreeBSD, and go ahead and install its latest version as the new server's OS.  Oh well, I'm sure there will be an option in the future for Ubuntu, considering how amazing jails are and how big the community is.

The first thing that comes to mind is Linux [**_[COLOR="Blue"]KVM[/COLOR]_**]("http://www.linux-kvm.org/page/Main_Page") for full virtual machines.  You can also run [**_[COLOR="Blue"]OpenVZ[/COLOR]_**]("http://wiki.openvz.org/Main_Page") (this is a kernel hack for containers).  Look at [**_[COLOR="Blue"]Proxmox[/COLOR]_**]("http://www.proxmox.com/") for a complete implementation of both of these.  I'm not sure that OpenVZ will be the way of the future with the new userland Linux Containers (LXC) becoming an alternative.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.ibm.com/developerworks/linux/library/l-lxc-containers/") for a start.  [**_[COLOR="Blue"]Here[/COLOR]_**]("https://help.ubuntu.com/community/LXC") is an Ubuntu community help page on LXC.  I believe that Proxmox is also moving towards implementing LXC in the future.

---

### Post by TheFu on 2012-02-22
I'd look into LXC.  You probably want to avoid full virtualization overhead that KVM/QEMU would bring.  I've read that there are some issues with OpenVZ network security, but don't know this to be true first hand.  The network guys at my LUG prefer LXC over OpenVZ.

[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

---

