---
title: "Virtual Box mouse freezing when entering full screen"
date: 2023-02-07
forum: Virtualisation
---

### Post by adam17 on 2023-02-07
Hi all,

I have been having issues with Virtual Box for some time when using Ubuntu as the Host.

When I run a virtual machine (no matter what OS it is) I am running into issues where the mouse is unable to click anything within the virtual machine. This seems to happen when I use ctrl+F to enter the full screen.

The only way I am able to gain mouse control is to ctrl+F out of full screen and forcibly shutdown / restart the VM.

If i leave the VM in windowed mode this issue does not seem to happen as often, but full screen it happens 100% of the time.

I do not believe this is an issue with Virtual Box as I have Virtual Box (same version) running on a different PC as a windows host.

I have been having this issue with some time, through multiple versions of Virtual box and since Ubuntu 20.04, I am now running Ubuntu 22.04.1 LTS x86_64 and Virtual Box Version 7.0.6 r155176 (Qt5.15.3).

Has anyone had a similar issue and know how I might resolve this?

Thanks in advance Adam.

---

### Post by varunendra on 2023-02-07
> **adam17 said:**
> .....I have Virtual Box (same version) running on a **different PC as a [color=red]windows host[/color]**....
There is the difference ^ that can make all the difference in performance, compatibility, usability.

I'm no longer using VirtualBox, so no idea about the problem you are having, but I was having serious performance issue when I left it. A fresh install of Bodhi Linux was taking almost 8 minutes to get fully ready and responsive. Host specs were Intel i5-1035G1, RAM 16GB, with the VM given more than adequate resources.

Switched to KVM+QEmu, and life is happy since then. Booting time of the same VM (similarly configured) with same specs is about 15-20 seconds.

Unless you have some specific need to use VirtualBox, I'd say take advantage of Linux kernel, and try KVM :
```
sudo apt install virt-manager
```
Virt-Manager is a nice and very capable GUI frontend to create and manage the VMs like VBox or VMware, and installs all the necessary packages as dependencies.

WARNING : Don't expect it to be same as VBox. While it can do more, you may miss a few features in initial use. But after a little getting used to (taking a few hours to a few days) it is WAYYY better than VBox or VMware, even better than VMware Esxi (yes, it KVM is a type 1 hypervisor, aka "Bare Metal Hypervisor", and is true to that claim).

---

### Post by DuckHook on 2023-02-07
^+++1^

My experience also. I switched to KVM some years ago with far better stability, speed and resource usage.

But&#8230;

&#8230;this doesn't answer the OP's question.

@adam17

I would suggest that you post your problem in the VBox forums. Naturally, they are the VBox experts so would be far more attuned to problems such as yours.

The only thing I can suggest is that you look at your logs. I wouldn't even know what to look for, but that's always the first visit when diagnosing any issue.

---

### Post by MAFoElffen on 2023-02-08
There are people here (in this Forum, in this section) that use VirtualBox... But just haven't answered yet.

I used to, but changed to KVM many years ago.

---

### Post by adam17 on 2023-02-08
> **DuckHook said:**
> ^+++1^

I would suggest that you post your problem in the VBox forums. Naturally, they are the VBox experts so would be far more attuned to problems such as yours.

The only thing I can suggest is that you look at your logs. I wouldn't even know what to look for, but that's always the first visit when diagnosing any issue.

Thanks for the replies, I have tried posting in the virtual box forum, will little success, It does seem this is a common problem on debian based systems. May give the suggested KVM a go.

---

### Post by MAFoElffen on 2023-02-08
These are the instructions I refer to: [https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/)

---

### Post by hornet2151 on 2023-08-01
Maybe it is no longer relevant since you probably switched to KVM, but just in case:

Have you tried disabling the mini-toolbar? (Settings -> User Interface -> deactivate option "show in full-screen"). [See post on virtualbox-Forum: https://forums.virtualbox.org/viewtopic.php?f=7&t=95459]("https://forums.virtualbox.org/viewtopic.php?f=7&t=95459")

It solved the issue for me.

---

### Post by thaxton on 2023-10-07
I have had this problem also for a while.  It seems Wayland is causing it, when I logged off and changed to X11 had no problems since. That was 2 months ago.

Hope it helps.

---

