---
title: "KVM - How to Change Storage Directory"
date: 2010-01-24
forum: Server Platforms
---

### Post by robertomason on 2010-01-24
I'm running Ubuntu 9.10 with Kvm. I've used a howto to configure my network. Seems to work fine, I've installed the Virtual Machine manager, when I go to create my Virtual Machine, I see the the image is automatically created in /var/lib/libvirt/images. I have a totally separate path for my images. How to I configure a different image directory

Thank You
Roberto

---

### Post by scottwimer on 2011-05-18
Roberto,

I don't know if you figured this out yet or not.  But, since I just had the same question on my Ubuntu Lucid host, and found out the answer, I figured I should respond.  This way, when I have the same question in 4 months or so, the answer will be easy to find. :)

I'm using virtManager.  There are a couple of things you can do.

One thing you can do is change the config for virtManager.  To do this, edit /usr/share/virt-manager/config.py and search for DEFAULT_VIRT_IMAGE_DIR, changing it to what you want.

That's a brute force way that you probably shouldn't do.

The other, most likely better way, is to add a new storage pool.  Here's how I did that using virtManager.

In the Virtual Machine Manager window, right-click the VM host (not guest), to manage (I chose "localhost (QEMU)").  Select the "Details" entry from the pop-up menu.

In the "localhost (System) Host Details" window, select the storage tab.  There should be one entry in the list of storage pools on the left (which aren't labeled as storage pools, unfortunately), and that will be "default" with "Filesystem Directory" underneath the name "default".  Click the green plus sign on the bottom left of this window to add a new pool.  Follow the directions in the windows that pop up to name a new pool, leave the type as Filesystem Directory.  Then, specify the path for this pool.  I don't know if it will create the path for you if it doesn't already exist.

Then, once you have this new pool created, select the default pool, and hit the stop button in the bottom left of the Host Details window.  That should leave your new storage pool as the only active one.

Then, when you're creating new VMs, you can choose Managed Storage and create a new volume in the storage pool you just added.

This process works for me.   Good luck.

Scott

---

### Post by Sir_Mc_Tod on 2012-04-24
i know this thread is old, but i just wanted to show another way of "changing" the default images storage path.
just ad a symbolic link to the desired target to /var/lib/libvirt/images

---

