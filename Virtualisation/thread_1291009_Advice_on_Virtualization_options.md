---
title: "Advice on Virtualization options"
date: 2009-10-14
forum: Virtualisation
---

### Post by tenmillionmilesaway on 2009-10-14
Hi,

I have a server with ubuntu 9.40 (64bit) server installed on it.  It has 12gig of ram and a quad core processor.  We have one external ip address for this box, although i think it is possible to configure more.  I don't have physical access to the box, it is not on our network and I cannot change the installed os.  (i do have root access tho)

This is going to be a general purpose dev / demo / testing server for us and for the moment will run things like subversion, tomcat, apache, continuous integration.  My original plan was one vm for subversion and build tools and one or more vms for testing development tomcat / apache boxes. We may also need a vm for production stuff later on.  I also want the option to be able to move vms to different physical machines in the future.
I preferably want a free solution, but not necessarily open source.  These will be headless boxes so im not bothered about graphical performance or sound.  Im planning on all the vms being based on Ubuntu too.

We want to be able to access our vms externally, but with the one ip address, is this possible?

My original plan was to follow the instructions here:
[https://help.ubuntu.com/9.04/serverguide/C/virtualization.html](https://help.ubuntu.com/9.04/serverguide/C/virtualization.html)
and go with a KVM based solution, but after doing some more research i'm not so sure this is the best solution.

I had a quick look at VMware ESXi, but have also seen people talking about openvz.  Ive also seen Proxmox mentioned, but like I said, i dont want to / cant change the os.


Any comments / advice would be gratefully received

---

### Post by sh1ny on 2009-10-14
What exactly are your results from the research against KVM ? I am using it on a few live production servers and so far it's been acting out great.

---

### Post by tenmillionmilesaway on 2009-10-14
> **sh1ny said:**
> What exactly are your results from the research against KVM ? I am using it on a few live production servers and so far it's been acting out great.

I haven't deployed in production yet, Im just trying to decide on the best way forwards.

I have deployed a test instance using kvm on my laptop though, and so far it seems good.  Im just playing around with the config options.

---

