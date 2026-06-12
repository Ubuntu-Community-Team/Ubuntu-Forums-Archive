---
title: "Unable to resize the screen of VirtualBox Manager"
date: 2023-05-21
forum: Virtualisation
---

### Post by satimis on 2023-05-21
Hi,

Just discovered unable to resize the screen of Virtualbox manager.  It happens on both Ubuntu 22.04 and 20.04.

Please help.  Thanks in advance.

Regards

---

### Post by TheFu on 2023-05-24
I don't have time to provide detailed help, but resizing has the client-side and the server-side.  Additionally, verify that the current, correct, guest additions are installed.  After each new Linux kernel, I remember having to reinstall the guest additions again.  This was a virtualbox thing 10 yrs ago. IDK if they made that automatic since then.

Good luck.  I won't be monitoring this thread.

---

### Post by satimis on 2023-05-25
> **TheFu said:**
> I don't have time to provide detailed help, but resizing has the client-side and the server-side.  Additionally, verify that the current, correct, guest additions are installed.  After each new Linux kernel, I remember having to reinstall the guest additions again.  This was a virtualbox thing 10 yrs ago. IDK if they made that automatic since then.

Good luck.  I won't be monitoring this thread.
Thanks for your reply.

I have updated/upgraded Guest Addition frequently.

It is very strange to me
VM -> Settings -> General

On the screen I can see the buttons [Cancel][OK] at the right bottom corner but I can resize the screen.  It is possible moving the screen.

-> System/Display/Storage/etc
The length of screen becomes longer unable to see the [Cancel][OK] buttons.  I can save any change made on that screen.

back to -> General screen again.  It becomes longer the [Cancel][OK] buttons unable to see.  Still I can move the screen but unable to resize it.

I have been running VirtualBox for long time.  This problem just happens.  I have posted the problem to their forum but without a reply.

Regards

---

### Post by ajgreeny on 2023-05-25
So tell us which version of virtualbox you have on your host OS and which version of guest additions was installed in the guest by running the **vboxguestadditions.run** file.

I may have the name of that guest additions .run file wrong as I now use KVM not vbox and I think that once installed vbox tells you if the GA need updating when you open an updated version of the vbox manager window.

I'm a bit rusty on details of vbox now but this is all worth checking

---

### Post by satimis on 2023-05-25
> **ajgreeny said:**
> So tell us which version of virtualbox you have on your host OS and which version of guest additions was installed in the guest by running the **vboxguestadditions.run** file.

I may have the name of that guest additions .run file wrong as I now use KVM not vbox and I think that once installed vbox tells you if the GA need updating when you open an updated version of the vbox manager window.

I'm a bit rusty on details of vbox now but this is all worth checking
On Ubuntu 22.04 Host

$ echo $(virtualbox --help | head -n 1 | awk '{print $NF}')```

v7.0.8

```

$ VBoxClient --version```

Command 'VBoxClient' not found, but can be installed with:
sudo apt install virtualbox-guest-x11      # version 6.1.38-dfsg-3~ubuntu1.22.04.1, or
sudo apt install virtualbox-guest-x11-hwe  # version 6.1.38-dfsg-3~ubuntu1.22.04.1

```

**[COLOR="#FF0000"]On Host[/COLOR]**
$ sudo apt install virtualbox-guest-x11
$ VBoxClient --version```

6.1.38_Ubuntur153438

```

**[COLOR="#FF0000"]On VM[/COLOR]**
VBoxClient --version```

7.0.8r156879

```

Regards

---

### Post by ajgreeny on 2023-05-25
It looks as if you may be mixing versions of VBox and the guest additions from the repos and also direct from the VBox website at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) but it's not clear to me from what you have said in post #5 above. Unfortunately I no longer use VBox so can not really help with more detail.

