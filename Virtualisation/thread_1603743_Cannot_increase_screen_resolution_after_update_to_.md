---
title: "Cannot increase screen resolution after update to ubuntu 10.10"
date: 2010-10-23
forum: Virtualisation
---

### Post by twagener on 2010-10-23
Hi,

I have recently updated my ubuntu virtual machine to ubuntu 10.10. I am running the vm with the latest version of vmware.
After the update I can not increase the screen resolution past 1280x920. Before the update I was running the vm at 1920x1200 without any problem although I noticed that unity desktop stopped working some time ago. The vmware tools seem to install ok after I have removed the old installation.

Can somebody give me a hint how to fix this?

Thank you,

Thomas

---

### Post by fjgaude on 2010-10-23
Have you re-installed the VMware Tools for Linux? If not that might be the issue. You needs the tools to work correctly for the various screen resolutions to work.

---

### Post by twagener on 2010-10-24
> **fjgaude said:**
> Have you re-installed the VMware Tools for Linux? If not that might be the issue. You needs the tools to work correctly for the various screen resolutions to work.

VMware tools were installed and after an explicit uninstall and a lot of --clobber-kernel-module were installed alright. 

I have solved the problem, in a way. I rebooted the VM with the ubuntu iso image. With the live file system I was able to set the screen resolution to 1920x1200 without any problem. Unmounting the iso image and rebooting the VM did the trick. I was able to set the correct resolution and everything works nicely:)

I suspect that there was something wrong with the VM otherwise I would not be able to explain why booting from a different media solved the problem:confused:

---

### Post by fjgaude on 2010-10-25
Ah... you solved your own problem, and that is how learning occurs. <smile>

---

