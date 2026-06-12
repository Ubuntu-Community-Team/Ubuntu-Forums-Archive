---
title: "VMware install erase partition - sanity check"
date: 2014-11-07
forum: Virtualisation
---

### Post by apple6 on 2014-11-07
I'm guessing that by selecting 'erase all and install' in the VMware process I'm not going to do any damage to the system that I'm running this in? 

Here's an image of where I'm at : 

[IMG]https://lh6.googleusercontent.com/_hMxcIlO7WrFNYQx21h5PdgY5HwBCcnf3VUZSlECWZzV=w999-h853-no[/IMG]



I'm sure that It won't, but I thought that I'd check 

I can't see the SCSI3 partition anywhere by looking at something like Gparted or `mount`, so does that mean that its a virtual partition? 

Thanks!

---

### Post by Mark Phelps on 2014-11-07
The text of the radio button you checked clearly says "Erase disk and install ..." -- so my guess is that if you continue in this, it will do exactly what it says -- erase the entire disk.

But ... I don't use VMWare and most folks around here are familiar with VirtualBox.

So, you should consider using that instead,  as you should be able to get better support for that.

---

### Post by TheFu on 2014-11-07
VMware makes 6+ different products. ESXi will overwrite everything. It wants to own the entire machine. 
Don't see the image here.
If using Workstation or Player, then this is about the virtual HDD provided to the setup of a new virtual machine. That is almost always (99.99999%) just a large file on disk and will not cause any issues with existing data. You CAN setup passthru to the real hardware disk controller, but that will not happen by accident - it is an involved process. I wouldn't worry.

---

### Post by slickymaster on 2014-11-07
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by apple6 on 2014-11-07
> **Mark Phelps said:**
> The text of the radio button you checked clearly says "Erase disk and install ..." -- so my guess is that if you continue in this, it will do exactly what it says -- erase the entire disk.

But ... I don't use VMWare and most folks around here are familiar with VirtualBox.

So, you should consider using that instead,  as you should be able to get better support for that.

And it didn't do that at all, which is why these things can be confusing ;)

---

### Post by apple6 on 2014-11-07
> **TheFu said:**
> VMware makes 6+ different products. ESXi will overwrite everything. It wants to own the entire machine. 
Don't see the image here.
If using Workstation or Player, then this is about the virtual HDD provided to the setup of a new virtual machine. That is almost always (99.99999%) just a large file on disk and will not cause any issues with existing data. You CAN setup passthru to the real hardware disk controller, but that will not happen by accident - it is an involved process. I wouldn't worry.


Thanks Fu - I'm trying to get it working with the VMWare tool box at the mo.

Another user has said that this forum is more familiar with Virtual Box, I have that as well if that's the case and I'm happy to use it instead. 

I tried using virtual box earlier though and ran into a problem: How do I actually select the ISO to use with the Oracle VirtualBox? 

Heres the error that Im looking at there : 

[IMG]https://lh5.googleusercontent.com/cKOcICtziwVWAWtA_Oz7uCWINAbf7eTHbq4tYgdGKGiw=w1278-h497-no[/IMG]

I'm not sure how to get around this. 

I have the Lubuntu ISO file in my downloads, but I don't know how to get VM Box to go and get it


thanks



EDIT 


I don't have the file thats mentioned in the image there in /etc

```

vco@geoHP:/etc/init.d$ ls | grep vbox
vboxautostart-service
vboxballoonctrl-service
vboxdrv
vboxweb-service

```

---

### Post by TheFu on 2014-11-07
So ... if you are stuck ... there are hundreds of youtube video walk-thrus for setting up virtual machines. Just be certain to find one using the same hostOS you are with the same hypervisor.

Do what they do and see the same results.

As to connecting an ISO to a VM .... let's step back. What is it that we really want to do?
* an ISO is a CDROM/DVD image
* that is a storage thing - look in the storage tab
* Storage needs to be connected by a controller ... there are usually disk and DVD controllers. 

I haven't used Player since ... 2008-ish and stopped using virtualbox about 2 yrs ago due to stability issues.  My needs are more about server-on-server virtualization and rock solid stable systems, not desktop-on-desktop VMs. For servers, KVM is more stable, faster, and easy enough to work with compared to every other alternative, IMHO.

Oh - and don't install multiple hypervisors on the same physical system. Pick one, **purge** the others.

---

### Post by apple6 on 2014-11-07
> **TheFu said:**
> 
Oh - and don't install multiple hypervisors on the same physical system. Pick one, **purge** the others.


Didn't know about that. 

Think I might start again, everythings been going really badly!

---

### Post by apple6 on 2014-11-07
> **TheFu said:**
> So ... if you are stuck ... there are hundreds of youtube video walk-thrus for setting up virtual machines. Just be certain to find one using the same hostOS you are with the same hypervisor.


They're mainly for Windows though really, there's not a swamp of guides that have people going through the process of setting a Linux VM up In Linux

---

