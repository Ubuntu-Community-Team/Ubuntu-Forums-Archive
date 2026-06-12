---
title: "Rescue files from dead VM?"
date: 2008-04-21
forum: Virtualisation
---

### Post by bluewhale on 2008-04-21
Planning for the worst :)  

How can I go into a VM which no longer boots and recover specific files from it? Similar to booting a 'dead' hard drive in another system to recover files.

---

### Post by Jonne on 2008-04-21
You should be able to load a livecd (load the iso into the virtual cd drive, or even in your real drive, depending how it's mapped), and hopefully read what's on the 'virtual disk'.

---

### Post by bluewhale on 2008-04-21
ok... I'm not quite following.  ](*,)  

If I boot to Ubuntu 7.10 from a live disk how would that help me gain access to the files in the VM? Is there a utility within the live version of Ubuntu that can open the VMDK files allowing me to recover them? Or does the VMDK file just allow anyone to peruse through it?

---

### Post by mrsteveman1 on 2008-04-21
I think you mean the bare hardware OS isnt working and you therefor cant get to a VM on the machine anyway.

I would boot a livecd, copy the VM and its files to an external drive, and reinstall the original bare hardware OS.

You could also run vmware inside the livecd but i wouldn't do that, its unnecessary.

---

### Post by bluewhale on 2008-04-22
Hey Steve: 

> I think you mean the bare hardware OS isnt working and you 
> therefor cant get to a VM on the machine anyway.

Pretty much. I mean booting into a live CD or taking the hard drive out and putting it in another system. Then pulling one single file off it. 

For one file I probably would not bother, but as I will probably have more than one VMWare PC running soon moving all of the VMDK files makes sense.  I was just looking for an easier way. 

Thanks to all. 

Paul

---

### Post by Jonne on 2008-04-22
It depends on what happened to the VM. If it's a Windows VM, and Windows decided to crap out (virus, registry corruption, being windows) without affecting the integrity of the virtual machine's disk, you can just go into the settings for the virtual machine, and mount an iso image of the ubuntu livecd. Start up the cd, let it boot off the liveCD, and see if you can still read the files on the virtual ntfs partition (you might have to mount it manually). If your files are still intact, you can just get them out with samba, shared folders or whatever you like.

If your host OS is screwed up (without it affecting the virtual machine), just copying all the files related to the virtual machine to a new installation should be enough (it should be a huge disk file, and some config files, depending on whether you use vmware or virtualbox).

If your files got corrupted due to HD failure or whatever, you should've backed up to another drive, there's probably not a lot you can do (except for some black magic with dd and such, but only the truly 1337 will be able to pull that off).

You should back up important stuff to another machine/an external disk/other media anyway, don't rely on recovery software.

---

