---
title: "import old windows"
date: 2018-05-30
forum: Virtualisation
---

### Post by nooshinnr on 2018-05-30
Hi every one
I had installed Vbox 5.1 on ubuntu 16.04 and the guest OS was windows 7. now that I have installed vbox 5.2.12 when I want to start that windows the following error appears:

 [I]The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user. 
[/I]
[I]also this problem still exist when I want to create a new machine and install a new windows.

Failed to open a session for the virtual machine Windows.[/I]

I used [COLOR=#0000ff]sudo *'/sbin/vboxconfig' *[/COLOR][COLOR=#000000]* but the problem is not solved*[/COLOR]

the error details says:

The virtual machine 'Windows' has terminated unexpectedly during startup with exit code 1 (0x1).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: MachineWrap
Interface: IMachine {85cd948e-a71f-4289-281e-0ca7ad48cd89}

can I access to the old version of windows I had or I have to forget about it?

---

### Post by cruzer001 on 2018-05-30
I have not experience this error, but I think I would first verify what kernel module is installed.  If its the incorrect version my first guess would be to remove it, but guesswork is not a good option :) so you may want to wait for others to reply.

How to list kernel  modules
[https://wiki.archlinux.org/index.php/Kernel_module](https://wiki.archlinux.org/index.php/Kernel_module)

What all do you have installed?
```
sudo apt list --installed | grep -i virtualbox
```

---

### Post by deadflowr on 2018-05-30
Try a reboot.
I would think the older vboxdrv-related kernel modules are still loaded.

---

### Post by nooshinnr on 2018-05-31
> **cruzer001 said:**
> I have not experience this error, but I think I would first verify what kernel module is installed.  If its the incorrect version my first guess would be to remove it, but guesswork is not a good option :) so you may want to wait for others to reply.

How to list kernel  modules
[https://wiki.archlinux.org/index.php/Kernel_module](https://wiki.archlinux.org/index.php/Kernel_module)

What all do you have installed?
```
sudo apt list --installed | grep -i virtualbox
```

When I used above command there were some old version of vbox kernels still

How can I remove them?

---

### Post by nooshinnr on 2018-05-31
> **deadflowr said:**
> Try a reboot.
I would think the older vboxdrv-related kernel modules are still loaded.

You were right older version modules are still exist I can’t remove them

---

### Post by deadflowr on 2018-05-31
What actually solved the problem?
(Assuming the Solved tag is true)

---

