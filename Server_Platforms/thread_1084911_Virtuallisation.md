---
title: "Virtuallisation"
date: 2009-03-02
forum: Server Platforms
---

### Post by BradleyAtkins on 2009-03-02
Hi I could do with some advise on virtualisation.

I want to host a few instances of server, probably Ubuntu server on a single machine at the same time. I think something like Virtual box would probably be fine for a novice like me to get started with virtualisation. However I would like to know if it would be possible to give each instance its own IP address on my home network. Would I need to fit multiple NIC's?

This is all so I can practice writing cross server tools, with probably an application server and a DB server behaving as independant machines on a network.

Cheers

Brad

---

### Post by windependence on 2009-03-02
Well, I don't know about Virtual Box but with VMware ESXi or VMware server it would be a snap to do what you want. Only one NIC required. You can even set up virtual switches and routers.

-Tim

---

### Post by LegendofTom on 2009-03-03
Any one of the many virtualization programs should allow an individual IP for each instance you have created. Just try Virtualbox and see what happens.

---

### Post by BradleyAtkins on 2009-03-05
Thanks for that I will try it out soon

---

### Post by BradleyAtkins on 2009-03-05
Thanks thats very specific and helpful

---

### Post by Seq on 2009-03-05
you'll want to investigate vmbuilder (package name is ubuntu-vm-builder) if you're going to be prototyping multiple Ubuntu VMs. If you use something like approx to proxy and cache apt, you can build a brand-new, customized server VM in about 3 minutes. It works with virtualbox in addition to libvirt/kvm (which is what I use).

---

### Post by Robstarusa on 2009-03-05
I'd recommend proxmox ve.  It is a bare metal installer based on the Debian kernel that powers hardy, with a MUCH newer kvm version than comes with ubuntu & fantastic web based management tools.  It supports "on line" (although not really 'live') migration between servers in a cluster.

---

### Post by jeffsa12 on 2009-03-05
Yes it's possible to do what you want with one network card with xVM VirtualBox 2.1.4. You'll build a "virtual hardware network card" on your "virtual PC", with it's own IP addy.

I just did it a few days ago. If you need setting details, ete. after you try, I'd be glad to help.

---

### Post by BradleyAtkins on 2009-03-06
Oh thats great thanks, I will keep that in mind. Am currently looking for a small machine to host it all on...

---

### Post by BradleyAtkins on 2009-03-06
Thanks, sounds a little more powerful than I need but will look at all of these when I buy the server.

Cheers

---

