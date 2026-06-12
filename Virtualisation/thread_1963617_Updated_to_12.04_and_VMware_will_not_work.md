---
title: "Updated to 12.04 and VMware will not work?"
date: 2012-04-22
forum: Virtualisation
---

### Post by tdipietro67 on 2012-04-22
Today I updated my machine from 10.04 LTS to 12.04 LTS and after completing the update I am no longer able to start up my VMware. I receive this message:

VMware Kernel Module Updater

Before you can run VMware, Several modules must be compiled and loaded into the running kernel.


If I select Install i receive an error message:

Unable to build kernel module.
see log file /tmp/vmware-root/setup-3742.log for details

I can not find the log file it is referring to.

I am running VMware Workstation 7

Is there a command or an update that I can perform to get my VM's back up and running?

I appreciate any help.

Thanks,
Anthony

---

### Post by thenixedreport on 2012-04-22
When you updated to 12.04, you also updated the kernel.  Therefore, the kernel modules need to be rebuilt.

Have you tried this?

```
sudo vmware-tools-config.pl
```

---

### Post by GameX2 on 2012-04-22
EDIT: Wrote too much.  Thenixedreport replied first. XD

Hi,

I'm running Ubuntu 11.10 64-Bits, and I've had this message as well when I ran VMware on the Kernel 3.4.0-030400RC3-Generic.  However, I do not have this problem with the 3.0.0-17-Generic Kernel.  Not sure if you can use an older Kernel?
Or maybe there's a updated version of VMware on the website.

Your VMs are still accessible, however; usually stored in your HOME or Documents folder.


Sorry I couldn't help much more, but good luck. ;)

---

### Post by tdipietro67 on 2012-04-22
> **thenixedreport said:**
> When you updated to 12.04, you also updated the kernel.  Therefore, the kernel modules need to be rebuilt.

Have you tried this?

```
sudo vmware-tools-config.pl
```

Hi and thanks for the quick response. 
I have attempted to use the command that you posted and I receive:

Command Not Found

Is there something I am missing? I am not very knowledgeable in Linux yet. I have been using it for approx. a year because I wanted to learn something new and not be forced to use MS.

---

### Post by tdipietro67 on 2012-04-22
> **GameX2 said:**
> EDIT: Wrote too much.  Thenixedreport replied first. XD

Hi,

I'm running Ubuntu 11.10 64-Bits, and I've had this message as well when I ran VMware on the Kernel 3.4.0-030400RC3-Generic.  However, I do not have this problem with the 3.0.0-17-Generic Kernel.  Not sure if you can use an older Kernel?
Or maybe there's a updated version of VMware on the website.

Your VMs are still accessible, however; usually stored in your HOME or Documents folder.


Sorry I couldn't help much more, but good luck. ;)

Hi,
Yes my VMware folder still exists in my Home folder. If I try and select any of the VM's and attempt to open them it tells me that I need to find a program to open them with or there is no program to open them.

---

### Post by thenixedreport on 2012-04-24
```
sudo vmware-config.pl
```

My bad.  The previous one was meant for a Linux-based guest in order to get VMWare Additions to work.  Sorry about that.

---

### Post by SlugSlug on 2012-04-24
I had this prob. fixed here:
[http://ubuntuforums.org/showthread.php?p=11850669](http://ubuntuforums.org/showthread.php?p=11850669)

---

