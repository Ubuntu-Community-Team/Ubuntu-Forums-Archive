---
title: "Migrating File Server to VM"
date: 2009-09-29
forum: Virtualisation
---

### Post by jpc82 on 2009-09-29
I was wondering what people thought of my idea, and if it will work.

I currently have my main desktop (Core 2 Duo, 4GB of RAM, Vista 64Bit) and a FileServer (Barton 2500+ Underclocked, 512MB Ram, Ubuntu).  I don't use my main desktop for day to day work (MacBook for that) and I have no more room for SATA drives in my fileserver.  I was thinking of setting up VMWare on my Vista machine, installing Ubuntu on it and then using that VM for my fileserver.  I would take the data drives out of my current file server and give the VM physical access to the drives for speed and so I don't have to reformat them and just run it in the background. 

This way I will eliminate my old computer and since all my fileserver does is act as a file server it should tax my desktop too much.  Also, since I mostly only use my main desktop when I need windows and for some video encoding 90% of the time its sitting there idle.  PS, the video encoding usually happens overnight and its just small files to move to my iPod.

What do you guys think of this idea?

---

### Post by dcstar on 2009-10-03
> **jpc82 said:**
> I was wondering what people thought of my idea, and if it will work.

I currently have my main desktop (Core 2 Duo, 4GB of RAM, Vista 64Bit) and a FileServer (Barton 2500+ Underclocked, 512MB Ram, Ubuntu).  I don't use my main desktop for day to day work (MacBook for that) and I have no more room for SATA drives in my fileserver.  I was thinking of setting up VMWare on my Vista machine, installing Ubuntu on it and then using that VM for my fileserver.  I would take the data drives out of my current file server and give the VM physical access to the drives for speed and so I don't have to reformat them and just run it in the background. 

This way I will eliminate my old computer and since all my fileserver does is act as a file server it should tax my desktop too much.  Also, since I mostly only use my main desktop when I need windows and for some video encoding 90% of the time its sitting there idle.  PS, the video encoding usually happens overnight and its just small files to move to my iPod.

What do you guys think of this idea?

Fairly pointless running a fileserver in a VM on a platform that can run the same function better in native mode.

Use VMs for things that can't be done (or done better/more securely) on the host platform.

---

