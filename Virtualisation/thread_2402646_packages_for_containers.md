---
title: "packages for containers"
date: 2018-10-02
forum: Virtualisation
---

### Post by Skaperen on 2018-10-02
IMHO, containers really should be referenced as "psuedo-virtualization".  but the world seems to refer to it as a form of   virtualization or more exactly as operating-system-level virtualization.  so i guess i will, too.

what i want to know, and spent the whole day, yesterday, trying to figure out, is the list of packages to install to have everything i need for containerization.

---

### Post by TheFu on 2018-10-03
Containers aren't virtualization. They are compartmentalization, more like a chroot + extra kernel protections than any paravirtualization or full machine virtualization solution.

There are multiple types of containers. The world has standardized on Docker's file format.  However the Ubuntu implementation of LXD is closer in actual use to regular machine/hardware virtualization which tends to be easier to understand.
[https://tutorials.ubuntu.com/tutorial/tutorial-setting-up-lxd-1604#0](https://tutorials.ubuntu.com/tutorial/tutorial-setting-up-lxd-1604#0) is a tutorial for setting up an LXD container.

Most of the time, a container shouldn't have a shell, ssh, or any services running that aren't the main reason for the container.  1-container ==== 1-service provided.  We are supposed to treat containers like we treat zombies.  When the container doesn't meet the needs anymore, shoot it in the head and rebuild the container, in layers, from scratch.  Most container services shouldn't have any data inside either.  There are security reasons for this.

But you can find container security best-practice presentations all over youtube.

And whatever you do, never let a container run as root.  NEVER.

---

### Post by Skaperen on 2018-10-03
> **TheFu said:**
> Containers aren't virtualization. They are compartmentalization, more like a chroot + extra kernel protections than any paravirtualization or full machine virtualization solution.

this is my thought on it.  but i see this categorization a lot.  it's hard to know which a given audience already beiieves. correcting it means i need to add an explanation.

and i could not find a better subforum for this question than here.

> **TheFu said:**
> There are multiple types of containers. The world has standardized on Docker's file format.  However the Ubuntu implementation of LXD is closer in actual use to regular machine/hardware virtualization which tends to be easier to understand.
[https://tutorials.ubuntu.com/tutorial/tutorial-setting-up-lxd-1604#0](https://tutorials.ubuntu.com/tutorial/tutorial-setting-up-lxd-1604#0) is a tutorial for setting up an LXD container.

if Docker is *just* a file format, then i have no need for it (yet).  likewise for orchestration, such as OprnVZ.  my current goal for which containerization, rather than virtualization, seems to be the way to go is to share files live without the issues of NFS, or worse, SMB.  i don't really need virtualization for this project.  so it will be a way to "get my feet wet" in containerization.

> **TheFu said:**
> Most of the time, a container shouldn't have a shell, ssh, or any services running that aren't the main reason for the container.  1-container ==== 1-service provided.  We are supposed to treat containers like we treat zombies.  When the container doesn't meet the needs anymore, shoot it in the head and rebuild the container, in layers, from scratch.  Most container services shouldn't have any data inside either.  There are security reasons for this.

that can certainly be a valid model for containerization.  my current project does not fit that model.  yet, i has no needs that require virtualization and can benefit from a system model of containerization while everything else might be doing application model.

> **TheFu said:**
> But you can find container security best-practice presentations all over youtube.

to the extent that they specify for the application model, they won't apply to *this* project.

> **TheFu said:**
> And whatever you do, never let a container run as root.  NEVER.

what i will be running as root in there is already run as root on the host system.


this project is for doing long-term testing of software in a variety of variant userland setups.  this will involve things like new and old versions of tools, compilers, and run-time engines such as Python.  by "long-term", after initial testing passes, various actual services will be *used* in their containerized setup that varies in the ways under test.

what will not be tested is different kernels.  true virtualization will continue to be used for this subset need.  but long-term testing will either not happen or not be so long.

it is trusted users (me,myself, and i) that will get root access in a container if it has no other shielding..  one thing in this regard i already wondered about is what if i run a bunch of containers with a hardlinked "copy" of libc to save space and the same swapped-in copy.  root access could corrupt it or worse if an untrusted user had that access.

i *also* am looking at the idea of running multiple distributions by containerization.  that way i can run them at better performance.  that and i would run very little under the host system.  this would be on my laptop.

---

