---
title: "VirtualBox-OSE kernel problem"
date: 2008-07-31
forum: Virtualisation
---

### Post by Stargazer989 on 2008-07-31
> The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I keep getting the error even though i installed:
> virtualbox-ose
virtualbox-ose module for linux-image-2.6.24-19-generic
virtualbox-ose module for linux-image-2.6.24-19-rt
virtualbox-ose module for linux-image-generic
virtualbox-ose module for linux-image-rt

---

### Post by decoherence on 2008-07-31
> **Stargazer989 said:**
> I keep getting the error even though i installed:

"Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups"

Have you done this?

System -> Administration -> Users and Groups

Unlock it, click Manage Groups, find vboxusers and click Properties. Make sure your user account is checked.

You will have to log out/log in for the change to take.

---

### Post by overdrank on 2008-07-31
moved :)

---

### Post by Stargazer989 on 2008-07-31
[s]why was it moved ? i'm a newbie pretty much :([/s]

i understand now

---

### Post by Stargazer989 on 2008-07-31
now there's something else wrong :(
i can run VB-OSE up to a point but then i get a Black screen with a small Red cursor. btw the OS i'm trying to run is AROS

---

### Post by decoherence on 2008-08-01
> **Stargazer989 said:**
> now there's something else wrong :(
i can run VB-OSE up to a point but then i get a Black screen with a small Red cursor. btw the OS i'm trying to run is AROS

Which version of AROS are you using? vmware? live? nightly? Have you tried different ones? It sounds to me like AROS and VB-OSE aren't getting along completely. You might check booting up a linux iso to rule out VB-OSE as the problem.

---

### Post by Stargazer989 on 2008-08-01
> **decoherence said:**
> Which version of AROS are you using? vmware? live? nightly? Have you tried different ones? It sounds to me like AROS and VB-OSE aren't getting along completely. You might check booting up a linux iso to rule out VB-OSE as the problem.

you know... just a few minutes after i made this post someone in the #AROS channel in FreeNode answered my question *about* AROS and VB-OSE! something about they never worked together. I tried getting a VMWARE for Ubuntu but they only have the binaries which i have to compile myself. Know any guides so that i don't have to do this over again (Mainly for VMWare + compiling for AROS)

please and thank you

---

### Post by weegee205 on 2011-07-31
I got a similar problem that said (I was running Ubuntu 8.10 under VirtualBox OSE) "Ubuntu 8.10 has shutdown with error code 1 (or something to that effect.) I opened a terminal window, uninstalled the kernel as root (sudo su), then reinstalled them. It worked.

---

