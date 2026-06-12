---
title: "3D acceleration working on VMware 3.0 but desktop effects not working"
date: 2009-11-13
forum: Virtualisation
---

### Post by ZipoTe on 2009-11-13
Hi folks!

Long time since my last post here on ubuntuforums :p hehe.

Ok, I have 3D working, as you can see:
[IMG]http://img40.imageshack.us/img40/9382/glxinfo.png[/IMG]
[IMG]http://img40.imageshack.us/img40/2764/glxgears.png[/IMG]

some people say 3D cannot be turned on but here you can see it can :D so here I am, looking around for some help because I can't seem to find the way to enable desktop effects.

By the way, I'm running VMWare on a Macbook with the Intel X3100.

Thank you!!

---

### Post by fjgaude on 2009-11-13
Well, in Ubuntu you go to System/Preferences/Appearance/Visual Effects and then click Normal, instead of the None. See what happens!

---

### Post by ZipoTe on 2009-11-13
Thank you but I already did it. Ubuntu tries to find the correct controller but it fails and returns "Desktop effects couldn't be enabled".

](*,)

---

### Post by fjgaude on 2009-11-13
Well then that's it... you are under a software video emulator and it is not good enough for advanced 3D. Are you trying to play 3D games in Ubuntu under a Mac?

---

### Post by rlsx on 2009-11-14
> **ZipoTe said:**
> Thank you but I already did it. Ubuntu tries to find the correct controller but it fails and returns "Desktop effects couldn't be enabled".
](*,)

From another thread, I wrote:

I have also tried both Ubuntu and Kubuntu 9.10, under Vmware WS 7.0. In Kubuntu, to enable visual effects, one is given the choice between "OpenGL" and "XRender". The former option doesn't work, but the second does work.

As I understand it, OpenGL is not (yet?) available for Linux guests in Vmware. Only for Windows guests.

Does Ubuntu try to use OpenGL to enable visual effects?

I don't know what "XRender" is. But, can't Ubuntu use that same technique/api that Kubuntu does, to implement visual effects?

---

### Post by ZipoTe on 2009-11-15
> **fjgaude said:**
> Well then that's it... you are under a software video emulator and it is not good enough for advanced 3D. Are you trying to play 3D games in Ubuntu under a Mac?

Nop, I just want to enable desktop effects :P

> **rlsx said:**
> From another thread, I wrote:

I have also tried both Ubuntu and Kubuntu 9.10, under Vmware WS 7.0. In Kubuntu, to enable visual effects, one is given the choice between "OpenGL" and "XRender". The former option doesn't work, but the second does work.

As I understand it, OpenGL is not (yet?) available for Linux guests in Vmware. Only for Windows guests.

Does Ubuntu try to use OpenGL to enable visual effects?

I don't know what "XRender" is. But, can't Ubuntu use that same technique/api that Kubuntu does, to implement visual effects?

Hmmm... interesting. Let's look for some information

Thanks! ;)

---

### Post by ZipoTe on 2009-11-15
No luck,

As far as I had read, there is no way I can make desktop effects use Xrender as Kubuntu does.

So I am like 2 days ago...

Help!

---

### Post by rlsx on 2009-11-21
Any ideas, anyone?

---

### Post by ZipoTe on 2009-11-21
No, I did't find the way to use desktop effects with XRender. I'm not sure if gnome can.

---

### Post by kartook on 2010-02-02
I am using workstation  7.0 and assigned 3 Gb Ram 
Enable 3D acceleration on display ,
Up to date ubuntu packages .
Vmware Tools installed latest version 

Now !! 
Time to enable dekstop effects  ..
Enabled the option flickering twice 


Error 
"Desktop effects could not be enabled"

Looking for solutions .if it work Wawwwwww  Great and advance thanks for the solution .. ;)


NOTE : 
The same i want to tell you my Windows 7 Effects are worknig on my Vmware Workstation 7 .... :popcorn:

---

### Post by tilixibr on 2010-05-02
exactly the same problem here, it's frustrating since it worked on my other virtual machine, it loaded the drivers on the first try, but now it didn't:( It searches for the driver and it fails
[edit] Im running VMWare on Windows 7, the VM is Ubuntu 10.04 64 bit

---

### Post by dcstar on 2010-05-05
> **tilixibr said:**
> exactly the same problem here, it's frustrating since it worked on my other virtual machine, it loaded the drivers on the first try, but now it didn't:( It searches for the driver and it fails
[edit] Im running VMWare on Windows 7, the VM is Ubuntu 10.04 64 bit

You don't really need desktop effects on the VM if you use Unity mode and run the apps on your host desktop using the effects it has.

---

