---
title: "Any suggestiond for a minimal distro for VMware"
date: 2008-12-29
forum: Virtualisation
---

### Post by thomasr on 2008-12-29
Looking for a minimal distro to install VMware server on. Only purpose will be to serve up virtual machines.

---

### Post by bodhi.zazen on 2008-12-29
What about the Ubuntu minimal CD ?

    [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Otherwise a minimal install of just about any distro should do.

After a minimal install you can remove packages you do not need.

---

### Post by nbotticelli on 2008-12-30
At work I just used Ubuntu Server 8.04.1 as my base install then put on the base xfce window manager plus firefox to manage the vm's from.

I think next time though I will just install vmware server on ubuntu server and then manage the server through ssh or remote desktop but I'm still very new to this also.

Didn't know about the minimal install. That's interesting.

---

### Post by solwic on 2008-12-30
> **thomasr said:**
> Looking for a minimal distro to install VMware server on. Only purpose will be to serve up virtual machines.

Any distro can be minimalized.  Puppy Linux, I hear, is pretty small.  So is Damn Small Linux (DSL).  

Ubuntu, as Bodhi said, has a minimal install, as well.  

Or...try them all!  :)

---

### Post by sql_noob on 2008-12-30
i'm setting up a test environment and this morning saw that VMWare has a free version of ESX server now. it's a 240MB iso and is a hypervisor. no need to install any OS since you boot off the CD you create, install it on the hardware and then virtualize any OS that it supports

---

### Post by thomasr on 2008-12-30
> **sql_noob said:**
> i'm setting up a test environment and this morning saw that VMWare has a free version of ESX server now. it's a 240MB iso and is a hypervisor. no need to install any OS since you boot off the CD you create, install it on the hardware and then virtualize any OS that it supports

Thanks, think I will give that a try.

---

