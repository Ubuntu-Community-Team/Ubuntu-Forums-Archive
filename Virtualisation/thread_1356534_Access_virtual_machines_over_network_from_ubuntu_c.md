---
title: "Access virtual machines over network from ubuntu computer"
date: 2009-12-16
forum: Virtualisation
---

### Post by mad_max0204 on 2009-12-16
Hi guys,

I have set up virtual machine serving server with lots of power, ram and storage running ubuntu 64bit and vmware workstation. Had to go with vmware workstation because I need basic DX9 support in VMs. In the same network are few computers that have ubuntu installed. Now I want to be able to access those VMs from ubuntu computers as those VMs OSes were installed locally. We all know that RDP is slow and sluggish and some applications I use disable dx9 when working over RDP. VNC is better with response but I havent found a good VNC client yet (any advice would be much appreciated).

Is there any other solution ? Maybe even change virtualization software ?
I looked over some citrix solutions but I'm not fammiliar with them. I even saw some citrix solution that fully uses GPU. If anyone is familiar with this pls advise.
So my basic goal is to get fast response and basic dx9 support in VMs.

Thanks

---

### Post by egravede on 2009-12-17
As far as I'm concerned there isn't anyway to remote into an Ubuntu client with anything other than RDP or VNC.  I currently use X11VNC server on my Ubuntu server and remote it using VNCviewer.  Its kind of sluggish and definitely doesn't have DX9 support, but we use it to host a virtualization of Windows XP SP3.  There are betas of rdesktop that you can try, but I haven't had any luck with them.

---

### Post by mad_max0204 on 2009-12-18
egravede,
sorry man but you didnt understand me.
I'm running VMs on Vmware Workstation with good DX9 support.
Host system is Ubuntu 64bit and I can VNC to without problems.
My question was regarding using those virtual machines (guests)
not the host OS.

---

### Post by egravede on 2009-12-18
Oh, I misunderstood :)

As of now I don't think there is anything that is going to be able to support DX9 as far as a remote client.  As you said in your first post VMware does have basic support, but I wouldn't know about VNC.  I did some light googling and a few commercial clients have popped up, but thats for you to decide :)

---

### Post by dcstar on 2009-12-23
> **mad_max0204 said:**
> egravede,
sorry man but you didnt understand me.
I'm running VMs on Vmware Workstation with good DX9 support.
Host system is Ubuntu 64bit and I can VNC to without problems.
My question was regarding using those virtual machines (guests)
not the host OS.

I know you can access VMs on VMware Sever hosts remotely via the VMware console tools, I don't know if VMware Workstation also provides this.

---

