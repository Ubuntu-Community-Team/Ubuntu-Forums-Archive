---
title: "Starting xorg and a GUI app at startup of an Ubuntu Proxmox LXC container?"
date: 2019-03-16
forum: Virtualisation
---

### Post by verulian on 2019-03-16
I have a scenario where I need to start up xorg and a graphical app when the container is started. **Is there any way to do this?** 

Everything I'm reading so far suggests using x2go and such things that trigger xorg to fire off after a user needs to sign on, but I need to do this in an automated fashion so that it starts without any interaction.

In my case I'm using Xubuntu 18.04 in a container, but I'm guessing doing this in Ubuntu would be just about identical for stock Ubuntu container.

---

### Post by TheFu on 2019-03-17
Should full OSes be run in containers? I thought that was against best practices. 
An exploit to break out of linux containers: [https://www.cyberark.com/threat-research-blog/the-route-to-root-container-escape-using-kernel-exploitation/](https://www.cyberark.com/threat-research-blog/the-route-to-root-container-escape-using-kernel-exploitation/)
If a very limited application-only setup is inside a container, then the tools just aren't available to the hacker. If all the container can do is run a webserver and the only code available is to run a webserver, then cracked container or not, it will only run a webserver. With a full OS, the tools needed to break out are available.

I thought proxmox was debian-based?

Treating a "container" like a full OS is a mistake.   xorg starts automatically already, but GUI applications cannot be started until after login, when the Xsession is created.  The only way I know would be to enable auto-login, which has huge security implications.  Don't do this using a userid when any network privileges.  If you need a full OS, please use a KVM VM.

x2go is for remote applications.  I use it daily, constantly, but only from remote systems. Access is not automatic.  x2go doesn't like Gnome3 or any DE that demands direct GPU access. Go ahead and try it, so you believe me. It is just storage for a new VM after all.  XFCE, LXDE, Mate and the lighter DEs work nicely with x2go for a reason.

---

### Post by verulian on 2019-03-17
This machine is to act as a gateway and will have a tight firewall that nothing from the public side will touch. It only needs to start this up and I would rather go lighter on the resources if possible vs using a full on vm with dedicated memory. Containers seem to be the right approach for this kind of use case scenario vs an actual VM.

---

### Post by TheFu on 2019-03-17
> **verulian said:**
>   Containers seem to be the right approach for this kind of use case scenario vs an actual VM.

I disagree.  Gateways need to be physical, single-purpose, machines, IMHO. If the beachhead is lost, then all is lost. Running a hypervisor or containers on a gateway machine doesn't pass my "does this smell ok" test.

OTOH, it is your machine, your network, your infrastructure.

Stepping back ... if you run a full OS, then automatic login is the only method to automatically get an Xsession started.  I don't think x2go will start an Xsession until the remote client requests it.  GUI programs can't be run without an Xsession (or whatever Wayland calls theirs).

I wouldn't know how to get X/Windows running on a server-only install, even if X11 is installed in a guest machine or guest "container".  Servers don't have GUIs or X/servers.  Can a GUI be loaded onto a Proxmox host?

---

### Post by verulian on 2019-03-17
I know of plenty of security consultants that would disagree and I guess we can agree to disagree here on the first point. 

GUIs work fine on Proxmox. I've been running a Windows Server on Proxmox for the time being, but have wanted to change over to *ubuntu.

Thanks for the thoughts, will keep digging and if no one else has any put here on this I'll report back once I finally figure it out.

---

