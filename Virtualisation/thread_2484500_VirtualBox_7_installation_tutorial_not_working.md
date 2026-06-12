---
title: "VirtualBox 7 installation tutorial not working"
date: 2023-02-28
forum: Virtualisation
---

### Post by theredled on 2023-02-28
Hi, 

I followed thoroughly that tutorial [https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview) 
But it's not working for me.
Unattended installation gives me an error "systemd-journald[2515]" : Failed to send WATCHDOG=1 notofication message: Transport endpoint is not connected connected"
(Would like to send you screenshots but uploading attachements doesn't seem to work...)

As for attended install, it gives me "[drm:vmw_host_printf] *ERROR* Failed to send host log message", then shows an endless graphical loading screen.

Any clue?

Using latest VirtualBox 7.0 on MacOs Catalina, and latest Ubuntu ISO 22.04.2-desktop-amd64

Thanks!

---

### Post by SeijiSensei on 2023-02-28
Try the "Guided" mode and enter your own username and password when prompted. This whole "unattended" business took me by surprise, too.

---

### Post by theredled on 2023-03-01
Thanks! But I don't get it, where and what is "Guided" mode?

---

### Post by ajgreeny on 2023-03-01
Guided mode is an option when you are installing from a local .iso file, and is offered I think, just after you chose the .iso file from your local filesystem.
It takes you step by step through the naming of the virtual system, the creation of your VM's partitions if you want to do that, whether you want the normal or minimal install ( that is on Xubuntu, but I'm not sure about the other DE varieties, and the setup of username, passwor, etc, etc. It is the method I always use for installing a VM in virtualbox, though I have now moved almost exclusively to KVM/QEMU instead of Virtualbox.

---

### Post by theredled on 2023-03-01
> **ajgreeny said:**
> Guided mode is an option when you are installing from a local .iso file, and is offered I think, just after you chose the .iso file from your local filesystem.
It takes you step by step through the naming of the virtual system, the creation of your VM's partitions if you want to do that, whether you want the normal or minimal install ( that is on Xubuntu, but I'm not sure about the other DE varieties, and the setup of username, passwor, etc, etc. It is the method I always use for installing a VM in virtualbox, though I have now moved almost exclusively to KVM/QEMU instead of Virtualbox.
Oh yeah so that's what I was using.

Does not work.

---

### Post by DuckHook on 2023-03-01
I gather that MacOS is your host?

If so, then I suggest that you contact Apple for their guidance. Presumably, you have Apple support for that pricey box you bought from them, so time for them to earn their keep.

Alternatively, you can try the Apple forums/support sites. Apple users would be far more familiar with their OS than we Linux types.

VBox also has its own forums, though they aren't too active these days. Again, VBox would be most familiar with the intricacies of their own platform.

Personally, I'm with ajgreeny: I dropped external slapped&#8209;on platforms like VBox some time ago in favour of Linux's native VM. KVM is not only solid, less troublesome and baked into the kernel, but runs faster for me. It's not the solution for you if you are using MacOS, but perhaps an Apple&#8209;native VM would be similarly superior. I don't know what Apple's VM is, but such knowledge shouldn't be hard to acquire.

---

### Post by bernard010 on 2023-03-20
Within your virtual box guest click the "New" icon.
Type the name of the O.S. you wish to install.

Now it will need the memory size for the guest OS. Be sure to leave the Host OS at least 4GB.
Click the create virtual hard disk to create now. You will be asked the type of file select VID then next.

Storage should be Dynamically allocated, you will only use what is needed no matter how large the partition is.
Ubuntu needs 25GB of storage to have enough for the OS, next.
You now need to open Settings and open the System tab. UN-check mark the floppy box and move it to the bottom of the list.
Check mark the Network box to have internet.Their are up and arrows to move the start-up order.
Disk, Network, Optical, Floppy should be the correct order.

Now move to the Display tab. Video memory about 64 MB. The Scale Factor setting for Ubuntu works best at 156%.
Be sure to check mark the Enable 3D Acceleration box.

Click the Start Icon and on the right click the folder icon on the right side of the screen.
You will now see a ADD+ icon on the top left click the icon. This will open your Host downloads folder.
Now you can select the OS you downloaded to install in virtual box, select open.
Next click Choose to choose this .iso file.
The only thing left is to click the Start Icon and the installer will begin installing your new OS.

---

