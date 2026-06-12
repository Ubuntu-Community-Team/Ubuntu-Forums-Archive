---
title: "Remote Windows desktops in Ubuntu."
date: 2009-04-26
forum: Virtualisation
---

### Post by albinootje on 2009-04-26
I want to switch some MS-Windows desktops to Ubuntu, and I would prefer a remote desktop option where users can run some MS-Windows based applications inside Ubuntu. 
Those applications are a few applications which won't run well in Wine or CrossOverLinux, and starting up VirtualBox on the desktops itself is not the perfect solution (too slow).

I would like to use a solution which is as cheap as possible. 
Buying a dedicated server for this is no problem, but I would like to keep the license costs for MS-Windows as low as possible.

What would you suggest ? XEN, VirtualBox, VMware or something else (I prefer not to depend this server on KVM) ?

Which MS-Windows version offers the best multi-user remote desktop setup (I'm not a Windows user) ?
Or would you recommend trimmed down MS-Windows instances for each user ?

How much RAM would you put in that server ?
I'm also thinking about running a FreeNX server on it, running/offering Ubuntu just for remotely editing documents for the users.

And would a 1000 Mbit instead of a 100 Mbit network lead to much improvement for this network ?
I'm talking about a network of about 20 computers total, with a maximum of 5 user laptops.

---

### Post by HermanAB on 2009-04-26
> I want to switch some MS-Windows desktops to Ubuntu, and I would prefer a remote desktop option where users can run some MS-Windows based applications inside Ubuntu.
Those applications are a few applications which won't run well in Wine or CrossOverLinux, and starting up VirtualBox on the desktops itself is not the perfect solution (too slow).

I would like to use a solution which is as cheap as possible.
Buying a dedicated server for this is no problem, but I would like to keep the license costs for MS-Windows as low as possible.
Use rdesktop.

> What would you suggest ? XEN, VirtualBox, VMware or something else (I prefer not to depend this server on KVM) ?
Virtualbox supports OpenGL, VMware supports DirectX, so VMware is probably best.

> Which MS-Windows version offers the best multi-user remote desktop setup (I'm not a Windows user) ?
Or would you recommend trimmed down MS-Windows instances for each user ?
Windows Server 2003 can do 3 remote users by default, more requires a license change.

> How much RAM would you put in that server ?
I'm also thinking about running a FreeNX server on it, running/offering Ubuntu just for remotely editing documents for the users.
Use 385MB per Windows VM.
You don't need FreeNX.  SSH is the best remote solution for Linux.

> And would a 1000 Mbit instead of a 100 Mbit network lead to much improvement for this network ?
I'm talking about a network of about 20 computers total, with a maximum of 5 user laptops. 
Won't make much difference.

Hope that helps!

---

### Post by albinootje on 2009-04-26
> **HermanAB said:**
> 
Hope that helps!

Thanks! :)

---

