---
title: "Virt-Manager (VMM) - Migrate from old Desktop to new Desktop - Connection Names"
date: 2024-12-02
forum: Virtualisation
---

### Post by Alan5127 on 2024-12-02
Hi All,

I am in the process of migrating my daily driver (old Dell Optiplex 755 running Ubuntu Desktop 22.04 LTS) to a newer Lenovo ThinkCentre M93p running Ubuntu Desktop 24.01.1 LTS.

I am about to migrate over my Virt-Manager (Virtual Machine Manager / VMM) settings, and I would like to export my connection settings from my old machine, and transfer them over to my new machine.  For the avoidance of doubt - I am NOT wanting to migrate a VM from one host to another, that is a completely different thing.

I don't have that many (a dozen or so), so I could do it manually, but I would like to understand how to do it 'better' (and with less risk of typos etc!)

All of the VMs (Qemu / KVM) are on remote servers, mostly hosted VPS machines, with a few on servers at clients, but I don't think that makes any difference?


I can get the connection strings (LibVirt URIs) from the old machine like this:

```
gsettings get org.virt-manager.virt-manager.connections uris
```

I can also get their 'auto connect' settings like this:

```
gsettings get org.virt-manager.virt-manager.connections autoconnect
```

However, I can't see how to get their 'friendly names' out?

By friendly names, I mean the names that you can edit to whatever you like so that they are meaningful when they display in the list in VMM.  You get to it by:

Select a connection
Edit - Connection Details
Overview tab
Basic details
Name (which is just a label that you can edit as you like)

I have checked on the website ([https://virt-manager.org/](https://virt-manager.org/)) but couldn't find anything there, nor with a Google search (but maybe my Google-Fu is lacking).

I have enumerated all of the schemas, and got this list (trimmed to only show the virt-manager ones):

> org.virt-manager.virt-manager
org.virt-manager.virt-manager.confirm
org.virt-manager.virt-manager.connections
org.virt-manager.virt-manager.console
org.virt-manager.virt-manager.details
org.virt-manager.virt-manager.new-vm
org.virt-manager.virt-manager.paths
org.virt-manager.virt-manager.stats
org.virt-manager.virt-manager.urls
org.virt-manager.virt-manager.vmlist-fields

I have then listed the keys under every single schema, but I can't find any that show the 'friendly name'.  If it can't be done this way, is there somewhere that those 'friendly names' are stored in a config file that I can copy over?


Any help would be much appreciated.


Thanks,

Alan.

---

### Post by TheFu on 2024-12-04
I have about 20 VMs, but never worried about the connection details from virt-manager.  I have ssh-keys setup between them all, which virt-manager will use, so it is just the connection string that needs to be entered.  That's just 1 thing to store and they all look the same.

QEMU/KVM, then check the box "Connect to remote host of SSH", enter my username, hostname. That generates the URI:
qemu+ssh://{username}@hostname/system    That's it.  The hostname is for the VM host, not the guests. After connecting the the VM host, the different guest VMs are populated - running or not.

---

### Post by Alan5127 on 2024-12-07
Hi TheFu,

> I have about 20 VMs, but never worried about the connection details from virt-manager. I have ssh-keys setup between them all, which virt-manager will use, so it is just the connection string that needs to be entered. That's just 1 thing to store and they all look the same.

Yep - that is what I'm trying to avoid.

The dozen or so servers, all having the same name, makes it much harder to find the actual VM I need.  Once you have the correct server (each of which might have one or a dozen VMs under it) is easy to navigate, but its inconvenient finding the right server.


> QEMU/KVM, then check the box "Connect to remote host of SSH", enter my username, hostname. That generates the URI:
qemu+ssh://{username}@hostname/system That's it. The hostname is for the VM host, not the guests. After connecting the the VM host, the different guest VMs are populated - running or not. 

That's all fine as per my OP, but the question here is where the 'friendly name' is stored - it has to be somewhere.

Any ideas as to the answer?


Thanks,

Alan.

---

### Post by TheFu on 2024-12-07
It always matched the name shown in the defined XML file for each VM.  That's under /etc/libvirt/qemu in separate files.  Also shown in virt-manager in the main tab as "Name"  But certainly that wouldn't be the answer you seek.

I'd never think to look in a gnome-db for stuff like this, since headless servers are commonly used for KVM/QEMU VMs.

---

