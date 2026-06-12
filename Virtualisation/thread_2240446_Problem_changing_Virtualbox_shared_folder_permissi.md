---
title: "Problem changing Virtualbox shared folder permission to rw"
date: 2014-08-20
forum: Virtualisation
---

### Post by linuxyogi on 2014-08-20
Hi,

Host : Lubuntu 14.04

Guest :Lubuntu 14.04

I can mount the shared folder in the VM by doing

```
sudo mount -t vboxsf share ~/host
```

I added the user to group vboxsf by doing 

```
 sudo adduser <username> vboxsf 
``` and then 

```
 sudo usermod -aG vboxsf <username> 
```

On both occasions I logged out from my guest and logged in but the shared folder remained read only. 

I tried the chown command also but it had no effect.

How to solve this ?

---

### Post by T.J. on 2014-08-20
Make sure that your account is part of the vboxsf group by looking at the /etc/group file, then be sure to restart the machine. Use the VirtualBox automount mechanism.  Virtualbox will not give you proper access to the share if you don't.  Thank Oracle for not doing a better job with their drivers, which are notoriously buggy.  I believe that they have been described by kernel developers as "crap".

---

### Post by linuxyogi on 2014-08-20
> **T.J. said:**
> Make sure that your account is part of the vboxsf group by looking at the /etc/group file, then be sure to restart the machine. Use the VirtualBox automount mechanism.  Virtualbox will not give you proper access to the share if you don't.  Thank Oracle for not doing a better job with their drivers, which are notoriously buggy.  I believe that they have been described by kernel developers as "crap".

I checked, my user account is part of the vboxsf group. Tried restarting the VM but same thing. I have selected auto mount.

On the the host my account is added to vboxusers group.

Is there any other opensource visualization software which is user friendly like Vbox ?

---

### Post by linuxyogi on 2014-08-20
Workaround found.

Configured NFS server on the VM. All I want to do is copy files from the VM to host.

Not marking as solved.

---

### Post by T.J. on 2014-08-20
What it sounds like to me is that the Ubuntu package failed to install the shared drivers properly.

1. Is dkms installed so that the VBox drivers are compiled to match your kernel?  
2.  Have you tried running "vboxdrv setup" as administrator?
3. Have you tried using the official Oracle binary package rather than the Ubuntu one?  Ubuntu is based on Debian Unstable and as such, it has unfixed bugs.  Installing the Oracle one may recompile the drivers and fix your problem.  Be sure to apt purge the Ubuntu one if you try that.

---

### Post by T.J. on 2014-08-20
> **linuxyogi said:**
> Is there any other opensource visualization software which is user friendly like Vbox ?

Actually, I think the preferred virtual management software on Linux hosts is probably either VMWARE, Xen, or KVM, not necessarily in that order.  Vmware is the closest one to VirtualBox and has better drivers as they are maintained with the actual Linux kernel.  You can use Vmware Player for free for noncommercial use, and is the first one I would recommend if you want to not spend any time on it.    KVM is the default Linux VM software as it is actually part of the Linux kernel, but you will need to hack some config files.  Xen is probably the best of the three having the most features, but you have to take the time to learn it.  Xen is also the most mature and stable of the three. It can also perform VGA passthrough, something that VirtualBox cannot do.  This allows such things as games and 3D software to be run successfully on Windows guests while using the guest's native video driver.

As a side note, you should be aware that the "guest additions" VirtualBox video drivers for Linux guests are absolutely crap.  They have no XVideo support, do extremely poor screen refreshes, cause OpenGL crashes, have overlay problems, and are generally just plain slow.  You're better off just turning off 3D acceleration on Linux guests when using VirtualBox.  They have been like that for years, Oracle seems to have no interest in fixing them or even fixing Direct3D for Windows guests for that matter.

---

### Post by Tadaen_Sylvermane on 2014-08-22
I don't know if this is your issue but it default mounts to /media/foldername_sf . Check there before giving up to see if that solves it.

Doubt it's the repo VirtualBox. I use it every day without issue.

*EDIT* Should mention to that you should be sure that in the shared folder settings you don't have "Read Only" checked. If you do that is the problem.

---

