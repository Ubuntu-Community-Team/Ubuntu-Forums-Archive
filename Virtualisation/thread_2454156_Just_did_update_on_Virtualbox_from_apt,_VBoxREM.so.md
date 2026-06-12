---
title: "Just did update on Virtualbox from apt, VBoxREM.so missing"
date: 2020-11-23
forum: Virtualisation
---

### Post by f00dl3 on 2020-11-23
I just did a sudo apt update; sudo apt upgrade yesterday and apparently after a reboot I was unable go get my Virtual Machine started. After researching the error that there was no DKMS library installed, I had to install virtualbox-dkms. Installing virtualbox-dkms forced me to uninstall virtualbox-6.0, and thus in it's place I had to install the virtualbox package. Virtualbox is now v6.1.10_Ubuntu r138449

Now every time I start the host OS and try to start the virtual machine over SSH before I am able to log into the GUI, I get the error "Unable to locate real file.... VBoxREM.so". 

Magically, the second I log into the GUI environment, Virtualbox Auto-starts the guest OS as it's supposed to. But I can't do this until I am physically in front of the computer.

---

### Post by TheFu on 2020-11-24
Are you using the VirtualBox PPA or just the standard repo?
Some software is best installed from a trusted PPA. I believe vbox is one of those where the PPA is better.  There are a few other packages like that, but I tend to stay with the repo versions assuming I'm running an LTS release.  I don't "do" non-LTS releases.

As for VBoxREM.so ... that isn't a proper name for a library, but you can search for it on the system and see whether the directory it is located in is also in your LD_LIBRARY_PATH both when you ssh in and when you login with a GUI session on the console. On Linux, library filenames must begin with "lib" .... so "libVBoxREM.so" could be valid.  I haven't used vbox in a very long time, so I don't know.

As for autostarting .... vbox is an end-user virtualization tool.  If you want it to behave like a server, then perhaps using a hypervisor made for servers would be a good idea?  Xen and KVM come to mind.  They also perform faster at most server tasks.  VM startup probably requires a user login and active GUI session to happen.  KVM and Xen VMs start with the OS.

KVM with Spice performs near native for GPU needs. We won't be running high-FPS games in it, but pretty much everything else works very fast ... except gnome3.

---

### Post by SeijiSensei on 2020-11-25
Remove the copy of VirtualBox you are running now, then follow these directions

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

Now you will always have the most up-to-date version of VBox, and one that will run consistently with the rest of your system. Plus it will update itself automatically along with the rest of your software.

Replace "<mydist>" with "eoan" in the line
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian <mydist> contrib
```
That's the version which works with Ubuntu versions starting with 19.10.

Also I have no VBoxREM.so on my system. The only library that comes with VB is /usr/lib/virtualbox/libvboxjxpcom.so.

However see [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1875271/comments/2](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1875271/comments/2) which describes how to use VBoxManage to accomplish what you want.

---

### Post by f00dl3 on 2020-11-25
So that worked. I already had a service created so it worked pretty much right after dropping the Ubuntu apt version of VBox 6.1 and installing the Oracle PPA version. I also had to remove virtualbox-dkms and virtualbox-ext-pack and download the extension pack file manually off of the Virtualbox site. DKMS apparently is not needed anymore or now integrated? 

Does the maintainer of the Ubuntu apt repository know their virtualbox package is broken?

---