I have never used the version from the Ubuntu repos but always used the most recent direct from the website which is now 7.0.8 and needs the extension pack from [https://download.virtualbox.org/virtualbox/7.0.8/Oracle_VM_VirtualBox_Extension_Pack-7.0.8.vbox-extpack](https://download.virtualbox.org/virtualbox/7.0.8/Oracle_VM_VirtualBox_Extension_Pack-7.0.8.vbox-extpack).  Just download tha , double click it and it will be installed into the VBox Manager.
Once installed in the VBox manager application you will be told a new version must be installed whenever a new version of VBox is released and started.  You will also be given the chance to upgrade the guest additions version when you start a VM using the new VBox version.

It is essential that the version of VBox and the extension pack/guest additions match exactly or you may experience the problems you have seen so I suggest perhaps you uninstall VBox completely and start again using versions from the VBox website only.  All your VMs will remain intact and should be able to run just as before.

---

### Post by satimis on 2023-05-25
> **ajgreeny said:**
> It looks as if you may be mixing versions of VBox and the guest additions from the repos and also direct from the VBox website at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) but it's not clear to me from what you have said in post #5 above. Unfortunately I no longer use VBox so can not really help with more detail.

I have never used the version from the Ubuntu repos but always used the most recent direct from the website which is now 7.0.8 and needs the extension pack from [https://download.virtualbox.org/virtualbox/7.0.8/Oracle_VM_VirtualBox_Extension_Pack-7.0.8.vbox-extpack](https://download.virtualbox.org/virtualbox/7.0.8/Oracle_VM_VirtualBox_Extension_Pack-7.0.8.vbox-extpack).  Just download tha , double click it and it will be installed into the VBox Manager.
Once installed in the VBox manager application you will be told a new version must be installed whenever a new version of VBox is released and started.  You will also be given the chance to upgrade the guest additions version when you start a VM using the new VBox version.

It is essential that the version of VBox and the extension pack/guest additions match exactly or you may experience the problems you have seen so I suggest perhaps you uninstall VBox completely and start again using versions from the VBox website only.  All your VMs will remain intact and should be able to run just as before.
Thanks for your advice.

I'll download the guest addition from VirtualBox website to check whether my problem can be solved.  I'll come back later.

A further question, can I install both KVM and VirtualBox on the same drive with the same Ubuntu 22.04 host?

I have been running VirtualBox for prolonged time.  Recently I discover that the package is lack of support.  I have KVM  running on another SSD drive.  It is not convenient switching drive to run it.

Thanks

Regards

---

### Post by ajgreeny on 2023-05-26
I still have one old computer which has both VBox and KVM/QEMU installed and both do work fine as far as I can see, though as I said, I haven't ready used VBox for a long time until I just tested that it still works, having moved to KVM.

You definitely must not run the two virtual systems at the same time or apparently problems will appear, but just having them installed does not seem to be detrimental to either one.

---

### Post by satimis on 2023-05-26
> **ajgreeny said:**
> I still have one old computer which has both VBox and KVM/QEMU installed and both do work fine as far as I can see, though as I said, I haven't ready used VBox for a long time until I just tested that it still works, having moved to KVM.

You definitely must not run the two virtual systems at the same time or apparently problems will appear, but just having them installed does not seem to be detrimental to either one.
Thanks for your advice.

Why asking this question it is because there are plenty of space on my daily working PCIe3.0 NVMe SSD, 2TB storage. I have a 500G SSD on this computer running KVM on Ubuntu 22.04 as host.  But it is not convenient switching the hard drives for running another virtualization system.

**[COLOR="#FF0000"]I only use the VM/Guest for 2 purposes;[/COLOR]**
1. Testing software.
2. Running the cloned sites of my live websites on Internet.  I have 35 live WP websites.  I use the cloned sites as backup because I'm only allowed creating 2 backups on my hosting server.  I won't run the cloned sites for work.

It is because the support service of VirtualBox declining. I'm considering switching completely to KVM.  I'll leave VirtualBox on the hard drive and won't delete it.

Do you have experience migrating websites on KVM guests running Duplicator packages?

Regards

---

### Post by ajgreeny on 2023-05-26
No experience of doing that I'm afraid.

I used VBox and now KVM simply to test new distros and disrto versions, nothing more.

---

