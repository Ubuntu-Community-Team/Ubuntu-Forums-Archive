---
title: "No display in VMware player on Ubuntu"
date: 2010-07-28
forum: Virtualisation
---

### Post by efpob on 2010-07-28
Ubuntu 10.04 64-bit, nvidia 256.35 drivers (also tried 195), 4GB RAM

I have been running VirtualBox for a while and decided to give VMWare player 3.1 a go.

I downloaded, installed via sudo, created a VM and when powering on the window where it should be showing the VM display is showing my desktop background!

I've tried updating my NVidia drivers, I've also gone back to stock Ubuntu drivers and just get a black display instead.

Full screen gives the same. Any ideas why there's no display?

The VM is running, you can see the window resize as the resolution changes from BIOS to the Windows7 setup CD

[IMG]http://i39.photobucket.com/albums/e198/mmpob/vmwareplayer.png[/IMG]

---

### Post by fjgaude on 2010-07-28
It seems you don't have the VM located to where Player would see it.

The Player looks to be working okay but you have no VM for it to use.

---

### Post by DarthScape on 2010-07-28
What happens when you try to put it into full screen?

---

### Post by efpob on 2010-07-29
I created a VM from scratch, following all defaults; you can see the Player window resize as the resolution changes, so it's definitely running a VM

Putting it in fullscreen results in a big black border, the toolbar across the top, and a transparent window to the desktop where the VM should be showing :S

---

### Post by fjgaude on 2010-07-29
What happens if you click on File and then Open a VM?

Player simply doesn't know where your VM is located, on what partition.

---

### Post by efpob on 2010-07-30
I tried that, and still the same.

I even removed the VMs from the list on the side, did File->Open, and tried running them.  Just a window to the desktop.

I suspend the machine and you can see it properly in the screen grab, but still no main display

---

### Post by dcstar on 2010-07-31
> **efpob said:**
> I tried that, and still the same.

I even removed the VMs from the list on the side, did File->Open, and tried running them.  Just a window to the desktop.

I suspend the machine and you can see it properly in the screen grab, but still no main display

Turn off the "Accelerate 3D Graphics" option on the VM, I have had weird things happen in Windows 7 VMs with that enabled in my Player 3.1 setup.

---

### Post by efpob on 2010-08-02
tried disabling hardware acceleration, and still no joy :S

---

### Post by dcstar on 2010-08-04
> **efpob said:**
> tried disabling hardware acceleration, and still no joy :S

Turn off all Visual Effects on the Ubuntu host.

---

### Post by efpob on 2010-08-04
now I just get a black screen instead of seeing the desktop background

---

### Post by fsando on 2011-05-11
A possible solution:

Hi, don't know if you found solutions to your problems. I had apparently the same problem: vmware player opens and boots windows but the screen is totally transparent, it turns out that I had something called gtk RGBA extension installed from a PPA (erik-b-andersen). When I removed it everything went back to normal.

---

