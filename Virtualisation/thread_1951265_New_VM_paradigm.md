---
title: "New VM paradigm"
date: 2012-04-02
forum: Virtualisation
---

### Post by freakalad on 2012-04-02
Hi all,

The new 12.04 LTS is due for release soon, but the new would-be VM environment is surprisingly light on details/documentation, other than [a great writeup by Dustin Kirkland]("http://blog.dustinkirkland.com/2011/08/formal-introduction-to-ubuntu-orchestra.html").

There are a number of key technologies that are now coming together to roll new systems & make more effective use of resources:
* KVM (incl libvirt)
* Orchestra 
* JuJu (Management Server, was: Ensemble)
& by extension:
** Cobbler (Provision Server)
** Nagios (Monitoring Server) 
** Rsyslog (Logging Server)

A number of other tools are also on the scene: 
* OpenStack
* SPICE (3D hardware-acceleration for KVM)
* convirt (not exactly new, but fits with the overall theme)

How much of this will be "simple" to install, or have proxies/installers via `tasksel`?
Are there any other good docco's or guides available for setting this up?

---

### Post by dzponce11 on 2012-04-19
I have no clue about 1/2 of what you just spat out here. just install it after you install the .iso. 

~~~~dzponce11:confused:

---

### Post by Old_Grey_Wolf on 2012-04-21
> **freakalad said:**
> How much of this will be "simple" to install, or have proxies/installers via `tasksel`?
Are there any other good docco's or guides available for setting this up?

Some installation information is at [https://wiki.ubuntu.com/ServerTeam/Orchestra](https://wiki.ubuntu.com/ServerTeam/Orchestra) see Deploying Orchestra fleets at the bottom of the page. This page has some more installation information for MaaS  [https://wiki.ubuntu.com/ServerTeam/MAAS](https://wiki.ubuntu.com/ServerTeam/MAAS).

---

### Post by freakalad on 2012-04-27
I've already referred to much of the information you guys have indicated, thanks.
I've not included the new MaaS stuff, as I really don't consider there to be much of a difference in deployment & management between baremetal & VM's - actually, there is more complexity in provisioning & deploying VM's than baremetal, IMHO.

I've also neglected to mention that the `tasksel` during the install has options for "Openstack" & "Ubuntu Cloud Image (instance)", but detailed information on these options are pretty sparse.
The "Virtual Machine host" option seems obvious to me - installs the KVM/libvirt stack.

I'm already running a KVM setup on my "old" 10.04 LTS host (will be upgrading in the coming weeks/months), so simply "just install it" is not really an option, unless I know what to expect.
Any spare machines that I have "lying around" capable of running a VM stack is going to be used to build redundancy.

---

