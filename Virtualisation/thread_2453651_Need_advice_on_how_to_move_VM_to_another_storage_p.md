---
title: "Need advice on how to move VM to another storage pool"
date: 2020-11-14
forum: Virtualisation
---

### Post by franknfurter2 on 2020-11-14
Hello everybody,

great, that you read this. Let me first describe my setup here:

I am a little bit new to virtualisation with virt-manager and KVM/QEMU and so I started out of the box and did not plan my setup before (yes, I know, it's a mistake). So today I have plugged in an new drive on the host and create a ext4 partition on it. It has to store my vms in future and so I created a directory named "BigDataDir" on it. Within virt-manager I created a new directory based storage pool named "BigData" pointing to "BigDataDir".

Many weeks ago, I started with small vm's and had created a first directory based StoragePool named "KVMPool" (within my home dir). Now I want to do a bit clean up an move the vm's in "KVMPool" to "BigData" Pool (merge them) and drop the pool "KVMPool" afterwards. The few Files within both pool have different names, so there will not be any name conflict.

Can someone help here maybe with a step by step guide and perhaps point me to a guide about how to plan and layout pools best way.

Regards

Frank

---

### Post by ajgreeny on 2020-11-14
Open up **virt-manager** and then open the VM you want to move. Now go to **View** menu and click **Details**.
In the window that opens go to the **SATA Disk** or IDE Disk depending on your VM.
Now move to the XML tab at the top instead of Details and there you will see the full pathway to the current folder.  The XML file is just text that you can edit, changing the current folder to the new folder pathway, then click the Apply button bottom right.

That's all you need to do, and you should find that it will just run as it did before from this new folder.
I had to do this myself recently when I imported a qcow2 from another machine and did not move it from the folder to which I downloaded the image before I imported it.

Good luck!

---

### Post by Dennis N on 2020-11-14
If using the same host, you can just copy the .qcow2 disk from the old to the new location, use virt-manager to delete the vm in the original location, then use virt-manager's "import existing disk image" option to import the copied .qcow2 from the new location. You may have to re-establish some of your configuration settings when you import. 

Based on my experience, you could even switch the host as well if necessary. I once moved some VMs from a Ubuntu host to Fedora host.

---

### Post by franknfurter2 on 2020-11-14
Dear ajgreeny,

thanks so far. So I do not find this tab pages like in your screenshot and I guess it has to do with an older virt-manager version. It's version 1.5.1 on my Ubuntu 18.04 LTS host. Seems that ubuntu LTS does not have the new versions. Could you tell me, which version you are using?
On the other hand I was thinking, that there should be a way or command to simply merge pools. So if one has many machines in one pool he or she has to edit a lot of xml. I thought that machine definitions had pointers to the pools and the pool pointers to the directories (or disk group, storage or what ever).

By the way: Do you know if the actual virt-manager will compile and work on Ubuntu 18.04

Regards

Frank

---

### Post by franknfurter2 on 2020-11-14
Just got virt-manager 3.1 running. I can see the xml tab. Thanks so far.

---

### Post by ajgreeny on 2020-11-14
My host is Xubuntu 20.04 and virt-manager version 2.2.1.

I am fairly new to KVM as well having previously used VBox for several years until the installation of host 20.04 so I do not know how different your version in 18.04 might be to my 2.2.1.  Perhaps you can get to those XML files in a different way in your version

What do you mean when you ask "if the actual virt-manager will compile and work on Ubuntu 18.04"?  18.04 has its own version of virt-manager which is 1.5.1, as you have already; there may be a PPA for bionic which will get you a later version, but before we go down that route tell us, or show us with a screenshot like mine, what you see when you open the VM from virt-manager and go to the **View ->Details** window.

Having searced my system the xml files are in /etc/libvirt/qemu/ where I have debian10.xml  Linux-Mint-20.xml  Lubuntu-Focal.xml  Ubuntu-20.10.xml  Windows_10.xml  Xubuntu-20.10.xml.  Unfortunately they read very differently to what I see in the virt-manager window, so I will keep looking.

EDIT:
OK, I was too late with all this as you have now found version 3.1.
Where did you find that; in a ppa?

---

### Post by TheFu on 2020-11-14
A few more options.

Option 1:
Is a trivial solution and uses a symbolic link.
[LIST=1]
[*]Shutdown all VMs.
[*]Move everything in /var/lib/libvirt/qemu/ to the new storage.
[*]Remove the qemu level under /var/lib/libvirt/ and create a symlink from  /var/lib/libvirt/qemu ---> the new location.
[*]Start all the VMs.
[/LIST]
Bam, you've just moved all the VMs to new storage and didn't need to create a new storage pool or anything.

Option 2:
[LIST=1]
[*]Shutdown all VMs.
[*]Move everything in /var/lib/libvirt/qemu/ to the new storage.
[*]virsh edit {name of guest VM}  ... change the location of the storage file to the new directory location. Fix any other directory locations in the file too. Do this step for each VM.
[*]Start all the VMs.
[/LIST]

Simple.  The VM definitions are just XML files. They aren't even ugly.  But libvirt doesn't like them being modified without someone telling libvirt that happened.  **virsh edit**, **virsh define** are the commands that handle that stuff.  

Sometimes the GUI is harder than necessary. I think this is one of those times, especially if you are fast in your editor.  Understanding what is really happening underneath the GUI is why we can be so much more efficient with things like this. /etc/libvirt/ is where te xml definitions for the VMs are stored.

Clearly, before modifying any of the XML files or VMs, ensure you have good backups for both.

---

### Post by Dennis N on 2020-11-14
Using LVM logical volume has proven to be a good idea for storage of VMs as you can outgrow your original estimate of space needed with a partition.

I never needed the xml file when moving a VM to a different host or storage location. Importing the VM disk created a new xml on the host.

---

### Post by ajgreeny on 2020-11-15
Well at least the OP can now see there are many ways to do this, several of which I was not aware of.

I see a lot more threads about KVM/QEMU and virt-manager now than I did before, possibly because I just notice them more now, being a fairly new user, moving from VBox. However I still believe it is by far the best virtualisation system of the most well known three; faster, smoother running and so far, less prone to freezes or crashes.

---

### Post by TheFu on 2020-11-15
> **Dennis N said:**
> Using LVM logical volume has proven to be a good idea for storage of VMs as you can outgrow your original estimate of space needed with a partition.
Yep.  I use LVM on the host to present block devices to each guest VM. LVM support of the guests is built-into libvirt and creation of new VMs using LVM is also trivial under virt-manager. 

> **Dennis N said:**
> I never needed the xml file when moving a VM to a different host or storage location. Importing the VM disk created a new xml on the host.
I've never used the import method.  In 2010 when I started using KVM/libvirt, it didn't work, so I never learned to trust it.  Same for the networking setup that libvirt automatically creates now - I don't trust it because it was so very bad and setting up a linux-bridge is pretty easy in either the interfaces file or in netplan ... er ... finally.  I have little use for host-only or NAT networking of my VMs.  

When I use LXD containers, they use a normal linux bridge too. More and more of my 'service VMs' are moving into LXD containers. They are much lighter and use far less storage, RAM, CPU, overhead.  There are some things which will always be in a VM, mainly things for network security.  And I'll never put a WAN router into a VM - that needs to be on real hardware.  Security architecture is part of my overall VM solutions, but so is storage and performance.

---

### Post by franknfurter2 on 2020-11-16
> **ajgreeny said:**
> 
EDIT:
OK, I was too late with all this as you have now found version 3.1.
Where did you find that; in a ppa?

I found the version 3.2.0 [here]("https://virt-manager.org/download/") and the version 3.1.0 [here]("https://releases.pagure.org/virt-manager/"). You find all the older version there. You can start them right out of the box but I found a problem with the version 3.x.x. See my post from today. So be careful.

---

