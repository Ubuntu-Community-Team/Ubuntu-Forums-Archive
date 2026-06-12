---
title: "ESXi as client hypervisor?"
date: 2009-07-29
forum: Virtualisation
---

### Post by nuseryame on 2009-07-29
I know that currently there is no free client hypervisor althought Citrix will release Xen Client soon, enabling you to run 2 operating systems at the same time, among other things.

However, I wonder if I can do just this by downloading ESXi server?

I understand that it requires admin from a separate Windows machine, but does this also mean that, if I were to put ESXi on my desktop, install Vista and Ubuntu as VMs, that I would not have an option to choose which VM to use at startup from the server and could not switch VMs while both in use, from the server?

Or simply, shall I stop being stupid and just wait for a free client hypervisor to come out instead of messing around with a server hypervisor and pretending it's a client hypervisor.

I am talking type 1 here by the way, I already have VirtualBox which is type 2, however...baremetal sounds cool, so I want to play with a baremetal hypervisor...just for home use.

---

### Post by juancarlospaco on 2009-07-29
Linux already its a Baremetal Hypervisor.

Citrix already releases XenServer and related tools Open Source.

Theres already existing free client hypervisor.

[[IMG]http://www.ulteo.com/home/main/images/uovd/screenshots/v1/session-gimp-word.png[/IMG]]("http://www.ulteo.com/home/en/ovdi/openvirtualdesktop/features#screenshots")

---

### Post by nuseryame on 2009-07-29
I don't understand what Ulteo OVD is, doesn't look like a hypervisor type 1 to me.

I was thinking of something like Hyperspace by Phoenix.

What I really want to do is play around with Smoothwall and have that in a VM, Ubuntu in another VM connecting to the internet through Smoothwall.

---

### Post by PilotJLR on 2009-07-30
OP, to answer your original questions... realistically... no. ESXi has strict hardware requirements, and there is a fair chance it won't work with your storage controller and/or network interfaces (assuming a typicall desktop or laptop).

If you want bare metal performance, KVM is really the best it is going to get, assuming your machine also functions as your workstation.

---

### Post by juancarlospaco on 2009-07-30
**+1 KVM**

*Chuck Norris uses Compiled Kernel+KVM*

---

