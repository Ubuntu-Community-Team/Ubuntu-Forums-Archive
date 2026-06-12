---
title: "KVM:  virsh shutdown not working"
date: 2023-01-24
forum: Virtualisation
---

### Post by aljames2 on 2023-01-24
I finally got it to work but wanted to hear if this seems to be a normal method.

Xubuntu 22.04 KVM Host
Ubuntu MATE 22.04 VM

From the Host, both virsh shutdown, and virt-manager shutdown commands did not shut down the VM.  Only destroy would work.

Upon closer inspection, what is happening is if the VM is running in the background, and I am not logged into the VM, and then when I initiate the shutdown command from the host, I can see the VM is prompting for a 2nd interaction, waiting for a shutdown button or some other similarly named button to be clicked to complete the task.

After reading the virsh manpage for the shutdown command, I learned there are various modes that can be used to do a shutdown.  Most of the Googl'in I did suggested checking that ACPI is enabled on the guest and to adjust the powerbutton event script, which seems all too much.  I was hoping for a "just work" solution.  The simplest I came up with was to just install qemu-guest-agent on the VM, which also adds a unix channel to the VM configuration, enabling this control.

This enables my virsh shutdown or virt-manager shutdown to do a graceful shutdown, vs using destroy.

On the VM:
```
sudo apt update
sudo apt install qemu-guest-agent
```

Restart the VM, then from the Host try to shutdown:
```
virsh shutdown --mode agent UbuntuMATE22.04
```

Or, use virt-manager gui to shutdown the VM.  Both now work.

I suppose this will be needed in future cases where the shutdown control doesn't work, depending on the host OS and/or VM distros running.  This is the first time I have had this problem.

Am I missing a simpler method here.

---

### Post by TheFu on 2023-01-24
I added acpi to my VMs a few years ago to solve this.

Some VMs take a looooooong time to shutdown, but others are gone in just a few seconds.  I think it depends on the number of added dæmons and the speed they typically work.  For example, my Zimbra VM takes 4 minutes to shutdown, but all my other VMs generally shutdown in less than 10 seconds.  Zimbra is quite slow to start and stop, even from inside the VM.

---

### Post by aljames2 on 2023-01-25
Thanks TheFu.  I had verified the acpi was enabled on my VM, but still had this issue with unresponsive shut downs.  I left it in shutdown mode for 30 minutes one time and still nothing.  When I viewed the VM window during that period of time, the pop-up was displayed, waiting for a mouse-click to select either shut down, restart or log off.  The only thing that would work was virsh destroy or force-off in virt-manager.  

My OP steps is the only thing I have found that allows a graceful shutdown from the host.

---

### Post by MAFoElffen on 2023-01-25
Version?
```

libvirtd --version
virsh --version

```

---

### Post by TheFu on 2023-01-25
> **aljames2 said:**
> Thanks TheFu.  I had verified the acpi was enabled on my VM, but still had this issue with unresponsive shut downs.  I left it in shutdown mode for 30 minutes one time and still nothing.  When I viewed the VM window during that period of time, the pop-up was displayed, waiting for a mouse-click to select either shut down, restart or log off.  The only thing that would work was virsh destroy or force-off in virt-manager.  

My OP steps is the only thing I have found that allows a graceful shutdown from the host.

Perhaps it is a bug?

OT:
Someone at my LUG this weekend was complaining that Ubuntu had stopped allowing some batch stuff and was prompting for user interaction at stupid times.  For some reason, I thought that was happening when they did apt upgrades ... asking to restart services even when on the CLI in batch.  It was stuck, sitting there.  I know that ansible tells all package management tools it is running in batch, so not to ask questions.  Think an environment variable is supported so APT doesn't wait.  
```
$ sudo DEBIAN_FRONTEND=noninteractive apt-get -y install ...
```

Maybe there's some environment similar for virsh shutdown?
```
$ virsh shutdown --help
  NAME
    shutdown - gracefully shutdown a domain

  SYNOPSIS
    shutdown <domain> [--mode <string>]

  DESCRIPTION
    Run shutdown in the target domain.

  OPTIONS
    [--domain] <string>  domain name, id or uuid
    --mode <string>  shutdown mode: acpi|agent|initctl|signal|paravirt

```
So, maybe 
'virsh shutdown mydomain --mode acpi' will work?

---

### Post by aljames2 on 2023-01-25
My libvirtd & virsh versions are both 8.0.0

> virsh shutdown mydomain --mode acpi
The mode acpi does not shutdown & power down the VM for me.  I do not get the sense the host side is stuck because it does call the shutdown event on the VM, but the VM displays the graphical pop-up, awaiting a mouse-click to complete the task.

---

### Post by TheFu on 2023-01-25
I'm back to "it's a bug".

I won't be moving to 22.04 anytime soon on my KVM hosts.  I do need to move off 18.04 soon for a few systems. Thanks for helping me decide.
Sorry, I'm of no help.  ;)

---

### Post by aljames2 on 2023-01-25
Lol.  Glad I could help :)

Perhaps it is exactly that, a bug!  I am still evaluating if I like Jammy.  I very much dislike the snapd world, but thought I would work some with it, figuring that it isn’t going away, probably.  Waiting does help us get past the bugs.

Flavours give 3 years of support but Ubuntu LTS 5-years. Helps when staying between releases.  Although, gnome is not my favorite.

I digress.  Thanks again!

---

