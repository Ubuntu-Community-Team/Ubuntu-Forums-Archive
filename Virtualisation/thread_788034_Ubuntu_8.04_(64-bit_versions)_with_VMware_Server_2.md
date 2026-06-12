---
title: "Ubuntu 8.04 (64-bit versions) with VMware Server 2.0 Beta 2, 64-bit - Starting VM Err"
date: 2008-05-09
forum: Virtualisation
---

### Post by hbomb341 on 2008-05-09
I am “new” the Ubuntu server environment but have been following it for a few years now.  So I made the plunge this week on a new server (Dual Opteron 2.2GHz 8GB Ram 320 GB SATA Drive) I am trying to bring online.  I installed Ubuntu 8.04 Hardy Heron (64-bit versions) with VMware Server 2.0 Beta 2, 64-bit.  I following the directions at [http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29](http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29) and was able to get it all running.  VERY happy with how easy Ubuntu is to install and use wish I would of made the plunge earlier.  But I have attached an error I am having when I try to start a Virtual Machine.

“Power on Virtual Machine” failed to complete
“The attempted operation cannot be performed in the current state (Power Off)”

I did some searching and wasn’t able to find a solution; Any one have any ideas?  Thank You for your help in advance.

---

### Post by raidensix on 2008-05-09
Are these newly installed VMs or copied from elsewhere?

---

### Post by cgabbadon on 2008-05-31
I have the same exact issue on Ubuntu 8.04 (64-bit) as well w i th VMware Server 2.0 Beta 2. I am attempting to create a new virtual machine and I get this error.  I didn't have this issue with the 32-bit version of Ubuntu 8.04, but I'm not sure if it is related to something I have misconfigured on my end.

---

### Post by jcostom on 2008-06-01
> **hbomb341 said:**
> I following the directions at [http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29](http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29) and was able to get it all running.

To me, that looks like your problem.  Those directions are for vmware server 1.x, not the 2.0 beta.

I've got the 2.0 beta 2 loaded on my amd64 Hardy system (Core 2 Quad, 8GB RAM), and it's running fine.  A bit rough around the edges now & then, but otherwise, working well.

The only change I had to make was to the vsock modules.  I had to get into the module source directory and unpack the vsock modules, and comment out 4 or 5 lines at the top of the Makefile.kernel file, then re-pack the vsock sources.  The specific changes are here:

[http://ubuntuforums.org/showpost.php?p=4742779&postcount=8](http://ubuntuforums.org/showpost.php?p=4742779&postcount=8)

I'd copy my vms out, completely whack the entire vmware install, including the sources and modules, then just cleanly install a new copy of the vmware 2.x code, and restore the vms.

---

### Post by sbeattie on 2008-06-04
I had a similar problem trying out the VMware Server 2 beta. In syslog (/var/log/messages) I saw the following messages when I got my errors:

[INDENT][FONT="Courier New"][ 3117.710532] /dev/vmmon[17589]: Task_Switch: Intel VT mode is in use by some other software
[ 3117.710540] /dev/vmmon[17589]: Vmx86_RunVM: Task_Switch failed[/FONT][/INDENT]

which made me realize that I also had the kvm modules loaded. Running

[INDENT][FONT="Courier New"]sudo /etc/init.d/kvm stop[/FONT]
[/INDENT]
to unload the modules let VMware server start working.

---

### Post by cgabbadon on 2008-06-07
Thanks much - removing the KVM modules worked for me.  One mistake I made however was I needed to mark the KVM modules for *complete removal*, not just regular removal.  Anyways, I'm up and running now with VMware Server 2.0 beta 2 - thanks for your suggestions everyone.

---

### Post by PilotJLR on 2008-06-15
And if you want to prevent KVM from loading on boot, but not uninstall it entirely, do this:
```

sudo update-rc.d -f kvm remove

```

---

