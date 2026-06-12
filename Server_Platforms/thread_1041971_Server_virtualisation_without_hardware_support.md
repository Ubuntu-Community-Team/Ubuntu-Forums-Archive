---
title: "Server virtualisation without hardware support"
date: 2009-01-17
forum: Server Platforms
---

### Post by nocturn on 2009-01-17
I need to run some sort of virtualisation on my home server to be able to run Zimbra (it conflicts with the locally installed ldap and webserver).

My box does not support hardware virtualisation though so I cannot use the default KVM option.
I experimented with Xen on Ubuntu, but it didn't go really well (it works fine on CentOS, but not Ubuntu) and I prefer to keep a running kernel from the mainline repos.

So, my question is what other options you can recommend?  This is a headless box running Ubuntu Server 8.04 (32-bit).

thanks

---

### Post by HermanAB on 2009-01-17
Use VMware Server version 1.x (I don't like the version 2).  It is free and works very well.  I always ensure that I have the kernel source on my machines and that I can compile the kernel, once that works, installing VMware is straight forward and it will compile and install itself.

---

### Post by albinootje on 2009-01-17
> **nocturn said:**
>  So, my question is what other options you can recommend?  This is a headless box running Ubuntu Server 8.04 (32-bit).


Since years I'm using OpenVZ, it's a bit comparable with Linux Virtual Server or UserModeLinux.

You can of course run Vmware or VirtualBox headless, but OpenVZ has very little overhead.

You will need a kernel with OpenVZ support, and you need to make yourself comfortable with using templates, and using the vzctl command, or go for the GUI options right away.

See here :
[http://en.wikipedia.org/wiki/OpenVZ](http://en.wikipedia.org/wiki/OpenVZ)
[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

Webvz looks very promising : [http://webvz.sourceforge.net/](http://webvz.sourceforge.net/) 
and so does this : [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

.. but I haven't tried those yet, because I'm very happy with the command line options I already have.

I had Zimbra running via an OpenVZ VPS a while back just for testing, worked fine, except that during the Zimbra installation Zimbra wanted a lot of resources, so I had to adjust settings for that temporarily.

---

### Post by Cracauer on 2009-01-17
VMware is still worth the money if you have an OS that supports it. It's really one of the better commercial packages out there.

I don't think that VMware supports most of the hardware support for visualization, namely the context switchable TLBs, at this time in the first place. So I wouldn't worry about the hardware.

Just get enough RAM.

---

### Post by nocturn on 2009-01-17
> **Cracauer said:**
> VMware is still worth the money if you have an OS that supports it. It's really one of the better commercial packages out there.

I don't think that VMware supports most of the hardware support for visualization, namely the context switchable TLBs, at this time in the first place. So I wouldn't worry about the hardware.

Just get enough RAM.

Thanks for the suggestion, but I'm avoiding VMWare because it's not Free Software.  If I would be willing to invest money, I'd upgrade the machine to one that supports hardware virtualistaion and just use KVM.

---

### Post by Cracauer on 2009-01-17
Well, since you need enough RAM anyway and since DDR2 RAM is cheaper, I think you should really think about consing up the money for a minimal new combo. Might also save some power.

---

### Post by albinootje on 2009-01-17
> **nocturn said:**
> Thanks for the suggestion, but I'm avoiding VMWare because it's not Free Software.  If I would be willing to invest money, I'd upgrade the machine to one that supports hardware virtualistaion and just use KVM.

Good, I don't like using VMware either for the same reason, and some other reasons :)

OpenVZ, Linux Virtual Server and UserModeLinux are all open source software, try them.
I have good experiences with OpenVZ. 
Before that I used "jails" on FreeBSD which was a little bit more work to deal with.

I recommend using only ssh on the "Hardware Node" if needed, and putting the rest of the services all on the various VPS-es (or VE, or containers as OpenVZ calls them).

---

