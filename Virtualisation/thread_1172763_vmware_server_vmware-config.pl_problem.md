---
title: "vmware server vmware-config.pl problem"
date: 2009-05-28
forum: Virtualisation
---

### Post by HDave on 2009-05-28
I am running Vmware Server 2.0 on Jaunty and everytime I want to reconfigure the networking I need to run the command:

```
sudo vmware-config.pl
```

But everytime I do I get this error message:

```
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmmon
vmci
vmnet

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.
```

If I manually remove the modules (per the instructions), the script will run, but it forces a recompile of the entire thing.  I've seen this error reported on other distros, but anybody else see this on Jaunty or have a solution?

---

### Post by w0ls0n on 2009-06-15
Hello,

I just do rm /lib/modules/2.6.28-11-generic/misc/* and reinstall. This is my only workaround. Once I reinstall it works fine.

---

### Post by km0ti0n on 2009-06-16
Yes I had the same problem.

When I used vmware in the past I've had to re-run the vmware-config.pl script it's worked fine, it's normally nessasary after something changed with the kernel or similar, never investigated it. 

But there's something different about this update, and the vmware-config.pl script that has effected it.  

w0ls0n : your fix worked many thanks.

---

### Post by jpapejr on 2010-08-05
I got by with just removing the modules it specified for me (vmmon, vmci, vmnet) and then running the vmware-config.pl script once more. It did a full recompile after that I think. But all is well.

---

