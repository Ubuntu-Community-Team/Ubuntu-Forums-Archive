---
title: "Problem getting Unity work in VMware"
date: 2010-12-27
forum: Virtualisation
---

### Post by echo1991 on 2010-12-27
Hey there. I'm new to the forum and pretty exhausted about getting Unity work in VMware.

My problem is the following:

I wanted to try out Unity. I first tried it on VirtualBox, then live on an ACER notebook and in the end in VMware.
No matter where I tried it, it would not work =/ I always get the message that there is no 3d acceleration...
I spend hours to solve the problem in VMware.. Searching on Google how to install that VMware-Tools, cause that seemed to be the key. I wasn't able to get it properly working, meaning Unity didn't work, still. 

Now my question:

Is there any way to get Unity working in VMware?

I'm using the recent iso of Natty (27.12.2010) with VMware-Player running on a Windows 7 Host.

I'm pretty desperate.. Really want that thingy get to work.


I'm sorry if this was already posted or solved somewhere else in the forum. Also I'm pretty new to Linux. I'd like to try Linux/Ubuntu as an alternative workspace,

Thanks for any help.

---

### Post by dcstar on 2010-12-27
> **echo1991 said:**
> Hey there. I'm new to the forum and pretty exhausted about getting Unity work in VMware.

My problem is the following:

I wanted to try out Unity. I first tried it on VirtualBox, then live on an ACER notebook and in the end in VMware.
No matter where I tried it, it would not work =/ I always get the message that there is no 3d acceleration...
..........

Do you have 3D video drivers working **on the host** and the Enhanced Video turn on in the VM configuration?

---

### Post by echo1991 on 2010-12-28
> **dcstar said:**
> Do you have 3D video drivers working **on the host** and the Enhanced Video turn on in the VM configuration?

My 3d video drivers on my Windows host work. I crossed "Accelerate 3D graphics" in VMware Player.

---

### Post by gurpal2000 on 2011-05-27
Same thing. My base system is Ubuntu normally. But I thought i'll try it the other way round. So using a Windows 7 64 host with the latest VM Workstation 7 and Natty 64 guest. I have all the 3D settings on, powerful machine etc. Even after installing vmware tools in Natty i couldnt find a way to get the unity 3d up and running. only 2d works...

---

### Post by fjgaude on 2011-05-28
It appears VMware Player doesn't have a 3D video emulation for many pieces of hardware. That's simply the way it is for now.

---

### Post by garvinrick4 on 2011-05-28
> It appears VMware Player doesn't have a 3D video emulation for many pieces of hardware. That's simply the way it is for now.
And that is the truth +1

---

### Post by garvinrick4 on 2011-05-28
I have to add it works quite well with 11.04 Natty Classic and is a fine product. 
I have one install of the VMware player with VMware tools which is quite easy to install. Nothing compares
to a regular partition install of Ubuntu but VMware works well for what it was intended.

---

### Post by Quadunit404 on 2011-05-28
If you want to use Unity in a virtual machine, use VirtualBox. That is the only virtualization platform that supports Unity and GNOME Shell.

---

### Post by Vepar on 2011-05-28
I'm having the same problem, at first start it told me that i don't have powerful enough hardware to run unity, and it started in gnome. I'm using Vmware workstation 7 and 3d acceleration box is checked. Is there no way to make this work?

---

### Post by colin.p on 2011-05-29
see post #5. Short answer-no.

---

### Post by Vepar on 2011-05-29
Oh well... Gnome it is... I can live without some eye candy. :D

---

### Post by colin.p on 2011-05-29
I can tell you that on my Dell 1545 laptop (certainly no extreme powerhouse) that unity 3d works fine in Virtualbox 4.08. The display adapter is only an onboard Intel adapter with, I think, 32 or 64 MB ram.

---

### Post by Quadunit404 on 2011-05-31
As I said before :)

> **Quadunit404 said:**
> If you want to use Unity in a virtual machine, **use VirtualBox.** That is the only virtualization platform that supports Unity and GNOME Shell.

---

### Post by bigcreturns on 2011-08-16
Unity 2d does work for VMWare Player running Guest OS 11.04.

sudo apt-get install unity-2d-default-settings

---

### Post by fjgaude on 2011-08-16
> **bigcreturns said:**
> Unity 2d does work for VMWare Player running Guest OS 11.04.

sudo apt-get install unity-2d-default-settings

As guest oneiric, 11.10 Alpha, 2D, works fine in VMware Player. But on the host Player will not install, yet. We wait for the update.

---

### Post by dancavs on 2011-08-30
> **Quadunit404 said:**
> If you want to use Unity in a virtual machine, use VirtualBox. That is the only virtualization platform that supports Unity and GNOME Shell.

+1 for virtual Box

I have just installed virtual Box running ubuntu 11.04 with Unity 3d running. no problems so far. I followed these instructions: 

[http://www.ubuntugeek.com/running-ubuntu-11-04-natty-unity-3d-on-virtualbox-4-x.html]("http://www.ubuntugeek.com/running-ubuntu-11-04-natty-unity-3d-on-virtualbox-4-x.html")

---

